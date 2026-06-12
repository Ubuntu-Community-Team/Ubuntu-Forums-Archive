---
title: "Cannot install Ubuntu 18.04"
date: 2018-08-17
forum: New to Ubuntu
---

### Post by thefirstcjones on 2018-08-17
First of all let me just say that I am brand new to Linux/Ubuntu in general. I feel as though I am mildly apt as far as computers go however and wanted to explore the other side of the OS world. So far it hasn't gone great. Let me get started.

I downloaded the Ubuntu iso and created a bootable USB drive using rufus with all the standard/default options selected, no fanciness, just a bootable USB, simple enough. I went into my bios on my laptop and disabled fast boot, secure boot. I ensured my bios was up to date by flashing it to the latest one (ASUS Version 301), and proceeded to boot into my USB that was recognized by my computer as bootable, so far so good. I clicked on the "try ubuntu first" option and that's the last that goes right. I get two screens that quickly flash with the words that say "error parsing pcc subspaces from pcct" then it goes to the purple Ubuntu screen and takes about one minute to load, then to a black screen that reads:

[0.032454] Error parsing PCC subspaces from PCCT

BusyBox "etc......."

(intramfs) Unable to find a medium containing a live file system

I've searched tons of forums and have tried: 
Putting it into a USB 2.0 port instead, no good, same effect.
Verifying the MD5SUM - it matches -, no good, same effect.
Reformatting the bootable USB in Rufus as GPT/UEFI and running UEFI-only boot in BIOS, no good, same effect.
Doing the same as above but with legacy mode activated as well, no good, same effect.
I have tried all of these in just about every combination plus some others I'm sure I'm forgetting as well.

Here's my hardware info:
ASUS X540LA
Intel i3 5020u
Intel HD Graphics 5500
4GB RAM
120GB SSD
Windows 10 Home (Up to date)

This seems like a prime system for Ubuntu, no dedicated graphics, simple, clean system. I figured, "what could go wrong?" My first experience with Linux hasn't been a pleasant one so far, here's to hoping someone can help me out before I decide to throw in the towel. Maybe it's not for me if I can't even get the darn bootable USB to run right? :confused:

Edit: I realize this probably should have been posted on the installation forum... Not sure how I can move it myself so someone may need to move it for me if necessary. Apologies.

---

### Post by oldfred on 2018-08-17
since new user ok here, if you want it moved I can do that.

Some SSD also need firmware updates.

Some other Lenovo with same issue but they said UEFI update solved it, or newer nVidia driver.
[https://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed](https://askubuntu.com/questions/670509/error-parsing-pcc-subspaces-from-pcct-acpi-pcc-probe-failed)

fixed in very new kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528684](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1528684)

---

### Post by thefirstcjones on 2018-08-17
Thanks for the reply, I see you're from SW Florida! Sarasota dweller here myself.

It's up to you as to whether you want to move the thread, I don't care either way, just want to follow the rules and be as relevant as possible with my post.

I didn't think about the SSD firmware, but since my issues have been coming from the "try Ubuntu before install", I thought that my issues would have nothing to do with my storage because it's not being accessed yet. Perhaps I'm wrong in assuming that. Regardless, I'll look into updates.

That very thread is what prompted me to update my bios in the first place during my research. Unfortunately, like I wrote before, it didn't make a difference. As for the Nvidia driver, my machine doesn't have an Nvidia GPU and therefore would not need the driver for one.

I'm a newbie with all this so I'm still learning terms like kernel, repositories, and other linux stuff that seems trivial to you pros I'm sure. But if I can't even install Linux to update the kernel, how am I supposed to update to the kernel on the bootable USB? Can I do it from GRUB? I'm pretty sure I can still get into that. Or is there a file on the iso that I can delete and drop the new kernel in? Forgive my ignorance here, I'm trying to figure it out. From most of my research I found that people who were updating kernels already had Ubuntu installed and did it from there, unfortunately that doesn't help my situation. Is there a way to make a bootable USB with the kernel you listed using windows?

---

### Post by oldfred on 2018-08-17
I have not had that problem, and it seems somewhat random.
Users make some changes or re-install with slightly different configuration and then it works.

I have never tried to use a newer kernel. And I would think a bit more advanced to add to installer.
I have 18.10 installed but have not updated in a week or two. It was using same kernel as 18.04 but will use a newer kernel, just not sure how new.

---

### Post by thefirstcjones on 2018-08-24
I suppose I should update this as I finally found a weird workaround that has nothing to do with any sort of code or file management skill whatsoever, haha. Here's the deal, after going through every setting possible with both the USB drive and bios. I stumbled upon a forum that said if they removed the USB drive while the purple "Ubuntu boot screen" with the little scrolling dots, then plugged it back into the same port, it would work. VOILA. IT DID! Finally was able to try Ubuntu and test drive the operating system a bit which is really all I wanted to do in the first place.

 I don't know why this issue happens. Perhaps it's something specific with my computer's bios. But ripping out the USB drive and then plugging it back in on the purple boot screen literally solved it for me. Everything seemed to work beautifully after that. Ran just as smoothly off my USB as windows does on my SSD.

Thanks oldFred for your help, it was a weird issue to have.

---

