---
title: "Remove Libre Office and replace it with Open Office"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by benjie1 on 2013-02-18
Is it possible to remove Libre Office and replace it with Open Office. Using Ubuntu v 12.04 and 32 bit. Thanks


Thanks to all. It works great. As a newbie and an older man, 76 yo, it is easier to stay with what you started with. Im my case it was OO. I guess LO is good but just not used to it and really don't like changes as a rule. So I wanted to go back to OO. Tks again for the help.

Bob

---

### Post by kabukiM0n0 on 2013-02-18
You can yes, doing the following
```
sudo add-apt-repository ppa:upubuntu-com/office  sudo apt-get update sudo apt-get install openoffice
```

Yet from what I read, now it is called Apache Open Office as the original people dropped it and was picked up by Apache. Even though the differences between Libre and Open are minimal.

---

### Post by ajgreeny on 2013-02-18
Just curious, but why change to OOo from LO; do you have a specific reason?

---

### Post by speartip on 2013-02-19
I must admit I have changed from LO to OO.
It just seems more stable & integrates better with unity IMO.
I downloaded the .deb from here:
[http://www.openoffice.org/download/other.html](http://www.openoffice.org/download/other.html)
& followed the installation instructions from here:
[http://forum.openoffice.org/en/forum/viewtopic.php?t=50119](http://forum.openoffice.org/en/forum/viewtopic.php?t=50119)

---

### Post by rewyllys on 2013-02-19
I suggest that you try installing LibreOffice 4.0, which has quite a few improvements over v. 3.5.  Here's a URL at which to start:

[http://blog.documentfoundation.org/2013/02/07/the-document-foundation-announces-libreoffice-4-0/](http://blog.documentfoundation.org/2013/02/07/the-document-foundation-announces-libreoffice-4-0/)

---

### Post by fuorviatos on 2013-02-19
> **speartip said:**
> 
It just seems more stable & integrates better with unity IMO.


Interesting opinion. I wonder about the reason..

---

### Post by auxilium on 2013-02-19
Hi,

You may check these sites:

[http://www.linuxinsider.com/story/76331.html](http://www.linuxinsider.com/story/76331.html)

[https://blogs.apache.org/OOo/entry/your_top_questions_answered](https://blogs.apache.org/OOo/entry/your_top_questions_answered)

[https://wiki.documentfoundation.org/Main_Page](https://wiki.documentfoundation.org/Main_Page)

[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)



Cheers,

---

### Post by speartip on 2013-02-19
> **fuorviatos said:**
> Interesting opinion. I wonder about the reason..

Not sure.
All I can say is that on my system, the program & documents seem to open smoother & quicker with OO.
The other thing that bugged me with LO, is that everytime I opened or closed the program, it wasn't smooth at all, like the screen seemed to jerk, this doesn't happen in OO.
Not saying there was anything wrong with LO, & will try out LO 4.0 when its been out a few weeks, but for me at present OO seems more solid.

---

### Post by fuorviatos on 2013-02-19
> **auxilium said:**
> Hi,

You may check these sites:

[http://www.linuxinsider.com/story/76331.html](http://www.linuxinsider.com/story/76331.html)

[https://blogs.apache.org/OOo/entry/your_top_questions_answered](https://blogs.apache.org/OOo/entry/your_top_questions_answered)

[https://wiki.documentfoundation.org/Main_Page](https://wiki.documentfoundation.org/Main_Page)

[http://en.wikipedia.org/wiki/LibreOffice](http://en.wikipedia.org/wiki/LibreOffice)



Cheers,
Thanks, I've looked those websites over, but the question still remains.
Why is Ooo better integrated with Unity than LO, seeing that Canonical made a switch to the second one?

---

### Post by vanadium on 2013-02-19
What do you mean with "better integrated"? Does the globale menu work better? Do menu hotkeys, such as Alt+o to open the format menu work?

---

### Post by Hagar Delest on 2013-02-19
LO is known to be rather heavily bugged until each of their X.Y.3 or even .4 version so beware. There are also glitches that may be new features like this one: [[Solved] Cannot remove "Manual Column Break"]("http://forum.openoffice.org/en/forum/viewtopic.php?f=7&t=59763").

---

### Post by speartip on 2013-02-20
> **vanadium said:**
> What do you mean with "better integrated"? Does the globale menu work better? Do menu hotkeys, such as Alt+o to open the format menu work?

Purely my experience with LO.
Extra icons kept appearing in the Unity Launcher.
I periodically had to delete all the LO icons & relock them to the Launcher. And as I mentioned earlier, opening & closing the program with OO was a lot smoother than with LO.
This might not be the same for everyone, & I must admit LO worked fine in KDE, but with Unity IMO, OO performs better.


Edit...
I have just followed the suggestion in post 5, & installed LO 4.0, (was going to wait, but since this thread have been itching to try it).
First impressions are, big improvement, & seems to have addressed my previous issues.
Will report back after a while using it.

---

