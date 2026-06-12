---
title: "Windows boot problem..."
date: 2012-01-21
forum: New to Ubuntu
---

### Post by Btdbilly on 2012-01-21
[U][COLOR="PaleTurquoise"]I have two partitions on my laptop, C and D I wanted to dualboot my existing Windows7 with Ubundu, however I accidently instaled Ubundu on the D partition istead of C causing it to be slow and despite that I cannot find Windows on the boot loader.

   As if that wasent enough I can't find the C drive either... Not at all, as if it never existed
  I could do a full wipe (format) and reinstal Windows and Ubundu but I dont want to lose the files I have in C they are really important to me :/

   What can I do to get my files from the C drive or (I would prefer this) get windows to boot? Any help apreciated.

 Thanks in advance :) .
[/COLOR][/U]



:EDIT: **[COLOR="Red"]Ignore the above[/COLOR]**

   I made a mistake I instaled ubundu on the C drive normally an found the Windows 7 directory (under Host in system) with the files but still cant boot Windows7...But I am sure this has been resolved in the forums so I will just search for it :)

---

### Post by GMachine_24 on 2012-01-21
Well, this is just part of the basics to check out but try update Grub or Grub2, as in:

```


#sudo update-grub

or

#sudo update-grub2


```

of course without the '#'

---

