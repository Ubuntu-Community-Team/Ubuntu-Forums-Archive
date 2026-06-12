---
title: "Installing Brother HL-6050 Laser Printer"
date: 2005-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by stevho on 2005-12-30
I have just successfully installed the HL-6050, both the Non-PostScript CUPS drivers and the PostScript (Brother 'BR-Script3') PPD.

Brother are quite good at supplying Linux drivers, but as is often the case, the generic Debian drivers and instructions don't install exactly the same in Ubuntu.

This is what I did to install the Brother LPR Driver v1.1.2-1 and HL6050 CUPS Wrapper v1.0.2-1 in Ubuntu 5.10.

1. Download LPR and CUPS Wrapper drivers from [http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html)
2. sudo mkdir /var/spool/lpd  
3. sudo mkdir /var/spool/lpd/HL6050  
4. sudo ln -s /etc/init.d/cupsys /etc/init.d/lpd  
This is a temporary link for the install only. It might not be necessary, but was suggested so I did it.
5. Synaptic > Install csh (doesn't work properly without!)
6. cd to dir containing drivers.
According to Brother installation notes, any messages aboutLPD/LPRng can be ignored, though I didn't get any.
7. sudo dpkg -i --force-all ./hl6050lpr*  
8. sudo dpkg -i --force-all ./cupswrapper*  
9. rm /etc/init.d/lpd  (remove temp link)
10. This should now have created the printer 'HL-6050-for-CUPS' as a local printer. You can try assigning a port and printing a test page, but it didn't work for me (as network printer on Lindy print server) with this first (driver-added) printer. I deleted this and installed a new printer:-
Add New Printer > Network Printer > UNIX (LPD) > Prt Svr IP and Queue > Brother > Driver > HL-6050-for-CUPS > Apply.
General tab > Print Test Page > Yes!

---

