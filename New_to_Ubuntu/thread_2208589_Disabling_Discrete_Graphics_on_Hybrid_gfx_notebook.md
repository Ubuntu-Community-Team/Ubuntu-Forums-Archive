---
title: "Disabling Discrete Graphics on Hybrid gfx notebook"
date: 2014-03-01
forum: New to Ubuntu
---

### Post by Nikhil_P on 2014-03-01
First of all i dont know if i need to mention this explicitly here since this is absolute beginners section ,anyway, imma noob and complete beginner.

I switched from windows 7 to ubuntu recently as all i do is web browsing and some research stuff and recent ms hotfixes were making my win system sluggish and slow. So i had to reserach a lot especially so becuase when i tried to dual boot ubuntu and win7 , got hooked up with a LDM bug in grub2 . But thanks to google and huge community support i could get it all solved in no time and got the dual boot setup up and running fine. After spending a few days with ubuntu ive found it to be perfect for all my needs and decided to fomat win partition to free up sapce for movies - surprisingly that bit also went fine.

Now the real problem started when i noticed significantly lesser battery life in ubuntu than in windows, not to mention the lappy was running hotter , even so i was hopeful to get it solved googling and with a bit of digging i found that this was all due to my Discrete Gpu being powered ON all the time and woot the solution was also easy -just install the proprietory driver and get the heck done with .Well my problem is having to download 150mb of amd driver will take up half my day in this part of the world , so had to dig lil deeper and found out the linux kernel feature called vag_switcheroo.

According to many a sites doing 

```
echo > OFF /sys/kernel/debug/vgaswitcheroo/switch
```

will turn off the unused gpu but i am skeptical whether this is a permanent solution - will i have to do this every time i wake my comp from suspend and every restart (which is the case i suppose ) ,if so , any workaround ? . Ive seen many guides mention an acpi module method as the best possible method to turn ON and OFF at user's discrertion - but that method seems way too complex for me to follow .Any pointers on handling this issue avoiding the propreitory drivers are welcome.

Also is there a way i could set a predefined level of brightness every time i start my session as it is always full

Thanks in advance

---

### Post by phidia on 2014-03-03
For setting the brightness see if [this]("http://ubuntuforums.org/showthread.php?t=2156537&highlight=laptop-mode-tools") works for you. Also laptop-mode-tools should be installed for it's other features-if you haven't already.

---

