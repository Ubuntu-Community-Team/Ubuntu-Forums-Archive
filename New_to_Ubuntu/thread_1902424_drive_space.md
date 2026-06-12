---
title: "drive space"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by degarb on 2011-12-30
After trying to use linux for 12 years, reading thousands of pages and usually abandoning linux for one reason or another, I still have no recollection or knowledge how to check free space on drive. (one of my linux mental blocks is I totally reject that a drive can be a directory. I reject this, reject this, reject this.).

Nautilus is useless, since it shows file system and not drive.  The size varies by hundreds of megs by the minute, depending on folder you are in.  Come on, any user of windows can=p find this out in 5 minutes of using windows, and will never forget. Also, window has better warning and protection against running out of free space unexpectedly.  The other day, Nautilus was telling me I have 100 to 200 megs free, then my file system hit zero after trying install one deb.  This locked me out of the main user account, I am guessing some validation file couldn't be copied due to lack of space. 

What does this mean?

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.3G  4.4G  596M  89% /
udev                  249M  236K  249M   1% /dev
none                  249M  272K  249M   1% /dev/shm
none                  249M  324K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw


Do I have 596 meg free or 249  or something all together different?  I am not trusting the larger number, due to the other day exerience.

---

### Post by chipbuster on 2011-12-30
it...looks like you have 569 MB free, and your Linux partition is only 5.3 GB to begin with o.0"

Did you intend to make a 5GB Linux system when you installed?

---

### Post by degarb on 2011-12-30
> **chipbuster said:**
> it...looks like you have 569 MB free, and your Linux partition is only 5.3 GB to begin with o.0"

Did you intend to make a 5GB Linux system when you installed?

I think the drive is 6 gig.  I think I made the swap double the ram.  Old 600 mhz laptop.  Runs, surprisingly well.  There only should be two partitions.  I wiped off win95.  The kids and wife worked to gether to break off the usb jump stick, so no longer will that be adding megs to this screen.  but my guess a jump drive would really confuse things.

---

### Post by degarb on 2011-12-30
> **chipbuster said:**
> it...looks like you have 569 MB free, and your Linux partition is only 5.3 GB to begin with o.0"

Did you intend to make a 5GB Linux system when you installed?


what is the 249 number?

---

### Post by Zill on 2011-12-30
> **degarb said:**
> I think the drive is 6 gig...

[Ubuntu Recommended Minimum System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")
> 15 GB of hard-drive space

[Windows 7 system requirements]("http://windows.microsoft.com/en-GB/windows7/products/system-requirements")
> 16 GB available hard disk space (32-bit) or 20 GB (64-bit)

---

### Post by aeronutt on 2011-12-30
Might try ```
df -h --total
```

---

### Post by chipbuster on 2011-12-30
I'll be honest--I'm not really sure. From what I can tell, they appear to be RAMdisks (filesystems created in the RAM), but that doesn't make sense because that's way more RAM than you have.

The data is in the format NAME TOTAL USED FREE (other stuff)

For example, the last line tells us that there is a partiton named "none" with 249M total space, and 0M used, so 249M free, and that it's mounted on /lib/init/rw

Could someone clear up exactly what these filesystems are and why they're needed?

---

### Post by degarb on 2011-12-30
> **chipbuster said:**
> I'll be honest--I'm not really sure. From what I can tell, they appear to be RAMdisks (filesystems created in the RAM), but that doesn't make sense because that's way more RAM than you have.

The data is in the format NAME TOTAL USED FREE (other stuff)

For example, the last line tells us that there is a partiton named "none" with 249M total space, and 0M used, so 249M free, and that it's mounted on /lib/init/rw

Could someone clear up exactly what these filesystems are and why they're needed?

My guess is to confuse and obfuscate.   I did find system monitor.  From that my best guess from sysmon, 249 is likely the free space on the swap.  For some reason, it was setup with only 298 meg of swap, with 500 meg of ram.

When I installed ubuntu 9.1 on the machine, xubuntu ran just as slow and had tons of necessary stuff missing to qualfy it as a real os--more something you spend the next 30 hours adding stuff to get machine functional.  I was barely under the specs of the 2 year old os.  But  worked out fine.

---

### Post by oldos2er on 2011-12-30
udev: [http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

Info on /run/lock and /run/shm: [http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run](http://askubuntu.com/questions/57297/why-has-var-run-been-migrated-to-run)

---

