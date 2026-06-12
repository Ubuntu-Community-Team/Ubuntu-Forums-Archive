---
title: "New Ubuntu User rather lost and needing guidance"
date: 2015-06-11
forum: New to Ubuntu
---

### Post by RayTomes on 2015-06-11
I am a long time Windows user who is seriously trying to convert to Ubuntu now. I use Win-XP but it is getting wobbly and so the time has come. I downloaded the ubuntu-14.04.2-desktop-i386.iso and made a DVD and can boot it OK. I have some issues with my disk drives as one 332 GB partition is not showing in Win-XP or in Ubuntu, probably a remnant from an earlier attempt at Ubuntu installation. I tried to set it up under Win-XP Computer management / Device manager but it doesn't allow me access. I also have an SSD which is at present disconnected because Win-XP cannot properly use it. Want to use that later too.

I use Thunderbird, Firefox and Open Office so hopefully these will be easy to switch over.

So I decided to try WUBI to get started. Later can change to a proper installation I suppose. I found wubi.exe on the DVD and copied it and the iso file to my D drive which is 332 GB (different partition to problem one mentioned above) and empty (apart from the usual windows bits it adds). I double clicked wubi.exe and it ran for a little while and complained "cannot download the metalink and therefore the ISO") and stopped. It did make an ubuntu directory on my D drive but clearly hasn't installed. I don't understand because the iso is right next to wubi.exe on D drive.

OK, what now?

---

### Post by wildmanne39 on 2015-06-11
Hi, welcome to the forum! wubi is no longer supported so you really should not go that route.
Here is the staff recommendation on wubi.
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by grahammechanical on 2015-06-11
It is not possible to convert a Wubi install of Ubuntu to a normal dual boot install. Wubi allows Ubuntu to be run inside Windows XP. So, if XP goes belly up then that will be the end of Ubuntu as well.

My advice would be to remove the Wubi installation. Wubi is no longer developed because it is not compatible with Windows 8. Very few forum members use a Wubi install so getting advice is not so easy. XP is no longer supported by Microsoft. So, the security risk is even higher now.

My advice would be to back up any important data. Run the Ubuntu Live session to become familiar with Ubuntu. Then install Ubuntu using the Erase disk and install Ubuntu option.

If you still wish to keep XP then use the install alongside option but first use Windows tools to defrag the disk and defrag more than once making sure XP loads each time.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Regards.

---

### Post by RayTomes on 2015-06-11
Thank you. Will do a dual boot system.

---

### Post by RayTomes on 2015-06-12
OK, I made a dual boot system but got a message that grub failed ... fatal error.
"Executing 'grub-install//dev/sda' failed"
It then carried on and asked me to pick a drive to put dual boot on (it was trying to do the wrong one I think - I have two 1 TB drives and the other one is not bootable AFAIK) and when I told it, it then seemed to come to a happy end.

The ubuntu partition is all set up OK (and the little 2nd on) but when I boot from disk it just goes straight to windows. In the old days I could run grub from within linux to set this right. Can I still do that? How?

---

### Post by mastablasta on 2015-06-12
you can use boot repair tool - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

also why not juts add the SSD and then install the Ubuntu to SSD, then tell the computer to boot from SSD and if it doesn't find windows automatically all you would need to do is update the grub menu.

just make sure you put /swap on normal hdd.

---

### Post by RayTomes on 2015-06-12
Thanks mastablasta. I have successfully made the system dual boot. Both OS work.
When I try to plug SSD drive in I can't boot anything even though it is set as last drive to boot. Not a ubuntu problem, perhaps a hardware problem. I experienced this before and took it out. Seems my system only works with two drives. Problem for another day.

When I ran ubuntu from DVD it managed to access internet OK. However when I booted from disk it cannot access internet. The network thing shows as disconnected and when I switch to ON it stays a while and then drops out again. Can't get anything done in that time. I have been complaining to ISP that there service is lousy as under windows I have to often try things 2 or 3 times to get it to work. Seems that ubuntu is being clear that line is disconnected. Is that a reasonable conclusion? Is there any sensible reason why ubuntu would disconnect?

OTOH I managed to post this no problem. Arrgghhh!

---

### Post by mastablasta on 2015-06-12
> **RayTomes said:**
> Thanks mastablasta. I have successfully made the system dual boot. Both OS work.
When I try to plug SSD drive in I can't boot anything even though it is set as last drive to boot. Not a ubuntu problem, perhaps a hardware problem. I experienced this before and took it out. Seems my system only works with two drives. Problem for another day.

perhaps you need to perform a BIOS update or the BIOS is just not compatible with your SSD.
furthermore the SSD might be forced to boot via bootloader e.g. if you keep GRUB bootloader on HDD and then use it to boot the OS from SSD. boot sequence would then look something like this:

computer on -> BIOS loaded -> bootloader accessed on HDD ---> system boot initialised using system files SSD

remember that the boot loader determines that disk is bootable (i.e. that you can boot form that disk) - so if you keep it on HDD, you would boot from HDD but system would still load from SSD ;)

> 
When I ran ubuntu from DVD it managed to access internet OK. However when I booted from disk it cannot access internet. The network thing shows as disconnected and when I switch to ON it stays a while and then drops out again. Can't get anything done in that time. I have been complaining to ISP that there service is lousy as under windows I have to often try things 2 or 3 times to get it to work. Seems that ubuntu is being clear that line is disconnected. Is that a reasonable conclusion? Is there any sensible reason why ubuntu would disconnect?


wired or wireless? wireless can drop due to bad driver or many other software related reasons. wired generally works as their drivers are pretty much standard it seems. when connection is dropped can you still access your router/modem? if you can, it means ISP is at fault.

---

### Post by wildmanne39 on 2015-06-12
If this is  wireless connection click on the wireless script in my signature and follow the directions for posting the file created in a thread on the forum. Please create a new thread just for the connection issue and it is best if it is in the networking and wireless section.
Thanks

---

### Post by RayTomes on 2015-06-12
The SSD did work when I only had one HD connected but not when I have two it seems.

BTW, I am doing this message from Ubuntu, so it is working and connecting to internet. The internet problems are definitely my ISP. Whenever it rains our connection drops out from time to time. Sunny now!

SOLVED

---

