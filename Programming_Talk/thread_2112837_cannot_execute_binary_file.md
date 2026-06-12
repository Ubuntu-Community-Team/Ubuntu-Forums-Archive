---
title: "cannot execute binary file"
date: 2013-02-05
forum: Programming Talk
---

### Post by sanda199 on 2013-02-05
Hi experts, after I run below programs, I got and error like this 

```
bash: ./socket.o: cannot execute binary file
```

why is that so? thanks a lot :)


```
#include "socket.h"   using namespace Robot;    //int fileSEND(const char *server, int PORT, const char *lfile, const char *rfile) //{ int main (int argc, char *argv[]) {	 	int socketDESC; 	struct sockaddr_in serverADDRESS; 	struct hostent *hostINFO; 	/*FILE *file_to_send; 	int ch; 	char toSEND[1]; 	char remoteFILE[4096]; 	int count1=1, count2=1, percent; 	char buffer[4096];*/ 	 	int PORT;	 	Image *send_img; 	int length =4096;  	hostINFO = gethostbyname(argv[1]); 	 	if(hostINFO==NULL) 	{ 		printf("Problem interpreting host\n");	 		return 1; 	} 	PORT = atoi(argv[2]); 	socketDESC = socket(AF_INET, SOCK_STREAM, 0); 	if(socketDESC<0) 	{ 		printf("Cannot create socket\n"); 		return 1; 	} 	 	serverADDRESS.sin_family = hostINFO->h_addrtype; 	memcpy((char *) &serverADDRESS.sin_addr.s_addr, hostINFO->h_addr_list[0],hostINFO->h_length); 	serverADDRESS.sin_port = htons(PORT); 	 	if(connect(socketDESC,(struct sockaddr *)&serverADDRESS,sizeof(serverADDRESS))<0) 	{ 		printf("Cannot connect\n"); 		return 1; 	} 	 	while(1) 	{ 		LinuxCamera::GetInstance()->CaptureFrame(); 		 		send_img=LinuxCamera::GetInstance()->fbuffer->m_RGBFrame; 		send(socketDESC,send_img, length,0); 	} 	close(socketDESC); 	return 0; }
```

---

### Post by collisionystm on 2013-02-05
Silly question... but is the file marked as executable in the permissions?

---

### Post by steeldriver on 2013-02-05
If the executable bit isn't set, the error you should get is 'Permission denied'

More likely (especially since it's a **.o** file) it is object code - not a binary executable. You can check with the 'file' command:-

```
$ ls -l dostuff*
-rwxrwxr-x 1 user user 7202 Feb  6 02:12 dostuff
-rw-rw-r-- 1 user user  132 Jan 25 02:29 dostuff.c
-rw-rw-r-- 1 user user 1104 Feb  6 01:41 dostuff.o

``````

$ ./dostuff.o
-bash: ./dostuff.o: Permission denied
$
$ chmod +x dostuff.o
$ ./dostuff.o
-bash: ./dostuff.o: cannot execute binary file
$
$ file dostuff.o
dostuff.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
$
```An actual executable binary will show as something like

```
$ file dostuff
dostuff: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe6fb535859265b9b8cbf46c7b455c06ded7c7a2b, not stripped
$

```Since your source code appears to have an entry point ('main') you probably compiled it wrong (again as suggested by the .o suffix - you probably used the '-c' flag as well, which prevented linking into an executable)

---

### Post by sanda199 on 2013-02-05
> **collisionystm said:**
> Silly question... but is the file marked as executable in the permissions?


Yes it is executable in the permission.

---

### Post by sanda199 on 2013-02-05
> **steeldriver said:**
> If the executable bit isn't set, the error you should get is 'Permission denied'

More likely (especially since it's a **.o** file) it is object code - not a binary executable. You can check with the 'file' command:-

```
$ ls -l dostuff*
-rwxrwxr-x 1 user user 7202 Feb  6 02:12 dostuff
-rw-rw-r-- 1 user user  132 Jan 25 02:29 dostuff.c
-rw-rw-r-- 1 user user 1104 Feb  6 01:41 dostuff.o

``````

$ ./dostuff.o
-bash: ./dostuff.o: Permission denied
$
$ chmod +x dostuff.o
$ ./dostuff.o
-bash: ./dostuff.o: cannot execute binary file
$
$ file dostuff.o
dostuff.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
$
```An actual executable binary will show as something like

```
$ file dostuff
dostuff: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe6fb535859265b9b8cbf46c7b455c06ded7c7a2b, not stripped
$

```Since your source code appears to have an entry point ('main') you probably compiled it wrong (again as suggested by the .o suffix - you probably used the '-c' flag as well, which prevented linking into an executable)



Hi thanks for your answer. I typed 

```
file socket.o
```and it shows like that

```
socket.o: E;F 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
```If i typed 

```
ls -l
```
```
-rwxr--r-- 1 root root socket.o 
```
How to solve it? How can i change root to user? :(

---

### Post by sanda199 on 2013-02-05
> **steeldriver said:**
> If the executable bit isn't set, the error you should get is 'Permission denied'

More likely (especially since it's a **.o** file) it is object code - not a binary executable. You can check with the 'file' command:-

```
$ ls -l dostuff*
-rwxrwxr-x 1 user user 7202 Feb  6 02:12 dostuff
-rw-rw-r-- 1 user user  132 Jan 25 02:29 dostuff.c
-rw-rw-r-- 1 user user 1104 Feb  6 01:41 dostuff.o

``````

$ ./dostuff.o
-bash: ./dostuff.o: Permission denied
$
$ chmod +x dostuff.o
$ ./dostuff.o
-bash: ./dostuff.o: cannot execute binary file
$
$ file dostuff.o
dostuff.o: ELF 32-bit LSB relocatable, Intel 80386, version 1 (SYSV), not stripped
$
```An actual executable binary will show as something like

```
$ file dostuff
dostuff: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe6fb535859265b9b8cbf46c7b455c06ded7c7a2b, not stripped
$

```Since your source code appears to have an entry point ('main') you probably compiled it wrong (again as suggested by the .o suffix - you probably used the '-c' flag as well, which prevented linking into an executable)




The way I compile is that I used [HTML]sudo make[/HTML]coz I need to compile with other programs all together.

---

### Post by steeldriver on 2013-02-05
How about you take a step back and tell us exactly what you are trying to do here?

It appears from your other thread that you used 'sudo make' under the mistaken belief that 'sudo' would cause make to build multiple files. Instead it has caused root to own the resulting object file. Your best option at this point imo is to do

```
rm socket.o
```and then build everything properly *without* sudo but *with* the correct gcc command line(s) (or an appropriate Makefile) - if you tell us more about what you are trying to build we can help you figure that out

---

### Post by trent.josephsen on 2013-02-05
Just
```
rm socket.o
```
No need for root access to delete files in a directory you own.

---

### Post by sanda199 on 2013-02-05
> **steeldriver said:**
> How about you take a step back and tell us exactly what you are trying to do here?

It appears from your other thread that you used 'sudo make' under the mistaken belief that 'sudo' would cause make to build multiple files. Instead it has caused root to own the resulting object file. Your best option at this point imo is to do

```
sudo rm socket.o
```and then build everything properly *without* sudo but *with* the correct gcc command line(s) (or an appropriate Makefile) - if you tell us more about what you are trying to build we can help you figure that out


Ok. Actually I m trying to connect my laptop and my robot with TCP/IP socket programming. My robot also used ubuntu OS as well. My compiler to compile my program and the rest of my robot programs is G++ compiler. So after I wrote my program, I opened the directory which it is located in terminal. And I used 

```
sudo su
``` for as a root user

after that I used 

```
sudo make
```    to make "Makefile" between my program and the rest of programs. I was ok until that. 

And after that I run my program like this 

```
./socket.o "172.16.22.8" 4547
```

Cannot run. and i checked by using 
 ```
ls -l
```

It appeared like that 

```
-rwxr--r-- root root socket.o
```

My source program and the rest are like this

```
-rwxr--r-- darwin darwin socket.cpp
```

If my explanation makes you confused, pls tell me. Thanks :)

---

### Post by sanda199 on 2013-02-06
How to solve that "cannot executable binary file" error? Why had it appeared? Thanks

---

### Post by trent.josephsen on 2013-02-06
You still appear not to understand the difference between an object file and an executable. This is how you might go about compiling (from the command line) a project that had two source files:

```
$ ls
file1.c file2.c
$ gcc -c *.c
$ ls
file1.c file1.o file2.c file2.o
$ gcc file1.o file2.o
$ ls
file1.c file1.o file2.c file2.o a.out
$ ./a.out
```

The .o files are object files. They result from compiling the source files, which is what the first gcc command does. They may be linked together to create a binary, which is what the second gcc command does. They may also be linked together to create a static or shared library, which I am not doing in this example. Object files are not executable, even if they have a main() function. (The only executable in this example is called a.out, because I didn't choose a different name with -o.)

You compiled your source file, but you did not link it, so it wasn't an executable. You got a permission denied error because the object file wasn't marked executable -- which is where you made your second mistake: instead of finding out where you went wrong, you tried to fix it by using sudo. This obviously didn't work because the object file (regardless of permissions) still isn't an executable file.

Perhaps it would help if you described in a little bit more detail what you're trying to do. You said before that you're trying to compile several files, but you didn't mention whether you want to compile *several source files into one executable*, or *several sources into many executables*. If you're using a Makefile, post that too.

---

