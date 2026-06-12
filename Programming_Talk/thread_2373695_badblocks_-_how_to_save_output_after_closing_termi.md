---
title: "badblocks - how to save output after closing terminal?"
date: 2017-10-09
forum: Programming Talk
---

### Post by madumi on 2017-10-09
I'm a little stuck here. I am running badblocks, but due to the time-frame of each test (36 hours), I tend to close the terminal.

How can I save the output? I've had little success & tried these commands:

```
sudo badblocks -nv -o /home/USER/badblocks.txt /dev/sda
```
```
sudo badblocks -nv /dev/sda > /home/USER/badblocks.txt
```
```
sudo badblocks -nv /dev/sda &> /home/USER/badblocks.txt
```

Each of these commands results in the creation of a badblocks.txt file at the commencement of the process, but at completion, the file remains empty. I'd like at least to see the output of the read/write/corruption errors, even if it's "0"

Any suggestions?

---

### Post by sudodus on 2017-10-09
One way to save the badblock information is via e2fsck.

From ```
man e2fsck
```

```
       -c     This  option  causes  e2fsck  to  use badblocks(8) program to do a read-only scan of the
              device in order to find any bad blocks.  If any bad blocks are found, they are added  to
              the  bad  block  inode  to prevent them from being allocated to a file or directory.  If
              this option is specified twice, then the bad block  scan  will  be  done  using  a  non-
              destructive read-write test.
```

I use the following command (when booted from another drive and after unmounting the partition to be checked)

```

sudo e2fsck -cf /dev/sdxn

```

where x is the device letter and n is the partition number.

---

### Post by SeijiSensei on 2017-10-09
It might be writing to SYSERR rather than STDOUT.  Try adding "2>&1" to the end of the command.  You should also be running this in the background if you close the terminal. Add an ampersand to the end of the command to put the job in the background.

---

### Post by madumi on 2017-10-09
Thanks so much for replies

@sudodus
Sadly e2fsck won't take -n or -y (non-interactive modes) when using -c... & I need it to run outside of the terminal... Is there another way to accomplish this?

@SeijiSensei
I think 2>&1 does the same thing as using &> for writing output (conflates SYSERR & STDOUT) & for some reason, this still results in an empty badblocks.txt file at the end...

Any other suggestions?

---

### Post by SeijiSensei on 2017-10-09
If you run badblocks without redirecting the output, does it appear on the screen?

---

### Post by sudodus on 2017-10-09
> **madumi said:**
> Thanks so much for replies

@sudodus
Sadly e2fsck won't take -n or -y (non-interactive modes) when using -c... & I need it to run outside of the terminal... Is there another way to accomplish this?


I don't know.

---

### Post by madumi on 2017-10-11
> **SeijiSensei said:**
> If you run badblocks without redirecting the output, does it appear on the screen?

Yup, if I run badblocks in the terminal without closing, it displays the progress & output correctly (on the screen)... Not sure what else I should be doing...

---

