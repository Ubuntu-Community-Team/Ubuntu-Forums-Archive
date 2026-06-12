---
title: "[SOLVED] Cant hear sound."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by misswham on 2008-07-04
Hello everyone and let me start off by saying I am so excited to be a part the Ubuntu family.  I am a total novice when it comes to Linux.  I am a basic user of any operating system.  I am a little more advanced in XP.  I have never typed a command in my life.  My question to day is, I can get music from my files to play but when I go to a website like Youtube I cant hear the sound.  What could be the reason why I cant hear videos on the internet but I can her sounds from my hard drive?  Also is it true that Linux is almost immuned to spyware, trojan horses and viruses?

Thanks in advance

---

### Post by nick_h on 2008-07-04
> but when I go to a website like Youtube I cant hear the sound.
I think you need the flash plugin for youtube.

> Also is it true that Linux is almost immuned to spyware, trojan horses and viruses?
Linux is built to be robust against viruses.  Commands will only run with root permission if you choose to run let them.

There is a good Linux Security post [here](http://ubuntuforums.org/showthread.php?t=510812).

---

### Post by S1xp4ck on 2008-07-04
Hi :)


Do you have flash plugin for your browser installed?

To check go to Applications>Add/Remove  and type flash plugin.  If the Macromedia Flash Plugin in the menu is unchecked, select it and click apply changes, this should install the flash support your browser needs.

Hope this helps you out.

---

### Post by ZabiGG on 2008-07-04
Hi Miss, and welcome to the community! :)

You do mention that you are a very basic user. If you really want to get the most of your Ubuntu experience, I'd suggest you start with the basics. There is a learning curve, and you might want to invest a few hours reading up on the terminal and ubuntu/linux to get a better feel of what you're getting into.

[This must-read sticky]("http://http://ubuntuforums.org/showthread.php?t=801404")

As well as the "Look here" link in m signature below will give you a great place to start. I personally recommend the beginner's guide to the terminal, so that you'll understand the instructions you might be given in these threads better.

Cheers and happy exploring to you,

Z.

---

### Post by misswham on 2008-07-04
There is no macromedia flash to check or uncheck in add or remove.  I went and check some other things that seemed to deal with audio and still no audio on you tube.  Any other suggestions?

---

### Post by Captain panda on 2008-07-04
Also, make sure that you close your media player before playing a you tube video. I have noticed that sometimes, leaving the media player open can stop he sound in videos.

---

### Post by misswham on 2008-07-05
i have tried making sure all flash players are check in the add/remove and still no sound.  i dont know what to do at this point.  

HELP::confused:

---

### Post by Redptc on 2008-07-05
Have you 'clicked' on the speaker icon to maximize the volume? You can also right 'click' on the icon to bring up 'Open Volume Control'. Both Master and PM should be Maximised or adjusted to a high level.

This reply may be too basic but you did say you were a beginner!

---

### Post by ChameleonDave on 2008-07-05
> **Redptc said:**
> Have you 'clicked' on the speaker icon to maximize the volume? You can also right 'click' on the icon to bring up 'Open Volume Control'. Both Master and PM should be Maximised or adjusted to a high level.

This reply may be too basic but you did say you were a beginner!

Well, he says that local audio files work, so that is not the problem.  The volume on the Youtube player could be muted though.

---

### Post by imjscn on 2008-07-05
> **Redptc said:**
> Have you 'clicked' on the speaker icon to maximize the volume? You can also right 'click' on the icon to bring up 'Open Volume Control'. Both Master and PM should be Maximised or adjusted to a high level.

This reply may be too basic but you did say you were a beginner!

Where is the speaker icon anyway? I can hear a little sound, I can see in the Settings Manager/Sounds that Ubuntu already recognized 2 sound cards in my PC, choose default or switch to either can't make a difference, I also see all the items below the device are checked.
where to go for a more detailed GUI style setting?

---

### Post by Redptc on 2008-07-05
My speaker icon is right at the top, next to the date.

It is black or grey and looks a bit like a ....speaker.

---

### Post by misswham on 2008-07-05
Still nothing.  I have been trying to do this for 24 hrs now.  Still nothing.  I hate giving up it is something I DONT do but this is the first time I dont see a light.  I have read through some of the other forum questions and I see people have had the same problem.  60% of my time is spent watching videos on You Tube, My Space etc and I cant get any of them to work.  I did go and check to make sure my Macromedia Flash was checked and it was.  I have checked a few other ones and nothing still. Does anyone have any other possibles for me to try.

---

### Post by ZabiGG on 2008-07-05
OK. Questions:

Have you enabled the restricted repositories (System > Administration > Synaptic Package Manager > Ubuntu Software tab, check all boxes, except Source), and medibuntu? (Medibuntu instructions below copied from [here)]("http://http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p4")

**6.1 Medibuntu**

 _Make sure Synaptic is closed for this or you'll get an error message _


Homepage:  [http://www.medibuntu.org/](http://www.medibuntu.org/)
 

Some packages like the Adobe Reader are not available in the standard-repositories. The easiest way to make such packages available to your system is to add the medibuntu repository. If you want to add this repository open a terminal ...
 ... import the repository ...
 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``` 

... import the gpg-key and update your package-list.
 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
If so, did you install the flash non-free plugin? Either search for flash non-free in Synaptic and install from there, or enter the following line in the terminal:

sudo apt-get install flashplugin-nonfree

By the way, flash is now Adobe and no longer Macromedia.

This should work.

Z.

---

### Post by WilhelmGGW on 2008-07-05
I am having the very same problem with no Flash sound on my new computer.  My volume adjustments are maxed. I hear other system sounds fine. And I find no flash to load in the list at Add Programs.  I need help, too.

Here's another clue.  Before I looked around to add software on my own, I went to the web in Firefox and attempted to view a Flash file on MSN.  My system automatically downloaded and installed the Adobe player, and then started the video.  Picture fine, no sound.

Maybe others have had the same experience.  Does that help the gurus here?

---

### Post by kansasnoob on 2008-07-05
Adding the proper Medibuntu repo as ZabiGG said and then adding flashplugin-nonfree from synaptic (or apt) is at the absolute top of my list. (while I'm in synaptic after adding the Medibuntu repo I also add non-free-codecs and acroread but that has nothing to do with your problems).

But, just in case you're not using Hardy, find the right Medibuntu repo for you and remember to add the GPG key:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

My next suggestion is to install gnome-alsamixer from synaptic (or apt), then you can find Gnome Alsa Mixer under Sound & Video:

[ATTACH]76503[/ATTACH]

[ATTACH]76504[/ATTACH]

As you can see there are many toggles to play with ........... so many it takes two screenshots to show them all.

---

### Post by kansasnoob on 2008-07-05
Also look here:

[http://ubuntuforums.org/showthread.php?t=849792](http://ubuntuforums.org/showthread.php?t=849792)

I saw that yesterday and was impressed enough to bookmark it.

---

### Post by WilhelmGGW on 2008-07-05
Yipes!  I tried everything here -- and now my sound doesn't work at all.  Not even the system level sounds (as at startup)!  I hope other folks are having better success.

---

### Post by WilhelmGGW on 2008-07-05
Doesn't Ubuntu have some slick diagnostic (troubleshooting) tool that one can use to figure out an apparently complex problem like this?

---

### Post by WilhelmGGW on 2008-07-05
Check out the first post in this thread!
[http://ubuntuforums.org/showthread.php?t=850574](http://ubuntuforums.org/showthread.php?t=850574)

I did what it says and it solved all of my sound problems!

---

### Post by misswham on 2008-07-06
I totally cleaned my hard drive, reinstalled xp, reinstalled unbuntu, did all of the updates, went to you tube, it prompted me to download adobe, did so and the video played and again still no sound.

This is the only thing about this operating system that is frustrating.  I really want to soley use this one, but I am a big youtube/myspace video watcher and I havent a clue at this point.

If this works I will be totally happy with the system and I can move on and start learning more about the workings of it but this is a simple thing I would think but it has turned into a big problem and I just dont know what to do but I have totally started over and still no sound on streaming videos but my videos and music plays on my hard drive and yes the volume is up on each of the videos I try and when I go to sound preferences and do a test i hear sounds on all of them expect sound capture under audio conferencing.  I dont know if that could be the problem.  This didnt make a sound the first time I downloaded also.

---

### Post by misswham on 2008-07-06
any more suggestions.  I did everything everyone suggested and all of my sound stopped.  i cleaned my harddrive and started over from scratch to get a possible solution.

Please someone, I know there are a lot of you who are extremely smart and can help me out.

---

### Post by ZabiGG on 2008-07-06
Again, you installed a version of flash that is not fully compatible with your system. Auto-installing software is a Windows thing. In Ubuntu you need to install what you need before trying to use it.

This [link]("http://ubuntuforums.org/showpost.php?p=5245736&postcount=2") includes instructions to install the non-free flash player and to uninstall the incompatible you insist on installing in Firefox.

I would also suggest you read up on the basics before you start making other modifications to your system (see "Look here" link in my signature). 

If you had problems with Ubuntu, why did you also reinstall Windows? That's an awful waste of time, and I'm sorry you had to go through that.

---

### Post by Mongao on 2009-05-22
> **ZabiGG said:**
> OK. Questions:

Have you enabled the restricted repositories (System > Administration > Synaptic Package Manager > Ubuntu Software tab, check all boxes, except Source), and medibuntu? (Medibuntu instructions below copied from [here)]("http://http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron-p4")

**6.1 Medibuntu**

 _Make sure Synaptic is closed for this or you'll get an error message _


Homepage:  [http://www.medibuntu.org/](http://www.medibuntu.org/)
 

Some packages like the Adobe Reader are not available in the standard-repositories. The easiest way to make such packages available to your system is to add the medibuntu repository. If you want to add this repository open a terminal ...
 ... import the repository ...
 

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
``` 

... import the gpg-key and update your package-list.
 

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
If so, did you install the flash non-free plugin? Either search for flash non-free in Synaptic and install from there, or enter the following line in the terminal:

sudo apt-get install flashplugin-nonfree

By the way, flash is now Adobe and no longer Macromedia.

This should work.

Z.

Hi all,

I am running 9.04 and have the same problem: no audio on You tube, but I have audio when I play videos from my HD; I have tried everything that is listed here in this thread, any other idea ?

Thanks

Mongao

---

