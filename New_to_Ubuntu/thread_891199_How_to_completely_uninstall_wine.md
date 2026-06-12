---
title: "How to completely uninstall wine?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-08-15
So I read an article about Fireworks 8 running under Wine and I thought i would try, seeing as I couldnt find my CD i downloaded a demo of Fireworks from a rather unsafe source, and installed it, I now fear I might have installed a virus, I want to completely remove wine so there is no place for it to hide, then I will reinstall wine and fireworks with my cd.

So my question is how do I completely uninstall wine? 

I installed it in Synaptic and uninstalled it with completely remove, but there is still the folder in my applications menu that says wine and under it macromedia, then Fireworks, but if I click on it it doesnt load.

Do I need to completely uninstall wine or am I safe from viruses as is?

is there any other steps I should take to make sure my pc is clean?

thanks,
abe

---

### Post by penguinbreath on 2008-08-15
Maybe you could try:

```
sudo apt-get remove wine --purge
```

I cannot offer any information about viruses when it comes to Ubuntu, as I do not know how they work inside WINE/Ubuntu.

Edit:

[http://www.winehq.org/pipermail/wine-users/2005-January/016730.html](http://www.winehq.org/pipermail/wine-users/2005-January/016730.html)

---

### Post by abeisgreat on 2008-08-15
I tried that, and wine seems to be gone, and I deleted the item in the menu, any other info on wine and viruses will be appreciated though


Edit: when I reinstalled wine the menu in my applications menu doesn't appear, what do i do?

---

### Post by fiestytom on 2008-08-15
Maybe you could try to delete the .wine directory in your home folder (Make sure "show hidden files" is checked), then try reinstalling wine...

If all else fails, you could just install virtualbox and install windows as a virtual machine

---

### Post by peruvianfreak250 on 2008-08-15
> **abeisgreat said:**
> I tried that, and wine seems to be gone, and I deleted the item in the menu, any other info on wine and viruses will be appreciated though


Edit: when I reinstalled wine the menu in my applications menu doesn't appear, what do i do?

try this

> sudo apt-get --purge remove wine
then

> sudo rm -r /home/username/.config/menus


then 
> killall gnome-panel
then restart

that worked for me

---

### Post by peruvianfreak250 on 2008-08-15
oh and remember to change "username" to whatever your username is

---

### Post by asmoore82 on 2008-08-15
unless you've seriously mangled your system configuration before the Wine ordeal,
you have very little to worry about in the way of "uninstalling" Wine...
since your user account could never change any files outside of your home directory :KS

sounds like you just need to nuke your ".wine" folder in your HOME directory:
```
rm -rf ~/.wine
```

---

