---
title: "I think I broke Ubuntu..."
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Wudugast on 2008-10-25
This will be a lengthy post, so I thank you in advance for reading it and for any advice you can give.

The problem starts with Windows, but it totally broke Ubuntu.

My difficulty began last night when I was playing Spore in Windows Vista Ultimate. I had Winamp, Azureus, AVG Antivirus, and of course, Spore open. Everything was going swimmingly until Spore suddenly crashed. I thought it was just an error in the game, but my computer suddenly slowed to a crawl, froze, and practically begged me to cold-reboot it.

I did.

The BIOS booted normally after the restart, and I went into Windows again only to be made told that I'd have to wait a while because the computer was installing updates. I have it set to notify me when updates are downloaded and to allow me to decide which ones to install. I was given no such choice. Anyhow, the updates install, and when I tried to play Spore, I got a monitor error that said "out of range."

Deleting all the settings for the game seemed to work and I eventually got it back. However, I got the same "out of range" error when I tried to boot Ubuntu.

I went into recovery mode and discovered that it thought I didn't have a graphics card. It wouldn't even let me specify which kind I had in the drop-down menu. Now, I obviously do have a graphics card and it isn't broken - I was able to fix Spore and play it again in Windows.

Here's what I did to try to get Ubuntu back:

I was going to go for a fresh install like I did with Spore. I downloaded a new live CD and burnt it off, but I wanted a text file from my Ubuntu drive, so I downloaded this program that claimed to be able to let me look at ext2 and ext3 formatted drives in Windows. It worked, but it didn't work. My Ubuntu drive is an ext3 and was still journaling, so it wouldn't mount in Windows.

I gave up and formatted the drive. Then I burnt a live CD and rebooted. This caused my computer's monitor to blink like it wasn't getting a signal. I ejected the live CD and did another cold reboot. I still didn't get a picture, but Windows eventually loaded.

I went into the live CD and used the option to install some files that would help the computer boot it on the next reboot.

That doesn't work.

Nothing works anymore. The monitor keeps blinking like it's not getting a signal, and I don't even get a BIOS or anything.

I'm using an NVIDIA nForce 680i SLI motherboard, and I can't find the button you push that makes it revert to factory BIOS settings.

I'm still wondering what happened to my computer and why a video game screwing up in Windows caused Ubuntu to die on me.

What happened and how can I fix it without being able to see the screen?

---

### Post by DrMelon on 2008-10-25
It sounds as if your gfx card is dying. Anything that flips out and then you aren't able to give your monitor a proper video signal seems to imply your gfx card is either overheating or dead.
Check it for dust.

---

### Post by Squish on 2008-10-25
Got any compressed air, its the best way to clean a dusty computer. The dishwasher only works for keyboards.

If that doesnt work, swap for another video card, if you have one laying around. and if it still doesnt work, then the problem might be something else.

---

### Post by Paqman on 2008-10-25
> **DrMelon said:**
> It sounds as if your gfx card is dying. 

That would be my guess too. Has your motherboard got onboard video that you can switch to in the meantime?

---

### Post by _Narcisse_ on 2008-10-25
Yeah, as DrMelon said, your graphics card may be dead and/or on its way. The best would be to test it on another computer, but if you can't, look on it for melted transistors or things like that. If your mother board have a VGA out, try plugging your monitor on it and see what happens.

---

### Post by Wudugast on 2008-10-25
Okay, I've got it running on a different graphics card, but something is still wrong.

When I try to boot it up without the Ubuntu Live CD, the GRUB tells me "error 17"

With the Live CD, all I get is a black screen. What's going on?

---

### Post by Aaron850679 on 2008-10-25
try burning another live cd that may fix it

---

