---
title: "VLC buggy in 12.04"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by davidbilla on 2012-05-22
Hi,

Did anyone else have problems with vlc 2.0.1 in 12.04? In a fresh, fully updated install of 12.04, I installed vlc from the repository. I found that quite a few things didn't work as expected.

1. Clicking on the icon on the top panel brings the vlc menu in which only the Play option is enabled. Stop, Previous, Next are all grayed out.

2. Short jumps (Alt+direction) don't work.

3. The audio gets disabled if long jumps/progress bar are used to seek avi files.

Any solutions?

---

### Post by flemur13013 on 2012-05-22
1. Not sure what you mean.

2. Short jumps (Alt+direction) work fine for me.

3. "Long jumps/progress bar are used to seek avi files" works fine for me.

You might want to try a different AVI file, or try your current file on the old version if possible  - sometimes VBR audio is troublesome.

---

### Post by davidbilla on 2012-05-22
Thanks for the quick reply.

1. Sorry if that wasn't clear. I was referring to the vlc icon on the top panel in the desktop. Clicking on it shows 'Hide VLC media player in taskbar', Play, Stop, Previous, Next etc., Of these four options, only Play is enabled (to play/ pause). The others are grayed out.

2 and 3. I have tried these avi files with vlc on 10.04. They all work fine there.

---

### Post by mc4man on 2012-05-22
If by icon you mean the vlc indicator icon in the panel, that's provided by the _sni-qt_ package  and it is absolute junk. There is no way to disable vlc from using it so I remove the package itself, then add Vlc to the systray whitelist. That icon works perfectly.
(if you don't know how to add an app to the whitelist ask.

Additionally you can get some basic control of vlc thru the sound menu (speaker icon), several ways to get it to show if not there.

Easiest is just open vlc > Tools > Preferences & make any option change, then save, -  (like "Allow only one instance" ), then close & re-open vlc - a log out/in may also be needed
Otherwise you need to add Vlc to interested players in gsettings - again ask if need be

---

### Post by davidbilla on 2012-05-23
Hi, thanks for your reply. Yeah, I would like to know how to add vlc to systray whitelist and also how to get vlc to show up when I click on speaker icon, like the way it shows up in your screenshot. Only rhythmbox is shown there for me.

---

### Post by sioxs on 2012-05-27
VLC was working fine up until a few days ago when an update reverted the sound control  to go back to the internal sound device. I use a PCI Creative soundcard and there has always been recognition issues from time to time. In this case, every other program worked flawlessly and for some reason VLC  produce sound  through the onboard device. ( Which I couldn't hear since nothing was plugged into it )
Switching the output message in VLC to debug mode produced these lines:
```

pulse debug: connected to sink 1: alsa_output.pci-0000_00_06.1.analog-surround-40
main debug: using audio output module "pulse"
pulse debug: listing sink alsa_output.pci-0000_01_00.0.analog-surround-40 (0): SB Live! EMU10k1 Analog Surround 4.0
pulse debug: listing sink alsa_output.pci-0000_00_06.1.analog-surround-40 (1): Built-in Audio Analog Surround 4.0
 
```After quite a bit of searching and finding nothing relevant it was easy to fix.
 System Settings > Mutimedia > Sound and Video Configuration 
Where I found the devices had been shuffled out of order selecting the correct device to "preferred" and moving it up the list immediately restored the sound in VLC and the plug-in for firefox.
Sometimes I find I over complicate things by assuming its a driver issue or config somewhere and in this case it was solved just by checking the basics.

---

### Post by davidbilla on 2012-05-29
Hi all,

Short jumps work fine - the problem was with the laptop keyboard! But the problem with audio remains. Jumping/seeking to a position in many avi or mp4 files (that work fine in other computers) multiple times cuts the audio. Haven't figured it out yet.

Edit: Figured out the problem with the keyboard. The keyboard layout was set to English (South Africa), in which the Right Alt key was not Right Alt! Changed to international - English(US) and it works fine now! But the problem with audio remains.

---

