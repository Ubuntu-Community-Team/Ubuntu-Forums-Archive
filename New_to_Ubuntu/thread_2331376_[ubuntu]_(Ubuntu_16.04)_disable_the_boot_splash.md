---
title: "[ubuntu] (Ubuntu 16.04) disable the boot splash"
date: 2016-07-21
forum: New to Ubuntu
---

### Post by urbi2 on 2016-07-21
How do I disable the boot splash screen, and only show kernel and boot text instead? first of all, Thanks :)

---

### Post by &amp;KyT$0P# on 2016-07-21
edit /etc/default/grub
remove 'quiet' and 'splash' from GRUB_CMDLINE_LINUX_DEFAULT line

so, assuming you have no other boot parameters, it would look like
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

save that, then run
```
sudo update-grub
```

reboot

---

### Post by urbi2 on 2016-07-21
> **halogen2 said:**
> edit /etc/default/grub
remove 'quiet' and 'splash' from GRUB_CMDLINE_LINUX_DEFAULT line

so, assuming you have no other boot parameters, it would look like
```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

save that, then run
```
sudo update-grub
```

reboot


thank you very much  :KS

---

### Post by &amp;KyT$0P# on 2016-07-21
You're welcome :D

---

### Post by paulbelcher2 on 2017-04-24
[h=1]I have Ubuntu 16.04.  I recently did an update and when I rebooted got this error.
[URL="https://askubuntu.com/questions/691729/piix4-smbus-0000007-3-host-smbus-controller-bus-not-enabled"]
Piix4_SMBus: 000:00:07.3: Host SMBus controller bus not enabled[/URL][/h][h=1]I tryed the following:
 1) I removed the "quite splash" in Grub
 2) add this line to the blacklist.conf file [blacklist i2c-piix4]

After added the piix4 to the blacklist, the error message no longer comes up but it still prompts me to enter maintenance mode.  

Please advise,
Thanks,
Paul[/h]

---

### Post by wildmanne39 on 2017-04-24
Please start your own thread so you can get the help you need.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

---

