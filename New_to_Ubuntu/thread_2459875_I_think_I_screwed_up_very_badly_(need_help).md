---
title: "I think I screwed up very badly (need help)"
date: 2021-03-28
forum: New to Ubuntu
---

### Post by lelolelo on 2021-03-28
I was playing around with Linux then I had the brilliant idea of stopping gdm service just to see what happens (I thought I would have to log in manually via CLI) so I went
systemctl disable gdm
systemctl stop gdm
Then I saw a black screen of terror and rebooted thinking I would have to log in manually via CLI but no. It doesn't even load a CLI. My Ubuntu broke. Is it over or is it still possible to make it work again?

---

### Post by CatKiller on 2021-03-28
I'd imagine that either booting to a root terminal from the Grub menu, or booting from a live USB and using a chroot, would work fine for re-enabling it.

---

### Post by Holger_Gehrke on 2021-03-28
Just a stupid idea, but have you tried to switch to another virtual terminal (ctrl-alt-F1 to ctrl-alt-F7) ? AFAIK in modern Ubuntu the display manager runs in a specific VT (number 1, I think), the GUI runs in another after log in and there should be login prompts on the other virtual terminals. So if the system goes to the VT where the display manager would be if you hadn't stopped and disabled it you should see a black screen, but the other terminals should be there and allow you to log in.

Holger

---

### Post by guiverc on 2021-03-28
We have no idea what OS & release you're using.

On my own system, I'd expect no consequences, the service is 'inactive (dead)' now as I use another DM anyway.

Given I don't know your release, I'd have expected switching to a text terminal (eg. ctrl+alt+F4) would have allowed text login; did you try?  (Catkiller's suggestion of booting to runlevel 1 is what I'd try next if that failed)

---

### Post by grahammechanical on 2021-03-28
To anyone reading this thread and tempted to learn by experimenting, please do it on a second install of Linux/Ubuntu that you do not mind do a re-install with. Please do not do it on your daily work system.

We all learn from our mistakes. Better to learn from the mistakes of others. :)

This might have something useful.

[https://help.gnome.org/admin/gdm/stable/](https://help.gnome.org/admin/gdm/stable/)

Regards

---

### Post by MartyBuntu on 2021-03-28
...or have a recent and reliable backup, preferably a full disk image that can be restored relatively quickly.

---

### Post by lelolelo on 2021-03-28
Thanks for all the replies. I was able to access the terminal with the CTRL + ALT + F2 - F6 keys and I decided to install sddm and plasma desktop to give it a second chance. Its all working again, thanks!

---

