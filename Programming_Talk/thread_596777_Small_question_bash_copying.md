---
title: "Small question: bash copying"
date: 2007-10-29
forum: Programming Talk
---

### Post by Can+~ on 2007-10-29
I wonder, is there an easy way to copy to the clipboard using the shell?

Something like

> lspci | grep -i ATI **[COLOR="#FFAA00"] > clipboard[/COLOR]**

It's nothing to serious really, but it would be very handy. :)

---

### Post by ghostdog74 on 2007-10-29
what do you want to do actually? a "clipboard" like you mentioned is just part of memory. For that, you can store your results in variables to be used later. Files can also serve as "clipboard" that you can use later. Otherwise, describe clearly what you want to do .

---

### Post by Can+~ on 2007-10-29
> **ghostdog74 said:**
> what do you want to do actually? a "clipboard" like you mentioned is just part of memory. For that, you can store your results in variables to be used later. Files can also serve as "clipboard" that you can use later. Otherwise, describe clearly what you want to do .

I'm talking about the typical clipboard, just like doing the above command for example, and then I go to .. the forum, and hit Ctrl+V to paste the output.

I thought of this like, when someone wants help with a driver, having an lspci is quite useful, so say "hey, dump this command on a shell, then come back and hit Ctrl+V to paste it".

I was googling, but got nothing, [except for a command for OSX]("http://www.digitalmediaminute.com/article/2287/copy-to-clipboard-shell-command").

And maybe.. it should be a pipe not an output ">" to make it more clear.

---

### Post by hecato on 2007-10-30
You mean something like

```

lspci > /dev/null

```


but instead

```

lspci > /dev/clipboard

```

I guess that would be nice?

---

### Post by syssyphus on 2007-10-30
sudo aptitude install xclip
...
uptime | xclip


your uptime is now in the middle-click clipboard, I am not aware of a command-line utility that accesses the control-c control-v clipboard.

---

### Post by &#35874;&#32487;&#38647; on 2010-07-21
```
lspci | xclip -selection clipboard

```
will copy the result of lspci to CLIPBOARD selection. 

There're 3 selection in X: PRIMARY, SECONDARY, CLIPBOARD

FWIK, PRIMARY selection is pasted using middle button, and CLIPBOARD is pasted using Shift-Insert.

I don't know what's SECONDARY is used for.

---

### Post by ssam on 2010-07-22
you might also find pastebinit useful
[http://linuxers.org/article/pastebinit-command-line-pastebin-client](http://linuxers.org/article/pastebinit-command-line-pastebin-client)

---

