---
title: "Ubuntu lucid kernel upgrade"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by npjoseph on 2011-09-23
hi i have ubuntu 10.04.3 installed on my laptop right now. the current kernel version is 2.6.32-33. is there any way i can upgrade to kernel version 3? the ubuntu kernel ppa does not exist for lucid. thanks.

---

### Post by garvinrick4 on 2011-09-23
Here are kernels had a 10.04 and would not use 3.0 kernel for me, also in Maverick and Natty
would use kernel and had to upgrade module-init-tools to 3.13 I believe it was. I needed because
3.0 kernel would work better with my Network card.
[Index of /~kernel-ppa/mainline]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Above the kernels are already built .deb just need the all.deb the headers and image. Download
all three and just click on and will install in Ubuntu software center if trouble command line.
Use your 32 or 64 bit of course. (uname -a)
Drop in Home
ls
sudo dpkg -i (copy and paste package) Do this for all 4 packages to be installed.

Can find module-init-tools in launchpad already in .deb can google and get 3.13 build in launchpad

## Again cannot remember why 10.04 would not work in 3.0 for me but in all other versions OK.
Some say 3.0 is installed in lucid. Google a bit and sure you will find results.

---

### Post by ajgreeny on 2011-09-23
The kernel ppa for lucid is at [http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu) and it does have version 3.0. though I haven't tried it yet.  I may have a go later and will report back.

In the past I used that ppa and updated to kernel version 2.6.38, which ran fine, but unfortunately slowed down any USB transfers or copying to a total dribble of about 10 or 11 KB/sec instead of the expected 20MB which I get with the current kernel.  I use 2.6.35-30 from the proposed repos at the moment and that is fine.

---

### Post by garvinrick4 on 2011-09-23
Hope it go's smooth for you, to late for me latest install I have is 10.10 now and quite a few 11.04's and
2 testing 11.10.
 The Nattys I have a just smooth as silk, from gnome-shell to Unity to Classic they all work so smooth.
Put a Natty with Gnome-shell ppa on its own partition and leave it be, works nice.
Would have liked to keep a 10.04 just because it is a LTS but could not get intels iwlagn driver to work
in N only G so was pain. Should have kept it in retrospect. You take care and see you in the Forums.

---

### Post by npjoseph on 2011-09-23
thanks everyone. i have added the ubuntu kernel ppa; im not sure if my nvidia graphics card drivers will work with the mainline kernels. i have to install linux-image-3.0.0.8-generic, linux-headers-3.0.0.8-generic and linux-headers-3.0.0.8 i'm guessing. these are the current versions. will check it out and let you know how it works.

---

### Post by npjoseph on 2011-09-23
i installed the packages and booted into the new kernel. ubuntu starts in low graphics mode and says nvidia-current module cannot be loaded. the broadcom wireless driver does not load either. i have rolled back to the  older kernel. please help.

---

### Post by garvinrick4 on 2011-09-23
Boot at grub menu into previous kernel that worked.
go into synaptics and remove offending kernel then (in synaptice type in kernel like 3.0.1) whatever it is.
sudo update-grub
If you cannot see menuentrys at boot hold down shift while booting.

As I stated before 3.0 and up did not work for me either in Lucid. Did you google and find a success.

---

### Post by ajgreeny on 2011-09-23
Here's the update I promised in post #3, if I got round to trying 3.0.0-8.

Installed 3.0.0-8 via synaptic; the kernel, the headers and headers-generic.  All worked well on my machine, an old sempron 2400+ with 2GB ram and ATI 9200SE AGP graphics card using the open source driver.

Or so I thought until I again tried to copy files from a USB drive to my hard disk, as that is where the 2.6.38 kernel let me down, and again the transfer rate was appalling and totally unacceptable, as I backup with rsync to a USB hard drive often.

There must be something missing, required for normal USB2 speeds to be possible when using this kernel, just as it was with the 2.6.38.  A great pity, but at least it did boot and run apparently without any problem, apart from the USB speed.

---

