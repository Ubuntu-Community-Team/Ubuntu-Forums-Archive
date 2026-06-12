---
title: "root folder"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by 8igwave on 2012-06-19
Can anyone give me step by step instuctions how to place an alternate iso file onto root folder of hard drive? Have the iso image just can't put it to roor?

---

### Post by Kakers on 2012-06-19
Well you can just move the file with:
1) Open Terminal.
2) Change directory to where the file is located with the 'cd' command (You can check where you are with 'pwd').
3) Move the file to /root/ with 'sudo mv <filename> /root/' of course you will need to replace <filename> with the name of the file.

<snip>
Hope this helps!

---

### Post by Cheesemill on 2012-06-19
Telling people how to activate the root account isn't allowed on these forums.
To gain access to a root terminal the preferred method is to do:
```
sudo -i
```

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by sudodus on 2012-06-19
> **8igwave said:**
> Can anyone give me step by step instuctions how to place an alternate iso file onto root folder of hard drive? Have the iso image just can't put it to roor?
I think I understand what you ask for, but I don't understand what you really want to do. I see no reason to place an alternate iso file onto the root folder of an existing installed system.

Do you want to boot from it? Or do you just want to store it somewhere and make it available for some or all users? Or something else?

---

### Post by zombifier25 on 2012-06-19
> **Kakers said:**
> But if you want to navigate to root:
1) Open Terminal.
2) Set root password with 'sudo passwd'.
3) Elevate to root with 'su' using the password you set.
4) Change directory to root with 'cd /root'

Hope this helps!

No.

---

### Post by 8igwave on 2012-06-19
Thanks got it! :)

---

### Post by 8igwave on 2012-06-19
Was trying to make a bootable usb from iso using unetbootin, it told me to move iso to root directory. Sussed it now tho cheers!

---

### Post by Kakers on 2012-06-19
> **Cheesemill said:**
> Telling people how to activate the root account isn't allowed on these forums.
To gain access to a root terminal the preferred method is to do:
```
sudo -i
```

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Ah! Looks like I need to go and do some more reading, thanks for pointing that out to me.

---

### Post by sudodus on 2012-06-19
To prepare the USB drive for Unetbootin you should make a primary partition with the FAT32 file system. I usually add the boot flag and the lba flag. The partition size should be big enough. 2 GB should be more than enough, 1GB should be enough in most cases (depending on the size of the system on the iso file).

And then you let Unetbootin do the job :-)

See also this link with several partitions, also a data partition to be used from linux as well as windows
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

But you can actually boot directly from the iso file as described in the following link
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

