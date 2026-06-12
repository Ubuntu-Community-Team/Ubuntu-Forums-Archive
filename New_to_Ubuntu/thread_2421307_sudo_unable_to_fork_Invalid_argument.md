---
title: "sudo: unable to fork: Invalid argument"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by ogola89 on 2019-06-19
Hi guys,

I posted this thread in the general help section as well as here as I'm not too sure of the best location.

So I am a bit new to the whole Linux environment, although I can work my way around, I am no way an expert. I am a biologist and know the commands in a general manner, but not necessarily what is going on underneath the hood for everything.

I have the Ubuntu WSL installed on my Windows 10 pro laptop.

I have been installing various things for some analyses I would want to perform in python, R, etc and have installed various environments with no issue.

However, today, something happened when I wanted to install nautilus. I typed in: 
```
sudo at update
``` 
instead of 
```
sudo apt update
```

I am using COMODO firewall, which prompted me as to how to treat the command/file. However, I noticed at that point that I had a typo and selected it to be 'contained' so as to not allow writing of anything that I wasn't sure.

I am not sure if the firewall setting worked, but now it seems my sudo command is broken.

Any time I use sudo now to install anything, it gives me the following error:
```
$ sudo apt-get update
sudo: unable to fork: Invalid argument

```

```
$ sudo apt install nautilus
sudo: unable to fork: Invalid argument
```

```
$ sudo apt-get install python3-matplotlib
sudo: unable to fork: Invalid argument

```

It seems it is a ubiquitous issue which comes up nomatter what I am trying to install. I installed some packages shortly prior to the ```
sudo at update
``` blunder, and I am convinced it may be something to do with this.

Could you please help me diagnose/fix the issue?

Thanks!

---

### Post by coffeecat on 2019-06-19
Duplicate of [https://ubuntuforums.org/showthread.php?t=2421305](https://ubuntuforums.org/showthread.php?t=2421305)

Closed.

---

