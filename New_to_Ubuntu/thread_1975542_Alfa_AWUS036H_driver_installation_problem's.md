---
title: "Alfa AWUS036H driver installation problem's"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by PADDYKCSDC on 2012-05-07
Hello everyone on this Ubuntu forum ,I'm a complete newbie to Ubuntu/Linux i have a little programing knowledge.I am running Ubuntu alongside windows (soon to be deleted) I am having problems installing the driver for my wireless adapter (AWUS036H) i have a small compact laptop with no disk drive so i installed the power control drivers off alfa's website.(i cannot use the additional driver application because my alfa is not plugged in ,and if i do plug it in the green light starts flickering dim my thought was because i have not got any drivers installed will this harm the adapter ?) 

so far I have got the drivers on my desktop  unpacked what do i do next ?

also if i go into terminal and type the sudo command e.g sudo eth1 or eth0 or usb0

it asks for a password but when I type my password no characters appear on screen (the cursor just stays in the same place) so i cannot enter my password

thank you very much for reading and any help would be a fantastic

p.s i have looked everywhere for this but they do not fit my situation and all of them use the generic user interface and i cannot find my hardware because it is not plugged in....should i plug it in and then see if i can update the driver from > additional drivers ?

---

### Post by arochester on 2012-05-07
1) Look here: [http://ubuntuforums.org/showthread.php?t=1605285](http://ubuntuforums.org/showthread.php?t=1605285)

2) In the Terminal your password will not show. Just type the password and hit enter

---

### Post by PADDYKCSDC on 2012-05-07
sorry for asking but eht does this mean ? 

3) Open a terminal window, go to where you extracted.

should i type sudo/desktop/036H_Linux_26.1040.0820.210

what should i type to get to where i extracted

the alfa awus036h driver is on my desktop and is named above

---

### Post by tilt2kngiht on 2012-05-07
when you have the Alfa connected go to the terminal and enter "ifconfig wlan1 on" (it might be wlan0 or wlan2) to enable it.

---

