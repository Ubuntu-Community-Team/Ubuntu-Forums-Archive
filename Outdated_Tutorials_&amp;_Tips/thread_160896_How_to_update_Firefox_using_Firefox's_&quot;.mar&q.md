---
title: "How to update Firefox using Firefox's &quot;.mar&quot; files."
date: 2006-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by hellerite on 2006-04-15
How to update firefox to a new version. For Dapper. 

Things you will need. Download to your home directory.
[INDENT]**A. Firefox's updater utility: Found in Firefox's tar file... Download to your home folder and extract.**[/INDENT]

[INDENT][B]B. Firefox's .mar file; "firefox-1.5.0.2.complete.mar" file: [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/update/linux-i686/](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/1.5.0.2/update/linux-i686/)
	   and choose your locale... In my case en-US.[/B][/INDENT]

Open gnome-terminal.

Create the following directory:
	[INDENT]**sudo mkdir /usr/lib/firefox-update**
[/INDENT]

Copy and rename the .mar file to the above directory.
	[INDENT]**sudo cp /home/<your home>/firefox-1.5.0.2.complete.mar /usr/lib/firefox-update/update.mar**[/INDENT]

Copy the updater utility to the firefox-update folder:
	[INDENT]**sudo cp /home/<your home>/firefox/updater /usr/lib/firefox-update**[/INDENT]

cd to the Firefox directory.
	[INDENT]**cd /usr/lib/firefox**[/INDENT]

Run the following command to update: (Make sure that you are in your current firefox directory... see above)
	[INDENT]**sudo ../firefox-update/updater ../firefox-update 0**[/INDENT]

Once the update completes change to /usr/lib/firefox-update directory and review the update.log file. Look for a "Succeeded" message at the bottom.

Open Firefox and go to Help/About Firefox. It should have the new version.

For More information on .mar files go to the following Mozilla address

**[http://wiki.mozilla.org/Software_Update:Manually_Installing_a_MAR_file](http://wiki.mozilla.org/Software_Update:Manually_Installing_a_MAR_file)**

[IMG]http://hellerite.googlepages.com/firefox-update.png/firefox-update-full.png[/IMG]

---

