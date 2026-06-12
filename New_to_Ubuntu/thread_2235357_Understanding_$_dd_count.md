---
title: "Understanding $ dd: count"
date: 2014-07-20
forum: New to Ubuntu
---

### Post by Mk32 on 2014-07-20
I have commmand here for creating a 10MB blank file: 

dd if=/dev/zero of=~/10MB.dsk count=20480

The count feature as I am told, works in 512K blocks. But how come it's in multiples of 2048, which is 512K * 4? For a 7MB image, I would use count=14336, for a 5MB I would use 10240, and so on. 

Perhaps I should use bs=1M? The man pages don't exactly help.

---

### Post by Hadaka on 2014-07-20
Hi, here is a link with dd examples,including and explaining
what you are trying to do.
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

I cannot stress [COLOR=#ff0000][/COLOR][COLOR=#ff0000]CAUTION[/COLOR] strongly enough with the dd command

you cannot recover the data if you enter a command incorrectly.

so proceed at your own risk. [COLOR=#ff0000]**CAUTION**[/COLOR]

---

### Post by at_first_light on 2014-07-20
> **Mk32 said:**
> I have commmand here for creating a 10MB blank file: 

dd if=/dev/zero of=~/10MB.dsk count=20480

The count feature as I am told, works in 512K blocks. But how come it's  in multiples of 2048, which is 512K * 4? For a 7MB image, I would use  count=14336, for a 5MB I would use 10240, and so on. 

Perhaps I should use bs=1M? The man pages don't exactly help.


By default DD uses 512 byte blocks. You are attempting to create a file that is 10485760 bytes in size. 10485760 bytes divided by 512 bytes = 20480 blocks which is the number of blocks you'll need to read. Count is the number of blocks to copy. For more information on DD check out: [https://www.gnu.org/software/coreutils/manual/html_node/dd-invocation.html](https://www.gnu.org/software/coreutils/manual/html_node/dd-invocation.html)
[U][B]
Steps:[/B][/U]
Create A 10 Megabyte Blank File:
```
dd if=/dev/zero of=~/10MB.img bs=1000 count=10000
```

Create A 10 Mebibyte Blank File:
```
dd if=/dev/zero of=~/10MiB.img bs=1048576 count=10
```

_**Notes:**_
- Make sure the file name is unique, or DD will overwrite it.
- Always use caution with DD as it's easy to make a mistake, and lose things forever (they will not be recoverable!).

---

