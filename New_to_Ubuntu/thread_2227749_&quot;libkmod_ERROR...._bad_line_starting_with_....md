---
title: "&quot;libkmod: ERROR.... bad line starting with .....&quot; on start-up issue"
date: 2014-06-03
forum: New to Ubuntu
---

### Post by Duncubuntu on 2014-06-03
Hello!

I am hoping there is someone who can help me out here.

After upgrading from 13.10 to 14.04 making sure everything was updated, and newest drivers were in use etc etc etc, I came across the following error:

libkmod: ERROR ../libkmod/libmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'snd-hda-intel'

I have been able to find some information online regarding this, but nothing too specific.

alsa-base.conf has no line that either starts with  'snd-hda-intel' or contains it, furthermore my alsa-base.conf is only 43 lines.

[http://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt](http://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt) <- this is almost identical to my error, however like I mentioned, that line doesn't exist!

If anyone could point me in the right direction, it would be greatly appreciated!
If you need more information to help, let me know!

I'm running an Asus N550J Notebook.

Thanks,
  Duncan

---

### Post by Ryououki on 2015-01-27
> **Duncubuntu said:**
> Hello!

I am hoping there is someone who can help me out here.

After upgrading from 13.10 to 14.04 making sure everything was updated, and newest drivers were in use etc etc etc, I came across the following error:

libkmod: ERROR ../libkmod/libmod-config.c:686 kmod_config_parse: /etc/modprobe.d/alsa-base.conf line 45: ignoring bad line starting with 'snd-hda-intel'

I have been able to find some information online regarding this, but nothing too specific.

alsa-base.conf has no line that either starts with  'snd-hda-intel' or contains it, furthermore my alsa-base.conf is only 43 lines.

[http://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt](http://askubuntu.com/questions/290884/blacklist-conf-ignoring-bad-line-boot-prompt) <- this is almost identical to my error, however like I mentioned, that line doesn't exist!

If anyone could point me in the right direction, it would be greatly appreciated!
If you need more information to help, let me know!

I'm running an Asus N550J Notebook.

Thanks,
  Duncan

I know this is old, but did you ever get it fixed?  I initially had the same issue as you and it continued on even after several reboots, but I ran the command 'sudo update-initramfs -k all -c' and after that, the problem is cleared up.

---

