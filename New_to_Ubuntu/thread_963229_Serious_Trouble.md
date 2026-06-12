---
title: "Serious Trouble"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Wraithing on 2008-10-30
Hi All,

I am currently unable to boot Ubuntu normally, though Windows works fine. I tried use the Live CD to backup my important files so that I can just reformat, but the system tells me that I don't have the permissions necessary to view the contents of the folder my files are in (it's a sub-folder in Documents). There's an "Unreadable" emblem on the folder I can't access. 

I noticed that my boot folder is completely empty, which might explain why I keep getting Error 15: File not found, when I try to boot normally.

Is there anything I can do to save my files? I'm a grad student and I have parts of my thesis saved in the folder I can't access. I'd really like to avoid losing it if I can.

Thanks in advance.

---

### Post by jamesrl on 2008-10-30
If its you just don't have permissions to read the directories, you can go launch nautilus as root.
Simply type:

```

gksudo nautilus
```

---

### Post by jamesrl on 2008-10-30
Also look at this for how to restore GRUB from a Live CD.
[http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD](http://ubuntuguide.org/wiki/Ubuntu:Hardy#How_to_restore_GRUB_to_a_partition_or_MBR_with_an_Ubuntu_Live_CD)

However, as a fellow grad student, i'd try and backup the important folders first.

---

### Post by bumanie on 2008-10-30
[Go here]("http://users.bigpond.net.au/hermanzone/p15.htm") to look at grub 15 errors and possible cures. Scroll about two thirds down the page to get to the grub error section.

---

