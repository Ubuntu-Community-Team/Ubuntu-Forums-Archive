---
title: "transfer pics from phone to pc?"
date: 2022-08-14
forum: New to Ubuntu
---

### Post by nginmu on 2022-08-14
I have Samsung galaxy s10 with android v 12, pc with lubuntu 21.10, and usb C lead.

How can I copy pics from phone to pc esily?

---

### Post by Rex Bouwense on 2022-08-14
I believe Lubuntu 21.10 has reached end of life.  However, it is very simple to copy your photos.  Plug your phone into your PC using the USB cable and open it in your file manager.  You will have to allow your PC to have access.  Your pictures are stored in the DCIM file or your Download file on your phone .  Merely copy the pictures and paste them to where your want them on your PC.  The Pictures folder is the obvious choice

---

### Post by nginmu on 2022-08-14
Strange.. couldn't get it to come up at all, but I had the phone into a little usbc hub thing. got rid of the hub, lead straight between pc and phone.. started working.

Thanks for the headsup on 21.10 being out of date.

---

### Post by jeremy31 on 2022-08-14
Likely had USB disconnects with the power draw while using the hub

---

### Post by SeijiSensei on 2022-08-15
Another option is KDEConnect which includes file transfers as well as a number of other phone applications if you have an Android phone. Doesn't require KDE to work. Install the app from the Google Play Store, and "sudo apt install kdeconnect" on the PC. It uses the local network.

---

### Post by ajgreeny on 2022-08-15
And another way- install the app wifi-file-transfer on your Android phone then use a web-browser to navigate to **local-IP:1234**, eg **192.168.1.76:1234**.
This shows a file-browser type window and allows download of files to your computer by using right click -> Save link as.

Transfer is only in the one direction, I think, but it save messing about with bluetooth which I don't have on my desktop, and avoids searching for a USB cable.

---

