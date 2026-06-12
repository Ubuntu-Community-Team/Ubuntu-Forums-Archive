---
title: "Clean install BUT before I do I need"
date: 2018-07-04
forum: New to Ubuntu
---

### Post by dave6 on 2018-07-04
Hi all
Just getting round to do a clean install of Ubuntu with Ubuntu Mate 18.04 LTS.  But before I do, I need to backup my book-marks and passwords for firefox and I don't remember how to.
I know there is more than one way of doing it, there is some way of backing up and moving firefox also a file with a name like jusson (that is a mis-spell) hiding some where 

Open to known ways of doing this which work.

Thanks
Dave

---

### Post by TheFu on 2018-07-04
Backup your HOME.
Install fresh.
Restore your HOME.

---

### Post by yancek on 2018-07-04
In firefox click on the Bookmarks tab and then Show all Bookmarks and you should see an option to Import and Backup.  Should be straightforware from there.  You should also have a hidden .mozilla directory in your user /home directory with a firefox sub-directory.  CHeck for the file you want there.

---

### Post by dave6 on 2018-07-04
TheFu.. Does that not just put all the junk back into a fresh install ? As I have 2 user's in there and I think that is the root of my problem.

Yancek, have my bookmarks backed-up now.  That hidden file .mozilla is that the one that holds the passwords ? As when I do the following   "starting off with silly bar on left:" files / computer / home / da-boss (that's my user name) I can't find a firefox folder never mind a firefox sub-directory 

I am getting there lads, just bear with me, cuz I am stupid

Dave

---

### Post by leunam12 on 2018-07-04
/home/da-boss/.mozilla/firefox

To backup insert a USB stick, create a folder named "firefox" in it (no quote marks) and then do:```
rsync -av /home/da-boss/.mozilla/firefox/ /media/da-boss/USB-STICK/firefox/
```Make sure to replace USB-STICK with the real name for you USB stick. If you are not sure type lsblk (enter) on terminal and check the MOUNTPOINT column.

---

### Post by dave6 on 2018-07-04
Thanks leunam12, err I can't find the terminal and I have looked under keyboard short cuts

Dave

---

### Post by SeijiSensei on 2018-07-04
Firefox settings are stored in the .mozilla subdirectory of your home. Filenames that begin with a period are "hidden" and do not appear in normal directory listings. You can see them from the command prompt with the command "ls -a". In a graphical file manager try hitting Alt+period.

---

### Post by TheFu on 2018-07-04
> **dave6 said:**
> TheFu.. Does that not just put all the junk back into a fresh install ? As I have 2 user's in there and I think that is the root of my problem.

$HOME is per-userid.  All userid settings and almost all data files are stored there - per user.
If you don't want to backup something, don't. Completely up to you.  System settings are NOT stored in $HOME. If your $HOME has junk you don't want, delete it or don't include it in the backup.

If you want to see if an issue is system-wide or just for 1 userid, create a new userid, logout and log into that new user, run the program. All better or not?

If you aren't already familiar with using the shell/terminal/cli (all effectively mean the same thing), just copy/paste using whatever file manager you like. rsync probably isn't something you should attempt first time in a shell, unless you really want to learn that part of the OS.  If you do want to learn it, GREAT!  Let us know.

---

### Post by leunam12 on 2018-07-04
Ctrl+Alt+T usually opens the terminal.

---

### Post by dave6 on 2018-07-04
OK lads, thank you all very much, but you are now getting over my head, put it this way to you. when you jump into a car, do you really want to know how the wiring loom works ? No, but if the light fails you may want to know how to replace it.

OK, I know I now have my book marks backed up, it just leaves the passwords, and I think there is about 150, as you know, every site you go to "including this one" they want you to use a user name and keep a password (safe) 
The back up thing onto a usb memory stick, after doing the above code and letting terminal run "had to go out to work for a few hours" it said some thing about files going missing before being copied, which I did not copy to paste here.

Easy way to copy hidden pass words then paste them back into new fresh Ubuntu Mate 18.04 lts

Dave

---

### Post by oldfred on 2018-07-05
I just back up entire Firefox & Thunderbird profiles.
I think I am running the same profile for about 10 years, multiple systems and versions. Same profile in old XP (long retired) and Ubuntu.

Firefox & Thunderbird use same type of profiles, just different paths.
       [http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced](http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced)
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox) 
    
When I am using a new Ubuntu, I load Firefox once to get a default profile. Then copy my profile over & edit profile.ini to use my old profile not newer one, just created. There also is a way to choose which profile to use from within Firefox, but never used that.

---

### Post by dave6 on 2018-07-05
Hi oldfred
When you back up firefox, "I don't have or use Thunderbird" does that include the saved passwords, if it does, how do you do it, as I can find nothing in this version of Ubuntu, it was yourself that told me about Ubuntu Mate and I have had it running off the DVD may have been version 16 as version 18 won't run for me as yet
How do I find the firefox folder ?

Dave

---

### Post by SeijiSensei on 2018-07-05
As I said before, everything related to firefox is stored in the "hidden" directory /home/yourusername/.mozilla.  For thunderbird, it's the directory /home/yourusername/.thunderbird.  See [https://vuquangson.com/show-hidden-files-folders-ubuntu-18-04-lts/](https://vuquangson.com/show-hidden-files-folders-ubuntu-18-04-lts/) for details on hidden files.

---

### Post by dave6 on 2018-07-05
SeijiSensei, could you please tell me how and where in ( screen shot ) the hidden file is hiding, still don't have or use thunderbird

Thankyou
Dave

---

### Post by oldfred on 2018-07-05
If running from DVD, you will not have saved files on DVD as it is not writable. You may have some data in RAM memory, but when you reboot that is gone.

What do these show, it is lowercase LL.
fred@bionic-z97:~$ ll ~/.thunderbird
fred@bionic-z97:~$ ll ~/.mozilla/firefox

---

### Post by Habitual on 2018-07-05
[https://help.ubuntu.com/community/HomeFolder#Back_Up_Your_Home_Directory](https://help.ubuntu.com/community/HomeFolder#Back_Up_Your_Home_Directory)

---

### Post by deadflowr on 2018-07-05
> **dave6 said:**
> SeijiSensei, could you please tell me how and where in ( screen shot ) the hidden file is hiding, still don't have or use thunderbird

Thankyou
Dave

Up in the toolbar at the right, click on the last icon (to the right of the magnifying glass) and scroll down to show hidden file/folders.
Or press ctrl + H on the keyboard)
that'll give access to hidden folders.

---

### Post by dave6 on 2018-07-06
Thanks deadflowr
Found it ! which brings up the next problem of why "maybe" my INTERNET is so dam slow, the firefox folder is 46.6kb in size while firefox old "which I got from Ubuntu 12" is 36MB in size.
So with that in mind, the only thing now I want is to back up my passwords ( ONLY PASSWORDS ) and "IF" I can ever get the software to run to write a new DVD for ( Ubuntu Mate 18.04 LTS ) and do a clean install from there or it, I can then resort my book marks which are backed up and then restore my passwords, about 150

Dave

---

### Post by dave6 on 2018-07-06
Habitual
You got that bit right and I have proved it
Quote

"Windows assumes the user is an idiot.
Linux demands proof."

End Quote

Dave

---

### Post by oldfred on 2018-07-06
Some details here on transferring data to new profile:
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

Updated link
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)

---

### Post by dave6 on 2018-07-07
oldfred
Bad news, none of your links work

Dave

---

### Post by #&amp;thj^% on 2018-07-07
> **dave6 said:**
> oldfred
Bad news, none of your links work

Dave

I can also verify:
> 
404 - File or directory not found.
The resource you are looking for might have been removed, had its name changed, or is temporarily unavailable.

This one works though: [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2018-07-07
All the ones that are [http://kb.mozillazine.org](http://kb.mozillazine.org) are obsolete.

there are now here [https://support.mozilla.org](https://support.mozilla.org), for example:
[https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile](https://support.mozilla.org/en-US/kb/recovering-important-data-from-an-old-profile)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)

---

### Post by dave6 on 2018-07-07
Thanks old Fred
I think I will call this thread closed, WHY ?
I posted a couple of replies on here, had downloaded a new copy of Ubuntu Mate 18 so I burnt it to disk, came back to the computer to check an email opened firefox to find it had updated to version 60 and wiped out all passwords bookmarks, the lot.
On to wifes chrome book which still has the link to ubuntu forums and read the above, I did make a copy of firefox (some-how) done a copy ctl+C found the folder "hidden folder" then cltr+V "see I do know key-brd shortcuts" restarted firefox... Ya-hoo all back and now I am running version 61 of firefox.

If I could only get the DVD disc to work, see other post under the name of Faulty download or disc.

So, a big thank you to all that took the time to answer..
Dave

---

