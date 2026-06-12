---
title: "Installing Ubuntu on Dell XPS M1530"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by blackeagle613 on 2008-07-18
Hello all! I am ready to use Ubuntu now, I would like to still keep Vista installed.

So here is my situation.

I currently have my HDD with Vista installed, I would like to install Ubuntu without having to uninstall Vista.

So what exactly do I need to do? I want to be able to boot both Vista and Ubuntu.

I need this to work with wireless will that be an issue?

Also, I heard that there are issues with Ubuntu and the touchpad on my laptop, what will I need to do to ensure my touchpad will work properly.

thank you all so much for helping out a noob!! from reading around the forums this seems like a really friendly bunch.

---

### Post by kool_kat_os on 2008-07-18
On your laptop...just try out the live cd and see if your touch pad works....same thing with your wireless

And when you are installing ubuntu there is an slider that you will see...it will be very easy....it will have windows vista on one side and ubuntu on the other side...you just drag the slider to your preference of space that you would like to give ubuntu.


EDIT:

It should look something like this...8.04.1 is easier becuase it will have the OS's labeled

[IMG]http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg[/IMG]

---

### Post by blackeagle613 on 2008-07-18
in the live cd the touchpad is crazy just flying around sparatically...

So when I move the slider it will take care of all the partitioning for me.... and what about setting up the bootloader?... I heard that there can be lots of problems with that.

---

### Post by kool_kat_os on 2008-07-18
The boot loader will install automatically.

You shouldnt have any problems ...

if your uninstalling ubuntu...then you will need to follow a few steps...

(I installed and uninstalled ubuntu 3 times and my windows partition is still not corrupt)

---

### Post by blackeagle613 on 2008-07-19
so what do I need to do in order for my touchpad to work properly?

---

### Post by anewguy on 2008-07-19
After installing Ubuntu, you will probably need to install the Synaptics package - it allows you to control your touchpad.

---

### Post by trentmc on 2008-07-19
I had probs with my XPS's touchpad the fix was...

to find the Kernel line in /boot/grub/menu.lst add i8042.nomux=1 at the end

after a reboot this worked perfect for me.

---

### Post by sampaguy on 2008-07-19
I have the same laptop and after some tweeking everything seems to work great except the wireless, I have googled and googled for 2 days with no success, does anyone have a problem with the wireless not working? Any fixes?

Thanks so much for the help!

---

### Post by trentmc on 2008-07-19
> **sampaguy said:**
> I have the same laptop and after some tweeking everything seems to work great except the wireless, I have googled and googled for 2 days with no success, does anyone have a problem with the wireless not working? Any fixes?

Thanks so much for the help!

My XPS was shipped with an Intel 4965AGN wireless-N Mini-card.... this just worked, without any tweaking with Hardy.

It is an installation/driver issue? or rather a wireless networking issue?

---

### Post by medley on 2008-07-19
> **blackeagle613 said:**
> in the live cd the touchpad is crazy just flying around sparatically...

So when I move the slider it will take care of all the partitioning for me.... and what about setting up the bootloader?... I heard that there can be lots of problems with that.

I've installed hardy on my Dell m1330 without any problems with the touchpad. I don't know why you should have any problems. The wireless also worked without problem.

Good luck.

---

### Post by blackeagle613 on 2008-07-20
If I install ubuntu via wubi will it work just the same as installing it through the traditional way? I found that by installing it through wubi it would still use the windows boot manager which is nice.

So will it work just as fast? and does it partition the drive? or will it still be on my current windows partition?

thanks

---

### Post by sampaguy on 2008-07-21
> **trentmc said:**
> My XPS was shipped with an Intel 4965AGN wireless-N Mini-card.... this just worked, without any tweaking with Hardy.

It is an installation/driver issue? or rather a wireless networking issue?

Perhaps instalation or networking, either way I have the same wireless card as you but can't get it to work for the life of me.

---

### Post by m_ad on 2008-07-21
I've found[ this]("http://http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") article is probably the best way to install Ubuntu with Vista already installed. It uses the Vista Shrink tool to shrink your existing partition, then install Ubuntu. I think a lot of people recommend doing it this way if you have Vista already installed.

As for the mouse etc.. not sure how to help, sorry.

---

### Post by medley on 2008-07-21
> **sampaguy said:**
> Perhaps instalation or networking, either way I have the same wireless card as you but can't get it to work for the life of me.

If your wireless interface is showing up in the network settings, you might try configuring it with a static address rather than using DHCP. I don't know why, but this is a frequent problem when I'm configuring wireless networking in Ubuntu. I installed Kubuntu 8.04 a couple of weeks ago on this 1330, and had trouble until I configured it for static IP. No problems since.

---

### Post by nuschii on 2008-07-26
> **trentmc said:**
> I had probs with my XPS's touchpad the fix was...

to find the Kernel line in /boot/grub/menu.lst add i8042.nomux=1 at the end

after a reboot this worked perfect for me.

Wow. Thanks a lot for that tip. Touchpad works perfect now. (Even a lot better than it does on Windows.) :D

Now what exactly does this kernel option do? Doesn't seem like a "touchpad related" option...

---

