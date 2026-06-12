---
title: "Palm Sync workaround for Mozilla Sunbird/Calendar"
date: 2005-05-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Dali on 2005-05-30
Greetings,

I've found a workaround for the lack of palm sync to Calendar. I know there is some development happening over at mozdev with regards sync capability, but I stumbled upon this today and wanted to share it with anyone who might find it useful.

I'm currently running Ubuntu Hoary, and use KPilot to sync my Sony Clie, as I had trouble with the gPilot utility.

KPilot allows me to set up conduits for various databases when I sync, and the calendar conduit allows me to save the datebook in .ics format, which is readable by Mozilla Calendar.

So the cool stuff is: setup the KPilot calendar conduit to export an .ics file to a location of your choosing. Sync your Palm so that the info on the device is added to the new .ics file.

Then in Mozilla Calendar, open a new calendar and point to that file. It'll add all your Palm's calendar entries. If you wish to send new calendar entries back to the palm that you've added using Mozilla Calendar, make sure that when saving new entries in Calendar that you choose the Calendar that points to the .ics file you are using.

Then when you sync with KPilot again, the new info should be added to the Palm's datebook database. The workaround is simply that you don't sync within Calendar itself, but use a common .ics file to pass info back and forth, syncing with KPilot.

I have experimented back and forth with this, and found it to be a reasonable workaround, at least until the mozdev initiative is fully fruitful!

Would someone else be willing to mess with this idea and confirm it's useability? I imagine that there would be similar workarounds on other platforms, using various syncing applications.

Best,

Dali

---

### Post by Burgundavia on 2005-05-30
Are you will to help test PDASupport for Breezy? If so, see this post:
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007742.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007742.html)

Corey

---

### Post by Dali on 2005-05-30
[QUOTE=Burgundavia]Are you will to help test PDASupport for Breezy? If so, see this post:
[http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007742.html](http://lists.ubuntu.com/archives/ubuntu-devel/2005-May/007742.html)

Corey[/QUOTE]
 Surely...I'll have a look at it!

Cheers,

Dali

---

### Post by Dali on 2005-05-30
[QUOTE=Dali]Surely...I'll have a look at it!

Cheers,

Dali[/QUOTE]
 I added my info to the wiki, hope that helps!  I think it's just a matter of recompiling gpilotd with the vendor and product id added to the hardcoded list of supported devices in gpilotd.c.  Not something I was prepared to do at that point, but might give it a go later this week.

Cheers,

d

---

