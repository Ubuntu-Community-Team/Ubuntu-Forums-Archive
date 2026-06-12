---
title: "Newbie: Using Ubuntu on Media Server/Backup"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by plusman on 2008-05-31
I'm hoping that some of the Ubuntu experts on this forum might be able to help me. Apologies in advance for the length of this post and the number of questions.

I have a small home network based around Windows XP, and have just bought a small server (HP Proliant ML115, 1.8GHz Dual Core AMD Opteron, 1GB RAM) which I want to use for a number of purposes:

1. As a store for all my media files (photos, music, etc) which currently reside on my Windows XP PC's.

2. As a server to stream music & video to my other PC's and to multimedia devices such as a Roku Soundbridge (which currently access my media using Windows Media Player, iTunes or Firefly).

3. As a backup for my key data (Word files, etc). Ideally I would also like to be able to access this from any PC/laptop on my network. (I also plan to run my server in a RAID format with the same data duplicated on 2 X 1Tb HDDs stored in the server)

4. to use as a way of downloading torrent files (currently I use Azureus running under XP).

My network is a mixed wired/wireless network consisting mainly of XP-based PC's and laptops but with an Apple Mac (OS 10), a few Roku soundbridges, a Wii and a PS3 thrown in for good measure.

I am interested in using Ubuntu as the operating system for my server, but currently have no experience of this OS. Can anybody help me with the following?

1. Should I use the server or desktop version of Ubuntu? 

2. Will I be able to access my files in their "native" format from my windows PC's (i.e. can I just cut/paste and open files to/from the server and my PC's, or will they be stored in a different formt under Ubuntu?, 

3. What would be the best media server to use to pipe media (mainly music) around my system and to the Roku. 

4. I currently use Acronis True Image 11 as my backup programme (again running under XP). I assume that I can continue to use this to backup all or part of my PC's systems onto to the Ubuntu-based server?

5. What would be the best firewall and antivirus to use on the server? (I currently use Comodo and Avast as my firewall/AV on my XP PC's).


Many thanks in advance for your help.

---

### Post by quelx on 2008-05-31
> 1. As a store for all my media files (photos, music, etc) which currently reside on my Windows XP PC's.

**samba** : [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> 2. As a server to stream music & video to my other PC's and to multimedia devices such as a Roku Soundbridge (which currently access my media using Windows Media Player, iTunes or Firefly).

check out **mt-daap** for the audio, for video I personally just use the samba shares.

> 3. As a backup for my key data (Word files, etc). Ideally I would also like to be able to access this from any PC/laptop on my network. (I also plan to run my server in a RAID format with the same data duplicated on 2 X 1Tb HDDs stored in the server)

**samba** again

> 4. to use as a way of downloading torrent files (currently I use Azureus running under XP).

**azureus** runs in Linux also. for me, I created a virtual machine (**vmware-server**) on my server with a gui to do this.

> 4. I currently use Acronis True Image 11 as my backup programme (again running under XP). I assume that I can continue to use this to backup all or part of my PC's systems onto to the Ubuntu-based server

**Samba** again, I beleive acronis can image over the network to windows shares...

> 5. What would be the best firewall and antivirus to use on the server? (I currently use Comodo and Avast as my firewall/AV on my XP PC's).

**iptables**/**ufw** for the firewall (you should check out **webmin** also for all the server management)

the server itself doesn't need virus protection, however **clamav** can be setup to scan the samba shares to protect the windows machines

---

### Post by anjilslaire on 2008-05-31
1. Desktop is fine. You'll have a GUI, and nothing you're needing really requires server apps.

2. Yes, storing files doesn't change their format. Use SAMBA to share your directories

3. Again, use samba to just share your music folders

4.Acronis running from your XP systems? As long as you enable the ability to write to the samba shares, you should be OK. If you mean doing backups on the ubuntu server, there are a variety of backup applications native to linux.

5. All ports are not enabled by default in Ubuntu, but you can run Firestarter from the repositories for free. AV is also not generally needed, but you can get ClamAV from the repositories for free as well.

I have all of my media stored on my ubuntu desktop that I stream/share to my network, including 2 xboxes, and it works perfectly.

---

### Post by plusman on 2008-06-02
Many thanks for the suggestions. I've downloaded the relevant files and will start loading them when I install the HDD's in my system. 

No doubt I'll be back for more help as the installation proceeds.....


Cheers

---

