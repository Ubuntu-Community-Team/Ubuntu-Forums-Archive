---
title: "[SOLVED] No support for tar.gz in fresh hardy install?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by tstack77 on 2008-05-31
I just downloaded GFX Boot and cannot open the tar.gz package. When I try to open it I get "Archive type not supported".

What do I do?

---

### Post by bumanie on 2008-05-31
> sudo apt-get install build-essential Then right click on thd file and choose extract here to extract it. Open the extracted file and there will be a text file telling you how to compile the file.

---

### Post by jrusso2 on 2008-05-31
What are you trying to open it with. There should be support?  You could always use the command line tar -xzf filename

---

### Post by p_quarles on 2008-05-31
Tar and gzip (the applications that manipulate "tar.gz" files) are both core utilities in the GNU system. No normal version of Linux would ever ship without them. 

My guess is that the file you downloaded is corrupt.

---

### Post by tstack77 on 2008-05-31
> **bumanie said:**
> Then right click on thd file and choose extract here to extract it. Open the extracted file and there will be a text file telling you how to compile the file.

That didn't work, same problem. This is so strange.

I don't know the exact command line syntax here to use the terminal. More info if you could. The package is on my desktop so it would be, home/stack/Desktop/ tar -xzf GFX??? (that doesn't do it)

EDIT: I downloaded the file from [HERE]("http://www.mediafire.com/?02wjst9fkdy"). Tried downloading it 3 different times with the same result.

---

### Post by p_quarles on 2008-05-31
That file works fine for me. To open it via the command line, you'll need to enter the directory in which it downloaded (using the "cd" command") and then run this:
```
tar -zxf GXF\ Grub.tar.gz
```
You will now have a new directory named "GFX Grub."

---

### Post by tstack77 on 2008-05-31
> **p_quarles said:**
> That file works fine for me. To open it via the command line, you'll need to enter the directory in which it downloaded (using the "cd" command") and then run this:
```
tar -zxf GXF\ Grub.tar.gz
```
You will now have a new directory named "GFX Grub."

I moved it into grub folder using gksudo nautilus. Tried the above and got:

xxxxx@xxxxx:~$ cd /boot/grub
xxxxx@xxxxx:/boot/grub$ tar -zxf GXF\ Grub.tar.gz
tar: GXF Grub.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

---

### Post by p_quarles on 2008-05-31
Sorry, typo. "GFX" not "GXF."

Also, since the file is in a protected directory, you'll need to use sudo with that command.

---

### Post by SeanHodges on 2008-05-31
I don't think you'll have permissions to extract straight to /boot/grub...

Do it in /home/xxxxx first

cd /home/xxxxx
tar -zxf GFX\ Grub.tar.gz

If that doesn't work then try downloading the file again, it could be corrupted during the last transfer.

---

### Post by tstack77 on 2008-05-31
> **p_quarles said:**
> Sorry, typo. "GFX" not "GXF."

Also, since the file is in a protected directory, you'll need to use sudo with that command.

xxxxx@xxxxx:/boot/grub$ sudo tar -zxf GFX\ Grub.tar.gz
tar: GFX Grub.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
xxxxx@xxxxx:/boot/grub$

Tried doing the same with the file in /home:

xxxxx@xxxxx:~/Desktop$ cd /home/xxxxx
xxxxx@xxxxx:~$ tar -zxf GFX\ Grub.tar.gz
tar: GFX Grub.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Downloading again for the fourth time does nothing either???

EDIT: I followed the instructions [HERE]("http://www.joejoe.org/forum/index.php?showtopic=13873") so I already have removed GRUB. Can't think of why this might be the cause but I have no other ideas?

---

### Post by ChameleonDave on 2008-05-31
> **tstack77 said:**
> I moved it into grub folder using gksudo nautilus. Tried the above and got:

xxxxx@xxxxx:~$ cd /boot/grub
xxxxx@xxxxx:/boot/grub$ tar -zxf GXF\ Grub.tar.gz
tar: GXF Grub.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

It says the file is not there.  Is it really not there?

Type "tar -zxf " and then hit Tab for autocompletion. It will give you a list of what is in the directory.  As you start the type the first few letters of what you want, you will be able to narrow it down.  In fact, if you type a capital G and then hit Tab, it will probably fill in the whole filename for you, if the file is really there.

You will also need to put "sudo" before the command, because you are in a system directory.

If you know so little about the command line, why are you messing with the internals of the system anyway?

---

### Post by p_quarles on 2008-05-31
What does this say?
```
ls /boot/grub
```

---

### Post by ChameleonDave on 2008-05-31
OK, I've just downloaded the file myself to see.

I've ended up with an uncompressed tar archive called "GFX" with no extension.

Stop downloading it again and again.  Just leave it on your desktop.

Type this:

```
cd ~/Desktop
tar -xf GFX
ls GFX\ Grub
```

---

### Post by tstack77 on 2008-05-31
> **p_quarles said:**
> What does this say?
```
ls /boot/grub
```

xxxxx@xxxxx:~$ ls /boot/grub
default        fat_stage1_5       jfs_stage1_5  minix_stage1_5     stage2
device.map     GFX                menu.lst      reiserfs_stage1_5  xfs_stage1_5
e2fs_stage1_5  installed-version  menu.lst~     stage1

When I hit tab all I get is a system beep. BUT I am looking at the file!

---

### Post by tstack77 on 2008-05-31
> **ChameleonDave said:**
> OK, I've just downloaded the file myself to see.

I've ended up with a gzipped tar archive called "GFX" with no extension.

Stop downloading it again and again.  Just leave it on your desktop.

Type this:

```
cd ~/Desktop
tar -zxf GFX
```

that worked...:-s

The cause? No tar.gz extension?

EDIT: Yup! Thanks for the help guys! Sorry for the run-around.

---

### Post by p_quarles on 2008-05-31
> **tstack77 said:**
> that worked...:-s

The cause? No tar.gz extension?
Something to do with the scripting on the server hosting the file, I think. It may be buggy, since it's apparently putting differently named files on different computers.

---

### Post by lswest on 2008-05-31
the filename you were using was wrong.  It was called "GFX" and not "GFX Grub.tar.gz".  Might be that the server has multiple mirrors you can download it from that it chooses from automatically, and that the package may be named differently on each one.

---

