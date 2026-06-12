---
title: "Moving from Window to Ubuntu"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by Luc_Nadon on 2014-03-03
I've been away from the Linux/Unix world for a long time, I've delved into the Windows world for over 15 years and now I'd like to come back. I decided to start with Ubuntu because of it's user community. I would like to setup a Ubuntu system similar to my windows system. I'm not afraid to search for information, to try things and blow installation away and start fresh. I just need a direction.

Currently setup in my windows environment is an Active Directory Domain with 5 workstations and 2 servers (F&P, Web & Database). I know that I can put LDAP on Ubuntu but that sounds like a "Band-Aid" solution. In essence what I'm looking so that when I log onto a Ubuntu workstation, all my permissions are the same throughout the network (kind of like AD for windows).

I might be somewhat of a newb in Ubuntu, but I know and understand the concepts behind networking, Web servers, databases and know how to search the Ubuntu community to get what I want, but can't find out the best method to switch over from windows.

---

### Post by GrouchyGaijin on 2014-03-03
This is probably a huge oversimlification but if you mean share files you could do that with Dropbox shared between all the computers on the network.
As for browsing history, passwords etc. Chromium and Firefox both have sync options.

---

### Post by Linuxratty on 2014-03-03
> **GrouchyGaijin said:**
> 
As for browsing history, passwords etc. Chromium and Firefox both have sync options.

Fire Fox is improving their sync so it will be easier to use.It's being tested now.
 You can put pictures and such on a thumb drive and then either duel boot or do as i did,install over Windows.

---

### Post by zircon_34 on 2014-03-03
I'm not an expert on that, but its fairly simple to install a samba server using Ubuntu as well as adding users and managing permissions. You basically can install samba via terminal using one command line, same for adding a user etc... I used that for sharing files between my different computers at home, windows and linux.

You can download Ubuntu 13.10 for your workstations and Ubuntu server for your server if you do not need a GUI on the server. I don't think it matters which Ubuntu you download as you can install the packages you want latter on to build up your linux box as you want. It just depends what desktop environment you prefer. Since I am fairly new with linux maybe somebody can comment on that?

It sound to me you were using windows XP, I heard that people recommend LUbuntu to switch from windows XP, but I can recommend to try maybe Ubuntu (Unity), KUbuntu and XUbuntu using live USB and then you choose the one distro that is most intuitive for you. Hope that helps

---

