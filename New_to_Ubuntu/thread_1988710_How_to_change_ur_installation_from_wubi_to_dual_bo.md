---
title: "How to change ur installation from wubi to dual boot ( live cd or usb )"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by Ragy94 on 2012-05-28
I've installed my ubuntu 12.04 using wubi next to my windows 7 64bit and then i experienced some problems ( hibernate , slow process and so on ) so now i want to reinstall ubuntu using live cd or usb but without losing my applications , data or settings .. but I'm not an advanced user so plz if anyone would help me :) just use a simple method with steps :) ! sorry for my bad english

---

### Post by MG&amp;TL on 2012-05-28
There are methods, such as this one: [https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi") but as you're not an advanced user, I suggest you make a list of your applications, backup (and check your backup!) your entire home directory (go up one level, there are hidden files in your home directory, they're settings), then uninstall wubi.

Install Ubuntu properly, then copy your files back across, then spend some time with the software centre installing your apps again.

---

### Post by Ragy94 on 2012-05-28
So could u tell me how to backup my settings and my home directory ??? using which app. or what :) thank u for ur reply

---

### Post by Ragy94 on 2012-05-28
I've found the backup application .. should i backup the home folder to ubuntu one or to a drive ?

---

### Post by mlentink on 2012-05-28
Doesn't really matter. USB-drive is probably a bit faster, depending on your internet connection.
Make sure to include all hidden files in your homedir (all files that start with a '.', only visible in the file manager after you selected 'show hidden files')

---

### Post by Ragy94 on 2012-05-28
:) Thank u .. just to make sure .. so now i show the hidden files in the home folder . then copy all to a usb ... then uninstall wubi ( from windows ) than install the live cd stuff .. and then after installing it . i paste the home folder and replace everything .. that's it ha ?

---

### Post by mlentink on 2012-05-28
Yes, that's about it. 
You might want to read the topics on dual boot first: [https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

---

### Post by Ragy94 on 2012-05-28
Thank u :)

---

### Post by MG&amp;TL on 2012-05-28
Just for future notice, 'backup' means 'copy'. So no app is really needed, the file manager is probably enough.

---

### Post by bcbc on 2012-05-28
> **MG&TL said:**
> There are methods, such as this one: [https://help.ubuntu.com/community/MigrateWubi]("https://help.ubuntu.com/community/MigrateWubi") but as you're not an advanced user, I suggest you make a list of your applications, backup (and check your backup!) your entire home directory (go up one level, there are hidden files in your home directory, they're settings), then uninstall wubi.

Install Ubuntu properly, then copy your files back across, then spend some time with the software centre installing your apps again.

I'm not sure why you think this is only for advanced users. The only thing you need to do is to create partitions and run a script. Or are you suggesting that creating partitions is only for advanced users and instead the ubuntu installer should be only used for that? :confused:

---

### Post by bcbc on 2012-05-28
> **Ragy94 said:**
> So could u tell me how to backup my settings and my home directory ??? using which app. or what :) thank u for ur reply

There are some instructions here to do it manually: [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

There are under the section: [COLOR="Red"]Alternative instructions[/COLOR] in the first post (don't use LVPM)

---

### Post by MG&amp;TL on 2012-05-29
> **bcbc said:**
> I'm not sure why you think this is only for advanced users. The only thing you need to do is to create partitions and run a script. Or are you suggesting that creating partitions is only for advanced users and instead the ubuntu installer should be only used for that? :confused:

You would appear to be the author-well done, it's really good. :)

With respect, the "only thing" turns out to be quite a few if you break them down. Also with respect, your script hasn't been tested as well as ubiquity has, so I didn't recommend it to the OP in case of the horror of "grub>" on boot. Yes, actually, partitions is not something I would mess with unless I knew what I was doing, and that constitutes 'advanced user'.

No misinformation or disrespect intended, just IMO it's not entirely foolproof and I hate  to tell people their data is gone.

---

### Post by bcbc on 2012-05-29
> **MG&TL said:**
> You would appear to be the author-well done, it's really good. :)

With respect, the "only thing" turns out to be quite a few if you break them down. Also with respect, your script hasn't been tested as well as ubiquity has, so I didn't recommend it to the OP in case of the horror of "grub>" on boot. Yes, actually, partitions is not something I would mess with unless I knew what I was doing, and that constitutes 'advanced user'.

No misinformation or disrespect intended, just IMO it's not entirely foolproof and I hate  to tell people their data is gone.
I don't think it's valid to compare the migration script to ubiquity. Ubiquity is an immensely complex application, reflected by the incredible number of bugs it has ([2299 open at this time]("https://bugs.launchpad.net/ubuntu/+source/ubiquity")).

Partitioning manually or letting ubiquity do it automatically carries at least the same risk and any user (advanced or not) would do well to understand these risks and backup beforehand. [Without trying to vilify ubiquity], it should be stated that it can damage Windows (Windows 7/vista can shrink their own partition more safely) and there have been cases of [ubiquity overwriting windows]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950") in the not to distant past. That's why I'd generally recommend manual partitioning anyway.

Compared to Ubiquity, the migration script is incredibly simple:
1. does a ridiculous amount of error checking
2. copies files
3. does some minor edits and then chroot's to update grub
4. optionally installs the grub bootloader (preferred option, but not mandatory)

But... you are absolutely entitled to share your opinion. I hope you don't mind if I chime in with my opinion as well.

---

### Post by MG&amp;TL on 2012-05-29
> **bcbc said:**
> I don't think it's valid to compare the migration script to ubiquity. Ubiquity is an immensely complex application, reflected by the incredible number of bugs it has ([2299 open at this time]("https://bugs.launchpad.net/ubuntu/+source/ubiquity")).

Partitioning manually or letting ubiquity do it automatically carries at least the same risk and any user (advanced or not) would do well to understand these risks and backup beforehand. [Without trying to vilify ubiquity], it should be stated that it can damage Windows (Windows 7/vista can shrink their own partition more safely) and there have been cases of [ubiquity overwriting windows]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950") in the not to distant past. That's why I'd generally recommend manual partitioning anyway.

Compared to Ubiquity, the migration script is incredibly simple:
1. does a ridiculous amount of error checking
2. copies files
3. does some minor edits and then chroot's to update grub
4. optionally installs the grub bootloader (preferred option, but not mandatory)

But... you are absolutely entitled to share your opinion. I hope you don't mind if I chime in with my opinion as well.

...you've convinced me. ;) Won't be making that point in future.

Of course not, everyone is entitled to their opinion.

---

