---
title: "What is &quot;v4l from repo&quot;?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by OKnotOK on 2008-06-19
Can someone tell me what this means and how to do it real quick? Someone advised me to do it to fix a problem, but I don't know how and I'm stuck! 

Thanks!

---

### Post by Duck2006 on 2008-06-19
> **OKnotOK said:**
> Can someone tell me what this means and how to do it real quick? Someone advised me to do it to fix a problem, but I don't know how and I'm stuck! 

Thanks!

What advise did they give you and what steps did you do to fix the problem?
What was the problem?

---

### Post by GavinZac on 2008-06-19
"from repo" means from the official ubuntu repositories (a repository is somewhere you keep a bunch of stuff, organised).

They're telling you to install Video4Linux (v4l) from those repositories, using the Synaptic Package Manager

---

### Post by OKnotOK on 2008-06-19
I'm trying to fix some problems with using my webcam. I've posted several threads about it over the last couple days, but most of them have been "bump" posts, lol! 

Someone just told me that my camera ought to work when I install "v4l from repo" but I don't know what that means. 

The basic problem is that I get an error message when I try to use Camorama that says "could not connect to your device. /dev/video0"

However I know its connected properly because I can see my image in Cheese & Ekiga.

(I don't know how to use Ekiga and don't really care to - but was told to see if my cam worked there.)

I am trying to record videos using my webcam (Logitech Quickcam Deluxe). 

With Cheese the audio keeps messing up -- there is a link to the problem below.

[http://launchpadlibrarian.net/15444818/SoundBug.ogg](http://launchpadlibrarian.net/15444818/SoundBug.ogg)

Output of lsusb 

> Bus 002 Device 004: ID 058f:6377 Alcor Micro Corp. 
Bus 002 Device 003: ID 046d:09c1 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0461:4d16 Primax Electronics, Ltd 
Bus 001 Device 001: ID 0000:0000 

---

### Post by OKnotOK on 2008-06-19
> **GavinZac said:**
> "from repo" means from the official ubuntu repositories (a repository is somewhere you keep a bunch of stuff, organised).

They're telling you to install Video4Linux (v4l) from those repositories, using the Synaptic Package Manager

I would thank you but I can't see the little medal to do it with!

---

### Post by GavinZac on 2008-06-19
> **OKnotOK said:**
> I would thank you but I can't see the little medal to do it with!

I think you found it! :D I hope it fixes your problem. If it doesn't, keep asking questions in this thread so they won't get mixed up everywhere else on the forum (and I guess it'll make it easier for my lazy **** to find them).

---

### Post by OKnotOK on 2008-06-19
> **GavinZac said:**
> "from repo" means from the official ubuntu repositories (a repository is somewhere you keep a bunch of stuff, organised).

They're telling you to install Video4Linux (v4l) from those repositories, using the Synaptic Package Manager

I searched for "video4linux" in the synaptic package manager, and didn't get anything by this name. But @ the top of the list of things it pulled up was Camorama -- the program I'm trying to get to work (ie its already on my computer). 

What a mess!

---

### Post by Duck2006 on 2008-06-19
System -> Administration ->Synaptic Package Manager then click on search and type in v4l and it will come up make it for install the click on apply and it will install it for you.

---

### Post by OKnotOK on 2008-06-19
> **GavinZac said:**
> I think you found it! :D I hope it fixes your problem. If it doesn't, keep asking questions in this thread so they won't get mixed up everywhere else on the forum (and I guess it'll make it easier for my lazy **** to find them).

Well, I keep posting new threads because I ask a question, get an answer I half-way understand, post a follow-up question, and never get another response to the thread. 

I've been trying to solve this problem for a week. 

I've never had anything like this happen on the Ubuntu Forums before. I've always found more help than I needed. Except for this problem. I don't get it!

---

### Post by OKnotOK on 2008-06-19
> **Duck2006 said:**
> System -> Administration ->Synaptic Package Manager then click on search and type in v4l and it will come up make it for install the click on apply and it will install it for you.

Should it be named SPECIFICALLY "V4L" or "Video4Linux"? Nothing by that specific name comes up. As I said, the top of the list is Camorama... Which is what I'm trying to use already!

---

### Post by Duck2006 on 2008-06-19
I found v4l-conf i found 21 packs in there, not sure witch one/s you should load.

---

### Post by GavinZac on 2008-06-19
> **OKnotOK said:**
> Should it be named SPECIFICALLY "V4L" or "Video4Linux"? Nothing by that specific name comes up. As I said, the top of the list is Camorama... Which is what I'm trying to use already!

if you search for "v4l", and scroll all the way down, is the XOrg V4L driver installed (green)? It most probably is. I don't think you need to install anything, if Cheese shows you the video

I can't understand why Cheese would break the audio when recording. Does it do this when you're just recording a sound? Like, in Sound Recorder?

---

### Post by OKnotOK on 2008-06-19
> **GavinZac said:**
> if you search for "v4l", and scroll all the way down, is the XOrg V4L driver installed (green)? It most probably is. I don't think you need to install anything, if Cheese shows you the video

I can't understand why Cheese would break the audio when recording. Does it do this when you're just recording a sound? Like, in Sound Recorder?

Well, the sound recorder won't open now! It says "your audio capture settings are invalid. please correct them in Multimedia Settings" It didn't say that before... I don't know what changed.

Audacity appears to be recording, but doesn't play back anything.

---

### Post by OKnotOK on 2008-06-19
I found and installed v4l-conf and that doesn't change any of the problems. 

Could it be that the webcam I am using is not supported by camorama?

---

### Post by OKnotOK on 2008-06-19
> **OKnotOK said:**
> Well, the sound recorder won't open now! It says "your audio capture settings are invalid. please correct them in Multimedia Settings" It didn't say that before... I don't know what changed.

Audacity appears to be recording, but doesn't play back anything.

Okay I clicked around and fixed the problem with sound recorder.

Audacity is still the same, but I don't care about that -- for anything besides testing anyway.

---

### Post by GavinZac on 2008-06-22
Did that fix the problem with Cheese too?

---

### Post by felixq78 on 2010-02-10
> **GavinZac said:**
> "from repo" means from the official ubuntu repositories (a repository is somewhere you keep a bunch of stuff, organised).

They're telling you to install Video4Linux (v4l) from those repositories, using the Synaptic Package Manager

That's great, how do we access this repository?

---

### Post by Miljet on 2010-02-10
> That's great, how do we access this repository?

The answer is right in front of you. It says "using the Synaptic Package Manager."

---

