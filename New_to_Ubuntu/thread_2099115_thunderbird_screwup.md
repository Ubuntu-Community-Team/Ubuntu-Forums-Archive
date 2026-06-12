---
title: "thunderbird screwup"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by pgte3 on 2012-12-28
Maybe someone can help me. I have messed up my thunderbird email client. I am trying to figure out why I could not change a setting within thunderbird, so I started thunderbird with in a terminal window (sudo thunderbird), thunderbird came up as if it was new with no accounts etc. I close it, and now when I start thunderbird normally (desktop icon) it starts as if new with no accounts etc. What have I done, how do I correct it?

---

### Post by GreatDanton on 2012-12-28
In terminal type:
```
thunderbird
```I just tried your combination and it's working. Just to let you know: for graphical apps instead of sudo we use **gksudo**.

---

### Post by howefield on 2012-12-28
Opening thunderbird with root has done just that, opened the application as another user, ie root and not you, so no accounts would show for it.

Btw, opening a graphical application as root is usually better done with gksudo.

I can't replicate your issue, as having opened as root, and now opening normally my accounts are showing.

Do you have a backup of your ~/.thunderbird folder ?

---

### Post by pgte3 on 2012-12-28
typed thunderbird, same issue, comes up as if "new", no accounts etc.

---

### Post by GreatDanton on 2012-12-28
oic, previously I typed gksudo and it was working. Now I tried sudo thunderbird and also screwed mine =).

---

### Post by howefield on 2012-12-28
For me, gksudo opens with new profile, and sudo opens with my accounts showing but messes some of the permissions.

I expect you have messed the permissions on your .thunderbird/* folder.

---

### Post by Paddy Landau on 2012-12-28
When you use [FONT=Lucida Console]sudo[/FONT], it uses *your* home folder instead of root's.

That is why you should use either [FONT=Lucida Console]sudo[/FONT] [FONT=Lucida Console]-H[/FONT] or [FONT=Lucida Console]gksudo[/FONT], especially for graphical applications (which tend to save data into the home folder). These use root's home folder, not yours.

It is quite possible that your Thunderbird folder is now set to belong to root, and therefore you cannot use it.

Close Thunderbird (if open); open a terminal ([FONT=Lucida Console]Ctrl[/FONT]+[FONT=Lucida Console]Alt[/FONT]+[FONT=Lucida Console]T[/FONT]); enter the following command, which will prompt for your password. (You can use the mouse and right-click to copy-and-paste, preventing typing errors.)
```
sudo chown --recursive ${USER}:${USER} ~/.thunderbird
```After the command has run (which should take only a second or two), close your terminal window and try Thunderbird again properly (**not** using [FONT=Lucida Console]sudo[/FONT] or [FONT=Lucida Console]gksudo[/FONT]!).

---

### Post by GreatDanton on 2012-12-28
```
sudo chown --recursive ${USER}:${USER} ~/.thunderbird
```Unfortunately this is not the solution. 

I think the problem is in /home/.thunderbird/profiles.ini
This is what is in:
```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=ow36bc90.default

```Thunderbird somehow thinks that the last profile is the default profile. So how do I change that to the profile 0 (which is I assume my profile)?

---

### Post by howefield on 2012-12-28
> **GreatDanton said:**
> ```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=ow36bc90.default

```Thunderbird somehow thinks that the last profile is the default profile. So how do I change that to the profile 0 (which is I assume my profile)?

Don't think that is the issue either, that is exactly the same as my (good) profile.ini (except of course for the foder name in the Path field)

Did you really try screwing thunderbird up without having a tar ball of your existing ~/.thunderbird ? ;-)

---

### Post by GreatDanton on 2012-12-28
> **howefield said:**
> 
Did you really try screwing thunderbird up without having a tar ball of your existing ~/.thunderbird ? ;-)

Yes. Actually I am doing this just for fun. I don't have any important mails anyway, and I can set up my accounts in few minutes. But what can I learn if I just leave the problem behind?

---

### Post by pgte3 on 2012-12-28
This did not seem to work:

sudo chown --recursive ${USER}:${USER} ~/.thunderbird

It does seem like a permissions thing...I see what looks like all my account stuff in ~/.thunderbird/o6a7vfuy.default

Running sudo thunderbird changed something, but what?

---

### Post by pgte3 on 2012-12-28
For completeness my profile looks like this:

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=o6a7vfuy.default

---

### Post by Elmer Fudd on 2012-12-28
When you go to (in a file manager) home/.thunderbird, how many profiles to you see in that directory. If you have multiple profile directories you can go into account settings/server settings and browse for the "local directory" and try the different ones.  You may recover your original dataset that way.

---

### Post by pgte3 on 2012-12-28
one... profile.ini

---

### Post by howefield on 2012-12-28
When you try the command 

```
ls -l ~/.thunderbird/o6a7vfuy.default
```

does root appear to control any of the files/folders ?

---

### Post by steeldriver on 2012-12-28
You could also try starting in profile manager mode

```
$ thunderbird -ProfileManager
```instead of rooting around the filesystem for the rogue profile?

[https://support.mozillamessaging.com/en-US/kb/using-multiple-profiles](https://support.mozillamessaging.com/en-US/kb/using-multiple-profiles)

 Maybe it created a profile for root in /root and is trying to load that?

---

### Post by pgte3 on 2012-12-28
ls -l ~/.thunderbird/o6a7vfuy.default

-rw-rw-rw-  1 peter peter     1373 Dec 19 19:52 abook.mab
-rw-rw-rw-  1 peter peter   524288 Dec 19 18:22 addons.sqlite
-rw-rw-rw-  1 peter peter   524288 Dec 19 18:18 blist.sqlite
-rw-rw-rw-  1 peter peter    27897 Dec 27 16:00 blocklist.xml
drwxrwxrwx 18 peter peter     4096 Dec 28 14:18 Cache
-rw-rw-rw-  1 peter peter        1 Dec 28 18:13 _CACHE_CLEAN_
-rw-rw-rw-  1 peter peter    65536 Dec 28 18:13 cert8.db
-rw-rw-rw-  1 peter peter    98304 Dec 19 18:18 chromeappsstore.sqlite
-rw-rw-rw-  1 peter peter      157 Dec 19 19:48 compatibility.ini
-rw-rw-rw-  1 peter peter   229376 Dec 20 20:38 content-prefs.sqlite
-rw-rw-rw-  1 peter peter   524288 Dec 28 14:24 cookies.sqlite
-rw-rw-rw-  1 peter peter       36 Dec 28 14:32 directoryTree.json
-rw-rw-rw-  1 peter peter      417 Dec 19 18:18 extensions.ini
-rw-rw-rw-  1 peter peter   458752 Dec 19 18:18 extensions.sqlite
-rw-rw-r--  1 peter peter      100 Dec 28 18:13 folderTree.json
-rw-rw-rw-  1 peter peter 13598720 Dec 28 14:24 global-messages-db.sqlite
-rw-rw-rw-  1 peter peter     1730 Dec 25 10:33 history.mab
drwxrwxrwx  5 peter peter     4096 Dec 20 17:45 ImapMail
-rw-rw-rw-  1 peter peter    22094 Dec 28 14:21 impab.mab
-rw-rw-rw-  1 peter peter        0 Dec 28 14:30 Invalidprefs.js
-rw-rw-rw-  1 peter peter    16384 Dec 28 18:13 key3.db
-rw-rw-rw-  1 peter peter     8112 Dec 28 14:30 localstore.rdf
drwxrwxrwx  7 peter peter     4096 Dec 20 15:10 Mail
-rw-rw-rw-  1 peter peter      482 Dec 19 18:18 mailViews.dat
drwxrwxrwx  2 peter peter     4096 Dec 19 18:18 minidumps
drwxrwxrwx  2 peter peter     4096 Dec 28 14:30 OfflineCache
-rw-rw-rw-  1 peter peter    13198 Dec 28 14:30 panacea.dat
-rw-rw-rw-  1 peter peter    65536 Dec 28 14:30 permissions.sqlite
-rw-rw-rw-  1 peter peter 10485760 Dec 20 15:33 places.sqlite
-rw-rw-rw-  1 peter peter     3219 Dec 20 12:45 pluginreg.dat
-rw-rw-r--  1 peter peter     2908 Dec 28 18:13 prefs.js
-rw-rw-rw-  1 peter peter    16384 Dec 19 18:18 secmod.db
-rw-rw-r--  1 peter peter       86 Dec 28 18:13 session.json
-rw-rw-rw-  1 peter peter   327680 Dec 20 12:58 signons.sqlite
drwxrwxrwx  2 peter peter     4096 Dec 19 19:49 startupCache
-rw-rw-r--  1 peter peter       10 Dec 28 18:13 virtualFolders.dat
-rw-rw-rw-  1 peter peter    98304 Dec 28 18:13 webappsstore.sqlite

---

### Post by Elmer Fudd on 2012-12-28
Try this.
Open nautilus. Make sure that View/"Show hidden files" is selected
Navigate to the .thunderbird directory (where the profile.ini is located) and see if you have alternate profile **directories** (like /o6a7vfuy.default). Note the name of the other profile directories.

Then edit the profile.ini by replacing Path=ow36bc90.default with Path=theotherprofiledirectorynamethatyoufound.default

restart Thunderbird.

Worked for me, but may be because I screwed mine up in a different way.

---

### Post by pgte3 on 2012-12-28
Well change the thread title from Thunderbird screwup to Thunderbird really big screwup.

I tried to use the ProfileManager as suggested in a previous post, and created a new profile and started with it. It did not help. I chose the profile path of where my profile.ini was. I then used the ProfileManager and deleted the new profile I created and it gave a message about cleaning up directories and files related to the new one, I said yes. It deleted the entire ~./thunderbird directory...bye bye all my stuff. It is my own dam fault for screwing around with sudo in the first place without understanding what it might do to Thunderbird.

I started Thunderbird and rebuilt my email accounts and it is now working, but old emails (not too many) are gone. Hard lesson, live and learn hopefully.

Thanks for all the help.

---

### Post by Elmer Fudd on 2012-12-28
> **pgte3 said:**
> Well change the thread title from Thunderbird screwup to Thunderbird really big screwup.

I tried to use the ProfileManager as suggested in a previous post, and created a new profile and started with it. It did not help. I chose the profile path of where my profile.ini was. I then used the ProfileManager and deleted the new profile I created and it gave a message about cleaning up directories and files related to the new one, I said yes. It deleted the entire ~./thunderbird directory...bye bye all my stuff. It is my own dam fault for screwing around with sudo in the first place without understanding what it might do to Thunderbird.

I started Thunderbird and rebuilt my email accounts and it is now working, but old emails (not too many) are gone. Hard lesson, live and learn hopefully.

Thanks for all the help.

Could you do me a favor and open nautilus. Select the "Go" menu and selcct "Trash" and let me know if the /.thundebird directory is there.
If so, may be able to recover your old emails. Even if you don't care, I would like to know if the way the directory was deleted left it in the trash.
thanks

---

### Post by pgte3 on 2012-12-28
The trash folder does not have any of the Thunderbird files or directories in it. Thanks again for your suggestions.

---

