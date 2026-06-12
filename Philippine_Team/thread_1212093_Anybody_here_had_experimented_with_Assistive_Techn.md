---
title: "Anybody here had experimented with Assistive Technology"
date: 2009-07-13
forum: Philippine Team
---

### Post by reneorense on 2009-07-13
Hi, mejo kakaumpisa ko pa lang makasanayan ang Ubuntu and I have been using it with the aide of its Assistive Technology features...

I'm just wondering if there's anyone here whom had tried using Orca screen reader and attempted to change its voice synthesizer to a better one. Currently, it uses eSpeak for its synth, pero I was hearing these past months na pwede rin daw gumana ang Eloqune na synthesizer dito (Eloquence is the one JAWS for Windows is using), pero wala akong idea as to how I could acquire such sa Bubuntu...

Anyone? At least konting idea to get me started in chaging my synthsizer..?

8-)

---

### Post by Samhain13 on 2009-07-13
I try Orca on-and-off (but you know that already, hehe). Not sure how to change the TTS though. But what I know is that you can set the eSpeak parameters so that you can "remix" the active voice-- like change its pitch and reading speed. I'll explore this in the near future and share what I find out.

But there are other assistive technologies that I use every day; like the zoom and ADD features of CompizFusion.

OT: welcome to the Philippine LoCo forum! Tried approving your friend request just now but it doesn't want to work. Will try again tomorrow, there's probably a glitch in the board.

--[Edit]--

I did a quick search on Google and I got something:
[http://ubuntuforums.org/showthread.php?t=808389](http://ubuntuforums.org/showthread.php?t=808389)

Check out **mj86**'s post. It basically says that you need to install a new TTS synth and if Orca can work with it, you'll be able to choose the synth over eSpeak in the configuration window. But in the example given, the synth is Festival.

I can't seem to find anything about Eloqune or Eloquence in Ubuntu.

--[Edit 2]--

OK. The instructions mentioned in the thread above maybe obsolete. Here's how I was able to use Festival instead of eSpeak in Orca.

1. go to Synaptic
2. search for "Festival" and install it, a library will be installed with it
3. search for "festvox" and choose a voice package; if you don't do this, the Orca preferences window will not load (it just greys-out) and when you run Festival in the terminal, you'll get a warning and eventually an error if you tell it to say something
4. you can install additional voices too, if you like

Once you have Festival and at least one voice installed, you can fire-up Orca and go to the preferences and select it over eSpeak. If you downloaded multiple voices, you can select one from there too.

If there are other TTS synths out there, you'll more-or-less follow the same steps. Install the synth and install at least one voice. :)

---

### Post by reneorense on 2009-07-13
> **Samhain13 said:**
> I try Orca on-and-off (but you know that already, hehe). Not sure how to change the TTS though. But what I know is that you can set the eSpeak parameters so that you can "remix" the active voice-- like change its pitch and reading speed. I'll explore this in the near future and share what I find out.

But there are other assistive technologies that I use every day; like the zoom and ADD features of CompizFusion.

OT: welcome to the Philippine LoCo forum! Tried approving your friend request just now but it doesn't want to work. Will try again tomorrow, there's probably a glitch in the board.

--[Edit]--

I did a quick search on Google and I got something:
[http://ubuntuforums.org/showthread.php?t=808389](http://ubuntuforums.org/showthread.php?t=808389)

Check out **mj86**'s post. It basically says that you need to install a new TTS synth and if Orca can work with it, you'll be able to choose the synth over eSpeak in the configuration window. But in the example given, the synth is Festival.

I can't seem to find anything about Eloqune or Eloquence in Ubuntu.

Thanks a lot in advance... I sure will need a lot of help going around GNOME. I managed to install the speech dispatcher, but there weren't no voices yet... I guess it has something to do with buying the voices, so until then I go with eSpeak on my Orca in tandem CompizFusion's Magnifier for my accessibility walk through in Ubuntu...

8-)

---

### Post by Samhain13 on 2009-07-13
^ Ngee, gising ka pa pala. I just edited my post (see Edit 2). :lolflag:

OT: really excited that you're here. When you get this all sorted out, maybe Ubuntu and other FOSS will get an opportunity to be tried by more people from our handicapped/disabled communities. And hopefully, we'll gain more users from that sector; the developers are always motivated when their user-base widens.

From what I've heard, mahal pala talaga ang licensing ng accessibility software sa ibang platforms, making the software itself inaccessible to people that need it. How ironic.

---

### Post by dannybuntu on 2009-07-13
wrong post...sorry...move along...

---

### Post by markedisonchua on 2009-07-16
> I have it on USB but I deleted it. NO IDEA TO USE IT.
Well I am puzzled

---

