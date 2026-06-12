---
title: "Menu.lst file"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by frimilden on 2008-05-08
Someone on another forum I frequent is asking for someone to help him out with a menu.lst file

> please upload for me a menu.lst of ubuntu 8.04, i have wracked mine and now i can`t boot ubuntu anymore. thanks


My question is it safe to give this person this file? I mean does it contain anything in it that should not be giving out like a password or anything like that?

---

### Post by tamoneya on 2008-05-08
there are no passwords in the menu.lst.  If you have a grub password there will be the md5sum of your password but this isnt sensitive as it is encrypted.  The only other information that can be seen is a little bit of stuff about what operating systems are on which disks.

---

### Post by celticbhoy on 2008-05-08
It does not contain any passwords or anything like it.
But the chances of his setup being the same as yours are remots, It might help him if he has corrupted his and knows his setup though

---

### Post by frimilden on 2008-05-08
> **tamoneya said:**
> there are no passwords in the menu.lst.  If you have a grub password there will be the md5sum of your password but this isnt sensitive as it is encrypted.  The only other information that can be seen is a little bit of stuff about what operating systems are on which disks.

Thank you very much for your swift reply, it is appreciated. :popcorn:

---

### Post by frimilden on 2008-05-08
> **celticbhoy said:**
> It does not contain any passwords or anything like it.
But the chances of his setup being the same as yours are remots, It might help him if he has corrupted his and knows his setup though

Thank you too for your swift reply. I will give him the file then and maybe it will help him out. We shall see :popcorn:

---

### Post by tamoneya on 2008-05-08
have him post his current menu.lst and the result of```
sudo fdisk -l
``` here or in a different thread and we will get it all fixed up quickly as usual.

---

### Post by kansasnoob on 2008-05-08
I always "edit" the beginning of such files.

Like if my file begins with: kansasnoob@kansasnoob , I just change it to nebraskaboob@nebraskaboob or anything really.

If your password is present (it won't be if you've "sudoed" anything since you last used the terminal) just replace it with ***********.

I've never had anyone hack me from the Ubuntu forums! If I did I'd post about it and I'm sure they'd be blocked till the end of time!

You should be able to find the help you need with the GRUB menu right here.

I've received help here with GRUB a lot of times!

---

### Post by wootah on 2008-05-08
If you do have a password listed, it wouldn't hurt to just snip it out. The default setup from Ubuntu gives the reader a good sense of what is required.

ex:
<snipped>
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret
<snipped>

With all the comments, it should be some what reasonable to reconstruct the menu.lst. You just need to know what the partitions are.

---

### Post by frimilden on 2008-05-08
Thank you all for the help. I have directed him to this forum for any help he may need...You guys are great and this forum rocks :popcorn:

---

