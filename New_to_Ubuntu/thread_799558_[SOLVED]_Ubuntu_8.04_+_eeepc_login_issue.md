---
title: "[SOLVED] Ubuntu 8.04 + eeepc login issue"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by mjwhitfield on 2008-05-19
Hello chaps,

I need help debugging an issue.  I ran the LiveCD os 8.04 on my eeepc last night, which worked fine.

I've found a script here:
[http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly](http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly)

Which will fix the wireless, suspend, osd etc...

Anyhow, I've done the install, and rebooted as which point I've hit a brick wall.

The steps are thus:
1. I get to the login screen (GDM)
2. type in my username
3. type in my password
4. screen goes brown (as it would when GNOME is about to kick in)
5. at this point, it just sits there and doesn't progress

I can't tell if it's doing anything, as ubuntu is installed to the SD card, and not the SSD, so there is no access light.

Can anyone start me off with ideas about how I might start the debugging process to find out what is wrong?

Thanks,
MJ

---

### Post by EXCiD3 on 2008-05-20
On the login menu try changing the Session to something other than what it defaults to. It could be something that is trying to run automatically when you login.

---

### Post by mjwhitfield on 2008-05-20
It's something to do with the GNOME keyring, I have found a solution here:
[http://forum.eeeuser.com/viewtopic.php?id=25872](http://forum.eeeuser.com/viewtopic.php?id=25872)

The fix is thus - 

Nano and create a new file here:
```
sudo nano /etc/hal/fdi/policy/removable_root_fix.fdi
```

Paste this in:
```
<?xml version="1.0" encoding="ISO-8859-1"?> <!-- -*- SGML -*- --> 
<deviceinfo version="0.2">

  <device>
    <match key="volume.mount_point" string="/">    
    <merge key="@block.storage_device:storage.removable" type="bool">false</merge>
    </match>
  </device>

</deviceinfo>
```

Restart hal:
```
$ sudo invoke-rc.d hal restart
```

There's a bug listed in launchpad here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434)

---

