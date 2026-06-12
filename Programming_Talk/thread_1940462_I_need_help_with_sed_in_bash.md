---
title: "I need help with sed in bash"
date: 2012-03-13
forum: Programming Talk
---

### Post by forrestcupp on 2012-03-13
I've worked for hours to try to get my .docx & .xlsx files to be associated with my MS Office that was installed with PlayOnLinux. I'm finding out that PlayOnLinux is great for installing things, but not so great for actually using them.

Anyway, I finally figured out how to use **mimeopen -d** to create a custom command for playonlinux to associate files in Nautilus. The only problem was that it didn't work if the filename or folder name had spaces. So I found where someone put the following code in the PlayOnLinux shortcut scripts for Word and Excel. That code makes it work with spaces, but a side effect of this code is that it replaces all 'C's with 'Z's in the file and folder names. Can anyone tell me exactly what this is doing, and maybe how to get it to work with spaces, but not replace the 'C's? Here's the code:
```
"$(echo "$@" | sed -e 's:C:Z:' -e 's:/*/:\\:g')"
```

---

### Post by wojox on 2012-03-13
```
's:C:Z:'
```
What if you remove this chunk. It's what substitutes C for Z

---

### Post by forrestcupp on 2012-03-13
It worked perfectly without that. Thank you very much. I don't know why the guy had that in there.

Thanks again.

---

### Post by forrestcupp on 2012-03-14
> **wojox said:**
> ```
's:C:Z:'
```
What if you remove this chunk. It's what substitutes C for Z

I just wanted to let you know that in the Wine subforums, I wrote a [HowTo about how to do all of the things I was trying to get done](http://ubuntuforums.org/showthread.php?p=11763042#post11763042), and I credited you for helping me with that code.

Thanks again.

---

### Post by wojox on 2012-03-14
You are welcome and thank you. :p

---

