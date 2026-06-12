---
title: "lpr Issues"
date: 2012-05-04
forum: Programming Talk
---

### Post by CrusaderAD on 2012-05-04
I'm trying out the following code:

```
lpr -# 1 -P Dell testnew.gif
```

and I can tell it gets spooled to the print with this command:

```
lpq -P Dell
```

then it just disappears. Nothing gets printed. Now, I manually print the image from image viewer on the desktop GUI (same user) and it prints fine. Any ideas for this behavior?

---

### Post by The Cog on 2012-05-04
I thought that lpr doesn't process files at all, just passes them transparently to the printer. So unless your printer can understand gif data, it may simply not know what to do. When using lpr, I think it would be normal to pass your gif file through a "filter" program to convert it into whatever print stream the printer understands.
Try printing a plain text file instead, and see if that works. something like:
```
lpr -# 1 -P Dell /etc/fstab
```

Actually, I'm only guessing that lpr doesn't have the smarts to convert the file to a print stream, but I think it's worth trying to print a text file just to help work out where the problem lies.

---

### Post by CrusaderAD on 2012-05-04
I got it. I had to convert it to a PS file first with imagemagick then print the PS file.

```
convert -scale 600x400 -quality 100 /home/user/temp/testnew.gif /home/user/temp/testnew.ps
```

---

### Post by The Cog on 2012-05-04
Oh, good! Thanks for the feedback.

---

