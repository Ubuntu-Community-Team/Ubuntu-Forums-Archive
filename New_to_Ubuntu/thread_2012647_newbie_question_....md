---
title: "newbie question ..."
date: 2012-06-29
forum: New to Ubuntu
---

### Post by Homeroast on 2012-06-29
When I go to my Ubuntu server bash comes up.  What command do I use to run nano as the text editor?

---

### Post by josephmills on 2012-06-29
> **Homeroast said:**
> When I go to my Ubuntu server bash comes up.  What command do I use to run nano as the text editor?

```
nano <name of file to edit >
```
after editing 
press 
ctrl+x then y then enter.

---

### Post by MG&amp;TL on 2012-06-29
No question is stupid. :)

Just run:

```
nano <file>
```

...replacing <file> with a filename.

---

### Post by codemaniac on 2012-06-29
> **Homeroast said:**
> When I go to my Ubuntu server bash comes up.  What command do I use to run nano as the text editor?

```
nano *filename*
```

EDIT : Sorry for the redundant post , guess we three were on same page . ;)

---

### Post by NikTh on 2012-06-29
> **mg&tl said:**
> no question is stupid. :)

+1 :)

---

### Post by bogan on 2012-06-30
Hi!, **al**l,

Even more stupid query:

Should it not be ```
gksu nano <filename> 
```If you need sudo permissions to edit the file, or is that only for 'gedit'?

Chao!, **bogan.**

---

### Post by digithal on 2012-06-30
Gksu is only a Gtk+ frontend to su/sudo.
In your case, use *sudo nano filename*.

---

### Post by MG&amp;TL on 2012-06-30
> **bogan said:**
> Hi!, **al**l,

Even more stupid query:

Should it not be ```
gksu nano <filename> 
```If you need sudo permissions to edit the file, or is that only for 'gedit'?

Chao!, **bogan.**

Rule is:

GNOME apps: [I]gksu
[/I]KDE apps: *kdesu*
CLI apps: [I]sudo


[/I]

---

### Post by Ji Ruo on 2012-06-30
> **bogan said:**
> Hi!, **al**l,

Even more stupid query:

Should it not be ```
gksu nano <filename> 
```If you need sudo permissions to edit the file, or is that only for 'gedit'?

Chao!, **bogan.**

gksu is used when you are using a graphical user interface (GUI) which is based on GNOME. Because you are launching a command line application (nano), you don't need to use gksu. Use **sudo** instead:```
sudo nano <file>
```


Another bit of advice for the OP which may help. Nearly all commands (including applications such as nano) will have a *man page* which will give you a comprehensive listing of their usage. So you can type```
man nano
``` and it will bring up the man (manual) page, which you can scroll through. Press q to exit. You can also try the command with the --help option:```
nano --help
```Both very handy when you are on the command line.

---

### Post by Homeroast on 2012-07-01
Thanks Ji Ruo.

I was wondering how to quit nano.

---

### Post by IWantFroyo on 2012-07-01
Hit Ctrl-x.

It'll ask you whether you want to save the file and what you want to name it as (if already named just hit enter).

---

### Post by MG&amp;TL on 2012-07-01
There's commands listed at the bottom of the editor if that helps you remember. :)

---

### Post by Homeroast on 2012-07-12
When I use ctrl-x it asks me to save the file.  I enter y for yes. It seems to save the file but does not return me to bash.  How do I return to bash?  q and ctrl-q do not work.

Thanks for all your help!

---

### Post by steeldriver on 2012-07-12
I think you just need to press Enter to confirm you want to overwrite the original file (answering 'Y' just confirms you want to save the modified file... somewhere - it doesn't actually write anything yet)

Alternatively instead of trying to exit with Ctrl-x while you have unsaved changes, you can press Ctrl-o (write out) --> Enter (to confirm you want to overwrite the existing file) --> Ctrl-x which will exit immediately (because there's no unsaved buffer)

---

