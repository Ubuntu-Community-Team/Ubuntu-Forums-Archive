---
title: "Disc space problems."
date: 2013-04-19
forum: New to Ubuntu
---

### Post by alvitawa on 2013-04-19
I have Windows and Ubuntu installed on the same laptop. On ubuntu i have very little space and on windows i have a lot of free space, so i want Ubuntu to have more disk space by moving it to the same drive as Windows or something, but i don't have any idea on how to do that. How could i move Ubuntu to a bigger disc or do something to obtain more space?

This is the File Systems information i get from System Monitor:

Device      |      Directory                  | Type  |  Total   |   Free   |     Available    | Used
/dev/loop0  /                                     ext4    16.1 GiB   2.3 GiB     1.5 GiB        1.5GiB     90%
/dev/sda3   /host                               fuseblk 451.0 GiB 256.8 GiB  256.8 GiB     256.8GiB  43%
/dev/sda2   /media/SYSTEM RESERVED  fuseblk 100.0 MiB 74.8 MiB   74.8 MiB      74.8MiB    25%

On windows, at "Computer", it says there's only 1 drive with a total storage of 500GB


sorry for eventually bad english, i'm not english

---

### Post by ibjsb4 on 2013-04-19
Your WUBI install is allotted 16G.  WUBI has a max size of 30G, so you could resize if you wanted to.

[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=resize+wubi&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=resize+wubi&sa=Search&cof=FORID:9)

Most people will agree though, that dual boot is the way to go.

---

### Post by alvitawa on 2013-04-19
Tanks [**[COLOR=#000000]ibjsb4[/COLOR]**]("http://ubuntuforums.org/member.php?u=1729120") that's exactly what i was looking for.

---

