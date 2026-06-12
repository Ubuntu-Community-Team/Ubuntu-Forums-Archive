---
title: "How To Listen Music In Ubuntu"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by EDLIU on 2012-01-05
Hi,

I have a MacBook Pro running Ubuntu 11.10. How do I listen to music in the Ubuntu using Banshee?

Each time I open the "Audio Disc", the songs are listed, but cannot be played in the "Banshee Media Player". How do I let Banshee play the Music CDes?

BTW, if I double click the "song files" in the Audio Disc, will it "RIP" the songs automaticlly?

Thanks.

Ed

---

### Post by Lars Noodén on 2012-01-05
Ubuntu is moving away from that one as a default starting with 12.04.  So you may wish to try Rhythmbox, Amarok, Clementine, Totem, or Exaile.  It will be Rhythmbox which will be the new default and be in the next LTS for five years.  Give one of them a try instead.

---

### Post by EDLIU on 2012-01-05
Hi,

Thanks.

But before moving to the new player, how can I use banshee?

Thanks.

Ed

---

### Post by plucky on 2012-01-05
> **EDLIU said:**
> Hi,

Thanks.

But before moving to the new player, how can I use banshee?

Thanks.

Ed

Run from a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` or search for it in **Software Centre** and install it.

Good Luck

---

### Post by mastablasta on 2012-01-05
no that's not it.
 
your porgramme is not mounting the correct point as audio CD. i have same problem with Amarok and i can't say that Ubutnu is doing it right here. it's like no one ever tested an Audio Cd on it. 
 
you see it might be mounting audio disk on sr01, or cdrom or even sc01. you have to fin where it should be (easiest done by VLC) and then try to set it so it reads it from propper mount point. 
 
to me only VLC works. even specialised audioCd listening programmes do not work.
 
 
if you want to rip, you can rip to mp3 and then listen to the music.

---

### Post by EDLIU on 2012-01-05
> **plucky said:**
> Run from a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` or search for it in **Software Centre** and install it.

Good Luck


Hi,

I followed the instructions, and got the following messages:

"
Failed to fetch [http://tw.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread4_4.1.3-10ubuntu4.1_i386.deb](http://tw.archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdread/libdvdread4_4.1.3-10ubuntu4.1_i386.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"

So what does the message mean? What should I do now?

If the download failed, what should I do with the "downloaded files"?

Thanks.

Ed

---

### Post by EDLIU on 2012-01-05
> **mastablasta said:**
> no that's not it.
 
your porgramme is not mounting the correct point as audio CD. i have same problem with Amarok and i can't say that Ubutnu is doing it right here. it's like no one ever tested an Audio Cd on it. 
 
you see it might be mounting audio disk on sr01, or cdrom or even sc01. you have to fin where it should be (easiest done by VLC) and then try to set it so it reads it from propper mount point. 
 
to me only VLC works. even specialised audioCd listening programmes do not work.
 
 
if you want to rip, you can rip to mp3 and then listen to the music.

Hi,

So what should I do now?

I'm new to Ubuntu(Linux)

Thanks.

Ed

---

### Post by mastablasta on 2012-01-05
Heh i would also like to know this but so far no one replied to my post (at least i think it was left unanswered). so far i haven't been able to figure out a solution by myself as i am not an expert here. 
 
you can install and use VLC media player to open AudioCD or you can rip the CD to MP3 (for example with k3b programme). For Mp3 it won't be a problem to listen to them in banshee.
 
to get mp3 codecs you do need ubuntu-restricted-extras package found in the software center.
 
another option is to find a setting for multimedia drives and drive mounting and set the correct values (although my Kubuntu doesn't use them for some reason).
 
third option is to use command line to play the audioCD :-) work on my computer just fine. it's the gui that is lame. 
 
and i don't know why they can't fix this. i meat it should automaticly find the mount point under which audio CD mounts. it recognises the Audio CD so it knows where it is and it knows it is an audioCD, but it just can't use it as audio CD.

---

### Post by plucky on 2012-01-05
> **EDLIU said:**
> Hi,

So what should I do now?

I'm new to Ubuntu(Linux)

Thanks.

Ed

You need to update your lists first.

Run ```
sudo apt-get update
sudo apt-get install -f
``` and post output.

Good Luck

---

### Post by EDLIU on 2012-01-05
> **plucky said:**
> You need to update your lists first.

Run ```
sudo apt-get update
sudo apt-get install -f
``` and post output.

Good Luck

After running the first sudo command:
Reading package lists... Done

And after running the second sudo command:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 273 not upgraded.

So what should I do now? Can you tell me what the two commands did?

Thanks.

Ed

---

### Post by EDLIU on 2012-01-05
Hi,

I ran the two sudo commands, but still cannot listen to my Audio Discs using Banshee.

Like I posted, I'm new to Ubuntu(Linux), can you show me how I can listen to music in my Ubuntu?

For example,

Click open Audio Disc, Click "Open Banshee Media Player", CLICK on "Track 1.wav". Run Banshee. ext..
Or whatever "RIGHT" way to listen to the music

Thanks.

Ed

---

### Post by plucky on 2012-01-06
> 0 upgraded, 0 newly installed, 0 to remove and **273 not upgraded**.


The first command updated the package manager list files and the second command will try to fix any broken packages.

Try running the Update Manager and install the packages that haven't been upgraded,or you can do the same thing by running ```
sudo apt-get upgrade
```

Good Luck

---

