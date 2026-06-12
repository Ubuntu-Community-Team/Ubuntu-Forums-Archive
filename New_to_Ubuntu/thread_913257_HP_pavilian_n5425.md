---
title: "HP pavilian n5425"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by W R Wilsey on 2008-09-07
New to the forums and Ubuntu. Non-programing idiot has gotten the resolution so that I can not read anything at all. Only went to 600x800 anyway and was trying to fix. Screen is skinny and long. I have the shell root up (ie. black screen with root@daniel:`#) showing. Plz help me in a simple concise way that an idiot can handle. Thanks Folks.

W R Wilsey

---

### Post by W R Wilsey on 2008-09-07
bumb

---

### Post by W R Wilsey on 2008-09-07
Can someone explain in simple terms how to restore resolution back to the 600x800 that I had before. On laptop pavilian n5425 all I see is tall and skinny beyond readable on screen. Thanks,

---

### Post by W R Wilsey on 2008-09-07
Please help me...

---

### Post by W R Wilsey on 2008-09-08
I take it no one can help me...

Big frown on face :(

---

### Post by W R Wilsey on 2008-09-08
This board is of no value to me when no one answeres my post. I would like some help. Please... Even if it's wrong...

---

### Post by starcannon on 2008-09-08
Hi there, lets see what we have here. In the shell please type.

```
lshw -class display
```

post the return values here please.

GL

---

### Post by W R Wilsey on 2008-09-08
OMG, Thanks starcannon. I will type it in now. I have found how to open in a fail safe terminal at log in. I know nothing of linux so this is all new to me.

Results of typed entry are:

*-diplay UNCLAIMED
    description:VGAcompatible controller
    product:CyberBlade/XP
    vender:Trident Microsystems
    physical id:0
    bus info:pci@0000:01:00.0
    version:63
    width: 32 bits
    clock:66Mhz
    capabilities:vga_controller bus_master cap_list
    configuration:latency=64

Again Thankie so muchie....

---

### Post by starcannon on 2008-09-08
Try this:

```

sudo dpkg-reconfigure -phigh xserver-xorg

```

then:
```

sudo /etc/init.d/gdm restart

```

or alternately just reboot, that should get you back to a usable desktop.

---

### Post by W R Wilsey on 2008-09-08
first result was :

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20080908085448


Second result was:

black screen with
* starting anac(h)ronistic cron anacron   [ok]
* starting deferred execution schedular atd   [ok]
* starting periodic command schedular crond    [ok]
* checking battery state...   [ok]
* running local boot scripts (/etc/rc.local)   [ok]
blinking underscore curser


system seems to be waiting or thinking now. Not sure which.
Sorry if I sound or act ignorant as this is my first time w/ Linux. There seems to be alot for me to learn. Nothing like windows at all. LOL

---

### Post by W R Wilsey on 2008-09-08
System rebooted with same result. Screen seems tall. If the laptop screen is pushed down at angle I can almost see the window, almost.

---

### Post by starcannon on 2008-09-08
Try this step x step guide.

[http://ubuntuforums.org/archive/index.php/t-763964.html](http://ubuntuforums.org/archive/index.php/t-763964.html)

GL keep me posted, I'll add help where I can.

---

### Post by W R Wilsey on 2008-09-08
Very nice...
One question, it said user is to log off. From the little terminal box I have up how should I do that? Just Ctrl-alt backspace? Is that their way of saying restart? May I hit you up for other issues? Ok, more then one question. Is there a good book you would suggest for learning (besides the "for dummies books")? How do I post a thank you that shows up to your credit?

Very Sincerely Thankful,
Rob

---

### Post by starcannon on 2008-09-08
you can log off with the UI, or with CTRL-ALT-Backspace or simply reboot, all will work fine.

I haven't bought any Ubuntu specific (i have linux bible and in a nutshell) books, I use the forums, google, and the seat of my pants, not in any particular order, generally google is my best teacher. Though if I were inclined, I'd probably haunt the geek isles in Barnes and Knobles, or do some looking around at Amazon.

Sure feel free, if I can help I will, do be sure to ask in forums though, so that others that have a similar issue can find out how you solved it (be sure to click on Thread Tools and Mark as Solved when your issue is fixed)

The thankyou link is the blue-ribbon with gold medal below each posters post.

Glad to be of service... now if I can compile kiba-dock for 64bit we'll both be set ;)

---

### Post by W R Wilsey on 2008-09-08
I jump for joy to quickly...
The log in screen is right now but not the rest after. 
I sit scratching head, wondering...XP for $100 or another bald spot...

---

### Post by starcannon on 2008-09-08
Yeah, Linux comes in 2 prices, 

The expensive:

Learn to install it.

The inexpensive:

Pay some one else to install it.

Windows comes with never ending subscriptions to pay to subscribe virus protection, pay for all software, pay, pay, pay.

In the end you'll pay regardless of what OS you use, just basically comes down to what your preferred terms of payment are.

Anyway, be sure give yourself time to learn, trials by fire always leave someone getting burnt.

---

### Post by W R Wilsey on 2008-09-09
I'm not sure I understand why just the log in screen is affected. Once the thing boots it's back to the white screen. I've fiddled with the sudo displayconfig-gtk. But it never stays. Without that I may not ever understand. I need some GUI as I migrate from windows. Is it better to be at the root@(username) dir or username@username? At the first mentioned dir it said there was no displayconfig thingie when I tried to run it but it worked in the secnd one. There is no option to boot from the cdrom disk at startup. Can I do that somehow and just start from scratch again(I know "the old reinstall windows" mindset)? What was your first experience with this sort of thing like? Again thanks for your help.

---

### Post by W R Wilsey on 2008-09-10
I have installed ubuntu 8.04 on a pavilian n5425. It is my sons and in true teen fashion screwed up the resolution. I have been handed links to so many things of which I do not understand because I am a first time user. I want to just get it back to where I can at least see the screen. The system does not seem to want to boot the cdrom so it defaults to the HD. In a very simple way to keep me interested so I don't fall back to MS "how do I just get back to square one"? I know little to no commands at this point but can learn albeit slowly. Even if I could get the cd to boot and just do a reinstall? I feel like I'm sitting in the front seat of an aircraft. I can fly it, somehow...

---

### Post by W R Wilsey on 2008-09-10
OK, so I post in three threads and only one person will try to help. Cuddos to "starcannon" for trying. I'm really upset that no one else has responded to my posts. Windows is worth the price just in tech support then? POO 
Maybe I should just bang head on desk.  POO

---

### Post by W R Wilsey on 2008-09-10
OK, so I post in three threads and only one person will try to help. Cuddos to "starcannon" for trying. I'm really upset that no one else has responded to my posts. Windows is worth the price just in tech support then? POO 
Maybe I should just bang head on desk.  POO

---

### Post by W R Wilsey on 2008-09-10
OK, so I post in three threads and only one person will try to help. Cuddos to "starcannon" for trying. I'm really upset that no one else has responded to my posts. Windows is worth the price just in tech support then? POO 
Maybe I should just bang head on desk.  POO

---

### Post by Sef on 2008-09-10
Do not post more than one thread on the same subject.

Please have patience when awaiting an answer.  We are all volunteers here and sometimes an answer can come quick and at other times, it can come slow.

If you truly desire very fast answers, then you can [buy support]("http://www.ubuntu.com/support/paid").

Also there is also Ubuntu IRC, which is a chat room for Ubuntu problems.  If you are on a Ubuntu machine or using the Live CD, to download xchat:  Applications > Add/Remove > Search: type in xchat > check the box next to xchat > apply changes > apply > close

Threads have been merged.

---

### Post by Sef on 2008-09-10
> Is it better to be at the root@(username) dir or username@username? At the first mentioned dir it said there was no displayconfig thingie when I tried to run it but it worked in the secnd one. There is no option to boot from the cdrom disk at startup. Can I do that somehow and just start from scratch again(I know "the old reinstall windows" mindset)?

username@username is best.  If you are root, then you are just as vulnerable as Windows. 

As for display thingy: could have been a mistype. I have done those enough.

As for the boot up problem, how old is your computer?  If it is newer than about 8 years, it should have that option to boot from cd-rom.

---

### Post by W R Wilsey on 2008-09-11
All I am asking is: If the screen resolution is so screwed that it can't be read, how do I change it, or reinstall ubuntu? I have done many things that I've read and did get the login screen readable. After that it loads to like the worst resolution possible. EVERY time I boot my laptop it goes straight to the hard drive. I have entered laptop setup and selected the boot sequence to Cdrom,HD,Floppy,Network properly to no avail. I'm not a computer person so giving me links to articles that I do not understand will only make my anxiety worse. I'm a windows person only because it's easy. I want Linux because it's safe.

I do not mean to sound crass or rude and apologize if I do. As said before I'm new and just want to learn. Virtual handshake to anyone I've dissed...](*,)

Sorry I post with my desktop XP. The laptop is next to me with DSL. Yes, imagine for a minute me and two systems wrestling around wires and limbs flailing around.

---

### Post by W R Wilsey on 2008-09-12
Good Bye linux....

---

### Post by W R Wilsey on 2008-09-26
Without any help I managed to get the screen back to 800x600. Now I need to make it a little bigger. You would be proud of me if you knew what an idiot I was to start with. Starcannon, would you please contact me again. I think you can help me for sure now.

---

