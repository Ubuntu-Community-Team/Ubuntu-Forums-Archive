---
title: "HOWTO parallels workstation on UBUNTU INTREPID IBEX(linux HOST)"
date: 2008-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by terlmann on 2008-12-21
=HOWTO Install Parallels Workstation 2.0 on Ubuntu 8.10(Intrepid Ibex)====
===========Updated howto version 1.1 with all commands================
[COLOR="PaleGreen"]Stuff in green is commands executed by your machine[/COLOR]
[COLOR="Red"]Stuff in red represents actual work[/COLOR]

==SYSTEM SPEC===
> [COLOR="PaleGreen"]2.6.27-10-generic Linux kernel[/COLOR](you have to rerun parallels-config if you ever update this)
Minimum P3 Processor
Minimum 512 mb ram
Minimum 4 gigabytes free HD space
[COLOR="Red"]*A valid parallels testing or purchased license key*[/COLOR]
==INSTRUCTIONS==


Step 1:

Open a console in the directory where you plan to store every temporary file for this installation.


Step 2:

> 
[COLOR="PaleGreen"]sudo apt-get install build-essential libqt3-mt-dev[/COLOR]# This command will install all needed files from ubuntu repositories. If you don't have them, it should also pull in about 40 mb of xorg and kernel header files, along with a possible 100 mb in compilers and libraries for compilers :-P

Step 3:
[COLOR="Red"]
Go get a beer. This is going to take the rest of your morning.[/COLOR]

Step 4:

> [COLOR="PaleGreen"]sudo mv /bin/sh /bin/sh.old && sudo ln -s /bin/bash /bin/sh[/COLOR]#this command will duplicate a needed program for added shell functionality.


Step 5:

Download the following file to the working directory and double-click on it.
------------------------------------------------------------------------------------
[http://download.parallels.com/stuff/Parallels-2.2.2234-lin-en-parallels.deb](http://download.parallels.com/stuff/Parallels-2.2.2234-lin-en-parallels.deb)
--------------------------------------------------------------------------------------

Step 6 & 7:

Download this file to the working directory and run the command after it in the console.
-------------------------------------------------------------
[http://rapidshare.com/files/160879462/devel.tar.gz]("http://rapidshare.com/files/160879462/devel.tar.gz")
-------------------------------------------------------------
> [COLOR="PaleGreen"]sudo cp devel.tar.gz /usr/lib/parallels/devel.tar.gz[/COLOR]#this command will copy the needed file to the directory of the package to be installed.


Step 8 & 9:

Download
-----------------
[prlnet.c]("http://forum.parallels.com/attachment.php?attachmentid=434&d=1174660748")
-----------------
**[COLOR="Red"]#link requires you to be logged into parallels forum[/COLOR]**

> [COLOR="PaleGreen"]sudo cp prlnet.c /usr/lib/parallels/drivers/drv_net/linux/prlnet.c[/COLOR]#copies second needed file

Step 10 :
> [COLOR="PaleGreen"]sudo parallels-config[/COLOR]#builds files

==CONFIGURATION FINISHED==


==RUNTIME INSTRUCTIONS
Run parallels with
> [COLOR="PaleGreen"]sudo parallels[/COLOR]Set VM acceleration to "normal".
#Parallels will complain about "rtc" , ignore this, it is because ubuntu
doesn't have the realtime timer that parallels wants.

[COLOR="Red"]ATTENTION[/COLOR] : Parallels says "Cannot access hypervisor!"


Issue the following command from a tty if at all possible:
> [COLOR="PaleGreen"]cd /etc/lib/parallels/autostart/ && sudo ./quick_stop && sudo ./quick_start[/COLOR]#then rerun parallels using sudo parallels


Rock on DUDES!:guitar:

I reviewed this product at [http://uchiharules.wordpress.com/2008/12/21/parallels-desktop-for-linux-review/]("http://uchiharules.wordpress.com/2008/12/21/parallels-desktop-for-linux-review/")

---

### Post by terlmann on 2008-12-21
By all the power that is NOT within me(and I assure you that's almost all of it), I compel the forces of this digital world to apply the banner of stickyness to this thread(and possibly relocate it if necessary to a more ideal location.)

---

### Post by birddog165 on 2009-01-03
So why can't I just do the normal install using Parallels. Why all this hassle?

Edit: Sorry. I'm not trying to sound rude. I'm just curious because this is something I'm interested in.

---

### Post by jac0117 on 2009-01-10
So for step 9.  I have already downloaded prlnet.c.  When I type:
sudo cp prlnet.c /usr/lib/parallels/drivers/drv_net/linux/prlnet.c  

I get the following error:
cp: cannot create regular file `/usr/lib/parallels/drivers/drv_net/linux/prlnet.c': No such file or directory


What's wrong with this?

---

### Post by Robertjm on 2009-01-17
Every time there's a kernel update/change Parallel's Desktop throws a cow and refuses to run.

I'm going to have to try this tomorrow, when I've got the free morning. Thanks in advance for resolving a HUGE hole in my computing power that the people at Parallels don't seen to care about anymore.

(Now if we could just get to version 3 I'd be ecstatic!!).

Robert

----------------
> **birddog165 said:**
> So why can't I just do the normal install using Parallels. Why all this hassle?

Edit: Sorry. I'm not trying to sound rude. I'm just curious because this is something I'm interested in.

---

### Post by Robertjm on 2009-01-17
So I decided to go through the steps this afternoon, and it really didn't take as long as expected. Perhaps that was because I had a previous install (albeit one that didn't work).

I was so happy to see Parallels launch. HOWEVER, when I restarted my virtual machine it just sat there telling me to please wait and has been sitting on zero for a LOOONNNNGGGG time. Normally I'd kill the process and relaunch, but I'm a little nervous to do that with it being my virtual machine with all sorts of stuff I'd hate to lose.

Did you experience this too>?

Robert

---

### Post by Robertjm on 2009-01-18
This is really odd.

I was able to get Parallels working yesterday just fine. However, when I tried to start it this morning I got the "Cannot start Hypervisor" error message. 

When I tried you fix for it, my system told me it couldn't find quick_stop
I tried searching for quick_stop, but it's apparently nowhere on my system.

Thoughts?

Robert

---

### Post by gmatt on 2009-02-20
For those of you looking for 2 of the files devel.tar.gz and prlnet.c you can download them at [http://gara.matt.googlepages.com/parallels_howto_necessary_files.tar.gz](http://gara.matt.googlepages.com/parallels_howto_necessary_files.tar.gz)

I think that prlnet.c should be accessible without a login because the trial version is free and you can't possibly get the trial version to work without this file, so enjoy.

---

### Post by thenubsauce on 2009-06-01
so after everything works. I can delete the two files right?

---

### Post by yibbidy on 2009-07-09
> **Robertjm said:**
> This is really odd.

I was able to get Parallels working yesterday just fine. However, when I tried to start it this morning I got the "Cannot start Hypervisor" error message. 

I get this too since upgrading to 8.10.  I have found a workaround, but have no idea why it works.

Start Parallels Transporter.
Go as far as you can through the wizard to transfer an image from a physical computer (without actually transfering one).
Exit Transporter and start Parallels VM.  It should work now.
I don't get the hypervisor error until after the next reboot.

Hope this helps!

Shaun

---

### Post by ajay_greatz on 2009-07-19
I'm facing this problem 'Unable to communicate with hypervisor!'. Could anyone please help out.

---

### Post by ImpactIT on 2009-07-24
Me to... This thread was soo very helpful but I can't get paraells to run - "Unable to communicate with Hypervisor". It is on a client's machine so I need it woriking ASAP as I recomended Ubuntu and Paralles to them :( Help!! Otherwise it works great on Ubuntu 9.4!

---

