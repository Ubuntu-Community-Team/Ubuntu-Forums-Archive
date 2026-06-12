---
title: "Cannot reach log-in screen after downloading updates"
date: 2013-09-03
forum: New to Ubuntu
---

### Post by zirgut on 2013-09-03
I have been running 12.04 quite happily for over a year and doing regular updates. The last time I downloaded there was quite a large package , maybe 90 + updates. After downloading the login screen would not come up. I get the grub screen and then there is the command screen. Not really sure what to call it. When I enter user name and password what comes up is 
Documentation:https:/ help.ubuntu.com/
packages can be updated
updates are security updates.

Then once when I tried to start in recovery mode the message that came up was:
7 packages can be updated
0 updates are security updates.

Suggestions and guidance would be very much appreciated
Thanks

---

### Post by cariboo on 2013-09-03
I'd suggest starting in recovery mode, and then select Dpkg from the menu, to make sure all the updates have been installed properly. If that doesn't get you to a login screen, the restart in recovery mode again, and select Networking from the menu, then once you are connected, go back to the menu and select dpkg again.

---

### Post by zirgut on 2013-09-04
Thanks for that. I will try that later. It is on my friends computer. Get back to you.

---

### Post by zirgut on 2013-09-08
Hi,
I have tried your suggestions cariboo907 and they have not done the trick. Just wondering where I go from here.
I did also try some commands that I had seen on the forum for a similar problem.
These were:

sudo apt-get clean

sudo apt-get update

sudo apt-get update

sudo apt-get auto remove

The last one was listed by the instructions when I did what you suggested.
Is it time to reinstall ubuntu?
Thanks

---

### Post by Bashing-om on 2013-09-08
zirgut; Hi !

Just a thought .. are you running a proprietary graphics driver ? .. and perhaps the updates broke the proprietary driver ?
See if you can boot into your system from a "recovery" console from the grub menu.

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by zirgut on 2013-09-16
Hi,
Thanks for your advice. I have tried going to the recovery start from the grub menu including previous ubuntu editions. All to no avail however.
Any further suggestions received with thanks.

---

