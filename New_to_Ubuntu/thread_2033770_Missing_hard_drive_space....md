---
title: "Missing hard drive space..."
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Ziron on 2012-07-26
I'm not too sure if I'm supposed to post this here, but here it goes.

My system had 89.7GiB of space and then I decided to make a digital copy of one of my DVDs and I was left with 79.8GiB of space. However, there was something wrong with the file and I deleted it. After I deleted the file, I checked my hard drive and I noticed that I didn't get the 9.9 GiB of space back. Can anyone help me get it back?

---

### Post by papibe on 2012-07-26
Hi Ziron. Welcome to the forums ):P

The file probably went to the Trash. If you empty it, you'll recover the space.

Tell us how it goes.
Regards.

---

### Post by Ziron on 2012-07-26
Hi, thanks for the quick reply!

I've already done that, and no luck. That's why I'm here.

---

### Post by papibe on 2012-07-26
Sorry to hear that.

How did you remove the file? Using the GUI, the terminal?

Regards.

---

### Post by Ziron on 2012-07-26
I used the GUI.

---

### Post by papibe on 2012-07-26
Could you post the result of this command?
```
ls -R ~/.local/share/Trash/
```
Regards.

---

### Post by Ziron on 2012-07-26
*****@*****:~$ ls -R ~/.local/share/Trash/
/home/****/.local/share/Trash/:
expunged  files  info

/home/****/.local/share/Trash/expunged:

/home/****/.local/share/Trash/files:

/home/****/.local/share/Trash/info:
****@*****:~$

Edit: I thought I might mention that the copy was made with VLC. Does VLC keep copies somewhere?

---

### Post by papibe on 2012-07-26
Nothing hidden on the Trash folder.

Could you verify again the space available by posting the result of this command?
```
df -h
```
Regards.

---

### Post by Ziron on 2012-07-26
```
****@*****:~$ df -h
df: `/root/.gvfs': Permission denied
Filesystem             Size  Used Avail Use% Mounted on
/dev/sdb2               93G  8.9G   80G  11% /
udev                   1.9G  4.0K  1.9G   1% /dev
tmpfs                  766M  948K  765M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   1.9G  160K  1.9G   1% /run/shm
/dev/sdb1              473M   55M  395M  13% /boot
/home/****/.Private   93G  8.9G   80G  11% /home/****
/dev/sdb5              499G  407M  499G   1% /media/Z Storage
****@*****:~$
```

---

### Post by Bufeu on 2012-07-27
The path to the Trash is **/home/username/.local/share/Trash**. If you deleted something as root (e.g. deleted a file using Nautilus invoked via gksu), it's at: **/root/.local/share/Trash**.

---

### Post by Ziron on 2012-07-27
There's nothing in that trash. Could it be that I actually still have the space and it's just not showing up?

---

### Post by papibe on 2012-07-27
Very unlikely.

Let's see if there's a copy of the file somewhere.

This command will print all files that 4Gb or bigger:
```
find -type f -size +4G -print
```
Tell us how it goes.
Regards.

---

### Post by Ziron on 2012-07-27
I think I did that wrong. This is all it gave me.

```
****@******:~$ find -type f -size +4G -print
find: `./.Trash-0': Permission denied

```

---

### Post by papibe on 2012-07-27
No. You did it right, and there may be a clue on that result.

Could you post the result of this command?
```
sudo du -ah .Trash-0
```
Regards.

---

### Post by Ziron on 2012-07-27
```
*****@*****:~$ sudo du -ah .Trash-0
12K    .Trash-0/files/examples.desktop
16K    .Trash-0/files
12K    .Trash-0/info/examples.desktop.trashinfo
16K    .Trash-0/info
36K    .Trash-0
****@*****:~$ 
```

---

### Post by Ziron on 2012-07-28
I guess I'll just resign myself to the fact that the hard drive space is gone.
Thanks anyway.

---

