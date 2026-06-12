---
title: "Upgrade from 10.04 to 12.04 - HUD not working"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by warlock_handler on 2012-06-04
Hi,
yesterday I upgraded to 12.04 everything went well, just that now the HUD isnt working when I am on any application (like firefox) and press Alt ; the HUD appears but when I type anything on it (like file) it doesnt show any results.

Can you please help me debug this

how do i check if the HUD service is running or not??

thnx

---

### Post by warlock_handler on 2012-06-04
ok i got it working ... sudo apt-get install indicator-appmenu-tools

ref: [http://askubuntu.com/questions/128090/hud-wont-work-on-12-04](http://askubuntu.com/questions/128090/hud-wont-work-on-12-04)

---

### Post by waperboy on 2012-06-07
> **warlock_handler said:**
> ok i got it working ... sudo apt-get install indicator-appmenu-tools

ref: [http://askubuntu.com/questions/128090/hud-wont-work-on-12-04](http://askubuntu.com/questions/128090/hud-wont-work-on-12-04)

This helped somewhat, but only options that are in my "notification applets" appear in the HUD results - Network disconnect etc, Dropbox, mail stuff, sound stuff, log out etc.

?

---

### Post by warlock_handler on 2012-06-07
> **waperboy said:**
> This helped somewhat, but only options that are in my "notification applets" appear in the HUD results - Network disconnect etc, Dropbox, mail stuff, sound stuff, log out etc.

?

what??? didnt get you there... what exactly is the issue???

---

### Post by hornetster on 2012-09-18
I have this exact problem ie the only results I get from HUD are relevant for the programs running in the notification applets.
Was there ever a solution for this?
Thanks, John.

Solved: my specific problem was with LibreOffice. After some playing and searching, found that another component needs to be installed - lo-menubar - not installed by default..

---

