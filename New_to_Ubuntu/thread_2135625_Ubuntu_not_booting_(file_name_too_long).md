---
title: "Ubuntu not booting (file name too long)"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by Arendyl on 2013-04-14
[FONT=arial][SIZE=3]I am attempting to load ubuntu, but during the process, it displays a black screen filled with diamonds ([COLOR=#000000]&#9830;), followed by a message stating "file name to long". It doesn't continue the boot, just stays on that screen. Any ideas how to fix this?
Also, grub appears now when it didnt before. Thanks in advance[/COLOR][/SIZE][/FONT]

---

### Post by Arendyl on 2013-04-20
ok, if i can't fix my boot, is there anyway to pull my files from my hdd onto an external drive via liveCD? I can see the files in my file browser, but it wont let me access them due to lack of permissions. any way around this?

---

### Post by dgharmon on 2013-04-20
> **Arendyl said:**
> ok, if i can't fix my boot, is there anyway to pull my files from my hdd onto an external drive via liveCD? I can see the files in my file browser, but it wont let me access them due to lack of permissions. any way around this?

When you boot from the liveCD open up a console and type sudo -i, you should then be able to access the files ...

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by oldfred on 2013-04-20
Grub knows if you have abnormal shutdown or boot errors and will show menu. Then you may be able to boot with recovery mode to make repairs, or get to command line.

Any idea what file is too long? Did you edit fstab, change language or do something where it is having issues. Or maybe it is just corruption, and from a liveCD you may need to run fsck?

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

