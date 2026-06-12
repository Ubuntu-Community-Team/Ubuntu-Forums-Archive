---
title: "To compile one or more programs together"
date: 2013-02-06
forum: Programming Talk
---

### Post by sanda199 on 2013-02-06
Hi everyone, I wanna compile one or more programs together at the same time. I used 

```
sudo make
```

Is it the right way to compile? I am using G++ compiler and ubuntu 11.10. Thanks a lot

---

### Post by ofnuts on 2013-02-06
The right way is to create  a makefile that tell make what it needs to do. This isn't that much complicated but explaining the whole process would be a very long post. Examples abound on the net
.
And no, there is no need to do "sudo make"... "make" is enough. If the result of your compile needs root privs to be installed/run, then do that part outside of the makefile. But I find it strange that someone who doesn't seem familiar at all with code compilation is writing code that requires root privildeges.

---

### Post by sanda199 on 2013-02-06
> **ofnuts said:**
> The right way is to create  a makefile that tell make what it needs to do. This isn't that much complicated but explaining the whole process would be a very long post. Examples abound on the net
.
And no, there is no need to do "sudo make"... "make" is enough. If the result of your compile needs root privs to be installed/run, then do that part outside of the makefile. But I find it strange that someone who doesn't seem familiar at all with code compilation is writing code that requires root privildeges.


So how can i compile all those programs together at the same time? What is the command line to do that? Thanks

---

### Post by r-senior on 2013-02-06
It might help if you explained a little more about what you are trying to do and where you got these programs from. Is it that you wrote them on Windows and are having problems compiling on Ubuntu, or is it that you've taken these programs from someone else and are just trying to compile them?

I think the forum is finding it difficult to understand that you have programs that are clearly beyond a beginner level but you are asking very basic questions that someone who had written and compiled "Hello World", would be able to answer.

It helps if you read the questions that people put to you carefully and try to answer them rather than adding a whole set of new questions. If English is not your first language, please ask for help.

Please also try to avoid multiple threads if they are all related because people who are willing to help you get confused by them all.

---

### Post by sanda199 on 2013-02-06
> **r-senior said:**
> It might help if you explained a little more about what you are trying to do and where you got these programs from. Is it that you wrote them on Windows and are having problems compiling on Ubuntu, or is it that you've taken these programs from someone else and are just trying to compile them?

I think the forum is finding it difficult to understand that you have programs that are clearly beyond a beginner level but you are asking very basic questions that someone who had written and compiled "Hello World", would be able to answer.

It helps if you read the questions that people put to you carefully and try to answer them rather than adding a whole set of new questions. If English is not your first language, please ask for help.

Please also try to avoid multiple threads if they are all related because people who are willing to help you get confused by them all.


Ok. Actually I m trying to connect my laptop and my robot with TCP/IP  socket programming. My robot also used ubuntu OS as well. My compiler to  compile my program and the rest of my robot programs is G++ compiler.  So after I wrote my program, I opened the directory which it is located  in terminal. And I used 

 	Code:
 	sudo su 
 for as a root user

after that I used 

 	Code:
 	sudo make 
    to make "Makefile" between my program and the rest of programs. I was ok until that. 

And after that I run my program like this 

 	Code:
 	./socket.o "172.16.22.8" 4547 
I got an error like 

```
bash: ./socket.o: cannot execute binary file
```


Is there anything wrong? pls kindly tell me. Since this morning I tried to solve that "cannot execute binary file" until now. Thanks

---

### Post by muteXe on 2013-02-06
I'll say it again:
why are you trying to run an object file?

Have a quick read of this:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html)

And i'm failry sure you dont need to use sudo either.

---

### Post by sanda199 on 2013-02-06
> **muteXe said:**
> I'll say it again:
why are you trying to run an object file?

Have a quick read of this:
[http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html)

And i'm failry sure you dont need to use sudo either.

I have told you. Last time I use that command and run it. It worked fine. So pls tell me how to run that program? It is not only one program. There are many programs which link together with my program.

---

### Post by sanda199 on 2013-02-06
Since I typed 
```
make
```

It automatically come out my socket.o file If I run like that 

```
./socket
```

error is like 
```
bash: ./socket: No such file or directory
```

if I run like this

```
./socket.o
```

I got error like 

```
bash: ./socket.o: cannot execute binary file
```


So how to solve it? Thanks

---

### Post by muteXe on 2013-02-06
after you've typed make, type 'ls -l' and paste the results here. in other words, let's have a look at what's produced after your make.

(they are all lower case L's in that command by the way).

---

### Post by sanda199 on 2013-02-06
After make, 
```
darwin@darwin:~$ cd ../../
darwin@darwin:/$ cd darwin/Linux/build 
darwin@darwin:/darwin/Linux/build$ sudo su 
[sudo] password for darwin: 
root@darwin:/darwin/Linux/build# sudo make 
ar cr ../lib/darwin.a ../../Framework/src/CM730.o ../../Framework/src/math/Matrix.o ../../Framework/src/math/Plane.o ../../Framework/src/math/Point.o ../../Framework/src/math/Vector.o ../../Framework/src/motion/JointData.o ../../Framework/src/motion/Kinematics.o ../../Framework/src/motion/MotionManager.o ../../Framework/src/motion/MotionStatus.o ../../Framework/src/motion/modules/Action.o ../../Framework/src/motion/modules/Head.o ../../Framework/src/motion/modules/Walking.o ../../Framework/src/vision/BallFollower.o ../../Framework/src/vision/BallTracker.o ../../Framework/src/vision/ColorFinder.o ../../Framework/src/vision/Image.o ../../Framework/src/vision/ImgProcess.o ../../Framework/src/minIni/minIni.o ../../Linux/build/socket.o streamer/httpd.o streamer/jpeg_utils.o streamer/mjpg_streamer.o LinuxActionScript.o LinuxCamera.o LinuxCM730.o LinuxMotionTimer.o LinuxNetwork.o
 
```

After ls -l 
```
 -rw-r--r-- 1 darwin darwin  2491 2013-01-14 09:01 1.jpeg
-rwxr-xr-x 1 darwin darwin  3784 2012-03-16 09:56 LinuxActionScript.cpp
-rwxr-xr-x 1 darwin darwin  5064 2012-03-16 09:57 LinuxActionScript.o
-rwxr-xr-x 1 darwin darwin 12719 2012-03-16 09:56 LinuxCamera.cpp
-rwxr-xr-x 1 darwin darwin 14760 2012-03-16 09:57 LinuxCamera.o
-rwxr-xr-x 1 darwin darwin  5388 2012-03-16 09:56 LinuxCM730.cpp
-rwxr-xr-x 1 darwin darwin  8744 2012-03-16 09:57 LinuxCM730.o
-rwxr-xr-x 1 darwin darwin  2330 2012-03-16 09:56 LinuxMotionTimer.cpp
-rwxr-xr-x 1 darwin darwin  3624 2012-03-16 09:57 LinuxMotionTimer.o
-rwxr-xr-x 1 darwin darwin  5498 2012-03-16 09:56 LinuxNetwork.cpp
-rwxr-xr-x 1 darwin darwin 17080 2012-03-16 09:57 LinuxNetwork.o
-rwxr-xr-x 1 darwin darwin  1861 2013-01-29 16:08 Makefile
-rw-r--r-- 1 darwin darwin  1861 2013-01-29 16:08 Makefile~
-rw-r--r-- 1 darwin darwin  2131 2013-01-29 14:16 socket1.cpp
-rw-r--r-- 1 darwin darwin  2131 2013-01-29 14:16 socket1.cpp~
-rwxr-xr-x 1 darwin darwin 13388 2013-01-29 14:24 socket1.o
-rwxr-xr-x 1 darwin darwin  3242 2013-02-06 08:40 socket.cpp
-rw-r--r-- 1 darwin darwin  3252 2013-02-06 08:39 socket.cpp~
-rwxr-xr-x 1 darwin darwin  2364 2013-02-06 16:29 socket.o
-rw-r--r-- 1 darwin darwin  3220 2013-02-04 17:26 socket_p.cpp
drwx------ 3 darwin darwin  4096 2013-02-05 08:20 streamer
drwxr-xr-x 2 darwin darwin  4096 2013-01-31 10:23 try
-rw-r--r-- 1 darwin darwin   188 2013-01-14 12:47 try.c
-rw-r--r-- 1 darwin darwin  1809 2013-01-14 11:32 try.h
-rwxr-xr-x 1 darwin darwin  8903 2013-01-15 07:37 try.o
   
```

---

### Post by muteXe on 2013-02-06
```

./socket

```

is not working because it isn't being created.  Are you sure this thing is compiling?

run make again like this
```

make &> results.txt

```

and then copy and paste here the contents of results.txt .

---

### Post by Tony Flury on 2013-02-06
> **sanda199 said:**
> I have told you. Last time I use that command and run it. It worked fine. So pls tell me how to run that program? It is not only one program. There are many programs which link together with my program.

Unless previously you remaned your executable to be a .o file (which is not a good idea but entirely possible), there is no way that you can run a .o file - it is an module object file, which is not an eecutable file.

A module object contains the compiled code from a single module (i.e. a single source code file).

It still needs to be linked against other moduled and libraries to create an executable files.

You have been provided some great links by some experts that tries to explain all of this.

---

