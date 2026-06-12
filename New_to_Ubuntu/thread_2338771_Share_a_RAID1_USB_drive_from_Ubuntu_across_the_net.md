---
title: "Share a RAID1 USB drive from Ubuntu across the network to windows users?"
date: 2016-10-01
forum: New to Ubuntu
---

### Post by noripsni on 2016-10-01
[SIZE=2][FONT=arial][COLOR=#111111]I am excited about learning the ways of Ubuntu 16.04 LTS! But I've got a few questions and hope to receive some answers. I am completely new to this type of OS, where terminal is used a lot. Bare with me.
[/COLOR]
[COLOR=#111111]My Intention: Use a microPC to share a RAID1 USB stick (2x32GB sticks in RAID1). Why a small amount of space? Well, mainly will be used for documents and small files(Like redirecting my saves from games to this RAID1). Also for my experience! AND this PC doesn't have anymore SATA ports, prebuilt old microPC used in an office.
[/COLOR]
[COLOR=#111111]My Progress: I managed to create the RAID1 myself, pretty proud. WAS NOT EASY I must say, but again, i'm new. I'm able to access the RAID1 in and out, create/delete files. All is well. Now I wanted to share this RAID1 to my network that has windows clients (Windows 8/10). I learned I needed Samba, so I installed it. I also installed the GUI to it as well... This is where it's been a real rocky. Like how Harambe blew up on the internet rattling the foundation of whatever zoo he was in; that kind of rocky. Unimaginable.
[/COLOR]
[COLOR=#111111]My Problem: After messing with so many settings, changing things in the smbd.conf file... I could see the RAID1 via my windows 10 but cannot get into it, permission denied! Then I tried something a bit different, re-installed samba; left everything default; created a folder on the main drive(Where OS is installed); shared the folder; VIOLA, I can access that folder from windows and add/delete files. I do the same with the RAID, nope. I still can't access it, even after adding that RAID1 to the share via the samba GUI.
[/COLOR]
[COLOR=#111111]My Thoughts: I am not sure why this is or how to resolve it. I've been inhaling webpages right off my computer screen. Could it be the RAID1 that's not allowing this?
[/COLOR]
[COLOR=#111111]My Wishes: I'd like to, at least, access the RAID1 from the windows clients. Then i'd like to set a password on the RAID so when a new PC needs access, there would require a password(Not every time you open the directory though). Now that I thought of that, would that affect the way the my games would save to the RAID1? Or would a, "Map to network drive", solve that?[/COLOR]
[/FONT][/SIZE][COLOR=#111111][FONT=Ubuntu][SIZE=2][FONT=arial]I really appreciate all your answers and having read all of this! I've tried sharing through the Samba GUI, did not work. I tried sharing by right clicking and sharing, did not work.
[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by colmax on 2016-10-01
if the usb memstik is flashing it's reading/writing or saying wtf
may not have the space to create raid which normally has inbuilt redundancy in case a drive fails

---

### Post by noripsni on 2016-10-01
Thanks for responding, Colmax. Just got home and saw the drives with no activity, no flashing lights. Now I just started formatting them again. But still no RAID1 showing up on the side. [COLOR=#111111][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by noripsni on 2016-10-02
I got it to work!!!! Using the guide here, [http://travelinlibrarian.info/2013/05/how-to-share-an-external-usb-hard-drive-from-ubuntu-to-a-windows-network/](http://travelinlibrarian.info/2013/05/how-to-share-an-external-usb-hard-drive-from-ubuntu-to-a-windows-network/)
The thing that was throwing me off was the 'force user = <user>', I thought it was the user that I am logged into on ubuntu, which is "Admin". BUT, I saw that the only user in samba was, "root", changed that to root and I now have access. I'm pretty confused how the user is root though. Now I'd like to see how I can setup a password so that would provide more security?

---

### Post by colmax on 2016-10-04
Hey kudos to you noripsni
Admin & root seem to have the same abilities-syntax withstanding
su is temporary metinks
Password protection should be present in your raid install
May be your lead disk

---

