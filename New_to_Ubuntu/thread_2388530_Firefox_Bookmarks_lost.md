---
title: "Firefox Bookmarks lost"
date: 2018-04-04
forum: New to Ubuntu
---

### Post by dave1956 on 2018-04-04
Hi all
Decided to start a new post on this.  I upgraded from Ubuntu 12 to Ubuntu 16 and in the process: 1, I forgot to backup my bookmarks from firefox and 2nd during the upgrade I miss-spelt my user name on the computer.. 
So, I now have 2 users on the computer and ALL my files are under the old user name

Does any one know how I could rescue my bookmarks from the old user which was running firefox ver ( 34 ? )

There would be about 100+ bookmarks, I did backup the passwords, I just forgot the blinking bookmarks
Can any one help with this please

Thanks 
Dave ):P

---

### Post by &amp;KyT$0P# on 2018-04-04
The bookmarks are stored in [FONT=Courier New]places.sqlite[/FONT] in the old Firefox [profile]("https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data#w_finding-your-profile-without-opening-firefox").  If it doesn't work to completely quit Firefox, then copy [FONT=Courier New]places.sqlite[/FONT] from the old profile to the new profile, try restoring your bookmarks [this way]("https://support.mozilla.org/en-US/kb/restore-bookmarks-from-backup-or-move-them#w_using-a-bookmark-backup-file").

If your old user account had a different uid than your current user, you might need to use [FONT=Courier New]chown[/FONT] after copying files -
```
sudo chown <you>: places.sqlite
```
replacing <you> with your current username

---

### Post by yancek on 2018-04-04
Check the Mozilla link below, scroll down to the section "Finding your profile without opening firefox".  The places.squlite file should be there.

[https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data](https://support.mozilla.org/en-US/kb/profiles-where-firefox-stores-user-data)

In firefox you should familiarize yourself with the backup/restore option.  Click on Bookmarks, click on Show all Bookmarks and you will see an optio to select backup or restore.

---

### Post by oldfred on 2018-04-04
I regularly copy entire profile for both Firefox & Thunderbird from one install to another. And then edit profile.ini with correct info on my standard profile.

       Firefox
[URL="http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox"]http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox
      [/URL]
 [http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced](http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced)
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile) 
    [URL="http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox"]
[/URL]

---

### Post by usama947 on 2018-04-05
[FONT=arial]**-FIRST,** [/FONT][B]Firefox automatically creates backups of yourbookmarks, which can be helpful if your bookmarks arelost or missing.
-Click the Bookmarks button (or >Bookmarks) and select Show All Bookmarks. 
-At the top of the Library window, click on Import and Backup and select Restore.
- HOPE IT HELPS YOU ![/B]

---

### Post by dave1956 on 2018-04-05
> **oldfred said:**
> I regularly copy entire profile for both Firefox & Thunderbird from one install to another. And then edit profile.ini with correct info on my standard profile.

       Firefox
[URL="http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox"]http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox
      [/URL]
 [http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced](http://kb.mozillazine.org/Moving_your_profile_folder#Modify_profiles.ini_to_point_to_the_new_location_-_Advanced)
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile) 
    [URL="http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox"]
[/URL]

Ah, but can you install all your passwords, as I have now discovered password exporter does not work with firefox 57 and above

Dave

---

### Post by dave1956 on 2018-04-05
Hi lads, or maybe lassie's
Did not get time yesterday to post on here to thank you both (halogen2 and yancek) for your help + the wifes chrome book.  I done the no use firefox but found the [FONT=Courier New]places.sqlite files and done the copy paste..  And I have just discovered in the last 15 minutes that the password exporter does not work with this version of firefox.... Which is a bit strange as every web site wants you to log in and save a password
Maybe there is some thing different that can do the import of passwords.
And now you know why I try to avoid doing upgrades, not worth the hassle
Time to kill this thread, thanks all

Dave
[/FONT]

---

### Post by oldfred on 2018-04-05
When I copy the entire profile all my passwords are also copied.

I am retired and live part time (Winter) in Fla and in Ill (Summer). Two different desktop systems and I backup to flash drive(s) and restore entire profile to my other system.
Everything is the same in both systems.

---

### Post by SeijiSensei on 2018-04-05
I just copy the entire ~/.mozilla directory to my home directory on a new installation.

---

### Post by dave1956 on 2018-04-05
Oldfred and SeijiSensei
That is interesting, when you say entire .mozilla directory would that be the one hiding (this is from memory) computer/drive/home/user/home/firefox yes I know it looks strand, bearing in mind I messed up the upgrade computer user bit, I am watching TV using wife's chrome book

Dave

---

### Post by yancek on 2018-04-05
> computer/drive/home/user/home/firefox

Strange path.  In a standard Ubuntu 16.04, the files you are looking for would be in:  /home/user/.mozilla/firefox.  Not the dot/period before mozilla.  That means it is a hidden file.  To access it in nautilus file manager, open nautilus in your /home/user directory, click on the View tab and click on show hiddent files.  o

---

### Post by dave1956 on 2018-04-06
Yes worked, just have to mark this thread as solved.

Thanks all

Dave

---

