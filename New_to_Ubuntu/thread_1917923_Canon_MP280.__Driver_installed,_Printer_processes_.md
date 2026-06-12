---
title: "Canon MP280.  Driver installed, Printer processes document, does not print"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Me887799 on 2012-01-30
I have a Canon MP280 printer ([http://tinyurl.com/2cn55qx](http://tinyurl.com/2cn55qx)) with drivers installed via the software manager.

Printer is found to be installed, and is available in printers under system settings, though when trying to print, the printer reports that it has processed, printed, and completed but does not actually print anything.

I have tried to install linux Canon drivers through the foreign Canon site, but it does not locate the printer.  Additionally, in a last ditch effort, I have tried to install printers via WINE but no go.

I am currently operating Ubuntu 11.1.  
Any help to resolve this issue would be much appreciated.  I would not like to dual boot only to print.

---

### Post by bluexrider on 2012-01-31
Linux driver support here for the Pixma MP280

You will need to compile the driver but here is the source. [http://support-asia.canon-asia.com/contents/ASIA/EN/0100302002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100302002.html)

Here is another list [http://software.canon-europe.com/products/0010883.asp](http://software.canon-europe.com/products/0010883.asp)

---

### Post by Me887799 on 2012-01-31
My apologies.  I've been trying for a day or two to fix this, and I ran out of options.  I think I asked for help too soon, as I resolved this issue on my own.

This issue has been fixed.

How I fixed it if anyone finds this thread:
If you installed the Canon MP280 drivers through the software manager and it fails to print in the manner I've stated above, download the foreign (still English) Canon MP280 linux drivers here: [http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100301402.html) and extract contents to a place of your chosing.

Go to Printers is System Settings, right click your Canon MP280 printer, and DELETE it.

In the terminal, navigate (cd) to the folder containing the files you extracted from the .tar.gz file.  Allow the installer.sh script to be bootable by typing chmod +x installer.sh

AFTER you have made the installer script bootable, enter 'sudo ./installer.sh' without quotes.  Immediately in Ubuntu 11.10, you should see a dialogue box telling you the printer is being installed, even though the installer inside terminal reports the printer being undiscovered.  

Continue to the printer settings in System Settings, and right click your printer, go to properties, and print a test page by clicking the bottom left hand button labeled "Print Test Page".

---

### Post by bluexrider on 2012-01-31
glad you got it going please mark this
(SOLVED)

---

### Post by sjoseph on 2012-08-15
Thanks for this post. I was having similar problems w the 12. upgrade. This worked great...

---

