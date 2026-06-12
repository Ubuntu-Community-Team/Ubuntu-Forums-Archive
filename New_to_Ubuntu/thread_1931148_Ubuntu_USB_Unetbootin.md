---
title: "Ubuntu USB Unetbootin"
date: 2012-02-24
forum: New to Ubuntu
---

### Post by Likeacupcake on 2012-02-24
Hello, newbie here!

I'm trying to setup Ubuntu on a new build computer.

I had a few minutes looking over the BIOS system, just checking everything works, and noticed that boot priorities were disabled. However, that is not an issue, as it is defaulting to a USB I've set up using Unetbootin for a Ubuntu boot disk.

When I plug it into my laptop I get the auto-start asking me what I want to do, but when I boot my desktop and select either to boot from the USB or to install the system, the screen just goes black and appears to hang.

The screen remains black, but power is still active.

I'm looking to set the system up to boot from USB, not installing anything. Means I can have my pull harddrives in public space, and boot in any system I want to use.

Can anyone tell me what I'm doing wrong? Thanks for the help!

---

### Post by HeroOfCanton on 2012-02-24
Could be a video driver problem since it's going blank when the GUI starts. Unity is heavy on 3D and sketchy with some video cards. Might want to try an older ubuntu (10.10 or older), or another distro like Lubuntu, Xubuntu, or Kubuntu (in order of light to heavy).

---

### Post by Likeacupcake on 2012-02-24
I'm trying to set up 10.04_live.

Should I look at another version of Linux? Or just Ubuntu?

---

### Post by SuaSwe on 2012-02-25
Are you already using Ubuntu on another machine? If so I'd suggest using the Startup USB creator - it's geared for Ubuntu so at least you'll know the USB drive is most likely OK. :) 

If it persists, you could try the suggestion [here]("http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html"). I seem to recall having the same problem some time in the past, and setting quiet splash resolved it for me.

---

### Post by Likeacupcake on 2012-02-25
Thanks for your help, but I've past that.

Now I'm trying to get my ODD and HDD to work: The system isn't recognise them, and my ODD's tray doesn't extend.

Can't see what's wrong, and my search and been fruitless thus far. I will succeed!

---

### Post by stn21 on 2012-02-25
> **Likeacupcake said:**
> ... Now I'm trying to get my ODD and HDD to work: The system isn't recognise them, and my ODD's tray doesn't extend. ...

What exactly do you mean by "system" and "recognize" ? 

Are you able to boot ubuntu now ? Does ubuntu not recognize your HDD? Or does the BIOS not recognize your drives? If your CD-drive does not work at all that sounds like a problem with its data- or powercable or the drive itself.

Try to fix the CD-drive and boot ubuntu-10.04-desktop as live-CD. That **always** works for me if everything else fails. If you really cannot boot this live-CD I would say some of your hardware is broken.

Unetbootin is a really cool tool but sometimes it can cause boot-problems. So for testing start with the ubuntu-live-CD, use it to check your drives and other hardware, and only when everything works go on to USB. 

Or just skip USB-boot and install from CD.

---

### Post by Likeacupcake on 2012-02-25
> **stn21 said:**
> What exactly do you mean by "system" and "recognize" ? 

Are you able to boot ubuntu now ? Does ubuntu not recognize your HDD? Or does the BIOS not recognize your drives? If your CD-drive does not work at all that sounds like a problem with its data- or powercable or the drive itself.

Try to fix the CD-drive and boot ubuntu-10.04-desktop as live-CD. That **always** works for me if everything else fails. If you really cannot boot this live-CD I would say some of your hardware is broken.

Unetbootin is a really cool tool but sometimes it can cause boot-problems. So for testing start with the ubuntu-live-CD, use it to check your drives and other hardware, and only when everything works go on to USB. 

Or just skip USB-boot and install from CD.


By system I mean everything: The BIOS doesn't list the HDD, but does list the ODD. The ODD tray doesn't open, and I don't have access to a burner of any description, hence why I'm trying to boot from USB, or I would have gone with a disk and made short work of all this.

The ODD LED lights up on start up, and when I press the eject button, but then stops and the tray does that extend.

Pain in the ***, as I've spent my entire afternoon trying to get this to work, and now I'm stumped at one little problem:mad:

---

### Post by Likeacupcake on 2012-02-25
I've just got back from a chat with someone at a computer store, who had a look at both.

It appears an electrical fault in one has shorted out both.

Thanks for your help!

---

