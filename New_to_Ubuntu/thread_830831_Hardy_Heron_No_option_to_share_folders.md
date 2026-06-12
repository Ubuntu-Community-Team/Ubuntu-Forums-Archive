---
title: "Hardy Heron_No option to share folders"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by the_trooper47 on 2008-06-16
Hi All!    
        i'm only new to linux/xubuntu, but i've managed to install xubuntu & am able to surf the net. Major problem is I cannot share a folder. If i right click on a folder (e.g. /home/music) there's no option for "sharing". I've checked in "Synaptics" & samba server is already installed, thinking it wasnt installed properly i uninstalled it, restarted & re-installed samba. Trying this again to share the folderrr but i couldnt make it happen. After clicking on "network" & while trying to configure a box come up & said I dont have this option installed, both options were then ticked but it wouldnt work even after entering my password, it would simply return to the same pop up box every 1-2 mins or so asking for me to do the same thing again, only option was to close or continue. Is this a bug with xubuntu hardy heron 8.04 or am i missing a step or 2 or 3?  :)

Cheers,

 Jim.

:guitar:

---

### Post by dizee on 2008-06-16
Have you tried adding the folders you want to share in the Shared Folders option in the menu under System?

Xfce's file browser Thunar doesn't support network shares as far as I understand but it can be made work.

---

### Post by Dani Filth on 2008-06-16
As far as I know, the Xubuntu default browser Thunar doesn't support file sharing, if you are experienced user and know how to deal with the *buntu distros then search google for a solution to share folders for Xubuntu. Or else, I'd prefer installing Nautilus then use Samba or install Smb4k then use Konqueror to share.

Hope this helps :D

---

### Post by the_trooper47 on 2008-06-17
Thanks Dani, i'm d.loading Nautilus now & will try it with samba. For the previous post from Dizee (thanks also) i had already tried that but it wouldnt work!  Will let ya's know how i go!  :-)

---

### Post by hyper_ch on 2008-06-17
or you could just setup the sharing in the /etc/samba/smb.conf file.

---

