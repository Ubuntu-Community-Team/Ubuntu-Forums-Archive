---
title: "can I depend on ubuntu live"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by amrosama77 on 2012-08-14
I want to have stable ubuntu version but on my flash key
so can I depend on ubutn live
or
there is a better way to have full installation (bootable) on my 8G flash drive?

Thank you,

---

### Post by lukeiamyourfather on 2012-08-14
Define "stable" for your purposes. It won't be any more prone to crash than an installation on a hard disk if that's what you mean. Though a USB flash drive sure is a lot easier to break off, lose, or otherwise ruin compared to a internal hard disk.

---

### Post by amrosama77 on 2012-08-14
so you mean that i can't depend on a flash drive,

but the ubuntu live is not the problem here,

so what if I get a new external hard and put my ubuntu live bootable system on it?

---

### Post by Kalanac on 2012-08-14
Hi there.  A USB flash drive is fine and can run just like a regular hard drive, there are just a few little caveats:

- Pulling out the flash drive (or knocking it out while spinning around on your swivel chair like I did once) will be very bad.  You could physically damage the drive and if there was a read/write process going on at the time, data might very well be corrupted.

- Some computers, especially older ones, have problems booting up USB drives.  If you only plan on using it on one machine or a few that you know work, that's fine, but beware of possible problems on some machines.

- It'll run just a little bit slower than a regular hard drive.  It won't make a great deal of difference and it depends on how fast you need it to be running.  For general use it's more than sufficient.

If you're wanting to install Ubuntu on a flash drive, there are two approaches:

- Live Image: This is the .iso that is used to install.  The benefit of using the Live image is that it'll configure itself each time it boots, so it's great if you're planning on plugging into different machines.  You can set a persistence file in the Startup Disk Creator program that comes with Ubuntu.

- Install to USB: This is actually installing Ubuntu to the USB drive in the same way you'd install to a hard drive, rather than using the .iso image.  This has the benefit of faster boot times because the environment will be preconfigured, however, unless the computer you're plugged into is either the same or similar, you might find a few problems occurring ranging from slight to completely inoperable, not so good if you're planning on moving between machines.  This is because the install won't configure itself like the live install and will call up the configurations from the original install.

---

### Post by amrosama77 on 2012-08-14
Thank you so much Mr.Kalanac
so we can't consider ubuntu live (not stable), but it's just little be slower

but I focused some bad experience with it, I added a new user then restart and no system login and no system run at all :confused:

---

### Post by cryptotheslow on 2012-08-14
I have also noticed the Live environment does have some odd behaviours when creating new users - even with a persistence file.

Instead what I choose to do is actually a full install to the USB flash drive. As I only had one spare USB key the last time I did this, I burnt the ISO to a CD - booted up from that and then did the installation to the USB key. It is exactly the same as any other installation - just be very sure when going through the process that you choose the USB drive for the root / partition AND select the option to put the GRUB boot-loader on there also.

Once done, boot from the USB key and it behaves just like any other installation - just a little slower booting up and starting the larger applications. You can create additional users etc. just as you would on an installation to a hard-drive.

As long as you don't install any proprietary drivers it should boot on pretty much any PC as these days the vast majority of hardware is recognised at boot time.

---

### Post by amrosama77 on 2012-08-14
Thank You,

then after doing so how to set software center to install programs to my main hard not to my small 8G flash drive?

---

### Post by Jay MC on 2012-08-14
> **Kalanac said:**
> Pulling out the flash drive (or knocking it out while spinning around on your swivel chair like I did once) will be very bad.  You could physically damage the drive and if there was a read/write process going on at the time, data might very well be corrupted.

If I was running Ubuntu like this, I'd either be using cloud storage to save my files, or - if I couldn't depend on internet access - at least backing them up to somewhere religiously.

---

### Post by Jay MC on 2012-08-14
> **amrosama77 said:**
> then after doing so how to set software center to **install programs to my main hard** not to my small 8G flash drive?

Does this mean you always intend to use the same PC?  If so, out of curiousity, why rely on live?

Are you worried about/daunted by the installation process?  If so (and the PC has Windows) have you considered Wubi...?

---

### Post by amrosama77 on 2012-08-14
yes manly I will use same pc, but it will be great to be able to have my system on my flash on the run,

I thought to let the whole pc out of ubuntu as I am not familiar with it.

we know many times ubuntu fail me down by not opening and I don't know what to do at all !!!

---

### Post by cryptotheslow on 2012-08-14
That becomes quite complicated to achieve. If you manage to do it somehow then whenever you are "on the run" then those programs installed to the PC hard-drive will be unavailable and depending on how you set it up may lead to breakage.

My complete Ubuntu install is currently using 7.9GB including my own docs etc. A fairly new and clean install of Lubuntu on my USB stick is currently running at 5.9GB including my own docs etc. Either would be fairly tight on an 8GB stick.

If you can get hold of a larger USB stick then things would be much simpler (I currently use a 32GB stick for my portable Lubuntu stick).

---

### Post by amrosama77 on 2012-08-14
also I don't like the idea of using wubi as I don't want to depend on windows as all, don't like the idea of making anti viruses system (ubuntu) to depend on (viruses system) windows at all


I guess I should buy 32G flash drive :D

---

### Post by lukeiamyourfather on 2012-08-15
I would just dual boot using the internal hard disk or purchase another hard disk (can pick one up for $15 at a used computer shop). If you still want the mobility use a USB flash drive as a secondary installation. That's my two cents. Good luck with whatever you end up with.

---

