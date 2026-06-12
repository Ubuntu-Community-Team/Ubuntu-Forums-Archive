---
title: "updater - failed to load repository?"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by Kanahau on 2013-01-19
I have been running Ubuntu 12.04 and it is great, however i am having a small problem with the updater. A red triangle with an exclamation mark will appear in the top bar. when i check updates as instructed, it tells me it has failed to check repository (see pic) it doesnt seem to upload any updates and remains telling me it was last updated 8 days ago?

I don't know the correct question to ask as i do not know what the problem is?
or should i just not worry about it ........... ?

okay i couldn't work out how to insert the screen shot so i attached it instead?

---

### Post by grahammechanical on 2013-01-19
The information under Details in that dialog box would have been helpful.

You could try going to Software Sources and unchecking any PPAs that you may have installed and trying to update again.

Regards.

---

### Post by Kanahau on 2013-01-19
**Grahammechanical**
When details is clicked here is the message:

W:Failed to fetch [http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/cooperjona/stormcloud/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Hope this helps

---

### Post by arpanaut on 2013-01-19
It appears that PPA is no longer active, you will need to go to your "Software Sources" and untick that PPA's items.

---

### Post by ibjsb4 on 2013-01-19
Sources how to

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

---

