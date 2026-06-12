---
title: "Automate ECHO 255 | SUDO TEE command!"
date: 2016-05-19
forum: New to Ubuntu
---

### Post by kwanbis on 2016-05-19
Hello guys. I'm using Ubuntu 16.04 with my ThinkPad T520. The default sensitivity of the trackpoint is terrible, but I found out that this command fixes it:

echo 220 | sudo tee /sys/devices/platform/i8042/serio1/serio2/sensitivity

Now, how do I make that execute automatically each time I log in, ideally without having to type my password because of sudo?

Or is there a better way?

Thanks!

---

### Post by kwanbis on 2016-05-30
So I tried following this: [http://askubuntu.com/questions/290099/how-to-run-a-script-during-boot-as-root](http://askubuntu.com/questions/290099/how-to-run-a-script-during-boot-as-root)

But still no luck. Anyone?

---

### Post by kwanbis on 2016-06-01
Come on guys, I'm sure there is a way! I tried this but does nothing: [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)

---

### Post by Habitual on 2016-06-01
> **kwanbis said:**
> Come on guys, I'm sure there is a way! I tried this but does nothing: [http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up](http://askubuntu.com/questions/814/how-to-run-scripts-on-start-up)

We're volunteers?
If all you really need to do is put 220 into the /sys/devices/platform/i8042/serio1/serio2/sensitivity file on bootup, that should be easy.
What version of Ubuntu are we working with?

So, If I understand correctly, you can just edit /etc/rc.local and enter this
```
echo 220 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```above the ```
exit 0
```line.
in to the /etc/rc.local file.
and rebooting it should set it to 220.

the use of sudo in this context is not necessary. *but it is with tee*.
/etc/rc.local runs as root after all the system **services** have started.
Any command you stick in there runs as root.
Hope that helps.

---

### Post by kwanbis on 2016-06-01
> **Habitual said:**
> We're volunteers?
If all you really need to do is put 220 into the /sys/devices/platform/i8042/serio1/serio2/sensitivity file on bootup, that should be easy.
What version of Ubuntu are we working with?

So, If I understand correctly, you can just edit /etc/rc.local and enter this
```
echo 220 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
```above the ```
exit 0
```line.
in to the /etc/rc.local file.
and rebooting it should set it to 220.

the use of sudo in this context is not necessary. *but it is with tee*.
/etc/rc.local runs as root after all the system **services** have started.
Any command you stick in there runs as root.
Hope that helps.
Thanks. I know this is volunteering! I was just trying harder to ask!

I'm gonna try and get back. Thanks.

---

### Post by Habitual on 2016-06-02
```

...
# By default this script does nothing.

echo 220 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
exit 0

```

Perm should be [noparse]root:root[/noparse]  and mine is 755.

Have a Great Day!

---

### Post by kwanbis on 2016-06-02
> **Habitual said:**
> If all you really need to do is put 220 into the /sys/devices/platform/i8042/serio1/serio2/sensitivity file on bootup, that should be easy.
That is what I understand that I'm doing yes.

> **Habitual said:**
> What version of Ubuntu are we working with?
I'm using 16.04

> **Habitual said:**
> So, If I understand correctly, you can just edit /etc/rc.local and enter this
echo 220 > /sys/devices/platform/i8042/serio1/serio2/sensitivity[/CODE]above the ```
exit 0
```line.
and rebooting it should set it to 220.
Sadly, it does nothing :(

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 255 > /sys/devices/platform/i8042/serio1/serio2/sensitivity
exit 0
```

> **Habitual said:**
> the use of sudo in this context is not necessary. *but it is with tee*./etc/rc.local runs as root after all the system **services** have started. Any command you stick in there runs as root.
Any idea why?

---

### Post by Habitual on 2016-06-02
Can I have the output of ```
sudo stat --printf %a %n \n /etc/rc.local
``` please?

---

### Post by Habitual on 2016-06-02
Can I have the output of ```
sudo ls -lF /etc/rc.local
``` please?

---

### Post by kwanbis on 2016-06-02
> **Habitual said:**
> Can I have the output of ```
sudo ls -lF /etc/rc.local
``` please?
Sure thing!

```
kwanbis@U520:~$ sudo stat --printf %a %n \n /etc/rc.local
stat: cannot stat '%n': No such file or directory
stat: cannot stat 'n': No such file or directory
755kwanbis@U520:~$ sudo ls -lF /etc/rc.local
-rwxr-xr-x 1 root root 370 jun  2 08:59 /etc/rc.local*
```

---

### Post by Habitual on 2016-06-02
Those are good perms and owner:group
Does the "/sys/devices/platform/i8042/serio1/serio2/sensitivity" file exist on your system?
terminal  and issue:
```
sudo ls -lF /sys/devices/platform/i8042/serio1/serio2/sensitivity
```
and since we expect it to be successful, let's just see what's in it **after you boot**,
```
sudo grep 220 /sys/devices/platform/i8042/serio1/serio2/sensitivity
```
What's the result?

---

### Post by kwanbis on 2016-06-02
> **Habitual said:**
> Those are good perms and owner:group
Does the "/sys/devices/platform/i8042/serio1/serio2/sensitivity" file exist on your system?
terminal  and issue:
```
sudo ls -lF /sys/devices/platform/i8042/serio1/serio2/sensitivity
```
and since we expect it to be successful, let's just see what's in it **after you boot**,
```
sudo grep 220 /sys/devices/platform/i8042/serio1/serio2/sensitivity
```
What's the result?
IT WORKED! I rebooted the system and now it is working! It seems the first time I only logged off and in again! Just in case, here is the information you requested:

kwanbis@U520:~$ sudo ls -lF /sys/devices/platform/i8042/serio1/serio2/sensitivity[sudo] password for kwanbis: 
-rw-r--r-- 1 root root 4096 jun  2 09:00 /sys/devices/platform/i8042/serio1/serio2/sensitivity
kwanbis@U520:~$ 

BOOT

kwanbis@U520:~$ sudo ls -lF /sys/devices/platform/i8042/serio1/serio2/sensitivity[sudo] password for kwanbis: 
-rw-r--r-- 1 root root 4096 jun  2 15:03 /sys/devices/platform/i8042/serio1/serio2/sensitivity
kwanbis@U520:~$ 

THANKS A LOT!

---

### Post by Habitual on 2016-06-02
Glad it worked out!

---

