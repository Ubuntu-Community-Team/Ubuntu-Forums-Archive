---
title: "The hosts file"
date: 2021-06-28
forum: New to Ubuntu
---

### Post by billywyatt2 on 2021-06-28
I am running Ubuntu 20.04.2 LTS and really enjoy using the OS.

But i do have a couple of problems and they are:

1) I want to block my computer from accessing _Facebook_ via the hosts file
and the command line. Could someone show me how to go about this
please.

2) I suffer with cataracts in both eyes and find it very difficult to read the text in the Ubuntu terminal.
Could someone please help me out here and show me how to enlarge the textl please.

Many thanks

---

### Post by tea for one on 2021-06-28
> **billywyatt2 said:**
> 2) I suffer with cataracts in both eyes and find it very difficult to read the text in the Ubuntu terminal.
Could someone please help me out here and show me how to enlarge the textl please

This is for GNOME terminal:-

Open terminal > Edit > Preferences > Custom Font > Click Monospace Regular 11 (probably)
A new editing box will appear to allow you to specify the font size.

Pink arrow on attached screenshot

[ATTACH=CONFIG]288740[/ATTACH]

---

### Post by guiverc on 2021-06-28
To block facebook via hosts, you can just add lines like

```
127.0.0.1    facebook.com
```

Nice and easy it feels like; but facebook have a load of other addresses; my current list (which I got from online) has 191 such records needed just to block facebook (*okay that count includes maybe 4 comment lines which aren't needed*)

I can't recall where I got my list (*I know it was from a youtuber, but it wasn't his list and I forget where it was from, so I won't currently provide it, but a quick list I found is*)

[https://gist.github.com/djaiss/85a0ada83e6bca68e41e](https://gist.github.com/djaiss/85a0ada83e6bca68e41e)

As that only provides 12 lines (for facebook); it's somewhat less complete than what I'm currently using.. but you'll get the idea anyway.

---

### Post by ActionParsnip on 2021-06-28
It's the same as in Windows

---

### Post by billywyatt2 on 2021-06-29
I have finally been able to enlarge the text in the terminal - Yippee!

As for the hosts file, i opened a terminal and typed:
```

sudo pluma /etc/hosts

```

The hosts file opened
and then i typed:
```

127.0.0.1 facebook.com

```

Clicked on save and still no difference?

Thanks for all the help everyone but i have decided to turn off my Desktop computer
until i have had the operation to remove these cataracts.

---

### Post by ActionParsnip on 2021-06-29
If the DNS has been cached recently then the cache will be used. I suspect this will work now

---

### Post by TheFu on 2021-06-29
[https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279](https://lifehacker.com/how-to-block-unwanted-ads-in-all-applications-and-speed-30814279)
Note the article date and which websites are blocked.  ;)

---

### Post by The Cog on 2021-06-29
For quick enlarging or shrinking text: **[COLOR="#0000FF"]Ctrl +[/COLOR]** (you may need the shift key as well to get a plus) and **[COLOR="#0000FF"]Ctrl -[/COLOR]** will do the trick.

---

