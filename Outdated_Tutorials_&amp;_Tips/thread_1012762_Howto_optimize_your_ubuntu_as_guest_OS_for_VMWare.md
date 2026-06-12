---
title: "Howto optimize your ubuntu as guest OS for VMWare"
date: 2008-12-16
forum: Outdated Tutorials &amp; Tips
---

### Post by cmartins on 2008-12-16
My company has given me a lazy laptop with the laziest harddisk i’ve seen! And since i abuse from vmware and have usually 2 or 3 VM’s running, i’ve had to make some tunnings to my ubuntu.

My thoughts beside any optimization:

    * The disk is slow, i cant persist vmware memory on a harddisk file
    *I have 4G of RAM, i want to use and abuse from it
    * Ubuntu by default writes the modification timestamp… i want to avoid disk IO
    * Do i really need my laptop to work as a laptop? no…

So… here it goes…

on /etc/vmware/config or in each  vmx
mainMem.useNamedFile = FALSE
tmpDirectory=”/dev/shm”

#let’s garantee that we’ve have a steady memory…
prefvmx.useRecommendedLockedMemSize=”TRUE”
prefvmx.minVmMemPct=”100&#8243;
MemTrimRate = “0&#8243;
MemAllowAutoScaleDown = “FALSE”

#to collapse the memory shared pool
mem.ShareScanTotal=0
mem.ShareScanVM=0
mem.ShareScanThreshold=4096
sched.mem.maxmemctl=0
sched.mem.pshare.enable = “FALSE”

- To remove the acccess timestamp i’ve modified/etc/fstab and put the noatime in each hdd mount

- Increase the shared memory size
/etc/default/tmpfs   SHM_SIZE=4G

-disabling laptop tools
sudo chmod -x /usr/lib/pm-utils/power.d/laptop-tools

- Some /etc/sysctl.conf magic
vm.swappiness = 0
vm.overcommit_memory = 1
vm.dirty_background_ratio = 5
vm.dirty_ratio = 10
vm.dirty_expire_centisecs = 1000
dev.rtc.max-user-freq = 1024
vm.laptop_mode = 0

And that’s it :) My life is shining!! :) 


My post at:
[http://cmartinstekzone.wordpress.com/2008/11/20/my-ubuntus-optimization-to-vmware/](http://cmartinstekzone.wordpress.com/2008/11/20/my-ubuntus-optimization-to-vmware/)

---

