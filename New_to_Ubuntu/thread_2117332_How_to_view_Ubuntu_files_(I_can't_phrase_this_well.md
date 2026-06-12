---
title: "How to view Ubuntu files (I can't phrase this well)"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by savagecube on 2013-02-18
I had a computer with windows/ubuntu dual boot. I have the hard disk taken out, and have some connector thing which allows it to be plugged into a usb port. 
I plug it into my other computer which is only running windows 7. 
2 things come up. One is 400gb, which has my windows files. The other is 100gb, and is called System Reserved. It has about 80gb used, but inside I don't see any files. 
I'm wondering where the Ubuntu stuff is stored, and how do I view it?
 
Thanks for looking! :)

---

### Post by PowerBarry43 on 2013-02-18
Hi

Windows can only see other Windows partitions that are formatted in NTFS like the Windows 7 install on your hard drive will be. Ubuntu generally uses ext3 or ext4. Windows doesn't have a driver to read this filesystem so that would explain why you can't see it from Windows. To get round this you could do one of two things. Either boot from an Ubuntu liveCD on your computer which your USB hard drive connected and from there you will be able to see all partitions on both hard drives, or failing that there is a driver on sourceforge that allows Windows to read ext partitions although I wouldn't mess with this if you don't have to!

Hope this helps!

Barry

---

### Post by schragge on 2013-02-18
For Windows drivers, see
[list]
[*][http://www.ext2fsd.com/?page_id=2](http://www.ext2fsd.com/?page_id=2)
[*][http://www.fs-driver.org/](http://www.fs-driver.org/) (only ext2 and partially ext3), [how-to](http://robertbeal.com/528/mount-ext3-in-windows-7-x64)
[*][http://sourceforge.net/projects/ext2read](http://sourceforge.net/projects/ext2read) (read-only)
[*][http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/) (read-only)
[/list]

---

### Post by offgridguy on 2013-02-18
> **powerbarry43 said:**
> hi

windows can only see other windows partitions that are formatted in ntfs like the windows 7 install on your hard drive will be. Ubuntu generally uses ext3 or ext4. Windows doesn't have a driver to read this filesystem so that would explain why you can't see it from windows. To get round this you could do one of two things. Either boot from an ubuntu livecd on your computer which your usb hard drive connected and from there you will be able to see all partitions on both hard drives, or failing that there is a driver on sourceforge that allows windows to read ext partitions although i wouldn't mess with this if you don't have to!

Hope this helps!

Barry
+1

---

### Post by Mark Phelps on 2013-02-18
> **savagecube said:**
> 2 things come up. One is 400gb, which has my windows files. The other is 100gb, and is called System Reserved. It has about 80gb used, but inside I don't see any files. 
The System Reserved is your Win7 boot partition -- it only has boot loader files in it, so there is nothing in there you need.
> I'm wondering where the Ubuntu stuff is stored, and how do I view it?
I'm presuming you're talking about the Win7 Disk Management utility, right? It will SEE the other Linux filesystem partitions, it just won't be able to see inside them.  So, you should see those partitions in the tool panel.

IF you do NOT see those partitions, and instead, your entire drive is NTFS partitions, that means Ubuntu is actually INSIDE a Windows partition -- and in that case, you would have to be boot into Ubuntu to see those files.

---

### Post by savagecube on 2013-02-18
> **PowerBarry43 said:**
> Hi

Windows can only see other Windows partitions that are formatted in NTFS like the Windows 7 install on your hard drive will be. Ubuntu generally uses ext3 or ext4. Windows doesn't have a driver to read this filesystem so that would explain why you can't see it from Windows. To get round this you could do one of two things. Either boot from an Ubuntu liveCD on your computer which your USB hard drive connected and from there you will be able to see all partitions on both hard drives, or failing that there is a driver on sourceforge that allows Windows to read ext partitions although I wouldn't mess with this if you don't have to!

Hope this helps!

Barry

I didn't think it would be this simple. Thanks

---

