---
title: "Dynagen/Dynamips on Ubuntu"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Dani Filth on 2008-05-22
Hello folks,

I'm trying to run Dynagen/Dynamips on Ubuntu. If you don't know what that is, it is a simulator to Cisco routers & switches which act as the real Cisco routers & switches.

I follow some guides at :
[http://dynagen.org/tutorial.htm](http://dynagen.org/tutorial.htm)
[http://7200emu.hacki.at/viewtopic.php?t=5025](http://7200emu.hacki.at/viewtopic.php?t=5025)
[http://ubuntuforums.org/showthread.php?t=791768&highlight=dynagen](http://ubuntuforums.org/showthread.php?t=791768&highlight=dynagen)

But I ran into the problem after typing in "dynamips -H 7200 &", the problem is as following :
> dh@dh-laptop:~$ dynamips -H 7200 &
Cisco Router Simulation Platform (version 0.2.8-RC2-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: Nov 26 2007 06:40:51

[1] 16876
dh@dh-laptop:~$ ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
**Hypervisor: unable to create TCP sockets.**
Shutdown in progress...
Shutdown completed.

[1]+  Done                    dynamips -H 7200
dh@dh-laptop:~$ 


The bold text is where the problem occurs whilst it's not supposed to be.

For more details, I install it in an easy way (I simply search synaptic for "dynamips" & "dynagen" and install them) so I don't know which versions they are, and I don't know where is their folder (sorry for being a noob).

I have the standard Cisco IOS image with me, I config the simple1.net file as below :
> # Simple lab

[localhost]

    #[[7200]]
    #image = \Program Files\Dynamips\images\c7200-jk9o3s-mz.124-7a.image
    # On Linux / Unix use forward slashes:
    # image = /opt/7200-images/c7200-jk9o3s-mz.124-7a.image

    [[2691]]
    image = /opt/images/c2691-i-mz.123-12a.bin
    npe = npe-400
#    ram = 160
    ram = 100
        
    [[ROUTER R1]]
#    s1/0 = R2 s1/0
    
    [[router R2]]
    # No need to specify an adapter here, it is taken care of
    # by the interface specification under Router R1
This file leads the path to "/opt/images/IOSimage.bin" already. I mean everything went ok, except to that part above.

So, does anybody who has used Dynagen/Dynamips on Ubuntu before have a solution for this problem?

I'll be very grateful for any help, if you need more details, I'll try to give as possible.
Sorry for my bad English as well.

---

### Post by Dani Filth on 2008-05-22
Anyone?

---

### Post by Dani Filth on 2008-05-23
I removed the old ones and manually install them, now I'm able to detect the virtual routers, but when I try to either "telnet R1" or "putty -telnet -P 2000 R1", it returned an "segmentation fault" error.
(R1 is router 1 in this case)

I searched google for the solution and a site (which is temporary down atm, I guess) has a solution like :
> 
I get a segmentation fault (seen on Fedora Core and Redhat systems) 

The ExecShield protection must be disabled: 
/sbin/sysctl -w kernel.exec-shield=0
/sbin/sysctl -w kernel.randomize_va_space=0

or: 
echo 0 > /proc/sys/kernel/exec-shield
echo 0 > /proc/sys/kernel/randomize_va_space 

(thanks to Francisco Jesus Monserrat Coll for this information) 


If you have an AMD64 or an Intel with EM64T, you have to specify the "noexec=off" option to the Linux kernel boot command line (thanks to Yannick for this information).
This is a solution to fix the "segmentation fault" in Fedora which can be found [here](http://209.85.175.104/search?q=cache:3M3Yku97ITcJ:www.ipflow.utc.fr/index.php/Cisco_7200_Simulator_FAQ+Cisco_7200_Simulator_FAQ&hl=en&ct=clnk&cd=1) but it doesn't work in Ubuntu. 
When I tried that command it said that
> error: "kernel.exec-shield" is an unknown key
Does anyone know how to overcome this problem in Ubuntu, thanks in advance :popcorn:

---

### Post by Dani Filth on 2008-05-24
Please :(
I really want to get this work in Ubuntu, so that I can utterly get rid of XP from my PC :(

---

### Post by cyphur335 on 2008-05-25
I've run into that "cannot create TCP sockets" error as well before, it seems to be related to the socket you've selected to run Dynamips on (as noted in your dynamips command and in your .net file).  Do a "netstat -np | grep <port>" and check the status of the port.  If it's in "CLOSE_WAIT" then you'll have to somehow clear the port(I just reboot, if someone knows a better method please post it up!).  

As for the segmentation fault, what version of dynagen are you running? I can see from your posted info that you're running dynamips version 0.2.8-RC2-x86. 

Don't forget to head over to Hacki's forum and do a search in the Linux section.

---

### Post by Dani Filth on 2008-05-25
Hi cyphur335, thanks for replying :D

It seemed that the automatic installation was faulty, so I manually installed dynagen+dynamips as [this tutorial](http://7200emu.hacki.at/viewtopic.php?t=5025). So their versions are dynamips-0.2.8RC1-1.i386 and dynagen-0.10.1-1.noarch.

Plus, the IOS images should be ok because I copied them from my friend's Windows PC, which work well in his PC.

I'm able to "list" the R1 & R2, but when I "telnet R1", it gave me [the result](http://img143.imageshack.us/img143/7103/telnetr1yx9.jpg)
And stuck there forever. Not sure if there is anything wrong with my aforementioned "simple1.net" configuration.

As for "netstat -np | grep <port>", in this case, the port for R1 is 2000 (am I right?) and the result is Transmission is using port 2000.

---

### Post by cyphur335 on 2008-05-26
Not a problem! 

If Transmission is using port 2000, then you are going to have a conflict.  My suggestion would be change the port Transmission uses, or statically define the console ports for your virtual devices(using the **console = xxxx** command under each device definition using a unique port number for each).

Also, here are some errors in your sample .net you originally posted up.  Sorry I didn't catch these the first time around! 

> 
# Simple lab

[localhost]

#[[7200]]
#image = \Program Files\Dynamips\images\c7200-jk9o3s-mz.124-7a.image
# On Linux / Unix use forward slashes:
# image = /opt/7200-images/c7200-jk9o3s-mz.124-7a.image

[[2691]]
image = /opt/images/c2691-i-mz.123-12a.bin
**npe = npe-400**  *<-- remove that, the NPE is 7200 specific hardware *
# ram = 160
**ram = 100**  *<-- does that support your IOS image?  check Cisco.com for required RAM*

[[ROUTER R1]]
*_MISSING:_*** model = 2691**
# s1/0 = R2 s1/0

[[router R2]]
*_MISSING:_*** model = 2691**
# No need to specify an adapter here, it is taken care of
# by the interface specification under Router R1



Please make those corrections, clear up the port 2000 conflict, and post up the results!

---

### Post by itsnavee on 2009-12-08
you dont need to restart i guess. follow this:
# ps -ef | grep dynamips

then kill the dynamips process if u find any; use this command to kill the process
# kill -9 <process_id>

now check:
# netstat -ap | grep 7200

all should be clear. let me now ....

---

### Post by ubtsay on 2010-03-26
I am running into a problem with Dynamips on Ubuntu 9.10 X86_64. Any help is greatly appreciated!
Dynagen Version #0.11.0 
Dynamips Version#0.2.8-RC2-amd64
 
 
Here is the error message. 
dynagen -d /opt/dynamips/dynagen-0.11.0/sample_labs/simple1/simple1.net
Python version: 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1]
Reading configuration file...
  DEBUG: sending to localhost:7200 -> hypervisor version
  DEBUG: returned -> ['100-0.2.8-RC2-amd64']
  DEBUG: sending to localhost:7200 -> hypervisor reset
  DEBUG: returned -> ['100-OK']
  DEBUG: sending to localhost:7200 -> hypervisor working_dir "/opt/dynamips/dynagen-0.11.0/sample_labs/simple1"
  DEBUG: returned -> ['100-OK']
  DEBUG: sending to localhost:7200 -> c7200 create R1 0
[COLOR=red]*** Error: Unknown command 'create'[/COLOR]
See dynamips output for more info.
  DEBUG: sending to localhost:7200 -> hypervisor reset
  DEBUG: returned -> ['100-OK']
Press ENTER to continue

Here is .net file
# Simple lab
[localhost]
    [[7200]]
    #image = \Program Files\Dynamips\images\c7200-jk9o3s-mz.124-7a.image
    # On Linux / Unix use forward slashes:
    image = /opt/dynamips/images/c7200-jk9s-mz.124-25.bin
    npe = npe-400
    ram = 256
        
    [[ROUTER R1]]
    s1/0 = R2 s1/0
    
    [[router R2]]
    # No need to specify an adapter here, it is taken care of
    # by the interface specification under Router R1

---

