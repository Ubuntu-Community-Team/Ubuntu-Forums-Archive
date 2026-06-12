---
title: "Cannot use 100% of the memory"
date: 2014-06-29
forum: New to Ubuntu
---

### Post by vgezer on 2014-06-29
I have a 64-bit system with 4 GB memory.

However, when the memory usage goes above 3.0 GB, the computer is not responsive at all. I cannot click anywhere, even move the cursor.

Any help would be appreciated.

---

### Post by netgooroo on 2014-06-29
In most normal Linux installs, you will never use all of your on board memory..  what exactly are you doing to use this much of your RAM? 

If I'm lucky, I may use 600MB of my 4G worth on my system. So, can you give us more information please?

---

### Post by vgezer on 2014-06-29
Actually, I have only a chromium open. Even without chrome - having apache server and the desktop itself - it is using more than 1 GB. If there is a command to list them according to the memory usage, I can copy and paste it here.

---

### Post by philinux on 2014-06-29
> **vgezer said:**
> Actually, I have only a chromium open. Even without chrome - having apache server and the desktop itself - it is using more than 1 GB. If there is a command to list them according to the memory usage, I can copy and paste it here.

Type system in dash then open system monitor. click the processes tab then the memory tab.

---

### Post by vgezer on 2014-06-29
I don't actually use Unity as desktop environment, but KDE. Here is the top output sorted by memory usage. Maybe this could help.

```
PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                         
 3102 volkan    20   0 1175700 235084 101196 S   0,0  5,9 144:36.27 chrome                                          
 3060 volkan    20   0 2114376 285352  58412 S   1,3  7,2 194:28.59 chrome                                          
 1272 root      20   0  453996  72344  51372 S   1,0  1,8  90:34.07 Xorg                                            
30400 volkan    20   0 1076088  95864  40484 S   0,0  2,4   0:11.46 chrome                                          
29839 volkan    20   0 1206004 200584  36892 S   0,7  5,1   3:28.75 chrome                                          
28849 volkan    20   0 1232544 231964  35556 S   0,3  5,9   0:49.08 chrome                                          
30222 volkan    20   0 1055360 104472  33432 S   0,0  2,6   0:18.36 chrome                                          
30511 volkan    20   0 1023152  77736  28568 S   0,7  2,0   0:03.10 chrome                                          
28946 volkan    20   0 1064928  84468  27212 S   0,0  2,1   0:07.11 chrome                                          
28992 volkan    20   0 1017916  76216  26996 S   0,0  1,9   0:05.36 chrome                                          
30457 volkan    20   0  602264  37400  23896 D   1,3  0,9   0:03.36 konsole                                         
30050 volkan    20   0 1015788  76768  23568 S   0,0  1,9   0:02.78 chrome                                          
 1814 www-data  20   0  412980  36168  23560 S   0,0  0,9   0:14.88 apache2                                         
 4387 www-data  20   0  425440  47612  22112 S   0,0  1,2   0:13.99 apache2                                         
 2500 volkan    20   0 4713248 149860  21952 S   0,7  3,8  53:48.64 plasma-desktop                                  
19828 www-data  20   0  408300  31364  19084 S   0,0  0,8   0:07.15 apache2                                         
28865 volkan    20   0  887148  26648  18300 S   0,7  0,7   0:05.28 chrome                                          
19582 www-data  20   0  408568  29668  17320 S   0,0  0,7   0:07.55 apache2                                         
25108 www-data  20   0  408308  28200  15924 S   0,0  0,7   0:03.18 apache2                                         
25106 www-data  20   0  407992  27844  15876 S   0,0  0,7   0:03.57 apache2                                         
25107 www-data  20   0  408284  28084  15836 S   0,0  0,7   0:03.50 apache2                                         
20474 www-data  20   0  408276  27832  15652 S   0,0  0,7   0:05.01 apache2                                         
20259 www-data  20   0  405684  23988  14404 S   0,0  0,6   0:06.47 apache2                                         
25114 www-data  20   0  405684  23960  14384 S   0,0  0,6   0:02.57 apache2                                         
 2490 volkan    20   0 3120264  62928  11376 S   0,0  1,6  65:39.21 kwin
```

---

### Post by ajgreeny on 2014-06-29
Use **top** again but this time press upper case M to sort processes by memory use and it may tell us more.

However, some of your processes do seem to be using a lot of memory %age compared to my machine, so it would also be useful if you showed us the output of **free -m** to see just how much memory really is being used.

---

### Post by vgezer on 2014-06-29
> **ajgreeny said:**
> Use **top** again but this time press upper case M to sort processes by memory use and it may tell us more.

However, some of your processes do seem to be using a lot of memory %age compared to my machine, so it would also be useful if you showed us the output of **free -m** to see just how much memory really is being used.

Thanks for the response.

The output of top after M:

```
top - 19:17:01 up 5 days,  5:41,  6 users,  load average: 0,63, 0,75, 0,93Tasks: 269 total,   2 running, 265 sleeping,   0 stopped,   2 zombie
%Cpu(s):  2,8 us,  1,5 sy,  0,0 ni, 95,4 id,  0,2 wa,  0,1 hi,  0,0 si,  0,0 st
KiB Mem:   3958944 total,  3659212 used,   299732 free,   125584 buffers
KiB Swap:        0 total,        0 used,        0 free.  1158984 cached Mem


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                         
 3060 volkan    20   0 2126800 338760  61144 S   8,6  8,6 208:14.75 chrome                                          
 4534 volkan    20   0 1204480 215964  27252 S   1,3  5,5   0:13.86 chrome                                          
 3102 volkan    20   0 1155848 206376  82916 S   5,0  5,2 153:51.05 chrome                                          
16873 volkan    20   0 1139088 197504   8152 S   0,0  5,0   9:01.53 chrome                                          
 2500 volkan    20   0 4713332 152892  24748 S   1,7  3,9  55:49.53 plasma-desktop                                  
 2776 volkan    20   0 2650476 127080   5792 S   1,3  3,2  13:44.14 dropbox                                         
 2753 volkan    20   0 1050284 100740  10660 S   0,0  2,5   6:48.56 owncloud                                        
 5341 volkan    20   0 4271988  97808   9336 S   0,3  2,5   4:00.02 quassel                                         
 4713 volkan    20   0 1030840  86352  27576 S   0,0  2,2   0:01.85 chrome                                          
 1272 root      20   0  459496  79644  54844 S   8,3  2,0  97:01.34 Xorg                                            
 2490 volkan    20   0 3201296  68160  15532 S   1,7  1,7  70:09.63 kwin                                            
 4698 volkan    20   0 1003528  62912  23160 S   0,0  1,6   0:01.40 chrome                                          
 2437 volkan    20   0 1875384  59796   5124 S   0,0  1,5   1:36.21 kded4                                           
 4387 www-data  20   0  425440  47620  22120 S   0,0  1,2   0:15.21 apache2                                         
 2633 volkan    20   0 2052732  45632  12688 S   0,0  1,2   0:17.66 krunner                                         
 1279 mysql     20   0  484436  45228    560 S   0,0  1,1   2:18.46 mysqld                                          
 4442 volkan    20   0  976320  40632  22260 S   0,0  1,0   0:01.18 chrome                                          
 3131 volkan    20   0  987408  40060   8704 S   0,0  1,0   0:12.03 chrome                                          
 3152 volkan    20   0  983056  39048  10012 S   0,7  1,0   7:02.10 chrome                                          
30457 volkan    20   0  603172  38644  23556 S   6,0  1,0   0:15.23 konsole                                         
 1814 www-data  20   0  412980  36300  23692 S   0,0  0,9   0:16.98 apache2                                         
19828 www-data  20   0  408300  31388  19104 S   0,0  0,8   0:08.67 apache2                                         
 3147 volkan    20   0  975296  30144   6184 S   0,0  0,8   0:27.74 chrome                                          
 2601 volkan    20   0 1832012  30048    632 S   0,0  0,8   2:18.25 mysqld                                          
19582 www-data  20   0  408568  29736  17428 S   0,0  0,8   0:08.85 apache2  
```

And **free -m**:

```
$ LANG=C free -m
             total       used       free     shared    buffers     cached
Mem:          3866       3576        289        264        122       1128
-/+ buffers/cache:       2324       1541
Swap:            0          0          0
```

---

### Post by oldos2er on 2014-06-29
Why not set up a swap partition or file? It should help with the system becoming unresponsive.

---

### Post by newb85 on 2014-06-29
I second oldos2er's suggestion.  The outputs of top and free indicate that you really don't have 1GB unused, but more like .3GB.  If you regularly get that low, swap is a good idea.  (If you're on an SSD, you're probably best to use a swap file, not a swap partition, to effectively use trim.)

Also, I'm not sure what all you're doing with Chrome, but it seems to be taking a considerable bit more memory that I've observed it to need under everyday conditions.  Are you doing something more demanding, like streaming video, having a bunch of tabs open, etc.?

---

### Post by vgezer on 2014-06-30
I've just setup a swap partition as I have a normal hard-disk. I will update the topic after using it a little bit :). Thanks.

---

