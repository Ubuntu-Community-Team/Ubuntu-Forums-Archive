---
title: "sound card issues"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by garth653 on 2008-05-06
Hey everyone, I'm an absolute noob, just recently decided that my life can go on without Windows.  I've installed Ubuntu 8.04 on my computer, a dell inspiron, x86 type and am trying to hash out some issues.  I have searched for this problem on this thread, and on Google, and have tried numerous things to get it hashed out, but I just can't figure out what my problem is.  Situation:  I have a Sound Blaster sound card, pretty sure it's a emu10k1 Audigy 2.  I say I'm pretty sure because that is what I've found in the terminal using lshw when I first installed.  I cannot figure out how to get the rear speakers going, and I'm getting static from the speakers.  The static happens when my computer is "thinking hard."  Like when I have multiple programs running. I can turn the sound down and still hear it.  I've tried playing with Alsamixer: no success.  I've installed emu10k1 tools and cannot figure out how to use them.  Also, now my soundcard has changed names on me.  It is saying just Audigy, dropped the 2.  Did I change it's name by installing alsa-tools?  If anyone can help steer me in the right direction, I'd be very grateful.  Like I said, I'm new to this whole deal, so some of the tech jargon is a little over my head right now, but I'm trying.  Any ideas?  Any specific info I need to post to help?

Thanks.

---

### Post by sp0nge on 2008-05-06
This worked for me:

First, we’re going to create/edit a file called .asoundrc in your home directory.

Open a terminal session (Applications ->Accessories -> Terminal) andÂ  type:
```

gksudo gedit .asoundrc
```

Once gedit opens up either add this to the blank file, or change your .asoundrc file to the following:

  ```
  pcm.!default {
    type plug
    slave.pcm “surround51&#8243;
    slave.channels 6
    route_policy duplicate
    }
```

Hopefully this will help out.

---

### Post by bobpur on 2008-05-06
Your problem sounds similar to one I had a while back. You didn't put the specs of your Dell in your post so I don't know if these suggestions will work for you or not. Here are a couple things to try:
1. Fiddle with your volume controls. In Ubuntu there is a volume control in the upper right corner of your screen. It looks like a small speaker with curved lines in front of it. Turn that one down while turning up the volume on your speakers. Depending on your speakers, having the system volume turned up all the way will distort the sound coming out of your speakers. 
2. Remove the Audigy card and put it in a PCI slot as far from other PCI cards as you can get. This will reduce interference from other cards.
3. Remove the Audigy card entirely and plug speakers in to the motherboard speaker jack. It should be the light green one as it was on your Audigy card. You will be playing through your motherboards built in sound card. You may have to enter the BIOS to activate the onboard sound.
4. DiamondTek has a couple of soundcards on [www.newegg.com](www.newegg.com) that come in 5.1 and 7.1 configurations for between $20-$40. These cards compare favorably to the Audigy cards and might be worth consideration if you can't get your Audigy card going. These cards are linux friendly. The bundled software includes Audacity. A program found in many distros or able to be installed.

Good luck!

---

### Post by garth653 on 2008-05-06
Thanks for your quick replies.  Sp0nge, I'm at work now but I'll try that over my lunch break.  bobpur, I'm pretty sure my soundcard is already as far from the other cards as it can get.  My PC is a Dell Inspiron 9100, Pentium D, don't know the speed, I can get it when I get home.  Dell lists my soundcard as a SB0358.

---

### Post by garth653 on 2008-05-06
Well, I tried what sp0nge said, and now I cannot play music.  When I try to open a song in Amorok it says xine was unable to initialize any audio drivers.  I can hear the beep when I go to configure sound and click the test button.  Oh well, back to work and I'll keep trying later.

---

### Post by garth653 on 2008-05-06
bump for help

---

### Post by garth653 on 2008-05-09
Well, in case any other noobs are following this, I am still no closer to getting this to work.  Soundcard works like a champ when I choose to boot Windows:  all speakers work.  I got rid of Amarok, and installed Banshee, got the sound working again, but still no rear speakers.  I plugged the speakers into the PC soundcard, and they all work, but it's just not nearly as good quality as the SB.   I may be going to a new sound card, but that really is not what I want to do.  The whole reason I installed Ubuntu was dissatisfaction with Windows, and high costs. I might have unrealistic expectations, but I was hoping to be able to do everything in Linux that I could do with Windows, and do it without spending any money.  So far I'm just about there, just can't get this sound card deal figured out, and I can't find a Linux program comparable to Nero. (not even Nero for Linux)  Oh well.  

I'm still open to suggestions if anyone has any ideas.  I'm more than happy to provide more info if you just let me know what you need.

---

