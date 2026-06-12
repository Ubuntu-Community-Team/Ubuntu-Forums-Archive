---
title: "Upgrading from 13.04 to 13.10 Prep for Upgrade Error"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Wheeladrew on 2013-10-13
Just as the Title suggests, I am getting a "Preparing the upgrade failed" error when attempting to upgrade from 13.04 to 13.10 when running the 
> do-release-upgrade -dcommand.

Anybody have some advice?

---

### Post by Bashing-om on 2013-10-13
Wheeladrew; Weelll..

Lubuntu ?? .. Is the screensaver deactivated ?
Is 13.04 fully updated ?
Are all 3rd party PPAs sources non active ?
update-manager-core installed ?

[INDENT][INDENT]just off the top of my head
[/INDENT][/INDENT]

---

### Post by Wheeladrew on 2013-10-13
This is standard Ubuntu, the screensaver is deactivated, 13.04 is updated, and I got one error when running sudo apt-get update
W: Failed to fetch [http://ppa.launchpad.net/drwright/stable/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/drwright/stable/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found
And yes, update-manager-core is installed.

---

### Post by Bashing-om on 2013-10-13
Wheeladrew;
The last supported version I see for that PPA is for precise.
Suggest ya also disable that ppa and try the upgrade once more.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Wheeladrew on 2013-10-13
I got rid of that PPA, now.
I updated my computer again, and then restarted and ran the>  do-release-upgrade command. 

The terminal output 
> ~$ do-release-upgradeChecking for a new Ubuntu release
No new release found


This confused me, because I have 13.04. I checked my Details page and it verified this.

Thanks for your help so far, by the way.

---

### Post by Wheeladrew on 2013-10-13
I ran that last command incorrectly. (forgot the -d) 
It is now updating!

---

### Post by Bashing-om on 2013-10-13
Wheeladrew; You do good work !

You are aware that what you are installing is not the final release version ? 
Version 13.10 is scheduled for release on the 17th of this month... There are yet to be changes from this build that is installed as to what will be.

Hopefully the wonderful package manager will take care of all.

[INDENT][INDENT]on your mark, get set ->[/INDENT][/INDENT]

---

