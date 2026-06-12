---
title: "ubuntu is so slow!!!"
date: 2016-09-18
forum: New to Ubuntu
---

### Post by soloraptonic on 2016-09-18
im currently running a fresh install of ubuntu 16.0.4 on an hp probook 4440s with an intel celeron clocked at 1.7 ghz with 6 gigs of ram, intel hd graphics and a 250 gig 7200 rpm sata 3 hard drive...... but for the life of me i cant figure out why programs are opening so slow. google chrome and firefox take any where from 15 to 20 seconds to open up from a cold boot, and they take 7 to 10 seconds to open after previously being opened. video playback is slow and choppy, and overall its seeming like ubuntu is just not going to work out wich is a shame because i love ubuntu, any suggestions?

---

### Post by kc1di on 2016-09-18
Take a look at what is running in the background.  and stop anything that is not needed.  Check the programs that are hogging cpu time and ram. see if you can do without them.
you may find that mate or xfce run faster also. 
good luck

---

### Post by RobGoss on 2016-09-18
Hello and welcome, I use Per-load to help speed up things like browsers opening and also software programs, you can install it by running this command:

```
 sudo apt-get install preload
```

You can also disable programs you're not really using at startup, just type in **startup application, **from the search tab and in should appear un-check anything you don't  really use and make sure you know what application you're disabling

---

### Post by oldos2er on 2016-09-18
The celeron is not a processor known for its speed; not sure if there's much you can do about that.

---

### Post by Bucky Ball on 2016-09-18
> **oldos2er said:**
> The celeron is not a processor known for its speed; not sure if there's much you can do about that.

Absolutely. 

Welcome. Doesn't matter about the other specs if the processor is not up to it. It may not even be a 64bit processor (you didn't mention) in which case it wouldn't be seeing the 6Gb of RAM (as in that scenario you would be using the 32bit version of Ubuntu and accessing 3Gb of RAM, of close).

Please confirm which release of Ubuntu you are using, 32 or 64bit. If you are limited to 32bit, you might try a lighter flavour, like Xubuntu or Lubuntu. Not sure what the state of play with PAE kernels is at the mo, but that should allow 32bit systems to see and access more than 3Gb of RAM.

* Just one more idea: could you open a terminal, type in

```
top
```

and hit enter. Second line from the bottom, look for something like this:

```
KiB Mem :  3907984 total
```

That is mine and I have 4Gb installed on a 64bit machine. What does your say?

---

### Post by poorguy on 2016-09-18
Hey soloraptonic,

Give Ubuntu Mate 16.04 a try I'm running 32 bit without any slowness or sluggishness on a 2005 Dell Optiplex Desktop GX620 / Intel Pentium 4 630  3.0 GHz processor and 3.0 GB DDR2 Ram with Intel integrated graphics adapter. :D

---

### Post by Citta on 2016-09-18
Hi,
I tried to install that via GUI, seems it is not there. Why? Via terminal-no problem!
Thanks for your reply.

---

### Post by howefield on 2016-09-18
> **Citta said:**
> Hi,
I tried to install that via GUI, seems it is not there. Why? Via terminal-no problem!
Thanks for your reply.

If by GUI you mean the Ubuntu Software application, it is still a work in progress. There are quite a few applications/packages that it doesn't pick up on.

---

### Post by kc1di on 2016-09-18
> **howefield said:**
> If by GUI you mean the Ubuntu Software application, it is still a work in progress. There are quite a few applications/packages that it doesn't pick up on.

if you want you can install synaptic and it will include the other packages.  Also Think the advice to try mate of Xfce or Lubuntu may be a better match for you machine.

---

### Post by mörgæs on 2016-09-19
Though Celeron translates to 'somewhat less than a real Pentium' this particular Celeron is likely to be an Ivy Bridge processor around four years old. 

It should be blazingly fast compared to my 12-14 years old hardware which runs an acceptable speed, and yes Ivy Bridge is 64 bit and hence able to read a vast amount of memory.

The Preload-idea mentioned above is worth trying.

---

### Post by howefield on 2016-09-19
Might be worth checking the Unity support of the graphics card..

```
/usr/lib/nux/unity_support_test -p
```

Example.

```
hugh@xenial-laptop:~$  /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org
OpenGL renderer string: Gallium 0.4 on AMD REDWOOD (DRM 2.43.0, LLVM 3.8.0)
OpenGL version string:  3.0 Mesa 11.2.0

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
hugh@xenial-laptop:~$
```

---

### Post by dcpifhq on 2016-09-19
Probably you have some junk files that need to be cleaned!:grin:

Do:

```
sudo apt-get install bleachbit
```

This program is similar to CCleaner.
And if you're not familiar with CCleaner, search up on Google what items to choose for cleaning to get the best results!

---

### Post by RobGoss on 2016-09-19
Sometimes things like **compiz settings manager** and all those animations can slow your machine down. I for one never use things like that just to speed up my machines performance

Also with Ubuntu you can use **system monitor** to see what's using up some of the memory on your machine and the CPU usage along with a few more ways to see how your machine is preforming

---

### Post by RobGoss on 2016-09-19
> **soloraptonic said:**
> im currently running a fresh install of ubuntu 16.0.4 on an hp probook 4440s with an intel celeron clocked at 1.7 ghz with 6 gigs of ram, intel hd graphics and a 250 gig 7200 rpm sata 3 hard drive...... but for the life of me i cant figure out why programs are opening so slow. google chrome and firefox take any where from 15 to 20 seconds to open up from a cold boot, and they take 7 to 10 seconds to open after previously being opened. video playback is slow and choppy, and overall its seeming like ubuntu is just not going to work out wich is a shame because i love ubuntu, any suggestions?


So you say **Google chrome **and **Firefox**, is really slow at opening correct? You might want to consider it might be one of the browser extensions you have installed if anything. I never really use more then what's needed for any browser I use. If in fact you have browser extensions installed I would try to disable them one by one or all and restart your machine then open your web browser up and see how things run, if the performance of your machines get better you can enable them one at a time to see which one is causng you trouble. just a thought

---

### Post by oldos2er on 2016-09-19
> **dcpifhq said:**
> Probably you have some junk files that need to be cleaned!

OP mentioned a fresh install, so I doubt that's the case.

---

### Post by poorguy on 2016-09-19
> **soloraptonic said:**
> ...... but for the life of me i cant figure out why programs are opening so slow. google chrome and firefox take any where from 15 to 20 seconds to open up from a cold boot, and they take 7 to 10 seconds to open after previously being opened. video playback is slow and choppy, and overall its seeming like ubuntu is just not going to work out  any suggestions?

Haven't seen it mentioned yet. 
What kind of internet connection are you using? 
If wireless you may want to see how strong of a connection signal you are receiving. 
Also if using wireless try using a wired connection and see if that helps.

---

### Post by Citta on 2016-09-20
> **howefield said:**
> If by GUI you mean the Ubuntu Software application, it is still a work in progress. There are quite a few applications/packages that it doesn't pick up on.
Yes, I mean the Ubuntu Software. How can I find a certain software, generally, if it is not in Ubuntu Software available? What to do, if I do not want to pester the forums with such questions? I would not know, how to find the mentioned software. Suitable steps to be taken in Linux?
Thanks for your hints!

---

### Post by howefield on 2016-09-20
> **Citta said:**
> Yes, I mean the Ubuntu Software. How can I find a certain software, generally, if it is not in Ubuntu Software available? What to do, if I do not want to pester the forums with such questions? I would not know, how to find the mentioned software. Suitable steps to be taken in Linux?
Thanks for your hints!

As you said, you installed it via the terminal, so being "comfortable" with using the terminal you could use apt-cache search package, eg

```
apt-cache search preload
```

In some cases the output may be long so pipe it to less, eg..

```
apt-cache search preload | less
```

and page down at page at a time, or use the enter key to go down a line at a time. Q key to quit.

If you want a gui, you could try Synaptic Package Manager.

---

### Post by Citta on 2016-09-24
Hm, that means you know already the name and purpose. What do you do, if you know just the problem, slowness? Or other, less known purposes. To find an office software for Linux, well, even I would know how to do  this. What approach would be the best to solve such questions? Searching software for Win is easy, but here I do not know the best way.

---

### Post by ian-weisser on 2016-09-24
Your problem is not slowness. 'Slow' is the symptom. You must still discover the cause.
The way you identify problems is not to search for magic software solutions. Ask questions here, like you are doing.

Learn to use 'top' or 'htop' to identify if the problem is limited memory or CPU.
Learn to use 'iotop' to determine if the problem is a slow disk or other I/O issue.
Learn to review your logs for unusual activity during slow periods.

---

### Post by HermanAB on 2016-09-24
BTW, a slow browser is frequently due to a lame DNS.  If you want raw speed, then you should install Slackware.  Ubuntu is a huge resource hog in comparison to Slack.

---

### Post by Bruce_Gibbs on 2016-09-24
When you say it loads slowly. Is it taking a long time to load the software or are the graphics loading slowly? If the graphics a loading in strips from top to bottom of the screen or it appears that the card is taking time to produce images almost haltingly it could be a graphics driver issue..? Just a suggestion. I have an AMD Athlon system with a Radeon 5500 graphics card that I can't run 16.04 on beacuse of slow graphics rendering... Works perfectly in 14.04 though because the OS supports that card.

---

### Post by howefield on 2016-09-25
> **Citta said:**
> Hm, that means you know already the name and purpose. What do you do, if you know just the problem, slowness? Or other, less known purposes. To find an office software for Linux, well, even I would know how to do  this. What approach would be the best to solve such questions? Searching software for Win is easy, but here I do not know the best way.

Start a new thread, best not to further derail the OPs question.

---

### Post by Citta on 2016-09-25
Where to start a new thread-could not find something like "Software" etc.?

---

### Post by howefield on 2016-09-25
> **Citta said:**
> Where to start a new thread-could not find something like "Software" etc.?

If unsure..
[URL="https://ubuntuforums.org/forumdisplay.php?f=326"]
Forum: New to Ubuntu[/URL]
The perfect place to post for your Ubuntu support if you are new to Linux.

or

[Forum: General Help]("https://ubuntuforums.org/forumdisplay.php?f=331")
All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, UbuntuGnome and Ubuntu Mate.

is probably a good enough bet.

---

### Post by mJayk on 2016-09-26
> **poorguy said:**
> Haven't seen it mentioned yet. 
What kind of internet connection are you using? 
If wireless you may want to see how strong of a connection signal you are receiving. 
Also if using wireless try using a wired connection and see if that helps.

This will in no way effect the speed of opening a web browser

---

