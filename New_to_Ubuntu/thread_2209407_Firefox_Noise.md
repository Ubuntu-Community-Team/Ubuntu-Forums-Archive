---
title: "Firefox Noise"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by ArlieS on 2014-03-05
I'm running Ubuntu 12.04 LTS with Unity. I believe I last installed patches approx. 2 weeks ago. This morning I did "sudo apt-get update" and "sudo apt-get upgrade" to pick up the fix for GnuLTS. All seemed fine. I then did "sudo shutdown -r now". All still seemed fine. 

Then I launched firefox. It reloaded most of my open tabs - I cancelled some, based on the list it displayed.

My speakers started playing a variety of drivel, including something about working at Hooters, and various things that must have been advertisements. I can't find any tabs that contain start-when-launched videos or other indications of likeliness to blather at me. The system has been up for 46 minutes, and I still have noise coming out of my speakers - at the moment it's some kind of music. 

Is there any way to:
 1) find which tabs are generating the noise
2) control the privilege of using the speakers within firefox
3) determine whether the noise is coming from some misfeature like invisible windows - thus explaining why I can't find the culprit windows.
4) Ban firefox itself from playing audio, without disabling it for the whole system. (Not what I want, but better than having to keep the speakres physically turned off.) 

I've turned off the speakers physically, not in time to avoid the resulting headache. And I guess I can try reloading firefox without my open tab collection, in case that helps. (Maybe the noise is a new firefox feature, trying to interest me in whaever drivel they've been paid to promote?)

But does anyone have a better approach?

[Edit: it's perhaps worth noting that I'd killed and restarted firefox earlier in the day, before updating Ubuntu, with pretty much the same collection of tabs (perhaps a few more), and had *not* had a bunch of noise spew out of my speakers. Also, the launch after reboot I got one of the messages from Firefox which told me that Firrfox itself had been updated, suggesting a new bug/misfeature added to Ubuntu 12.04's version of firefox some time in the last fortnight, rather than a collection of noise-making tabs.]

---

### Post by Impavidus on 2014-03-05
Open pulseaudio volume controller. If you can't find it, the terminal command **pavucontrol** should open it for you. In one of its tabs it shows a list of all applications playing sound at that moment. You can mute them individually to find the culprit.

If you think it's Firefox, closing the offending tab may work. Navigating the offending tab to a known silent website may work too and is reversible.

---

