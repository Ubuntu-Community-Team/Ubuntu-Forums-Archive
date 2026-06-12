---
title: "[SOLVED] Post output???"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by ZabiGG on 2008-05-13
Newbie patrol checking in...

Hi-dee-ho newbies!

When you ask a question and well-intending folk try to help out but ask you to post your output, they mean you should provide a copy and paste of the contents of a specific file.

Here's how to go about it:

- open the file they mention 
(probably a 5- or 6-letter  bit of Chinese you don't understand) in the editor of your choice
- the terminal is faster for this so take a leap of faith:

type in

sudo gedit nameoffile
enter your password
copy the contents
and paste in in your thread message

close the file (but DON'T save!)

Voilà!

Have fun.

---

### Post by Inxsible on 2008-05-13
> **ZabiGG said:**
> Newbie patrol checking in...

Hi-dee-ho newbies!

When you ask a question and well-intending folk try to help out but ask you to post your output, they mean you should provide a copy and paste of the contents of a specific file.

Here's how to go about it:

- open the file they mention 
(probably a 5- or 6-letter  bit of Chinese you don't understand) in the editor of your choice
- the terminal is faster for this so take a leap of faith:

type in

sudo gedit nameoffile
enter your password
copy the contents
and paste in in your thread message

close the file (but DON'T save!)

Voilà!

Have fun.
If you simply want to copy the contents, you can just use ```
gedit nameoffile
```That way you dont have to enter the password and you dont have to worry about accidently hitting the save button etc.

It is only if you want to add information to a file that you need to open it with root privs. Also using gksudo as opposed to sudo is better. See [this link]("http://www.psychocats.net/ubuntu/graphicalsudo") for the why

---

### Post by ZabiGG on 2008-05-13
I stand corrected ;) Thanks!

---

### Post by JoshuaRL on 2008-05-13
Also, if you need to use sudo to change a file in gedit, always use:
```

gksu gedit /path/to/file/nameoffile

```
If you use sudo with a graphical application, you can mess up some important privilidges.  Important to remember.

---

### Post by ZabiGG on 2008-05-13
Keep 'em coming guys :)

It's a great exercise in making things simple!

THANK YOU.

:KS

---

