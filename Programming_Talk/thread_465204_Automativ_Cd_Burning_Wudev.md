---
title: "Automativ Cd Burning W/udev"
date: 2007-06-05
forum: Programming Talk
---

### Post by geekgod on 2007-06-05
So here is the task 

A headless tower running kubuntu 7.04 containing 2 cd burners we will  call a and b.

What i need to accomplish which I imagine can be done with udev and a bash script, is that if a user puts a blank cd in drive A udev  calls a bash script that runs:

cdrecord -v speed=40 dev=0,0,0 Iso_file_a.iso
eject cdrom0

If a blank cd is placed in drive b we call the following

cdrecord -v speed=40 dev=0,0,1 Iso_file_b.iso
eject cdrom1

Any thoughts would be appreciated.

We are using this for internal duplication of Trixbox CD's but any result of this project could likely be adapted to a KIOSK that allows users to insert a disk and get their choice of x number of distros...


Thanks

---

### Post by geekgod on 2007-06-05
bump

---

### Post by KaeseEs on 2007-06-05
I'm not a udev hacker,but your basic Idea seems right.  Your control flow should be something like```
#receive udev event
#mount cdrom
#run cdrecord appropriately
#unmount cdrom
#eject
```

To this end, udev can be made to respond to events by writing 'rules'.  A quick guide can be found at [http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by geekgod on 2007-06-09
Heres the udev

<code>
KERNEL=="[hs]d[a-z]", PROGRAM="/home/james/cdburn.pl", SYMLINK="cdrom"

</code



Heres the perl script


<code>

#!/usr/bin/perl

open (HDD, "/proc/ide/hdd/capacity");
    my $hdd_cap =  <HDD>;
    close(HDD);
  
open (HDC, "/proc/ide/hdc/capacity");
    my $hdc_cap =  <HDC>;
    close(HDC);

  if ($hdd_cap == 4)
 { 
  print "Disk in Drive 2 \n";
  exec("/usr/bin/cdrecord -v -eject speed=16 dev=/dev/hdd /home/james/mycd.iso");
 }elsif($hdc_cap == 4){
 print "Disk in Drive 1 \n";
 exec("/usr/bin/cdrecord -v -eject speed=16 dev=/dev/hdc /home/james/mycd.iso");
 }else{print "NO DISK \n";}
fi;
</code>


This works on IDE Drives I have a revamped version of this I am prettying up, this was an initial stab at it if anyone wants a base. The 2nd version is udev free but only good if the machines sole purpose is the burn.

---

