---
title: "Ubuntu crash"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by MrKappa on 2012-08-23
I have started to have several system crashes on my Ubuntu and I cannot understand the reason. 
I did  a memory test from live cd and I found no issue
When crashes i see no high RAM use o specific application, the machine just crash and I cannot operare. Keyboard leds starts flashing and the HDD LED show that the HDD has still some activity. I add my dsmeg hoping somebody can help me with suggestions. Thanks

---

### Post by Bashing-om on 2012-08-23
mrkappa; welcome.

 My apologies for my delay in responding to your request. It was my desire that one of greater expertize than I handle this. But ....

 Looking at your dmesg it is obvious that sda7 has problems. There are two things required at this time. 
1. run a smart mon test on the disk drive from the disk utility. Suggest to do the full test even though it takes no little matter of time.
2. check the integrity of the file system .. a quick way to look for a problem is to reboot system with a forced file system check: 
  from the command line:
```
sudo touch /forcefsck 
```
Which will check the file system on the next boot.
reboot now:
```
sudo shutdown -r now
```
  Then check the dmesg file for errors.

At this point we may want to run the system file checker for deeper analysis.

[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by MrKappa on 2012-08-24
Many thanks for your kindness for supporting me for this issue. 
It seems that you was right! I have checked the disk from a linux live cd and also ran the "sudo touch /forcefsck" from ubuntu. 
For the moment it's running fine and I have no trace of sda7 errors on my dsmeg for now. 
It was very interesting for me to learn a little bit more about this log investigation. I will monitor from now to see how will work in the next days. 
Thanks again!!

---

### Post by Bashing-om on 2012-08-24
mrkappa;
   
  That is great... good news!// However, I still suggest that the disk device be checked/verified by the on-board disk utility (smart mon is real smart in checking your disk for failure.) It has relieved me of much anxiety.

 Reading your logs from time-to-time is always a good practice.

  kindly regarding <==BDQ

---

### Post by MrKappa on 2012-08-25
Hello' Bashing-om,
I have no experience with smart mon until now but I will search the necessary information as tutorial and "how to". I will follow your advice.
So far my pc is running perfectly again!
Thank you.

---

### Post by Bashing-om on 2012-08-25
MrKappa;


 on my 10.04 system the smart mon is system=>administration=>disk utility,
on the left side is a list of devices; choose the device of interest, on the right side will appear a larger assortment of options for this device, choose SMART Data /view SMART data and run self test/ from this pop-up screen choose "Run Self-test.


[LIST]
[*]HTH <==BDQ
[/LIST]

---

### Post by MrKappa on 2012-08-26
> **Bashing-om said:**
> MrKappa;


 on my 10.04 system the smart mon is system=>administration=>disk utility,
on the left side is a list of devices; choose the device of interest, on the right side will appear a larger assortment of options for this device, choose SMART Data /view SMART data and run self test/ from this pop-up screen choose "Run Self-test.


[LIST]
[*]HTH <==BDQ
[/LIST]

Perfect. I have used it already. On ubuntu 12.04 I can launch from terminal writing: palimpsest. Thanks

---

### Post by Bashing-om on 2012-08-26
MrKappa;
 Great! you do good work.

  If you are satisfied... please mark this thread solved ...to aide others in seeking their solution.


[INDENT]smiles <==BDQ

[/INDENT]

---

