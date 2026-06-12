---
title: "Skype runs incomplete? 12.04 64 bit"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by escrappa on 2012-04-29
Dear all:

I am very new to ubuntu. I had 11.10 in 32 bit version running. Skype was installed and was working fine.

I have now installed 12.04 in 64-bit.

Downloaded skype for 64-bit. It was installed (but does not appear in  software center under installed applications). It opens and seems to  work.

Skype does not appear in the upper right corner task. I cannot access  the options, which should be in the upper left corner, as always? There  is nothing.

After I oppend skype once and close it I cannot log in a second time. It says "skype is probably running". 

I do not know how to deinstall skype and really don't know how to proceed.

Thx for any hint.

Tom

---

### Post by robbosch on 2012-04-29
I had exactly the same problem. I solved it by de-installing skype.
Add the partner repositories in update manager (in fact add the repositories in /etc/apt/sources.list)
Then either install through software center or terminal (apt-get)

de-install skype:
open software center. type skype in the search window and click remove.
alternatively open a terminal and type: sudo apt-get remove skype

Then open update management
click configuration
go to the 2nd tab and tick partners repositories

if partner repositories are not there, add them by clicking 'add'

---

### Post by escrappa on 2012-04-29
Thx.

I have de-installed skype. 

In the updated manager I have checked the second tab. Everything is ticked (but for the cd-option).

I don't know howe to add partner repositories?

Something must still be wrong: When I download skype now the software center crashes.

---

### Post by 3rdalbum on 2012-04-29
The Skype notification area icon appears on my 12.04 machine, so not sure why it's not appearing on yours.

One possible thing I can think of is the notification area whitelist. Skype uses the "notification area" API to put the icon in the top panel, but this method is depreciated; so Unity doesn't display notification area icons unless you add them to the "whitelist".

It's in dconf-editor - you will need to install dconf-tools and then type 'dconf-editor' into the terminal. Then go to Desktop, then Unity, then Panel, and then the one item in there is whitelisted notification area icons.

Funnily enough, Skype isn't in mine, but its icon appears in my panel. Maybe setting the setting to "all" will cause Skype's notification area icon to appear in your panel.

---

### Post by escrappa on 2012-04-29
I installed it through the terminal - now it is working.

Whatever it was ...

Thank you everybody.

Tom

---

