---
title: "Installing BF2CC and Mono"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by TNE26 on 2008-04-29
Hi. I searched the forum for it but didn't find anything I could use.

The main reason why I installed Ubuntu, was to make an old pc that apparently didn't want to boot from one of my Winblows No eXPerience HDD's, so I decided to go with Ubuntu :)

I want to have a BF2 server running BF2CC for my LAN-parties so my gaming-laptop don't have to deal with it.

I got Ubuntu installed on one of my HDD's on 30 GB, figured I wont need more since I'll only use it for BF2, SAMBA- and webserver.

So, I installed the BF2 linux server without problems. Then I downloaded the mono 1.1.12.1 install for linux in .bin-format, but I have no clue how to install it. I read a lot about to type sudo +x ./filename.bin and so on, but i couldn't get it working.

**So here's my question:**
*1: *How do I install mono??
*2: *How do I run the BF2CC Daemon afterwards??
*3: *Is 2.00 GHz Pentium 4, 256 MB 133 MHz DDR-RAM, and a 30 GB HDD enough to run a server with 5-7 people?

---

### Post by Vadi on 2008-05-01
Are you sure mono is what you need? Mono is for compiling applications, not running them.

---

### Post by TNE26 on 2008-05-03
I think that I need mono, since the BF2CC website tells me so, but I'm not sure.

BF2CC is regretably using .NET, so I think I need mono (again, I'm a complete noob when it comes to linux..)

If you know another way of making .NET applications run on linux, please let me know :)

If you'd like to have a closer look at BF2CC, then visit [www.bf2cc.com](www.bf2cc.com). Under downloads it says

[QUOTE=BF2CC Website] BF2CC Version 1.4.2446: Released Sep 5, 2006

    * BF2CC GUI Client
      Download the BF2CC Client 1.4.2446
    * BF2CC Daemon (ModManager Scripts Included)
      Download the BF2CC Daemon 1.4.2446
    * ModManager Admin Scripts
      Download the ModManager Scripts 1.4
    * Linux Users must Install Mono
      Latest Tested Working version is v.1.1.12
      DO NOT USE Mono v.1.1.13 - it will Not work

The .NET Framework MUST be installed on your machine to run the Client or Daemon. Go to WindowsUpdate.Microsoft.com to install it. We recommend that you install ALL recommended updates and service packs from Windows Update.
The .NET Framework 2.0 Beta will NOT work. You can install either the normal 2.0 version or the 1.1 version with the 1.1 Service Pack. [/QUOTE]

---

### Post by Vadi on 2008-05-03
Ah yes.

The thing is that mono is already installed by default (tomboy, fspot need it). I checked in synaptic, it's version is 1.2.6, which should be good enough...

So if the BF not working as it is or?

(and, by the way, you can easily install a lot of programs from either Applications - Add/Remove, or System - Administration - Synaptic Package Manager)

---

### Post by TNE26 on 2008-05-06
The BF2 server works fine, but its BF2CC that i cant get working. By the way, the newest version of mono that can run BF2CC is 1.1.12.1

[QUOTE=BF2CC Website]* Linux Users must Install Mono
Latest Tested Working version is v.1.1.12
**DO NOT USE Mono v.1.1.13 - it will Not work**[/QUOTE]

But are you able to run downloaded .bin-files from Add/remove and synaptic?

And when i get mono installed, how do i run BF2CC with mono? Do i have to download .NET first, or is mono a replacement for .NET?

---

### Post by Vadi on 2008-05-06
Add/Remove / Synaptic download & install files from Ubuntu repositories (which are online servers). .bin files are on their own, and you can't run them with those. Mono is essentially an implementation of .NET on Linux, so once you get it installed, you shouldn't need to worry about it.

Try then opening the terminal, using "cd" to get to the directory with the bin, and then do "sudo ./*mono-1.1.12.1_0-installer.bin*" to run it.

---

### Post by TNE26 on 2008-05-07
Thanks, I'll try that. I haven't been with my Ubuntu computer since last Wednesday, so I haven't gotten a chance to try it out yet, but I'll look at it tonight :)

---

### Post by TNE26 on 2008-05-07
I tried the sudo thing on the file, it asked for password, I entered, but then nothing happened, just showed an empty line: server@server-pc:~$ (my user for the server is called "server" :) ) Then I tried downloading the file again, and did the same thing, but now it says: "sudo: ./mono-1.1.12.1_0-installer2.bin: command not found" which I don't understand since I entered the exact same thing except for the "2" in the end.

---

### Post by Vadi on 2008-05-07
Sometimes if you get a normal prompt right after, that means everything went okay.

And also if a script runs a command that's invalid, you'll get that message too - so that's what probably made the msg (not your command, but the scripts). Try BF now?

---

### Post by TNE26 on 2008-05-08
I'll try BF2CC now, but how do i initiate it? is it in the terminal? fx: "mono ./bf2ccd.exe" if im in the directory where bf2ccd is installed? I'll try that. Maybe that's wrong, but i just can't wait :D

Edit:

Well i tried that, and here's what i get (I know this must have been the wrong method, but maybe this could help):

server@server-pc:~$ cd BF2CC
server@server-pc:~/BF2CC$ mono bf2ccd.exe

** (bf2ccd.exe:6021): WARNING **: The following assembly referenced from /home/server/BF2CC/bf2ccd.exe could not be loaded:
     Assembly:   System.Data    (assemblyref_index=1)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/server/BF2CC/).


** (bf2ccd.exe:6021): WARNING **: Could not load file or assembly 'System.Data, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x8176370]
        mono [0x817699e]
        mono [0x8176a98]
        mono [0x8176f2d]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d5e050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1210816816 (LWP 6021)]
[New Thread -1220269168 (LWP 6023)]
[New Thread -1214518384 (LWP 6022)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1214518384 (LWP 6022)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220269168 (LWP 6023)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1210816816 (LWP 6021)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214518384 (LWP 6022)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ec39f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb79be3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220269168 (LWP 6023)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7ec0676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb792c1dc in ?? ()
#4  0xb792c1c4 in ?? ()
#5  0xb7ebe541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb792c1dc in ?? ()
#8  0xb792c1c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1210816816 (LWP 6021)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e142a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f33780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f33b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7c00844 in ?? ()
#6  0xb7c0082c in ?? ()
#7  0xb7c00828 in ?? ()
#8  0xb7c00824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)
server@server-pc:~/BF2CC$

---

### Post by Vadi on 2008-05-08
I have no idea now then. Time for you to google / ask on their forums :/

---

### Post by TNE26 on 2008-05-08
Okay.. Thanks for all of your help. But I don't know exactly what I'm doing wrong. I can't install/run soldat server (also bin). It justs give me another empty line, and is not shown when i type "ps x"

---

### Post by lijak on 2008-05-28
Hi,
I have exactly the same problem. But I have found out, that on ubuntu 8.04 64bit (server or desktop) and ubuntu 8.04 32bit server, installation of mono.bin doesnt work. BUT on ubuntu 8.04 32bit desktop, installation works without any problems (installation of mono appears on GUI).

---

### Post by TNE26 on 2008-06-04
huh? Strange.. but i have ubuntu 7.10 Desktop.. do you know if that 'll work? I also heard something about having to convert the files into a format ubuntu will read.. i mean from bin to some ubuntu executeable..

---

### Post by Vadi on 2008-06-04
Ubuntu doesn't rely on the filename extensions (.bin, .exe) as much as windows does. So a binary file doesn't have to have a .bin ending, it can have no ending at all. As long as its compiled for ubuntu it'll run properly.

---

### Post by TNE26 on 2008-06-07
thats the thing.. i dont think its compiled for ubuntu. Its made for linux in general, and i heard that the bin file has to be converted to .deb files to run (The file has .bin extension)

U might wanna try it out and see if you can do it.. i got it here: [http://ftp.novell.com/pub/mono/archive/1.1.12.1/download/](http://ftp.novell.com/pub/mono/archive/1.1.12.1/download/) and the direct D/L link: [http://ftp.novell.com/pub/mono/archive/1.1.12.1/linux-installer/0/mono-1.1.12.1_0-installer.bin](http://ftp.novell.com/pub/mono/archive/1.1.12.1/linux-installer/0/mono-1.1.12.1_0-installer.bin)

You can try running it (and installing it), and let me know if you can, and how :)

---

### Post by extremal on 2008-11-23
Have you tried running like 
```
mono bf2ccd.exe -showlog
```
:confused:

---

### Post by directhex on 2008-11-23
> **extremal said:**
> Have you tried running like 
```
mono bf2ccd.exe -showlog
```
:confused:

Yeah, that seems fine here

The "Client" on the other hand... not so much. It appears to be... bad. Missing assemblies I suspect. IPAddress.dll?

---

### Post by Coizado on 2010-04-03
Hi there,

I'm not sure you are still interested in a solution for this problem, since your post is almost 2 years old, but I thought I'd post anyways, so other people searching google would find the answer.

I came across the same problem on my Ubuntu 8.04 and 8.10 boxes, here is the way it works:

Before you begin, if you have apt-get any mono packages please:

```
dpkg --get-selections
```

Find all mono packages in the list and:

```
apt-get remove package-name
```

Then:

```
apt-get autoremove
```

If you box is a clean install:

Download Mono version 1.1.12.1:
```
wget http://ftp.novell.com/pub/mono/archive/1.1.12.1/linux-installer/0/mono-1.1.12.1_0-installer.bin
```

Give the file execution permission:

```
chmod +x mono-1.1.12.1_0-installer.bin
```

Execute the file (Just say yes to everything):
```
./mono-1.1.12.1_0-installer.bin
```

Reboot (It's not exactly needed but what can I say, I'm a windows user):
```
reboot
```

Now install the Develop pack in order to install the necessary libraries:
```
apt-get install mono-1.0-devel
```

Okay, now you are good to go.

To avid some random errors, I found out it works best if you are in the same folder as the .exe file:

```
cd /path_to_bf2/BF2CCD/
```

And I get weird errors if I'm not in the root account so:

```
sudo mono bf2ccd.exe
```

You probably gonna need the libstdc library to run the bf2 server itself, so:

```
apt-get install libstdc++5
```

Well, I hope this helps some internet searcher who's in the same problem, and I hope that if this solution works for you, you will register in the forum and post a small "Thank you" note, aren't you?

Best Regards folks,

Coizado.

---

