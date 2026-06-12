---
title: "Ubuntu Desktop / Ubuntu Server / Kubuntu - Tripple boot."
date: 2008-10-01
forum: New to Ubuntu
---

### Post by lyphogra on 2008-10-01
Hi, folks!

I'm very new Linux user, so i have stumbled upon a problem of how to set up these three different OS. Recently, i have got brand fresh new CD's and 160Gb HDD. Any advices from both experienced users and new ones how to divide this space more efficiently and make a workplace to use with pleasure.

Great thanks, Lyphogra.

---

### Post by jpoRS on 2008-10-01
Lyphogra,

I am not sure exactly what you are asking.  Would you mind being more specific?

Welcome to the forums!
jim

---

### Post by opscure on 2008-10-01
There are plenty of documents out there on setting up multiple operating systems, but the basics of it are:

partition your drive (1 boot (hda1)- >1GB, 3 (hda2, 3, and 4) primary- 52GB, 1 swap (hda5)- 3GB) this can differ and can be tailored to your needs (ie. which OS will need more space. etc.)

Install grub (or lilo) to boot partition (this can be done through the gui of the 1st OS install)

install second OS to second primary partition (no bootloader)

install third OS to third primary partition (no bootloader)

configure grub for other two OS and remove auto boot timer (so you have to select from the OS from grub)

done.


Also you can try [google]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=vWg&q=three+OS+boot+grub+linux&btnG=Search")(<-Link) or [ubuntuforums]("http://ubuntuforums.org/search.php?searchid=48867939")(<-Also a Link) search.

You are likely going to run into specific issues that you should post back up as they arise, but a general question like this is hard to be specific with an answer.  Just go for it and use the forums and google as a reference when you get stuck on something.

---

### Post by lyphogra on 2008-10-01
> **jpoRS said:**
> Lyphogra,

I am not sure exactly what you are asking.  Would you mind being more specific?

Welcome to the forums!
jim

Thanks, Jim!

Okay.. i am really just asking how to set up Ubuntu Desktop / Ubuntu Server / Kubuntu on one PC? How to divide partitions, i mean e.g. how much does it need for *swap*? Or how much does Server edition need in comparison with Desktop edition? Just your proposals and your steps how you would do this very appreciated.

---

### Post by lyphogra on 2008-10-01
> **opscure said:**
> There are plenty of documents out there on setting up multiple operating systems, but the basics of it are:

partition your drive (1 boot (hda1)- >1GB, 3 (hda2, 3, and 4) primary- 52GB, 1 swap (hda5)- 3GB) this can differ and can be tailored to your needs (ie. which OS will need more space. etc.)

Install grub (or lilo) to boot partition (this can be done through the gui of the 1st OS install)

install second OS to second primary partition (no bootloader)

install third OS to third primary partition (no bootloader)

configure grub for other two OS and remove auto boot timer (so you have to select from the OS from grub)

done.


Also you can try [google]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=vWg&q=three+OS+boot+grub+linux&btnG=Search")(<-Link) or [ubuntuforums]("http://ubuntuforums.org/search.php?searchid=48867939")(<-Also a Link) search.

You are likely going to run into specific issues that you should post back up as they arise, but a general question like this is hard to be specific with an answer.  Just go for it and use the forums and google as a reference when you get stuck on something.

Yes, great thanks.. That's what i needed. I will really decide myself about the details and will use forums, search engines, etc.. in case of trouble. But for the first time for me it was quite an answer to find out here.

---

### Post by durand on 2008-10-01
> **lyphogra said:**
> Thanks, Jim!

Okay.. i am really just asking how to set up Ubuntu Desktop / Ubuntu Server / Kubuntu on one PC? How to divide partitions, i mean e.g. how much does it need for *swap*? Or how much does Server edition need in comparison with Desktop edition? Just your proposals and your steps how you would do this very appreciated.

For swap, the rule used to be double the memory (for 256MB memory, 512MB swap) but if you have 1GB or more memory, then 1GB swap is more than enough.

---

### Post by silverglade00 on 2008-10-01
Another option you have is to just install a single one. All three can be configured to act like each other. For instance, if you install Ubuntu Desktop, then install the kubuntu-desktop package, you can switch back and forth and effectively have Ubuntu and Kubuntu. Install some server packages using tasksel in the terminal, and you have the server part.

---

### Post by snowpine on 2008-10-01
> **silverglade00 said:**
> Another option you have is to just install a single one. All three can be configured to act like each other. For instance, if you install Ubuntu Desktop, then install the kubuntu-desktop package, you can switch back and forth and effectively have Ubuntu and Kubuntu. Install some server packages using tasksel in the terminal, and you have the server part.

This is the best advice yet. There is no reason to triple-boot. Ubuntu, Kubuntu, and Server all use the same core system, so it would be a waste (and a logistical hassle) to have three different copies of the same thing on your hard drive. You can install Ubuntu, then 'sudo aptitude-install kubuntu-desktop' to add the Kubuntu environment, then add whatever server packages you need. Easy.

---

### Post by durand on 2008-10-01
To install a LAMP environment, you can use:
```
sudo tasksel install lamp-server
``` from a standard ubuntu install.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Kellemora on 2008-10-01
Hi L

Silver already gave you the scoop on not needing different Ubuntu packages as they can all do what you want without rebooting.

I'm chiming in to add a note for your notebook for when and if you decide to install other OS's to play with.

I'm running a triple boot, CentOS, Debian and Ubuntu.

After having loaded this combination now on 5 different hard drives, I've learned a little bit about a great order to do it in to prevent problems.

Ubuntu seems to handle Grub better than any other Distro.  Have no idea why, it just does is all.

After I divide up my hard drive into 3 main partitions, leaving some free space for Ubuntu to create a swap file in.  I will install the OTHER OS's first, then install Ubuntu last and it will find the other Distro's and add them to the Bootloader, without errors to work out.

IF you want to have a Mickey$oft DOZE on the pooter, it will have to be the 1st Primary and hold the bootloader as well to prevent other problems.  The Doze don't like to be second fiddle to anyone else, hi hi..........

For some reason I've found working with Grub from Ubuntu is much easier, simpler and less problematic.

And FWIW:  Those who KNOW what they are doing will say I'm talking through my HAT, hi hi..........
I LEAVE all the individual Bootloaders installed, so I can go and cut n paste from them, like when they update the kernel, and move it to the Working Bootloader that's read on start-up.

TTUL
Gary

---

### Post by lyphogra on 2008-10-02
Okay, many thanks for replies. SOLVED

---

