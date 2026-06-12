---
title: "dual-boot: problem grub-bootloader"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Stefanie on 2008-04-24
I don't know if this is the right forum to post this, but i've got a dual-boot problem. A couple of days ago I installed Ubuntu in dual-boot with Windows XP. The installation was succesful, but there is a problem with the grub bootloader. Every time after I shut down Windows and restart the pc, the bootloader fails and my computer won't startup anymore (infinite startup loop). The only solution is to use the ubuntu livecd to repair Grub, but i'd rather not do this every time after I used windows. the problem does not occur with ubuntu (when i shut down ubuntu the computer restarts normally).

Is this problem related to grub or to windows and how can i solve it?

---

### Post by artir on 2008-04-24
That seems to be related to Windows.

---

### Post by prshah on 2008-04-24
> **Stefanie said:**
>  Every time after I shut down Windows and restart the pc, the bootloader fails and my computer won't startup anymore (infinite startup loop). the problem does not occur with ubuntu (when i shut down ubuntu the computer restarts normally).
Is this problem related to grub or to windows and how can i solve it?

Looks like a windows antivirus program is, in it's own misguided way, trying to repair an "unauthorized" change to the MBR.

To confirm, disable your antivirus in Windows (you may want to disconnect from the Internet before this action), restart, you may/will run into GRUB troubles, repair, then again start Windows, then shutdown normally and restart again, then see if you get the GRUB problems again.

If you don't, post the name of the antivirus product you are using, and someone can tell you how to disable boot-sector checking. Or alternately, you may just need to "re-inoculate" the boot sector, ie, tell the anti-virus that the current boot sector is fine and dont mess with it until you detect another change.

---

### Post by king2007 on 2008-04-24
> **prshah said:**
> Looks like a windows antivirus program is, in it's own misguided way, trying to repair an "unauthorized" change to the MBR.
To confirm, disable your antivirus in Windows (you may want to disconnect from the Internet before this action), restart, you may/will run into GRUB troubles, repair, then again start Windows, then shutdown normally and restart again, then see if you get the GRUB problems again.
If you don't, post the name of the antivirus product you are using, and someone can tell you how to disable boot-sector checking. Or alternately, you may just need to "re-inoculate" the boot sector, ie, tell the anti-virus that the current boot sector is fine and dont mess with it until you detect another change.

To say the same as Stefanie, windows vista "repairs" the master boot record - so tell us please how to proceed ? 1) recognize under windows the disc where ubuntu was installed 2) how to open a terminal-window to enter commands on the command line ? 3) upon restarting windows has  disabled the GRUB and denies ubuntu can be started ! 4) re-installing either gutsy gibbon or hardy heron does NOT solve the problem

---

### Post by Stefanie on 2008-04-24
> **prshah said:**
> Looks like a windows antivirus program is, in it's own misguided way, trying to repair an "unauthorized" change to the MBR.

To confirm, disable your antivirus in Windows (you may want to disconnect from the Internet before this action), restart, you may/will run into GRUB troubles, repair, then again start Windows, then shutdown normally and restart again, then see if you get the GRUB problems again.

If you don't, post the name of the antivirus product you are using, and someone can tell you how to disable boot-sector checking. Or alternately, you may just need to "re-inoculate" the boot sector, ie, tell the anti-virus that the current boot sector is fine and dont mess with it until you detect another change.

thank you, disabling my virus scanner solved the problem. i use AVG 7.4, how should i configure it to stop it from checking the boot-sector? 

@king: you should use the liveCD to start Ubuntu, open a terminal and type:

```
sudo grub
root (hd0,2)
setup (hdO)
quit
```
this will repair grub. note that the number after hd0, depends on the partition where you installed grub and ubuntu

---

### Post by Stefanie on 2008-04-24
problem solved, thanks a lot prshah! 
i did a quick virus scan with AVG and it warned me about the changed mbr. i just confirmed the changes and the problems are finally over :-)

---

### Post by WitchCraft on 2008-05-04
> **king2007 said:**
> To say the same as Stefanie, windows vista "repairs" the master boot record - so tell us please how to proceed ? 1) recognize under windows the disc where ubuntu was installed 2) how to open a terminal-window to enter commands on the command line ? 3) upon restarting windows has  disabled the GRUB and denies ubuntu can be started ! 4) re-installing either gutsy gibbon or hardy heron does NOT solve the problem

You could use the Windows Vista Bootloader instead.
You can download a free tool called EasyBCD, to add a Linux partition to your Vista bootloader. It works flawlessly for me, I tripple boot Visa/XP/Linux

---

### Post by king2007 on 2008-05-04
thanks stefanie and WitchCraft i have tried both, but still do not succeed in
running ubuntu - i still can not boot = how can i chqnge this keyboqrd ? 
correctly using the live CD i can get into alt-f2 but entering commands does not help - with easybcd i was able to delete 2 incorrect entries, but for example booting with supergrubdisc i have lots of errors :(

---

### Post by king2007 on 2008-05-04
at my wit's end girls and boys i decided to insert the linux starter again gutsy gibbon 7.10 and guess what ? 
i am downloading now at this very moment 1027 files i.e. an upgrade to hardy heron 8.04 !! i cannot believe my eyes and i should go to bed actually but this is very exciting .... see you soon with the upgraded version !!

---

