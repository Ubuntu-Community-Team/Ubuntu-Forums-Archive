---
title: "Need help with a terminal command"
date: 2012-12-05
forum: New to Ubuntu
---

### Post by Seadevil on 2012-12-05
I found a Brother printer driver installer & the instructions said to enter the following command in terminal:

Su Command: gunzip linux-br-printer-installer-1.0.0-1.gz

I entered this in the dir with the installer file. But I 

get  "UNKOWN ID: Command

I made command all lowercase, tried without the colon, but

same error message.

what is wrong with the command ?

---

### Post by steeldriver on 2012-12-05
I don't think the 'Su command:' part is meant to be taken literally - just

```
gunzip linux-br-printer-installer-1.0.0-1.gz
```There should be no need to use elevated permissions unless you are unzipping directly in a system directory - if you are, then the correct way in Ubuntu would use 'sudo' not 'su' anyway

```
**sudo **gunzip linux-br-printer-installer-1.0.0-1.gz
```

---

### Post by williejones on 2012-12-05
> **Seadevil said:**
> I found a Brother printer driver installer & the instructions said to enter the following command in terminal:

Su Command: gunzip linux-br-printer-installer-1.0.0-1.gz

I entered this in the dir with the installer file. But I 

get  "UNKOWN ID: Command

I made command all lowercase, tried without the colon, but

same error message.

what is wrong with the command ?

The su is to switch you to the sudo (administrator) command.  So in a terminal cd to the directory with the driver and enter su.  This will prompt you to enter your password.  Then run the rest of the install, type in gunzip linux-br-printer-installer-1.0.0-1.gz

---

### Post by Seadevil on 2012-12-05
thank you all VERY much.  If he put Command: in parentheses, i would have understood that was NOT part of the command. lol.

---

