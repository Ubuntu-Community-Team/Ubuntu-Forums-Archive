---
title: "Ubuntu 10.10 freezes at login"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by kyletos on 2011-09-12
Hello forum. I just started having this problem today. I dual boot a system with ubuntu 10.10 and windows 7. Windows runs fine, but whenever I select the ubuntu option, it takes me to the login screen and immediately freezes. I have tried a dozen times and nothing changes. I tried unplugging my mouse, and then plugging an external keyboard via USB (since I'm using a laptop) and that didn't work. I have an ASUS K501 with a Dual-Core 2.3 GHz processor and 4 gigabytes of RAM. 

There is a second additional problem however. I made a rookie mistake. A different forum had the same problem and all they did was delete the gconf directory from /etc. I, without making a backup, deleted it and tried to restart. Now, instead of freezing at the log in screen, it freezes at a screen with this error:

"there is a problem with the configuration server (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256"

I apologize for a long post. And any help from here would be appreciated. I have searched some threads from this site, but nothing seemed to help. Feel free to ask for any further clarifications or specifications if you need them. Thank you for your time and have a good day.

---

### Post by madjr on 2011-09-12
hi, is this a wubi install or is it installed on its own partition?

---

### Post by kyletos on 2011-09-12
It is installed on it's own partition. 

Any thoughts or other questions?

---

### Post by madjr on 2011-09-12
when you boot does it take you to GDM at least so you can choose an account?

maybe try login into another account or guest account.

do you remember anything in particular that happened before you started having this issue?

if you cant login into any account try going into recovery mode in grub and use the options presented like repair packages or fail safe graphics option, etc..

[http://1ijack.blogspot.com/2011/03/ubuntu-recovery-from-bad-update.html](http://1ijack.blogspot.com/2011/03/ubuntu-recovery-from-bad-update.html)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

if nothing else works (and no one else has another suggestion), i would try a live-cd, backup the files i need and probably just reinstall and get my system back working like new in 20 mins.

---

### Post by kyletos on 2011-09-15
So, when I booted, immediately after the account screen came up it froze. I couldn't choose anything. I don't remember doing anything before hand that was extreme, although it could have been an update that I installed.

I fixed the missing deleted file by booting with a live CD and then  copying the file into where it is supposed to be. 

Then to try and fix the other problems ctrl-alt-backspace did nothing but the alt-sysrq-R-E-I-S-O-B worked in restarting it. I really didn't want to reinstall because of many libraries that I have had to install for programs that I use. So, what ended up working was to update the entire system and then go into the grub mode and repair packages. So now it works and it's up and running.

---

### Post by madjr on 2011-09-15
> **kyletos said:**
> So, when I booted, immediately after the account screen came up it froze. I couldn't choose anything. I don't remember doing anything before hand that was extreme, although it could have been an update that I installed.

I fixed the missing deleted file by booting with a live CD and then  copying the file into where it is supposed to be. 

Then to try and fix the other problems ctrl-alt-backspace did nothing but the alt-sysrq-R-E-I-S-O-B worked in restarting it. I really didn't want to reinstall because of many libraries that I have had to install for programs that I use. So, what ended up working was to update the entire system and then go into the grub mode and repair packages. So now it works and it's up and running.

glad you could get it working, you're already a pro at this :)

---

