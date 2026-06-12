---
title: "Hmmm.. Compiling stuff yourself?"
date: 2005-05-11
forum: Programming Talk
---

### Post by GoneWacko on 2005-05-11
Edit: Aaargh, I only just noticed the subforum... Jeez. :roll: Just my luck

Hey all. I guess this is the most logical place to post this, if not, well... Too bad :)

I'd call myself an intermediate linux user. I *could* switch to linux entirely and completely remove my windows *IF* it were easier to play most games on linux. I know my way around, and when I don't, I have various ways to find out what way to go :)

Only one thing (well, more than one thing, really) is something I never completely got the hang of: Compiling things yourself.

I am a programmer. I have a fair deal of knowledge of Delphi (Object Pascal) and I know C, although I hardly do anything with it.

But building packages myself, as  opposed to doing a simple apt-get, is something I have some questions about.

I'll just list my questions :)
[list]
[*]Can I delete the source code once I've done 'make install' ?
[*]What is the best way to put source when building it? I've seen multiple approaches. From people putting it in the /proc directory to /usr/share/src/
[/list]
Hmm. I was sure I had more questions, but I seem to have forgotten what they were... :) Happens to the best.
I'd be happy if these two questions were answered because they have always been a bit unclear to me.

---

### Post by Xian on 2005-05-11
[QUOTE=GoneWacko]I'll just list my questions :)
[list]
[*]Can I delete the source code once I've done 'make install' ?
[*]What is the best way to put source when building it? I've seen multiple approaches. From people putting it in the /proc directory to /usr/share/src/
[/list][/QUOTE]
1. I'd save it since with most packages you can go back into that directory and use the 'make uninstall' command to remove it from your system.
2. While you are building it? That really doesn't make any difference AFAIK unless you are using some type of spec file and building source binary packages.

---

### Post by JonahRowley on 2005-05-11
[QUOTE=GoneWacko]Can I delete the source code once I've done 'make install' ?[/quote]
Yes, but "make uninstall" provided by that makefile is useful.

> What is the best way to put source when building it? I've seen multiple approaches. From people putting it in the /proc directory to /usr/share/src/
**/proc**?!  No, do **not** put it there.  I don't think you *can* even put it there.  It doesn't really matter, I use **~/src** since I build as my normal user, and install under sudo.

---

### Post by ow50 on 2005-05-11
If you do,
$ ./configure && make
$ sudo checkinstall

you can uninstall with apt-get/synaptic. The problem is that all apps don't provide an uninstallation feature at all, which can be very annoying. Using checkinstall you can delete the source code, but maybe keep the resulting deb package in case you need to reinstall.

---

### Post by jerome bettis on 2005-05-11
[QUOTE=ow50]If you do,
$ ./configure && make
$ sudo checkinstall

you can uninstall with apt-get/synaptic. The problem is that all apps don't provide an uninstallation feature at all, which can be very annoying. Using checkinstall you can delete the source code, but maybe keep the resulting deb package in case you need to reinstall.[/QUOTE]
 i did not know that!  thanks for the tip.

as far as where to put it, i use /usr/src or ~/src sometimes.  /proc???? that's not even a real filesystem

---

### Post by vague- on 2005-05-12
You can always do:

```
$ make -n uninstall
```

and capture the output.  It is usually sufficient, double-check before you delete the folder.

---

### Post by GoneWacko on 2005-05-12
Well.. then it wasn't /proc. hmm. Something I found to be a weird location, anyhow.

But thanks for the help :)

---

