---
title: "Too many versions of 8.04! Confusions about GRUB and MBR..."
date: 2008-06-12
forum: New to Ubuntu
---

### Post by agatestnalderman on 2008-06-12
ok slighhhtly different problem,

i have an acer aspire 5315 bundled with an OEM vista.  naturally, i immediately proceeded to load ubuntu 7.10, but could never get the soundcard recognized so i always had to blow through grub and boot to vista.

then i thought i would try the beta 8.04, maybe the sound card and the ALSA drivers would work on this new version but no such luck.

ok now that i saw that 8.04 was out of beta and in the LTS i got excited! i thought wow ok, now it will definitely work and i can use ubuntu again, hooray!

SO i dl in vista and burn onto DVD and to my surprise, it says it can install ubuntu 8.04 STRAIGHT THROUGH VISTA!  how cool, thinks i, so i go ahead and do this BUT now when i turn my laptop on i get grub 8.04 (the beta one) and vista as my options then when i pick vista i get the vista version of grub asking do i want to load vista or ubuntu (the stable LTS one)

My question is, how can i chuck the beta 8.04 off my MBR and delete grub altogether?? (since the stable LTS ubuntu i want to keep seems to load through the vista loader) 

I've backed everything up, i just can't figure out how to get rid of it without making problems....if i just delete the partition then im going to get grub error 22 or whatev( i've had problems with this before :p )

suggestions?

---

### Post by philinux on 2008-06-12
Did you use Wubi or dual boot with partitions?

---

### Post by defrex on 2008-06-12
I've never used Wubi myself, but from what I understand you can 'uninstall' ubuntu as well. I'd say do that, and reinstall it using the live cd into the regular grub menu.

If you really like the wubi version better (keep in mind, ubuntu is a file under windows, not on it's own partition), then boot a live cd, and use gparted to delete the old ubuntu partitions and give the space back to windows. Then run the vista cd and restore the windows MBR, then reinstall from wubi.

Unfortunately both of these options involve nuking your ubuntu installs. I'm just not sure how else to do it.

---

### Post by agatestnalderman on 2008-06-12
no theyre all on seperate partitions, but the new one that i want to keep was previously a NTFS, dont know if the ubuntu install converted it, i think i saw sometihng about  to ext3 during the install....

unfortunately i dont knwo what wubi is.... is that this new thing that allowed ubuntu to load from the vista loader?

when i installed the version i want to keep it was installing through vista like any other normal windoze app installing... but then it went through the normal OS install when i restarted (ive installed and reinstalled MANY times in the past trying get this stupid sound card to work and it finally does!!)... was this wubi?

---

### Post by philinux on 2008-06-12
> **agatestnalderman said:**
> no theyre all on seperate partitions, but the new one that i want to keep was previously a NTFS, dont know if the ubuntu install converted it, i think i saw sometihng about  to ext3 during the install....

unfortunately i dont knwo what wubi is.... is that this new thing that allowed ubuntu to load from the vista loader?

when i installed the version i want to keep it was installing through vista like any other normal windoze app installing... but then it went through the normal OS install when i restarted (ive installed and reinstalled MANY times in the past trying get this stupid sound card to work and it finally does!!)... was this wubi?

If it installed through windows I think so. It will be in Add/Remove software, like any other windows app.

---

### Post by agatestnalderman on 2008-06-12
cool, i was wondering what that was, its a really cool new feature :)

so any ideas about how to get rid of the old ubuntu partition and delete grub then? i like this wubi way better :) btw it's not on the C:/ from vista but on a spare data partition.

i found this code:

sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

to try uninstalling the ubunutu and grub from the non-wubi partition
but it was unsuccessful, said it didnt recognize dd as a command and some other problem.  im still pretty new to linux, is there some code you could help me out with to get rid of this stupid bloat partition and grub altogether without messing up my MBR?

i know if i just delete the old ubuntu partition, grub wont load and the whole chain of normal booting is messed up cause ive made that mistake before :P im a trial and error sort of linux user.... :D

which is why its so fortunate that there exist forums like this to get me out of these sticky situations :)

Thanks guys!

---

