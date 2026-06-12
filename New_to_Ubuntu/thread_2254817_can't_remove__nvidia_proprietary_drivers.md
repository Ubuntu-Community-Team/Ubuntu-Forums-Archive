---
title: "can't remove  nvidia proprietary drivers"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by rolands2 on 2014-11-30
Hello!  Following instructions on this page [http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely](http://askubuntu.com/questions/206283/how-can-i-uninstall-a-nvidia-driver-completely) I tried to remove all installed nvidia proprietary drivers, but I got this error:        >   (Reading database ... 230121 files and directories currently installed.) Removing nvidia-340 (340.58-0ubuntu1~xedgers14.10.1) ... stop: Unknown job: nvidia-persistenced userdel: user nvidia-persistenced is currently used by process 1508 dpkg: error processing package nvidia-340 (--remove):  subprocess installed post-removal script returned error exit status 8 Errors were encountered while processing:  nvidia-340 E: Sub-process /usr/bin/dpkg returned an error code (1)               What this error mean and is there way to fiz that? So the goal is to switch to nouveau driver, because after installing nvidia drivers I now have problems with screen freezing and web pages on firefox is not properly rendering. And also I cant switch to nouveau in additional drivers settings.

---

