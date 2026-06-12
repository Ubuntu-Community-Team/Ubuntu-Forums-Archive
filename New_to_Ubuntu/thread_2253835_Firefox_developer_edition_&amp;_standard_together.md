---
title: "Firefox developer edition &amp; standard together?"
date: 2014-11-22
forum: New to Ubuntu
---

### Post by Neil_Nand on 2014-11-22
Hello,

I've recently downloaded & installed Firefox developer edition but it seems to have replaced my 'standard' Firefox.

Is there a way for me to install both of them at the same time? At the moment no matter what I try & cannot remove the developer edition, every time I try and reinstall Firefox I end up with the developer edition again.

I'd like both so I can use the standard one for general use and the developer version for development use.

Thanks for any help,
Neil.

---

### Post by coldcritter64 on 2014-11-23
I run firefox nightly alongside iceweasel (Debian's branding of firefox, gives the same conflict you are seeing). I have also run nightly on Ubuntu in the past and noted the problem there as well, and used this technique.
[B]
Important: please read and try to understand the steps fully before attempting the instructions. Edit: [/B]$HOME and the "~" symbol represent your users home folder, "/home/<you>/", to the system. [B] 

Also IMPORTANT:[/B] **before attempting the next instructions** please check the contents of the following command for your current set up ...
Note: The keyboard combination "ctrl + alt + t", will bring up a terminal in Unity.

```
cat $HOME/.mozilla/firefox/profiles.ini && ls $HOME/.mozilla/firefox
``` this is to check no problems have been caused so far with using the developer edition. 
Should be OK, just a precaution albeit an important one. 
IF you need to post the output back here for checking please use the advanced editor, copy and paste your results between [noparse]```

```[/noparse] tags by highlighting your output in the editor and pressing the # button on the toolbar. Only if you think you need to have the results checked otherwise just compare them to... 

EXAMPLE output from this install, and what I'm looking for if you don't post back results, at least check the highlighted details next ...
> ```
$ cat $HOME/.mozilla/firefox/profiles.ini && ls $HOME/.mozilla/firefox
[General]
StartWithLastProfile=1

[Profile0]
**Name=default**
IsRelative=1
Path=0dkb032m**.default**
**Default=1**

[Profile1]
Name=Nightly
IsRelative=1
Path=ggi7rwel.Nightly

0dkb032m**.default**  Crash Reports  ggi7rwel.Nightly  profiles.ini
```You can see the profile I generated for Nightly here using the following instructions... "ggi7rwel.Nightly". 

The default profile "0dkb032m**.default"** is being used as default by the **Default=1 **entry listed under its header. The name in the profiles.ini file must match up with the entries from the ls command for the randomly generated strings.

Instructions ...
To run both at the same time without one "taking over", you need to set up firefox profiles.

**STEP 1**...Before attempting this **back up your mozilla firefox folder** in your home directory, the following command copied and pasted in terminal will place a visible copy on your desktop. ~/.mozilla is the hidden folder inside your home folder holding all your firefox user settings, this includes current profile set ups. This is a precaution against totally messing up your installation of firefox as it is at present.

```
cp -R ~/.mozilla $HOME/Desktop/mozilla-BAK
```

**Step 2**. To set up a profile for the developer edition,

**a.** Run the following command in a terminal ```
firefox -P
``` A window pops up. 
**b.** Press "Create Profile"
**c.** Press "Next"
**d.** Name it "Developer" (or whatever you specifically want it called by firefox, name is a suggestion only).
**e.** Press "Finish".
**f. DO NOT PRESS "Start Firefox" just yet**. PRESS "Exit"

**Step 3**. (launch command and script) You need to use a special command like
```
/path/to/developer/edition/of/firefox/firefox -P "**D**eveloper"
``` note I've highlighted the capital D to differentiate it from a script you can make next for easier launching, especially from terminal.

An example of mine with my profile named "Nightly" ...
> ```
$HOME/bin/firefox-nightlies/firefox/firefox -P "Nightly"
```copy and pasting that code here launches firefox-nightly even if iceweasel is running without any problems. Change your path and profile name to suit your install, those details are from this install I'm posting from.

Rather than run that command in a terminal all the time or enter it fully in a desktop config file I create a script in ~/bin to hold it called "nightly". Note the lower case "N" used in the script name "nightly", differentiates the script from the profile with the capital "N". 

My script here, change the path and Profile name to suit how you saved your profile etc.
Open a text editor (gedit) and copy in the following contents of the code box in full **changing the path and Profile name to suit your install** ...
> ```
#!/bin/bash
#
# Start firefox nigthly with the Nightly profile.
#
#

$HOME/bin/firefox-nightlies/firefox/firefox -P "Nightly" $1
``` Note: the $1 at the end of the path allows the script name to be fed a URL eg. "nightly http://www.google.com" will open the google search page in Firefox nightly from the command line.

This is saved in ~/bin/nightly (_*yours would be saved as ~/bin/developer if you called the Profile "Developer"*_ ) which is in the system path, as such you can launch your browser just by,in my case, typing "nightly" (again note the lower case "N").  Right click the script you create in ~/bin and open the properties dialog, click on the permissions tab, then tick the box "Allow executing file as program". This sets the script as executable.

**NB.** if you have to create the folder ~/bin, do a log out of the desktop and then log back in, this will initiate the folders use in the system path, only needs doing once and it is permanently set up for use.

Now any desktop launchers (desktop configuration files) or terminals just need "nightly (or "developer" ;))" entered to fire up the browser even if iceweasel (firefox in your case) is already running. You can separate the 2 like in this use case, or run multiple versions more generally speaking with a separately named profile and script for each version.

If you mess up and lose all your settings or render the browser rather blank (lose bookmarks, extensions etc), you can recover to the initial state from the backup on your Desktop. 

To recover, (only use this if you've created the backup "mozilla-BAK" in Step 1. please)
Close all firefox/developer version windows. 
Open your home folder, show hidden files/folders (pressing the "ctrl + h", keyboard combination will do so). Open the ".mozilla" folder and delete everything inside, leave the empty ~/.mozilla folder open.
Open the backup on the desktop, copy / paste the contents of the Desktop folder backup to the open ~/.mozilla folder. Restore is complete. Restarting firefox should have the initial set up back in place.

Take care following this and good luck, coldcritter64

---

### Post by Neil_Nand on 2014-12-01
Sorry for taking so long to get back to you.

I tried those steps but couldn't seem to get it to work, I think I might just be better off downloading Firefox from their website and running it directly from that rather than trying to revert my now permanent developer edition back to the non-developer one.

When I download Firefox from their website where is the best place in the file system to put them?

Thanks for putting in the time for the tutorial though, it's much appreciated.

---

### Post by patrick88 on 2015-05-14
I'm trying to do this but I'm getting the following error on the command:

> firefox -P

> (process:31895): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed



Afterwards a new firefox window opens.

EDIT

Nevermind, tried it without firefox open and it worked.

EDIT 2:

The opt/firefox-developer/firefox/firefox -P "Dev" command just opens up normal firefox though . . .

---

