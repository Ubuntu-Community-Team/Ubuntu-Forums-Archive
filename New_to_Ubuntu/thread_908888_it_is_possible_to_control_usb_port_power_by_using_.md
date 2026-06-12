---
title: "it is possible to control usb port power by using bash script"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by say2sky on 2008-09-02
I want to sync all contents on internal hdd to 2.5" usb external hdd at set period by using cron. But I hope to power off usb port after finish this sync operation. 

My question is 
How I can power off an usb port by use bash script?
is there a special command to achieve this goal? 

Thanks in advance for help and suggestion.

---

### Post by NESFreak on 2008-09-03
don't know if this works [http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/](http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/)
doesn't unmount powers it down? I believe you could also try some stuff with hdparm

---

### Post by say2sky on 2008-09-03
> **NESFreak said:**
> don't know if this works [http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/](http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/)
doesn't unmount powers it down? I believe you could also try some stuff with hdparm

thanks for your info and I have tried all the related method I can found through google.

here is what I have found after spend some time googling about power control problem for USB port. 

1) a lot of linux user hope to find a way to control USB port's power by using command line(soft power control)
2) until now NO utilities/apps/command can reach the goal to control power to USB port in Linux.
3) for Windows, there are software for USB port power control.
4) there are some people have tries to invent some apps to achieve soft power control for USB port, but no successful info or product can be found.

anyone can find further info or a way to achieve this USB port power will  help a lot of Linux users.

ps. now no matter ide hd or sata hd, 8.04 ubuntu will use /dev/sdx device file as I understand sdparm will be used for hd parameter but not hdparm. hdparm have options for power control but sdparm donot have.

---

