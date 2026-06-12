---
title: "need copy/paste working"
date: 2014-07-03
forum: New to Ubuntu
---

### Post by gfhfghdfgdfgsfsf on 2014-07-03
ok, first of all, wow, I figured out the riddle to sign up to these forums. It was a nice mindtrap the way you auto redirect users without JS acces into oblivion once they click continue.....  As for my question... I just installed ubuntu server.... I installed xfce4, but nothing seems to work.  If I try to run browser gives me some generic 'input/output error'.... ok  So I went to install firefox but it was so much text to type I tried to copy/paste with no success (linux cannot do a simple copy/paste a computer could do in two decades ago?).  So I tried to install vmware tools. Gave me some generic cryptic message about mounting a cd drive or something.   I open a file manager and try to go to /root and it tells me permission denied (kill me now).  Ok, so I open terminal, if I type ls mnt/cdrom I see vmwaretools. That is as far as I got. Every command I type fails.  I got no browser. No copy/paste to install new software, even tab auto-complete does not work.  I have completely lost all my patience. Typical linux, it cannot even get the very basic right. Any tips to get this working?

---

### Post by ubudog on 2014-07-03
You say you installed Ubuntu Server.  This does not come with any desktop environment or GUI programs, as it is meant for server installs, not desktop installs.

What you want is [Ubuntu Desktop]("http://www.ubuntu.com/download/desktop").

---

### Post by gfhfghdfgdfgsfsf on 2014-07-03
I want server install, I work with the WAMP stack and want to get familiar with the LAMP stack on a linux machine so I can play around with PHP frameworks native to linux.

I got closer to installing to install vmware tools, but now its asking me stupid questions like the location of gcc... This is what makes me lose my mind with linux, how am I supposed to know that?

---

### Post by ubudog on 2014-07-03
You can do all of those things in Ubuntu Desktop, while also having a working desktop environment.  The Server edition really isn't meant to run any desktop environment, rather is meant for total command-line use.

Ubuntu Desktop can still be configured with a LAMP stack, and it'd be much easier to get familiar with LAMP like that, IMHO.

---

### Post by grumblebum2 on 2014-07-03
What experience do you have using Linux?

---

### Post by gfhfghdfgdfgsfsf on 2014-07-03
ubudog: Ok, maybe ill give that a try tomorrow, cause I am completely losing my patience here, its like each time I get something done linux throws me a new error... But I remember unity was a big cluster F. Is it possible to get a more user friendly UI on ubuntu desktop with a few simple commands (like the linux mint GUI?)


grumblebum2: Not much, I pciked ubuntu for its support. I have used linux as my main OS about a decade ago for a few months. I also used in in college and had a few linux vm's here and there over the years... but its been a while with since ive used linux.

edit: Or can I just use linux mint and get support here, or is that a taboo thing to do?

---

### Post by ubudog on 2014-07-03
> **gfhfghdfgdfgsfsf said:**
> ubudog: Ok, maybe ill give that a try tomorrow, cause I am completely losing my patience here, its like each time I get something done linux throws me a new error... But I remember unity was a big cluster F. Is it possible to get a more user friendly UI on ubuntu desktop with a few simple commands (like the linux mint GUI?)


Yes, I use Xubuntu, which I'd definitely recommend.  Xubuntu uses xfce and is also less resource-intensive, and still comes with all the Ubuntu repositories, so you can get a LAMP stack up and running, same as you can in Ubuntu Server.

Just take some time and have some patience while you're learning.

---

### Post by QIII on 2014-07-03
If you are having trouble with copying and pasting in the terminal, you don't CNTL +  C and CNTL + V.

It's CNTL + SHIFT + C and CNTL + SHIFT + V.

So, from someone's instructions on the web or whatever, CNTL + C to copy and CNTL + SHIFT + V to paste it in the terminal.

---

### Post by capscrew on 2014-07-03
> **QIII said:**
> If you are having trouble with copying and pasting in the terminal, you don't CNTL +  C and CNTL + V.

It's CNTL + SHIFT + C and CNTL + SHIFT + V.

So, from someone's instructions on the web or whatever, CNTL + C to copy and CNTL + SHIFT + V to paste it in the terminal.

In the terminal you can place the curser at the text use a double left click to set the text to the clipboard.  Then use SHIFT + insert to paste it where you want.

Isn't it interesting how when a user doesn't understand the system it's the system that is wrong.  Just my observation.  All my servers are headless.  I ssh to the host so I only use the CLI for configuration and work.

---

### Post by QIII on 2014-07-03
Yah, but...

Left hand on keyboard at normal position, right on mouse...  :)

---

### Post by capscrew on 2014-07-03
> **QIII said:**
> Yah, but...

Left hand on keyboard at normal position, right on mouse...  :)

I have one of each.  ;-)  

It sure helps when you have to cd to some/long/and/hard/to/type/out/directory 

It only works in the pseudo terminal.  I don't even think about it anymore.  It just works, except when you sit down at a console and there's no mouse!

---

### Post by stalkingwolf on 2014-07-03
yes you should be able to install any DE you want.

---

### Post by bluephoenix2 on 2014-07-04
When you say cut and paste is not working, I would assume that even the mouse pointer is not working is that correct?  You have to install then openssh in order for you to telnet to your main OS, if Mac then open a terminal window and type ssh [username@ipaddress], the password is the sudo password you have defined in your installation steps.

Installation of openssh
[https://help.ubuntu.com/14.04/serverguide/openssh-server.html](https://help.ubuntu.com/14.04/serverguide/openssh-server.html)

---

### Post by gfhfghdfgdfgsfsf on 2014-07-06
Not much luck with Xubuntu yet....

On each bootup it gives me some sort of error and I need to authenticate then type 'startxfce4'...

Once I am in the graphics are messed up. Its like I am seeing two desktops.

When I click on 'install vmware tools' and am once again getting: "vmware tools installation cannot be started manually while easy install is in progress".

Once again, havent even started using linux and it seems every aspect is failing...

---

### Post by capscrew on 2014-07-06
> **gfhfghdfgdfgsfsf said:**
> Not much luck with Xubuntu yet....

On each bootup it gives me some sort of error and I need to authenticate then type 'startxfce4'...

Once I am in the graphics are messed up. Its like I am seeing two desktops.

When I click on 'install vmware tools' and am once again getting: "vmware tools installation cannot be started manually while easy install is in progress".

Once again, havent even started using linux and it seems every aspect is failing...
What ever your problems are, if you don't logically diagnose them you will never get it corrected.  Complaining never helps.  You seem to have multiple problems.  I would cure the first one before starting on the next one.

Considering you have taken an Ubuntu Server Edition and added a DE it sounds like there are dependency problems.  I think you should start with a Xububtu DE install.  At least all the packages are integrated.  The sever install has no advantage over the desktop version other than simplicity and the default install of tasksel.  You can install tasksel on the desktop so there is no disadvantage to using Xubuntu DE. 

All of this seems to be way OT from the original problem of cut and paste.

---

### Post by gfhfghdfgdfgsfsf on 2014-07-06
I installed xubuntu-14.04-desktop-amd64.iso.

I asked for cut and paste because a lot of the times I need to write these long commands, so I wanted to be able to cut and paste....

Its like linux is setup to make me as angry as possible by getting me to type as many useless commands that I should not have to type. ONly have bring my hopes up that I resovled something but to get another generic error telling me to type other things... and that process repeats itself over and over. This has always been my linux experience.

Anytime I boot up now it tells me: sda1: write same failed. Manually zeroing.

Then I need to hit enter. Type my username, hit enter. Type my pasword. Hit enter. Type startxfce4. Hit enter. All that just to get into the OS...

Once I try to change to a usual resolution the graphics are completely messed up.

Often while I am in the terminal it will keeps ask me for my password, cant I just type it in once when I open the terminal... Or better yet how about it never ask me for my password until I lock the machine.... I mean this is a dev machine in a virtual PC, can I please not get asked for my password so many times? Have some mercy linux...

Or when I install something... isnt there some sort of command to tell it to use all default parameters, so I dont need to babysit it and keep hitting enter?

---

### Post by grumblebum2 on 2014-07-06
> **grumblebum2 said:**
> What experience do you have using Linux?
You appear to be quite competent with windows and think you can plough your way through linux without much effort.
If it riles you so much maybe you should stick to windows.

---

### Post by gfhfghdfgdfgsfsf on 2014-07-06
There should be no effort needed. All I want to do is get the OS going with copy/paste and display management. That simple task is not working.   Linux should not be about losers who want to spend there time writing commands to feel cool, it should be a useful OS.  But this xubuntu thing is completely not working. Ive never seen the graphics so messed up in any OS before (including images).

---

### Post by grumblebum2 on 2014-07-06
> **gfhfghdfgdfgsfsf said:**
> There should be no effort needed. All I want to do is get the OS going with copy/paste and display management. That simple task is not working.   Linux should not be about losers who want to spend there time writing commands to feel cool, it should be a useful OS.
Well try installing a normal desktop iso and learn about permissions, terminal, file structure, recovery procedures etc before diving into a server install.
PS knowing how to use the terminal is one of the best aspects of Linux.

"**writing commands to feel cool**" lol
You too can learn to be cool. ;)

---

### Post by Bucky Ball on 2014-07-07
Personally? I'd start again. Install the server and install xfce4, NOT xubuntu-desktop. Any *buntu-desktop is going to drag in a heap of stuff you don't want/need, and for this situation, is bad advice. If you are going to install xubuntu-desktop, just install Xubuntu. Effectively, you would be doing that anyway.

Not sure why people advise to install *buntu-desktop on a pared back, minimally installed machine (particularly a server which is often headless). Wrong. They are effectively saying 'Install *buntu'. :-k

If you want a desktop environment on a server, xfce4 or lxde (and you can go lighter) are generally the default and best choices. Good luck.

---

### Post by QIII on 2014-07-07
> Linux should not be about losers who want to spend there time writing commands to feel cool

It's not.  Calling the members of this forum "losers" is cutting it pretty close to the line of insulting them, which will get you an infraction.

> it should be a useful OS

It is.  There is no doubt that *you *are having difficulty.  But unless you believe that we are all engaged in some sort of malicious fraud and only pretending to be using Linux, you are making a hasty generalization based on a sample size of one:  you.

I sense that part of what you are failing to realize that Linux is not a drop-in replacement for Windows.  It is something entirely different.

You did not learn how to use Windows in a day.  You will not learn Linux in a day.

If you grow up speaking English, then it is not likely that you will be able to speak German fluently after one class, a term or even a year of study.  If you expect to, you will be frustrated.

I would suggest that you make an effort to change your general tenor and demeanor if you expect help from people who are here voluntarily.  Furthermore, rather than a "laundry list" thread, start one thread for one problem and get a solution for that problem before moving on to the next.

---

### Post by bobnn on 2014-07-07
> Once I try to **change to a usual resolution **the graphics are completely messed up.
...
I mean this is a dev machine **in a virtual PC,**

Ummm - these (bolded) things might be related.  

Some will dislike me saying this, but I'd use 12.04 - 14.04 is still pretty new, with some "fit and finish" things being ironed out.

I'll let others decide on whther to install desktop and makle it a server, or install server and add a desktop.  From my experience, either is doable and each will have issues of it's own; but I thnk starting with the desktop and then - after the desktop is up and working - adding the servers for LAMP would probably be easier.

Snide comments will not be useful.  The truth is this stuff works pretty good.  

If you are stuck in a text console, issue:

```
sudo apt-get install gpm
```

Once that's up and running you'll be able drag across text in the console to copy it and paste to the command line with a middle-click.

---

### Post by Bucky Ball on 2014-07-07
> **bobnn said:**
> 

```
sudo apt-get install gpm
```



I think bobnn means install:

```
sudo apt-get install **gdm**
```

This is not your only option. There is also xdm, lightdm and others, all install as above, but replace 'gdm'. As you've installed a server version you will have lots of stuff missing and definitely not the place for a newcomer to find an easy ride. You will, on the other hand, learn something trying to fix it to your like. 

Just install xfce4 or lxde and a lot of the problems will go away and you'll have a much easier time fixing the rest.

---

### Post by deadflowr on 2014-07-07
gpm is general purpose mouse.
from apt-cache show(cause I'm too lazy to open synaptic or look else where)
> Description-en: General Purpose Mouse interface
 This package provides a daemon that captures mouse events when the system
 console is active, and delivers events to applications through a library.
 .
 By default, the daemon provides a 'selection' mode, so that
 cut-and-paste with the mouse works on the console just as it does
 under X.
FWIW

---

### Post by Bucky Ball on 2014-07-07
Ah, my mistake. ;)

---

### Post by gfhfghdfgdfgsfsf on 2014-07-07
> **grumblebum2 said:**
> Well try installing a normal desktop iso and learn about permissions, terminal, file structure, recovery procedures etc before diving into a server install. PS knowing how to use the terminal is one of the best aspects of Linux.  "**writing commands to feel cool**" lol You too can learn to be cool. ;)  I used to know the terminal and enoguh commands to get around. I just found it annoying and not very efficient (bad design if you have a GUI).

---

### Post by gfhfghdfgdfgsfsf on 2014-07-07
> **Bucky Ball said:**
> Personally? I'd start again. Install the server and install xfce4, NOT xubuntu-desktop. Any *buntu-desktop is going to drag in a heap of stuff you don't want/need, and for this situation, is bad advice. If you are going to install xubuntu-desktop, just install Xubuntu. Effectively, you would be doing that anyway.  Not sure why people advise to install *buntu-desktop on a pared back, minimally installed machine (particularly a server which is often headless). Wrong. They are effectively saying 'Install *buntu'. :-k  If you want a desktop environment on a server, xfce4 or lxde (and you can go lighter) are generally the default and best choices. Good luck.  I did start over again. I went for Linux Mint cinnamon. So far so good. It booted up fine. I was able to change the resolution without nothing breaking. And I was even able to install vmware tools without any issue (copy/paste works, and it even detected my printer and stuff, so I can drag & drop).       

But I originally went with server edition thinking I could just install a GUI and start quickly learning linux then dive into LAMP. But when I was not able to get even the basic stuff done I started to rage.

---

### Post by Bucky Ball on 2014-07-07
So this is solved? If so please mark as such using Thread Tools at top right to help others. Thanks. ;)

Just a tip: Linux Mint is not supported in the main areas here. Feel free to post in ***Other OS/Distro Support*** here, though, if you need help. Linux Mint has an active community and forum and you might have more luck posting there. 

Enjoy and good luck. ;)

---

### Post by JeQhdMD on 2014-07-07
Good post Bucky . . . . ;)

---

