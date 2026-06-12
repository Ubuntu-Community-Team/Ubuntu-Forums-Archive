---
title: "command to list hardware"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by Messyhair42 on 2012-06-14
I'm looking for a command, one I've used before, one that will list all my storage media (hard drives and flash drive included), their partitions and respective sizes. I need to find information relating to my computers structure.

---

### Post by roelforg on 2012-06-14
```

sudo lshw >~/hw.txt

```
it'll take a while, just wait for the prompt to come back.
The info is now in ~/hw.txt

---

### Post by prshah on 2012-06-14
> **Messyhair42 said:**
> one that will list all my storage media (hard drives and flash drive included), their partitions and respective sizes. I need to find information relating to my computers structure.

```

df -h
```

This will also list "virtual" partitions, such as /proc, which you can ignore.

As in the command above, you can redirect it to a file eg```
df -h > filename
```

---

### Post by seenthelite on 2012-06-14
```
sudo lshw -html > hwinfo.html
```

Then look in Home folder.  


[http://wiki.linuxquestions.org/wiki/Commands](http://wiki.linuxquestions.org/wiki/Commands)

---

### Post by zeljkojagust on 2012-06-14
lshw, lsscsi, lspci, lsusb... also listing files in /proc folder will give you all the info on your hardware in details.

---

### Post by chamber on 2012-06-14
> **prshah said:**
> ```

df -h
```

This will also list "virtual" partitions, such as /proc, which you can ignore.

As in the command above, you can redirect it to a file eg```
df -h > filename
```

This and

```
sudo fdisk -l
```

df has a much better output though.

The choice of title for your thread is poor though.

---

### Post by Messyhair42 on 2012-06-14
> **chamber said:**
> This and

```
sudo fdisk -l
```

df has a much better output though.


Thanks, this is what I was looking for

---

