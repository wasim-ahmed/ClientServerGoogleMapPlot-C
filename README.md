# ClientServerGoogleMapPlot-C

Coordinates can be plotted using this project on to the Google Map from a C application. The server application acts as Web Server as well as Web Socket
Server. Here Client sends the data to Server which in turn get plotted on to map. Currently the Client application is hard coded with the 10 coordinates
which are communicated and plotted on map at the every 5 seconds.

# SetUp

Start the Server application & then Client application. Go to web browser like Google Chrome & connect to the server using URL "localhost:8000". You should
see the coordinates being plotted on Goole Map. 

# Build Info

The project is build on Windows 10 using MinGw 4.7.2

Compile Client:

gcc -c client.c -I ..\lws-default-20883362\include -I ..\wolfssl-3.15.3 -I ..\wolfssl-3.15.3\wolfssl

gcc  -o client.exe client.o -l ws2_32 -l websockets -L ..\lws-default-20883362\bin\Release


Compile Server:

gcc -c server.c -I ..\lws-default-20883362\include -I ..\wolfssl-3.15.3 -I ..\wolfssl-3.15.3\wolfssl

gcc  -o server.exe server.o -l ws2_32 -l websockets -L ..\lws-default-20883362\bin\Release


#NOTE : For building this project on MinGW 4.7.1 

Download the latest 64 bit libwebsockets binary where LWS_METHOD=x64 is there with some more arguments folder name will be like "lws-x64-22747226" from @ https://ci.appveyor.com/project/lws-team/libwebsockets .
Comment "#define LWS_WITH_LIBUV" from lws_config.h  and build as usual. Remember to change the folder name in your build commands. so commands will be :

For Client:
gcc -c client.c -I ..\lws-x64-22747226\include -I ..\wolfssl-3.15.3 -I ..\wolfssl-3.15.3\wolfssl

gcc -o client.exe client.o -l ws2_32 -l websockets -L ..\lws-x64-22747226\bin\Release

For Server:
gcc -c server.c -I ..\lws-x64-22747226\include -I ..\wolfssl-3.15.3 -I ..\wolfssl-3.15.3\wolfssl

gcc -o server.exe server.o -l ws2_32 -l websockets -L ..\lws-x64-22747226\bin\Release


# Software component:

Web socket C application @ https://github.com/iamscottmoyers/simple-libwebsockets-example

Web socket requires wolfssl which is obtained @ https://www.wolfssl.com/

Web Socket binaries are obtained from @ https://ci.appveyor.com/project/lws-team/libwebsockets . For official website @ https://libwebsockets.org/
