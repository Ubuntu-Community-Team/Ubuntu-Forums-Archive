---
title: "I love my music"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Rhavage on 2008-07-07
Hello all. I'm currently getting my feet wet with the live CD for Ubuntu to get more familiar with it. I had a bad experience with XP ](*,)  and I'm looking for other options, but have a question or two about Ubuntu...

I love downloading live shows that are usually in .flac or .shn format. What bittorrent like programs do you suggest to use for d/l'ing the music?

Second... What programs are out there to convert these files to wav/mp3 files to burn to CD's?

OK and a thrid question. What are some programs I can use to transfer music to my portable mp3 player? (Gigabeat to be more exact.)

Thanks for any info in advance!

---

### Post by tjwoosta on 2008-07-07
for bittorent clients 
i use transmission (comes preinstalled on ubuntu hardy)

i also use bittornado  on my other computer running gutsy

---

### Post by BGFG on 2008-07-07
For torrents - i use deluge (pretty fast and friendly)
Music - Rythmbox Banshee or Amarok (i hear they sync well with players)
Conversion - I'm not really sure. but browse the repositories with add/Remove you should find lots of options.

Enjoy yourself!

---

### Post by wolfen69 on 2008-07-07
> What programs are out there to convert these files to wav/mp3 files to burn to CD's?soundconverter is what i use.
> What are some programs I can use to transfer music to my portable mp3 player? (Gigabeat to be more exact.) well, some players will be treated as a regular flash drive (storage), which makes it real easy to transfer files. no extra apps needed. my psp works great with ubuntu.

---

### Post by Rhavage on 2008-07-07
Thanks for the quick replies. I'll do some more research on these and see what I can do.

---

### Post by cozmicharlie on 2008-07-08
Welcome to Ubuntu.  I am also a big music downloader and I have been very happy with Ubuntu since I switched a few years ago.  The advice others have given is good except that the players and converters recommended to do not all support shn.  If you are like me, then a lot of your music will be in shn.  Only a few players can handle shn and you must install the shn codec for them to work.  You should take a look at a few tutorials that will help you get set up for both shn and flac.  This is what I do.

Follow this tutorial to install the shn codec and play in mplayer.  You will also need the shn codec for conversion to mp3  ([http://ubuntuforums.org/showthread.php?t=739658&highlight=shn](http://ubuntuforums.org/showthread.php?t=739658&highlight=shn))

A better player IMHO is xmms and it will paly both shn and flac - follow this tutorial ([http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)).

A couple options for conversion are SoundKonverter (available in Synaptic) and PACPL ([http://ubuntuforums.org/showthread.php?t=712064&highlight=shn](http://ubuntuforums.org/showthread.php?t=712064&highlight=shn)).  Remember though you must have the shn codec installed.

For Bittorrent I use Azureus but Deluge is very popular.

gtkpod is good for ipods but if you are a true music lover then change to Rockbox and listen to your music in flac.

Have fun

---

### Post by Rhavage on 2008-07-08
Thanks Charlie, I'm a huge fan of live music. I have a few different sites I go to get most of my stuff and subscribe to Napster. I'm just backing up  a few things on this PC before I dive into full Ubuntu install. I have a feeling I'll feel right at home when I learn the tricks of the trade. :)

---

### Post by Rhavage on 2008-07-09
> **cozmicharlie said:**
> 


A better player IMHO is xmms and it will paly both shn and flac - follow this tutorial ([http://ubuntuforums.org/showthread.php?t=833164&highlight=shn](http://ubuntuforums.org/showthread.php?t=833164&highlight=shn)).


Ok, I'm only about 20 hours old into Ubuntu and I really want to get used to the terminal instead of using the actual download file. I had no problems with the cut and paste for the first step, but when it gets to the 2nd step, is "~" supposed to be a folder I create in the HOME directory? And if so, where do I find the HOME directory?:confused:

Sorry if this is a dumb question, I'll probly have heaps more to come.

---

### Post by arsenic23 on 2008-07-09
> **Rhavage said:**
> Ok, I'm only about 20 hours old into Ubuntu and I really want to get used to the terminal instead of using the actual download file. I had no problems with the cut and paste for the first step, but when it gets to the 2nd step, is "~" supposed to be a folder I create in the HOME directory? And if so, where do I find the HOME directory?:confused:

Sorry if this is a dumb question, I'll probly have heaps more to come.

When yout type **~/** that is the same thing as typing **/home/yourusername/**.  So that second step is using mkdir to make a directory named **build** in your home folder.

---

### Post by Rhavage on 2008-07-09
ok, so when I see the "~" while doing this, I should be putting in /home/username/....  correct?

---

### Post by tjwoosta on 2008-07-09
> ok, so when I see the "~" while doing this, I should be putting in /home/username/.... correct?

no

~/ that literally means the same exact thing as typing /home/yourusername


for instance if i were to type this in a terminal
```
cd ~/Music
``` 

it would change directory to /home/myusername/Music


so anytime something is in the home/username directory you can use ~/ instead (like a shortcut)

---

### Post by Rhavage on 2008-07-09
Ok, got ya, thanks for the help folks.

---

