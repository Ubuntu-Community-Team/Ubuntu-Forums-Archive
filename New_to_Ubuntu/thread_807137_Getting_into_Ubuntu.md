---
title: "Getting into Ubuntu"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bern1939 on 2008-05-25
Trying to get into Ubuntu 7.10 via recovery mode.
I have a partition space problem apparently at 47GB???? plus an inability to type my username!!

Anyway I am running 'recovery' and have arrived at the following screen dump:

"gzip:/var/log//dmesg.0.gz':No space left on device
mv: cannot stat `/var/log//dmesg.).gz': No such file or directory
root@bernard-desktop:~# "

What do I enter at this point to proceed please or am I lost??


Bern

---

### Post by shifty_powers on 2008-05-25
well for a start, why do you need to use recovery mode?

---

### Post by unutbu on 2008-05-25
It sounds like you've run out of space on your linux partition.

```
"gzip:/var/log//dmesg.0.gz':**No space left on device**
```

You can check how much space is available on your partitions by typing

```
df
```

One way you can alleviate the problem is to try to delete some stuff you don't need. To find the top 10 directories which are consuming the most space, type

```
du / | sort -rn | head -n 10
```

---

### Post by bern1939 on 2008-05-25
Thanks but the results mean little to me.
I wonder if there is anything I can type at the terminal bit to get into Ubuntu?

Thanks

bern

---

### Post by unutbu on 2008-05-25
You won't be able to get into Ubuntu as a normal user until you fix this problem. To make sure that my guess -- that your partition is too full -- is correct, please post the output to the df command.

If you have just installed Ubuntu and are getting this error, it means that you've allocated too little space for Ubuntu and you'll need to repartition and create some more space for Ubuntu. 

If you have been using Ubuntu for a while and are now encountering this problem, it means you've filled up your account/system too much and you need to find some things to delete. The 

```
du / | sort -rn | head -n 10
```

is a non-graphical way of asking the computer what directories are the biggest space hogs. There are nicer graphical utilities but you won't be able to access them until you free up some more space.

---

