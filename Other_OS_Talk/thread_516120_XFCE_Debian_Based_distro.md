---
title: "XFCE Debian Based distro"
date: 2007-08-02
forum: Other OS Talk
---

### Post by izizzle on 2007-08-02
Does anyone know any good debian based distro's that come with xfce as the default desktop?  I can only think of Dreamlinux... Anybody else know any good ones?

---

### Post by Rocket2DMn on 2007-08-02
Xubuntu

---

### Post by Paul133 on 2007-08-02
As rocket said, xubuntu. In order to get it if you're currenly running Ubuntu or Kubuntu, bring up a terminal and type ```
sudo aptitude update && sudo atitude install xubuntu-desktop
``` At least, I think that'll work.

---

### Post by izizzle on 2007-08-02
I dunno so much about xubuntu.... it's not debin based and it has weak repositories....

---

### Post by qamelian on 2007-08-02
> **izizzle said:**
> I dunno so much about xubuntu.... it's not debin based and it has weak repositories....

It is Debian-based, since it is a variant of Ubuntu and Ubuntu derives from Debian.

---

### Post by izizzle on 2007-08-02
ok, but then why are it's repos so weak?

---

### Post by kerry_s on 2007-08-02
> **izizzle said:**
> ok, but then why are it's repos so weak?

you most likely did not turn on all the repos.

why not just go straight debian?
[http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-xfce-CD-1.iso)

PS: even with debian you must add the other repo's if you want more access or the latest and greatest.mine->

```

# deb cdrom:[Debian GNU/Linux 4.0 r0 _Etch_ - Official i386 xfce-CD Binary-1 20070407-12:12]/ etch contrib main 

deb http://ftp.debian.org/debian/ etch main contrib non-free 

deb http://security.debian.org/ etch/updates main contrib non-free 

deb http://ftp.debian.org/debian/ lenny main contrib non-free 

deb http://security.debian.org/ lenny/updates main contrib non-free 

deb http://ftp.debian.org/debian/ sid main contrib non-free 

deb http://www.debian-multimedia.org/ sid main 


```

---

### Post by raul_ on 2007-08-02
Zenwalk is Slack based. Debian is a good mother distro, but there are others, and I think Slackware is also an excellent mother distro

---

### Post by izizzle on 2007-08-02
I tried going 'straight debian' once. BAD IDEA. I did not know that I would have to compile everything myself including the repos! SO, i ended up uninstalling debian and reinstalling ubuntu. However, this was not the xfce cd....

---

### Post by Bachstelze on 2007-08-02
> **izizzle said:**
> I tried going 'straight debian' once. BAD IDEA. I did not know that I would have to compile everything myself including the repos!

Rubbish.

---

### Post by Paul133 on 2007-08-02
How differen is Debian from Ubuntu?

---

### Post by kerry_s on 2007-08-02
> **izizzle said:**
> I tried going 'straight debian' once. BAD IDEA. I did not know that I would have to compile everything myself including the repos! SO, i ended up uninstalling debian and reinstalling ubuntu. However, this was not the xfce cd....

What! you are out of your mind, i have never ever had to compile and i use the net installer and just install the base, then build up from there, just using apt-get.
it's simple as hell, once you learn the basics, you can do anything. you just need to spend a little more time learning, give it more than a couple of hours. :)

---

### Post by kerry_s on 2007-08-02
> **Paul133 said:**
> How differen is Debian from Ubuntu?

ubuntu is debian rebuilt to make it easier. you should probably stick with ubuntu till you learn something.

---

### Post by izizzle on 2007-08-02
Am i gonna have to download the base and build it up even with the xfce cd? Or is it a little different?

---

### Post by Paul133 on 2007-08-02
Kerry, I assumed Debain was pretty similar to Ubuntu. But when izizzle's suggestion that everything had to be installed from source in Debian threw me for a loop. I merely expected confirmation that Debian was similar to Ubuntu (you don't have to compile your own kernel or most programs, you still have repo's, you still use apt, etc.). Sory if I didn't make that clear.

---

### Post by kerry_s on 2007-08-02
> **izizzle said:**
> Am i gonna have to download the base and build it up even with the xfce cd? Or is it a little different?

It's exactly like the xubuntu install, you get a complete desktop. at the first screen where you would normally hit enter, you can type> installgui <and then enter and you will get i nice/pretty installer.

---

### Post by Bachstelze on 2007-08-02
> **Paul133 said:**
> Kerry, I assumed Debain was pretty similar to Ubuntu.

It is. Pretty much everything that is in the Ubuntu repositories is in the Debian ones as well.


> **kerry_s said:**
> It's exactly like the xubuntu install, you get a complete desktop.

Except that it's a bit less bloated - you don't get tons of programs installed, you have a basic XFCE desktop and then you add the programs of your choice from there using Apt.

---

### Post by kerry_s on 2007-08-02
> **Paul133 said:**
> Kerry, I assumed Debain was pretty similar to Ubuntu. But when izizzle's suggestion that everything had to be installed from source in Debian threw me for a loop. I merely expected confirmation that Debian was similar to Ubuntu (you don't have to compile your own kernel or most programs, you still have repo's, you still use apt, etc.). Sory if I didn't make that clear.

Yeah, that had me scratching my head to. ubuntu and debian are equal in what you can do with them. I like to build mine from scratch on top of the base install.
it's this simple in both debian and ubuntu.

first you grab the mini.iso, otherwise known as the net installer.
ubuntu> [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
debian> [http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso](http://mirrors.kernel.org/debian-cd/current/i386/iso-cd/debian-40r0-i386-businesscard.iso)

then you the base install
in ubuntu you type> server
in debian, when it gets to package selection, you just unselect everything.

after the reboot,you'll be at command line no gui yet.
ubuntu> sudo su <to make you root
debian> just log in with the root password yo made during install

then you get the gui stuff and the desktop you want to use, it's the same command for ubuntu and debian.
apt-get install xorg gdm synaptic "your wm or de"
example:
apt-get install xorg gdm synaptic icewm menu

then just reboot(ctrl+alt+delete)
select your wm or de in the session menu and log in

that's it, very simple to get the gui, once your in gui you just open synaptic and click what ever else you want to install for your needs.

everyone should try a custom install at least once, most won't even go back to a full desktop, why should they, when they can build exactly what they want.

wow, long story hey. :lolflag:

---

### Post by Paul133 on 2007-08-02
On my last computer, I had to use the alternate CD. I would've used the minimal CD if I'd heard of it. Had to install the GUI, though at the command prompt, I used ```
sudo aptitude update && sudo aptitude install ubuntu-desktop
``` Does that only install Gnome, or does it install other programs as well. Obviously, I had everything else because I had the alternate CD and not the minimal. I'll have to try that sometime, though. I'm not terribly knowledgeable when i comes to Linux, and although I know the basics, I wouldn't install Gentoo or Slackware sat this point, though I could probably handle Debian. I just took some offense to > you should probably stick with ubuntu till you learn something

---

### Post by Bachstelze on 2007-08-02
> **Paul133 said:**
> I'll have to try that sometime, though. I'm not terribly knowledgeable when i comes to Linux, and although I know the basics, I wouldn't install Gentoo or Slackware sat this point, though I could probably handle Debian. I just took some offense to

TRue, but OTOH, the best way to learn is to try something new. By the way, Gentoo is extremely well documented, and the Handbook really holds your hand through all the install process. If you want to learn, that's the way to go :) And the great thing about Gentoo's installation process is that as long as the partitions for it are ready, you don't even need to leave your current Linux until your Gentoo is finished to install, so it is very easy to get help if you need it.


By the way, I'm moving this to the Other OS section.

---

### Post by miggols99 on 2007-08-03
Dreamlinux is a decent XFCE distro based on Debian.

[http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)

---

### Post by darksong on 2007-08-03
Install debian then the xfce desktop.

---

### Post by 67GTA on 2007-08-03
I actually preferred SAM. It is based on PCLinuxOS, and uses Apt/Synaptic, so it is not too big a change from Debian based distros. You just don't have as many apps in the repos.

---

### Post by AlanRogers on 2007-08-03
I truly fail to see how the OP had so much trouble with Debian; was it a really old example?
 
I've recently switched from Ubuntu to Debian, just to see what the differences are, and what I've found is what I've learned in Ubuntu is directly portable to Debian. 
 
The biggest bonus for me is the ability to install exactly and only what I want, instead of using meta-packages. These are a good idea in principle but a bit of a pain for serial tweakers like me.

---

### Post by ThinkBuntu on 2007-08-03
> **izizzle said:**
> I tried going 'straight debian' once. BAD IDEA. I did not know that I would have to compile everything myself including the repos! SO, i ended up uninstalling debian and reinstalling ubuntu. However, this was not the xfce cd....
Maybe you mean "configure" and not "compile"? Debian isn't a source-based distro, and it has a larger package base than any other distro, meaning you should have to do less compiling with it than with any other.

---

### Post by miggols99 on 2007-08-04
I had problems with configuring Debian. One thing was enabling KDM themes. It told me to edit some file, I tried it, but it didn't work!

---

