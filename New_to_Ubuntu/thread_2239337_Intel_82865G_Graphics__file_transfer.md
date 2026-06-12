---
title: "Intel 82865G Graphics / file transfer"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by John_Briggs on 2014-08-13
Hello Everyone, I am in need of guidance. I have a hard time understanding some of the tutorials and faqs. I need some lay man assistance and information.

First off is my PC and general information

Dell Dimension 3000
Intel Pentium 4 CPU 2.80GHz, 2.0GB RAM, Intel 82865G Graphics Controller

I am converting from Windows XP Home Edition SP3 32-bit to the latest version of Lubuntu. I am all for leaving XP behind me and I have no use for Windows 7.

My issues and concerns are as follows.

1. Video Graphics have the parallel lines in them no matter what video player I use. I use VLC Media Player primarily but even the default video player does this. I have tried changing the Video defaults and made sure to have proper codecs as far as I can tel. But nothing changes. I have this constant line blurring into my videos. I only play 720p and below. It Varies between x264 mp4, x264 mkv but primarily xvid avi.

2. I have always used the network option on my PC under XP to transfer files from this PC to a PC upstairs and vice versa. The PC upstairs is Win 7 Home Premium SP1 64-bit. I am able to move files between the 2 PCs with great ease via Network connection and shared workgroup. I cannot figure out how to do this with Lubuntu's latest versions. I have read documentation on this matter but cannot figure out how to understand any of it.

If any additional information is needed then please ask and I will do my best to provide it. Please be patient and kind to me. I really need help and will listen to more experience users with great patients of my own.

Thanks, John

---

### Post by Dennis N on 2014-08-13
I will give you my simple method of transfering files between Windows and Linux computers:

Install Filezilla on the Windows machine
Install openssh-server in Lubuntu (it's in the Ubuntu Software center).

Work from the Windows machine, you can use Filezilla to connect by SSH to your Lubuntu system and transfer files in either direction.

(For just a couple of files, you might as well use a USB flash drive and walk them to the other machine.)

Sorry, but I can't give any suggestion on the video issue.

---

### Post by Rob Sayer on 2014-08-13
Ad far as codecs go, linux is blissfully free of most of the issues with codecs that Windows suffers from because you can't corrupt is at the 'registry' level so easily.  VLC doesn't need codecs because it uses its own libraries.  So does SMPlayer, which is my favorite.

All I've ever done for codecs is install ubuntu-restricted-extras, which is one of the 1st things on my post install to do list.  I rarely install from untrusted 3rd party ppa's and if such a program wants to replace any part of my existing codec libraries I won't install it.

Your video problems may be caused by trying to use openGL output codec modules, and I don't think that video adapter works with openGL.  Try setting the video output module to x11.

Try searching with something like "ubuntu Intel 82865G", but don't blindly start copying and pasting stuff into the terminal.  A lot of that stuff is for older ubuntu versions.

---

### Post by John_Briggs on 2014-08-13
> **Rob Sayer said:**
> Ad far as codecs go, linux is blissfully free of most of the issues with codecs that Windows suffers from because you can't corrupt is at the 'registry' level so easily.  VLC doesn't need codecs because it uses its own libraries.  So does SMPlayer, which is my favorite.

All I've ever done for codecs is install ubuntu-restricted-extras, which is one of the 1st things on my post install to do list.  I rarely install from untrusted 3rd party ppa's and if such a program wants to replace any part of my existing codec libraries I won't install it.

Your video problems may be caused by trying to use openGL output codec modules, and I don't think that video adapter works with openGL.  Try setting the video output module to x11.

Try searching with something like "ubuntu Intel 82865G", but don't blindly start copying and pasting stuff into the terminal.  A lot of that stuff is for older ubuntu versions.

I actually have tryed them all as OPENGL doesn't work right at all. I still get the lines no matter what. So that's why I am asking here as my searches have not yielded a fix as of yet. I appreciate your time though.

> **Dennis N said:**
> I will give you my simple method of transfering files between Windows and Linux computers:

Install Filezilla on the Windows machine
Install openssh-server in Lubuntu (it's in the Ubuntu Software center).

Work from the Windows machine, you can use Filezilla to connect by SSH to your Lubuntu system and transfer files in either direction.

(For just a couple of files, you might as well use a USB flash drive and walk them to the other machine.)

Sorry, but I can't give any suggestion on the video issue.

I cannot afford a huge usb flash drive unfortunately and I transfer a large amount of video files between computers. Is there any directions on how to do this perhaps. It needs to be as simple as possible for me like with my shared workgroup method if possible. Thanks for taking the time to reply.

---

### Post by mörgæs on 2014-08-13
For the Intel graphics it might help to add an xorg.conf. 
More info in the link in my signature.

---

### Post by John_Briggs on 2014-08-13
I would like to try that as I did read it yesterday but it is all greek to me. What do I do with that information. How do I do it?

---

### Post by mörgæs on 2014-08-13
Please tell exactly which part you don't understand so I can change the guide.

---

### Post by John_Briggs on 2014-08-13
I really would not know what to tell you. I am a newbie. I have no clue how to run commands or change things. The entire part about xorg.conf confuses me. I don't know what to do with that information. I am so sorry for not being geek enough for this stuff. I want to learn but my comprehension is greatly limited. I hate to be a bother. I just really want to fiogure my 2 issues out so I can get off of windows xp completely. I like Lubuntu. Other than the 2 issues I need to resolve there is nothing I need to change. It's great off the shelf otherwise. I suf the internet via Firefox and download stuff with Downthemall and that's great. I watch lots of tv and movie video files via VLC Media Player. And I transfer lots of files between my 2 PCs. I have no other uses than those. If I can just figure the 2 inital issues posted in my post then I am in perfect shape.

---

