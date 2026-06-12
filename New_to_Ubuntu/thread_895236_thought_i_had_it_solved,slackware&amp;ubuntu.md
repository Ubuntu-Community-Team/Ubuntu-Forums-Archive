---
title: "thought i had it solved,slackware&amp;ubuntu"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-08-20
ok i installed slackware,and it took over the mbr,and i lost access to ubuntu,so i edited the lilo.conf to include ubuntu.
but it doesnt work,so i got the bright idea to install ubuntu
to my usb hd and i set the grub to /dev/sdb,and again edited
the lilo.conf,to no avail.is there solution to this dilemma?
should i install grub on slack or am i editing the lilo.conf wrong.i can post the lilo.conf if its helpfull.
any help i can get with this would be appreciated.
Rick:(

---

### Post by meanburrito920 on 2008-08-20
If you are running grub, then the file will be /boot/grub/menu.lst

edit that, not lilo.conf.

---

### Post by rixtr66 on 2008-08-20
no slackware uses lilo and thats what im trying to solve,the grub refrence was just an idea to switch slack to grub so i can access my ubuntu,but right now im dealing with lilo,heres what it looks like;

boot=/dev/sda
linear
prompt
timeout=50
root=/dev/sda5

image=/usr/src/linux/arch/i386/boot/bzImage
	label="Linux_Compiled"
	root=/dev/sda5
	read-only
	optional

other=/dev/sda1
	label="NT"

image="/dev/sda1"
	root="/dev/sda5"

other=/dev/sdb
	label="ubuntu"

image="/dev/sdb1"
                root="/dev/sdb"

image= /boot/vmlinuz.old
root=/dev/hda5
label= slack.old
read-only

i dont know if this will help,but the way i have it written doesnt work.
Rick

---

