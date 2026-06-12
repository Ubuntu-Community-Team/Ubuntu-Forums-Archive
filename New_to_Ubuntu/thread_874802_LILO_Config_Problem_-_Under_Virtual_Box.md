---
title: "LILO Config Problem - Under Virtual Box"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by tdz on 2008-07-30
I have already tried to get an answer to this problem on the Virtual Box forums. I was directed to try a more specialized forum for getting kernel builds up and running. As I indicated below, I am a newbie to Ubuntu and relatively new to Linux.  This is my first kernel, especially under vbox.  I'm not sure if a complete native install would have this problem.  Since this is a work project, though, I need to use the environment that my employer has.

I should indicate that the kernel seems to build with no problems.

I am attempting to rebuild the 2.6.24-16 Ubuntu kernel to support a device driver that I am working on. Initially, LILO was not installed on my system.

After installing LILO to help support the rebuilt kernel (per the README and HOWTO in the kernel source tree), I was instructed by apt-get to run liloconfig.

Liloconfig fails to run, but gives the following warning:

"WARNING!

Your /etc/fstab configuration file gives device UUID=2cd970-4f40-492a-91bf-fe683c083e1b as the root filesystem device. This doesn't loot to me like an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple configuration program does not handle.

You should either repair the situation or hand-roll your own /etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig again to retry the configuration process. Documentation for LILO can be found in /usr/share/doc/lilo/."

Since I'm a relative newbie to both kernel building and vbox, I'm not sure how to proceed. The advice I've gotten so far is that the filesystem used under vbox is "different" from that used for a full native install and that is causing this.

I'm not sure what to do to roll my own lilo.conf using the information in fstab. In fact, at this point, if someone has some advice on manually copying the kernel, etc and not using LILO or GRUB, that would be ok.  (Actually, if this is doable, that may be preferable just to get more sense of what is involved in installing a kernel.  I suspect that early on there were no tools like LILO and folks had to do a lot of this stuff by hand anyway.)

The hardware is a standard Dell PC with no RAID or other esoteric hardware attached.

Thanks in advance.

Tom

---

### Post by The Cog on 2008-07-30
In fstab, you will probably find a pair of lines for each mounted partition. The first line is a commented out device name sudh as /dev/sda1 and that is followed by the actual configuration line for that partition, but using the UUID identifier instead of the /dev/... identifier. 

The UUID uses a disk label, which can be useful because the mounting system can still find the right partition if you add/delete other partitions or move hard disks around, which would render a /dev/... definition pointing at the wrong place. Hope that makes sense.

Anyway, for now I suggest you make a copy of the oriiginal /etc/fatab file, then replace the UUID= identifier with the /dev/sd... identifier from the line above. I.e. change

# /dev/sda5
UUID=8937492598745 ext3 / <rest of the stuff...>

to 

/dev/sda5 ext3 / <rest of the stuff...>

which should keep that other program happy. Unless you are shuffling disks or partitions, you will never know the difference yourself.

---

### Post by tdz on 2008-07-30
**THANK YOU.**

The suggestion worked.

Now it's on to the next step in getting my kernel loaded and my driver (and the hardware) working.  I must admit, this is both a challenge and fun.  I'm relatively new to Linux, but not to software.  Most of my background is in fighting with various RTOS systems and there a lot of this would involve trying to persuade a vendor to solve the problems or provide the help.  The Linux community approach is a lot better (and faster).  :)

Tom

---

