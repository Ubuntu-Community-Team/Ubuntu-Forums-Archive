---
title: "what if I have two ubuntus?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jeff Odom on 2008-09-23
I accidently download ubuntu twice thinking I made a mistake, so I need to know how to delete one of them.

---

### Post by digitzero on 2008-09-23
If you downloaded it to your computer, just delete the duplicate file.

Did you end up installing it twice?

---

### Post by jemate18 on 2008-09-23
> **jeff Odom said:**
> I accidently download ubuntu twice thinking I made a mistake, so I need to know how to delete one of them.

You mean you have donwloaded two ISO of Ubuntu from the website?

---

### Post by Crafty Kisses on 2008-09-23
Are you talking about two partitions?

---

### Post by Murrquan on 2008-09-23
I am assuming that you downloaded the .iso for Ubuntu 8.04 via the "Get Ubuntu" page on ubuntu.com, and that you downloaded a duplicate copy.

Check to see where your web browser is putting your downloads. Then look for the files that you downloaded, and delete one of them. To identify the files, look for the following:

[LIST]
[*]**Name**: They should both say "Ubuntu" something-or-other, and if you can check your download history you can see what the exact names were.
[*]**Size**: They should be very large files, about 700 MB if you downloaded the normal version.
[*]**Extension**: Your computer should say that they are ISO files.
[/LIST]

If one of the files is about 700 MB and another is smaller, it's because you canceled the download on the smaller one. Delete it, and not the larger file.

Let us know if this doesn't help!

---

### Post by kansasnoob on 2008-09-23
Please go to Terminal and post the output of:

```
sudo fdisk -l
``` 

BTW, that's a lower case L at the end!

---

