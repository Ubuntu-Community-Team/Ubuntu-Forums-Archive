---
title: "Latest Boot Info Script news"
date: 2011-05-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2011-05-21
A few days ago I was notified of the release of version 0.60, then today I was informed of this:

> If you download the last version from git (not in v0.60), you will be able to get the last git version much easier in the future:

```
bash ./boot_info_script.sh --update <filename>
```

If no filename is specified, the file will be saved in the home dir as

"boot_info_script_YYYY-MM-DD_hh:mm:ss.sh".

When this new script is run, it will display the retrieval date in the RESULTS.txt file too.

If you notice any bugs in BIS (someone on the forum), PM me.

This was also fixed:

Remove spurious space for the "Boot sector info:" line output, which was a side effect of replacing echo with printf when fixing the displaying of the grub2 embedded config file. 

You can certainly PM me if you see something wrong with the script itself, or you could start a new thread here requesting assistance:

[http://sourceforge.net/projects/bootinfoscript/forums/forum/905692](http://sourceforge.net/projects/bootinfoscript/forums/forum/905692)

Please don't post there requesting assistance with boot problems though ;)

---

