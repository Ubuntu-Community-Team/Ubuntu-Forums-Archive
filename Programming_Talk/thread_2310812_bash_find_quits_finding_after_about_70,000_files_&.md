---
title: "bash: find quits finding after about 70,000 files &amp; doesn't return"
date: 2016-01-22
forum: Programming Talk
---

### Post by Dreamer Fithp Apprentice on 2016-01-22
I've tried several variations of this:```
find / -regextype posix-extended -regex ".*\.(jpg|gif|png|jpeg|mp4|mp3|avi|wmv|mpg|mpeg|rar|7z|zip)" 2>/dev/null > log
```all based on find, and they all stop after the log grows to about 7.3 mb, which is about 70000 lines. I run that line in a terminal and it never returns. The file quits growing and the last line is typically truncated. I want to use this in a script, but as is, it will never move on to the next instruction, not to mention it isn't finding all the files it is supposed to. Why is this?

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
To clarify one point:

A partial solution would still be useful. Even if I can't get find to find all it supposed to, it would be helpful if it would at least give up and return so I could use the partial results.

Alternately, if I could make it go on and get the rest of the files it should, even if it doesn't return, that would also be useful. I could always put it in a separate process with "&", sleep for a few minutes or until the file size stabilized, and then kill it, and go on to the next instruction. Inelegant and inefficient, but it should work.

Also, some things I've excluded:

-I'm not that I'm running out of drive space.

- It isn't hanging on one particular file or dir because I can use variations on the command using different but more or less equivalent syntax, variations on the regex and such, and it will return a different set of files, presumably because it is finding them in a different order, even if it should be finding the same set in principal.

---

### Post by steeldriver on 2016-01-22
Perhaps it's disappearing into a different filesystem? I'd start by adding a `-xdev` 

```

-xdev  Don't descend directories on other filesystems.

```

Have you removed the stderr redirection to see if anything in the error stream is enlightening?

I'm always a little leery of using regex where a simpler

```

\( -name '*.jpg' -o -name '*.gif' -o -name '*.png' ... \)

```

should do.

---

### Post by Dreamer Fithp Apprentice on 2016-01-22
Thank you, Steeldriver. That is, indeed, helpful.

> **steeldriver said:**
> Perhaps it's disappearing into a different filesystem? Yes. By design. Most of the files it finds should be on another filesystem.  I can't see the rationale of the order in which it finds files. From cat-ing ~/log, I find it apparently crawls through one non-standard subdirectory in my / partion, skips some others that alphabetically should come in between, then crawls /media into another system partition (I mount all other file systems in points like /media/user/something), goes through at least some of that, I suspect all, then gets into a data partition and bogs down part way through that.

> **steeldriver said:**
> Have you removed the stderr redirection to  see if anything in the error stream is enlightening?Yes. I  should have said so. Mea culpa. Nothing there. I just put that in to  suppress the "permission denied" messages on directories without read  perms.> **steeldriver said:**
> I'm always a little leery of using regex where a simpler

```

\( -name '*.jpg' -o -name '*.gif' -o -name '*.png' ... \)

```

should do.I just tested that. Earlier I tested eleventy-seven  variations, mostly found on stackoverflow. They all work the same. If  one is faster, I suppose I should be interested in that, but I haven't  looked at that aspect. The only reason I'm using that one now is that it  looked like the most visually comprehensible and hence the easiest to  edit to change the file extensions.

Okay, I saved this for last:> **steeldriver said:**
> I'd start by adding a `-xdev`Well  now, that isn't the solution, but it is darned informative. Because I  have only a handful of media files in the / filesystem for find to find. And find returns  after finding them, making a tiny ~/log file.

                                 **[SIZE=7]                                      AHA![/SIZE]**

 I suspect the  problem isn't with find per se but for some reason the filesystem gives  up on keeping up with its output. So find keeps chugging along - that's  why it isn't returning. If I waited half an hour it probably would. But  nothing more gets written. I should have suspected that.  It's acting  just like I was trying to write to a full disk but df shows plenty of  space. Oh my. This might have something to do with caching, soft or  hard, which is a very hairy subject. OK, that suggests 2 experiments.  I'll report back on that part.

---

### Post by Dreamer Fithp Apprentice on 2016-01-23
I made an ext2 filesystem to see if maybe there was some bug in ext4 and ran the command for an hour. Didn't make any difference. But I did harvest 1 additional datum:
Find is using almost all my RAM. On lxtask it showed as a little over a gB on both the RSS column and the VM-size column. I've never found an explanation of exactly what those numbers mean and how they are different, but I assume they are some overlapping measures of RAM usage.

I have 2 gB on this machine. When I shut down the terminal that find was running on the total RAM usage (at least that is clear) went from almost maxed out to 175 mB.

So what's left? A bug in find? Surely it shouldn't be using that much RAM?

---

### Post by steeldriver on 2016-01-23
If you can't use -xdev than I'd suggest at least excluding things like /proc - which you could do using the prune command e.g.

```

find / \( -path /dev -o -path /proc -o -path /run -o -path /sys \) -prune -o *rest of your predicates*

```

---

### Post by Dreamer Fithp Apprentice on 2016-01-23
Thanks again, Steeldriver.
```
find / \( -path /dev -o -path /proc -o -path /run -o -path /sys \) -prune -o \( -name '*.jpg' -o -name '*.gif' -o -name '*.png' \)  2>/dev/null > log
```&```
find /media/me/data-1/ \( -path /dev -o -path /proc -o -path /run  -o -path /sys \) -prune -o \( -name '*.jpg' -o -name '*.gif' -o -name  '*.png' \)  2>/dev/null > log
```both give the same result. The log is a little smaller at 5.9 mB. I'd be willing to bet that is somehow connected to the fact I used the extensions in your example rather than make it the same as the others. You'll note that in the second case, instead of aiming it at root I pointed it at a data directory that would be all one filesystem anyway.

Even if the system were caching writes aggressively, surely it wouldn't hold them for an hour. I'm stumped. I wonder if this is a bug in find or something weird in the usb system. I'm writing to a usb external drive. That's my only choice atm. Maybe some other folks could run one of these and see if they get the same result?

---

### Post by steeldriver on 2016-01-24
I don't think the buffering that you're seeing is at the drive level: the *shell* will buffer stdout by default when it is redirected to a file - in other words, it won't output anything until it has a full buffer's worth of filenames (even if that means stopping partway through a filename, as you have observed) or has terminated

If you are searching deep into directories that have few matches, then it's quite normal for it to appear like nothing is happening for long periods of time

You can play with stdbuf if you like e.g.

```

**stdbuf -o0** find / *whatever *

```

---

### Post by Dreamer Fithp Apprentice on 2016-01-24
Thanks. Interesting. I didn't know bash did that. It hasn't changed matters though. But I am making progress. I made a subdir in the root of the data partition, and moved the other directories there into it a few at a time and kept running the command on it. Bottom line, I think I've isolated the directory causing the problem. It might have something to do with excessive path length or maybe too many files in a directory. Whether THE problem or not, definitely A problem. I'll narrow it down and isolate the exact cause, then check if the global problem goes away. I'll post when I can report more. It is taking a loooooooong time to rm the dir. I just hate journaling when I need to delete something big.

---

### Post by Dreamer Fithp Apprentice on 2016-01-26
Here is what I THINK the situation is:
The  directory causing the problem was created by BleachBit, when I  ill-advisedly ran it with settings to wipe empty drive space on the data  directory, and it was interrupted part way through. BB created several  subdirectories in its wipe directory and created astronomical numbers of  files in those subdirectories when wiping free space. So many that the  directory files themselves are HUGE, over a gB each. I don't mean the  content of the directory - I mean the actual directory itself. Thunar  reports the actual size of directory files, not the amount of content.  So for example, thunar reports most directories on my system as 4.1 kb.  If the directory "contained" ("indexed" would be a better word) 3 files,  each a terabyte in size, it would still be a 4.1 kb file. But if it  "contained" a gazillion 0 byte files, it would be huge. Experiment  clearly indicates this directory as the source of the problem. As to WHY  a directory like this should cause find to stop reporting (or for bash  to stop passing on its report) in the middle of a line, I haven't a  clue. It strikes me as likely to be a bug that only shows up under  strange circumstances.

When I get through rm-ing those files,  I'll create some test files to test aspects of this hypothesis, but  running ```
rm -r -f -v
``` against the directory is taking forever. It is  working, the -v assures me of that, but there is a tremendous number of  files. And no matter how I nice it, that rm really bogs my system down.  So I run it for a few hours at a time. It's taking so long I may give up on rm, create another filesystem (maybe ext2 so I won't have to go through  this again - fsck journaling), copy all my other files over, and  reformat this partition.

Anyway, that's what is taking me so long to report back on this. Hopefully, I'll finish rm-ing before the drive wears out.

---

