---
title: "Sound problems"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Yes_It's_Me on 2011-07-09
I've never had sound working properly since Ubuntu adopted pulseaudio. No matter what (VERY COMMON) sound card and (VERY COMMON) 5.1 speaker system I use, adjusting any settings will result in noise and crashes and distortion. Hell not doing anything at all can result in those problems. It's just stupid. And it shits me because the Ubuntu developers focus so darn hard on making the system boot 0.00001 second faster or making these stupid scrollbars (which are very buggy at this point). Yet something as critical and simple as sound never gets any damn attention. Winodws 98 had better sound capabilities than Ubuntu in 2011. Believe me, I know.

People don't give up on Linux because the scrollbars are ordinary, they give up on it because they can't get sound working. Or networking. Or Video. Or the printer.

---

### Post by cariboo on 2011-07-09
Moved to a thread of it's own, as it is off topic for the thread it was in.

I'd suggest that you don't have a common sound system, as I run Natty/Oneiric/Debian stable on several different systems, ranging from an Apple G4 to my current nvidia based system, including Sound Blaster cards, I haven't had a problem with sound for years.

What audio chipset does your system have?

---

### Post by Yes_It's_Me on 2011-07-10
On my old machine I had a very common motherboard (ASUS A8N-E( with an AC97 chipset (just about the most common card there was at that time...). On my new machine I use integrated Intel audio and a PCI Asus Xonar DX. Both very common. My speaker system is a simple Logitech X-530 5.1 setup. Also very common. I've also tried using other speakers (even in stereo mode). And there's just no luck in the world for this. It's been better as of late (eg, right now if i change the 'subwoofer' setting in the sound preferences it doesn't flip out, but it doesn't do anything either). A few weeks ago it was flipping out, it probably will soon in the future, again.

The biggest issue I have is that we seem to implement things without them being anywhere near ready.

---

### Post by cariboo on 2011-07-10
You really didn't answer my question, what chipset? If you don't know, open a terminal and type:

```
lspci
```

That Asus sound card is pretty unusual,  as I've only seen it mentioned on the forums once before, and it may have been you that mentioned it.

When you run alsamixer, do all the channels show up like in my screen shot?

As you can see, mine shows front, surround and center.

**Edit:**I should have scrolled over to show the side and sub-woofer outputs too.

---

### Post by Mr. Picklesworth on 2011-07-10
> **Yes_It's_Me said:**
> I've never had sound working properly since Ubuntu adopted pulseaudio. No matter what (VERY COMMON) sound card and (VERY COMMON) 5.1 speaker system I use, adjusting any settings will result in noise and crashes and distortion. Hell not doing anything at all can result in those problems. It's just stupid. And it shits me because the Ubuntu developers focus so darn hard on making the system boot 0.00001 second faster or making these stupid scrollbars (which are very buggy at this point). Yet something as critical and simple as sound never gets any damn attention. Winodws 98 had better sound capabilities than Ubuntu in 2011. Believe me, I know.

People don't give up on Linux because the scrollbars are ordinary, they give up on it because they can't get sound working. Or networking. Or Video. Or the printer.

You might want to check out the ALSA project to be sure your sound card is supposed to work. When I was shopping for simple sound cards a while back, I was a little surprised to realize these things have a ton of variety and support is really kind of patchy. I decided on one that only recently gained support (Asus Xonar DS), and a few quirks were noted on that page. As expected, those quirks were exactly as expected through PulseAudio, because Pulse really just talks to ALSA and tells it what to do.

Here is ALSA's table about Asus sound card support: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus)
(Okay, I would check that myself but it seems their website is dead at the moment).

In short, consider filing a bug report for your sound card with ALSA, or following the existing ones upstream. Because, most of the time, (at this point), that's where the problem is.

---

### Post by lidex on 2011-07-12
Maybe you'll find something here:
[http://www.google.com/search?q=Asus+Xonar+DX&sitesearch=ubuntuforums.org](http://www.google.com/search?q=Asus+Xonar+DX&sitesearch=ubuntuforums.org)

Also with two sound cards there is sometimes a conflict, have you tried disabling onboard audio in bios?

---

