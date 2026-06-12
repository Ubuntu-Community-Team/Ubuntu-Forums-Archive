---
title: "Mounting problem."
date: 2014-05-01
forum: New to Ubuntu
---

### Post by shields2 on 2014-05-01
I am having this problem since installing 14.04.

Here's the line I entered into my fstab:
```
UUID=xxx-xxx-xxx-xxx  /media/wd4tb ext4 defaults 0 0 
```
Naturally, the xxx in the example are the real numbers of the drive.

When I boot, the drive shows up on the left hand side, but dropbox and my copy app can't see it until I open it in Nautilus.

Any ideas why?

Thanks!

---

### Post by coffeecat on 2014-05-01
Post moved to its own thread.

---

### Post by sandyd on 2014-05-01
> **shields2 said:**
> I am having this problem since installing 14.04.

Here's the line I entered into my fstab:
```
UUID=xxx-xxx-xxx-xxx  /media/wd4tb ext4 defaults 0 0 
```
Naturally, the xxx in the example are the real numbers of the drive.

When I boot, the drive shows up on the left hand side, but dropbox and my copy app can't see it until I open it in Nautilus.

Any ideas why?

Thanks!

What does the terminal output when you reboot, and run
```

sudo mount -a
```

---

### Post by shields2 on 2014-05-01
> **sandyd said:**
> What does the terminal output when you reboot, and run
```

sudo mount -a
```

It asks for my password and then returns this:
```
myusername@thepciuse:~$ sudo mount -a
[sudo] password for myusername: 
myusername@thepciuse:~$ 

```

(yes -- i did reboot before typing this.)

---

### Post by sandyd on 2014-05-02
Try running
```

sudo mkdir /media/username/xxx-xxx-xxx-xxx
sudo chown username:username /media/username/xxx-xxx-xxx-xxx

```

And using the following fstab
```

UUID=xxx-xxx-xxx-xxx  /media/username/xxx-xxx-xxx-xxx ext4 defaults 0 0
```
Where *username* is your username

---

### Post by shields2 on 2014-05-05
> **sandyd said:**
> Try running
```

sudo mkdir /media/username/xxx-xxx-xxx-xxx
sudo chown username:username /media/username/xxx-xxx-xxx-xxx

```

And using the following fstab
```

UUID=xxx-xxx-xxx-xxx  /media/username/xxx-xxx-xxx-xxx ext4 defaults 0 0
```
Where *username* is your username

This seems to have done the trick!

Thanks!

---

