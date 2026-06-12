---
title: "Anyone know what this error message means????"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-18
Ubunteros,

I was trying to use Rhythmbox to play an mp3 file but received this message.

Anyone know what it means?

Thanks

---

### Post by ajmorris on 2008-11-18
hi there,
that error is quite ambiguous. Could you please start rhythmbox from a terminal, and post the output from it here when you try to play the file.
 
 
AJ

---

### Post by suomalainen on 2008-11-18
> **ajmorris said:**
> hi there,
that error is quite ambiguous. Could you please start rhythmbox from a terminal, and post the output from it here when you try to play the file.
 
 
AJ

How do I sttart from terminal? Sorry for the stupid question... I guess it's sudo something???

---

### Post by scorp123 on 2008-11-18
> **suomalainen said:**
> I was trying to use Rhythmbox to play an mp3 file but received this message. Did you install MP3 support? MP3 being a proprietary technology is not installed per default on Ubuntu (the makers of Ubuntu would otherwise risk becoming potential targets for some nasty lawsuit, especially in the USA thanks to the DMCA and some other countries with similar laws ...). If you did not install MP3 support then no program is able to play MP3 files. This might be the case here?

Easiest and quickest way to get all the codec goodies:
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by ajmorris on 2008-11-18
it is in the menus under accessories -- i think, however, you can press ALT+F2 and type in ```
gnome-terminal
``` into the dialog box. Then once the terminal is open, just type rhythmbox into it, and press enter, then when rhythmbox is open, try to play the file in it, and post here the whole output that is in the terminal (if it is long, please use envelops)
 
 
 
AJ

---

### Post by dhtseany on 2008-11-18
The terminal is located under Applications -> Accessories and it's the black, square icon with a white letter in it. Then, if you don't know the command already, being typing "rythm" and hit Tab. That might help figuring out what command is needed to start it (Sorry not on my UB box at the moment ;))

Peace
Sean

---

### Post by suomalainen on 2008-11-18
I need to back up so you all know whats going on.

I recently installed Ubuntu 8.04LTS on a friends Compaq Presario 5140.

I then visited [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) in order to install all multimedia related "things".

I've done 7 such installs and all, except this one, have been flawless.

When I tested the PC after all was said and done, I got the error message that I then posted and you responded to.

During the Interim I got hold of a sound card from another machine and installed that instead of using that which is built onto the motherboard.

Now I can launch Rhythmbox and listen to Mozart.... :> So that is good now.

But I still have a problem with watching DVD's. If I use VLC ot Totem they both crash and the movie doesnt even launch. The same is said about live video streams that I visit on the Internet.

Based on the attached snapshot, do I have sufficient HDD space to launch these apps? Or is something else going on.

I really would like to get the DVD player runnning tonight.

Thank you for helping me!!!

---

### Post by ajmorris on 2008-11-18
Your hard disk space is fine :)
can i please get that terminal output? Also, i have not used rhythmbox before, are you sure it can stream movies?
 
If it doesnt, can paste the output of vlc or totem, and we can troubleshoot them instead :)
 
 
AJ

---

### Post by suomalainen on 2008-11-19
Is it really necessary??? As mentioned above it's working now!

Except for my DVD....... This doesn't work.

---

### Post by CLomax on 2008-11-19
I had that error when I had the wrong sound setting.

Right click the speaker like thing on the top right then select 'Preferences'. Make sure Alsa is selected.

<EDIT>
> As mentioned above it's working now!

*facepalm* ignore my message.
</EDIT>

---

### Post by suomalainen on 2008-11-19
"that error" occured with bad sound card. Read above....

If I never got it, because a working card was already there, i would never have received this msg.

Therefore this ain't applicable to this. 

Sorry.

---

