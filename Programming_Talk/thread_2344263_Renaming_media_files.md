---
title: "Renaming media files"
date: 2016-11-23
forum: Programming Talk
---

### Post by Herbon on 2016-11-23
Greeting all

I have a NAS fill of TV shows and their seasons. Most of files have odd names. I tried running the following command in the folder, 

```

#Standardized poorly named show and display progress bar.
rename -v 's/.*[s,S](\d{2}).*[e,E](\d{2}).*\.mkv/Designated.Survivor\ S$1E$2.mkv/' | pv

```

Yet I not seeing any changes in files or progress bar, listed below is what I see after running the command

```

SillyNuBee@GX620:~/Documents/Video/Designated.Survivor.S01$ sudo rename -v 's/.*[s,S](\d{2}).*[e,E](\d{2}).*\.mkv/Designated.Survivor\ S$1E$2.mkv/' | pv
^C 0 B 0:54:18 [   0 B/s] [<=>                                                                    ]

```

Any suggestion? :confused:

---

### Post by steeldriver on 2016-11-23
You're telling it *how *to rename the files, but not *which *files to rename - it needs to be something like

```

rename -v 's/.*[s,S](\d{2}).*[e,E](\d{2}).*\.mkv/Designated.Survivor\ S$1E$2.mkv/' ***.mkv** | pv

```

Personally I'd add a -n (no operation) switch until I was sure that the rename command was working right

```

rename -v**n** 's/.*[s,S](\d{2}).*[e,E](\d{2}).*\.mkv/Designated.Survivor\ S$1E$2.mkv/' ***.mkv** | pv

```

---

### Post by Herbon on 2016-11-23
So I ran the following command without (-n), and got the following.
It somehow missed the three (in bold) files?

```

#
SillyNuBee@GX620:~/Documents/Video/Designated.Survivor.S01$ ls
**designated.survivor 104.hdtv-lol[ettv].mkv**  Designated.Survivor S01E01.mkv  Designated.Survivor S01E07.mkv
**designated.survivor 105.hdtv-lol[ettv].mkv**  Designated.Survivor S01E02.mkv  
**designated.survivor 106.hdtv-lol[ettv].mkv**  Designated.Survivor S01E03.mkv


```

Here is the original named files

```

#
SillyNuBee@GX620:~/Documents/Video/Designated.Survivor.S01$ ls
designated.survivor.104.hdtv-lol[ettv].mkv
designated.survivor.105.hdtv-lol[ettv].mkv
designated.survivor.106.hdtv-lol[ettv].mkv
Designated.Survivor.S01E01.HDTV.x264-KILLERS[ettv].mkv
Designated.Survivor.S01E02.HDTV.x264-KILLERS[ettv].mkv
Designated.Survivor.S01E03.HDTV.x264-KILLERS[ettv].mkv
Designated.Survivor.S01E07.720p.HDTV.X264-DIMENSION[ettv].mkv

```

It seem like I missed a step.

---

### Post by steeldriver on 2016-11-24
That shouldn't be a mystery - the filenames simply don't match your .*[s,S](\d{2}).*[e,E](\d{2}).*\.mkv pattern

Assuming the 3 digits can be broken down as 1 digit for series followed by 2 digits for episode, you could try something like

```

's/.*\.(\d)(\d{2})\..*\.mkv/Designated.Survivor\ S$1E$2.mkv/'

```

---

### Post by Herbon on 2016-11-26
Ok this works!

Thanks

---

