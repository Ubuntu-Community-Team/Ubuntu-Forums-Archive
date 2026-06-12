---
title: "Getting Weird sudo errors in console. Probably lost root priviledges totally"
date: 2013-12-23
forum: New to Ubuntu
---

### Post by dreadkit.kat on 2013-12-23
Last thing that changed in my system was I installed AVG antivirus to scan an effected Hard drive. 
And I didn't even notice it then. After uninstalling AVG i got a few weird log messages in the console which I ignored for the timebeing.

sudo: /etc/sudoers.d/avg-gui is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-main is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-settings is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-updatedaemon is mode 0755, should be 0440

I also installed the avg gui application from this link
[http://forums.avg.com/in-en/avg-forums?sec=thread&act=show&id=234645](http://forums.avg.com/in-en/avg-forums?sec=thread&act=show&id=234645)

and then uninstalled it as well...

This is after uninstalling the avg. I get this same exact message everytime I sudo any command. I am trying to install multisystem and am not able to install it as it says that I am not root user even though I am using sudo with it.

---

### Post by sisco311 on 2013-12-23
It looks like something went wrong during the uninstallation process. 

You should be able to use pkexec to run commands as root and fix the file permissions:
```
pkexec chmod 0440 /etc/sudoers.d/avg-gui
pkexec chmod 0440 /etc/sudoers.d/avg-main
...
```

Or if you are sure that the package is no longer installed, then you can remove the files.

---

### Post by whitesmith on 2013-12-23
> **dreadkit.kat said:**
> Last thing that changed in my system was I installed AVG antivirus to scan an effected Hard drive. 
And I didn't even notice it then. After uninstalling AVG i got a few weird log messages in the console which I ignored for the timebeing.

sudo: /etc/sudoers.d/avg-gui is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-main is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-settings is mode 0755, should be 0440
sudo: /etc/sudoers.d/avg-updatedaemon is mode 0755, should be 0440

I also installed the avg gui application from this link
[http://forums.avg.com/in-en/avg-forums?sec=thread&act=show&id=234645](http://forums.avg.com/in-en/avg-forums?sec=thread&act=show&id=234645)

and then uninstalled it as well...

This is after uninstalling the avg. I get this same exact message everytime I sudo any command. I am trying to install multisystem and am not able to install it as it says that I am not root user even though I am using sudo with it.You don't say why you installed AVG. Are you dual-booting into Win/Ubuntu? Ubuntu effectively self-isolates from malware, so a 100% pure Linux system probably doesn't need it. You definitely have not "lost" root privileges. Linux doesn't work without root. Prove this to yourself by doing ```
sudo su && whoami
``` Make sure you immediately```
exit
``` or you can cause even more problems. Consider uninstalling AVG and keep your distance from stuff like this. Most AV thingies today are just theatrical software. They enter stage-left, speak soothing (but ineffective) lines and then exit without doing anything useful. See what Bruce Schneider and other experts have to say about all this AV noise, then make up your mind. Best of luck to you!

---

