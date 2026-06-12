---
title: "[SOLVED] gnome panel both gone - hardy 8.04"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by trigsenior on 2008-05-18
hello,

I have had ubuntu 8.04 working on my laptop with gnome for a couple days , when for no  apparent reason both my panels disapeared =(

i have tryed this commands


sudo dpkg-reconfigur gnome-panel
gnome-panel is broken or not fully installed 

what should i do ? 

this is what i was planning on doing 

apt-get remove gnome-panel
apt-get install gnome-panel

is this a good idea ?

thanxs for your help

---

### Post by N.N. on 2008-05-18
Did you install a new applet recently? That could possibly have broken gnome-panel. Which error messages do you get when you run gnome-panel from the terminal?

You can include the -s flag with apt-get to perform a simulation of an action. Try doing ```
sudo apt-get -s remove gnome-panel
``` and see what gets removed along with the panel. It seems safe to remove gnome-panel and then reinstall it.

---

### Post by trigsenior on 2008-05-18
thanxs for fast reply 
it says gnome-panel is not installed .. weird 
before this happened the only thing i did was remove evolution mail mabey i uninstalled gnome panel but i don t see how.

shall i just install gnome panel  again ?

update 

i ran 

sudo apt-get -s remove gnome-panel

package gnome-panel is not installed, so not removed.
the following packages were automaticly installed and are no longer required :
tremulous-data

---

### Post by N.N. on 2008-05-18
The removal of evolution could be the cause of the problem. I don't know why it breaks the panel, but I once assisted another user with a similar problem who deduced as follows: > **brydong said:**
> I believe I know how I messed up and caused this though...Based on advice here, [http://ubuntuforums.org/showthread.php?t=688687&highlight=menu+bars+disappear+gnome](http://ubuntuforums.org/showthread.php?t=688687&highlight=menu+bars+disappear+gnome)

I put those dirs back in place and I'm reinstalling ubuntu-desktop. Based on the packages I'm seeing pulled down, I'm pretty sure I caused this when I removed some evolution packages. I didn't realize they were required for gnome and panel menus. Once this is done I'll try gnome again and hopefully I'm back in business.

Perhaps it's a bug. Anyway, try installing gnome-panel again. If that doesn't solve the problem, install the ubuntu-desktop package again.

---

### Post by trigsenior on 2008-05-18
thanxs for spending you time helping N.N i reinstalled gnome panel and it all works now :)

:guitar:

---

### Post by N.N. on 2008-05-18
> **trigsenior said:**
> thanxs for spending you time helping N.N i reinstalled gnome panel and it all works now :)

:guitar:

You're welcome. Glad I could help. :)

---

