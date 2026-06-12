---
title: "update faliure"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by joks on 2012-12-27
after installing jdownloader or skype or dropbox i am not able to update anymore i get the failure:
W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

please help

---

### Post by sandyd on 2012-12-27
> **joks said:**
> after installing jdownloader or skype or dropbox i am not able to update anymore i get the failure:
W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

please help
You have cdrom updates on for some reason, and have a discontinued ppa

Go to Software Center -> Edit Software Sources
Click on the "Other Software" Tab, and make sure there is no checkmark beside any entries that start with "cdrom".
Then, scroll down until you see
```

http://ppa.launchpad.net/gwibber-daily/

```
and remove the checkmark from in front of the entrie(s) as well.

Click close, and wait for it to update :)

---

### Post by deadflowr on 2012-12-27
> Click close, and wait for it to update

Or don't wait and open a terminal and type:

```
sudo apt-get update
```

And if you have any problems, post the output(Please use the code tags {#} if you do).

Note: to open a terminal press ctrl + T, or open the dash an type terminal.

---

### Post by ibjsb4 on 2012-12-27
And maybe some pic's would help.

To uncheck CDrom go here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

To remove that PPA go here:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

And about that PPA, like sandyd said, no build for 12.10.

[https://launchpad.net/~gwibber-daily/+archive/ppa](https://launchpad.net/~gwibber-daily/+archive/ppa)

---

### Post by joks on 2012-12-28
Hey guys,
thanks for your help, but i still 
get a update failure:
with terminal:
Fetched 4,121 B in 6s (645 B/s)                                                
W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.

with updater:
W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)/dists/quantal/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

i deactivated the two ppa you said...(picture)
[[IMG]http://www.picamatic.com/show/2012/12/28/03/39/8917852_bigthumb.png[/IMG]](http://www.picamatic.com/view/8917852_Screenshot_from_2012-12-28_13:44:37/)

---

### Post by audiomick on 2012-12-28
> **sandyd said:**
> You have cdrom updates on for some reason,...
Go to Software Center -> Edit Software Sources
Click on the "Other Software" Tab, and make sure there is no checkmark beside any entries that start with "cdrom"..

Did you do that to remove all cdroms from the package sources? It is still looking for one for some reason.

Edit: no, you didn't apparently. I just looked at the screenshot, and can see a cd rom selected at the top of the list. You need to deselect that.

---

### Post by joks on 2012-12-28
thanks guys, now it works, but now not everything will be updated or?

---

### Post by ibjsb4 on 2012-12-28
> **joks said:**
> thanks guys, now it works, but now not everything will be updated or?

Yes it will  :) your good to go

And welcome to the forum

---

### Post by audiomick on 2012-12-28
> **joks said:**
> thanks guys, now it works, but now not everything will be updated or?

You don't need the cdrom to update, so that is not an issue. The updater gets the updates from the repositories on the net. A cdrom would only be relevant if you were trying to do something offline, perhaps.

As far as the PPA goes, that looks like the daily build PPA for Gwibber. Gwibber is in the standard repos, and I would suggest sticking to that unless you have a really good reason for wanting to have a newer version. Your current update problem is only one reason for this.

I can't say for sure why that PPA failed, but reasons might include that it has moved, the developer is not maintaining it anymore, it is temporarily offline, amongst others.

---

