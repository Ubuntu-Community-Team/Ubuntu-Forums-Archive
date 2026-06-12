---
title: "IP Sockets Project for University"
date: 2008-08-05
forum: Programming Talk
---

### Post by saqureshi on 2008-08-05
Hi There all 

I am developing an IP sockets program for my final year Bsc (Hons) in Computing & Networks which is going to be used for the university robot project. I have the IP sockets program working and now I am trying to add some additions functions to the program which allows me to measure network performance related tests over a (LAN). 

The tests will include sending/echoing bytes a number of bytes to the server and back. The tests will also need to show the time of how long it took to send & receive the message from the client & server respectively, the timing has to be measure milliseconds and to be able to calculate the the elasped time. The project needs to be in for the 28th August and I am not having much luck with it. 

I have enclosed some coding below to show what the program currently looks like at the moment, This also includes my attempts of measuring the time when a message is received by the server, and my attempts to show the number of bytes sent. I desperately need help, any small piece of info you may have just might mke the difference. The coding is shown below for the client & server, this might take a little while to read. 

Client Coding: 


#include "mySocket.h" 
#include "myLog.h" 
#include "myException.h" 
#include "myHostInfo.h" 
#include <string.h> 
//#include "PerfTimer.h" 
#include <Windows.h> 
#include <Time.h> 
//#include <afxwin.h> 


myLog winLog; 
void readServerConfig(string&); 
void checkFileExistence(const string&); 

int main() 
{ 
// Initialize the winsock library 
myTcpSocket::initialize(); 
// LARGE_INTEGER *lpPerformanceCount = (LARGE_INTEGER) new (sizeof 
(LARGE_INTEGER)); 
LARGE_INTEGER lpPerformanceCount ; 
// u_char cTTL 
// CString str; 




// get client's information (assume neither the name nor the address is given) 
winLog << endl; 
winLog << "Retrieve the localHost [CLIENT] name and address:" << endl; 
myHostInfo clientInfo; 
string clientName = clientInfo.getHostName(); 
string clientIPAddress = clientInfo.getHostIPAddress(); 
std::cout << "Name: " << clientName << endl; 
std::cout << "Address: " << clientIPAddress << endl; 
winLog << " ==> Name: " << clientName << endl; 
winLog << " ==> Address: " << clientIPAddress << endl; 

// get server's IP address and name 
string serverIPAddress = ""; 
readServerConfig(serverIPAddress); 
winLog << endl; 
winLog << "Retrieve the remoteHost [SERVER] name and address:" << endl; 
winLog << " ==> the given address is " << serverIPAddress << endl; 

myHostInfo serverInfo(serverIPAddress,ADDRESS); 
string serverName = serverInfo.getHostName(); 
std::cout << "Name: " << serverName << endl; 
std::cout << "Address: " << serverIPAddress << endl; 
winLog << " ==> Name: " << serverName << endl; 
winLog << " ==> Address: " << serverIPAddress << endl; 

// create the socket for client 
myTcpSocket myClient(PORTNUM); 
std::cout << myClient; 
winLog << "client configuation: " << endl; 
winLog << myClient; 

// connect to the server. 
std::cout << "connecting to the server [" << serverName << "] ... " << endl; 
winLog << "connecting to the server [" << serverName << "] ... " << endl; 
myClient.connectToServer(serverIPAddress,ADDRESS); 

int recvBytes = 0; 

while (1) 
{ 
// send message to server 
char messageToServer[MAX_MSG_LEN+1]= "hello world2"; 
//char senddata(socketId,buf,MAX_MSG_LENGTH,0); 
//memset(messageToServer,0,sizeof(messageToServer)); 
std::cout << "[SEND] "; 
std::cin.getline(messageToServer,MAX_MSG_LEN); 
//memset(messageToServer,0,sizeof(senddata)); 
std::cout << " %s [%s]with %d bytes of data:"; 
std::cout << strlen(messageToServer); 


//########################################### 

char tmpbuf[128], timebuf[26]; 
time_t ltime; 
string mystr; 
mystr="ABC"; 
// time( &ltime ); 
QueryPerformanceCounter( &lpPerformanceCount); 
std::cout<<( "Time in something:=%ldms,TTL=%d", &lpPerformanceCount); 
//Removing getline so we that we don't need to wait for input //std::cin.getline 
// (messageToServer,MAX_MSG_LEN); 




//########################################### 


winLog << "[SEND] " << mystr << endl; 
myClient.sendMessage(mystr); 
if ( !string(messageToServer).compare("Quit") || !string 
(messageToServer).compare("quit") ) 
break; 

// receive message from server 
string messageFromServer = ""; 
recvBytes = myClient.recieveMessage(messageFromServer); 
if ( recvBytes == -99 ) 
break; 

std::cout << "[RECV:" << serverName << "]: " << messageFromServer << endl; 
winLog << "[RECV:" << serverName << "]: " << messageFromServer << endl; 

} 

return 1; 
} 

void readServerConfig(string& serverIPAddr) 
{ 
serverIPAddr = "127.0.0.1"; //DEBUG 15.02.08 
string serverConfigFile = ".\\serverConfig.txt"; 
//checkFileExistence(serverConfigFile); 
//ifstream serverConfig(serverConfigFile.c_str()); 

// read server's IP address 
//getline(serverConfig,serverIPAddr); 

//serverConfig.close(); 
} 

void checkFileExistence(const string& fileName) 
{ 
ifstream file(fileName.c_str()); 
if (!file) 
{ 
std::cout << "Cannot continue:" << fileName << " does NOT exist!" << endl; 
exit(1); 
} 
file.close(); 
} 



Server coding: 

#include "myEvent.h" 
#include "mySocket.h" 
#include "myLog.h" 
#include "myException.h" 
#include "myHostInfo.h" 
#include "mySemaphore.h" 
#include "myThread.h" 
#include "myThreadArgument.h" 
#include <iostream> 
#include <stdio.h> 
#include <sys/types.h> 
#include <sys/timeb.h> 
#include <time.h> 



myLog winLog; 



DWORD WINAPI clientHandleThread(LPVOID threadInfo) 
{ 
// this structure will contain all the data this callback will work on 
myThreadArgument* clientArgument = (myThreadArgument*)threadInfo; 

// the semamphore to protect the access to the std output 
mySemaphore* coutSemaphore = clientArgument->getCoutSemaphore(); 

// get the client connection: receiving messages from client and 
// sending messages to the client will all be done by using 
// this client connection 
myTcpSocket* clientConnection = clientArgument->getClientConnect(); 
string clientName = clientArgument->getHostName(); 

// the server is communicating with this client here 
while(1) 
{ 
string messageFromClient = ""; 

// receive from the client 

int numBytes = clientConnection->recieveMessage(messageFromClient); 
if ( numBytes == -99 ) 
break; 

// write to the console and the log file, so lock the semaphore 
coutSemaphore->lock(); 

cout << "[RECV fr " << clientName << "]: " << messageFromClient << endl; 
winLog << "[RECV fr " << clientName << "]: " << messageFromClient << endl; 

// if the client wants to discount 
if ( messageFromClient.compare("quit") == 0 || messageFromClient.compare("Quit") == 0 ) 
{ 
coutSemaphore->unlock(); 
break; 
} 
else // send to the client 
{ 
char messageToClient[MAX_MSG_LEN+1]; 
memset(messageToClient,0,sizeof(messageToClient)); 
cout << "[SEND to " << clientName << "]: "; 
//PC cin.getline(messageToClient,MAX_MSG_LEN); 
winLog << "[SEND to " << clientName << "]: " << messageToClient << endl; 
clientConnection->sendMessage(string(messageToClient)); 
coutSemaphore->unlock(); 
} 
} 

// if we reach here, this session with the client is done, 
// so we set the event on this thread to inform the main 
// control that this session is finished 
clientArgument->getExitEvent()->setEvent(); 
return 1; 
} 

DWORD WINAPI serverHandleThread(LPVOID threadInfo) 
{ 
// this structure will contain all the data this callback will work on 
myThreadArgument* serverArgument = (myThreadArgument*)threadInfo; 

// the semamphore to protect the access to the std output 
mySemaphore* coutSemaphore = serverArgument->getCoutSemaphore(); 

// get the server 
myTcpSocket* myServer = serverArgument->getClientConnect(); 
string serverName = serverArgument->getHostName(); 

// bind the server to the socket 
myServer->bindSocket(); 
cout << endl << "server finishes binding process... " << endl; 
winLog << endl << "server finishes binding process... " << endl; 

// server starts to wait for client calls 
myServer->listenToClient(); 
cout << "server is waiting for client calls ... " << endl; 
winLog << "server is waiting for client calls ... " << endl; 

// server starts to listen, and generates a thread to 
// handle each client 

myThreadArgument* clientArgument[MAX_NUM_CLIENTS]; 
myThread* clientHandle[MAX_NUM_CLIENTS]; 
for ( int i = 0; i < MAX_NUM_CLIENTS; i++ ) 
{ 
clientArgument[i] = NULL; 
clientHandle[i] = NULL; 
} 
int currNumOfClients = 0; 

while ( 1 ) 
{ 
// wait to accept a client connection. 
// processing is suspended until the client connects 
myTcpSocket* client; // connection dedicated for client communication 
string clientName; // client name 
client = myServer->acceptClient(clientName); 
clientName = clientName + "-" + char(65+currNumOfClients); 

// lock the std out so we can write to the console 
coutSemaphore->lock(); 
cout << endl << "==> A client from [" << clientName << "] is connected!" << endl << endl; 
winLog << endl << "==> A client from [" << clientName << "] is connected!" << endl << endl; 
coutSemaphore->unlock(); 

// for this client, generate a thread to handle it 
if ( currNumOfClients < MAX_NUM_CLIENTS-1 ) 
{ 
clientArgument[currNumOfClients] = new myThreadArgument 
(client,coutSemaphore,clientName); 
clientHandle[currNumOfClients] = new myThread(clientHandleThread, 
(void*)clientArgument[currNumOfClients]); 
serverArgument->addClientArgument(clientArgument[currNumOfClients]); 
clientHandle[currNumOfClients]->execute(); 
currNumOfClients++; 
} 
} 

return 1; 
} 

int main(void) 

{ 

// build a semaphore so we can synchronize the access to std cout 
// also includes the log file 
mySemaphore coutSemaphore(string(""),1); 

// Initialize the winsock library 
myTcpSocket::initialize(); 

// create the server: local host will be used as the server, let us 
// first use myHostInfo class to show the name and IP address 
// of the local host 
winLog << endl; 
winLog << "Retrieve the local host name and address:" << endl; 

myHostInfo serverInfo; 
string serverName = serverInfo.getHostName(); 
string serverIPAddress = serverInfo.getHostIPAddress(); 
std::cout << "my localhost (server) information:" << endl; 
std::cout << " Name: " << serverName << endl; 
std::cout << " Address: " << serverIPAddress << endl; 
winLog << " ==> Name: " << serverName << endl; 
winLog << " ==> Address: " << serverIPAddress << endl; 

// open socket on the local host(server) and show its configuration 
myTcpSocket myServer(PORTNUM); 
std::cout << myServer; 
winLog << myServer; 

// create a thread to implement server process: listening to the socket, 
// accepting client calls and communicating with clients. This will free the 
// main control (see below) to do other process. 
myThreadArgument* serverArgument = new myThreadArgument 
(&myServer,&coutSemaphore,serverName); 
myThread* serverThread = new myThread(serverHandleThread,(void*) 
serverArgument); 
serverThread->execute(); 

// main control: since the serverThread is handling the server functions, 
// this main control is free to do other things. 
while ( 1 ) //MAIN CONTROL LOOP 
{ 
// do whatever you need to do here, I am using Sleep(x) 
// to make a little delay, pretending to be the other 
// possible processings. 
Sleep(1000); 

} 
return 1; 
} 

Thank you 

Shahid

---

### Post by catchmeifyoutry on 2008-08-05
Hi,
I don't think anybody is going to read your code if you post it just as is.
You have to ask a specific question if you want any response.
What's not working? What is the code doing now? What should it be doing?

Also, if your on a Computer & Networking project of the university, and YOU don't know how to solve it, isn't it then maybe a bit too specific and specialized? I mean, it can't be a simple programming problem, right?
In any case, you should provide more info an background.

---

### Post by catchmeifyoutry on 2008-08-05
Oh, also, I see now that your code is for windows.
Since this is ubuntuforums and ubuntu is a linux distribution, you might be better off on a forum for windows programmers.
In fact, I (and probably many others here) am not very familiar with windows network api and cannot compile your, if I wanted to try it out.

Best.

---

### Post by escapee on 2008-08-05
Shahid,

When posting code, please use the CODE or PHP tags for readability...it's not likely anyone will read that as is.
And as catchmeifyoutry has already stated, you haven't really asked a direct question about your code.  If you ask a question, you'll likely get help.  If you ask us to do your work for you, it's likely no one will respond.

Good luck.

---

### Post by DraconPern on 2008-08-07
Don't reinvent the wheel. You need to look at the boost library immediately!  Look at the asio namespace.

---

### Post by Kadrus on 2008-08-07
Please post your code in a readable format
[PHP]
#include "mySocket.h"
#include "myLog.h"
#include "myException.h"
#include "myHostInfo.h"
#include <string.h>
//#include "PerfTimer.h"
#include <Windows.h>
#include <Time.h>
//#include <afxwin.h>


myLog winLog;
void readServerConfig(string&);
void checkFileExistence(const string&);

int main()
{
// Initialize the winsock library
myTcpSocket::initialize();
// LARGE_INTEGER *lpPerformanceCount = (LARGE_INTEGER) new (sizeof
(LARGE_INTEGER));
LARGE_INTEGER lpPerformanceCount ;
// u_char cTTL
// CString str;




// get client's information (assume neither the name nor the address is given)
winLog << endl;
winLog << "Retrieve the localHost [CLIENT] name and address:" << endl;
myHostInfo clientInfo;
string clientName = clientInfo.getHostName();
string clientIPAddress = clientInfo.getHostIPAddress();
std::cout << "Name: " << clientName << endl;
std::cout << "Address: " << clientIPAddress << endl;
winLog << " ==> Name: " << clientName << endl;
winLog << " ==> Address: " << clientIPAddress << endl;

// get server's IP address and name
string serverIPAddress = "";
readServerConfig(serverIPAddress);
winLog << endl;
winLog << "Retrieve the remoteHost [SERVER] name and address:" << endl;
winLog << " ==> the given address is " << serverIPAddress << endl;

myHostInfo serverInfo(serverIPAddress,ADDRESS);
string serverName = serverInfo.getHostName();
std::cout << "Name: " << serverName << endl;
std::cout << "Address: " << serverIPAddress << endl;
winLog << " ==> Name: " << serverName << endl;
winLog << " ==> Address: " << serverIPAddress << endl;

// create the socket for client
myTcpSocket myClient(PORTNUM);
std::cout << myClient;
winLog << "client configuation: " << endl;
winLog << myClient;

// connect to the server.
std::cout << "connecting to the server [" << serverName << "] ... " << endl;
winLog << "connecting to the server [" << serverName << "] ... " << endl;
myClient.connectToServer(serverIPAddress,ADDRESS);

int recvBytes = 0;

while (1)
{
// send message to server
char messageToServer[MAX_MSG_LEN+1]= "hello world2";
//char senddata(socketId,buf,MAX_MSG_LENGTH,0);
//memset(messageToServer,0,sizeof(messageToServer));
std::cout << "[SEND] ";
std::cin.getline(messageToServer,MAX_MSG_LEN);
//memset(messageToServer,0,sizeof(senddata));
std::cout << " %s [%s]with %d bytes of data:";
std::cout << strlen(messageToServer);


//###########################################

char tmpbuf[128], timebuf[26];
time_t ltime;
string mystr;
mystr="ABC";
// time( &ltime );
QueryPerformanceCounter( &lpPerformanceCount);
std::cout<<( "Time in something:=%ldms,TTL=%d", &lpPerformanceCount);
//Removing getline so we that we don't need to wait for input //std::cin.getline
// (messageToServer,MAX_MSG_LEN);




//###########################################


winLog << "[SEND] " << mystr << endl;
myClient.sendMessage(mystr);
if ( !string(messageToServer).compare("Quit") || !string
(messageToServer).compare("quit") )
break;

// receive message from server
string messageFromServer = "";
recvBytes = myClient.recieveMessage(messageFromServer);
if ( recvBytes == -99 )
break;

std::cout << "[RECV:" << serverName << "]: " << messageFromServer << endl;
winLog << "[RECV:" << serverName << "]: " << messageFromServer << endl;

}

return 1;
}

void readServerConfig(string& serverIPAddr)
{
serverIPAddr = "127.0.0.1"; //DEBUG 15.02.08
string serverConfigFile = ".\\serverConfig.txt";
//checkFileExistence(serverConfigFile);
//ifstream serverConfig(serverConfigFile.c_str());

// read server's IP address
//getline(serverConfig,serverIPAddr);

//serverConfig.close();
}

void checkFileExistence(const string& fileName)
{
ifstream file(fileName.c_str());
if (!file)
{
std::cout << "Cannot continue:" << fileName << " does NOT exist!" << endl;
exit(1);
}
file.close();
}



Server coding:

#include "myEvent.h"
#include "mySocket.h"
#include "myLog.h"
#include "myException.h"
#include "myHostInfo.h"
#include "mySemaphore.h"
#include "myThread.h"
#include "myThreadArgument.h"
#include <iostream>
#include <stdio.h>
#include <sys/types.h>
#include <sys/timeb.h>
#include <time.h>



myLog winLog;



DWORD WINAPI clientHandleThread(LPVOID threadInfo)
{
// this structure will contain all the data this callback will work on
myThreadArgument* clientArgument = (myThreadArgument*)threadInfo;

// the semamphore to protect the access to the std output
mySemaphore* coutSemaphore = clientArgument->getCoutSemaphore();

// get the client connection: receiving messages from client and
// sending messages to the client will all be done by using
// this client connection
myTcpSocket* clientConnection = clientArgument->getClientConnect();
string clientName = clientArgument->getHostName();

// the server is communicating with this client here
while(1)
{
string messageFromClient = "";

// receive from the client

int numBytes = clientConnection->recieveMessage(messageFromClient);
if ( numBytes == -99 )
break;

// write to the console and the log file, so lock the semaphore
coutSemaphore->lock();

cout << "[RECV fr " << clientName << "]: " << messageFromClient << endl;
winLog << "[RECV fr " << clientName << "]: " << messageFromClient << endl;

// if the client wants to discount
if ( messageFromClient.compare("quit") == 0 || messageFromClient.compare("Quit") == 0 )
{
coutSemaphore->unlock();
break;
}
else // send to the client
{
char messageToClient[MAX_MSG_LEN+1];
memset(messageToClient,0,sizeof(messageToClient));
cout << "[SEND to " << clientName << "]: ";
//PC cin.getline(messageToClient,MAX_MSG_LEN);
winLog << "[SEND to " << clientName << "]: " << messageToClient << endl;
clientConnection->sendMessage(string(messageToClient));
coutSemaphore->unlock();
}
}

// if we reach here, this session with the client is done,
// so we set the event on this thread to inform the main
// control that this session is finished
clientArgument->getExitEvent()->setEvent();
return 1;
}

DWORD WINAPI serverHandleThread(LPVOID threadInfo)
{
// this structure will contain all the data this callback will work on
myThreadArgument* serverArgument = (myThreadArgument*)threadInfo;

// the semamphore to protect the access to the std output
mySemaphore* coutSemaphore = serverArgument->getCoutSemaphore();

// get the server
myTcpSocket* myServer = serverArgument->getClientConnect();
string serverName = serverArgument->getHostName();

// bind the server to the socket
myServer->bindSocket();
cout << endl << "server finishes binding process... " << endl;
winLog << endl << "server finishes binding process... " << endl;

// server starts to wait for client calls
myServer->listenToClient();
cout << "server is waiting for client calls ... " << endl;
winLog << "server is waiting for client calls ... " << endl;

// server starts to listen, and generates a thread to
// handle each client

myThreadArgument* clientArgument[MAX_NUM_CLIENTS];
myThread* clientHandle[MAX_NUM_CLIENTS];
for ( int i = 0; i < MAX_NUM_CLIENTS; i++ )
{
clientArgument[i] = NULL;
clientHandle[i] = NULL;
}
int currNumOfClients = 0;

while ( 1 )
{
// wait to accept a client connection.
// processing is suspended until the client connects
myTcpSocket* client; // connection dedicated for client communication
string clientName; // client name
client = myServer->acceptClient(clientName);
clientName = clientName + "-" + char(65+currNumOfClients);

// lock the std out so we can write to the console
coutSemaphore->lock();
cout << endl << "==> A client from [" << clientName << "] is connected!" << endl << endl;
winLog << endl << "==> A client from [" << clientName << "] is connected!" << endl << endl;
coutSemaphore->unlock();

// for this client, generate a thread to handle it
if ( currNumOfClients < MAX_NUM_CLIENTS-1 )
{
clientArgument[currNumOfClients] = new myThreadArgument
(client,coutSemaphore,clientName);
clientHandle[currNumOfClients] = new myThread(clientHandleThread,
(void*)clientArgument[currNumOfClients]);
serverArgument->addClientArgument(clientArgument[currNumOfClients]);
clientHandle[currNumOfClients]->execute();
currNumOfClients++;
}
}

return 1;
}

int main(void)

{

// build a semaphore so we can synchronize the access to std cout
// also includes the log file
mySemaphore coutSemaphore(string(""),1);

// Initialize the winsock library
myTcpSocket::initialize();

// create the server: local host will be used as the server, let us
// first use myHostInfo class to show the name and IP address
// of the local host
winLog << endl;
winLog << "Retrieve the local host name and address:" << endl;

myHostInfo serverInfo;
string serverName = serverInfo.getHostName();
string serverIPAddress = serverInfo.getHostIPAddress();
std::cout << "my localhost (server) information:" << endl;
std::cout << " Name: " << serverName << endl;
std::cout << " Address: " << serverIPAddress << endl;
winLog << " ==> Name: " << serverName << endl;
winLog << " ==> Address: " << serverIPAddress << endl;

// open socket on the local host(server) and show its configuration
myTcpSocket myServer(PORTNUM);
std::cout << myServer;
winLog << myServer;

// create a thread to implement server process: listening to the socket,
// accepting client calls and communicating with clients. This will free the
// main control (see below) to do other process.
myThreadArgument* serverArgument = new myThreadArgument
(&myServer,&coutSemaphore,serverName);
myThread* serverThread = new myThread(serverHandleThread,(void*)
serverArgument);
serverThread->execute();

// main control: since the serverThread is handling the server functions,
// this main control is free to do other things.
while ( 1 ) //MAIN CONTROL LOOP
{
// do whatever you need to do here, I am using Sleep(x)
// to make a little delay, pretending to be the other
// possible processings.
Sleep(1000);

}
return 1;
} 
[/PHP]
Give us details on what's not working,or no one can help..

---

### Post by dwhitney67 on 2008-08-07
Here's a few comments, not necessarily in any particular order:

Try to simplify the TCP socket wrapper classes such that the server application doesn't have to specifically perform the bind and the listen steps to get the port open.  These steps should be encapsulated in the wrapper class.  Just provide the server a port, and then "enable" it.  Ditto for the WinSock initialization; this step should be done the instant a TCP socket class is instantiated.

I would recommend that you strip away the cout statements that you have in your code, especially if your intent is to perform a timing study.

I would also recommend that you rely on select() to determine when there is activity from the client.  That way you can determine when/if a message is sent or whether the client has disconnected.  You cannot assume the client will send the "Quit" message directive to the server!

Also, when receiving data from the client (or the client receives from the server), you should not assume that a complete message will be received.  When using the TCP protocol it is possible that the message can be broken apart, especially if large messages are sent.  This is why it is important to rely on select() so that your application will know when to pick up (read) remaining parts of a message.

It is up to you to decide what message protocol will be used between the client and the server.  For now, it appears that your messages are null-terminated.  That is fine, however if a message is broken up, you may not get that terminating character where you expect it!  Consider using a different delimiter (such as a \n).

Anyhow, that's my $0.02 worth of advice.

---

