---
title: "Problem with POSIX, libc6 and pthread_timedjoin_np"
date: 2008-01-13
forum: Packaging and Compiling Programs
---

### Post by recon69 on 2008-01-13
Right, I'm trying to compile a app "peragro", the devs assure me that the problem is on my system. which is very likley :)

when i compile the app I get the error 

mec@ubuntu-mec:~/development/peragro/trunk$ jam
...found 729 target(s)...
...updating 11 target(s)...
C++ ./out/linuxx86/optimize/src/client/cursor.o
./src/client/entity/entity.h: In constructor ‘PT::Entity::Entity::Entity()’:
./src/client/entity/entity.h:129: warning: converting negative value ‘-0x00000000000000001’ to ‘unsigned int’
./src/common/util/thread.h: In member function ‘void Thread::kill()’:
./src/common/util/thread.h:83: error: ‘pthread_timedjoin_np’ was not declared in this scope


I am running dapper 6.06, using gcc 4.0.3 and have libc6 2.3.6 installed. I have a large mess of paths set up for the compiler which might have somthing to do with the problem. 

if anyone has any ideas what might be wrong plz enlighten me. I am happy to add any other info that might help fix my problem. 

thx in advance 
Recon

---

### Post by recon69 on 2008-01-13
Ok, from loking on the web for info I have found the following 

mec@ubuntu-mec:~/development/peragro/trunk$ uname -r
2.6.15-29-386
mec@ubuntu-mec:~/development/peragro/trunk$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.3.6

so I have NPTL installed, but it seams that maybe libc6 is not using it and i need to recompile libc6 with configuration option --enable-add-ons=nptl when configuring glibc 

now, I just have to figure out how to actual configure it and recompile it, also was wonder if this was a good idea as libc6 is a pritty important lib for the os and could have side effects. 

any comments? 

regards

---

