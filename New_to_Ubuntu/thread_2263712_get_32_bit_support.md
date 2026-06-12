---
title: "get 32 bit support"
date: 2015-02-02
forum: New to Ubuntu
---

### Post by Tully_ on 2015-02-02
I am very, very new to ubuntu and i want to download steam but i need 32 bit libraries. ive looked at tutorials online but none have helped me at all, any help would be greatly appreciated.

---

### Post by Tadaen_Sylvermane on 2015-02-02
install steam from the software center. it will do all of that for you.

---

### Post by efflandt on 2015-02-02
Which Ubuntu version? In 64-bit 14.04.1 I installed steam from Software Center and it simply worked. Although, I copied my game files over from 12.04 when I copied my home to fresh 14.04.1 install.

If still running 12.04 (which you probably would not if new to Ubuntu) you might need to install ia32-libs if that is not automatically installed when installing steam from Software Center, but I already had that installed in 12.04 before installing steam beta from a deb file in Jan 2013 before it was released. Many Linux steam games are 32-bit, but some also have 64-bit versions, or some are 64-bit only.

What I am not sure of is whether you still need to put 32-bit flash in (libflashplayer.so from install_flash_player_11_linux.i386.tar.gz from adobe.com) into ~/.local/share/Steam/ubuntu12_32/ in order for videos to work in Steam Store from steam client. Although, if you install flashplugin-installer or ubuntu-restricted-extras, flash should work in firefox at store.steampowered.com.

---

