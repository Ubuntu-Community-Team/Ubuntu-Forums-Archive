---
title: "Stuck in Terminal (TTY1) [Version 12.10]"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by mc5 on 2013-01-31
Hello,

I've gone through the installation and now I've come to the Terminal. I'm able to sign in and everything but when I reboot, it brings me right back the Terminal. How do I get out and what else do I need to do to get Ubuntu running?

Also, I not able to create Swap files using this: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Are these common problems or did I miss some basic installation guide??

---

### Post by ibjsb4 on 2013-01-31
How did you install 12.10?  A standard install will create its own swap space.

---

### Post by ikt on 2013-01-31
> **mc5 said:**
> I've gone through the installation and now I've come to the Terminal.

Did you install Ubuntu Server edition or Ubuntu Desktop?

Shouldn't be seeing any terminals when getting Ubuntu Desktop going.

---

### Post by mc5 on 2013-01-31
I installed Server via a DVD.

---

### Post by mc5 on 2013-01-31
Just booted my computer for the first time in 8 hours and it takes me directly to Terminal.

---

### Post by kanikilu on 2013-01-31
> **mc5 said:**
> I installed Server via a DVD. The server install doesn't include a desktop environment. If you want one, you'll have to install it yourself. There are many to choose from, but if you just want the equivalent of the standard Ubuntu (unity) desktop, I believe the metapackage you want to install is called **ubuntu-desktop**.

[https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F](https://help.ubuntu.com/community/ServerFaq#What.27s_the_difference_between_desktop_and_server.3F)

---

### Post by Impavidus on 2013-01-31
By default the server edition doesn't contain a GUI. You can install the standard GUI using```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```If you prefer, you can use xubuntu-desktop or lubuntu-desktop instead of ubuntu-desktop.

Edit: Ah, I thought I was fast with my reply...

---

### Post by mc5 on 2013-01-31
I've burned Ubuntu desktop to a DVD and placed it in my laptop. It won't read/run the DVD automatically, is there a command in the Terminal I can put in to run and install Ubuntu Desktop from a DVD?

---

### Post by mc5 on 2013-01-31
Any time I type "sudo apt-get update", I get a long list of errors and "Failed to fetch" listing the temporary failure resolving ubuntu.com sites.

---

### Post by Cheesehead on 2013-01-31
> **mc5 said:**
> I've burned Ubuntu desktop to a DVD and placed it in my laptop. It won't read/run the DVD automatically

That is normal. An Ubuntu desktop DVD usually means an install disk. Most users don't want to overwrite their entire operating system and lose all their data.

However, in your case that may be a good idea. To reinstall, boot from the DVD (not the hard drive).

---

### Post by Grinage on 2013-01-31
> **mc5 said:**
> Any time I type "sudo apt-get update", I get a long list of errors and "Failed to fetch" listing the temporary failure resolving ubuntu.com sites.

it could be that your network card was not correctly configured or is not configured at all, it's kind of a pain to do this without a gui but it can be done if the above error is all you're getting.

---

### Post by mc5 on 2013-01-31
Is there anyway to configure the network card? 

Also, I'm in the middle of installing the Ubuntu Desktop 12.10 and it's taking a really long time on the "Preparing to install Ubuntu" screen. Is this normal?

---

### Post by Grinage on 2013-01-31
depending on hardware it's hard to define long, but typically the installs shouldn't take longer than half an hour to an hour at the longest, although this can be longer on older hardware, and once the Ubuntu Desktop is finished it will be easier to tell whether or not you have network support and what steps you need to take to correct it if not from there.

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
> depending on hardware it's hard to define long, but typically the installs shouldn't take longer than half an hour to an hour at the longest, although this can be longer on older hardware, and once the Ubuntu Desktop is finished it will be easier to tell whether or not you have network support and what steps you need to take to correct it if not from there.

Alright. I'm going through the installation again. I guess I'm on the "Try Ubuntu" portion of my disc since I quit the installation process before. 

I'm at 'Preparing to Install Ubuntu'. The first three boxes (has at least 4.8 GB available drive space, is plugged in to a power source, and is connected to the Internet) are all checked.

'Downloading updates while installing' is checked.

'Install this third party software' is checked.

But it's still taking some time. Already 15-20 mins. Is this normal?

---

### Post by CharlesA on 2013-01-31
> **mc5 said:**
> 
But it's still taking some time. Already 15-20 mins. Is this normal?

Yes.

---

### Post by Grinage on 2013-01-31
> **mc5 said:**
> 

But it's still taking some time. Already 15-20 mins. Is this normal?

the install is checking for updates and downloading them and and there can be quite a few, although 15-20 isn't bad, unfortunately there's not really an indicator as to how long the downloads will take, it depends both on your hardware and your internet connection.  your install is only as fast as it's slowest component, and if that's your internet connection then you could be in for a wait.  Be patient, as long as the Installation doesn't hang or give you a kernel panic you should be alright.

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
> the install is checking for updates and downloading them and and there can be quite a few, although 15-20 isn't bad, unfortunately there's not really an indicator as to how long the downloads will take, it depends both on your hardware and your internet connection.  your install is only as fast as it's slowest component, and if that's your internet connection then you could be in for a wait.  Be patient, as long as the Installation doesn't hang or give you a kernel panic you should be alright.

I'm still at the same screen.

---

### Post by Grinage on 2013-01-31
does your machine have an HDD indicator that tells you when the hdd is access files?  adding up the time between posts you should be nearly finished with the install from the time you first posted about it being slow.  There's a chance there's a minimized debconf screen waiting for input from you, and of course it will sit there and do nothing until you enter the information.  Try ALT+TAB ing  to see if there are hidden screens you can't see, also if your keyboard has indicator lights for CAPSLOCK and NUMLOCK try activating these keys to check if they light up, if they do not then your install has frozen.  if that's the case that's a whole other realm of troubleshooting if a replacement live cd doesn't turn the trick.

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
> does your machine have an HDD indicator that tells you when the hdd is access files?  adding up the time between posts you should be nearly finished with the install from the time you first posted about it being slow.  There's a chance there's a minimized debconf screen waiting for input from you, and of course it will sit there and do nothing until you enter the information.  Try ALT+TAB ing  to see if there are hidden screens you can't see, also if your keyboard has indicator lights for CAPSLOCK and NUMLOCK try activating these keys to check if they light up, if they do not then your install has frozen.  if that's the case that's a whole other realm of troubleshooting if a replacement live cd doesn't turn the trick.

Just tried ALT+TAB ing but found no other windows or screens. I also do not have lights for CAPSLOCK or NUMLOCK on my laptop.

---

### Post by Grinage on 2013-01-31
This wouldn't be an Aspire Laptop would it?

---

### Post by Grinage on 2013-01-31
I'm still at the same screen.


What might be hanging you up is that you expect a status indicator, it's been awhile since I paid any attention to the live cd but there typically isn't a status indicator to tell you how far along the process is.  If this is an Aspire post the particular model, some Aspire laptops can be *different,* in a learning experience kind of way.

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
> This wouldn't be an Aspire Laptop would it?

Yeah. It is. I should have probably clarified. It's an Acer Aspire laptop.

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
>   If this is an Aspire post the particular model, some Aspire laptops can be *different,* in a learning experience kind of way.

Aspire 5252

---

### Post by Grinage on 2013-01-31
[http://www.debianadmin.com/ubuntu-12-10-quantal-quetzal-screenshots.html](http://www.debianadmin.com/ubuntu-12-10-quantal-quetzal-screenshots.html)


check out the link, tell us exactly which screenshot your install freezes on, that will give us more information as well

---

### Post by mc5 on 2013-01-31
> **Grinage said:**
> [http://www.debianadmin.com/ubuntu-12-10-quantal-quetzal-screenshots.html](http://www.debianadmin.com/ubuntu-12-10-quantal-quetzal-screenshots.html)


check out the link, tell us exactly which screenshot your install freezes on, that will give us more information as well

[http://www.debianadmin.com/wp-content/gallery/quantal/3.png](http://www.debianadmin.com/wp-content/gallery/quantal/3.png)

---

### Post by Grinage on 2013-01-31
OK that answers a whole lot, first make sure you have the right install cd either ubuntu server x64 or ubuntu desktop 64.  The I386 kernels will load and have problems on this machine.  

1. verify good cd, if you can burn a fresh ISO image that you know is correct
2. go straight to the install ubuntu ignore the try feature 
3. Use Guided use entire disk if you're not familiar with partitioning in linux, 
4. be plugged into a LAN for networking, wireless will not work correctly right away you'll have to tweak it once the install is complete
5. make sure all the boxes are checked and begin the install.
6. make sure the laptop has a full charge and don't move or disturb it during the install the acpi features when the unit switches from ac to dc power will cause the install to hang.

If you're trying other flavors there are other options, if you want server functions use a server CD but there are different options for this.

---

### Post by mc5 on 2013-01-31
I had been trying to install 32bit. Could that be the problem?

---

### Post by Grinage on 2013-01-31
Oh yes, this is a 64bit machine and it throws weird acpi signals which you'll have to correct later once the install is complete

---

### Post by Grinage on 2013-01-31
If your install completes successfully mark this thread as solved and then to solve your wireless issues checkout the network connectivity section of the forums.  Mid production of this particular laptop Acer switched up it's wireless nic cards.  If your wireless only works when you are tethered or if it constantly drops these are solutions that have already been found.  One final note for this machine, if you get very strange errors and glitches with no explanation you will need to edit your grub config file

/etc/default/grub

you will find the following lines
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

replace the quiet with nolapic or noapic or in some cases both separated by a space, if that doesn't resolve the issue then use acpi=off instead.
after making the change run update-grub


Welcome to the world of Unbuntu and enjoy, if you decide you don't like Gnome3 there are plenty of other flavors of Unbuntu to play with and enjoy.

---

