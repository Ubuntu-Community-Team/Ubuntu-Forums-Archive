---
title: "How i Installed Cinelerra in Fiesty"
date: 2007-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by kelvin spratt on 2007-06-03
This is how i made Cinelerra work in fiesty 
After downloading from Cinelerra Cv for fiesty and getting no joy this is what i did first i completely removed Cinelerra with Sypaptic then this is what i did next
1, terminal, sudo gedit /etc/apt/sources.list  2, Add paste these two entries to the end of the list. debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./
debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./   add a space between deb  http
3, press save then close. 4, in terminal paste sudo apt-get update  5, 
sudo apt-get install cinelerra    This is where the fun starts the terminal will tell you that the versions of some of the dependencies wrong then i got an update which i allowed. this is what i did next. 6, copy the entries one at a time into search in Sypaptic and completly removed them i think there were three i removed. 7, reboot,  8, open terminal
sudo apt-get update  9, sudo apt-get install cinelerra   this should install Cinelerra and have no messages,  10, reboot, 11, start Cinelerra it should fire up in all its glory? well it did for me there is no guarantee this will work for everyone but its worked twice for me,
Mint 3 users this does not work for you with full permissions.

---

### Post by treblesix on 2007-07-21
Hi,

I am having no joy getting this to work.

When trying to install the software following youre instructions, I get ...........

The following packages have unmet dependencies.
  cinelerra: Depends: libguicast (= 1:2.0.0-1svn20060611.1) but 1:2.1.0-2svn2007424ubuntu3 is to be installed
E: Broken packages

---

### Post by Matt Nichols on 2007-07-21
Sweet! It worked! I had tried oodles of other ways to do this, but yours actually worked! Thanks, dude!

---

### Post by treblesix on 2007-07-22
This is the only way I could get it to work on Feisty ..............


Add these to software packages

sudo gedit /etc/apt/sources.list 

Ubuntu Edgy

    deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
    deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./ 



Cinelerra started giving the error message regarding shmmax. This should be the amount of memory shared between process by the kernel. After some work with google I found an easy solution - in the terminal I gave:

    sudo gedit /etc/sysctl.conf

and at the end of this file I added the line

    kernel/shmmax=0x7fffffff

I saved the file and I made

    sudo sysctl -p

Now cinelerra run fine.

It doesn't seem to alow the editing of DV, which is a bit gutting.

---

### Post by pushkarajapte on 2007-07-26
Dear Kelvin,
I followed your post and went through all the steps. I thought I was through, but then.....
Now Cinelerra has got installed (I hope so!!!) as its icon also appears in the Applications - Sound and Video menu. But the icon just refuses to respond. In short, nothing happens. :(
How do I rectify this?
Thanks in advance
Pushkaraj

---

### Post by kelvin spratt on 2007-07-27
All i can suggest is you look at my other post [http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223) i have installed cinelerra about 10 times without problems but it has to be done exactly as i did once installed get Aptoncd, and back up your software to an ISO this will give you a deb package with all the dependences of all the software installed after
you installed Feisty,so you can reinstall without the internet. as i am dyslexic i wrote this for me and it works great on my computer. i have a copy of the working Deb and its self contained? thats all i use now

---

### Post by pushkarajapte on 2007-07-28
Dear Kelvin,
I repeated the whole thing again but when i do "apt-get install cinelerra", it gives a command saying that the installed version is already up to date. So the installation IS complete is what I think, but it is stil not running.
I have another problem, if you can help me with it. How do I install Mozilla composer?
Thanks,

---

### Post by treblesix on 2007-07-28
Try what I did in my previous post. It might work.

---

### Post by pushkarajapte on 2007-07-28
I am sorry Kelvin, but it still refuses to cooperate. The installation goes through all the steps that you have mentioned It even builds the icon for Cinelerra in the Applications - Sound and Video menu, but thats about it. Nothing at all happens when I click that icon.
When i do the step 4 mentioned in your post (get update), it gives the following error messages.  Could this be the reason?

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) universe/multiverse Packages                  
  404 Not Found [IP: 91.189.89.6 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) universe/multiverse Packages                  
  404 Not Found [IP: 91.189.89.6 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages   
  Sub-process gzip returned an error code (1)

Are these the three enties you had referred to, which have to removed using synaptic? How do I do that?
Thanks in advance,
Pushkaraj
India

---

### Post by winkerlongtooth on 2007-07-29
Hi Kelvin and all.

Thanks for the procedure. I was installing this on Ubuntu as a VMWare client with a Windows XP Pro host if that makes any difference.

I got up to step 5 and then things changed for me...

> **kelvin spratt said:**
> 
1, terminal, sudo gedit /etc/apt/sources.list  

2, Add paste these two entries to the end of the list. 
[INDENT]debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools ./[/INDENT]
[INDENT]debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./[/INDENT]   
add a space between deb  http 

3, press save then close. 
4, in terminal paste sudo apt-get update  
5, sudo apt-get install cinelerra    


What happened for me is that I got a update notification for Cinelerra before the dependencies were downloaded. I got a message saying the files weren't verified (or whatever - it went by so fast and I is a Noob). I said "yes" which was not the default.

Once the libraries were installed I got an error on the last one. At that point the updater said the database was corrupted (egad) and to run "sudo apt-get install -f" which I did and which also installed the libraries that were missing - and this time without an error.

I did a reboot and ta-daaaaa. I have the icon and Cinelerra came up.

I credit Kelvin and his brilliance and whomping good noobie luck. Thanks!

---

### Post by LiamTreacy on 2007-08-03
Doesn't work, I find. Still have broken dependencies - liblame0, libmjpegtools0c2a and libquicktimehv.

---

### Post by kelvin spratt on 2007-08-03
if you read what i wrote again you will notice that i mention about 3 dependencies that need to be removed
sudo apt-get install cinelerra This is where the fun starts the terminal will tell you that the versions of some of the dependencies wrong then i got an update which i allowed. this is what i did next. 6, copy the entries one at a time into search in Sypaptic and completly removed them i think there were three i removed. 7, reboot, 8, open terminal

---

### Post by kelvin spratt on 2007-08-03
Doesn't work, I find. Still have broken dependencies - liblame0, libmjpegtools0c2a and libquicktimehv.kelvin spratt;3127216]

if you read what i wrote again you will notice that i mention about 3 dependencies that need to be removed
sudo apt-get install cinelerra This is where the fun starts the terminal will tell you that the versions of some of the dependencies wrong then i got an update which i allowed. this is what i did next. 6, copy the entries one at a time into search in Sypaptic and completly removed them i think there were three i removed. 7, reboot, 8, open terminal[/QUOTE]

---

### Post by cotcot on 2007-08-07
Did not work for me. Could not solve 1 dependency (libquicktimehv).
I tried with the .rpm converted to .deb with alien. Works fine now.

---

### Post by LiamTreacy on 2007-08-19
> **kelvin spratt said:**
> 
if you read what i wrote again you will notice that i mention about 3 dependencies that need to be removed
sudo apt-get install cinelerra This is where the fun starts the terminal will tell you that the versions of some of the dependencies wrong then i got an update which i allowed. this is what i did next. 6, copy the entries one at a time into search in Sypaptic and completly removed them i think there were three i removed. 7, reboot, 8, open terminal
OK. Thank you.

---

