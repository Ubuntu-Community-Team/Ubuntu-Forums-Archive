---
title: "HowTo: Create your own Screensaver using native Ubuntu tools."
date: 2010-07-20
forum: Outdated Tutorials &amp; Tips
---

### Post by k3lt01 on 2010-07-20
[SIZE="3"]**HowTo: Create your own Screensaver using native Ubuntu tools.**[/SIZE]

**What's the point of this tutorial?**

This tutorial is it is here for those who wish to work with what is already installed on their system and wish to have a screen background that changes at predetermined intervals. It is for those who want to understand the already natively available AND installed system. It has been tested on Ubuntu 10.04 Lucid Lynx which is the current LTS. I will not, because I don't have any earlier versions installed anymore, be testing this on anything prior to Ubuntu 10.04. As each new version is released I will test it and report any difficulties found. If you have difficulties please feel free to let me know what they are and we can work through them together. It is based on the script and setup for the background named "Cosmos" which comes pre-installed in Ubuntu 10.04.

**Please note: This is just 1 way of doing this, there are many more ways and formats possible. Choose what is the best for you. This tutorial isn't here to dictate to anyone what is the best method for you to use. Instead, as has already been stated, it is here for those who wish to work with what is already installed on their system. If you find something others can use you could create a Tutorial on it to help others. Please do not turn this tutorial into a "my way is the best way" discussion, instead treat it like the technical tutorial it is and leave discussion about other methods to other threads.**

Note: I do not know if this will work in Kubuntu, Xubuntu, or any other variant other than Ubuntu. IF you try this in anything other than Ubuntu 10.04 and it works please let us know so we can add the information to this thread and give you the credit for your hard work in testing this in an untested variant.

**[SIZE="2"]1: Preliminary work.[/SIZE]** 
Follow the instructions in [this thread]("http://ubuntuforums.org/showpost.php?p=9271549&postcount=1").

**[SIZE="2"]2: Finding the required files.[/SIZE]**
[Taken from this thread]("http://ubuntuforums.org/showpost.php?p=9490170&postcount=11").

Now you have your slideshow setup and in the right place you need to go to Places > Search for Files. Search for Cosmos and you will find:
 [LIST]
[*]cosmos-slideshow.desktop (a configuration file in /usr/share/applications/screensavers)
[/LIST][LIST]
[*]cosmos (the folder containing the Cosmos backgrounds which you will have noticed is used as the basis of the slideshow background)
[/LIST][LIST]
[*]cosmos.xml (again used as the basis for the background slideshow)
[/LIST].

**[SIZE="2"]3: Modifying the file.[/SIZE]**
Open cosmos-slideshow.desktop by opening a terminal and typing or pasting.
```
gksudo gedit /usr/share/applications/screensavers/cosmos-slideshow.desktop
```Now you have that open change the following *[COLOR="Red"]ITALIC[/COLOR]* entries to suit your screensaver.

```
[Desktop Entry]
Name=*[COLOR="Red"]Cosmos[/COLOR]*
Comment=Display a slideshow of pictures of *[COLOR="Red"]the cosmos[/COLOR]*
Exec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow --location=/usr/share/backgrounds/*[COLOR="Red"]cosmos[/COLOR]*
TryExec=/usr/lib/gnome-screensaver/gnome-screensaver/slideshow
StartupNotify=false
Terminal=false
Type=Application
Categories=GNOME;Screensaver;
OnlyShowIn=GNOME;
X-Ubuntu-Gettext-Domain=gnome-screensaver
```
Save the file with A NEW NAME, this is so you don't lose cosmos.

**[SIZE="2"]4: Telling Ubuntu that you have a new Screensaver.[/SIZE]**
Now that you have done that press Alt-F2 and in the dialogue box type in gconf-editor. Go Apps > gnome-screensaver. On the opposite pane you should see a list go down until you see "mode", tap on mode twice and you will get another dialogue box appear, enter single into the Value line and click ok. Open the Screensaver preferences choose you new screensaver and your done.

Test it out and let us know how you go.

If you have any hints or suggestions regarding this format please feel free to make them and I will adjust this post accordingly.

---

### Post by panafff on 2010-08-14
Cool thanks, it would be grat if you add screenshots ;)

---

### Post by k3lt01 on 2010-08-14
The relevant screenshots are in the Preliminary work thread. I'll grab some for you though and add them when I have a little time.

---

### Post by Joris Donders on 2010-10-30
hi I did all the steps you've mentioned (including a new script for background slide show). 
But only the last step isn't correct I suppose; I've been trying the gconf-editor command and in the side pane I've found the mode option. But when I go to the screensaver preference there is no new screensaver shown. So the OS doesn't add the new screensaver in the option list. How do I add this screensaver in the option list of preferences ? 

I really enjoyed this work out !!! Hopefully there is a solution for this...

great topic!!

---

### Post by k3lt01 on 2010-11-02
Hi Joris, I haven't come across the issue your referring to  myself but will test it out again in the next few days and get back to you with what I find. It will take a couple of days at least as my "playing" machine is currently getting a huge work-over (8 different versions of Linux will be installed. 3 Ubuntu, 3 Debian, 1 Mint-LMDE, and 1 Linux From Scratch LFS).

Thanks for posting and I will b in touch soon with what I find.

Cheers.

---

### Post by k3lt01 on 2010-11-07
Hi again Joris. I have gone through everything again and find no problem with the steps I have written out. I have spent the last week setting up this laptop as described in my last post and on the Ubuntu 10.10 install I made, not just copied and pasted, the lotr background slideshow and then went through the screensaver process. Everything works as it should.

Without seeing your files I can only suggest that you check them again and then go through the process again. If you want it may help to take notes as you go so if you find anything as you do it again you can give us the exact details.

---

### Post by artooro on 2010-11-08
Sorry, dupe post

---

### Post by artooro on 2010-11-08
I've been reading about this and it looks like custom screensavers should be stored in /usr/local/share/applications/screensavers instead. But that doesn't work either.

Also I've tried running the update-desktop-database command which creates

---

### Post by artooro on 2010-11-08
So I've been reading and it looks like custom screensavers should be in /usr/local/share/applications/screensavers instead. But even then gnome-screensaver does not pick it up.

Also I've tried running the update-desktop-database command which created a mimeinfo.cache file but that's it.

---

### Post by artooro on 2010-11-08
OK, just so everyone knows the only way I found to fix this was to create a debian package to install the screensaver.

---

### Post by Joris Donders on 2010-11-11
hi, the tutorial is right after all!! I've set the mode of the screensaver in random though and yes you're right it works !!!
So the last step I've changed the value to random and my own made screensaver was shown!!! Then selected in pref. the screensaver and yes DISCO !

Maybe there are some issues, I've pressed ENTER instead of ok in gconfig-editor, I don't know if that was the problem that I've encountered. But it worked.

Super Topic, I've made various links to this tread on my website and another forum (dutch) !!
Just loving this work-out !!!
Thx for this tutorial

---

### Post by k3lt01 on 2010-12-31
> **artooro said:**
> OK, just so everyone knows the only way I found to fix this was to create a debian package to install the screensaver.Sorry artooro for the late reply. There should be no need to create a deb package, I have done this many times and have not had any difficulty following the steps as I have posted it. Just as an aside I don't even know how to create a deb package :confused:

---

### Post by k3lt01 on 2010-12-31
> **Joris Donders said:**
> hi, the tutorial is right after all!! I've set the mode of the screensaver in random though and yes you're right it works !!!
So the last step I've changed the value to random and my own made screensaver was shown!!! Then selected in pref. the screensaver and yes DISCO !

Maybe there are some issues, I've pressed ENTER instead of ok in gconfig-editor, I don't know if that was the problem that I've encountered. But it worked.

Super Topic, I've made various links to this tread on my website and another forum (dutch) !!
Just loving this work-out !!!
Thx for this tutorialHi Joris, sorry for the very late reply. It's good that this worked for you, there does seem to b some problems for some people that unfortunately I am unable to copy.

Also thanks for th heads up about posting links to this thread. I'll take a look at your site and link to it in various places if you would like.

Have a good new year :popcorn:

---

