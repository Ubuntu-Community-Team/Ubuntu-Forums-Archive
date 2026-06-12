---
title: "Please Help!!! Ubuntu 8.04 couldn't boot"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by mulen7 on 2008-12-01
Hello all,

 I new to Linux. I have Ubuntu Hardy installed on my Toshiba Laptop, (1GB RAM, no CD Drive). I was trying to setup Remote Desktop, to access my office' PC while away. And I ran 

'sudo chmod 644 *' by mistake in the Terminal, and all the files and folders on my Desktop disappeared. Then we I rebooted the laptop, Ubuntu couldn't reboot, instead I'm stuck with (initramfs).

PLEASE HELP!!!!!!!!!!!!

Regards,

---

### Post by taurus on 2008-12-01
When you ran that command, what directory were you in?  Were you in your $HOME or were you in root, /?

---

### Post by mulen7 on 2008-12-01
I was in my $HOME directory. but I entered the password for sudo earlier, before running chmod command

---

### Post by taurus on 2008-12-01
So your machine won't boot at all?  Have you tried the recovery mode?  

Otherwise, you can fix your $HOME from the LiveCD.  Boot your machine with the LiveCD.  Then, open a terminal and mount your harddrive, assuming you don't have a separate /home and your / is located at /dev/sda1.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
cd /media/ubuntu/home
sudo chmod -R 755 <your_username>
sudo chmod 600 <your_username>/.dmrc
```
Replace <your_username> with the name that you log in to your machine.  Reboot and see what happens then.

---

### Post by mulen7 on 2008-12-01
I don't have CD Drive, (neither internal, nor external). I've tried the recovery mode but the same thing happens (initramfs).

---

