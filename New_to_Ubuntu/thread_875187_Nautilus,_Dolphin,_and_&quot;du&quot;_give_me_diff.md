---
title: "Nautilus, Dolphin, and &quot;du&quot; give me different answers for folder size--why?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by jasper.davidson on 2008-07-30
If I do "du -h /path/folder1", I see that this particular folder is [COLOR="Red"]"208K"[/COLOR]. If I go into Nautilus though, right-click the folder and select properties, it says the folder is [COLOR="Red"]"169.7 KB"[/COLOR]. And if I do the same in Dolphin, it says the folder is [COLOR="Red"]"173.7 KB (177,821)"[/COLOR]:
```

[COLOR="Blue"]/path/folder1:[/COLOR]
du -h    --> 208K
Nautilus --> 169.7 KB
Dolphin  --> 173.7 KB (177,821)
```

I would assume the 177,821 is Bytes, so that 173.7 is actually KiB (Ki=1024). But then where is Nautilus getting 169.7 KB? 
```
177,821 / 1024 / 1.024 = 169.6  ???
```
And where is du -h getting "208K"? Anyway, I'm sure there has to be a simple answer, so please enlighten me what's going on here. :)

---

### Post by jasper.davidson on 2008-07-31
I've got to be missing something obvious here, can anyone please help me out?

Another quirk:
```
du -h --> 208K
du -b --> 177,821 B
```
How is 208K the same as 177,821 Bytes? 

P.S. There are no symbolic links in the directory in question.

---

### Post by neurostu on 2008-07-31
I'm no expert but there is a difference between the size of a file and the space the file occupies on the Hard Disk... (This could be responsible for the difference)

Because of addressing issues your computer cannot have each single byte writeable as a different file, that would require 100gb of addressing to address everybit on a 100gb drive. To solve this problem most modern filesystems require a minimun address range of 4kbytes. This means that if you have a 1 kilobyte file, it occupies 1 kilobyte of harddisk space and has 3kilobytes of adjacent dead space.  This might seem like a waste, but with most files well over 4kb, it really isn't that big of a deal.

I'm not sure though why 177 KB is taking up 208KB...

Again I'm no expert...

---

### Post by jasper.davidson on 2008-08-02
Thanks for your reply, Neurostu, that might have something to do with what is going on here. But I would think that du, Nautilus, and Dolphin would all get their information directly from the ext3 file system I'm using, so their answers would at least be consistent. 

Is there anybody that can give me a definitive answer why my folder sizes differ depending on whether I use du, Nautilus, Dolphin, or some other file manager? I would really like to know what is going on here.

---

### Post by jasper.davidson on 2008-08-04
I've tried this with other folders and get the exact same crazy results: du, Nautilus, and Dolphin do not agree on how big a folder is. 

Is everyone as clueless about this as I am, or is there someone who can shed some light on what exactly is going on? :)

---

### Post by Swamptey on 2013-03-19
> Is there anybody that can give me a definitive answer why my folder sizes differ
Yes

> How is 208K the same as 177,821 Bytes?
Firstly, if you take a look at the du manual page, you can read that '-b' implies '--apparent-size'

 > --apparent-size[INDENT=2]print  apparent sizes, rather than disk usage ...
[/INDENT]
 -b, --bytes[INDENT=2]equivalent to `--apparent-size --block-size=1'[/INDENT]
[INDENT=2]
[/INDENT]
 
So in the case described, 'du --block-size=1' should give 212 992
And 'du --apparant-size -h' should give 173.7K

By default du prints disk usage and not the apparant size

> 177,821 / 1024 / 1.024 = 169.6  ???
No, 169.7 is 173.7 minus 4K, the size of the directory itself.

Also note, that when used with '-h', du rounds the size to a greater value. The best tool to estimate disk usage is baobab. The worst one is df. Sometimes df yields weird results, and I don't know why it does so.

---

### Post by QIII on 2013-03-19
This is an extremely old, and now closed, thread.

---

