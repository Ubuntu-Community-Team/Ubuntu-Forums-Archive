---
title: "scanner now not recognised"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by Brian_Williamson on 2015-08-10
hi, I am new to Linux and have installed Lubuntu 15.04 on Dell laptop. An Epson XP-314 was plugged in, and after finding what to download and install got the printer going and by clicking the simple scan icon the scanner also worked. Two days ago when trying to scan, I get a message "scanner not recognised". As it had been working fine I was at a loss, as the printer itself still works a treat. Hope someone has an easy solution for me.
Brian

---

### Post by jatin2302 on 2015-08-10
go to printers from the menu > delete the present printer> add your printer or scanner, 
now do to scan > click on scan> if it shows an error, click on "change printer", u night be getting an alternate printer in the menu, select that and retry>>
FYI- i was getting an same error using my hp1005 . due to page jam or any other unknown error, printer is stuck, it do not print nor scan, i got to add a new printer, even after reset of my printer..

---

### Post by YTL on 2015-08-12
Did you install Firewall in between? If you did, one option is temporarily turn off Firewall as it need to get response signal back from scanner. The other option, you have to use terminal to enter command -- "sudo ufw allow from xxx.xxx.xxx.xxx" (without " ") (xxx--- is your scanner's IP address) then press enter, then exit terminal.
Hope this will help.

---

