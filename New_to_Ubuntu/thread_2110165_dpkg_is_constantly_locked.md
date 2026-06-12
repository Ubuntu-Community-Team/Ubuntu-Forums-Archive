---
title: "dpkg is constantly locked"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Pieman15 on 2013-01-29
I'm having issues with dpkg after my system froze during an update this morning. It's constantly in a locked state and I cannot unlock it permanetly. When I open the Ubuntu Software Center, there's an item titled "Searching" that is in progress (the item remaing after rebooting). I believe this might be my culprit, but I'm unable to cancel it successfully. Here's what I've attempted:
 
ps -e | grep -e apt -e adept | grep -v grep
I see one process, but I cannot kill it using sudo kill <pid>
 
I've also tried:
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
After running these commands, if I try to use dpkg I'm asked to configure dpkg using sudo dpkg --configure -a.
sudo dpkg --configure -a
This command freezes after the screen reads "DKMS install complete". Upon rebooting multiple times, dpkg is still locked. I've also tried running the two rm commands then rebooting, but to no avail.
 
Perhaps unrelated, but difficult to fix without the use of the dpkg command, I also lost both my eth0 and wlan0 interfaces when my system froze. It's weird, if my ethernet cable is plugged in after a reboot, both interfaces will appear under ifconfig -a and the internet will work for 1-2 minutes. Then, they both become disabled and ifconfig -a only shows my lo interface. If the cable is unplugged after a reboot, neither interface is enabled and ifconfig -a only shows my lo interface. Normally, I never use eth0, but I hooked it while trying to troubleshoot my wlan0 issues.
 
Any ideas? Thanks in advance for your help.

Solved: 
ps ax | grep dpkg
sudo kill <pid(s)>
In my case, the update froze while installing something called bcmwl-kernal-source, something related to my broadcom wireless card. Even after a rebooting multiple times, dpkg was "stuck" attempting to install the bcmwl-kernal-source, so I had to first delete the dpkg pids and then remove the bcmwl-source-kernal (sudo apt-get remove bcmwl-kernal-source). I then restarted and my network interfaces returned back to normal and dpkg was free.

---

### Post by mörgæs on 2013-01-31
Please mark the thread 'solved' using 'thread tools'. Have done it for you this time.

---

