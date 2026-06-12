---
title: "Ubuntu 11.10 causes trouble for Mozilla applications"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by herwin on 2011-10-14
Earlier today I upgraded to Ubuntu to 11.10.

Since then I get an error message when I start both Firefox and Thunderbird (both were already installed and in use before the upgrade). The error message is the same:

"An error occurred while loading or saving configuration information for thunderbird-bin. Some of your configuration settings may not work properly." [when I start firefox it refers to firefox-bin].

When I click to see more details it reads:

"Configuration server couldn't be contacted: D-BUS error: Method "GetDefaultDatabase" with signature "" on interface "org.gnome.GConf.Server" doesn't exist ubuntu oceilot"

Any suggestions?

Thanks

---

### Post by collisionystm on 2011-10-14
> **herwin said:**
> Earlier today I upgraded to Ubuntu to 11.10.

Since then I get an error message when I start both Firefox and Thunderbird (both were already installed and in use before the upgrade). The error message is the same:

"An error occurred while loading or saving configuration information for thunderbird-bin. Some of your configuration settings may not work properly." [when I start firefox it refers to firefox-bin].

When I click to see more details it reads:

"Configuration server couldn't be contacted: D-BUS error: Method "GetDefaultDatabase" with signature "" on interface "org.gnome.GConf.Server" doesn't exist ubuntu oceilot"

Any suggestions?

Thanks

They might not have upgraded properly.. try this.

Un-install firefox

open terminal

sudo apt-get clean

re-install firefox from software center.

If this works, we can do this with Thunderbird, but we need to back it up first.

Go to your home folder

press CTRL + H to see your hidden files. Copy the .thunderbird folder. make sure thunderbird is closed when you do this.

Put the copied folder somewhere, my documents for instance.

uninstall thunderbird, re-install

put your .thunderbird folder back.

---

### Post by herwin on 2011-10-19
Sorry for the delay in getting back to you. I was travelling.

I found out what the problem was (and it is rather embarrassing):

I had re-started the computer after the update. I had too many things open that I was working on to re-start the computer when the upgrade was done.

By the time I did reach the point where I could re-start the computer I had forgotten that it had no re-started yet after the upgrade.:oops:

After the re-start everything works fine.

Thanks for the suggestions anyway!

---

### Post by herwin on 2011-10-19
Sorry, the third line should read: I had NOT re-started the upgrade.

---

