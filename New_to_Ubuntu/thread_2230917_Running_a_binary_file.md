---
title: "Running a binary file"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by ramTn on 2014-06-22
Hi everyone,

I recieved a file by email with no extension which is supposed to be the compiled version of a C++ code for linux.

The problem is that I am a beginner and I have absolutely no idea how to run this file and I also have limited access to the person who I recieved the file from. I already tried 
chmod +x ./pp  
./pp 
both on ubuntu 32bit and Cygwin64bit, but it gives me the error "-bash: ./pp: cannot execute binary file".

Here is the link to the file:
[https://www.dropbox.com/s/b9tmnrxwfj8bgup/pp](https://www.dropbox.com/s/b9tmnrxwfj8bgup/pp)

Would you please help me to figure out the issue and run this code?

Thank you in advance!

---

### Post by anakai on 2014-06-22
Have you tried using the bash before running it?
```
bash ./pp
``` 
or
```
sudo bash ./pp
```

*But I would not recommend you to run it with sudo if you don't know what it is. I would never trie a file like this without any information on what it is.*

---

### Post by Impavidus on 2014-06-22
It's normal for Linux executables to have no extension.

When I download the file and try and determine its file type, I get```
$ file pp
pp: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=8be990d19f360b4cc0b217a3732a290ec50ec297, not stripped
```So it's a 64 bit Linux executable. It won't run on 32 bit Linux systems. The 2.6.24 version number is no problem, I also get that when compiling code on my Trusty system. I don't know about Cygwin.

I'm not going to try and run this executable, as I don't know whether I can trust its source. But I think it should run on my system, provided all libraries are present. To find which libraries you need, I tried```
$ objdump -p pp | grep NEEDED
  NEEDED               libstdc++.so.6
  NEEDED               libm.so.6
  NEEDED               libgcc_s.so.1
  NEEDED               libc.so.6
```I think these are all standard libraries.

---

### Post by ramTn on 2014-06-22
Thank you very much guys for your respond! Your comments are really helpful.

> **anakai said:**
> Have you tried using the bash before running it?
```
bash ./pp
``` 
or
```
sudo bash ./pp
```

*But I would not recommend you to run it with sudo if you don't know what it is. I would never trie a file like this without any information on what it is.*

I actully trust the source but the problem is that my Cygwin64 does not recognize the command "sudo". I'm installing ubuntu 64x to try it.

> **Impavidus said:**
> It's normal for Linux executables to have no extension.

When I download the file and try and determine its file type, I get```
$ file pp
pp: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=8be990d19f360b4cc0b217a3732a290ec50ec297, not stripped
```So it's a 64 bit Linux executable. It won't run on 32 bit Linux systems. The 2.6.24 version number is no problem, I also get that when compiling code on my Trusty system. I don't know about Cygwin.

I'm not going to try and run this executable, as I don't know whether I can trust its source. But I think it should run on my system, provided all libraries are present. To find which libraries you need, I tried```
$ objdump -p pp | grep NEEDED
  NEEDED               libstdc++.so.6
  NEEDED               libm.so.6
  NEEDED               libgcc_s.so.1
  NEEDED               libc.so.6
```I think these are all standard libraries.

Sorry one more question, how can I make sure whether these four libraries are installed on my ubuntu? and if not, how can I install them?

UPDATE: It worked on ubuntu 64 bit! Thanks a lot!

---

### Post by oldos2er on 2014-06-22
Glad it worked! Would you please mark the thread as 'Solved' (under Thread Tools at the top of the page)? Thanks.

---

