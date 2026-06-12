---
title: "Some bugs on my ubuntu 24.04"
date: 2024-09-01
forum: New to Ubuntu
---

### Post by ravnathan on 2024-09-01
Hi I'm fairly new to ubuntu 24.04, this is my 4th month using and I have been having a blast. I'm gonna throw some long context so then you will understand it better and hopefully can come out with a solution. Please skip to the 3rd paragraph if you wanna just go straight to the issue, thank you

About 10 years ago when I was eager to learn about installing new OS that I never touched before, so I tried using linux mint and ubuntu when I had to still manually sign the partition stuff etc. Life happened, and I stopped doing anything productive for 10 whole years due to personal stuff. Right now I wanna regain my rights as a human being to live a normal life and be curious about anything related to tech like how I used to 10 years ago. I'm learning web development at the moment through a bootcamp, and my old laptop was an ASUS with 8th gen intel chip, 8GB. It came with preinstalled Windows but I thought I wanna use ubuntu again to just explore about the OS while exploring web development at the same time. I didn't run into issues on ubuntu's end for the first 1 month but rather on the hardware part since using Postman can take quite the resource, 

I decided to grab a brand new Lenovo ideapad and I installed ubuntu alongside windows, as in dual boot thing, so that I wouldn't get rid of the original WIndows that came with the laptop in case I need anything to do with it.
There come issues with it. First few days using it was ok but first week I started encountering issues that is recurring up to this day, everyday. First issue is, you know how it looks like when a monitor or a tv if you break them physically? Like broken screen stuff, that kind of stuff happens everyday, frequently, whenever I'm browsing, coding, or scrolling down discord, but once I refreshed the browser page for example, the shattered looking pixels thing disappeared. I just have to refresh the window or move tab to another app and it will disappear, but in like 15 to 20 mins it will happen again.

Second issue is the sound driver, first 2 months was ok, even with the first issue that I stated before, I tried to just bear with it, but sound issue was so annoying. Looking back when I first installed ubuntu on this current laptop (Lenovo one) or even before this laptop (ASUS one), whenever I plugged in jack audio (headphone) the prompt will appear on which kind of sound device that I've just plugged in. It stopped doing that but instead it never detected any jack and just proceeded playing the music or whatever I was playing not through the external device but through the inbuild speaker. I tried to troubleshoot the issue and learned about alsamixer stuff (which btw it's also an opportunity for me to learn dealing with ubuntu stuff related so in a sense it's good that a problem came up) and on terminal I didn't even find my headphone on the list, so after hours of googling I found a solution which was "sudo [FONT=var(--ff-mono)]alsactl restore" and it started to detect my headphones BUT no prompt to use whatsoever whenever I plugged in anything. The biggest one is that, when I'm playing music and I go afk, I come back to my laptop and my music will suddenly turn into the loudest high-pitched shriek of noise that you would ever hear and I hurt my ears because of that.

Any solution would be appreciated, if reinstalling ubuntu is the solution then it'll have to wait until my bootcamp is over which is in a month. Here's my laptop spec if that would help to pinpoint the issue:

[/FONT]**Lenovo IdeaPad Slim 5 14IMH9**


[LIST]
[*]Processor : Intel® Core&#8482; Ultra 5 125H, 14C (4P + 8E + 2LPE) / 18T, Max Turbo up to 4.5Ghz, 18MB
[*]Display : 14&#8243; WUXGA (1920×1200) IPS 300nits Anti-glare, 60Hz, 100% sRGB
[*]Memory : 16GB Soldered LPDDR5x-7467, not upgradable
[*]Storage : 512GB SSD M.2 2242 PCIe® 4.0×4 NVMe®
[*]Graphics : Integrated Intel® Arc&#8482; Graphics
[*]Wireless : Wi-Fi® 6E, 11ax 2×2 + BT5.2
[*]Speakers : Stereo speakers, 2W x2, optimized with Dolby® Audio&#8482;
[/LIST]

---

### Post by TheFu on 2024-09-03
Check the GPU drivers for any screen issues.
Also, try using X.org instead of Wayland as the display server.  This is controlled pre-login using the 'gear' on the login screen.

Sound is confusing.  There are 3 different tools.  ALSA, PulseAudio and Pipewire.  Pipewire is used on 24.04 and generally has good feedback from most users. A few other distros moved to it years ago.  I've never used it - 24.04 is too new for my needs - so I cannot help.  Just be thankful that you aren't having to deal with PulseAudio.  
ALSA was a pain too. We had to manually edit config files with it. No GUI that worked. The Pulse GUI was a layer over ALSA and as bad as it was, it was better for most users (just not me).

---

