---
title: "ubuntu 2.04 boot problem"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by chitragurung on 2012-07-25
I got problem with ubuntu 10.04.4 and I re install ubuntu 12.04 using USB.

Now it does not boot only can boot from USB. How can I change it

Also, no wireless network and I could not find terminal for command etc.

My machine is Dell inspiron mini 10.

---

### Post by drs305 on 2012-07-25
Grub is probably installed on the USB drive instead of your main drive. Try installing Boot Repair (link in sig line) and clicking on "Recommended Repair". If that doesn't fix it, post the contents of, or link to, the boot info script results. You can run the script from Boot Repair.

You should be able to open a terminal with CTRL-ALT-T.

---

### Post by chitragurung on 2012-07-25
how to install boot repair

---

### Post by drs305 on 2012-07-25
> **chitragurung said:**
> how to install boot repair

Please see the link in my signature line for Boot Repair.

---

### Post by chitragurung on 2012-07-25
I have not internet connection in troubled laptop. How can I install boot repair using usb ?

---

### Post by drs305 on 2012-07-25
I thought it was just your wireless that wasn't working...

You can make a Boot Repair or Ubuntu Secure Remix CD from another computer. 

You might be able to download the .deb file from your working computer, copy it to your Ubuntu system, and then double-click to install or:
```
sudo dpkg -i /<path>/boot-repair_3.18-0ppa42~precise_all.deb
```

You can download the file from:
[https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages]("https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages")
Click the top package (the first boot-repair link, then click again on the filename above to download the deb file.

Creating a bootable disk would be better if your Ubuntu computer has a CD/DVD drive.

---

### Post by chitragurung on 2012-07-25
I got error when I try to install in Ubuntu

---

### Post by d4m1r on 2012-07-25
> **chitragurung said:**
> I got error when I try to install in Ubuntu


Well...what was the error?

---

### Post by chitragurung on 2012-07-25
it is just blinking cursor in blank black screen.

---

### Post by chitragurung on 2012-07-26
I got following message when try boot repair

chitra@chitra-Inspiron-1011:~$ sudo dpkg -i /home/chitra/Home/Downloads/boot-repair_3.18-0ppa42~precise_all.deb
[sudo] password for chitra: 
dpkg: error: dpkg status database is locked by another process
chitra@chitra-Inspiron-1011:~$ ^C
chitra@chitra-Inspiron-1011:~$ 





> **drs305 said:**
> I thought it was just your wireless that wasn't working...

You can make a Boot Repair or Ubuntu Secure Remix CD from another computer. 

You might be able to download the .deb file from your working computer, copy it to your Ubuntu system, and then double-click to install or:
```
sudo dpkg -i /<path>/boot-repair_3.18-0ppa42~precise_all.deb
```You can download the file from:
[https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages]("https://launchpad.net/%7Eyannubuntu/+archive/boot-repair/+packages")
Click the top package (the first boot-repair link, then click again on the filename above to download the deb file.

Creating a bootable disk would be better if your Ubuntu computer has a CD/DVD drive.

---

### Post by drs305 on 2012-07-26
Chitra,

The 'lock' message probably indicates there are two processes trying to use the package manager (APT) at the same time. If you have Ubuntu Software Center, Update Manager or Synaptic open it generates a 'lock' file and running the terminal command won't work. Make sure none of these other applications is open.

If you can't find another running APT application, rebooting will usually remove the lock file and the command can then run.

---

### Post by chitragurung on 2012-07-27
after updating and installing boot repair, it came to normal  operation. 

But now got problem in Evolution address book.

In Ubuntu 12.04 I copied all the messages all the folders but I could not copy addressbook.db to new evolution in Ubuntu 12.04 as well thunderbird.

How can I manage it. I try to find various solutions in google but no success.

Thanks

---

### Post by drs305 on 2012-07-27
> **chitragurung said:**
> after updating and installing boot repair, it came to normal  operation. 

But now got problem in Evolution address book.

In Ubuntu 12.04 I copied all the messages all the folders but I could not copy addressbook.db to new evolution in Ubuntu 12.04 as well thunderbird.

How can I manage it. I try to find various solutions in google but no success.

Thanks

Glad at least one problem is fixed. I suggest opening a new thread for yor evolution issue, as the helpers for that might be different that the ones who read this thread.

When you are done with this thread, please mark it SOLVED via the 'Thread Tools' link near the top right of the first post. Thanks.

---

