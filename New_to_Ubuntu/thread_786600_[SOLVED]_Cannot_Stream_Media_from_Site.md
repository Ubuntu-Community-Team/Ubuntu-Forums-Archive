---
title: "[SOLVED] Cannot Stream Media from Site"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by kolisikepu on 2008-05-08
Hi Community,

I cannot stream radio or video online.  I've tried searching online for help before coming here, but couldn't find anything that made sense or worked.

Can any one help.  Here's a screendump of what I see when I try to stream something.

---

### Post by glennric on 2008-05-08
What site is it that you are trying to view?  Also, what browser plugin are you using?

---

### Post by billgoldberg on 2008-05-08
Doesn't that mean the video isn't available?

---

### Post by drs305 on 2008-05-08
Giving us the specific site address would be helpful. I went to the Drift site and it appears the videos are flash based. If you are running 32 bit, adding the Ubuntu Restricted Extras should enable flash (System, Add/Remove, All, Ubuntu Restricted Extras).

If you are running 64 bit, try this:
```
sudo apt-get install flashplugin-nonfree lib32nss-mdns
```

---

### Post by kolisikepu on 2008-05-08
Sorry... this would help wouldn't it.

[http://media.iinet.net.au/index.cgi?id=drift](http://media.iinet.net.au/index.cgi?id=drift)

I'm running Ubuntu Studio Hardy.

> What site is it that you are trying to view?  Also, what browser plugin are you using? 	

I've just added a screendump of my addons for Firefox if that helps too.

---

### Post by kolisikepu on 2008-05-08
> **drs305 said:**
> Giving us the specific site address would be helpful. I went to the Drift site and it appears the videos are flash based. If you are running 32 bit, adding the Ubuntu Restricted Extras should enable flash (System, Add/Remove, All, Ubuntu Restricted Extras).

If you are running 64 bit, try this:
```
sudo apt-get install flashplugin-nonfree lib32nss-mdns
```
It's not flash as I can play flash, such as 'youtube' sites and see flash adverts too.

---

### Post by drs305 on 2008-05-08
Now that I have the page address - that specific page is trying to open [http://media.iinet.net.au/media/intro-nonii.wmv](http://media.iinet.net.au/media/intro-nonii.wmv)  a windows media file. I tried using the firefox mediaplayerconnectivity plugin using vlc, mplayer, and smplayer and none of them could run that link.

I went to another site that has .wmv files and they all played fine, although on my machine it appeared that flash was controlling things. Here is the link to other .wmv files. You could try playing them and see if they work. I'm suspecting it's a problem with the specific site you are trying to access.
[http://www.metacafe.com/tags/wmv/](http://www.metacafe.com/tags/wmv/)

---

### Post by ubuntu-freak on 2008-05-08
See part 1 and 2 of my [sticky](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

---

### Post by kolisikepu on 2008-05-08
> **drs305 said:**
> Now that I have the page address - that specific page is trying to open [http://media.iinet.net.au/media/intro-nonii.wmv](http://media.iinet.net.au/media/intro-nonii.wmv)  a windows media file. I tried using the firefox mediaplayerconnectivity plugin using vlc, mplayer, and smplayer and none of them could run that link.

I went to another site that has .wmv files and they all played fine, although on my machine it appeared that flash was controlling things. Here is the link to other .wmv files. You could try playing them and see if they work. I'm suspecting it's a problem with the specific site you are trying to access.
[http://www.metacafe.com/tags/wmv/](http://www.metacafe.com/tags/wmv/)
That's a flash site where media files have been converted to flash.  My site is actual wmv's streaming... such as live TV.

Try this site to see if you can stream any live TV channels.
[http://wwitv.com/portal.htm?http://wwitv.com/television/index.html?http://wwitv.com/tv_channels/b3498.htm](http://wwitv.com/portal.htm?http://wwitv.com/television/index.html?http://wwitv.com/tv_channels/b3498.htm)

---

### Post by drs305 on 2008-05-08
> **kolisikepu said:**
> That's a flash site where media files have been converted to flash.  My site is actual wmv's streaming... such as live TV.

Try this site to see if you can stream any live TV channels.
[http://wwitv.com/portal.htm?http://wwitv.com/television/index.html?http://wwitv.com/tv_channels/b3498.htm](http://wwitv.com/portal.htm?http://wwitv.com/television/index.html?http://wwitv.com/tv_channels/b3498.htm)

Yes, that link runs fine with MPC plugin in firefox. However, MPC shows that as an asx file and not wmv

Added: I tried four other TV links from your link and they all played with MPC and vlc as well.

Added again: reassuringlyoffensive - Great Howto!

---

### Post by asrai on 2008-05-08
I'm also with iinet.  If you follow reassuringly offensive's excellent multimedia how-to (go to the multimedia and video forum and it is a sticky there) and install gecko media player with its firefox plugin (you will need to remove the totem and mplayer firefox plugins) it will work perfectly.

I have no interest at all in drifting but I got it all set up a few days ago just to see if it would work. :rolleyes:

---

### Post by ubuntu-freak on 2008-05-08
> **asrai said:**
> I'm also with iinet.  If you follow reassuringly offensive's excellent multimedia how-to (go to the multimedia and video forum and it is a sticky there) and install gnome-mplayer with its firefox plugin (you will need to remove the totem and mplayer firefox plugins) it will work perfectly.

I have no interest at all in drifting but I got it all set up a few days ago just to see if it would work. :rolleyes:

 
Thanks! :-) Thought I was being ignored.
 
Nathan

---

### Post by kolisikepu on 2008-05-08
> **reassuringlyoffensive said:**
> Thanks! :-) Thought I was being ignored.
 
Nathan
Who's the man.... Nathan is everybody!!  Give this guy a pay rise.

Nathan... thank you, thank you, thank you!  It's all working now.  And again... GREAT HOW TO! :guitar:

---

### Post by kolisikepu on 2008-05-08
Hey... where's the solved button gone??  I want to mark my thread as solved. :confused:

---

### Post by ubuntu-freak on 2008-05-08
> **kolisikepu said:**
> Who's the man.... Nathan is everybody!!  Give this guy a pay rise.

Nathan... thank you, thank you, thank you!  It's all working now.  And again... GREAT HOW TO! :guitar:

 
You're welcome. :-)
 
I don't think you can mark them as solved just yet, don't worry about it.
 
Nathan

---

### Post by kolisikepu on 2008-05-08
Sweet then...

Just wanted to say thank you and asrai as well.  I'm not into drifting, but it was streaming video that was annoying me.  Now I can stream Sydney's radio stations too online.  Your how to fixed all my streaming issues.  I've ignored it for so long now that I got fed up with it lately cause I want to use Ubuntu full time at home.

Sorry for the delayed thank you too.... I crashed for work before trying it.  Got it all working this morning.  Cheers big ears!

---

