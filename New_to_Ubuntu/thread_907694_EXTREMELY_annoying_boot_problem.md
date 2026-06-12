---
title: "EXTREMELY annoying boot problem"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Miakehl on 2008-09-01
I just recently re did my former windows machine with Ubuntu 8.04 but I've been having boot issues. I started with trying to boot a live CD to install but Every time it gets to the loading screen that says "UBUNTU" in pretty orange letter the loading bar goes right to left two times and hangs the second time no matter what. i then downloaded the Alternate CD to install and it worked fine no issues with the install. Now that the machine is installed I'm having the same issue but it's intermittent sometimes it hangs and sometimes it doesen't. Right now I've been restarting it via power strip power switch for almost 30 minutes and it's been hanging every time. I've changed all the BIOS setting I can think of pulgged snd unplugged all extra cords, and jiggled the handle countless times. Iv'e redownloaded install cds from many different sources including Mininova and the Ubuntu website itself and all the cds give me this same issue. I've never had a problem before and I don't like this issue now. Has anyone had or heard of this problem and a possible solution?

Thanks,
Brandon

---

### Post by porchrat on 2008-09-01
have you tried turning ACPI off?

---

### Post by arpanaut on 2008-09-01
I've seen this before...

Someone was trying to install using a TV as a monitor, I don't think that the stock driver for the video recognizes the monitor right and the boot just hangs.

Sorry, I don't recall the solution, but if you have a "normal" monitor to use to get installed then try working out using the TV after installing different driver might be an easier solution.

Good Luck.

---

### Post by nicedude on 2008-09-01
This could be heat related as well,  I didn't have any problems with mine until summer came into full heat wave and then if it is hot ( say mid 80"s ) where I was then it would lockup and do a thermal shutdown. After I tweaked the CPU to power save better and run slower it hasn't happened again.

May not be a factor in your case but if after disabling acpi you still have the problem then it is something to look at, especially if it only does this after its been on for a while when it hasn't been used for a while and then does it almost immediately upon reboot etc.

---

### Post by Miakehl on 2008-09-01
What is acpi?

I'm assuming it's in the BIOS? I'll try to remember that as I'm not going to try to restart the machine in case it hangs again.

As for the TV, I installed 7.10 with this tv and used it forever with absolutely no problems but with 8.04 it goes nuts. I think it may be a heat issue as I leave my machine on for months at a time if I can only restarting if I have to.

---

### Post by Miakehl on 2008-09-01
/bump

---

### Post by rekado on 2008-09-19
> **Miakehl said:**
> What is acpi?

I'm assuming it's in the BIOS? I'll try to remember that as I'm not going to try to restart the machine in case it hangs again.

As for the TV, I installed 7.10 with this tv and used it forever with absolutely no problems but with 8.04 it goes nuts. I think it may be a heat issue as I leave my machine on for months at a time if I can only restarting if I have to.

ACPI is Advanced Configuration and Power Interface. When it is enabled your system knows about itself a bit more. It is recommended to keep it turned on whenever possible, but sometimes it just won't work with it enabled. You can deactivate it on boot time:

1. When GRUB appears press "e" (for edit).
2. You will see a long line of text. Append *acpi=off* to the end.
3. once you are done go back to the initial selection and press "b" to boot the selected kernel.

This is only a one-time change. Next time you reboot it will be gone. If you want to change it permanently you have to make changes in /etc/boot/grub/menu.lst.

---

### Post by nowshining on 2008-09-19
more lhan likely it is what I had when i tried hardy, the klogd service is hanging, ctrl + alt + f1 or f2 and login, from there sudo killall klogd and it should continue to boot up fine..

---

