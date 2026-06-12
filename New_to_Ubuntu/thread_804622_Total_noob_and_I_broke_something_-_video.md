---
title: "Total noob and I broke something - video"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by watson524 on 2008-05-23
Hi all,

for years I've been going to take my "old machine" and go to linux on it, so after perusing these forums and the great amount of help, I've done it. I have the newest version of the other OS running on my main machine but put 8.04 on the old machine. Installed easily no major issues, and I was just starting to play. Mind you, I've used UNIX machines a lot but not where I had to configure them or anything. 

I am running a KVM switch to save some space and all was fine. I've heard of issues using a USB converted to PS/2 mouse with a KVM switch so I'm using a regular PS/2 mouse. I have an acer AL1714 monitor. I noticed that programs were really large and I couldn't really move them in order to see all buttons in the lower right. Checked resolution, only 800x600 available. Ok I figured I'll sort that out later. OS told me it had a bunch of updates to install so I figured it knew more than I did, have at it. Comes back up, log in, right after login says "input not support". Ok..... so since I read that error can be caused (on the "other" OS) by KVM switch mice ports, I yanked out the mouse, put my old MS scroll wheel mouse right into the box (USB with PS/2 converter), boot up, still the same thing. I don't really have a way to run 2 monitors (not enough space) but I am kind of stuck because it won't show me anything past the log in (hence I think the update did something with the drivers). I don't mind reinstalling the OS since the setup was so darn easy if anyone thinks that's what needs to happen.

Sorry this is long but I'm trying to be as detailed as possible.

thanks!

---

### Post by kilroy423 on 2008-05-23
I think that you might have a driver issue.  I would reinstall and then get the latest and greatest drivers for your video card.

Kilroy

---

### Post by watson524 on 2008-05-23
Ok thanks. I'm pretty busy this weekend but I'll try to get to it and report back.

Where can I get drivers for the video card? I think I've only ever seen Windows based ones on most websites. Do most manufacturers have Linux ones available?

---

### Post by ubuntu-freak on 2008-05-23
You shouldn't have to reinstall Ubuntu. 
 
Boot into recovery mode and type "xfix", which will then attempt to autodetect and configure your hardware again. To reach the login screen after that, type "startx". If your resolution is still wrong, press Alt+F2, type "gksudo displayconfig-gtk" and your password when prompted. You can then select your screen type/resolution.
 
You didn't mention what graphics device you are using, but Ubuntu should handle that for you anyway.
 
Nathan

---

### Post by watson524 on 2008-05-24
Ok it appears that booting into recovery mode worked. And then I hit the auto adjust button on my monitor and it sorted out the "screen spilling over" issue.

thanks!! I'm sure now that I can see things, I'll have a bunch more questions. My idea of linux was always x windows and command line based so this isn't nearly as hard as I thought it'd be.

---

