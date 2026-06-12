---
title: "permission denied error in socket programming in c"
date: 2013-02-05
forum: Programming Talk
---

### Post by sanda199 on 2013-02-05
Hi everyone,I got error when I run this program. I am using ubuntu 11.10.
This is my program. 

#include "socket.h"


using namespace Robot;



//int fileSEND(const char *server, int PORT, const char *lfile, const char *rfile)
//{
int main (int argc, char *argv[])
{	
	int socketDESC;
	struct sockaddr_in serverADDRESS;
	struct hostent *hostINFO;
	/*FILE *file_to_send;
	int ch;
	char toSEND[1];
	char remoteFILE[4096];
	int count1=1, count2=1, percent;
	char buffer[4096];*/
	
	int PORT;	
	Image *send_img;
	int length =4096;

	hostINFO = gethostbyname(argv[1]);
	
	if(hostINFO==NULL)
	{
		printf("Problem interpreting host\n");	
		return 1;
	}
	PORT = atoi(argv[2]);
	socketDESC = socket(AF_INET, SOCK_STREAM, 0);
	if(socketDESC<0)
	{
		printf("Cannot create socket\n");
		return 1;
	}
	
	serverADDRESS.sin_family = hostINFO->h_addrtype;
	memcpy((char *) &serverADDRESS.sin_addr.s_addr, hostINFO->h_addr_list[0],hostINFO->h_length);
	serverADDRESS.sin_port = htons(PORT);
	
	if(connect(socketDESC,(struct sockaddr *)&serverADDRESS,sizeof(serverADDRESS))<0)
	{
		printf("Cannot connect\n");
		return 1;
	}
	
	while(1)
	{
		LinuxCamera::GetInstance()->CaptureFrame();
		
		send_img=LinuxCamera::GetInstance()->fbuffer->m_RGBFrame;
		send(socketDESC,send_img, length,0);
	}
	close(socketDESC);
	return 0;
}
	
after i run, I got "permission denied"
Why is that so? If anyone knows  how tosolve it, pls kindly share me. thanks

---

### Post by r-senior on 2013-02-05
Is this C? If so, why is there a "using namespace" at the top and references to namespaces lower down?

How are you compiling this?

Could you edit your post and enclose the code in code tags? (See the # button in the toolbar above the post edit control, or manually wrap with code tags).

The more information you can provide, including a full error message, the more likely it is that someone will help.

---

### Post by sanda199 on 2013-02-05
```

#include "socket.h"


using namespace Robot;



//int fileSEND(const char *server, int PORT, const char *lfile, const char *rfile)
//{
int main (int argc, char *argv[])
{	
	int socketDESC;
	struct sockaddr_in serverADDRESS;
	struct hostent *hostINFO;
	/*FILE *file_to_send;
	int ch;
	char toSEND[1];
	char remoteFILE[4096];
	int count1=1, count2=1, percent;
	char buffer[4096];*/
	
	int PORT;	
	Image *send_img;
	int length =4096;

	hostINFO = gethostbyname(argv[1]);
	
	if(hostINFO==NULL)
	{
		printf("Problem interpreting host\n");	
		return 1;
	}
	PORT = atoi(argv[2]);
	socketDESC = socket(AF_INET, SOCK_STREAM, 0);
	if(socketDESC<0)
	{
		printf("Cannot create socket\n");
		return 1;
	}
	
	serverADDRESS.sin_family = hostINFO->h_addrtype;
	memcpy((char *) &serverADDRESS.sin_addr.s_addr, hostINFO->h_addr_list[0],hostINFO->h_length);
	serverADDRESS.sin_port = htons(PORT);
	
	if(connect(socketDESC,(struct sockaddr *)&serverADDRESS,sizeof(serverADDRESS))<0)
	{
		printf("Cannot connect\n");
		return 1;
	}
	
	while(1)
	{
		LinuxCamera::GetInstance()->CaptureFrame();
		
		send_img=LinuxCamera::GetInstance()->fbuffer->m_RGBFrame;
		send(socketDESC,send_img, length,0);
	}
	close(socketDESC);
	return 0;
}
```

---

### Post by sanda199 on 2013-02-05
I run my program like that

```
root@darwin# ./socket.o "172.15.112.3" 4455
```


and i got this error

```
bash: ./socket.o: Permission denied
```


I don't know how to solve that error. If anyone knows, pls help me. thanks millions.

---

### Post by muteXe on 2013-02-05
are you trying to run a .o file??
what command did you use to compile this?
and where are you running it from?

edit: and are you logged in as root?

---

### Post by sanda199 on 2013-02-05
> **muteXe said:**
> are you trying to run a .o file??
what command did you use to compile this?
and where are you running it from?

edit: and are you logged in as root?



The command that i use to run program is shown above. I save my program under file system. So I open my program like that first.

```
cd ../../
```

after that I run my program by using 

```
root@darwin# ./socket.o "172.17.111.7" 4547
```

---

### Post by Bachstelze on 2013-02-05
An object file is not an executable... Before writing complex programs, I suggest you actually learn how to compile a source file.

What's up with people wanting to run before they learn to walk, seriously...

---

### Post by sanda199 on 2013-02-05
> **Bachstelze said:**
> An object file is not an executable... Before writing complex programs, I suggest you actually learn how to compile a source file.

What's up with people wanting to run before they learn to walk, seriously...



I am not running before I don't know how to walk.Last time run like that command, I can run. This time I change the directory. I m using root user. If you said an object file is not an executable, why I can run last time?

---

### Post by spjackson on 2013-02-05
You have already been asked whether this is C++ and not C (as per the title). It is not valid C, even if socket.h contains magic macros such as
```

#define using

```
So I'll assume it is C++. It is not valid C++ unless socket.h includes lots of extra headers that are required for the library functions you call. So I'll assume it does.

Normally a .o file on Linux is an "object" file, i.e. the result of a compilation, not an executable which is the result of linking. You could call an executable socket.o if you want to but it's a bad idea and the error you are getting suggests that you haven't.

The following line would create the object file socket.o which would give you the error you are getting if you tried to run it.
```

g++ -c socket.c

```

The following line would create the executable socket which you could run as ./socket
```

g++ -o socket socket.c # extra include paths and libraries go here

```

---

### Post by 3rdalbum on 2013-02-05
> **Bachstelze said:**
> An object file is not an executable... Before writing complex programs, I suggest you actually learn how to compile a source file.


+1.

Also, before you can run a compiled program, you need to make it executable. You can either do this by right-clicking the file, going to Properties and the Permissions tab, and then clicking "Allow file to execute as a program" - or you can use the chmod command.

Without the execute permission, any attempt to run the file will result in "Permission Denied". But as Bachstelze said, you need to compile the file first, then add the execute permission, then you can run it.

---

### Post by muteXe on 2013-02-05
> **sanda199 said:**
> Last time run like that command, I can run.

Impossible :)

---

### Post by dwhitney67 on 2013-02-05
> **3rdalbum said:**
> +1.

Also, before you can run a compiled program, you need to make it executable. You can either do this by right-clicking the file, going to Properties and the Permissions tab, and then clicking "Allow file to execute as a program" - or you can use the chmod command.

Without the execute permission, any attempt to run the file will result in "Permission Denied". But as Bachstelze said, you need to compile the file first, then add the execute permission, then you can run it.

I'm sorry to call this out, but your information (albeit correct in spirit) is nonsense.

I've yet to see a case on a working Linux system, where one builds an application, that the resulting file does not already have the appropriate permissions set.

If of course you are building on a FAT32 or NTFS mount point, then your results may vary since this is not truly a Linux environment.

It has already been stated that generating an object file, followed by generating the executable file, should be sufficient.  A chmod (or right-clicking) on a file is NOT necessary.

In summary:
```

g++ -c socket.cpp

g++ -o socket socket.o

```

If the OP only has one file, then may I suggest merely doing the following:
```

make socket

```

---

### Post by sanda199 on 2013-02-05
> **3rdalbum said:**
> +1.

Also, before you can run a compiled program, you need to make it executable. You can either do this by right-clicking the file, going to Properties and the Permissions tab, and then clicking "Allow file to execute as a program" - or you can use the chmod command.

Without the execute permission, any attempt to run the file will result in "Permission Denied". But as Bachstelze said, you need to compile the file first, then add the execute permission, then you can run it.


Hi, firstly thanks for your answer. I tried to compile it again and appeared socket.o file. But the file icon is with lock. and I used 

```
ls -l
```


and it show like that

```
-rw-r--r-- 1 root root 2364 2013-02-06 8:29 socket.o
```


I used
```
chmod u+rwx socket.o
```

but still can't. I don't know how to solve it. thanks

---

### Post by sanda199 on 2013-02-05
> **dwhitney67 said:**
> I'm sorry to call this out, but your information (albeit correct in spirit) is nonsense.

I've yet to see a case on a working Linux system, where one builds an application, that the resulting file does not already have the appropriate permissions set.

If of course you are building on a FAT32 or NTFS mount point, then your results may vary since this is not truly a Linux environment.

It has already been stated that generating an object file, followed by generating the executable file, should be sufficient.  A chmod (or right-clicking) on a file is NOT necessary.

In summary:
```

g++ -c socket.cpp

g++ -o socket socket.o

```If the OP only has one file, then may I suggest merely doing the following:
```

make socket

```



If i use 

```
make socket
```

It will compile only one program. Coz I have 10 more programs to compile with my socket program.  I used 

```
sudo make
```

But my socket.o icon is with lock pattern. I don't know how to remove it away.

---

### Post by dwhitney67 on 2013-02-06
> **sanda199 said:**
> If i use 

```
make socket
```

It will compile only one program. Coz I have 10 more programs to compile with my socket program.  I used 

```
sudo make
```

But my socket.o icon is with lock pattern. I don't know how to remove it away.

You should be able to remove any file on your system, unless you do not have permissions to do it.

Using 'sudo' to build your user application is silly.  It is not necessary, and it exposes risk to corrupting your system should the products of your Makefile overwrite another system file.

I would suggest that you re-evaluate your knowledge of Linux and file permissions before you proceed any further with your application development.

Then take small steps in the development process.  Learn to build your application from the command line, and then when you appreciate the knowledge gained, then migrate to using a Makefile.  You should not have to use 'sudo' or have root-privileges to do any of this.

P.S.  Good developers on Linux only use the command line (or an IDE  :rolleyes: ).  Try to avoid using Nautilus to browse directories... that's so lame.

---

### Post by trent.josephsen on 2013-02-06
> **dwhitney67 said:**
> Then take small steps in the development process.  Learn to build your application from the command line, and then when you appreciate the knowledge gained, then migrate to using a Makefile.  **You should not have to use 'sudo' or have root-privileges to do any of this.**
Just wanted to stress this, emphasis mine. sudo is almost never the solution to your problem unless you are performing explicitly administrative tasks like installing packages or editing configuration files. Don't escalate your own privileges unless you *really* need to.

---

### Post by muteXe on 2013-02-06
Somebody should merge his/her 2 threads. They're converging onto the same subject.

---

