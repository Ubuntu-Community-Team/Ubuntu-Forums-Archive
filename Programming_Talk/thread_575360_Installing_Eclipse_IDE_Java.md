---
title: "Installing Eclipse IDE Java"
date: 2007-10-13
forum: Programming Talk
---

### Post by MCBTunes on 2007-10-13
I downloaded the program but I am struggling putting it where it needs to be. I am learning java, and I need it, not only because I hear it is fantastic, but also for a class I am in. I am running Ubuntu 7.04.

From the eclipse website I downloaded Eclipse SDK 3.3.1-linux-gtk, the tar.gz file.

It saved to my desktop, so I extracted it there and the file ended up on my desktop, there is an executable and the program works. The README didn't really  help

However, I don't want the file on my desktop, and I would like the program to be available in my applications -> programming section.

It almost seems as if the program isn't really integrated into the system right now. I shouldn't have to open a file and click an executable to run it. Where do I put this file?

I couldn't really think of another place for this post, sorry if it is inappropriate. 

Mike.

---

### Post by scawa on 2007-10-14
Ooo... I get to post my first help!!!

I just got this to work.   I used the instructions in this location.   I created it in my local home folder, since I am the only one on this workstation.  I even got my MyEclipse plugin to work with a manual MyEclipse install.

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

Good luck

---

### Post by CptPicard on 2007-10-14
The easiest way to get eclipse is through the repositories. Just fire up Synaptic (or Adept if you're on Kubuntu) and search for eclipse and click to install it.

Alternatively, do what I do... get the tarball and extract it to /opt. You'll need root rights for this, so something like 

```

sudo -s -H
cd /opt
mv ~/eclipse-sdk...tar.gz .
tar zxf eclipse-sdk..tar.gz

```

(fashion to taste according to where you downloaded it to initially)

Now, this isn't really much different from extracting into your home directory, but it's just more of an "appropriate" place to put it IMO. Actually, you're fine running eclipse even from your Desktop-extracted directory, but it's... uh.. sort of ugly. :)

Then you just launch it by running /opt/eclipse/eclipse. Getting it to your menu manually should be easy, just find where to edit it... I personally use a Kicker button.

---

### Post by MCBTunes on 2007-10-15
Ok, I did the following
```

michael@michael-linux:~$ sudo -s -H
Password:
root@michael-linux:/home/michael# cd /opt
root@michael-linux:/opt# mv /home/michael/Desktop/eclipse-SDK-3.3.1-linux-gtk.tar.gz .
root@michael-linux:/opt# tar zxf eclipse-SDK-3.3.1-linux-gtk.tar.gz
root@michael-linux:/opt# ls
eclipse  eclipse-SDK-3.3.1-linux-gtk.tar.gz
root@michael-linux:/opt# /opt/eclipse/eclipse
root@michael-linux:/opt# exit
exit

```

and it went smoothly. Although there are a couple issues I am concerned with

For some reason it was the only file in opt, I did an ls as you can see and eclipse was it. What is the reason behind this? If I were to download Junit for testing would I put it here also and do the same thing?

Also, as far as putting it in my menu. I am still quite unsure about how to tackle that.
> just find where to edit it... I personally use a Kicker button.

I am a little unsure about what you mean. Sorry guys, I am not real experienced with linux.

Edit: I got an icon, so that is a plus, now all i need to do is click, I Would stil llike it in the menu too, I have a few other programs like this. That are only an icon.

I also just fired up Synaptic Package manager(I didnt even realize that existed)... it is just a thing that you click and it installs many of the most common programs? It appears as if they are all older versions though. For instance, the Junit and Eclipse I donwloaded from their respective sites are newer versions,

---

### Post by aitorcalero on 2007-10-16
> **MCBTunes said:**
> 
I also just fired up Synaptic Package manager(I didnt even realize that existed)... it is just a thing that you click and it installs many of the most common programs? It appears as if they are all older versions though. For instance, the Junit and Eclipse I donwloaded from their respective sites are newer versions,

Synaptic is IMHO the best tool in Ubuntu/Debian related Linux distros, but for Eclipse is better to download it directly from Eclipse website, since versions changes rapidly and Synaptic / Ubuntu team cannot handle with it, or at least as fast as changes occur.
I usually install Eclipse in my home directory to avoid problems with updates related to permissions.

---

