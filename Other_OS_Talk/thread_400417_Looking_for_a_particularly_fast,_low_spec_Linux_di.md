---
title: "Looking for a particularly fast, low spec Linux distro"
date: 2007-04-03
forum: Other OS Talk
---

### Post by patrick1314 on 2007-04-03
Hello!

I'm looking for a Linux distro that has the following qualities:

- Very fast start-up time (faster than Ubuntu or SuSE for example)
- Very low requirements or graphical needs
- Easy to set up and maintain
- Specifically for use with Word-processing (preferably with OOo Writer or KWord at a stretch)
- Perhaps also lower battery demands (for laptop)

You see, what I want is to have a second (or third) OS on my laptop that is specifically for word-processing or work-related tasks and perhaps Wikipedia and web-browsing with Firefox or a derivative browser. I want to do such tasks as these without the distractions of email or messenger programmes on my main Ubuntu OS - and especially for very fast startup time and better battery life.

Anyone have any suggestions? I was thinking of the lighter weight Xubuntu, but it would probably have the same slowish startup time and battery drain that Ubuntu has.

Thanks!

EDIT: Also, it would be great if it was a Debian based one. I have come to appreciate Debian based over RPM based ones - but it's not a 'deal-breaker'.

---

### Post by aysiu on 2007-04-03
Damn Small Linux is Debian-based.

---

### Post by patrick1314 on 2007-04-03
Hah! Just got an email alert there notifying me of a reply, just as I discovered the Damn Small Linux webpage!
Thanks. I'll take a look at it.

:)

---

### Post by dannyboy79 on 2007-04-03
i have tried both and I actually like puppy better but I did find that the latest puppy doesn't support the Atheros chipset that's in my netgear card (i think it's the AR5212?) either 1 will fit your needs though. puppy is a little larger than dsl though.

---

### Post by jjalocha on 2007-04-03
Maybe you should have a look at [Fluxbuntu]("http://fluxbuntu.org/"), based on Fluxbox? I haven't tried it yet, but I'm looking for it's upcoming Feisty release, which looks quite promising.

---

### Post by NeoLithium on 2007-04-03
Fluxbuntu is actually good as well, just as jjalocha stated... it loads quick; low on all resources and it also uses the Ubuntu repo's; so it's excellent in many respects.  Although DSL or Puppy are both good in their own right as well; just trying to add some support to the Ubuntu derivative ;)

---

### Post by aysiu on 2007-04-03
You can also do your own custom barebones installation of Ubuntu.

Using the Alternate CD, choose the Install a Server option.

This will give you a barebones Ubuntu. You'll then be presented with a command-line after login. Type ```
sudo nano -B /etc/apt/sources.list
``` Uncomment (remove the # sign from the front of) any lines that look like web addresses. Save (Control-X, Y, Enter).

Then ```
sudo apt-get update && sudo apt-get install icewm menu xterm synaptic firefox xorg openoffice.org apmd acpi gksu acpi-support acpid gdm
``` will install some basics for you. ```
sudo dpkg-reconfigure xserver-xorg
``` will help you adjust the screen resolution and finally ```
sudo /etc/init.d/gdm restart
``` will get you up and running graphically. From there, you can use Synaptic to install anything else you might need.

---

### Post by patrick1314 on 2007-04-03
Ah! Thank you all for your speedy and informative replies! I'm definitely trying Damn Small Linux - after I get Syslinux up and working I'll try it from a USB flash. Then I'll give Puppy a try and then I'll have a look at this up-and-coming Fluxbuntu.
And finally, I really like the sound of this 'barebones' Ubuntu... so I'll have to give that a try too!

Thanks again!

---

### Post by ynnhoj on 2007-04-03
along the same lines of a customized ubuntu server install: you could give arch linux a try.  it's pretty speedy, and you can choose to install whatever you like.  generally, you're best off doing a "base" install, then doing a system upgrade and installing xorg and the window manager and other applications of your choice with pacman..

---

### Post by arox on 2007-04-04
I suggest Zenwalk or Arch

---

### Post by ThinkBuntu on 2007-04-04
I second Zenwalk...you'll have a system immediately, something you don't get with Arch. Also, Arch is based on KDE (and is renowned for its KDE repositories and support) while Zenwalk is based on the much faster XFCE. After distro-jumping, I've settled on Zenwalk.

---

### Post by .aku on 2007-04-04
> **ThinkBuntu said:**
> I second Zenwalk...you'll have a system immediately, something you don't get with Arch. Also, Arch is based on KDE (and is renowned for its KDE repositories and support) while Zenwalk is based on the much faster XFCE. After distro-jumping, I've settled on Zenwalk.

Arch is not based on *anything*.
It is an independently developed distro without any default DE's or even WM's.

Still, +1 for **Zenwalk**. ;)

//aku

---

### Post by koshatnik on 2007-04-05
If you've got the patience, Slackware. Its the fastest distro I've used to date.

---

### Post by arox on 2007-04-05
Zenwalk
Arch

---

### Post by ThinkBuntu on 2007-04-05
> **.aku said:**
> Arch is not based on *anything*.
It is an independently developed distro without any default DE's or even WM's.

Still, +1 for **Zenwalk**. ;)

//aku

Of course, no distro can be based on a desktop environment. What I meant was that it is well known for its KDE support.

---

### Post by Amorphous_Snake on 2007-04-05
How about recommending a light distro for my Celeron 1.2 GHz with 384 MB RAM. Currently it's running Ubuntu 6.10. I did try Xubuntu but I didn't notice that much of difference in terms of speed.

I don't think that this PC will be able to run Ubuntu 7.04 properly when it's released although I will try it and Xubuntu too.

But now I am thinking of trying one of those lightweight distros like Arch, Frugalware, SaxenOS, KateOS, SAM, Vector or Zenwalk. The thing is that I am a newbie! I want a fast, lightweight and easy to install and configure distro. I did try Arch but gave up as I realized I wasn't its target audience! I couldn't even boot into the system. I am thinking about Zenwalk and SAM. How is it? And how are all the other ones I have mentioned compared to Xubuntu? I know that they are Slackware based and I have never used Slackware before (well, I did try SLAX and ZenLive 4.2).

---

### Post by Nils Olav on 2007-04-05
> **Amorphous_Snake said:**
> How about recommending a light distro for my Celeron 1.2 GHz with 384 MB RAM. Currently it's running Ubuntu 6.10. I did try Xubuntu but I didn't notice that much of difference in terms of speed.

I don't think that this PC will be able to run Ubuntu 7.04 properly when it's released although I will try it and Xubuntu too.

But now I am thinking of trying one of those lightweight distros like Arch, Frugalware, SaxenOS, KateOS, SAM, Vector or Zenwalk. The thing is that I am a newbie! I want a fast, lightweight and easy to install and configure distro. I did try Arch but gave up as I realized I wasn't its target audience! I couldn't even boot into the system. I am thinking about Zenwalk and SAM. How is it? And how are all the other ones I have mentioned compared to Xubuntu? I know that they are Slackware based and I have never used Slackware before (well, I did try SLAX and ZenLive 4.2).

Try puppy linux, it's really light weight.

---

### Post by ThinkBuntu on 2007-04-05
Zenwalk is very good, and is the fastest/most stable distro I've tried. I'm giving Mepis a try out of curiosity, but I'll almost certainly go back to Zenwalk. It comes with a very solid application suite (AbiWord, GIMP, Bluefish, amongst others) and is moderately tough to configure once you get beyond the basics. Wireless can be accomplished with MadWifi, although the system natively supports certain cards (just not mine). Xfce is as good as GNOME. Oh, and the Zenwalk design is very appealing.

 Community support is really handled by about four to ten dedicated Zenwalkers on theri forums, and the wiki is awful, but the distro is very stable and well designed. Download and burn the ISO and give it a go! I'll do my best to answer any questions you have in the Zenwalk forums once you have it installed.

One last note. When auto-partitioning, it gets hung up on the fist partition. Simply hold down your backspace key at this point (there's no sign of it, except that it's stuck on the sda1 screen: this is the Linux boot partition, and it installs fine).

Have fun Zenwalking!

---

### Post by Amorphous_Snake on 2007-04-05
Mmmm I just visited their website. Strange, I thought it was like DSL but I saw screenshots running XFCE. How is package management and other stuff?

Edit: That was about Puppy.

---

### Post by Amorphous_Snake on 2007-04-05
> **ThinkBuntu said:**
> Zenwalk is very good, and is the fastest/most stable distro I've tried. I'm giving Mepis a try out of curiosity, but I'll almost certainly go back to Zenwalk. It comes with a very solid application suite (AbiWord, GIMP, Bluefish, amongst others) and is moderately tough to configure once you get beyond the basics. Wireless can be accomplished with MadWifi, although the system natively supports certain cards (just not mine). Xfce is as good as GNOME. Oh, and the Zenwalk design is very appealing.

 Community support is really handled by about four to ten dedicated Zenwalkers on theri forums, and the wiki is awful, but the distro is very stable and well designed. Download and burn the ISO and give it a go! I'll do my best to answer any questions you have in the Zenwalk forums once you have it installed.

One last note. When auto-partitioning, it gets hung up on the fist partition. Simply hold down your backspace key at this point (there's no sign of it, except that it's stuck on the sda1 screen: this is the Linux boot partition, and it installs fine).

Have fun Zenwalking!

Thanks. But how is package management? For exaple, one of the first things I will need to download and isntall will be Openoffice. Do the repos have the latest versions of commonly used software?

---

### Post by ThinkBuntu on 2007-04-05
Package management in Zenwalk is handled by netpkg. I've used it before, and it's as good as any other. Quick, resolves dependencies reliably, and has a solid repository. You wont find a huge amount of packages in it, but everything I've ever needed from Inkscape to OpenOffice has been there. One nice thing is that you choose your mirror through the Netpkg utility (no editing text files).

The software selection doesn't hold a flame to Ubuntu, but that's to be expected because Ubuntu has one of the largest repositories.

---

### Post by Amorphous_Snake on 2007-04-05
I heard that you can only manage one repo at a time. Is that true? I don't mind the size of the repo as long as it has all the things I need. I mainly use this PC for web browsing (How about plugins?), word processing and watching movies (codecs and players?).

---

### Post by ThinkBuntu on 2007-04-05
Codecs are included. You name the format, you'll be able to play it. I haven't used mine to play DVDs, so I can't speak for that. And as far as plugins go, if the application supports them, there's no reason Zenwalk would somehow break them.

And yes, I believe you can only view one mirror at a time. But I can't say that with 100% certainty...

---

### Post by Amorphous_Snake on 2007-04-05
Thanks, I will try to download and install it. I am also very interested in trying SAM 2007. I will be downloading both shortly. Thanks again.

But how about Vector, KateOS  and SaxenOS when compared to Zenwalk? All are based on Slackware, am I right?

---

### Post by Nils Olav on 2007-04-05
> **Amorphous_Snake said:**
> Mmmm I just visited their website. Strange, I thought it was like DSL but I saw screenshots running XFCE. How is package management and other stuff?

Edit: That was about Puppy.

Actually it use JWM. It package management is descent IMHO. Here's a link you might be interested in: [http://www.puppyos.com/development/package-management.htm](http://www.puppyos.com/development/package-management.htm).

---

### Post by Amorphous_Snake on 2007-04-06
Thanks, ThinkBuntu. I had a ZenLive 4.2 CD so I tried it, I have to say that I didn't like the package management. A quick look at some of the programs I use was very disappointing. For example K3B was at version 0.12, Azureus was missing, Wine was at 0.9.27 (I use uTorrent via Wine and it runs perfectly with 0.9.33).

Netpkg itself is good, but do you know if there are up to date repos available?

Nils Olav, I might give the new Puppy release a try.

And does anyone know if i will gain any performance gain if I run an i686 distro on my PC (again, it's a Celeron or PIII 1.2 GHz, running 'uname -m' gives i686)? I think I will try an already compiled distro like Foresight or sidux, I can't install Arch, and from the look of things Frugalware seems to be the same.

---

### Post by RAV TUX on 2007-04-07
> **Amorphous_Snake said:**
> Thanks, ThinkBuntu. I had a ZenLive 4.2 CD so I tried it, I have to say that I didn't like the package management. A quick look at some of the programs I use was very disappointing. For example K3B was at version 0.12, Azureus was missing, Wine was at 0.9.27 (I use uTorrent via Wine and it runs perfectly with 0.9.33).

Netpkg itself is good, but do you know if there are up to date repos available?

Nils Olav, I might give the new Puppy release a try.

And does anyone know if i will gain any performance gain if I run an i686 distro on my PC (again, it's a Celeron or PIII 1.2 GHz, running 'uname -m' gives i686)? I think I will try an already compiled distro like Foresight or sidux, I can't install Arch, and from the look of things Frugalware seems to be the same.

Try a "minimal" install of [COLOR=Purple][B]Oz


[IMG]http://skins.hotbar.com/skins/mailskins/em/google_emoticons/emoti_5.gif[/IMG]
[/B][/COLOR]

---

### Post by Amorphous_Snake on 2007-04-07
Thanks RAV TUX. I heard about your distro on these forums. It's based on Foresight, right? I am downloading Foresight 1.1 DVD now. If things go fine, I will download Oz next. Try to make a Distrowatch entry for your Oz.

What's in the minimal install? XFCE or Fluxbox?

---

### Post by RAV TUX on 2007-04-07
> **Amorphous_Snake said:**
> Thanks RAV TUX. I heard about your distro on these forums. It's based on Foresight, right? I am downloading Foresight 1.1 DVD now. If things go fine, I will download Oz next. Try to make a Distrowatch entry for your Oz.

What's in the minimal install? XFCE or Fluxbox?actually Oz is based on rPath, much like Foresight.

---

