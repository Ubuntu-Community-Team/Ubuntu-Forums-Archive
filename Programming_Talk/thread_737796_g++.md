---
title: "g++?"
date: 2008-03-27
forum: Programming Talk
---

### Post by rayj00 on 2008-03-27
I'm trying to compile a program. When I do the "make", I get the following response:

rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -ljrtp -o test \
                     SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp  
                      SipMessage.cpp SipUri.cpp util.cpp
make: g++: Command not found
make: *** [test] Error 127

I used Synaptic to install g++ but I cannot find the g++ command, even as sudo...

Ideas?

Thanks

Ray

---

### Post by mssever on 2008-03-27
```
sudo aptitude install build-essential
```

---

### Post by rayj00 on 2008-03-28
Ok...seems g++ was really g++-4.1 renamed it and advanced...a little.
The next error is:


rayj@Ubuntu-Pentest:~/Tools/SIP/SIP_Rogue/sip_rogue$ make
rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -ljrtp -o test \
           SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipUri.cpp test.cpp util.cpp 
./test || ( FT=$?; echo Failed $FT Tests; exit $FT )
./test: error while loading shared libraries: libjrtp-3.7.1.so: cannot open shared object file: No such file or directory
Failed 127 Tests
make: *** [test] Error 127

And I have this:
root@Ubuntu-Pentest:~# ls -l /usr/local/lib/libjrtp*
-rwxr-xr-x 1 root root 281970 2008-03-27 20:49 /usr/local/lib/libjrtp-3.7.1.so
-rw-r--r-- 1 root root 418936 2008-03-27 20:49 /usr/local/lib/libjrtp.a
-rwxr-xr-x 1 root root    800 2008-03-27 20:49 /usr/local/lib/libjrtp.la
lrwxrwxrwx 1 root root     16 2008-03-27 20:49 /usr/local/lib/libjrtp.so -> libjrtp-3.7.1.so

So, it looks like I have the correct libjrtp-3.7.1.so
The "make" just can't find it?

How do I fix this??

Thanks

Ray

---

### Post by lloyd_b on 2008-03-28
> **rayj00 said:**
> Ok...seems g++ was really g++-4.1 renamed it and advanced...a little.
The next error is:


rayj@Ubuntu-Pentest:~/Tools/SIP/SIP_Rogue/sip_rogue$ make
rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -ljrtp -o test \
           SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipUri.cpp test.cpp util.cpp 
./test || ( FT=$?; echo Failed $FT Tests; exit $FT )
./test: error while loading shared libraries: libjrtp-3.7.1.so: cannot open shared object file: No such file or directory
Failed 127 Tests
make: *** [test] Error 127

And I have this:
root@Ubuntu-Pentest:~# ls -l /usr/local/lib/libjrtp*
-rwxr-xr-x 1 root root 281970 2008-03-27 20:49 /usr/local/lib/libjrtp-3.7.1.so
-rw-r--r-- 1 root root 418936 2008-03-27 20:49 /usr/local/lib/libjrtp.a
-rwxr-xr-x 1 root root    800 2008-03-27 20:49 /usr/local/lib/libjrtp.la
lrwxrwxrwx 1 root root     16 2008-03-27 20:49 /usr/local/lib/libjrtp.so -> libjrtp-3.7.1.so

So, it looks like I have the correct libjrtp-3.7.1.so
The "make" just can't find it?

How do I fix this??

Thanks

Ray

Edit the file "Makefile" in that directory, and find out where it's defining "-ljrtp".  Add in "-L/usr/local/lib".

What's going on is that the "-ljrtp" option tells it that it will be linking against libjrtp.so, but it's defaulting to only searching "/lib"  and "/usr/lib", so it never sees that library in "/usr/local/lib".  The "-L..." directive adds "/usr/local/lib" to the list of directories to search for libraries.

Lloyd B.

---

### Post by rayj00 on 2008-03-28
**Here are the lines in the Makefile:**

sip_rogue$(EXE_SUFFIX): $(SIP_ROGUE_SOURCE_FILES) $(SIP_ROGUE_HEADER_FILES)^M
        $(CXX) $(CXXFLAGS) -I../g711conversions -L/usr/local/lib -lpthread -ljrtp -lpcap -lnet ../g711conversions/g711conversions.o -o sip_rogue$(EXE_SUFFIX) \^M
           $(SIP_ROGUE_SOURCE_FILES)^M
^M
test$(EXE_SUFFIX): $(TEST_SOURCE_FILES) $(TEST_HEADER_FILES)^M
        $(CXX) $(CXXFLAGS) -lpthread -L/usr/local/lib -ljrtp -o test$(EXE_SUFFIX) \^M
           $(TEST_SOURCE_FILES)^M
        ./test || ( FT=$$?; echo Failed $$FT Tests; exit $$FT )

**And the make output:**

rayj@Ubuntu-Pentest:~/Tools/SIP/SIP_Rogue/sip_rogue$ make
rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -L/usr/local/lib -ljrtp -o test \
           SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipUri.cpp test.cpp util.cpp 
./test || ( FT=$?; echo Failed $FT Tests; exit $FT )
./test: error while loading shared libraries: libjrtp-3.7.1.so: cannot open shared object file: No such file or directory
Failed 127 Tests
make: *** [test] Error 127

I appreciate your help on this...

Ray

---

### Post by lloyd_b on 2008-03-28
Hmmm...
 
Okay, I misunderstood the original problem.  The makefile is not only compiling "test", it's also running it.  The compile is successful, it's the run that's failing.

Question: Is the "libjrtp..." stuff something that you compiled?  I'm assuming so, as it's in the "/usr/local/lib" directory.

Try this - in a terminal window: "sudo ldconfig".  Then try running "make" again and see if it finds the library.

"ldconfig" updates some system info that tells the routine responsible for loading shared libraries where to find them.  If it hasn't been run since that library was compiled, this may be the problem.  

(Ideally, the "make install" for that library should have called ldconfig, but perhaps the Makefile for the library is missing that step).

Lloyd B.

---

### Post by rayj00 on 2008-03-28
After doing the lfconfig, I get the same error:

rayj@Ubuntu-Pentest:~/Tools/SIP/SIP_Rogue/sip_rogue$ make
rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -L/usr/local/lib -ljrtp -o test \
           SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipUri.cpp test.cpp util.cpp 
./test || ( FT=$?; echo Failed $FT Tests; exit $FT )
./test: error while loading shared libraries: libjrtp-3.7.1.so: cannot open shared object file: No such file or directory
Failed 127 Tests
make: *** [test] Error 127

And I did not compile the libjrtp. Should I?

---

### Post by lloyd_b on 2008-03-28
> **rayj00 said:**
> After doing the lfconfig, I get the same error:

And I did not compile the libjrtp. Should I?

"ifconfig"?  Was that a typo for "ldconfig"?

Where did those libraries come from?  You didn't compile them, and there's no package in the repos for libjrtp.

Personally, if I'm dealing with libraries that aren't available from the repos I prefer to compile them on my machine, that way I can be reasonably certain they're built and installed correctly.  That may or may not make a difference in this case.

Lloyd B.

---

### Post by rayj00 on 2008-03-28
Yes, typo...

And the libraries came with the program. I believe the program was developed under Red Hat.

If you are find yourself really bored with nothing to do, you can get the
source code here:

[http://www.hackingvoip.com/tools/sip_rogue.tar.gz](http://www.hackingvoip.com/tools/sip_rogue.tar.gz)

Rest assure that I am a not a hacker. I do pentesting for a living and my client is the government. I would be out of a really nice gig if I were caught doing something unethical or illegal.

Unfortunately I know just enough about programming to be dangerous. This is definitely one area that I will be improving on....

---

### Post by lloyd_b on 2008-03-28
> **rayj00 said:**
> Yes, typo...

And the libraries came with the program. I believe the program was developed under Red Hat.

If you are find yourself really bored with nothing to do, you can get the
source code here:

[http://www.hackingvoip.com/tools/sip_rogue.tar.gz](http://www.hackingvoip.com/tools/sip_rogue.tar.gz)

Rest assure that I am a not a hacker. I do pentesting for a living and my client is the government. I would be out of a really nice gig if I were caught doing something unethical or illegal.

Unfortunately I know just enough about programming to be dangerous. This is definitely one area that I will be improving on....

I downloaded and compiled it.  I *did* initially see that error about libjtrp.so, but once I ran ldconfig, it disappeared.  Now I"m getting a completely different error, that I don't understand.  Of course, the fact that my screen is filled with compiler warnings doesn't help much (these folks desperately need to clean up their code).

Ok - if I run "make test", it now reports "# Passed all tests", which means that I got it compiled correctly.

Could you post the contents of the file "/etc/ld.so.conf".  And if it's nothing but an "include...", please post the contents of the various files that are included.  Running "ldconfig" *should* have cleared up the problem - the fact that it didn't means that it's probably an issue with ldconfig's configuration.

Lloyd B.

---

### Post by rayj00 on 2008-03-28
rayj@Ubuntu-Pentest:/etc$ cat ld.so.conf
include /etc/ld.so.conf.d/*.conf
/usr/X11R6/lib
/opt/nessus/lib

rayj@Ubuntu-Pentest:/etc$ cd ld.so.conf.d
[email]rayj@Ubuntu-Pentest:/etc/ld.so.conf[/email].d$ ls
i486-linux-gnu
[email]rayj@Ubuntu-Pentest:/etc/ld.so.conf[/email].d$ ls -l
total 4
-rwxr-xr-x 1 root root 64 2006-10-10 07:33 i486-linux-gnu

---

### Post by lloyd_b on 2008-03-28
> **rayj00 said:**
> rayj@Ubuntu-Pentest:/etc$ cat ld.so.conf
include /etc/ld.so.conf.d/*.conf
/usr/X11R6/lib
/opt/nessus/lib

rayj@Ubuntu-Pentest:/etc$ cd ld.so.conf.d
[email]rayj@Ubuntu-Pentest:/etc/ld.so.conf[/email].d$ ls
i486-linux-gnu
[email]rayj@Ubuntu-Pentest:/etc/ld.so.conf[/email].d$ ls -l
total 4
-rwxr-xr-x 1 root root 64 2006-10-10 07:33 i486-linux-gnu

Bingo.  "ldconfig" hasn't been told to even look in "/usr/local/lib" for shared libraries.

Try adding "/usr/local/lib" to the end of "/etc/ld.so.conf" (note - you'll need a sudo or gksudo to edit this file), and then run "sudo ldconfig" again.  This should take care of this library error.

Lloyd B.

---

### Post by rayj00 on 2008-03-29
Yep.. That cleared a lot of errors. Now the only thing left is:

root@Ubuntu-Pentest:/home/rayj/Tools/SIP/SIP_Rogue/sip_rogue# make
rm -f test
g++ -ggdb -Wall -Wshadow -D_REENTRANT -lpthread -L/usr/local/lib/libjrtp -ljrtp -o test \
           SdpMessage.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipUri.cpp test.cpp util.cpp 
./test || ( FT=$?; echo Failed $FT Tests; exit $FT )
# Passed All Tests
g++ -ggdb -Wall -Wshadow -D_REENTRANT -I../g711conversions -L/usr/local/lib/libjrtp -lpthread -ljrtp -lpcap -lnet ../g711conversions/g711conversions.o -o sip_rogue \
           AttackAudio.cpp ControlMessage.cpp ControlPort.cpp hash.cpp main.cpp RtpHandler.cpp SdpMessage.cpp SipCall.cpp SipDispatcher.cpp SipEndPoint.cpp SipHeader.cpp SipIdentifier.cpp SipMessage.cpp SipProxyEndPoint.cpp SipRegistrarConnector.cpp SipRegistrar.cpp SipUdpPort.cpp SipUri.cpp util.cpp 
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
ControlMessage.h:44: error: extra qualification ‘ControlMessage::’ on member ‘ControlMessage’
ControlMessage.h:45: error: extra qualification ‘ControlMessage::’ on member ‘operator=’
make: *** [sip_rogue] Error 1

Ray

---

### Post by WW on 2008-03-29
That error looks familiar.  Check out [this thread](http://ubuntuforums.org/showthread.php?t=376650).

---

