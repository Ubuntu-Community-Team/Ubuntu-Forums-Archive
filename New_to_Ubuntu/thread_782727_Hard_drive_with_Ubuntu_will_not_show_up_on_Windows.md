---
title: "Hard drive with Ubuntu will not show up on Windows My Computer"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by giordun on 2008-05-05
Hi guys. I currently have 2 hard drives installed onto my computer. Hard drive A is the one I have been using for a while and it has Windows installed on it. Hard drive B I just bought recently to use because I was running low on space. It worked fine.

Recently I decided to install Ubuntu and since Hard Drive A was low on space I decided to install it onto Hard Drive B. It works fine. On Ubuntu I can access both hard drives no problem.

But when I switch back to Windows, I can only access Hard Drive A. I went to Device manager and it can detect hard drive B and it says it is fine.

The problem is hard drive B won't show up on My Computer...

So I did a quick Yahoo Answers and the problem seems to be that Windows will not read the drive because it's Ubuntu.

How the hell do I get it to work?

---

### Post by hyper_ch on 2008-05-05
Windows does not support other filesystems than its own. As Ubuntu by default uses ext3, windows can't read it.

---

### Post by philinux on 2008-05-05
It's because windoze cant natively read ext3. There is a way though. What version of windoze are you running

---

### Post by Joeb454 on 2008-05-05
It won't show up - because Ubuntu (and linux as a whole) _typically_ uses Ext2 or Ext3 as a file system, which is not readable by Windows, though some users may choose a different filesystem.

However a quick google search should give you a driver to allow you to read the drive from Windows :)

Found the link -> [fs-driver.org]("http://www.fs-driver.org/")

---

### Post by billgoldberg on 2008-05-05
Windows can't read/access ext3 drives.

It's easily fixed by installing ext2 drivers on windows:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by aheckler on 2008-05-05
What filesystem is the second drive using? If it's using the regular Linux filesystem (ext3) then Windows won't be able to read it because it doesn't have native support for ext3.

You need [this]("http://www.fs-driver.org/index.html"), although I can't vouch for it's functionality, as I've never had to use it.

EDIT: Jeez, I was pretty slow on that one!

---

### Post by mlentink on 2008-05-05
So you may want to look at [http://www.fs-driver.org/](http://www.fs-driver.org/)

Edit: I really need to learn to type faster... ;-)

---

### Post by billgoldberg on 2008-05-05
> **Joeb454 said:**
> It won't show up - because Ubuntu (and linux as a whole) uses Ext2 or Ext3 as a file system, which is not readable by Windows.


The windows part is true, but stating ubuntu and linux as a whole uses ext2 or ext3 is not true.

For one, I'm running hardy heron on reiserfs instead of ext3.

---

### Post by Joeb454 on 2008-05-05
Ok I mean typically - the average Linux user will be running off an ext2 or ext3 formatted drive :) Though I am aware of others.

Edited my original post now :p

---

### Post by giordun on 2008-05-05
Ok I have gotten it to show up but it needs me to format the drive... So i'll like lose everything there right?

Damn Windows is pretty crap.

---

### Post by hyper_ch on 2008-05-05
no, it does not need to be formatted... in its current state windows just can't read it... as others have said, install the fs-driver and it works...

---

### Post by giordun on 2008-05-06
I installed the driver already. This time the drives show up but it requires me to format it to view it...

---

### Post by philinux on 2008-05-06
[http://www.fs-driver.org/troubleshoot.html](http://www.fs-driver.org/troubleshoot.html)

---

