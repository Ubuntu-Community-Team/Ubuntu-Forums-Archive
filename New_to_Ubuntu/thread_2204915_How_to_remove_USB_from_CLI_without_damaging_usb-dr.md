---
title: "How to remove USB from CLI without damaging usb-drive"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Psil0cybin on 2014-02-11
If I use the command   ```
sudo umount /media/usbname
```   would that remove my usb stick via the terminal properly without damaging it? If not, what is the proper way of removing a USB media point from the CLI?  Thanks in advance.

---

### Post by Bucky Ball on 2014-02-11
Yes, that would unmount it and then it would be safe to remove. Any particular reason you are not simply right clicking on it in a file manager and 'Eject'?

---

### Post by slooksterpsv on 2014-02-11
If you know the device name you can umount it that way as well:

```

sudo umount /dev/sdb1

```

@Bucky - he asked how to do it via CLI - maybe Server? Trying to get install working? Graphics drivers? Various reasons possibly.

---

### Post by tfrue on 2014-02-11
Just to note, issuing the command:
```

mount
```
Will show you what is currently mounted to your system which would not be safe to remove, so after issuing the *sudo umount* command, you could run the *mount *command again and see that it has successfully been unmounted and safe to remove.

---

### Post by Psil0cybin on 2014-02-11
>                               [INDENT]                     Yes, that would unmount it and then it would be safe to remove. Any  particular reason you are not simply right clicking on it in a file  manager and 'Eject'?                 [/INDENT]
            
                         


Thank you for your fast reply. I am just interested in learning how to use the CLI more, as I really do prefer it, I think of it this way, Linux is like a stick shift car, so I like to go through the extra work in order to learn a few things about how the operating system functions, although If I am not mistaken umount is just a script for much bigger commands, that would be a pain to execute? Correct?

> @Bucky - he asked how to do it via CLI - maybe Server? Trying to get  install working? Graphics drivers? Various reasons possibly.

Nope, not server, just for education purposes - for learning how my linux desktop functions perhaps If I am already in the terminal to remove the USB (as I like to use nano to edit files)
hope I did not ask a silly question!

Thanks Ubuntu community!

---

### Post by sudodus on 2014-02-11
Welcome to running your computer 'like a stick shift car' :-)

When you have collected enough experience, you will be enjoy reading man and info pages. Sometimes there is more information in the corresponding info page.

[FONT=courier new]**man program**[/FONT] and [FONT=courier new]**info program**[/FONT], for example

```
man mount
``` and ```
man umount
``` and ```
man udisks
```

Udisks is used by the file browsers in 12.04 LTS to automount partitions.

---

### Post by Psil0cybin on 2014-02-15
> **sudodus said:**
> Welcome to running your computer 'like a stick shift car' :-)

When you have collected enough experience, you will be enjoy reading man and info pages. Sometimes there is more information in the corresponding info page.

[FONT=courier new]**man program**[/FONT] and [FONT=courier new]**info program**[/FONT], for example

```
man mount
``` and ```
man umount
``` and ```
man udisks
```

Udisks is used by the file browsers in 12.04 LTS to automount partitions.


Thank you so much, very helpful!

---

### Post by wiremoons on 2014-02-16
An alternative command you can use in your Terminal window is:  **lsblk**

This also shows you what drives are mounted currently on you computer - but includes a line diagram to show the device name, and the partitions and mount points that belong to that device. Might be useful to know about...

Nothing wrong with the mount commands and instructions in the previous posts of course - just thought you might like to know about this one too :)

---

### Post by Psil0cybin on 2014-03-01
Thanks so much, everyone! **very** useful information :guitar:

---

