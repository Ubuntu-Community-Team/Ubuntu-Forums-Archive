---
title: "Compiling 32bit from 64bit Ubuntu(g++)"
date: 2009-04-14
forum: Programming Talk
---

### Post by Zer0d on 2009-04-14
I'm running Ubuntu 8.10 64bit. I want to compile c++ programs into 32bit using g++. By default g++ choose 64bit because I'm on a 64bit OS.

---

### Post by Krupski on 2009-04-14
> **Zer0d said:**
> I'm running Ubuntu 8.10 64bit. I want to compile c++ programs into 32bit using g++. By default g++ choose 64bit because I'm on a 64bit OS.

Add the command line switch "-m32". This will force the compiler to make a 32 bit executable.

---

### Post by Zer0d on 2009-04-14
Thank you for the answer, I've already tried the -m32 swith but all I get in output is this:
```

*@*:~/Desktop# g++ -m32 server.cpp -o server
In file included from /usr/include/features.h:354,
                 from /usr/include/string.h:26,
                 from server.cpp:22:
/usr/include/gnu/stubs.h:7:27: error: gnu/stubs-32.h: No such file or directory

```
Do I need some special library for this?

---

### Post by Zer0d on 2009-04-14
I installed ibc6-dev-i386 and tried to compile again, result is:

```

*@*:~/Desktop# g++ -m32 server.cpp -o server
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```

---

### Post by johnl on 2009-04-14
I also ran into this issue.  I was able to work around it by specifying which libstdc++ to link to:

```

g++ **-m32** -c main.cc -o main.o
g++ **-m32 -L/usr/lib32/ -lstdc++** main.o -o test


```

"file test":
> 
test: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped


---

### Post by Krupski on 2009-04-14
> **johnl said:**
> I also ran into this issue.  I was able to work around it by specifying which libstdc++ to link to:

```

g++ **-m32** -c main.cc -o main.o
g++ **-m32 -L/usr/lib32/ -lstdc++** main.o -o test


```

"file test":

Strange. All I installed is "build-essential" and "ia32-libs" and it worked. No special command line switches needed (except -m32 of course).

---

### Post by Zer0d on 2009-04-14
Thanks again for the replies =) It's kinda odd, I already have both build-essential and ia32-libs installed. I've tried compiling in different ways, the output's:

**g++ -m32 server.cpp -o server**:
```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```

**g++ -m32 -L/usr/lib32/ -lstdc++ server.cpp -o server**:
```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.so when searching for -lstdc++
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.3.2/libstdc++.a when searching for -lstdc++
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status

```

(Compiled without errors but won't run)** g++ -m32 -L/usr/lib32/ -lstdc++ -c server.cpp -o server**:
```

bash: ./server: cannot execute binary file

```

(Compiled without errors but won't run)** g++ -m32 -c server.cpp -o server**:
```

bash: ./server: cannot execute binary file

```


It will run just fine if I compile it to 64bit (**g++ server.cpp -o server**) but then the whole point is gone.

The example I compiled here is just a simple socket server. Here is the code if it has anything to do with the problem:
```

#include <string.h> // strlen, bzero
#include <stdlib.h> // exit
#include <arpa/inet.h> // sockaddr_in, AF_INET, SOCK_STREAM, socket, htons, INADDR_ANY
#include <iostream> // cout, endl

using namespace std;

int main()
{
	int sock, cli;
	struct sockaddr_in server, client;
	unsigned int len;
	char mesg[] = "1";
	int sent;
	
	if((sock = socket(AF_INET, SOCK_STREAM, 0)) == -1)
	{
		cout<<"Socket";
		exit(-1);
	}
	
	server.sin_family = AF_INET;
	server.sin_port = htons(10000);
	server.sin_addr.s_addr = INADDR_ANY;
	bzero(&server.sin_zero, 8);
	
	len = sizeof(struct sockaddr_in);
	
	if((bind(sock, (struct sockaddr*)&server, len)) == -1)
	{
		cout<<"Bind";
		exit(-1);
	}
	
	if((listen(sock, 5)) == -1)
	{
		cout<<"Listen";
		exit(-1);
	}
	
	while(1)
	{
		if((cli = accept(sock, (struct sockaddr*)&client, &len)) == -1)
		{
			cout<<"Accept";
			exit(-1);
		}
		sent = send(cli, mesg, strlen(mesg), 0);
		cout<<"Sent "<<sent<<" bytes to client: "<<inet_ntoa(client.sin_addr)<<endl;		
		close(cli);
	}
	return 0;
}

```

---

### Post by Krupski on 2009-04-14
> **Zer0d said:**
> Thanks again for the replies =) It's kinda odd, I already have both build-essential and ia32-libs installed. I've tried compiling in different ways, the output's:

**g++ -m32 server.cpp -o server**:


I just cut-n-pasted your code into "server.cpp", then ran your command line exactly:



```

root@michael:~/c-progs# g++ -m32 server.cpp -o server
root@michael:~/c-progs# ls -laF server
-rwxr-xr-x 1 root root 10141 2009-04-14 20:15 server*
root@michael:~/c-progs# 

```

It compiled - no errors and produced a 10K executable.

I don't know how to test if it works though... the only part I tried was to run it in two different terminals at once. The first one runs, the second one exits with the message "Bind" as I would expect from reading the code.

-- Roger

---

### Post by Zer0d on 2009-04-15
> **Krupski said:**
> I just cut-n-pasted your code into "server.cpp", then ran your command line exactly:



```

root@michael:~/c-progs# g++ -m32 server.cpp -o server
root@michael:~/c-progs# ls -laF server
-rwxr-xr-x 1 root root 10141 2009-04-14 20:15 server*
root@michael:~/c-progs# 

```

It compiled - no errors and produced a 10K executable.

I don't know how to test if it works though... the only part I tried was to run it in two different terminals at once. The first one runs, the second one exits with the message "Bind" as I would expect from reading the code.

-- Roger

What happens if you compile it this way:
**g++ -m32 -L/usr/lib32/ -lstdc++ server.cpp -o server**
Does that also work for you?

The program only act as a "server" and is running at port 10000. You can't have two programs running at same port thats why you got the "bind" message :) Even getting "error" message "bind" shows that it compiled successful for you.

---

### Post by Krupski on 2009-04-15
> **Zer0d said:**
> What happens if you compile it this way:
**g++ -m32 -L/usr/lib32/ -lstdc++ server.cpp -o server**
Does that also work for you?

The program only act as a "server" and is running at port 10000. You can't have two programs running at same port thats why you got the "bind" message :) Even getting "error" message "bind" shows that it compiled successful for you.

Same thing... it compiles with no error, and trying to run a second instance produces the "bind" message.

```

root@michael:~/c-progs# g++ -m32 -L/usr/lib32/ -lstdc++ server.cpp -o server
root@michael:~/c-progs# ./server 
^C
root@michael:~/c-progs# 

```

From the other terminal:

```

root@michael:~/c-progs# ./server 
Bindroot@michael:~/c-progs# 

```

[IMG]http://www.gunsnet.net/forums/images/smilies/oh.gif[/IMG]

---

### Post by johnl on 2009-04-15
Hi, unfortunately I don't have too much more advice for you :(

```

g++ [various flags] -c server.cpp -o server

```

The reason you can't run the result is because you are not creating an executable.  "-c" means compile the file into an object file (.o).  You would need a second link to link it into an executable (as I posted above).

I would check that you have a 32-bit libstdc++:

```

find /usr/lib32 -name "libstdc++.so*"

```

You should have a /usr/lib32/libstdc++.so that is a symlink to a libstdc++.so.x.y.z

On my system this file is part of the package 'lib32stdc++6'.  Give installing that package a shot.  You might also need 'lib32gcc1'.

---

### Post by Krupski on 2009-04-15
> **Zer0d said:**
> What happens if you compile it this way:
**g++ -m32 -L/usr/lib32/ -lstdc++ server.cpp -o server**
Does that also work for you?

The program only act as a "server" and is running at port 10000. You can't have two programs running at same port thats why you got the "bind" message :) Even getting "error" message "bind" shows that it compiled successful for you.

I just looked at my list of "stuff to add to a new install" and noticed I have a few other things in there... maybe this is the key to your problem.

```

apt-get -V install [COLOR="Red"]**g++-4.3-multilib**[/COLOR]
apt-get -V install [COLOR="Red"]**g++-multilib**[/COLOR]

```

---

### Post by Zer0d on 2009-04-18
Thanks for the replies =)

Result from running **find /usr/lib32 -name "libstdc++.so***":
```

/usr/lib32/libstdc++.so.6.0.10
/usr/lib32/libstdc++.so.5
/usr/lib32/libstdc++.so.6
/usr/lib32/libstdc++.so.5.0.7

```

I have **g++-4.3-multilib**, **g++-multilib** and **lib32stdc++6** but still it won't compile right:

**g++ -m32 -L/usr/lib32/ -lstdc++ -c HelloServer.cpp -o HelloServer32**
```

*@*:~/Desktop# ./HelloServer32 
bash: ./HelloServer32: cannot execute binary file

```

**g++ -m32 -c HelloServer.cpp -o HelloServer32**
```

*@*:~/Desktop# ./HelloServer32 
bash: ./HelloServer32: cannot execute binary file

```

---

