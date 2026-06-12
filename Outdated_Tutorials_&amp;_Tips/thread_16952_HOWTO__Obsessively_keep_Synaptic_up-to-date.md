---
title: "HOWTO:  Obsessively keep Synaptic up-to-date"
date: 2005-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by cka on 2005-02-24
**These methods have been tested by myself and are known to work in the latest Hoary release, but there's no real reason it shouldn't apply to Warty as well.**

Step 1:  Add an RC script to /etc/init.d to automatically update listings upon boot (assuming you've got your network setup to automatically connect):

[quote=/etc/init.d/apt-update]
#!/bin/sh

PATH=/usr/bin

. /lib/lsb/init-functions

log_begin_msg "Updating Synaptic package listings..."
/usr/bin/apt-get -qq update
log_end_msg $?

exit 0
[/quote]

STEP #2: Now chmod +x this script and symlink it to rc2.d (I suggest not doing this via rcS.d because on my machine that would try to update the packages before it initiated the PPPoE connection...  adding it in rc2.d a fair amount later than the ppp init script does a fine job of background-updating upon boot, but mileage may vary) with the command [color=red]ln /etc/init.d/apt-update /etc/rc2.d/S44apt-update[/color]

---

STEP #3: Next, configure a root crontab to run every set amount of time to keep packages up to date -- daily seems pretty good.  Fire up a ROOT CONSOLE via the Applications > System Tools menu and type [COLOR=Red]crontab -e[/COLOR].  This should load vim up, from here, do the following:

hit 'a'
type [COLOR=Red]@daily /usr/bin/apt-get -qq update[/COLOR]
hit esc, then type '!wq'

This will install a new crontab script for root to run every day and download the package lists.



Optionally, you can also download the update manager and update-notifier which are simple front-ends to updating your system via Synaptic (but I am unsure if this has found its way into Warty yet.)  Simply add a new program to start up in the Sessions screen in the Preferences menu, and refer /usr/bin/update-notifier and you'll have a flashy notification icon telling you something needs to get updated.  If not, you'll have to keep updating your system via apt-get or the Synaptic Smart Upgrade system.

Hope this was helpful to some.  Feel free to comment or make additions on this.

---

### Post by jdong on 2005-02-25
Hoary already has a nightly cronjob that does this in /etc/cron.daily.

---

### Post by NeoChaosX on 2005-02-26
This did come in handy, though - I used the same instructions to set up a script to update F-Prot's virus definitions at boot instead of doing it manually. Much thanks cka, even if the original intent for this How-To was already fufilled.

Also, that last command for writing the crontab should be ':wq'. Entering '!wq' caused vim to complain about "command not found", at least when I entered it.

---

