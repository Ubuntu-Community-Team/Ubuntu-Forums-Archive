---
title: "Wi-Fi loop issue"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by ahmad3 on 2013-08-21
hello i recently upgraded from Ubuntu 12.10 to 13.04 on 12.10 Wi-Fi didnt work at all it didnt even show that i had a Wi-Fi card just nothing
when i upgraded from 12.10 to 13.04 it showed that i had Wi-Fi i was able to connect the first time i booted up but after i shut down my PC and rebooted it showed that i had to enter the passwrd
it kept showing over and over right now im using wired conenction to post this can anyone tell me what to do i have Toshiba satilite C850 - B215

any help is welcomed :)

---

### Post by kurt18947 on 2013-08-21
I don't know if this will help you but it's quick, harmless to my knowledge and has worked for me in the past. Go to "network connections" and delete all wireless connections found there.  Then  click "new" and enter the information on the network you're trying to connect to.  I've had cases where everything looks correct for a wireless connection but it still wouldn't connect, just loop as you're seeing.  Deleting and re-entering fixed whatever was causing the problem.

---

### Post by ahmad3 on 2013-08-21
i did it before it didnt help also someone before told me to download and install WICD using the terminal with this command "sudo apt-get install wicd" i did it and when i rebooted it gave me errors i uninstalled it and it still didnt work and still gave me the errors

---

### Post by kurt18947 on 2013-08-21
> **ahmad3 said:**
> i did it before it didnt help also someone before told me to download and install WICD using the terminal with this command "sudo apt-get install wicd" i did it and when i rebooted it gave me errors i uninstalled it and it still didnt work and still gave me the errors

Did you disable Network-manager first?  I *think* (haven't done it myself) that you have to disable/remove Network Manager before enabling WICD.  You can't have both running at the same time but you do need to have one installed if not active.  You can install either one without a network connection but it isn't real simple.

---

### Post by ahmad3 on 2013-08-21
yea it was in a tut i forgot where i got it from it told me everything and it didnt work but nvm now since i got the Wi-Fi to work i didnt do anything it just worked by it self weird huh :P anyways i will mark this as solved

---

