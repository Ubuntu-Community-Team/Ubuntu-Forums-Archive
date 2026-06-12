---
title: "Comparing two directories"
date: 2009-03-13
forum: Programming Talk
---

### Post by HarryMcScary on 2009-03-13
Sorry if this is the wrong forum for bash questions.  Please move this if it is.

I wanted to check today to make sure that my backup music directory had everything that my main directory had so I did the following:
```
matt@acer:~$ ls -r /home/matt/music/*/ > primary
matt@acer:~$ ls -r /mnt/usbdrive/home/matt/music/*/ > external
matt@acer:~$ diff primary external > check
```
My output was strange, and I really have no idea what it means.  Any help translating it would be great.  (NB: there's more output, but it's all similar.  I see no reason to post it all unless some finds it necessary.)
```
1c1
< /home/matt/music/yeah_yeah_yeahs/:
---
> /mnt/usbdrive/home/matt/music/yeah_yeah_yeahs/:
12c12
< /home/matt/music/tv_on_the_radio/:
---
> /mnt/usbdrive/home/matt/music/tv_on_the_radio/:
18c18
< /home/matt/music/the_white_stripes/:
---
> /mnt/usbdrive/home/matt/music/the_white_stripes/:
29c29
```

Looking at the two files manually, they seem to be the same.  I'm a little at a loss for what all of this means.

Thanks in advance!

---

### Post by ghostdog74 on 2009-03-13
even though you have the same files both in different folders, diff will reflect a difference because of the different paths they are in.
you should just go to each directory and list the files
eg
```

# cd /home/matt/music
# ls -1 | sort > a.txt
# cd mnt/usbdrive/home/matt/music/
# ls -1 | sort > b.txt
# diff a.txt b.txt

```

---

### Post by HarryMcScary on 2009-03-13
That did it.

Thanks!

---

### Post by asimon on 2009-03-13
```

diff -qr /home/matt/music /mnt/usbdrive/home/matt/music/

```
is an other possibility. It shows only which files differ or are missing.
The q is for "Output only whether files differ", the r for "Recursively compare any subdirectories found".

If you are interested in what the diff output you posted means, have a look at [the Wikipedia entry for diff](http://en.wikipedia.org/wiki/Diff).

---

