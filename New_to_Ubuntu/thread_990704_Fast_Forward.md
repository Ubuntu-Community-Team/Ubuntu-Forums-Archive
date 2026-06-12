---
title: "Fast Forward"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by icyest on 2008-11-23
Whats a good Linux media player program that has a "fast forward" capability? Micosoft Media player has an ingenious (I don't mean to idolize microsoft), and very convenient fast forward function on their player that can play audio up to 1.4x and 1.6x times fast.

---

### Post by Ryadt on 2008-11-23
vlc.

---

### Post by beanhead on 2008-11-23
:D cool throwing away windows is good I still have to keep it for network programing though but I just load it up with virtualbox ose. I also fell in love with ubuntu 6.06 and have been using it ever since. I would recommend a linux phrasebook. it will walk you through the command line and also good reference, its a pocket size book you can get at borders. just thought that would help, Aloha

---

### Post by Disreali on 2008-11-23
> **icyest said:**
> Whats a good Linux media player program that has a "fast forward" capability? Micosoft Media player has an ingenious (I don't mean to idolize microsoft), and very convenient fast forward function on their player that can play audio up to 1.4x and 1.6x times fast.

I have not found a *nix media player with a FF capability.  I was able to install the Zoom Player 5 for windoz using WINE. It can work when it feels like it.  Not a realiable solution. 

I would rather a native *nix player (MPlayer) include FF, but I can't program, so the devs will get to it when they feel like it.  

I don't use WMP on windoz, I don't care for the UI. Have you tried to install WMP using WINE? It might work, though I have not tried it myself.

---

### Post by icyest on 2008-11-23
You see, the thing is that window's media player has a Fast Forward function that continues to play audio at 1.6x speed, so you end up hearing a faster version of the origional audio. Perfect for someone like me who receives a lot of custom recordings and has no time to listen to them all. 

VLC just doesn't cut it :[
It's functions are 2x 3x times the speed of normal, but the audio is muted.

---

### Post by Ryadt on 2008-11-23
Which version of vlc are you using. The latest one allows you to hear music being played at 1.5x and 2.0x

---

### Post by icyest on 2008-11-23
VLC media player 0.8.6e Janus (wxWidgets interface)

I am so UTTERLY SHOCKED that linux does not have such a simple audio playback function on any available players. Worst of all, its microsoft's media player that has this fast forwarding alone! T_T

Anyways, I did some research and found this amazing application for Winamp: [http://www.surina.net/pacemaker/](http://www.surina.net/pacemaker/)
Does this work on XMMS(the winamp clone)?

---

### Post by Disreali on 2008-11-23
> **Ryadt said:**
> Which version of vlc are you using. The latest one allows you to hear music being played at 1.5x and 2.0x

On what system are you using vlc, and what version? If it is a *nix system, did you build the .9.x version yourself? There are no stable .9.x versions in either the ubuntu  or debian repos.  

Also, I've used the updated vlc 0.9.6 windoz release and did not find the fast forward or rewind functions to work reliably. It seems your luck is better than mine.

---

### Post by icyest on 2008-11-23
So I guess (and I feel really bad for saying this, but) this is one of those times where the might of linux has to submit to the superior microsoft. :[

I hope that's not too blasphemous.

---

### Post by mbsullivan on 2008-11-23
> 
VLC media player 0.8.6e Janus (wxWidgets interface)

I am so UTTERLY SHOCKED that linux does not have such a simple audio playback function on any available players. Worst of all, its microsoft's media player that has this fast forwarding alone! T_T

Anyways, I did some research and found this amazing application for Winamp: [http://www.surina.net/pacemaker/](http://www.surina.net/pacemaker/)
Does this work on XMMS(the winamp clone)?

How'd you get that version installed? I just tried VLC out of the repositories, and it's v0.9.4.

Fast-forward works properly, with audio.

> 
On what system are you using vlc, and what version? If it is a *nix system, did you build the .9.x version yourself? There are no stable .9.x versions in either the ubuntu or debian repos.


Huh? From Intrpid repo:

```
vlc (0.9.4-1ubuntu3) [multiverse] multimedia player and streamer
```

Get a new version of VLC. This should solve your problem.

Mike

---

### Post by icyest on 2008-11-23
That's so weird. My Synaptics only reveals that 8.6 exists, not 9.4. I can't find 9.4!

---

### Post by mbsullivan on 2008-11-23
> That's so weird. My Synaptics only reveals that 8.6 exists, not 9.4. I can't find 9.4!

Hmm... check your /etc/apt/sources.list file to make sure you're using the Intrepid repos. If you need any help, post the file.

Mike

---

### Post by icyest on 2008-11-23
What's a /etc/apt/sources.list? Is that a command or a file directory? I'm used to seeing the full line if it really is a directory path, including the windows C:/

And what's an intrepid repo?

---

### Post by icyest on 2008-11-25
after doing some more research, I'm trying to get this program.[http://sox.sourceforge.net/](http://sox.sourceforge.net/)

I can't seem to get it. I've downloaded an archive of some sort, and It's basically a list of folders. the read me does nothing to help. Can someone try an install it?

Add/remove programs does not list this for some reason. is there a way to expand Add/remove's repositories (not synaptic's)?

It's suppose to speed up audio.

---

### Post by mbsullivan on 2008-11-25
Hi icyest,

> 
What's a /etc/apt/sources.list? Is that a command or a file directory? 

/etc/apt is a directory, and sources.list is a file that lists all of the repositories from which you can get software.

> I'm used to seeing the full line if it really is a directory path, including the windows C:/

/etc/apt/sources.list really is the whole absolute path, it just looks different than it would on Windows.

On Windows, every partition is assigned a letter and addressed separately. In contrast, under Linux every folder is mounted into a common tree structure. Thus, whereas on Windows you have a "root drive" prefix (C:) that tells which partition you're addressing from, this prefix is unnecessary under Linux, since you always go from the same root directory.

Therefore, if you ever see an address starting with / ("/etc/apt"), it is an absolute path, addressed from the single "root directory", which has no explicit letter.

> after doing some more research, I'm trying to get this program.[http://sox.sourceforge.net/](http://sox.sourceforge.net/)


You can install it through Synaptic (package name: [sox]("http://packages.ubuntu.com/intrepid/sox")) or from the command line with the following command:

```
sudo aptitude install sox
```

However, it would be nice to know that your Synaptic is working from the newest repositories. Could you post the contents of your /etc/apt/sources.list file, as well as what the terminal says if you run the following command:

```
 lsb_release -a

```

Good luck!
Mike

---

### Post by icyest on 2008-11-26
Screenshot of terminal says

[[IMG]http://img372.imageshack.us/img372/1154/screenshotttvi1.png[/IMG]](http://imageshack.us)
[[IMG]http://img372.imageshack.us/img372/screenshotttvi1.png/1/w657.png[/IMG]](http://g.imageshack.us/img372/screenshotttvi1.png/1/)

when code  "lsb_release -a" is entered.



Should be sources.list download off server in United States or Main Server?

---

### Post by mo0osah on 2008-11-26
I just wanted to let you guys know that my vlc (0.9.4) on intrepid works with audio forwarding upto 4x. I couldn't understand a word after 3x though.  Oh, I also just downloaded it from the repos so I'm pretty sure that it is there.  I have the restricted repos enabled. 

Hopefully that helps.

---

### Post by mbsullivan on 2008-11-26
> Screenshot of terminal says

That explains why your VLC from the repository isn't updated... You're running Hardy, not Intrepid.

You can still pull the package from the Intrepid repositories, but it'll take some more work. I can explain it if you want. Another option is to upgrade to Intrepid. Your version of VLC will be updated in the process.

Mike

---

### Post by icyest on 2008-11-28
How can I get Intrepid without having all my files erased? There doesn't seem to be an option to "Update" my current OS to 8.10.

And by the way, whats 64 bit and 32 bit? And how do I know which one I have for my OS? Is 64 better?

---

### Post by mbsullivan on 2008-11-29
> How can I get Intrepid without having all my files erased? There doesn't seem to be an option to "Update" my current OS to 8.10.

See [here]("http://www.ubuntu.com/getubuntu/upgrading"). Or, if you want to do it from command line, run:

```
sudo apt-get install update-manager-core
sudo do-release-upgrade

```

> by the way, whats 64 bit and 32 bit? And how do I know which one I have for my OS? Is 64 better? 

The difference between 64-bit and 32-bit operating systems is the *word size* of every command -- meaning the basic unit of memory transfer used between the CPU and memory, and the size of basic data elements. Both have their advantages and disadvantages, *but* the actual performance difference is very small.

The main advantages of 64-bit are the following:
(1) You can natively address > 3GB memory without a modified kernel.
(2) Some applications that require a large amount of memory bandwidth (such as video encoding or image manipulation) may experience a modest performance increase, since fewer instructions are required to fetch large chunks of data.
(3) You get better precision primitive units, but this is only of use for scientific computation.

The main advantages of 32-bit are the following:
(1) Generally better supported by applications and drivers. This is becoming less of an issue, but some programs may be less stable under 64-bit Linux. You can run 32-bit programs under the 64-bit operating system, as well, but I have had issues in the past.
(2) Applications will generally take less space, since all primitive units (such as integers) take up only 32 bits, as opposed to twice as much when compiled for a 64-bit OS.

To find out which you've installed, run:

```
uname -ar
```

And look @ the end of the printout. If it says "i686", you have 32-bit Linux installed. If it says "x86_64", you have 64-bit.

Which should you choose? That is up to you. If it were me, I'd say: if you have > 3GB of memory, go with 64-bit. If not, stick with 32-bit. It's just easier that way.

Mike

---

