---
title: "error while shutdown socket for reading."
date: 2010-09-06
forum: Programming Talk
---

### Post by arkashkin on 2010-09-06
Hello.
I'm writing a remote terminal service.
I have a problem in the client side.
The client should sends commands which need to be executed to the server side, the server then execute them and send back the result.

first the command sent and then there is a function - "talk2serv" which is responsible to send clients stdin content to the server (so when the server executes a command, he could use it..) and responsible to receive servers stdout and output it as its own stdout.

Seems that my client doing its job pretty well, but when I want to execute some command, and I pass it some thing to stdin, it complain about:

[B]receive_func: shutdown function failed.
: Transport endpoint is not connected[/B]

I must mention that it happens after I see the result of the command execution on the client side (client received the result from the server and printed it out..) 

I'm pasting here my client's code, and if some one have a clue about where is the problem in my code, please help me.


```
/* 
 * File:   rsh_client.cpp
 * Author: Arkadi Viner
 *
 * Created on September 6, 2010, 1:56 PM
 */
using namespace std;

#include <string.h>
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>
#include <sys/socket.h>
#include <netinet/in.h>

#include "libtcp.h"
#include <signal.h>
#include <ctype.h>
#include <iostream>


bool strToInt(char* str, int* result);
void fillCmdArgs(int argc, char* argv[], char * fill_host, int * fill_port, char * fill_arg);
void talk2serv(char * host, int * port, char * args);
void signals();
void closeSocket(int socket);

int input_from_stdin(char * buff);
void print_sys_err(const char *msg);
void print_err(const char *msg);
void close_fd(int sock);
void signalHandler(int signum);
bool send_func(int sock);
bool receive_func(int sock);
bool do_select(int max, fd_set * readset, fd_set * writeset);

#define MINIMUM_PARAM 4
#define MIN_PORT 0
#define MAX_PORT 65535
#define ERROR -1
#define TCPLIB_SEND_ALL 1
#define MAX_PARAM_BUFF 256
#define STD_BUFF_SIZE 65535
#define BYTE 1
#define HOST_LENGTH 4096
#define TCPLIB_GET_ALL  1
#define TCPLIB_GET_SOME 0


int sock;

int main(int argc, char** argv)
{

    int port;
    char temp_host[MAX_PARAM_BUFF]="";
    char temp_args[MAX_PARAM_BUFF] = "";
    char* host = (char*) &temp_host;
    char* args = (char*) &temp_args;

    fillCmdArgs(argc, argv, host, &port, args);

    talk2serv(host, &port, args);


    return (EXIT_SUCCESS);
}

/*
 *  the function retrives arguments from command line and checks for arguments error.
 *  on arguments errors, prints an informative error message and exit.
 */
void fillCmdArgs(int argc, char* argv[], char * fill_host, int * fill_port, char * fill_arg)
{
  int port;
  int paramLen;
  char * pointer = (fill_arg+1);
  char len=0;

  if (argc < MINIMUM_PARAM) //too few parameters
    print_err("Usage: rsh_client <host> <port> <command_pipeline>");

  if (!strToInt(argv[2], &port)) //port number isn't a number
    print_err("Usage: rsh_client <host> <port> <command_pipeline>");

  // verify port range
  if (port < MIN_PORT || port > MAX_PORT)
  {
    print_err("Usage: rsh_client <host> <port> <command_pipeline>");
  }

  *fill_port = port;

  paramLen = strlen(argv[1]);
  memcpy(fill_host, argv[1], paramLen);

  for(int i=3;i<argc;i++)
  {
        paramLen = strlen(argv[i]);

        memcpy(pointer, argv[i], paramLen);
        pointer=pointer+paramLen;
        if((i+1)<argc)
        {
            memset(pointer, ' ' , BYTE);
            len++;
        }
        pointer++;
        len+=paramLen;
  }
  fill_arg[0] = len;
}

/*
 *  the function converts array of chars to integer.
 *  on error return true, else false.
 */
bool strToInt(char* str, int* result)
{
  char* p;
  *result = (int)strtol(str, &p, 10);
  if (*p != 0)
    return true;
  if(errno == ERANGE) // if value is out of range
    return false;
  return true;
}

/*
 *  the function is menaging the communication between
 *  stdin of the client and stdout of the socket.
 */
void talk2serv(char * host, int * port, char * args)
{
  fd_set readset;
  fd_set writeset;
  bool toRead = true, toWrite = true;

  signals();

    sock = tcp_connect(host, *port);

    if(sock==ERROR)
        print_sys_err("talk2serv: couldn't create a sock.\n");

    if(tcp_send(sock,args,(args[0]+1),TCPLIB_SEND_ALL)==ERROR)
        print_err("talk2serv: failed to send arguments.\n");

    while(true)
    {
        FD_ZERO(&readset);
        FD_ZERO(&writeset);

        if(toRead)
        {
            FD_SET(sock, &readset);
            FD_SET(STDOUT_FILENO, &writeset);
        }
        if(toWrite)
        {
            FD_SET(STDIN_FILENO, &readset);
            FD_SET(sock, &writeset);
        }

        if(!do_select(sock, &readset, &writeset))
        {
            close_fd(sock);
            exit(EXIT_FAILURE);
        }

        //check if the socket is readable and stdout is writable.
        if((FD_ISSET(STDOUT_FILENO, &writeset))&& (FD_ISSET(sock, &readset)))
        {
            //cerr<<"recieving from socket."<<endl;TODO:REMOVE!
            //if finished recieving from the server, break.
            if(receive_func(sock)) break;
        }
        //check if stdin is readable and the socket is writable.
        if(FD_ISSET(sock, &writeset) && FD_ISSET(STDIN_FILENO, &readset))
        {
            //cerr<<"sending to socket."<<endl;TODO:REMOVE!
            if(send_func(sock))
            {
                //cerr<<"finished sending. now should only recieve."<<endl; TODO:REMOVE!
                toWrite=false;
            }
        }
    }

    close_fd(sock);
}

/*
 *  the function initiallizes signal handler for catching SIGPIPE signal.
 */
void signals()
{
    struct sigaction action;

    action.sa_handler = signalHandler;
    sigemptyset(&action.sa_mask);
    action.sa_flags = 0;

    if (sigaction(SIGPIPE, &action, NULL) < 0)
        print_sys_err("signals: failed initiallizing handler for the SIGPIPE signal handling.\n");
}

/*
 *  signal handler function. catches the SIGPIPE signal.
 */
void signalHandler(int signum)
{
    if (signum == SIGPIPE)
    {
        close_fd(sock);
        print_err("tpclient: Server closed the connection suddenly.\n");
    }
}

/*
 *  the function tries to close a specified file descriptor.
 *  on errors, prints an informative error message to stderr.
 */
void close_fd(int sock)
{
    while (close(sock) < 0)
    {
        if (errno == EINTR) //interrupted by a signal
            continue;

        perror("close_fd: couldn't close the socket./n");
    }
}

/*
 * prints to stderr both systems error and "msg" and exits the program.
 */
void print_sys_err(const char *msg)
{
    perror(msg);
    exit(EXIT_SUCCESS);
}

/*
 * prints to stderr the "msg" and exits the program.
 */
void print_err(const char *msg)
{
    fputs(msg,stderr);
    exit(EXIT_SUCCESS);
}

/*
 *  the function receives servers stdout from the socket and writes it to stdout.
 *  if nothing left to receive, the function returns true, else false.
 *  on error: prints error message and exit.
 */

bool do_select(int max, fd_set * readset, fd_set * writeset)
{
    while (((select(max+1, readset, writeset, NULL, NULL))) < 0)
    {
        if (errno == EINTR) //if was interrupted by a signal
                continue;

        print_sys_err ("do_select: select_func error.\n");
        return false;
    }

    return true;
}

/*
 *  the function receives servers stdout from the socket and writes it to stdout.
 *  if nothing left to receive, the function returns true, else false.
 *  on error: prints error message and exit.
 */
bool receive_func(int socket)
{
    char buffer[STD_BUFF_SIZE];
    long int len =0;

    memset(buffer, 0 , STD_BUFF_SIZE); //clear buffer

    if((len = tcp_receive(socket, buffer,(STD_BUFF_SIZE-1),TCPLIB_GET_SOME))==ERROR)
    {
        close_fd(socket);
        print_err("rsh_client: tcp_receive failed.\n");
    }

    if(len == 0)
    {   //close writing end of socket
        if (shutdown(socket, SHUT_RD) < 0)
        {
            close_fd(socket);
            print_sys_err("receive_func: shutdown function failed.\n");
        }
        return true;    //finished writing to stdout successfuly!
    }

    while(write(STDOUT_FILENO, buffer, len)<0) {
        if (errno == EINTR || errno == EAGAIN) continue;
        print_sys_err("receive_func : can't write to stdout.\n");
    }

    return false;
}

/*
 *  the function sends clients stdin to the server.
 *  if nothing left to send, the function returns true, else false.
 *  on error: prints error message and exit.
 */
bool send_func(int socket)
{
    char buffer [STD_BUFF_SIZE];
    int len=0;

    while((len=read(STDIN_FILENO,buffer,STD_BUFF_SIZE))<0) {
        if (errno == EINTR || errno == EAGAIN) continue;
        print_sys_err("Error : send_func: faild reading from stdin.\n");
    }

    if(len == ERROR) //error
    {
            close_fd(socket);
            print_sys_err("send_func: error while reading from stdin.\n");
    }

    else if(len == 0) //done reading from stdin
    {
        if (shutdown(socket, SHUT_WR) < 0) //close writing end of socket
        {
            close_fd(socket);
            print_sys_err("send_func: can't send shutdown.\n");
        }
        return true;
    }


    if(tcp_send(socket, buffer, len, TCPLIB_GET_ALL) != len)
    {
        print_err("send_func: tcp_send failed.\n");
        close_fd(socket);
    }

    return false;
}

```

---

