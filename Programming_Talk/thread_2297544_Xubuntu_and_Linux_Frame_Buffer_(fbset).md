---
title: "Xubuntu and Linux Frame Buffer (fbset)"
date: 2015-10-04
forum: Programming Talk
---

### Post by James_Lehman on 2015-10-04
Hello everyone.

I was wondering if there is someone here who knows about The Linux Frame Buffer; as in /dev/fb0 and fbset.

I just built a new computer with Xubuntu installed and an Nvidia  graphics card that can do 4K. Plus I got a nice 65 inch curved screen  LCD monitor that can do 4K.

On my Raspberry Pi 2, with Raspbian, I can boot into a high-res console and start and stop X easily.

I can also change the screen resolution and pixel color density.

I'd like to be able to do this in Xubuntu.

I'd love to be able to boot into a 32-bit 4K console!

Quite some time ago I wrote ezfb (a Linux Frame Buffer API) and I have been developing it to make it work better on the RPi2.

I'd really like to be able to get it working on this new Xubuntu machine.

I have successfully built kernel 3.19.8 and with that booted, I can get  info from fbset as in mode 640x480. But I cannot issue any fbset command  that changes anything.

Thanks in advance.

James.

---

### Post by mikodo on 2015-10-04
Might you want to ask that here too, if you haven't already:

[https://lists.ubuntu.com/mailman/listinfo/xubuntu-users](https://lists.ubuntu.com/mailman/listinfo/xubuntu-users)

[https://mail.xfce.org/mailman/listinfo/](https://mail.xfce.org/mailman/listinfo/)  maybe, [https://mail.xfce.org/mailman/listinfo/xfce](https://mail.xfce.org/mailman/listinfo/xfce)

[URL="https://forum.xfce.org/"]https://forum.xfce.org/


[/URL]

---

### Post by James_Lehman on 2015-10-06
I was hoping for some specific guidance; like what things enable in the 3.19.8 kernel config and how to get grub to boot to a 3840x2160 32 bit console.

I guess I'll keep looking.....

It might have a lot to do with what video card driver I am using.

I tried to install a video editor and it goofed up everything to the point that I had no X. I had to install the Nvidia drivers.

I've been playing around with the Linux Frame Buffer for well over 15 years and I've never had so much trouble getting to it.

Can someone please explain to me why there is no way to log out of this GUI to a console and get back into it again?

... never mind ...

[Ctrl][Alt][F1] through [F6] takes you out of a running Xfce to a console. [Ctrl][Alt][F7] takes you back into the still running Xfce.

Still looking for a proper way to build the kernel and get fbset working.

James.

---

### Post by James_Lehman on 2015-10-08
Upon further investigation on this matter, it was found necessary to uninstall the proprietary nVidia driver that had been manually installed and then reinstall nouveau.

cp or mv the NVIDIA-Linux-x86_64-*.run (manually installed propietary nVidia driver) file to /root

reboot into recovery mode kernel
drop to root in a shell. Issue the commands

[FONT=courier new]./NVIDIA-Linux-x86_64-352.41.run --uninstall
# note above is the one I used.
[/FONT]
[FONT=courier new]apt-get remove --purge 'nvidia*'[/FONT]
[FONT=courier new]
apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core xserver-xorg-video-nouveau nouveau-firmware[/FONT]
[FONT=courier new]
update-alternatives --config gl_conf

ldconfig

update-initramfs -u

dpkg-reconfigure xserver-xorg

# remmed out line begins with a #
[/FONT]
I did the research on the web in a working Xfce with the proprietary nVidia driver loaded. I made a text file with the above commands in it, made it executable and moved it to /root. I edited the file and remmed out all the lines but one at a time, in order from top to bottom and ran the file between each edit.

I was then able to boot up into a frame buffer that kinda works, using nouveau. It was 1920x1080; not what I really want.

When I startxfce4 I am also limited to 1920x1080 in my desktop environment.

So, it looks like the only way to get 3840x2160 in X only (no frame buffer) is to use the proprietary driver.

I loaded the one from the Ubuntu Software Center instead of installing the run file manually.

I don't see that it makes any difference except when I go to Settings Manager. With the proprietary nVidia driver loaded from Ubuntu Software Center, I can see Additional Drivers and I can choose to revert to the nouveau driver from there. But, if I do, I go back to only 1920x1080 and I can no longer see Additional Drivers in the Settings Manager. So I have to install the nVidia drivers again.

[FONT=courier new]add-apt-repository ppa:mad:org-edgers/ppa -y

apt-get update

apt-get install nvidia-current
[/FONT]
With the manually installed driver (NVIDIA-Linux-x86_64-*.run), installed, when I go into the Settings Manager... Additional Drivers, I can see the manually installed driver in the list of video drivers and all the rest are greyed out and not selectable.

Apparently the nouveau driver that gives me a working Linux Frame Buffer does not yet support 4K (3840x2160) and the proprietary nVidia driver that gives me 4K in Xfce does not support at working Linux Frame Buffer.

Hopefully there is more to it than this!

I'd love to see some more posts in this thread to fully flesh out this subject.

Thanks!

---

### Post by James_Lehman on 2015-10-08
I just did a little communicating on the nouveau mailing list and got this as an answer:

[I]HDMI with nouveau is limited to 165mhz unfortunately. This is 
incorrect (the hardware can do more), but nevertheless, that's the 
present limit. If you can connect the screen over dual-link DVI or DP, 
you should be able to get the full resolution.[/I]

So, since my video card has only one of each HDMI, digital video and analog VGA ports and my monitor has only HDMI inputs, I guess I'll have to wait for future nouveau developments.

James.

---

