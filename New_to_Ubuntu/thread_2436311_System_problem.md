---
title: "System problem"
date: 2020-02-04
forum: New to Ubuntu
---

### Post by old-nomad on 2020-02-04
I have only just installed Ubuntu-18.04 LTS and everything is fine except When i boot-up the machine i get a pop-up warning me that a: System program problem was detected. The only option i have is to report this problem. Can anyone tell me how i might resolve this problem please. Perhaps a new install?

---

### Post by sdsurfer on 2020-02-04
I get these now and then too, and am interested in any replies. Have you dug into the logs and found anything? I started the thread below months ago and it is unanswered. Generally everything else works as expected, correct?

[https://ubuntuforums.org/showthread.php?t=2425037](https://ubuntuforums.org/showthread.php?t=2425037)

---

### Post by yetimon_64 on 2020-02-04
> **sdsurfer said:**
> ...Have you dug into the logs and found anything? ...
The directory /var/crash holds the crash files and usually contains the name of the offending application in the file name. Simply listing the directory will show what applications have crashed.
```
ls /var/crash
```

The application/service that generates these reports is apport. As I don't generally follow through with reporting errors and if they become too much of a nuisance I disable apport in /etc/default/apport by setting "enabled=0" ; to do so you can use the command... 
```
pkexec gedit /etc/default/apport
```
and set the "enabled" setting to 0 (zero) then save the file.

To make absolutely sure apport doesn't show any more pop ups I also mask the service with the command...
```
sudo systemctl mask apport
```

The apport service is only for error reporting back to Canonical and it can be turned off. Definitely no need to do a reinstall for such, especially if the system is otherwise usable/stable.

If you want to keep apport active but have a particular crash file causing a persistent pop up you can just clean out the /var/crash directory with "sudo rm /var/crash/*" (without the quotes); this will stop pop ups temporarily till the next crash generates a new file. This is probably better than disabling  or turning off the service totally as new errors can be viewed. Sometimes the system will throw up a few errors then eventually settle down I've noticed. Some applications like compiz (I'm on ubuntu mate with compiz) will constantly cause such error reports; this type of situation is what causes me to disable/mask the apport service most of the time. **Edit**: I should note it is possible to blacklist a particular application (like compiz noted here) from error reporting without turning off or disabling apport.

Regards, yeti.

---

### Post by MoebusNet on 2020-02-04
@old-nomad - You say this is a fresh installation; is it possible that you have not installed any updates yet? I had an issue with that pop-up: it was referring to a bug that was fixed in subsequent updates. After the updates, the pop-up disappeared.

EDIT - This is the thread where my issue was addressed: [https://ubuntuforums.org/showthread.php?t=2424834](https://ubuntuforums.org/showthread.php?t=2424834)

I took the mentioned actions, but I believe a fix was issued later.

---

### Post by yancek on 2020-02-04
On the occasions I have seen that error, there is an option to click on Details which shows a little more info.

---

