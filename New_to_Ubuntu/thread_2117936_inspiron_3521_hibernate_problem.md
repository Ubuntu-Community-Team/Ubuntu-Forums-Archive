---
title: "inspiron 3521 hibernate problem"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by cifadam on 2013-02-19
Hi everyone;

I recently bought a Dell Inspiron 3521 laptop. It came with a 12.04 ubuntu installation. I really don't like unity, so I set up Xubuntu 12.04 with my existing iso. But after a few days i realized my OS is 32bit and laptop is 64bit. And there were some stability problems. Then I decided to go back to original system and install xubuntu-desktop on it. I did exactly like this. Now almost everything is ok, but hibernate is not working. In 32bit xubuntu installation it was working, but now is not. My system is completely up to date. I've been searching for a few days, but couldn't find something useful/working. Is anybody can help me? Thanks a lot.

---

### Post by Toz on 2013-02-19
Hello and welcome to the forums.

How are hibernating the laptop? (Hibernation is disabled by default in 12.04 - see: [http://askubuntu.com/questions/94754/how-to-enable-hibernation]("http://askubuntu.com/questions/94754/how-to-enable-hibernation"))

Can you post back the contents of your /var/log/pm-suspend.log file like this (from a terminal window):
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

---

### Post by cifadam on 2013-02-20
hi again and thanks :)

i tried to hibernate after configuring the hibernate option according to ubuntu help page. but didn't work. here is the output: [http://paste.ubuntu.com/1690270/](http://paste.ubuntu.com/1690270/)

---

### Post by Toz on 2013-02-20
I'm willing to bet that zram is interfering with your hibernate attempt. Did you install zram purposefully?

What does:
```
cat /var/log/syslog | grep PM:
```
...return?

Links of interest:
- [http://ubuntuforums.org/showthread.php?t=1987805]("http://ubuntuforums.org/showthread.php?t=1987805")
- [http://ubuntuforums.org/showthread.php?t=2087415]("http://ubuntuforums.org/showthread.php?t=2087415")
- [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/954668]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/954668")

---

### Post by Toz on 2013-02-20
And oh, hibernate will also _not_ work if you have an encrypted swap file. See: [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Failure_due_to_encrypted_swap]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume#Failure_due_to_encrypted_swap").

There is a potential way to make it work though, see: [https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap]("https://help.ubuntu.com/community/EnableHibernateWithEncryptedSwap")

---

### Post by cifadam on 2013-02-20
```
cat /var/log/syslog | grep PM:
``` gives this: [http://paste.ubuntu.com/1690746/](http://paste.ubuntu.com/1690746/)

i've never heard about zram nor encrypted swap :/ i'm looking at the links you gave right now.

---

### Post by cifadam on 2013-02-20
[IMG]http://img16.imageshack.us/img16/7392/screenshot0220201305070.png[/IMG]

by the way, my swap partition is in an extended partition, can it be related?

---

### Post by cifadam on 2013-02-20
i followed this quote, in [this]("http://ubuntuforums.org/showthread.php?t=2087415") page, which is originally from [this ]("https://help.ubuntu.com/community/SwapFaq")page. first not worked, but then i installed zram-config, restarted, than it worked. 

>  			 				Making the swap partition work for hibernate (optional) 
**'INFO: This will not work for 12.04, resume from hibernate work differently in 12.04.**' 

[LIST=1]
[*]Pull up a Terminal again and  run cat /proc/swaps  and hopefully you see the path to your swap  partition listed there. If  not chances are something went wrong in the  steps above. Here's my  output:
[/LIST]

Filename                                Type            Size    Used     Priority /dev/sda2                               partition       2676732  73380   -1
[LIST=1]
[*]gksu gedit /etc/default/grub & to pull up the boot loader configuration
[*]Look for the line GRUB_CMDLINE_LINUX="" and make sure it looks like  this (using your UUID of course)  GRUB_CMDLINE_LINUX="resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7"  and save the file
[*]sudo update-grub and wait for it to finish
[*]gksu gedit /etc/initramfs-tools/conf.d/resume & and make sure  its contents are resume=UUID=41e86209-3802-424b-9a9d-d7683142dab7 (with  your UUID of course in place of mine). Save the file!
[*]sudo update-initramfs -u
[*]Reboot!
[/LIST]
Now you should be able to hibernate and resume! 			 		

now system says something like "failed to thow: -error 19" just before hibernating but it can wake up anyway. it seems ok for now. on the other hand, when i try to start zram-config in terminal, it gives this error message:

>  start: Rejected send message, 1 matched rules; type="method_call", sender=":1.89" (uid=1001 pid=4087 comm="start zram-config ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init") 

i'm not sure it's a problem or not :)

---

### Post by Toz on 2013-02-20
> now system says something like "failed to thow: -error 19" just before hibernating but it can wake up anyway. it seems ok for now. on the other hand, when i try to start zram-config in terminal, it gives this error message:

Can you post back again /var/log/pm-suspend.log?
```
pastebinit /var/log/pm-suspend.log
```

---

### Post by cifadam on 2013-02-20
finally, i'm not sure if it's okay to ask here, but, booting my laptop lasts exactly 45 seconds, from power button to login screen. then it takes another 20 seconds after login screen. is it normal for a new system, it seems a bit long for me.

EDIT: i haven't seen your last post, sorry. this is the new log file: [http://paste.ubuntu.com/1691744/](http://paste.ubuntu.com/1691744/)

---

### Post by Toz on 2013-02-20
> this is the new log file: [http://paste.ubuntu.com/1691744/](http://paste.ubuntu.com/1691744/)
There is nothing in this log file about an "error 19". Can you check your syslog:
```
cat /var/log/syslog | grep -i error | grep 19
```

> finally, i'm not sure if it's okay to ask here, but, booting my laptop lasts exactly 45 seconds, from power button to login screen. then it takes another 20 seconds after login screen. is it normal for a new system, it seems a bit long for me.

Perhaps its best to create a new thread for this issue so that this thread doesn't get confusing. When creating your new thread, post the contents of your dmesg boot log (each entry is time-stamped):
```
pastebinit /var/log/dmesg
```

---

### Post by cifadam on 2013-02-20
> cat /var/log/syslog | grep -i error | grep 19

here is the output: [http://paste.ubuntu.com/1693080/](http://paste.ubuntu.com/1693080/)

---

### Post by Toz on 2013-02-20
> **cifadam said:**
> here is the output: [http://paste.ubuntu.com/1693080/](http://paste.ubuntu.com/1693080/)

Okay, it in there, unfortunately it doesn't really help pinpoint the problem device/process. 

Just to confirm, hibernate is working now, correct?

If you want to troubleshoot this further, we'll need a more detailed debug log. Follow these procedures:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-hibernate

```
...and after you return from hibernation, post back the detailed log file:
```
pastebinit /var/log/pm-suspend.log
```

As well as your complete syslog:
```
pastebinit /var/log/syslog
```

And your device listing:
```
lspci
```

---

### Post by cifadam on 2013-02-21
solving this problem completely, without any error messages, might help somebody else; but actually i don't want to steal your time any more. hibernate is now working somehow. boot, hibernate, wake up from hibernate, these are all very slow for this hardware; but it's okay for now. i'll probably get a amd64 xubuntu iso and make a clean install, as soon as i find a fast internet connection. thank you very much for your help.

---

