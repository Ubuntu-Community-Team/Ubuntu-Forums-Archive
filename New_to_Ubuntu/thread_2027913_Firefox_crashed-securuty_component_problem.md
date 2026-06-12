---
title: "Firefox crashed-securuty component problem?"
date: 2012-07-17
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-07-17
I know I read a thread yesterday which suggested that uninstalling and reinstalling might sort a firefox problem, but I cannot find it so am not sure mine is the same problem. I resorted to going back to google chrome to be able to carry on, but what does this mean and how do I resolve it? - unistalling and reinstalling did nothing.

'Could not initialise the application's security component. The most probable cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard drive is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features.'

Ubuntu 12.4

I did check if I had room on my hard disk and it looks like I do so I think the other solution will be the right one, but no idea what to do. Thanks, J

---

### Post by ajgreeny on 2012-07-17
Use the command ```
mv .mozilla .mozillabak
``` in terminal and then restart firefox.  That renames the hidden folder .mozilla in your home as .mozillabak but leaves all the files and folders in it still intact.

You will temporarily have lost all your bookmarks and extensions, but we can get them back later; let's go one step at a time.

Once you have firefox running properly, get all your bookmarks back by going to Bookmarks->Show all bookmarks, then to Import and backup->Restore->Choose File, and you can then navigate to your old folder .mozillbak/firefox/[COLOR=Red]qn4bdmr0[/COLOR].default/bookmarkbackups and choose the most recent .json file to restore.

The profile name shown above in red will be different on your machine, but will probably be the only [COLOR=Red]x#x#x#[/COLOR].default folder, so it will be obvious.  Most if not all plugins should still work, but you will need to install any add-ons that are needed from the mozilla website, [Firefox Add-ons]("https://addons.mozilla.org/en-US/firefox/")

---

### Post by Jackalyn on 2012-07-17
> **ajgreeny said:**
> Use the command ```
mv .mozilla .mozillabak
``` in terminal and then restart firefox.  That renames the hidden folder .mozilla in your home as .mozillabak but leaves all the files and folders in it still intact.

You will temporarily have lost all your bookmarks and extensions, but we can get them back later; let's go one step at a time.

Once you have firefox running properly, get all your bookmarks back by going to Bookmarks->Show all bookmarks, then to Import and backup->Restore->Choose File, and you can then navigate to your old folder .mozillbak/firefox/[COLOR=Red]qn4bdmr0[/COLOR].default/bookmarkbackups and choose the most recent .json file to restore.

The profile name shown above in red will be different on your machine, but will probably be the only [COLOR=Red]x#x#x#[/COLOR].default folder, so it will be obvious.  Most if not all plugins should still work, but you will need to install any add-ons that are needed from the mozilla website, [Firefox Add-ons]("https://addons.mozilla.org/en-US/firefox/")

Thanks that worked - had to try twice but now all up and running and have to decide between Chrome and Firefox now! :popcorn:J

---

