---
title: "Home server hdd setup"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by nikita.shatunov on 2014-10-02
[FONT=arial][COLOR=#333333]So i am trying to build home server for backup/archive purpose. I have older computer that i am using, it has intel core 2 cpu, 2gig of ram and 3 hdds - 3tb (new empty drive), 80gig old drive that i run ubuntu of and 320gigs that is full of old file archive i ran under windows that is ntfs. So i need this server for 3 tasks:[/COLOR]
[/FONT]
[LIST=1]
[*][FONT=arial]Backup for mac with timemachine[/FONT]
[*][FONT=arial]Backup for windows with its own native servcie[/FONT]
[*][FONT=arial]file archive that i can access from mac/windows/samsung smarttv and so on[/FONT]
[/LIST]
[FONT=arial][COLOR=#333333]how should i go about arranging the hard drives? should i have separate partition for all of my tasks or folders will do, what filesystem should i use for each partition? and maybe any other tips for doing this setup.[/COLOR]
[COLOR=#333333]PS i initially wanted to use freeNAS for this type of job but my setup turned out to be too weak for it so i have to go with Ubuntu and setting everything up myself.[/COLOR][/FONT]

---

### Post by mastablasta on 2014-10-03
what drive is the 3Tb one? is it red?

anyway I am in a similar boat. if you do not know how to setup Linux and want to go with Ubuntu I suggest you have a look at Zentyal. Anyway server will need about 4GB disk space to run, the rest is all data space. Ubuntu can read and write to NTFS just fine. how you want to arrange the disk is actually according to your preference. based on advice from some good forum members I plan to do:
partition with data that changes a lot
partition with data that is relatively static

the question remains on how you intend to access the file archive for regular use. what protocol you will use. Windows can connect to Linux via SAMBA, (s)FTP... I don't know the protocols supported by Samsung smart tv. you can install web file manager what you intend to do after accessing the files (just operate them or actually open them - e.g. paly media...).

oh and if you are like me and prefer server with a GUI here are some good ones (besides previously mentioned Zentyal) I've been testing:
- Ajenti (just a nice light gui for server administration)
- Nethserver (based on CentOS, gui for server administration)
- Openmediavault (based on Debian - designed specifically for NAS)
- Clear OS (basically like Zentyal ment for small server only based on CentOS)

also i've been checking own cloud - which seems to be the most advanced free cloud and easiest for setting it up at home. has client for windows, iOS, android...

---

