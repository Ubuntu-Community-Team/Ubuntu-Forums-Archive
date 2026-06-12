---
title: "Using VOCE"
date: 2012-02-05
forum: Packaging and Compiling Programs
---

### Post by roelforg on 2012-02-05
Hello,
 
I don't know if i should post here or in "Programming Talk",
but as it won't compile, i ask it here...
Right.
 
 
I wanna make my pc voice controlled,
i did the same thing on my win(tm) pc (i prefer windows, but my school mandates you have 1 windows pc, so i can't do much about it (other than multiboot/swapping hd's (preferred))).
I used VOCE (voce.sf.net) on windows (+ the c++ program i wrote to control the pc).
The problem is that VOCE needs to compile with -ljvm.
But i can't find that anywhere on my sys and i would like to avoid sun's bloated orig java.
I have both openjdk-6 and openjdk-7 installed.
I really want this to work because julius would be only alternative and it doesn't have an api.
I like VOCE the most because it has both tts and stt.
So i can have a conversation like this (note: my win pc does this already but on my linux i can do soooooooooooooo much more with it):
<ME> Computer
<PC> Yes?
<ME> Open disk tray
<ME> *puts DVD in drive*
<ME> Computer
<PC> Yes?
<ME> Close disk tray
<ME> Computer
<PC> Yes?
<ME> Play disk
<PC> *plays DVD*
<ME> *blown back in chair by Dolby intro (the one with super-bass)* :popcorn:
(did i mention my pc has a enormous 21.5" Full-HD Touchscreen and hooked up to DJ audio that's loud enough to be heard 2 houses over when on full power, while in my 2*1.5 meter large room?)
 
Note: I did get this working in windows without to much hassle (installing jdk takes time, ya know but after i changed the link-paths it worked).
 
I'd really like this to work.
 
Added bonus: My friend is a computer geek too... only he doesn't do programming, he does hw. Not that i don't do hw, i just don't have to much of it. I use the pc's at full cap with linux (pc: 256 mb mem, pIII cpu, boot time: 2m, take that windows).
 
PS. If anyone knows where to get some cheap SDRAM DIMM mem sticks (256mb or larger (currently at 2*128) for under €20 and without huge shipping fees to Europe, don't hasitate to say to (Amazon has the mem for 20 bucks, the shipping fee is 75 bucks, outright insane :mad:)!
 
Too much info maybe ?

---

### Post by roelforg on 2012-02-05
Nvm.
I just got a email from a forum member,
he said to add the following path to ld.so.conf and as link param:
/usr/lib/jvm/openjdk-6-jdk/jre/lib/i386/client and link with -ljvm
It worked!

---

### Post by mas644 on 2012-02-06
i was just trying to figure out the exact same thing, compiling voce on ubuntu using the c++ interface. i'm a little lost, could you post some details about the process (dependencies, build instructions for the sample programs). anything would be much appreciated.

UPDATE:
libjvm.so is located at a different location on my installation (11.04) at: 

 /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/amd64/jamvm/libjvm.so

i'm able to get my program to compile and link against this library. Of course the program won't run without having libjvm.so in the dynamic linker cache, so i've added the above path to ld.config, as well as the directory:

 /usr/lib/jvm/java-1.6.0-openjdk/jre/lib/amd64

which contains libjava.so. 

At this point, when I run the binary I compiled, I get an error:

 Error initialising natives: couldn't open libjava.so: use -verbose:jni for more information
 Error initialising VM (initialiseNatives)

Any explanations or magic emails from forum members would be much appreciated :) I'm a C/C++ guy rather than a Java guy, so a lot of this stuff about JDKs and JREs is a bit daunting. Still Googling around, but no dice :/

---

### Post by go_beep_yourself on 2012-05-09
This isn't voice recognition, but since you like that kind of software, I thought I should mention JSpeak.

[http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html](http://linuxinnovations.blogspot.com/2012/05/jspeak-ultimate-in-linux-text-to-speach.html)

---

