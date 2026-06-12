---
title: "Lubuntu/Ubuntu dual boot"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by cwejg on 2013-11-05
Hello, I installed Lubuntu duel boot with Ubuntu 12.04. Everything went OK but when I rebooted there was no option to which program to use, it just started in Lubuntu. I still have all of my files but just can't see how to start Ubuntu.

Thanks for your help.
Chuck

---

### Post by mastablasta on 2013-11-05
when you login you should be able to choose desktop type, if you choose unity or something like that you will get back into ubuntu. 

or if you really did a separate Lubuntu install then hold shift immediatelly on boot for grub to show up and then choose Ubuntu there.

---

### Post by cwejg on 2013-11-06
> **mastablasta said:**
> when you login you should be able to choose desktop type, if you choose unity or something like that you will get back into ubuntu. 

or if you really did a separate Lubuntu install then hold shift immediatelly on boot for grub to show up and then choose Ubuntu there.


Thanks I hold the shift and just for an instant I see Grub loading but and error on the screen wipes it out saying to change the video to 1280 X 1024 and that is what it's set for but it doesn't seem to reconize it and the error box wipes out the grub menu. I can change it to 800 X 600 and it does but goes back to 1280 X 1024 on a reboot. Bad video card maybe?

Thanks,
 Chuck

---

### Post by sudodus on 2013-11-06
You can change it persistently according to these links

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions](https://help.ubuntu.com/community/Grub2/Displays#Changing_Menu_Resolutions)

Change in the file [FONT=courier new]**/etc/default/grub**[/FONT]

```
sudo nano /etc/default/grub
```

Example: GRUB_GFXMODE=800x600

Save the changed file and remember to run

```
sudo update-grub
```

---

