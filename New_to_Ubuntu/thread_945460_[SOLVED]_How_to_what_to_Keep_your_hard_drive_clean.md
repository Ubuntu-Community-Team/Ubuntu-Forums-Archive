---
title: "[SOLVED] How to: what to: Keep your hard drive clean"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by ghoran on 2008-10-12
A while back I was given help to clean up space using
sudo rm -r /var/cache/apt/archives/*.deb

My question is are there other areas on the drive that can be cleaned up/archived on a regular basis

Thanks!

---

### Post by scragar on 2008-10-12
isn't that line the same as ```
sudo apt-get clean
```? From the man page:
>        clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

I don't think there is anywhere that builds up a bunch of files without a good reason.

---

### Post by Pro-reason on 2008-10-12
Install [Filelight](apt://filelight), and use it to see what is taking up space.  Generally, emptying your trash and clearing out your APT cache is all you need to do.

---

### Post by bodhi.zazen on 2008-10-12
Not as much with Linux as compared to other OS.

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html) 
   
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by Idefix82 on 2008-10-12
ou can have a look at [this tutorial]("http://ubuntuforums.org/showthread.php?t=140920"), but I would exercise extreme caution in following it. The author was a bit too reckless for my liking when it comes to deleting things. However, the tip with the orphaned packages filter for Synaptic is quite useful.

Bear in mind, that some packages are reported as orphaned just because they don't have any dependants. It doesn't automatically mean that you don't need them. But it's like with all tools which can damage things: just use common sense and ask questions if unsure.

---

### Post by ghoran on 2008-10-12
I want to thank everyone for their quick replies.
scragar- I did understand that it is the same as "sudo apt-get clean".
During the day, I work as a software engineer in a multi-platform shop.
One platform is SUN Unix and I therefore try to understand what the system engineers need to do.
I figure the more I understand about the OS the better off I am :)

---

### Post by ghoran on 2008-10-12
This machine has a small hard drive so I thought I would let everyone know what
[http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)
did

Before: (Note: I already did "sudo rm -r /var/cache/apt/archives/*.deb")

dad@ash-desktop:~$ df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              5874396   5412140    163852  98% /


Tip #1 - Getting rid of Residual Config packages
Only saw installed / not installed = Nothing to do

Tip #2 - Getting rid of partial packages
First I got:
dad@ash-desktop:~$ sudo apt-get autoclean
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dad@ash-desktop:~$ 

Then I realized that Synaptic Package manager needed to be shutdown

dad@ash-desktop:~$ df -k|grep sda1
/dev/sda1              5874396   5412196    163796  98% /
dad@ash-desktop:~$ 

Not much help there 

Tip #3 - Getting rid of unnecessary locale data 
Not much help there . either
/dev/sda1              5874396   5412456    163536  98% /


Tip #5- Adding a "Find orphaned packages" to Synaptic Package Manager- Skipped to this as recommended
There was only one orphaned package.
/dev/sda1              5874396   5413124    162868  98% /


I understand that I did not have much success but, I now have the tools to keep my machine clean.

THANKS!

---

### Post by Idefix82 on 2008-10-13
> **ghoran said:**
> 
Tip #5- Adding a "Find orphaned packages" to Synaptic Package Manager- Skipped to this as recommended
There was only one orphaned package.
/dev/sda1              5874396   5413124    162868  98% /

THANKS!

This procedure is particularly useful if you find something that you don't need and delete it. Just browse through the list of installed packages and remove those that you are certain you don't need. Example: you uninstall the GNOME-Games package. That by itself doesn't free much space. But then you discover that there are now two orphaned packages (don't quote me on numbers) so you uninstall those. You run the filter again and notice that more packages have become orphaned due to you uninstalling the previous ones (the search depth of this filter is one level). You keep going until no new orphaned packages show up and notice that you have freed up more than 100MB of space.

---

