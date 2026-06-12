---
title: "commands for cdrom"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by olddirtychris on 2008-05-05
sorry im a huge linux noob. I have a problem with linux and my graphics cards, well i think thats the problem. So i have the driver update for the cards but i can't get into ubuntu or mandriva. I can get ubuntu to the command screen but i don't know how to install the update i have on a cd. Im not sure the commands to load the cdrom. Like dos it would be d:\filename.exe but i have no idea in linux if someone could help me would be great. otherwise if you have heard of the problem when you try to load ubuntu and after i log in it locks up. I can move the mouse and thats it.

---

### Post by aktiwers on 2008-05-05
What Video card do you have?

You can't use that CD because if the file is an .exe file, because .exe files are for Windows.
But you should see your CD-rom drive in Places=>Computer

Tell us what video card you have and maybe we can help you install a Linux version of those drivers

---

### Post by olddirtychris on 2008-05-05
no its not a .exe file i was just giving the example of how i would type the command in windows. I have 2 7800gt's running sli.

---

### Post by lemming465 on 2008-05-05
To make the cdrom contents accessible you have to "mount" the CD.  Probably there is a line in /etc/fstab to help with this. (Do *cat /etc/fstab* to see it.)

If you only have 1 CD or DVD device, it will typically mount to /media/cdrom.  It may automatically mount when you insert the CD.  Try *ls /media/cdrom* and see if that lists any files.  If not, try *sudo mount /media/cdrom* and then retry the ls.

Assuming you can now get to the contents of the cdrom, what to do depends on what those are.  If the video driver you are trying to install is an ubuntu package (file with extension .deb), try *sudo dpkg -i* followed by the pathname of the file.

If it's an Nvidia display driver, those are typically shipped as shell scripts, try */bin/bash nvida**.  I can't remember off the top of my head if nvidia uses .sh or .run as their suffix.

If the file on the cd ends in .tar.gz, you need to unpack it somewhere like:
```
cd /tmp
tar xzf /media/cdrom/*.tar.gz
```
and then look inside the directory that got unpacked for further instructions.  There ought to be a file called README or INSTALL somewhere.

If you can provide more specifics about your hardware and the CD, we can be more specific.

---

### Post by olddirtychris on 2008-05-05
ok i think i my cdrom is /media/cdrom0. but i can't read anything thats on it. when i use ls it shows nothing when i use ls -al it just says total 8 then . and .. as files. the nvidia website said to type sh nvidia.... its a .run file. does it matter that i burned that disk in windows? will linux still recognize that cd?

---

### Post by olddirtychris on 2008-05-06
ok I can see the file on the cd now. But when i type sh nvidia... it says that it can't open the file

---

### Post by aktiwers on 2008-05-06
> **olddirtychris said:**
> ok I can see the file on the cd now. But when i type sh nvidia... it says that it can't open the file

Did you try go to System => administration=>Hardware drivers

And enable restricted modules?

---

### Post by lemming465 on 2008-05-08
> Did you try go to System => administration=>Hardware drivers ...
A great strategy for _after_ X and Gnome are up and running.  Before that is possible to, but involves a lot of fiddling with /etc/apt/sources.list with a text editor and a bunch of apt-get install commands, which may rather a lot of command line work for a Linux beginner.

If you have a CD with an NVIDIA driver .run file loaded, and you want to feed it in two things to watch out for:

a) you will probably get better results with the *bash* shell than the *sh* shell (on Ubuntu these are not the same).

b) you either have to use an absolute path, or cd into the directory with the file.

So maybe something like ```
sudo bash /media/cdrom0/NVIDIA*.run
```

---

