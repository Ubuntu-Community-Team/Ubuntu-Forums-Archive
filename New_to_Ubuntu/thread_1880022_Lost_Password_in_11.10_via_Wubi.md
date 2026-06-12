---
title: "Lost Password in 11.10 via Wubi"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by FleeingHomework on 2011-11-12
Hello.  I'm very new to Ubuntu, and recently decided to try using it through Wubi, but I forgot my password completely.  I've been trying to recover it for a few days, and haven't had any luck.

I first tried to follow the technique described here:
[http://ubuntuforums.org/showthread.php?t=1041232](http://ubuntuforums.org/showthread.php?t=1041232)
Using root shell or a recovery mode to reset the password.
Unfortunately, I could never get to either mode to try anything.

I also tried using a live CD, but struggled to mount the drive properly.  I eventually found some sort of shadow file I could get to, but then it said I didn't have sufficient permission to access it.

I'd appreciate any help or advice; I'm looking for anything that will prevent me from having to reinstall Oneiric.
Thanks

---

### Post by bcbc on 2011-11-12
Boot in recovery mode. Currently that will boot you to a root prompt (it's supposed to be the recovery menu, but until the fix gets through, wubi users on 11.10 get a root prompt).

Then confirm your userid: 
```
ls /home
```
On mine it looks like this:
> root@ubuntu:~# ls /home
bcbc
root@ubuntu:~# 


So my userid is *bcbc*

Then change the password with:
```
passwd <userid>
```
e.g. for me
```
passwd bcbc
```

Enter the new password and then reboot to test:
```
reboot
```

---

### Post by FleeingHomework on 2011-11-13
Thank you very much.  I was also missing that I needed to press shift from the operating system load screen (where I select ubuntu) in order to get to the menu with recovery mode as an option.

---

