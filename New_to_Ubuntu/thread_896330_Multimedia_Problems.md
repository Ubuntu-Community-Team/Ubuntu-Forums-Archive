---
title: "Multimedia Problems"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Generic Bond on 2008-08-21
I just reformatted my hard drive. I completely got rid of Windows and reinstalled Ubuntu. I'm having the same multimedia issues. It won't let me play or rip any of my CD's.

I put my first CD in my drive, tried playing it and this is what I got:
[IMG]http://img210.imageshack.us/img210/9861/mpnw7.jpg[/IMG]

If I can't have my music...ill go bonkers. I need help step by step. I hope somebody has patience! :lolflag:

---

### Post by tarps87 on 2008-08-21
can you double click on one of the songs and tell me what the error message says. Are they mp3s? Have you got restricted extras installed?

---

### Post by falcon61102 on 2008-08-21
More than likely you need to install the appropriate codecs.  When you double click on them, it should ask you to install the codecs, has that happened?

Wow, I type slow :).

---

### Post by Generic Bond on 2008-08-21
I have double clicked on the songs and it gives me nothing but reloading the red error sign over and over again.

How and where do I go to install the restricted codecs?

---

### Post by tarps87 on 2008-08-21
Try typing restricted into synaptic/ add remove programs, there should be a list of three, select them and click ok and it should work.

---

### Post by Generic Bond on 2008-08-21
Which ones do I add in synaptic?

---

### Post by tarps87 on 2008-08-21
There should be a description telling you which formats it supports, go for the ones your trying to play. If you use the 'add programs' under applications it may be easier. If you are still not sure can you print screen the one you find as I am not a my Ubuntu computer but should be able to recognise the ones you want from the picture

---

### Post by Generic Bond on 2008-08-21
[IMG]http://img179.imageshack.us/img179/3433/72143047ev2.jpg[/IMG]

---

### Post by falcon61102 on 2008-08-21
If you don't have any luck with that, and because you just reinstalled, you may want to take a look at this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Its a great guide to getting things setup.

---

### Post by tarps87 on 2008-08-21
I belive under synaptic they are called restricted extras like the kubuntu-restricted-extras but if you are using gnome you want ubuntu-restricted-extras
try removing kubuntu-restricted-extras and then in a terminal run:
```

sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Generic Bond on 2008-08-21
Do I need to remove kubuntu's restricted extras in Add Remove & Synaptic?

---

### Post by tarps87 on 2008-08-21
It would be a good idea to remove them as it will reduce the risc of conflicts
Are you using ubuntu or kubuntu?

---

### Post by Generic Bond on 2008-08-21
Ubuntu 8.04 with GNOME

---

### Post by tarps87 on 2008-08-21
Remove the kubuntu one then as this maybe the problem.
Once you've run:```

sudo apt-get install ubuntu-restricted-extras

```
Try and play a song an see what happens

---

### Post by Generic Bond on 2008-08-21
I did.

*"ubuntu-restricted-extras is already the newest version."*

Still having the same problem.

---

### Post by billgoldberg on 2008-08-21
> **Generic Bond said:**
> I did.

*"ubuntu-restricted-extras is already the newest version."*

Still having the same problem.

Open up a terminal and enter this:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

That will install all the codecs available.

--

After that if rythmbox still refuses to play anything, use another audio player like 'exaile' or 'banshee'.

Also look if 'vlc' can play it.

---

### Post by Generic Bond on 2008-08-21
[I]Error playing CD.
Reason: Failed to connect stream: Invalid argument

Error playing CD.
Reason: Internal data flow error.[/I]

I'm starting to get a little frustrated.

---

### Post by Generic Bond on 2008-08-21
Any ideas? :(

---

### Post by Generic Bond on 2008-08-21
Does anybody know what those error messages mean?

---

### Post by Generic Bond on 2008-08-21
> **billgoldberg said:**
> After that if rythmbox still refuses to play anything, use another audio player like 'exaile' or 'banshee'.

Also look if 'vlc' can play it.

I installed Banshee and it's still doing the same thing. It won't play.

---

### Post by Generic Bond on 2008-08-21
Just installed Exaile and it froze/crashed and was forced to force quit.

---

### Post by falcon61102 on 2008-08-21
Have you tried the Comprehensive Multimedia Guide:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I had a similar problem and after going through that it was fixed.  After part one I was able to play all my music files.

---

### Post by Generic Bond on 2008-08-22
Read it, updated and STILL won't work.

I don't understand what the problem is!

---

### Post by tarps87 on 2008-08-22
What format are the songs?

---

### Post by Generic Bond on 2008-08-22
Well, I'm importing them from a CD so they should be a .WAV format, but when I go to Places > Music, they're in a .OGG format.

---

### Post by Generic Bond on 2008-08-23
Any idea?

---

### Post by seagullplayer77 on 2008-08-23
I know that Ubuntu won't play DVDs after a default install, but I've never heard of the problem carrying over to CD playback. Just for kicks, try pulling something off of a data CD--some pictures, a document backup, something like that. Maybe the whole CD drive is acting screwy. I suppose another alternative would be trying to play an MP3 (or WAV, or OGG, or some sort of music file) off a flash drive. Maybe that'll work.

---

### Post by hanzomon4 on 2008-08-25
Not a codec problem [bug 191027]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027"), I just started having the same problem after enabling the proposed repos and updating.

---

### Post by Generic Bond on 2008-08-26
So what are we supposed to do to fix the problem? 
Wait until they fix the bug?

---

### Post by krazykookmany on 2008-08-26
//

---

### Post by Generic Bond on 2008-08-27
I mean, I can't even put the CD in and play it.

---

### Post by krazykookmany on 2008-08-27
//

---

### Post by impert on 2008-08-27
Could it be an error in your /etc/fstab file?
Here's the relevant line from mine. 
# <file system>   <mount point>     <type>     <options>       <dump>  <pass>

/dev/scd0          /media/cdrom0     udf,iso9660   user,noauto,exec  0       0

Just a suggestion.

---

### Post by krazykookmany on 2008-08-28
//

---

### Post by impert on 2008-08-28
Sorry I didn't get back to you sooner.
> For me the second line of code is different
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
Try getting rid of the **utf8**;. I have no idea what it does, but my system works without it, and yours doesn't (?)** man fstab** should tell you what it does, if you're curious.

---

### Post by impert on 2008-08-28
Ah, found it in the bottom of the **mount** manual page.
>  utf8   Convert 16 bit Unicode characters on CD to UTF-8.
I'm not much the wiser, but I'd try getting rid of it.

---

### Post by hanzomon4 on 2008-08-29
Try removing your .asoundrc or /etc/asoundrc

---

### Post by Generic Bond on 2008-08-29
> **hanzomon4 said:**
> Try removing your .asoundrc or /etc/asoundrc

And how do I go about doing that?

---

### Post by krazykookmany on 2008-09-08
//

---

