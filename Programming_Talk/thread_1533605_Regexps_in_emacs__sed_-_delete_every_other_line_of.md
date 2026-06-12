---
title: "Regexps in emacs / sed - delete every other line of a file?"
date: 2010-07-18
forum: Programming Talk
---

### Post by Zorgoth on 2010-07-18
Exactly as the title suggests, I am trying to find a way to delete every other line of a file using either emacs or sed.  If you know how to do it in both emacs and sed I would appreciate it if you could show me both ways so I can understand regexps better.

---

### Post by xsinsx on 2010-07-18
simple enough.
```
Macintosh:Desktop stephenjackson[color=#19177C]$ [/color]cat text.txt
1
2
3
4
5
6
7
8
9
Macintosh:Desktop stephenjackson[color=#19177C]$ [/color]sed -n [color=#BA2121]'p;N'[/color] text.txt
1
3
5
7
9

```

---

### Post by DaithiF on 2010-07-18
Hi,
also, in gnu sed you can do:
```
sed '2~2d' testfile

```
where the pattern is firstline~step, ie. starting from line 2 delete every 2nd line

---

### Post by Zorgoth on 2010-07-18
I know little about sed so this may not be very elegant but to delete three of every four lines in a file

```

sed '1~4p;1~1d' /path/to/file > /path/to/modified/file

```

should work

---

### Post by Zorgoth on 2010-07-18
oops wrong thread

---

### Post by jpkotta on 2010-07-18
You don't need regexps to do what you want.  (This is not tested very well.)

```

(defun delete-even-lines ()
  (interactive)
  (save-excursion
    (beginning-of-buffer)
    (while (not (eobp))
      (forward-line 1)
      (when (not (eobp))
        (delete-region (line-beginning-position)
                       (1+ (line-end-position)))))))

```

---

