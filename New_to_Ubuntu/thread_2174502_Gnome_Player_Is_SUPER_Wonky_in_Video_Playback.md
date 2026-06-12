---
title: "Gnome Player Is SUPER Wonky in Video Playback"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by benjamin6 on 2013-09-14
Alright, after trying out multiple OSes like Puppy Linux and whatnot, I think I'm settled on Lubuntu, and have it freshly installed.

A few moments ago I just tried to play a DVD of *Avatar: The Last Airbender*, and playback was horrible. It was able to start up the DVD, but for some reason had very blocky graphics, seemed to be playing extra fast, and had a weird sound-effect of a strumming rubberband. When I tried selecting play it simply froze up. 

Now, I know it isn't a hardware issue since I've been able to play DVDs on my laptop before, so Gnome seems to be the problem. I'm a newb, but I suppose a "codec" or the like is missing? What can I do to get Gnome up and running well?

---

### Post by montag dp on 2013-09-14
A few suggestions:

1) Try the DVD on a dedicated DVD player or another computer just to make sure it works (if you haven't done that).
2) Try VLC player if the above works.
3) Someone can correct me if I'm wrong, but I believe you can get proprietary codecs and the like by installing lubuntu-restricted-extras.  You may try that if #2 doesn't work:

(in the terminal)

sudo apt-get install lubuntu-restricted-extras

---

### Post by benjamin6 on 2013-09-14
I don't have another computer or a separate DVD player for testing, unfortunately. 

I installed VLC Player and not only am I getting the same problems, but some weirder ones too.

With *Airbender*, it does the same thing graphically. Blocks and choppiness, with no playback except for the messed up menu.

I put in *Duck Soup*, which is a much cleaner disc, and both Gnome and VLC won't load it.

Then I put in a James Bond movie and both Gnome and VLC Player gave me a solid green screen with choppy music.

---

### Post by TenPlus1 on 2013-09-15
Sounds like your internal DVD player needs a good clean...  Buy a cd head cleaner and use that a few times to see if it helps as dust and other nasties can build up inside DVD drives and cause playback problems...

---

### Post by benjamin6 on 2013-09-15
I'm inclined not to think that's the problem. Just a few short weeks ago I played a DVD with little trouble at all, and there was no problem with video or audio. 

I suspect it's the operating system, missing dependencies, or whatever since I was watching that DVD on the OS Puppy Precise, and the problems that I've described now all occur on Lubuntu.

---

### Post by benjamin6 on 2013-09-15
Okay, so through a test I figured it is indeed the operating system or something with the programs themselves.

I installed Racy Puppy Linux onto a USB and booted up from that, and the DVD works just fine from there. No graphical or sound issues whatsoever. Thus, some tweaking with the Lubuntu programs is needed.

What do you think? I know I could just use Puppy to play DVDs without installing it, but I'd rather not go through the trouble of switching if a fix is possible. This seems rather a tricky problem to look up. I'm puzzled as to what search terms I could use to do some research myself.

---

