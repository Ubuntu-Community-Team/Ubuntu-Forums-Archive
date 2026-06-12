---
title: "Hello world and brightness issues."
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Mahram Gander on 2013-03-05
First of all, I'd like to send my best wishes to everyone in the Ubuntu community. I've never used any other operating system besides Windows and OS X, the latter only at school or work, but in fact I've never owned a computer running anything beyond the Microsoft option. After spending the last couple of weeks doing a little research, I finally decided to blow Windows away for good and go with Ubuntu, and so far I'm really impressed! I've found software libre to cover all of my needs (no more piracy hypocrisy coming from me) and my laptop is starting in record time (usually I turned it on and went to take a leak or grab a cup of coffee while it was at it). Besides it looks great!

Anyway, the only issue I'm having with Quantal Quetzal on my Dell Studio 1558 is that the keys to adjust screen brightness aren't working. They show the indicator going up and down, but they don't change the brightness at all. I can't even change it on the Brightness and Lock menu. Is there any way for getting them to work? All of the other Fn keys seem to work well by the way. Hoping this is not so noobish as I'm already noob enough, I thank you in advance for any kind of reply.

¡Un saludo desde México! ):P

---

### Post by Mark_in_Hollywood on 2013-03-05
If you are unfamiliar with the Linux "command line" or "terminal". Come back and ask me. Meanwhile if you are feeling geeky, here's the solution:


[http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html](http://www.refreshit.info/2012/08/solved-brightness-increase-and-decrease.html)

Brightness problem in Ubuntu is one of the major problem in many PCs and I have the same problem in my laptop Acer Aspire 3830 TG in Ubuntu 12.10 Quantal Quetzal. When I use the function key and brightness button the indicator of brightness changes but there will be no change of brightness.
I searched in the web and found the many solutions but not working exactly for the problem. Before in my blog post I had given the solution for the brightness problem but I only changes the contrast. The battery power consumption is same if the display is more or less.

I have tried by updating the Kernel to the latest version. But I have found the best solution that can increase or decrease the brightness of the PC in Ubuntu using the function and brightness button. Just follow the steps:

Open terminal (Clt+Alt+T)  and run the command given below:

sudo gedit /etc/default/grub

Now the new window opens and you will see the lines given below:

GRUB_CMDLINE_LINUX_DEFAULT="quite_splice"
GRUB_CMDLINE_LINUX_DEFAULT="" 

Now you have to change the lines above by the command lines given below:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"

Then save the window and Update the grub from the terminal using :

sudo update-grub

Now you can Increase or decrease the brightness of your PC in Ubuntu 12.04 and the other versions also. This technique can be used in HP DV6, Acer Aspire, Dell Inspiron,  Toshiba and more others.

---

### Post by Mahram Gander on 2013-03-05
Thanks for your quick response friend! I'm not familiar with the terminal but I won't run from it. Running the command you gave me took me to the grub file in the gedit editor. The closest lines to what you're indicating are:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Before doing anything rash, I must ask: do I have to erase these two lines and replace them with

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"

or just add the missing part, leaving it like this?

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""

Edit: I erased and replaced those two lines with the code you gave me, saved and updated the grub, restarted and guess what? Problem solved! I'm now able to use the brightness keys, which is great 'cause my eyes were starting to hurt. 

Thanks again!

---

### Post by Mark_in_Hollywood on 2013-03-06
Please go back to the topmost thread (of yours) and select Edit, then Advanced Edit. At the top where you previously selected the "Prefix:" pull that down and mark this as "Solved" so others can get some help.

---

### Post by c2tarun on 2013-03-06
Just an FYI so that others know, this is a kernel [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765"). Somehow someone fixed it in post #71.

---

### Post by Mahram Gander on 2013-03-06
Thanks again Mark, just updated it!

---

