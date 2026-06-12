---
title: "Ubuntu Installer For Windows"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by Unknown Fella on 2012-06-12
Hello guys! I have a few noob questions about Ubuntu installed as a Windows program.

It has it's independient hard disk space (like if it was a partition, but it's not) reserved inside the Windows partition, as far as I have tried, there's no way to access to the whole hard drive when using Ubuntu (you can access the Ubuntu space only); also from Windows you can't access the data stored in Ubuntu.

I don't know if that's meant to be that way or just I have not found the way to do it. So that's my question, Is there a way to transfer data between both without using any external memory device?

If that's true, Can a security threat inside Ubuntu act over Windows once you switch?

Thank you for your time and answers (if I get any XD), I'm sorry if my english is confusing to someone, it's not my native language.

---

### Post by steviejay on 2012-06-12
> **Unknown Fella said:**
> Hello guys! I have a few noob questions about Ubuntu installed as a Windows program.

It has it's independient hard disk space (like if it was a partition, but it's not) reserved inside the Windows partition, as far as I have tried, there's no way to access to the whole hard drive when using Ubuntu (you can access the Ubuntu space only); also from Windows you can't access the data stored in Ubuntu.



When you say Ubuntu installed as a Windows program I assume you mean installing Ubuntu using '**wubi**'.

If that is the case and If memory serves me right, if you browse through the folders in the Ubuntu file system you will find a folder named '**host**'. All of the Windows OS files, including personal files* (documents, pictures, music etc.)* can be accessed there. In the case of personal files from ~host/Users/[I]profile name
[/I]
I'm not 100% sure but I don't think you can access the  Ubuntu files from within Windows.

---

### Post by wilee-nilee on 2012-06-12
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

See #13 and #14

---

### Post by Mark Phelps on 2012-06-13
> **Unknown Fella said:**
> Hello guys! I have a few noob questions about Ubuntu installed as a Windows program.

It has it's independient hard disk space (like if it was a partition, but it's not) reserved inside the Windows partition, as far as I have tried, there's no way to access to the whole hard drive when using Ubuntu (you can access the Ubuntu space only); also from Windows you can't access the data stored in Ubuntu.
As mentioned, in Wubi installs, the Windows part of the partition is mounted under /host in the filesystem.

> So that's my question, Is there a way to transfer data between both without using any external memory device?
While you CAN write to the Windows filesystem from inside Ubuntu, it's generally a BAD idea to do that, especially if your Windows version is Vista or Win7.  Those are very sensitive to file system changes made to their OS partitions from outside (i.e., from Ubuntu).  Making such changes risks corrupting the Windows filesystem and rendering Windows unbootable.

You can't write to the Ubuntu filesystem from inside Windows.  IT doesn't recognize non-Windows filesystems.

> If that's true, Can a security threat inside Ubuntu act over Windows once you switch?
IF you download infected software from inside Ubuntu, that won't affect Ubuntu because Linux viruses are very rare.  But, if you access that infected software when back in Windows, you can then infect Windows as a result.

---

