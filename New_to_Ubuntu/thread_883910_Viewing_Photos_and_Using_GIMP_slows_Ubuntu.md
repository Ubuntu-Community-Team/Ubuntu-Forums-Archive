---
title: "Viewing Photos and Using GIMP slows Ubuntu"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Teasdale on 2008-08-08
I've had Ubuntu for a few months and had no problems until the last couple of weeks. When I view photos, they take forever to load to the image viewer, and when I edit them in GIMP, my entire system starts to run slow and eventually halts altogether. Even after I close either or both programs, the system doesn't recover. If I didn't know any better, I'd think I had one of those viruses that runs a program in the background so that nothing else can run. The red "busy" light on the PC stays on as if it's struggling with some program, even when every program is closed. And the system never does recover. Last night it took so long trying to save a text file file that I finally went to bed and left it hanging. The next morning, that had resolved, but the red "busy" light was still on, and the computer was having trouble opening or closing anything - it seemed locked up, and I had to shut it off with the power button.

After a reboot, the computer is fine - until I either view photos or use GIMP. Then it has the same problem and doesn't recover.

I know I have a video driver problem - I have a NVidea card and none of the fixes have worked. But Ive lived with it for months and the PC has been fine. Could the wrong video-card driver make the computer lag to that extent?

---

### Post by billgoldberg on 2008-08-08
> **Teasdale said:**
> I've had Ubuntu for a few months and had no problems until the last couple of weeks. When I view photos, they take forever to load to the image viewer, and when I edit them in GIMP, my entire system starts to run slow and eventually halts altogether. Even after I close either or both programs, the system doesn't recover. If I didn't know any better, I'd think I had one of those viruses that runs a program in the background so that nothing else can run. The red "busy" light on the PC stays on as if it's struggling with some program, even when every program is closed. And the system never does recover. Last night it took so long trying to save a text file file that I finally went to bed and left it hanging. The next morning, that had resolved, but the red "busy" light was still on, and the computer was having trouble opening or closing anything - it seemed locked up, and I had to shut it off with the power button.

After a reboot, the computer is fine - until I either view photos or use GIMP. Then it has the same problem and doesn't recover.

I know I have a video driver problem - I have a NVidea card and none of the fixes have worked. But Ive lived with it for months and the PC has been fine. Could the wrong video-card driver make the computer lag to that extent?

I suggest you use a more lightweight image viewer.

A good one that is MUCH faster and does almost the same is Mirage.

It's in the Ubuntu repositories.

Seen in one of my screenshots here:

[http://billgoldbergmania.deviantart.com/art/Fluxbox-Desktop-Conky-1-94115441](http://billgoldbergmania.deviantart.com/art/Fluxbox-Desktop-Conky-1-94115441)

--

Completely remove the gimp using synaptic and install this version (double click to install).

[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

I think those problems could be some memory leak bug. I don't have that problem, but that doesn't mean much.

---

### Post by raul_ on 2008-08-08
Have you tried switching between the nVidia drivers and the open source drivers?

---

### Post by Teasdale on 2008-08-08
> **raul_ said:**
> Have you tried switching between the nVidia drivers and the open source drivers?

We tried everything. We looked up all the forums and tried every fix anyone had posted, and none of them worked - we ended up going back to what we started with and I resigned myself to living with what I had. Mostly everything works fine; windows look odd while they're closing or moving and I can't use any of Ubuntu's screensavers, but other than that, everything has worked fine until I started working with photos.

I think the only fix is to replace the video card, but with a 5-year old PC, I suspect there would be compatibility issues that would only cause more problems.

I'll try Mirage and the other GIMP.

--------------------

WOW! Mirage is a LOT faster! Thanks!

---

### Post by hrod beraht on 2008-08-08
> **Teasdale said:**
> I think the only fix is to replace the video card, but with a 5-year old PC...

I would think it was driver related, rather than too-slow hardware. My main desktop is 9 years old and only has an 8MB video card and it is remarkably fast even when editing huge GIMP files. Even my old Pentium III with 256MB RAM and a 4MB video card ran Ubuntu and GIMP well (before I turned it into a non-gui server), which is why I wouldn't think it was hardware-related if your computer is even newer.

Bob

---

### Post by Teasdale on 2008-08-09
> **hrod beraht said:**
> I would think it was driver related, rather than too-slow hardware.

Yes, I'm certain it's the driver. But if the driver issue is unsolvable (as it seems to be), then hardware is the next step. And I don't know if a new video card would sync with my motherboard, so I'm not sure that option is even feasible for me.

---

