---
title: "Getting an inf file from a netgear driver exe"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by laurencemulchrone on 2008-04-24
Hey guys.

i have read so many posts about getting inf files from exe's but i just cannot seem to do it....
i have unzip installed as well as cabextract installed.
the file is called **wg111t_2_0_setup.exe** and it is saved on my desktop

could anyone help me, how can i get the inf, im afraid i am still not good with the terminal, i am even unsure how to navigate to a file!

appreciate it!

---

### Post by dark_harmonics on 2008-05-05
I actually used a windows machine to pull out a similar (but not the same or i'd post it) inf file. You can use wine to extract it by executing it with wine at the command line and then extracting it somewhere you can find it. 
In a terminal
```

wine packageddriver.exe

```
Where packageddriver.exe is your self-extractig driver file.

---

### Post by vincent2k8 on 2008-09-26
Don't know whether this is correct or not but I downloaded the Windows .exe driver from Netgear for the WG511T card. Then downloaded and install the wine package (sudo .... something). Once the package is installed correctly, I tried the above suggestion of 'wine wg511t_5_2_setup.exe' and instead of extracting files, the program went through a full Windows Netgear driver and software installation. Now, there's a Netgear Wireless Wizard appeared on my desktop. Funny thing is I don't know whether the card is working because of the 'wine wg511t_5_2_setup.exe' or is it because the WG511T is natively supported by Ubuntu under restricted driver. I know that under System->Administration->Network Tools, I have an IP address assigned to my wireless card ath0 and I can use it but when I click on Configure, the system  tells me that the interface does not exist and to check that it's correctly supported by the system.

---

### Post by silverglade00 on 2008-09-26
Sounds like Wine is getting pretty good! That's pretty cool.

You should be able to find your drivers now in C:\Windows\system32\drivers

---

