---
title: "HOW-TO: Share Firefox/Thunderbird profiles between *buntu/Windows/OS X"
date: 2009-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by SentientFluid on 2009-04-26
[SIZE="3"][COLOR="Red"]Disclaimer: This is meant to provide general instructions on how to share your Firefox/Thunderbird profiles between operating systems on multi-boot systems.  It assumes you know the basics for sharing files/folders between the different operating systems on your computer, as well as the basics for copying/moving files/folders and navigating within the different operating systems.  You could theoretically share the profiles between multiple computers across a network, but that is beyond the scope of this post.[/COLOR][/SIZE]

When I first started using Ubuntu I dual-booted with Windows XP because some programs/devices I used weren't supported in Linux well enough. Back then my main pet peeve was that all my Firefox bookmarks and Thunderbird email was on my XP partition.  It was annoying trying to keep them both up to date. So I found out how to share the profiles between the 2 operating systems.

Just a note here, since the instructions for doing this with Firefox and Thunderbird are essentially the same, I'm just going to talk about Firefox and note the difference for Thunderbird.

Both Ubuntu and XP need to have read & write access to the location you're going to store your FF/TB profile.  When I did this in the past, NTFS support in Ubuntu wasn't all that reliable so I created a smallish FAT32 partition to store it (and other files) in.  Later on I moved it to my home folder in Ubuntu, and [gave ext2/3 support to XP]("http://www.fs-driver.org/").  I then just had FF/TB in XP read directly from my Ubuntu partition.

Anyway, here are the steps...

1. **Decide where you want your shared profile stored.**

[INDENT]This is up to you.  Some possibilities are:
[LIST]
[*]In /home/*username* on your Ubuntu partition.
[*]In C:\Documents and Settings\*XPusername*\Application Data\Mozilla\Firefox\Profiles.
[*]In a random folder on any partition that both Ubuntu and XP have read & write access to.
[/LIST]
Remember, if you're storing it on your Ubuntu partition, then XP will need the ext2 driver I linked to above otherwise it won't recognize your Ubuntu partition.  If you're storing it an NTFS XP partition, then make sure your version of Ubuntu can read/write to NTFS drives.[/INDENT]

2. **Locate the Firefox profile that has all your bookmarks, etc that you want to share.**
[INDENT]In all these locations you will see a folder whose name will be a series of random characters such as "ytlq1wlb.default".  Write it down and label it Firefox or Thunderbird so you know which is which.  When I refer to your **Profile Folder**, *this* is the one I am talking about. It holds all the information on your bookmarks, add-ons, toolbars, etc. This is the folder we are going to tell Firefox to use in each OS.
[INDENT]**In Ubuntu** (and Linux in general):
```
/home/*username*/.mozilla/firefox/
```
*.mozilla* is a hidden folder.  In Nautilus (since I use Gnome) you can show these by pressing Ctrl+H or View > Show hidden files.

**Note**: In Debian/Ubuntu builds of Thunderbird, you'll find your TB profile in **/home/*username*/.mozilla-thunderbird**.  Other TB builds will store it in **/home/*username*/.thunderbird**.  Both *.thunderbird* and *.mozilla-thunderbird* are hidden folders.

**In XP**:
```
C:\Documents and Settings\*username*\Application Data\Mozilla\Firefox\Profiles\
```
*Application Data* is a hidden folder.  Tools > Folder Options > View tab > "Show hidden files and folders" checkbox will let Windows Explorer see these.

**In Vista**:
```
C:\Users\*username*\AppData\Roaming\Mozilla\Firefox\Profiles
```
*AppData* is a hidden folder.  Organize > Folder and Search Options > Folder Options > View tab > Show hidden files and folders will let you see it.

And just for the heck of it, **in OS X** it's one of these:
```
Macintosh HD/*username*/Library/Mozilla/Firefox/Profiles/
Macintosh HD/*username*/Library/Application Support/Firefox/Profiles/
```
Neither were hidden last I checked.[/INDENT]

**MAKE A BACKUP OF THIS FOLDER**.  You're not going to be doing anything dangerous but accidents happen. I've accidentally dropped files/folders into bad places.  Better to err on the side of caution, I always say.
[/INDENT]

3.  **Move/Share this folder.**
[INDENT]I created a folder called Mozilla Profiles on a drive that both XP/Ubuntu had read/write access to.  I then moved the **Profile Folder** (remember, it's the one with the random characters for a name) into my Mozilla Profiles folder.

You essentially want to do the same. It's fine to leave it where it is so long as both operating systems have read/write access. You'll need to make sure the profile folder is shared.[/INDENT]

4. **Tell Firefox to use the Profile Folder we found in step 2.**
[INDENT]To do this we'll need to use Firefox's Profile Manager:
a. Quite Firefox completely.  You may want to print/write these instructions, or view the in a different browser.
b. Start the Firefox Profile Manager
[INDENT]In Ubuntu, open Terminal and type:
```
firefox -profilemanager
```
In Windows (XP or Vista) press the Windows Logo key and R then type:
```
firefox.exe -profilemanager
```
In OS X open Terminal (from your Utilities folder) and type:
```
/Applications/Firefox.app/Contents/MacOS/firefox -profilemanager
```

If you did it correctly you'll see the Firefox Profile Manager window.

c. Click the Create Profile button, then click Next.

d. Enter a Profile name.  I used "Shared Profile".  I like this simple. :)

e. Click Choose Folder and navigate into the **Profile Folder** from step 3.  Click Open (or OK, or whatever the button says).

f. Click Finish.

g. Make sure your Profile name you entered during step d is selected and there is a checkmark next to "Don't ask at startup".

h. Click Start Firefox.

You should now be looking at Firefox with all your bookmarks and other settings.[/INDENT]

Repeat these steps for Firefox in each OS that doesn't already have access to the shared profile.  Make sure to use the same Profile name in step d.

It's important to note that the Ubuntu Firefox builds aren't updated at the same time as the regular Firefox builds in Windows and other operating systems.  If the versions don't match, then it's possible some of your Firefox add-ons will be disabled in Ubuntu. Correcting this is beyond the scope of this post so please be forewarned.

[/INDENT]

---

### Post by bodhi.zazen on 2009-04-26
Moved to Tips and Tutorials.

The only thing I would add, just be aware of two things :

1. Windows does not support permissions. So, if you do not know how to set permissions of FAT / NTFS partitions see : 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

2. Just beware of sharing your entire windows or Ubuntu partitions as there *may* be security implications, especially with firefox. Be sure to scan the shared drive and anyting you download with antivirus / antimalware from windows from time to time. IMO probably best to set up a shared data partition.

---

### Post by angussf on 2009-05-13
I find there are some important extensions and even Firefox default settings that unfortunately have path info coded into them.  Since Linux and Windows paths are incompatible, these extensions prevent one from sharing a profile and the default settings might be a cause of some instability in FF.

Two extensions that I know have path info and subsequent problems: BetterPrivacy and FEBE.  BetterPrivacy requires the Flash Player LSO directory, and FEBE requires a backup directory.  Every time I have copied a profile from Linux to Windows or vice versa, I've had to edit these settings immediately or Firefox gets wonky on me.

I see path info for Brief and for DownThemAll as well in my prefs.js.

For BetterPrivacy, under Windows the default is "C:\Documents and Settings\Username\Application Data\Macromedia\Flash Player", while under Linux the default is /home/username/.macromedia/Flash_Player.  BetterPrivacy throws errors until I fix the path.

FEBE requires the user to enter the path to the backup directory where FEBE backups are stored.  Under Windows this might be something like D:\Backups\Firefox while under Linux it might be something like /home/username/Backups/Firefox ... FEBE doesn't fail with errors, it just won't make the backups AND it doesn't tell you it can't, it just fails silently.

It's not just add-ons that have this issue; there are paths in global settings in prefs.js:

In Windows you have several paths, among them these:
user_pref("browser.download.dir", "D:\\Data\\Downloads\\Internet\\Firefox");
user_pref("browser.download.lastDir", "D:\\Data\\Downloads\\Utilities\\Undelete Tools");
user_pref("browser.cache.disk.parent_directory", "C:\\DOCUME~1\\Angus\\LOCALS~1\\APPLIC~1\\Mozilla\\firefox");

In Linux these might be:
user_pref("browser.download.dir", "/home/username/Downloads");
user_pref("browser.download.lastDir", "/home/username/WinShared");

Interestingly my Linux FF has a Windows cache path:
user_pref("browser.cache.disk.parent_directory", "C:\\DOCUME~1\\Username\\LOCALS~1\\APPLIC~1\\Mozilla\\firefox"); 
and yet it seems to work fine, ignoring the bogus path and storing the cache files in the default location of /home/username/.mozilla/Firefox/Profiles/[random].default/Cache

It would be a Good Thing if Mozilla worked out some OS-independent way of handling paths so profiles could be shared across OSes.  I have no idea how this could be done easily.  Unfortunately so few people would benefit from ths that it might not be a worthwhile use of programming time.  OTOH this might be something worth addressing in specs for FF 4.0

---

