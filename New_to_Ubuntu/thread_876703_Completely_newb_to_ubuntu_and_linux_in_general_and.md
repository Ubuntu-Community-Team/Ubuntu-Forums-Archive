---
title: "Completely newb to ubuntu and linux in general and have a question about Nvidia"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by astoroth88 on 2008-08-01
I have GeForce 9600 and I have downloaded the latest drivers from the main site. I ran the "sh NVIDIA-Linux-x86_64-171.06-pkg2.run" but my terminal says that it can't find the specified file.  Anyone feel like helping a newb out :lolflag:

---

### Post by perlluver on 2008-08-01
> **astoroth88 said:**
> I have GeForce 9600 and I have downloaded the latest drivers from the main site. I ran the "sh NVIDIA-Linux-x86_64-171.06-pkg2.run" but my terminal says that it can't find the specified file.  Anyone feel like helping a newb out :lolflag:

You could try the hardware drivers, under system, administration.  Or use envy-gtk it is available via synaptic.

---

### Post by Unanimated on 2008-08-01
EnvyNG. Automates the whole thing.

[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu")

---

### Post by NikoC on 2008-08-01
> **astoroth88 said:**
> I have GeForce 9600 and I have downloaded the latest drivers from the main site. I ran the "sh NVIDIA-Linux-x86_64-171.06-pkg2.run" but my terminal says that it can't find the specified file.  Anyone feel like helping a newb out :lolflag:

Where did you save the file?
e.g. Desktop
if you start a terminal, it does so in your home directory, so first you type
cd Desktop
With the 'ls' command you get a list of files in that dir, and the nvidia drivers should be there...
I don't think you can install the driver when you are in your desktop environment though!
So you should press ctrl + alt + f1 first.
Also the command should be run as sudo.

Cheers.

---

### Post by daberger on 2008-08-01
nvidia 8000 series has a bunch of problems with ubuntu ( or so im told since my parents wont let me install it on the good comp...) im not sure about the 9600 but you may have to get someblacklisted drivers. not that that relates to your question at all...

---

### Post by Bucky Ball on 2008-08-01
> nvidia-glx-new &#8212; The latest, greatest nvidia driver for the 8000 series of cards. Ubuntu may prompt you to add this during the install, which takes care of this for you.

From this website: [http://www.kevinbecker.net/blog/2007/11/01/ubuntu-710-post-install-guide/](http://www.kevinbecker.net/blog/2007/11/01/ubuntu-710-post-install-guide/)

Make sure you have ubuntu-restricted-extras installed. The following page shows you how (and a lot more) ... :)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

... and yes, what NicoC said when you are in the terminal; be in the right directory and use sudo for installs in there, eg:

> sudo apt-get install thenameofwhatyouareinstallinggoeshere

---

### Post by astoroth88 on 2008-08-01
Ok, I've tried all those methods mentioned and none worked for me, I must be doing something wrong naturally, but i followed instructions to the detail. I used the SUDO install command and I attached a screen shot of what happened. not a very good picture at all but basically i used the cd to change to my desktop and then used the sudo command and typed in the file name exactly as if i were to copy and paste and the terminal said it couldn't find the file.


I thank you for your help everyone. =D>

Oh and I'm using Fiesty Fiesta or what ever it's called (Ubuntu 7.04)

---

### Post by NikoC on 2008-08-01
Hmmz,
Just a few pointers:
1) sudo apt-get install software_name
only works for packages that are made available via the so called repositories (you might want to do some reading up on this)
2) you have downloaded a driver package from nvidia, ergo it will not work via the apt-get install method since it is not a package that is in the repositories
If you read the install instructions that are mentioned on the nvidia website you will see that the right installation command is the following (and I'm copy/pasting directly from their website here):
STEP 3: Install 
Type "sh NVIDIA-Linux-x86-173.14.12-pkg1.run" to install the driver
However if you run this command in a terminal you will get an error saying that x (display manager) is still active.

So what you do is:
1) press ctrl + alt + f1 ---> this will get you in command line interface
2) login (if necessary, not sure about this one) with your regular username and password
3) sudo /etc/init.d/gdm stop
this will stop the display manager
4) cd ~/Desktop
5) ls (to confirm that the file is actually there)
6) sudo sh NVIDIA-Linux-x86-173.14.12-pkg1.run
7) follow the installation steps

And most of all: first read a bit more here [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html]("http://www.nvidia.com/object/linux_display_ia32_173.14.12.html"), there are some good tips in step 3.

---

### Post by Bucky Ball on 2008-08-01
Thanks for the pointers NicoC ...

---

### Post by phidia on 2008-08-01
> **astoroth88 said:**
> I have GeForce 9600 and I have downloaded the latest drivers from the main site. I ran the "sh NVIDIA-Linux-x86_64-171.06-pkg2.run" but my terminal says that it can't find the specified file.  Anyone feel like helping a newb out :lolflag:

I didn't notice anyone else mention this but 1) that runfile you have listed is _not_ the latest NVIDIA driver 2) You have the 64 bit driver which is fine but are you using x86_64 Ubuntu?
I don't have a 9600 card but do have experience  with nvidia cards and have seen some reports of special configuring or at least problems setting that model up. [This thread]("http://ubuntuforums.org/showthread.php?t=863205&highlight=nvidia+9600") reflects that-there are other threads like that at the multimedia & video forum.

Added more: The latest driver for 64bit > Linux AMD64/EM64T
Latest Version: [173.14.12]("http://www.nvidia.com/object/linux_display_amd64_173.14.12.html")
(Inserted link to download)

---

