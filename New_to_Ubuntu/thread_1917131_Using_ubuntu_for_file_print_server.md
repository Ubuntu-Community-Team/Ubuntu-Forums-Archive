---
title: "Using ubuntu for file print server"
date: 2012-01-29
forum: New to Ubuntu
---

### Post by orac008 on 2012-01-29
Hi, i have an older machine that isnt much use for much else, other than basic storage and print service (amd sempron 3400+, 2gb ddr2, 80gb hdd, 250gb hdd)
 
as you may well be able to take a gues i havent used anything linux much at all, hense why i used gparted to re-label the second hdd, and just right clicked the drive to remount it. How ever i have found that i cannot create files though the terminal. i dont know if its permision issue, but would like to get every thing sorted in my head before i install smb and try and use it as a basic server. - oh i decided that using the server version was gonna be a bit tricky as s first venture into this so am running desktop 11.10 64bit.
 
i have been folling this here :- [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
how ever once i have followed that i can run mkdir, and then ls which will show the directory i have jsut made, but it does not showup in the GUI. it also will not allow the rm to remove the directory >
 
cd media/BackUp
ls
boo hello new_folder <none of these show in GUI>
rm /media/BackUp/boo
rm: cannot remove '/media/BackUp/boo': Is a directory
 
if i run rm as sudo rm i get the following
[sudo] password for caro:
rm: cannot remove '/media/BackUp/boo': no such file or directory
 
o dont know if it make any difference but the drive is formated in NTFS, and was done on another machine running windows
 
i maybe floating about a bit, as i understand what i am trying to do can be quite tricky, i just hope i can repay you guys some time

---

