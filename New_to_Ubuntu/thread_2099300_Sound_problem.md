---
title: "Sound problem"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by RGNOME on 2012-12-29
Good evening gents.
Today I euthanased XP with 10.04.3 LTS.
All went flawlessly except the audio, not working.

I checked the terminal which provided the following:

r@r-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: AV710 [Chaintech AV-710], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AV710 [Chaintech AV-710], device 1: ICE1724 IEC958 [ICE1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AV710 [Chaintech AV-710], device 2: ICE1724 Surrounds [ICE1724 Surround PCM]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
r@r-desktop:~$ 

So, what can I do to get it working? please remember I am new at this.

Cheers

---

### Post by sudodus on 2012-12-29
Try with the Audio Settings dialogue window:

System -- Settings -- Audio Settings

Click the various tabs and tweak the settings available for Hardware, Input and Output.

It helps if you are playing something from an audio or video source (so that you will hear, when the audio starts working).

---

### Post by TheFu on 2012-12-29
> **RGNOME said:**
> Good evening gents.
Today I euthanased XP with 10.04.3 LTS.

Related to your question, there is an **Ubuntu Sound Troubleshooting** article easily [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) .  BTW, using "aplay -l" is a great start!

I'd like to point out that 10.04.x is about to be end of support in just a few months. If you are starting with a new install, you really, really, really, really want to start with 12.04 which will be supported for 5 years. "Support" means patches and updates - but mainly security patches. Further, the update from 10.04 to 12.04 should be relatively painless.  I just did it for Mom's PC last week.  **New deployments should not be using 10.04 desktop,** even if you hate the new GUI. There are easy solutions to get back to a non-unity-based GUI.

---

### Post by RGNOME on 2012-12-29
Of course!!!!
Simple.
Now is working.
Thank you!

---

### Post by RGNOME on 2012-12-29
Thank you TheFu, I tried 12.04 and I had 2 problems.
1. I disliked the GUI but that would not be a big problem (eventually I would get used to it)
2. my PC was running extremely slow.
I tried 12.04 and 11.10 with the same outcome.

---

### Post by TheFu on 2012-12-29
> **RGNOME said:**
> Thank you TheFu, I tried 12.04 and I had 2 problems.
1. I disliked the GUI but that would not be a big problem (eventually I would get used to it)
2. my PC was running extremely slow.
I tried 12.04 and 11.10 with the same outcome.

I understand completely!

The trick is to not use Unity.  XFCE and LXDE are more like the Gnome2 desktop you have on 10.04 and easily loaded through APT.

$ sudo apt-get install xfce4

Then logout and at the login screen, hit the little "cog" next to where you type in your userid. That should display a list of different desktop environments with XFCE listed.  Enjoy, while still being on a current OS.

When coming from Windows or OSX, most end users don't understand that the GUI is just another program under Linux. There are 50-1000 different options. If you don't like one, try a different version.  When you find one you like, you can easily remove all those others - including Unity.

While I haven't tried it, there is a growing community using "Cinnamon" as their preferred desktop now.  Personally, I find any "DE" overkill and prefer a straight WM - Window Manager setup.  I appears to me that 99.999999% of all bloat in Linux is with the desktop environments.  Those are not necessary to run programs at all.  Most end-users don't understand that.

---

### Post by RGNOME on 2012-12-29
TheFU, Thank you.
Point taken and accepted.
I will be using 10.04 as a learning tool until march 13 if I don't crash it first.
How do I make this thread 'solved'?

---

### Post by sudodus on 2012-12-30
> **RGNOME said:**
> TheFU, Thank you.
Point taken and accepted.
I will be using 10.04 as a learning tool until march 13 if I don't crash it first.
How do I make this thread 'solved'?
I'm glad that you solved the sound problem, and that your are planning for progress with the new LTS version 12.04 :KS

Click on **Thread Tools** at the top of this page and mark this thread as SOLVED! Finally, welcome back whenever you need help or have something to share :-)

---

