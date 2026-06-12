---
title: "will reinstalling Windows cause grub problems?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by gamer4lyf3 on 2008-07-16
greetings, I am going to be installing windows XP in replace of my Vista. When I installed Ubuntu I did it through Vista and it like fixed my grub stuff so it was easy to boot into Ubuntu. But When I replace Vista with XP (on the Vista partition) am I going to have a problem with grub since it installed from Vista? Will I be able to still boot into Ubuntu? So I guess basically I'm asking if there are any essential files for Ubuntu on the Vista partition.

---

### Post by bumanie on 2008-07-16
Did you install ubuntu via wubi? If so, get rid of vista, you will get rid of ubuntu. I would suggest you do a dual boot setup after you install xp, if you have found ubuntu to your liking. If it was a dual boot setup already (sorry, your post is not 100% clear on how you setup ubuntu), after the xp install, you will need to reinstall grub via a live cd.

---

### Post by rraj.be on 2008-07-16
When you are reinstalling widow's it will jsut overwrite your ubuntu bootloader and replace it with windows boot loader.

Just what you want is  reinstall GRUB [boot loader]

To reinstall GRUB after installing windows follow the step's.

Boot into live cd

open terminal and type 

```

sudo grub

find /boot/grub/stage1
```

If it returned like (hdx,y)

type ```
root (hdx,y)

setup (hdx)

quit

sudo reboot
```

Thats it.

**EDIT: **As the below poster told you could also see this link to get a good idea regarding dualbooting

[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

---

### Post by niyonk on 2008-07-16
Ofcourse...:rolleyes:

Like you said, you installed it through vista so...you will loose it.

But you can still add it later to XP's boot loader, though.

I haven't tried that, but you might wanna check around the forums for dual-boot between XP and Ubuntu 

or try this [link]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm") or this [one]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm") (depending on the case)

Cheers! :guitar:

---

