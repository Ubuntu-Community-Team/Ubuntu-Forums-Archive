---
title: "Samba Woes"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by MikeyPooh on 2008-10-04
Hello Everyone,
 
              I Have Installed Ubuntu Server 8.04, 
PC Specs
********
Intel P4 3.4GHZ
1.5GB Ram
Sony DVDRW/DL
Liteon Dvdrom
Drive 1 = Maxtor 200GB
Drive 2 = Maxtor 200GB
Drive 3 = Maxtor 200GB
Drive 4 = WD 250GB

First Drive is Partitioned As Follows

80GB /
10GB Swap
Remaining Space /media/software-photos

Drive 2 = /media/Music
Drive 3 = /media/Video
Drive 4 = /media/Movies


i cannot for the life of me figure out how to get the drives setup in samba so they can be seen from My Other 2 Windows XP Boxes, I Have Read All OF The Samba Docs And Cannot Figure It Out:(

Any Advice Would Be Greatly Appreciated:D

                   Thanks

                    Mike

---

### Post by linux6994 on 2008-10-04
Easy way to do it is to install system-config-samba and use it to add shares and change server settings to share. Look at the attached files.

Once it is installed it will be under System > Administration > Samba

Good Luck1

---

### Post by MikeyPooh on 2008-10-04
Thank You For Replying, I am Running Server not Desktop so there is no X Enviorment

        Thanks

         Mike

---

