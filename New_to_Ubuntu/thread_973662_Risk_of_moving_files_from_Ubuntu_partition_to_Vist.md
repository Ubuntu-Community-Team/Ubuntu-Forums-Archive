---
title: "Risk of moving files from Ubuntu partition to Vista partition"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by fishscale on 2008-11-06
I'm pretty new to Ubuntu, and I understand that I'm not really at risk for any windows malware infecting my linux partition.  However, I dual boot with Vista, and I am concerned about something I pick up on my Ubuntu partition infecting the Vista partition.  I already asked this question in the security forum, and got the really great answer to keep my Vista partition unmounted while in Ubuntu; that way, I would have to copy the file over to Vista for the infection to occur.  

However, what if I were to copy something over to the Vista partition?  What are my options for scanning files and protecting the Vista partition?  I am mainly concerned about stuff I get off of torrents, mainly music, maybe movies.  I am not that knowledgeable about viruses, spyware, and how they spread.  Can executables be embedded inside a video or audio file (one that can be played, not one that is labeled as a video or audio file but is actually something else)?  Basically, I am asking that if I download stuff with torrents and test the file out in Ubuntu, and it checks out ok, is it safe to move it to the Vista partition?

---

### Post by bumanie on 2008-11-06
Install clamav and clamtk via synaptic and scan any files prior to moving them.

---

### Post by handydan918 on 2008-11-06
> **fishscale said:**
> I'm pretty new to Ubuntu, and I understand that I'm not really at risk for any windows malware infecting my linux partition.  However, I dual boot with Vista, and I am concerned about something I pick up on my Ubuntu partition infecting the Vista partition.  I already asked this question in the security forum, and got the really great answer to keep my Vista partition unmounted while in Ubuntu; that way, I would have to copy the file over to Vista for the infection to occur.  

However, what if I were to copy something over to the Vista partition?  What are my options for scanning files and protecting the Vista partition?  I am mainly concerned about stuff I get off of torrents, mainly music, maybe movies.  I am not that knowledgeable about viruses, spyware, and how they spread.  Can executables be embedded inside a video or audio file (one that can be played, not one that is labeled as a video or audio file but is actually something else)?  Basically, I am asking that if I download stuff with torrents and test the file out in Ubuntu, and it checks out ok, is it safe to move it to the Vista partition?

Maybe. If clamav has the virus definition...otherwise, no.

---

### Post by fishscale on 2008-11-07
Forgive my ignorance, but can a virus be implanted in a valid audio or video file?  Or can you only have an audio or video file that doesn't really play anything, and is actually an executable?  What I'd like to do is to check each file I download by opening it in Ubuntu to see if it will play a file before moving it.  If this doesn't really mean it's safe, then I guess there's no real way to safely use torrents.

---

### Post by fishscale on 2008-11-08
bump?

---

### Post by otz070 on 2008-11-08
Not really sure if this helps, but from what I have seen I have never come across an audio file (mp3 or wave I mostly use mp3s though) however I have seen infected soundfont archives (If you use a daw or work with audio you would use these in case you are wondering:) I had some on my windows system and had a virus that infected them They werent to begin with) 

So generally with mp3s you should be pretty much safe the same with images
(though with images there are programs to hide executables within an image but I would assume that in most cases the only way to access the exe would be to actually use the program to encode the exe or other file within (This is called stegography-hiding data within data)  (I havn't actually come across any files like this that I know of yet)

As for movies I would be more cautious as These are often packed within archives and though the actual movie file may or may not be itself infected sometimes small hidden files containg viruses or other malware are sometimes contained within

You said that you are using torrents so the best way I could reccomend at all is to pack the files into archives (possibly using the .7z forrmat) If you use wine with your ubuntu you could run spybot s&d on wine to scan each archive/file ([www.winehq.com](www.winehq.com)) (Wine is a windows emulator for linux) or if you don't want to mess with wine then just copy the archives to a disk/usb drive or whatever and scan them with your windows

Anyway hope you find some solution:)

---

### Post by otz070 on 2008-11-08
oops the website for wine should be [www.winehq.org/](www.winehq.org/)
should work eitherway though just incase

---

