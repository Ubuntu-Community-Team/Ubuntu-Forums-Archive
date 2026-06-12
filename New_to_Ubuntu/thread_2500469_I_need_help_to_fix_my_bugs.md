---
title: "I need help to fix my bugs"
date: 2024-09-02
forum: New to Ubuntu
---

### Post by ravnathan on 2024-09-02
4 months in using ubuntu, 2 months while using this new laptop and I have a few bugs, some of the major ones are:

1. Screen bug, it looks like it's breaking, pixels stuff. I can't describe it well so I will attach some screenshots I've taken from these past 30 mins. Notice on 2nd picture, I sent a link on discord and some of the link was like sticky to the text field?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294191&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294192&stc=1[/IMG]

2. Audio bug, alsamixer messed up, it didn't detect my headphones, once I found a way to fix it now it produces high pitch audio noise that hurts my ears whenever my laptop is suspended.


What I've tried:

1. For my first problem I haven't tried anything since I'm in the middle of my bootcamp

2. Reinstalling alsamixer, [COLOR=#000000]sudo [/COLOR][COLOR=#000000][FONT=var(--ff-mono)]alsactl restore did the trick to detect my headphones, but it now makes high pitch audio noise stuff


Any help would be appreciated. Here's my laptop spec if it can help:

[/FONT][/COLOR][COLOR=#000000][INDENT]**Lenovo IdeaPad Slim 5 14IMH9**



[LIST]
[*]Processor : Intel® Core™ Ultra 5 125H, 14C (4P + 8E + 2LPE) / 18T, Max Turbo up to 4.5Ghz, 18MB
[*]Display : 14&#8243; WUXGA (1920×1200) IPS 300nits Anti-glare, 60Hz, 100% sRGB
[*]Memory : 16GB Soldered LPDDR5x-7467, not upgradable
[*]Storage : 512GB SSD M.2 2242 PCIe® 4.0×4 NVMe®
[*]Graphics : Integrated Intel® Arc™ Graphics
[*]Wireless : Wi-Fi® 6E, 11ax 2×2 + BT5.2
[*]Speakers : Stereo speakers, 2W x2, optimized with Dolby® Audio™
[/LIST]
[/INDENT]
[/COLOR]
[COLOR=#000000][FONT=var(--ff-mono)]
[/FONT][/COLOR]

---

### Post by TheFu on 2024-09-03
While alsa is part of the the normal Linux sound system in 22.04 and earlier. Touching ALSA shouldn't be needed since around 2016.  Use pulseAudio tools for all tweaking of audio.  If you are running 24.04 or later, pulse is replaced with pipewire, so using those tools is necessary.  There are tools like **pacmd** and **pactl** and **pavucontrol** to control almost everything.

However, I must admit that some update in the last 2 weeks has broken my audio (output and microphone) from working as expected in browsers on my 20.04 system.  Of course, mpv works perfect, as usual.  I haven't had time to reboot to see if a recent update (Saturday) may have addressed the issue.  I generally only reboot 1-2 times each month.

Any graphics stuff using Intel ARC GPUs is pretty new.  Can you open a bug with Intel?

---

