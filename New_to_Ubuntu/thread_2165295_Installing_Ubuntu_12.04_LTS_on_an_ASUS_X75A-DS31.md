---
title: "Installing Ubuntu 12.04 LTS on an ASUS X75A-DS31"
date: 2013-08-04
forum: New to Ubuntu
---

### Post by ryan4 on 2013-08-04
I recently purchased an [ASUS X75A-DS31]("http://www.amazon.com/gp/product/B00B7K11PU/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1") and decided to ditch Windows 8 for Ubuntu. 

Here are the steps I took to install Ubuntu (**if you seek to repeat my actions, you will need access to another computer to download some files and burn a CD, a USB storage device & a wired internet connection**; there are other solutions, this is just what worked for me).

Created an install CD from the [12.04.2 LTS 64-bit desktop torrent]("http://www.ubuntu.com/download/alternative-downloads"). In Windows 8, right-click the completed ISO and choose "Burn disc image".

Repeatedly pressed Esc upon booting up to enter BIOS, then modified the following settings:
[LIST]
[*]BOOT menu: changed Fast Boot to Disabled
[*]BOOT menu: changed Boot Option #1 to MATSHITA DVD-RAM UJ8E1
[*]SECURITY menu: changed Secure Boot Control to Disabled
[/LIST]

Saved & Exited BIOS

Chose UEFI: MATSHITA DVD-RAM UJ8E1 from boot options & installed Ubuntu

The next step was to get the AR8161 ethernet card running. I followed [the instructions here]("http://askubuntu.com/questions/237004/atheros-ar8161-ethernet-card-not-working-on-12-10-on-an-asus-n56vm"). The first step is to download the driver([compat-wireless-3.6.8-1-snpc]("http://wireless.kernel.org/en/users/Download/stable#compat-wireless_3.6_stable_releases")), which I did on another machine, then transfered it over using my USB drive. I put it in my Downloads folder on the X75A, opened a terminal by pressing Ctrl+Alt+T, then "cd Downloads" to get to the directory, then following the rest of the instructions.

With the wired connection up, the next step is to dowgrade the kernel from 3.5 to 3.2, since the wireless will not work under 3.5. The directions that I followed for getting the wireless working [can be found here]("http://ubuntuforums.org/showthread.php?t=2104690"). The boldface & underlined portion at the top states that the kernel should be no later than 3.2 for the fix to work. So I needed to downgrade the kernel first, then fix the wireless.

To downgrade the kernel, [ibjsb4]("http://ubuntuforums.org/member.php?u=1729120") suggested that I install synaptic package manager. I used the following commands in the terminal:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic

I opened synaptic by right-clicking on the Dash (at the upper-left) and choosing Applications, then choosing Synaptic Package Manager. I had to click Reload before the kernel 3.2 would show up in the search. In the quick filter I typed in "linux kernel image" and scrolled down to find the latest version: **linux-image-3.2.0-51-generic**. I checked the box to the left and clicked **Apply**. 

After installing the kernel, I had to make changes to **grub **([documentation here]("https://help.ubuntu.com/community/Grub2")):

I opened a terminal and ran:

sudo gedit /etc/default/grub

and made the following changes to the file:

GRUB_HIDDEN_TIMEOUT=5
GRUB_TIMEOUT=-1

I rebooted and repeatedly hit **shift** until grub loaded, chose "older versions" (I think it was the 3rd option), then again chose the 3rd option for kernel 3.2.

After booting up, I had to again install the wired drivers as above. But this time I had problems at the "make" step, and needed to install:

linux-headers-3.2.0-51_3.2.0-51.77_all.deb
linux-headers-3.2.0-51-generic_3.2.0-51.77_amd64.deb

I downloaded the above to my USB drive, transferred them to my Downloads folder on the new machine, opened a terminal, cd to Downloads and executed "dpkg -i *.deb". After this, I continued with "make", "make install", etc. from the directions for the wired driver, above.

With the wired internet working, next was to get the wireless working. I followed [these instructions]("http://ubuntuforums.org/showthread.php?t=2104690").

Now everything works for me. The only thing I still need to do is to make 3.2 the default kernel at bootup. I hope this helps someone else. Much thanks to those who wrote the directions in the above links.

Ryan

---

