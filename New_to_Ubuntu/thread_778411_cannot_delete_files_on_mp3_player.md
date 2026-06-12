---
title: "cannot delete files on mp3 player"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by pympnplaya on 2008-05-02
i have an archos gmini xs200 mp3 player.  the screen recently went out so i am now using it as an external hardrive for my mp3s.  i also used it to transfer some torrents from my laptop to my computer.  i deleted the files but now they are stuck in a folder named ".Trash-1000" on my mp3 player.  i want to get rid of the file because it is taking up 9.2 gigs of the 20 gig mp3 player.  but when i try and delete them on xubuntu either through terminal or thunar, i get a read-only access error and cannot delete it.  in terminal i get this output:

pympnplaya@pympnplaya-desktop:/media/JUKEBOX$ rm -r .Trash-1000
rm: cannot remove `.Trash-1000/files/Heroes.S02E09.HDTV.XviD-LOL.avi': Read-only file system
rm: cannot remove `.Trash-1000/files/heros': Read-only file system
rm: cannot remove `.Trash-1000/files/saigon': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg497': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg498': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg499': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg500': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg501': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg503': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg504': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg505': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg506': Read-only file system
rm: cannot remove `.Trash-1000/files/NPROTECT': Read-only file system
rm: cannot remove `.Trash-1000/files/desktop.ini': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg507.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg508.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg509.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg510.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg511.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/INFO2': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg502': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg502$1': Read-only file system

i also tried sudo rm but that didnt work either.  any suggestions?  thanx

---

### Post by kpkeerthi on 2008-05-02
Your player has been mounted readonly. So removing with sudo won't help. Unmount and disconnect your player. Connect it back. After a few seconds run this command in a terminal. 
```
dmesg | tail
```
Might give a clue as to why this is mounting read-only in first place. (ubuntu mounts disks read-only if there are file system errors).

---

### Post by pympnplaya on 2008-05-02
pympnplaya@pympnplaya-desktop:~$ dmesg | tail
[78604.170805] sd 10:0:0:0: [sdg] Assuming drive cache: write through
[78604.172795] sd 10:0:0:0: [sdg] 39070080 512-byte hardware sectors (20004 MB)
[78604.174544] sd 10:0:0:0: [sdg] Write Protect is off
[78604.174547] sd 10:0:0:0: [sdg] Mode Sense: 0b 00 00 08
[78604.174549] sd 10:0:0:0: [sdg] Assuming drive cache: write through
[78604.174554]  sdg: sdg1
[78604.514397] sd 10:0:0:0: [sdg] Attached SCSI disk
[78604.514471] sd 10:0:0:0: Attached scsi generic sg7 type 0
[78606.059430] ACPI: Unable to turn cooling device [f7c44f18] 'on'
[78612.052308] ACPI: Unable to turn cooling device [f7c44f18] 'on'

---

### Post by pympnplaya on 2008-05-02
nevermind i got it to delete after remounting thanx

---

