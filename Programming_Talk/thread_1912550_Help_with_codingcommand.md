---
title: "Help with coding/command"
date: 2012-01-20
forum: Programming Talk
---

### Post by geewhan on 2012-01-20
Hello everyone,
I am having some troubles with my code: server and client.
What my code does it takes a jpeg picture (lets say located on my ubuntu desktop) and sends it to the client where it creates a new jpeg, "test.jpeg". However I am having difficulty with my coding or the commends to have this done. I am new to writing network code so help is really appreciated.

```

------------server.cpp---------------
#include "serverInit.h"

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>

#include <unistd.h>//for sleep()
#include <iostream>
using std::cout;
using std::endl;
using std::fstream;
using std::ios;

#define MAX_PATH 256

void dostuff(int); /* function prototype */
//int UploadFile(char* PathofFile);
void error(const char *msg)
{
    perror(msg);
    exit(1);
}

int main(int argc, char *argv[])
{
     char PathofFile[MAX_PATH];
     int sConnect, sListen, portno, pid;
     socklen_t clilen;
     struct sockaddr_in serv_addr, cli_addr;

     if (argc < 2) {
         cout << "ERROR, no port provided" << endl;
	 //fprintf(stderr,"ERROR, no port provided\n");
         exit(1);
     }
     sConnect = socket(AF_INET, SOCK_STREAM, 0);
     sListen = socket(AF_INET, SOCK_STREAM, 0);

     if (sConnect < 0)
        error("ERROR opening socket");
     bzero((char *) &serv_addr, sizeof(serv_addr));
     portno = atoi(argv[1]);
     serv_addr.sin_family = AF_INET;
     serv_addr.sin_addr.s_addr = INADDR_ANY;
     serv_addr.sin_port = htons(portno);
     if (bind(sListen, (struct sockaddr *) &serv_addr,
              sizeof(serv_addr)) < 0)
              error("ERROR on binding");
     listen(sListen,SOMAXCONN);//5);
     clilen = sizeof(cli_addr);
     for(;; sleep(250))
     {
      if(sConnect = accept(sListen,
               (struct sockaddr *) &cli_addr, &clilen))
      {
	cout << "Connection Established!" << endl;

	gets(PathofFile);

	UploadFile(PathofFile);

	}

     }

  return 0;
}//End of Main


------serverInit.h---------


#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <fstream>
#include <iostream>
using std::cout;
using std::endl;
using std::ifstream;
int sConnect, sListen;
using std::ios;

int UploadFile(char* PathofFile)
{
	char* buffer;
	int size;

	ifstream file;

	file.open(PathofFile, ios::in | ios::binary | ios::ate);

	if(file.is_open())
	{
	file.seekg(0, ios::end);
	size = file.tellg();
	file.seekg(0, ios::beg);

	buffer = new char[size];

	file.read(buffer, size);

	send(sConnect, buffer, size, 0);

	file.close();	
	}

return 0;

}

--------client.cpp-------------
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <netdb.h>

#include <unistd.h>//for sleep()
#include <iostream>
#include <fstream>


using std::ofstream;
using std::cout;
using std::endl;
using std::ios;


void error(const char *msg)
{
    perror(msg);
    exit(0);
}

int main(int argc, char *argv[])
{
    int sConnect, portno, n;
    int WS, errorCode;
    char buffer[1000000];
    struct sockaddr_in serv_addr;
    struct hostent *server;

    //char buffer[256];
    if (argc < 3) {
       fprintf(stderr,"usage %s hostname port\n", argv[0]);
       exit(0);
    }
    portno = atoi(argv[2]);
    sConnect = socket(AF_INET, SOCK_STREAM, 0);
    if (sConnect < 0) 
        error("ERROR opening socket");
    server = gethostbyname(argv[1]);
    if (server == NULL) {
        cout << "ERROR, no such host" << endl;
        exit(0);
    }
    bzero((char *) &serv_addr, sizeof(serv_addr));
    serv_addr.sin_family = AF_INET;
    bcopy((char *)server->h_addr, 
         (char *)&serv_addr.sin_addr.s_addr,
         server->h_length);
    serv_addr.sin_port = htons(portno);


    for(;; sleep(250)){	
    	if (connect(sConnect,(struct sockaddr *) &serv_addr,sizeof(serv_addr)) < 0) 
        error("ERROR connecting");
    	if(errorCode != -1){//SOCKET_ERROR){
	WS = recv(sConnect, buffer, sizeof(buffer), 0);

	ofstream file;
	
	file.open("test.jpeg", ios::out | ios::binary | ios::ate);

	file.write(buffer, sizeof(buffer));

	file.close();	
	}

    }


return 0;

}//End of Main

```

---

### Post by sisco311 on 2012-01-20
Thread moved to **Programming Talk**.

---

### Post by geewhan on 2012-01-21
Can anyone tell me what I would write in the server terminal to send the jpeg file after the terminal prints out "Connected Established!"

If I run this in window (assuming I change this code to winsock) I would type the terminal:
C:\\Users\\user_name\\Desktop\\pic.jpeg

to send the jpeg file to the client folder.
I do not know how to do this in linux terminal.

Anyone have any suggestion?

---

### Post by Zugzwang on 2012-01-21
@OP: Perhaps you start by explaining what the problem is? You didn't actually say so yet.

---

### Post by Zugzwang on 2012-01-21
> **geewhan said:**
> Can anyone tell me what I would write in the server terminal to send the jpeg file after the terminal prints out "Connected Established!"

If I run this in window (assuming I change this code to winsock) I would type the terminal:
C:\\Users\\user_name\\Desktop\\pic.jpeg

to send the jpeg file to the server folder.
I do not know how to do this in linux terminal.



You would do precisely the same: write the path to the jpeg file into the terminal. For example, if you copied your jpeg-file to "/tmp/", you would write "/tmp/myexample.jpg<ENTER>".

The home directory of the user can be found in "/home/<USERNAME>/" in Linux.

The difference between file naming in Linux and Windows can be found here: [http://en.wikipedia.org/wiki/Path_%28computing%29](http://en.wikipedia.org/wiki/Path_%28computing%29)

---

### Post by geewhan on 2012-01-21
I have saved the jpeg file on my Desktop.

So I have done that before what you suggested
/home/<user_name>/Desktop/pic.jpeg

Unfortunately, this does not work.

If I may explain how I am running the terminals. I have two terminals: one for client and one for server.

server terminal commands:
g++ server.cpp
./a.out 2222
(waits for the client)

client terminal commands:
g++ client.cpp
./a.out 127.0.0.1 2222

server terminals commands:
prints out: "Connected Established!"

then I do in the server terminal after the "Connected Established!"
/home/<user_name>/Desktop/pic.jpg

Am I doing this incorrectly?

Thanks

---

### Post by Zugzwang on 2012-01-21
> **geewhan said:**
> 
then I do in the server terminal after the "Connected Established!"
/home/<user_name>/Desktop/pic.jpg

Am I doing this incorrectly?


Well, what happens if you typed this in the terminal?

---

### Post by geewhan on 2012-01-21
unfortunately 

nothing lol...

I thought I was writing it incorrectly because nothing happens.
I went to search for the jpeg file, and it doesn't exist.

Although once I end the terminal, the test.jpeg shows up in my client folder but broken.

I think that makes sense, since it seems that it does not receive my jpeg file which creates a broken jpeg file when the terminal ends.

---

### Post by Zugzwang on 2012-01-21
Nothing happens? Then it's time to exercise your debugging and error handling skills!

First of all, I've noted that you do not check all return values of the network functions that you call. In particular, the calls to "listen" or "send" might fail. Also, check the fail() flag of your "ifstream" to read the input file. Ensure that the user of your program is notified if any problem happened!

Then, you might want to consider trying to find out *where* your programs stops to work correctly. Either you learn how to use a debugger (though I have to admit, I always had problems with handling user input when using a debugger), or you enrich your program by some debugging output until you found the problem. Take the following code:

```

{
	cout << "Connection Established!" << endl;

	gets(PathofFile);

	UploadFile(PathofFile);

	}

```

Now add some hints to find out if the file name is detected correctly and "UploadFile" is actually called:

```

{
	cout << "Connection Established!" << endl;
	gets(PathofFile);
        cout << "Transmitting file: " << PathofFile << endl;
	UploadFile(PathofFile);
        cout << "File transmitted!" << endl;
}

```

---

