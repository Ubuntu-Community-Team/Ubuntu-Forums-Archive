---
title: "Nightmare recovery"
date: 2018-05-20
forum: New to Ubuntu
---

### Post by rudybaby on 2018-05-20
I was running Ubuntu 17.10 and got a message to upgrade to 18.04. I did the process, but system wouldn't boot up. Tried all sorts of recovery stuff, but nothing worked. Finally, reinstalled from USB 17.04 and upgraded to 17.10. I don't want to go through that again. Can I stick with 17.10 for a while?

---

### Post by deadflowr on 2018-05-20
Why not download a fresh copy of 18.04 and do a test run? (Do the Try Ubuntu option)
If it runs fine,  Backup the existing system and then install the new one fresh.
Then restore your backups.

You have until sometime in July when 17.10 goes lights out.

---

### Post by rudybaby on 2018-05-20
I see 18.04 is 64 bit. Will this run on a 32 bit machine?

---

### Post by deadflowr on 2018-05-20
> I see 18.04 is 64 bit. Will this run on a 32 bit machine?
No. 
Ubuntu stopped making 32-bit versions, but afaict only Ubuntu stopped.
I think all the official flavors still do 32-bit versions.
[https://www.ubuntu.com/download/flavours]("https://www.ubuntu.com/download/flavours")
If you need 32-bit then you might want a light desktop like Lubuntu or Xubuntu, imo.

---

### Post by Geoffrey_Arndt on 2018-05-20
No . . it requires 64 bit hardware, but,  Ubuntu Mate has some excellent features and a top notch development team.   Fully supports 32 bit machines till 2021  on LTS (18.04).   But 32 bit after 2021 may require some _**non-ubuntu distros**_ such as MX Linux.

For Mate:   [https://ubuntu-mate.org/download/index.html](https://ubuntu-mate.org/download/index.html)

For MX-Linux:   [https://mxlinux.org/](https://mxlinux.org/)

---

### Post by rudybaby on 2018-05-20
I'm going to try MATE 32 bit and see if it works. Thank you. Never ran MATE, so that will be new to me also. I hope a quick learning curve.

---

### Post by rudybaby on 2018-05-20
Okay, so it worked BUT I'm missing any toolbars or launchers. I can hit alt F1 and get a menu but there should be a top toolbar, no? where on that Alt F1 menu would toolbars be?

---

### Post by oldfred on 2018-05-20
What system do you have?
Almost all systems in last 10 years are really 64 bit.
A few very lightweight systems have 32 bit UEFI with 64 bit system.
Or very old system may be 32 bit, but then you do not want Ubuntu but one of the lightweight flavors.
       Light weight flavors
Lubuntu, xubuntu, Ubuntu mate, Budgie 
      
 [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by rudybaby on 2018-05-20
I was running regular Ubuntu just fine for months until it asked to upgrade to 18.04. After that nothing has worked right. I figured I would try MATE. The desktop is there but no panel on top, bottom or sides. Would be fine if I had a panel.

---

### Post by rudybaby on 2018-05-20
My processor is 32bit i5-2390T

---

### Post by Dennis N on 2018-05-20
> **rudybaby said:**
> My processor is 32bit i5-2390T
According to Intel, that is a 64-bit processor:
[https://ark.intel.com/products/53448/Intel-Core-i5-2390T-Processor-3M-Cache-up-to-3_50-GHz](https://ark.intel.com/products/53448/Intel-Core-i5-2390T-Processor-3M-Cache-up-to-3_50-GHz)
So Ubuntu 18.04 can work.

---

### Post by rudybaby on 2018-05-20
I see that. This is very frustrating. I had Ubuntu 17.10 working for a long time, then after the upgrade to 18.04 it screwed up everything. Should I try MATE 64 bit? 18.04 Ubuntu didn't work. It got to the Aadvark logo and froze there.

---

### Post by oldfred on 2018-05-20
Then what video card, or are you using the internal Intel video?
Have you updated UEFI?
Both UEFI & kernels have to be updated for Meltdown and Spectre CPU vulnerabilities.

---

### Post by mörgæs on 2018-05-21
I know it's not relevant for your processor but just for completeness:

Ubuntu 18.04 32 bit still exists! It's only the ISO providing the live boot that was shut down.

Installation is done from the minimal ISO.

---

### Post by rudybaby on 2018-05-21
What is the command to look at the hardware and system info?

---

### Post by oldfred on 2018-05-21
system info
 sudo lshw  

save as a file:
      If using sudo, run any sudo command like ls first. Sometimes sudo & redirect have issues.
sudo ls
File will be saved in your home folder
To save it as a file use
sudo lshw > hw.txt 

    You also can use parameters to get just details on what you want.
      To see drives:
sudo lshw -C Disk -short 
    
Various commands, use man to see options:


[LIST]
[*]lspci    * lsusb    * dmesg    * lshw    * dmidecode 
[/LIST]

---

