---
title: "Lubuntu 14.04 frozen in FireFox"
date: 2014-08-01
forum: New to Ubuntu
---

### Post by milty2012 on 2014-08-01
Lubuntu has been locking up while in Firefox - I can move the mouse but do nothing else - I can sometimes Ctrl-ALT-F1 and get out of the GUI interface and come back in via ctrl-alt-F7. My question, while outside of the GUI what comand or logs etc should I run or check in an attempt to unfreeze Lubuntu? Otherwise my only fix is a cold reboot. 

Thanks...Milty

---

### Post by claracc on 2014-08-02
I think tou will have to search what is the process which freezes ubuntu, i.e., you could try to write ```
ctrl+alt+t
``` in order to open a xterm, then there you can run top command to see which process is eating ram or cpu, see attached image.Also, when you discover the process which freeses computer, would be good to know why (proper video card driver?, enough ram?). Also, it can be useful to see in /var/log/messages if there is any error.

Then, when you have identified the culprit process ( it can be firefox or Xorg...) you can end the process, running in xterm ```
kill -9 PID_number_of_process
``` and see if computer unfreezes.

Also, you can try to log out of session with command line in xterm:

```
sudo pkill -u username
sudo service lightdm restart
```

And the last resource if nothing works, you can reboot system safely with:

```
alt+sysrq+ R E S U I B
``` or
```
alt+Prn Scrn+ R E S U I B
```

Please, see: [http://ubuntuforums.org/showthread.php?t=1256574](http://ubuntuforums.org/showthread.php?t=1256574)

---

