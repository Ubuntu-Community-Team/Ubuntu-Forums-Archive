---
title: "Installing Nvidia driver w/o operating system"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by dslax27 on 2008-06-04
Hello,
Super noob here. Here's the deal:

[LIST]
[*]PC with Nvidia graphics card
[*]No operating system
[*]Ubuntu boot cd v8.04 i386
[*]After I choose to install, I get the white screen of death described [on this thread]("http://ubuntuforums.org/showthread.php?t=785001")
[*]The above thread suggests to install [this driver]("http://www.nvnews.net/vbulletin/showthread.php?t=102509")
[/LIST]

**Ultimate question:**
How do I install a driver without first having a working operating system? :(

---

### Post by Cypher on 2008-06-04
Install Ubuntu using the Alternate CD which uses a text-based installer which will work on any video card/monitor. Once you've gotten Ubuntu installed, follow the thread about the driver installation and you should be able to get Gnome/KDE working..

---

### Post by dslax27 on 2008-06-04
Ok one last question filled with noobness that you'll probably throw up:

Where do I get the Alternate CD? If I already have it because it is part of the normal cd, how do I access the "alternate cd" portion?

Thank you so much!

---

### Post by tgrimley on 2008-06-04
They're different: [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

Check the box at the bottom of the page.

Also, you could try installing with your cd, and then install the driver from command line by ALT+CTRL+F1.

---

### Post by dslax27 on 2008-06-05
At what point hit alt-ctrl-F1?

---

### Post by tgrimley on 2008-06-05
Well I don't know this bug well, but I assume that you boot, it loads X/GNOME, whatever, and it turns white.  So once it's there you can switch to a terminal then.

---

### Post by dslax27 on 2008-06-05
Ok, I see the text version now.

It states ```
[Myuser]@[Mylogin}:~$_
```

...now what? Do I just pop in the driver cd? How will it know how to run the driver?

---

### Post by ardvark71 on 2008-06-05
> **dslax27 said:**
> Ok one last question filled with noobness that you'll probably throw up:


Hi...

Don't worry about what others think of your experience level, we all start from the beginning. ;)

Best Regards...

---

### Post by dslax27 on 2008-06-05
Hah thanks! Do you know what I should do though? Can anyone help me with my question below?

> **dslax27 said:**
> Ok, I see the text version now.

It states ```
[Myuser]@[Mylogin}:~$_
```

...now what? Do I just pop in the driver cd? How will it know how to run the driver?

---

### Post by eriqjaffe on 2008-06-05
> **dslax27 said:**
> Hah thanks! Do you know what I should do though? Can anyone help me with my question below?If your driver CD came with the video card, the chances of it having Linux drivers are pretty slim.

From a command prompt, EnvyNG is probably the way to go.

```
sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t
```

That should let you choose which nVidia driver you want and install it for you.  Mind you, I've never used the "text" interface for EnvyNG, but it should do the trick.

---

### Post by tgrimley on 2008-06-05
If you wanted to install the driver listed in the original post you can do 

```

wget http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run
sudo sh ./NVIDIA-Linux-x86-169.04-pkg1.run

```
and it should wget (download) and then run the installer

Also, if you want, you can do the wget'ing using a remote shell from another computer so you can cut and paste the url (assuming you have an ssh daemon running, which I don't believe is the default under ubuntu...).

---

### Post by dslax27 on 2008-06-05
Could I tell Ubuntu to read a CD with "NVIDIA-Linux-x86-169.04-pkg1.run" instead of the URL since my Ubuntu  is not connected to the Internet?

> **tgrimley said:**
> If you wanted to install the driver listed in the original post you can do 

```

wget http://us.download.nvidia.com/XFree86/Linux-x86/169.04/NVIDIA-Linux-x86-169.04-pkg1.run
sudo sh ./NVIDIA-Linux-x86-169.04-pkg1.run

```
and it should wget (download) and then run the installer

Also, if you want, you can do the wget'ing using a remote shell from another computer so you can cut and paste the url (assuming you have an ssh daemon running, which I don't believe is the default under ubuntu...).

---

### Post by dslax27 on 2008-06-05
Haha did I stump everybody?

---

### Post by eriqjaffe on 2008-06-05
> **dslax27 said:**
> Could I tell Ubuntu to read a CD with "NVIDIA-Linux-x86-169.04-pkg1.run" instead of the URL since my Ubuntu  is not connected to the Internet?You should be able to.

```
sudo sh ./path/to/cd/folder/NVIDIA-Linux-x86-169.04-pkg1.run
```

shouldn't be a problem.  You may need to mount the CD manually first, though.

---

### Post by dslax27 on 2008-06-06
Oh geez. I thought installing Ubuntu was supposed to be easy!

1. Well, how do I mount the CD manually? Remember, I do not have a Linux background, only a hatred for Windows haha! 

2. Also, I don't know how paths work in Ubuntu, so what does a typical path to my cd drive look like?

Thanks! I'm confident I am going to get this

---

### Post by eriqjaffe on 2008-06-06
Well, it's possible it's mounting automatically.

To manually mount the CD (IIRC):

Check to see if /media/cdrom exists.  If not, create it:

```
sudo mkdir /media/cdrom
```

Then mount the CD-ROM

```
sudo mount /dev/scd0 /media/cdrom
```

If that worked the way I *think* it will, the CD will then be at /media/cdrom.

Then it's just a matter of...

```
sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run
```

Obviously, "/path/to/" needs to reflect the actual path.  You can also navigate directly to the folder the driver is in via the "cd" command:

```
cd /media/cdrom
cd directory
cd otherdirectory

```

Which would put you in /media/cdrom/directory/otherdirectory

Then just run "sudo sh ./NVIDIA-Linux-x86-169.04-pkg1.run" as seen above.

---

### Post by tgrimley on 2008-06-06
Before trying to manually mount the CD-ROM, I'd do

```

ls /media/cdrom
ls /media/cdrom0
ls /media/cdrom1

```
etc 

If there is no output, then it's an empty mount point (your CD-ROM isn't mounted) and you can try and mount manually.  I'd imagine since you just switched to terminal after gnome loaded (the white screen) then it will automount in the background.  Worth a shot anyway.

---

### Post by dslax27 on 2008-06-08
> **eriqjaffe said:**
> Well, it's possible it's mounting automatically.

To manually mount the CD (IIRC):

Check to see if /media/cdrom exists.  If not, create it:

```
sudo mkdir /media/cdrom
```


[COLOR="Red"]I entered the above and I got "mkdir: cannot create directory '/media/cdrom' : File Exists"[/COLOR]

> **eriqjaffe said:**
> 
Then mount the CD-ROM

```
sudo mount /dev/scd0 /media/cdrom
```

If that worked the way I *think* it will, the CD will then be at /media/cdrom.


[COLOR="Red"]I presume I don't need to do the above since the "File Exists," right?[/COLOR]

> **eriqjaffe said:**
> 
Then it's just a matter of...

```
sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run
```

Obviously, "/path/to/" needs to reflect the actual path.  You can also navigate directly to the folder the driver is in via the "cd" command:

```
cd /media/cdrom
```


[COLOR="Red"]After "root@username:" I typed "cd /media/cdrom" and the next line outputs "root@username:/media/cdrom#"

I burned the CD using Windows XP with NVIDIA-Linux-x86-169.04-pkg1.run as its only file. No directories exist on the CD. It is just that this one file.

After "root@username:/media/cdrom#:" I typed "sudo sh ./NVIDIA-Linux-x86-169.04-pkg1.run" and it reads that it can't open my command.[/COLOR]

> **eriqjaffe said:**
> 
```

cd directory
cd otherdirectory

```

Which would put you in /media/cdrom/directory/otherdirectory

Then just run "sudo sh ./NVIDIA-Linux-x86-169.04-pkg1.run" as seen above.

[COLOR="Red"]There are no directories (folders) on my cd, just that one "/NVIDIA-Linux-x86-169.04-pkg1.run" file on the default directory. Do I need to use the above quote in any way?

**I think I'm close, but Linux does not recognize either my cd or the file on my cd. Any ideas? Your help is sincerely appreciated**[/COLOR]

---

### Post by dslax27 on 2008-06-08
T

---

### Post by tgrimley on 2008-06-08
I'm glad you're sticking with it!

What I would do is 
```

mv /media/cdrom/NVIDIA-Linux-x86-169.04-pkg1.run ~/

```
which will move the file from the cd to your home directory ~/ is shorthand for home, and you can type it just like that on the command line.

Then, I think you might need to change the permissions of the file to mark it as an executable.  You can do that by
```

chmod +x ~/NVIDIA-Linux-x86-169.04-pkg1.run

```

Then I'd try
```

sudo sh ~/NVIDIA-Linux-x86-169.04-pkg1.run

```

Hope that helps.  I'll keep checking on this thread :)

p.s. I'm not sure what you mean by After "root@username:" ... typically it's user@hostname.  I also noticed you said you were typing at a # prompt which indicates root.  You don't need to run as root to do these things, just run sudo before a command you need to run as root.

---

### Post by dslax27 on 2008-06-08
None of the above worked. Here are some things to note (perhaps one of my below actions are causing the problem)

I downloaded version 8.04, text version (since my video card is the problem)

When the Ubuntu 8.04 text version boots I get the following options:

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)


I've been chosing the recovery mode because when I choose the non-recovery mode, the graphics card tries to start and I get the white screen of death

After I select recovery mode, I get the following three options:

Recovery Menu:
1. resume normal boot [If I chose this, the white screen of death appears]
2. Drop to root shell prompt
3. Try to fix X server

Then I choose the root option because it gives me a commmand prompt. I've been typing all of the commands from this thread into there. Is this the wrong place to do this?

When I choose root i get the following before the cursor: "root@myname:/#_"

Is this the correct place for me to be typing in the suggested commands from the other posts in this thread? If not, how do I get there? Thanks!

---

### Post by tgrimley on 2008-06-08
I don't see why that method would be causing problems... but I don't know exactly what single user mode does other than log you in as root.

I would suggest letting it boot normally and doing CTRL+ALT+F1 to get to a terminal so that when you put in the CD Gnome will auto mount it in the background.. but that's not the classiest approach :)

When you do 
```
ls /media/cdrom/
``` did it list the .run file?  If so, what happens when you do ```
mv /media/cdrom/NVIDIA-Linux-x86-169.04-pkg1.run ~/
```

Do you see the installer when you ```
ls ~/
```?

---

### Post by dslax27 on 2008-06-09
Aha! When/where do I press CTRL+ALT+F1?

---

### Post by tgrimley on 2008-06-09
> **tgrimley said:**
> Well I don't know this bug well, but I assume that you boot, it loads X/GNOME, whatever, and it turns white.  So once it's there you can switch to a terminal then.

> **dslax27 said:**
> Aha! When/where do I press CTRL+ALT+F1?

From what I remember about this bug.. it's just a display thing and everything is running fine underneath.. so you should be able to kick back to a tty terminal

---

### Post by dslax27 on 2008-06-11
SUCCESS! Well - sort of. 

I got the CD to run using CTRL+ALT+F1 and "sudo mount /dev/scd0 /media/cdrom" and then "sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run"

Sweet.

Then the cd loads and I get this message: 
> You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux Driver download page at [www.nvidia.com](www.nvidia.com)

I hit "OK" and then the screen blacks out.


- [Here]("http://www.nvidia.com/object/linux_display_x86_96.43.05.html") is the NVIDIA support page referenced above for my GeForce4 4200 card.
- [Here ]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt")is the README file referenced above

Maybe I'm not reading the README carefully enough, but I can't seem to find out how to start up in X mode. It's probably because NVIDIA wrote their README for the general Linux audience, but not for Ubuntu specifically. Any suggestions?

---

### Post by signseeker on 2008-06-12
> **dslax27 said:**
> SUCCESS! Well - sort of. 

I got the CD to run using CTRL+ALT+F1 and "sudo mount /dev/scd0 /media/cdrom" and then "sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run"

Sweet.

Then the cd loads and I get this message: 


I hit "OK" and then the screen blacks out.


- [Here]("http://www.nvidia.com/object/linux_display_x86_96.43.05.html") is the NVIDIA support page referenced above for my GeForce4 4200 card.
- [Here ]("http://us.download.nvidia.com/XFree86/Linux-x86/96.43.05/README/README.txt")is the README file referenced above

Maybe I'm not reading the README carefully enough, but I can't seem to find out how to start up in X mode. It's probably because NVIDIA wrote their README for the general Linux audience, but not for Ubuntu specifically. Any suggestions?

Copy the file to your home directory. 

You cant run the Nvidia install script while an X session is active. 

So do a text login from a terminal, and then run the script with sudo. 

Good luck.

---

### Post by dslax27 on 2008-06-12
Please excuse my noobness, but how do I copy the file to my home directory? At what point in the boot process do I do that? 

So far here's my process:

[LIST=1]
[*]Turn on computer and wait until my graphics card-induced  white screen of death
[*]CTRL+ALT+F1 for the manual/text command environment
[*]Mount the CD drive with "sudo mount /dev/scd0 /media/cdrom" 
[*]Run the NVIDIA driver from the CD with "sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run"
[/LIST]

At what point do I copy the file from the CD to my home directory? How do I copy something to my directory without having a functional graphics card?

---

### Post by tgrimley on 2008-06-12
> **dslax27 said:**
> Please excuse my noobness, but how do I copy the file to my home directory? At what point in the boot process do I do that? 

So far here's my process:

[LIST=1]
[*]Turn on computer and wait until my graphics card-induced  white screen of death
[*]CTRL+ALT+F1 for the manual/text command environment
[*]Mount the CD drive with "sudo mount /dev/scd0 /media/cdrom" 
[*]Run the NVIDIA driver from the CD with "sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run"
[/LIST]

At what point do I copy the file from the CD to my home directory? How do I copy something to my directory without having a functional graphics card?

All you'll need to do is after you mount the cd, before you run the NVIDIA installer:
```

sudo /etc/init.d/gdm stop
```

To copy your process:

   1. Turn on computer and wait until my graphics card-induced white screen of death
   2. CTRL+ALT+F1 for the manual/text command environment
   3. Mount the CD drive with "sudo mount /dev/scd0 /media/cdrom"
   4. stop X server with "sudo /etc/init.d/gdm stop"
   5. Run the NVIDIA driver from the CD with "sudo sh /media/cdrom/path/to/NVIDIA-Linux-x86-169.04-pkg1.run"

---

### Post by dslax27 on 2008-06-13
Ok, now we're getting somewhere!

I got as far as the installer screen, but then I got the following error:

> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site [ftp://download.nvidia.com?](ftp://download.nvidia.com?)

How can I download a kernel if my machine isn't hooked up to the internet? The CD for the graphics card driver is in the CD drive, and I can't put in another cd since the CD drive won't eject during this mode.

---

### Post by Xiong Chiamiov on 2008-06-13
I've put together a guide [here]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329"), since a lot of people have had problems with the NVIDIA drivers that are included in Hardy.

Since you've already gotten most of it, I'll try to help you through the rest.  There *isn't* a precompiled binary for our kernel, so it doesn't really matter whether or not you tell it to try downloading one.  You'll have to continue and let it compile the driver.  I'm not sure what packages are installed on the live CD; you might have to install the libc-dev and build-essential packages.

---

### Post by signseeker on 2008-06-13
> **dslax27 said:**
> Ok, now we're getting somewhere!

I got as far as the installer screen, but then I got the following error:



How can I download a kernel if my machine isn't hooked up to the internet? The CD for the graphics card driver is in the CD drive, and I can't put in another cd since the CD drive won't eject during this mode.

Say no. It will then try to compile a kernel module for you.
Good luck.

---

### Post by dslax27 on 2008-06-13
> **signseeker said:**
> Say no. It will then try to compile a kernel module for you.
Good luck.

I said no and I received another error. 

> **Xiong Chiamiov said:**
>  I'm not sure what packages are installed on the live CD; you might have to install the libc-dev and build-essential packages.

How do I do that exactly?

---

### Post by dslax27 on 2008-06-15
Here's a solution:

I could sell my NVIDIA GeForce 4200 on Ebay and buy a replacement. Any comparable / affordable suggestions for a replacement that will work with Ubuntu?

---

