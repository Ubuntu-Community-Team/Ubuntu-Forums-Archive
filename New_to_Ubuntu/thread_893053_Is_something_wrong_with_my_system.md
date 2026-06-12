---
title: "Is something wrong with my system"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by bgast1 on 2008-08-17
I am currently using the latest Mint distro, Gnome desktop. It's based on Hardy Heron. My internet seems very slow. (It shouldn't be, it's Comcast) My computer seems to be slow as well. 

Ram 2.5 Gig
Processor -- Intel Pentium 4 Processor 540 with HT Technology,
-1 MB L2 Cache
-800 MHz front side bus
-3.2 GHz

ATI Radeon X1950 Pro PCIe video card. 

I don't recall my machine ever being this slow. Not even in Windows XP. There is no windows on this computer only Linux.

The Mint website said that their server was hacked, but it seems that this only affected Windows users. So I guess I really don't know what's up.

I could install Hardy Heron Gnome, Kubuntu with KDE 4, Suse 11.0, I won't install PCLOS though because it isn't updated enough with packages that I use. 

I basically will use this computer for multimedia stuff mostly, and my general office stuff and a fair amount of internet. I will buy a Vista computer after I save up some money for gaming.

---

### Post by f37u5g0d on 2008-08-17
Check out the system monitor (gui) or run the command "top" in the terminal and see what if something is eating up your cpu.

---

### Post by nicedude on 2008-08-17
If you do a reinstall then I vote for 32bit Ubuntu with Gnome, as your hardware specs more than support it. This should not be a slow computer with any of the OS's you mentioned or the one you are using so something is more than likely hogging CPU etc. so follow the other persons advice and use top to see whats hogging your resources. Also was it always slow with this OS or did this just start happening lately. In general though I would vote for redoing it with Ubuntu Hardy 32bit and see if that doesn't fix everything, at least if anything goes wrong in Ubuntu we all here can give you exact advise what to do :-) and there are always a bunch of Ubuntu heads in here.

---

### Post by bgast1 on 2008-08-17
Right now I am copying some files onto another disk, and as I type this both CPU's (linux reports hyperthreading as 2 cpu's are at about 47%. Most processes are sleeping. I am hardly using any memory at all. 

Of those files that I am copying the computer says that I am copying about 9.6 MB/sec. 

Perhaps the slowness is my perception, but it seems like it takes an awful long time for a page to load over the internet, and I am paying for more speed with Comcast.

In answer to the above post, It was not always this slow. Actually the internet seemed to load pretty fast, and I think that I was getting decent times with some torrents that I was downloading. Now I am lucky to get  10 Kib/s and I was getting speeds over 200 before.

---

### Post by mellowd on 2008-08-17
As for internet speed do you mean actual transfer speed or your browser is a bit slow to respond? Have you tried an online speedtest like this?: [www.speedtest.net](www.speedtest.net)

---

### Post by Bradtek on 2008-08-17
Have you tried something like
[http://speedtest.net/](http://speedtest.net/)
to see what your actual down/upload speed is ?

Have you tried different browsers ?

---

### Post by bgast1 on 2008-08-17
[[IMG]http://www.speedtest.net/result/310379656.png[/IMG]](http://www.speedtest.net)  I am using Firefox 3. By the way, if it is my perception, I have broad shoulders and thick skin, just tell me. It just seems incredibly slow the last few days.

---

### Post by Bradtek on 2008-08-17
Unless you say what speed you are supposed
 to be getting its kinda hard to give an opinion.

---

### Post by crazyness003 on 2008-08-17
hey, if you do multimedia stuffs, miight I suggest Ubuntu Studio? Right now im running uStudio in 64 bit (haha) but i reverted to the generic kernel. uStudio ships with the -rt kernel wich to my belief only helps when you synth anything using midi. 
Also, the GUI is ROXOR looking compared to the "human" theme for hardy. All access to ubuntu repos, all apps.
When you do get the iso, its actually a DVD iso, because all (most) a/v and graphics apps ship within the install iso. So once you install, you already have an arsenal of apps to use from the getgo

check out [Ubuntu Studio Here]("http://www.ubuntustudio.org")

As for internet speeds, i can actually observe a much, MUCH faster speed whilst in gnu/linux compared to windows XP. Im not even drawing Vista in the equasion. Its like Vista used 50% of network resources alone to check if you pirated something...every second. 
You go to watch youtube video, its probably thinking "OMG, HES TRYING TO ILLIGALY PIRATE, MICROSOFT, DOWNLOAD, NON GENUINE, THE INTERNET! SLOW IT DOWN!"

ps: w00t Chicago!!!

---

### Post by bgast1 on 2008-08-17
> **Bradtek said:**
> Unless you say what speed you are supposed
 to be getting its kinda hard to give an opinion.

Hmmm. Honestly, I don't know. Whatever Comcast's top speed is, is what I am supposed to be getting. At least I am paying extra for it. I'll try and check what speed that it is supposed to be.

Edit: Comcast advertises speeds upto 16 Mb per second.

---

### Post by bgast1 on 2008-08-17
> **crazyness003 said:**
> hey, if you do multimedia stuffs, miight I suggest Ubuntu Studio? Right now im running uStudio in 64 bit (haha) but i reverted to the generic kernel. uStudio ships with the -rt kernel wich to my belief only helps when you synth anything using midi. 
Also, the GUI is ROXOR looking compared to the "human" theme for hardy. All access to ubuntu repos, all apps.
When you do get the iso, its actually a DVD iso, because all (most) a/v and graphics apps ship within the install iso. So once you install, you already have an arsenal of apps to use from the getgo

check out [Ubuntu Studio Here]("http://www.ubuntustudio.org")

I'm not doing any intensive multi-media stuff right now. Just listening to tunes and watching movies. I fiddle around with the guitar, but I am not very good. Wouldn't mind recording myself though. Do you still recommend the Ubuntu Studio?

---

### Post by Bucky Ball on 2008-08-17
You can load all the UStudio packages by opening the UStudio repo without installing the OS, if you follow me. I run various flavours on all my boxes ... my laptop is currently running a mix of Ubuntu, Ubuntu Satanic Edition, Kubuntu and Xubuntu. There you go. ...

Ustudio is pretty full blown and for just recording a guitar, no, you don't really need. Try Audacity, which you will find in Synaptics. Extremely lightweight and efficient. :)

---

### Post by crazyness003 on 2008-08-17
I second the Audacity suggestion. uStudio is for semi-harcore mm peeps. Essentially, all it is, is a full Ubuntu OS slightly with a modified kernel, a mych better-looking UI, and already preinstalled with mm apps.

You can also "upgrade" to uStudio from a Ubuntu install by searching for ubuntustudio-desktop in Synaptic.

i think the command for it is
```

apt-get install ubuntustudio-desktop

```And this gets rid of some ubuntu-desktop modules to load the uStudio ones, plus all the apps that come with uStudio. You can still run the -generic kernel in uStudio, but it also installs the -rt one (real-time).
If you want give it a try, then if you dont like, just uninstall ubuntustudio-desktop and reinstall ubuntu-desktop

Of course only if you wanna spend the time and resourses on gettign all that. For what you wanna do: Audacity.
Small. Simple. Easy.

---

### Post by bgast1 on 2008-08-17
Well, I like to play around a lot. I don't really know a lot about full blown multimedia stuff, maybe audacity will be the way to go once I get Ubuntu installed. Right now I am still copying some files over to another hard drive so that I don't lose them when I do another install.

---

### Post by bgast1 on 2008-08-17
Bucky Ball-- What is Ubuntu Satanic Edition? :confused:

---

### Post by Bucky Ball on 2008-08-18
> **bgast1 said:**
> Bucky Ball-- What is Ubuntu Satanic Edition? :confused:

So much evil fun, is what it is! haha

Back in the real world, check here;

[http://ubuntusatanic.org/](http://ubuntusatanic.org/)

apt-get install the components you want as suggested in a previous post. Great desktops and themes. My laptop is my fun and uni grunt box so I have a lot of bits and pieces loaded, the desktop is Ubuntu Studio Hardy only after recent upgrade, but that was also running a blend with Studio and can't remember what. The 'household' machine is originally installed with Xubuntu, more ram was added and so was Ubuntu. Easy as that really. Still boots into Xubuntu splash, but opens to a blend of Xubuntu and Ubuntu packages (a lot of which are the same so doesn't install).  There are lots of tweaks for customisation and I was going through a 'phase' during mid-year break! lol  :)

---

