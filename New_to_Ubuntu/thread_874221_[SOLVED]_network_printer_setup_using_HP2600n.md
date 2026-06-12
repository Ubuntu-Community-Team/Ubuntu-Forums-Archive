---
title: "[SOLVED] network printer setup using HP2600n"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by flyer4100 on 2008-07-29
I have started searching the threads but i think i'm still not getting it right somehow. My printer is setup purely as a network printer ie it has no physical connection to either the two XP mchines or my laptop which is purely Ubuntu 8.04. the network is wired ETHERNET not wireless. Printing from either of the two XP mchines is fine

Following is how I attempted the setup in hardy heron.

System>Administration>Printing
this displays Printing configuration - localhost

Under Server settings - nothing is selected (ticked)
Under Local printers - PDF

Select New Printer - asks to select connection>Devices
selected AppSocket/HP JetDirect
Host - named it mobile (laptop name)
Port Number - already set at 9100
click Forward
selected HP from list of printer vendors
click Forward
Select Model - Color Laserjet 2600n
Drivers - HP Color Laserjet2600n Foomatic/foo 2hp [en](recommended)
click Forward

printer name - 2600n
Description - HP Color Laserjet 2600n
Location - mobile
Apply

selected 2600n from local printers and clicked print test page

The result is no printing and no errors..

any thoughts anyone

---

### Post by bab1 on 2008-07-29
> Following is how I attempted the setup in hardy heron.

System>Administration>Printing
this displays Printing configuration - localhost

Under Server settings - nothing is selected (ticked)
Under Local printers - PDF

Select New Printer - asks to select connection>Devices
selected AppSocket/HP JetDirect
Host - [COLOR="Red"]*named it mobile*[/COLOR] (laptop name)
Port Number - already set at 9100

You are supposed to use the hostname of the printer (or the IP address).  Have you named your printer in DNS?  If not use the IP addr and it should  work.

---

### Post by flyer4100 on 2008-07-29
> **bab1 said:**
> You are supposed to use the hostname of the printer (or the IP address).  Have you named your printer in DNS?  If not use the IP addr and it should  work.

Thanks heaps..now working well i printed a test page out and i/ve also just printed this thread as well

---

### Post by bab1 on 2008-07-29
Glad I could help.  Mark this thread solved please.  If you feel like it, click  on the little star at the lower right to say thanks.

---

### Post by flyer4100 on 2008-07-29
> **bab1 said:**
> Glad I could help.  Mark this thread solved please.  If you feel like it, click  on the little star at the lower right to say thanks.

sorry how do i mark as solved...so new to this thanks in advance

whoops found it noe

bab1 , hope your ok just been reading about the earthquake....

---

