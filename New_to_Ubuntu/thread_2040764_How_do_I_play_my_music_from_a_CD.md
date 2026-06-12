---
title: "How do I play my music from a CD?"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by Chemoflys on 2012-08-11
I put some music on a CD on my windows laptop, and I burnt the music to an orange infiniti disk. Nothing happens once I put it in my CD Drive thing.

I've looked through the options on System and I can't decide what category (DVD, CD ect) the disc falls in to.

Please help!

---

### Post by cwsnyder on 2012-08-11
Did you check that you could read the disk on your Windows drive before you started blaming Ubuntu?

Ubuntu can use Banshee, Parole, VLC, Totem, Amarok, Rhythmbox, mplayer and many other applications to play a properly recorded music CD, once it is mounted.

---

### Post by Chemoflys on 2012-08-11
> **cwsnyder said:**
> Did you check that you could read the disk on your Windows drive before you started blaming Ubuntu?

Ubuntu can use Banshee, Parole, VLC, Totem, Amarok, Rhythmbox, mplayer and many other applications to play a properly recorded music CD, once it is mounted.

Yes I did, and who say's I'm blaming Ubuntu? I'm not even blaming, I just said it wouldn't work. 

Can you tell me how I mount it please, as it doesn't open when I put it in my drive.

---

### Post by cwsnyder on 2012-08-11
On my system, an icon of a CD pops up on my desktop, I right click on the icon to **Mount Volume**, then open Banshee/VLC/etc., select the music album and play.

---

### Post by Chemoflys on 2012-08-11
> **cwsnyder said:**
> On my system, an icon of a CD pops up on my desktop, I right click on the icon to **Mount Volume**, then open Banshee/VLC/etc., select the music album and play.

That doesn't work for me, when I enter the disk nothing happens on my desktop.

---

### Post by Frogs Hair on 2012-08-11
If you haven't installed the Ubuntu restricted extras package do so. The package includes media codecs and flash. Under system settings > details > removable media select the application/action you want to use to play music. I have set Ubuntu to ask each time so below is the screen that appears when I insert a music disk.

---

### Post by pierceTN on 2012-08-11
First off, will it open/run on the *windows* machine? if not, it most likely did not burn right, if it will, you should be able to open it in vlc in ubuntu. When you stick the CD in do you hear the CD drive? have you had other CD's work in that computer recently?

-Pierce

---

### Post by Chemoflys on 2012-08-11
> **Frogs Hair said:**
> If you haven't installed the Ubuntu restricted extras package do so. The package includes media codecs and flash. Under system settings > details > removable media select the application/action you want to use to play music. I have set Ubuntu to ask each time so below is the screen that appears when I insert a music disk.

This is what I have done, but it doesn't work! I can play a blank CD with my Minecraft Gameplay on it but the other CD doesn't work lol.

---

### Post by Chemoflys on 2012-08-11
> **pierceTN said:**
> First off, will it open/run on the windows machine? if not, it most likely did not burn right, if it will, you should be able to open it in vlc in ubuntu. When you stick the CD in do you hear the CD drive? have you had other CD's work in that computer recently?

-Pierce

Yes it did open and run in my windows machine. I do hear a sort of fan then after a bit nothing happens and the noise stops. I've had a blank CD in there recently. ):P

I tried a command I found on a different thread and the paragraph at the bottom is what where the results.

[IMG]http://img69.imageshack.us/img69/9536/screenshotfrom201208112.png[/IMG]

How do I found the CD Properties that won't mount? Confusing :(!

---

### Post by pierceTN on 2012-08-11
do you have an option as to which format you use when you burned it? is it an mp3 file?

---

### Post by Chemoflys on 2012-08-11
> **pierceTN said:**
> do you have an option as to which format you use when you burned it? is it an mp3 file?

I'm not sure, I won't have the laptop till Wednesday so I'll just have to fix it then. Thanks for your help!

---

### Post by ajgreeny on 2012-08-11
So did you burn the CD as an audio CD or just "copy" the audio files to it, as you would a data CD?

---

### Post by Chemoflys on 2012-08-11
> **ajgreeny said:**
> So did you burn the CD as an audio CD or just "copy" the audio files to it, as you would a data CD?

I think I burned the CD as an Audio CD.

---

### Post by ads52 on 2012-08-11
It would be interesting to see any error messages when you atempt to play your audio cd from the commandline. First install MPayer and friend:

```
sudo apt-get install mplayer smplayer
```and then try the following:
```
mplayer -cache 2048 cdda://
```In my experience sometimes MPlayer finds what the gui players cannot :), and if it does not find the audio cd may very well provide more useful eror messages. 

BTW this tip is drawn from a larger page of [MPlayer tips]("https://help.ubuntu.com/community/MPlayerTips") on the Ubuntu Community Wiki.

---

