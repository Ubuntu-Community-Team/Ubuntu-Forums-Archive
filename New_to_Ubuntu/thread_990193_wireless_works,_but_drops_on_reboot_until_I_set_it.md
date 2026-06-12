---
title: "wireless works, but drops on reboot until I set it up again in network manager"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by eatingganesh on 2008-11-22
So, after literally two months trying to get my wireless to work, I happened upon a post that solved my problem. The wireless now works beautifully.

However, when I reboot the system, its settings disappear from the network manager. The system and OS recognize the wireless driver and hardware, and the wireless shows up in network manager. But - in network manager - the wireless shows as disabled. I simply have to enable it and re-enter the essid and WPA password and it works instantly. But everytime I reboot I have to do this and it is getting annoying.

I know there is a way to edit the wireless settings through terminal commands, but I'm not sure what those commands are, in what sequence they should be performed, and if manually setting it will solve this problem. Of course, there could be another even easier fix for this issue.

BTW I tried using WICD and it does not recognize the wireless at all even though the network manager does. 

Any suggestions on how to fix this annoyance? Thanks!

---

### Post by beno1990 on 2008-11-22
If you right-click the network manager and choose "Edit connections", and go to the wireless tab, do you see any connections listed? If so, click edit and make sure "Connect automatically" is ticked. Let me know if that helps.

---

