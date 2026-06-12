---
title: "Lost all my settings"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Nesaskewatch on 2011-10-15
Hi there.  I just did a fresh install of 11.10 with a separate home partition.  All went well, as it always does, except when it asked if I wanted to import any settings from previous user (I changed my computer and user names) I selected no for some reason...  Needless to say all my bookmarks, emails and some other things vanished.  Is there some way to recover these items so I can import them to the new install?  

Thanks very much for any assistance.  I really need some of those emails.  I didn't bother backing up this time as it is so routine to upgrade with the separate home, but like I said, for some reason I selected no when it asked if I want to import settings etc.  Aaaaarg.  I notice Tbird is the new default email client.  I was using evolution on the previous install.  Any hope there?

Cheers!

---

### Post by Nesaskewatch on 2011-10-15
Just to add a bit of info.  

When I upgraded I did _not_ select format for my home partition, thinking that would save all settings, but I did format root.  I am wondering if I messed up in changing my user name and computer name?  As I said, if I can recover the emails that were in Evolution I would be very happy.  I can live with losing a few bookmarks and some other piddly things.  Even with the user name change, isn't the data from the previous version carried over as long as the home partition was not formatted?  

Thanks again.

---

### Post by gsmanners on 2011-10-15
If all you did was change the user name, then those files should still be on your drive, though I'm not completely certain you can access them. You *should* be able to just copy what you need from the old home folder to the new one, though you definitely want to make backups first in case something important gets messed up.

---

### Post by JKyleOKC on 2011-10-15
> **Nesaskewatch said:**
> I am wondering if I messed up in changing my user name and computer name?  As I said, if I can recover the emails that were in Evolution I would be very happy.Changing your user name is almost certainly what caused your settings and data to vanish. Since you have a separate /home partition, they are probably still there. Try looking in the /home folder; you should see at least two directories there, one with your original user name and the other with your new user name. Your settings and data should be in the one with the original user name, while your new system will be looking for them in the one with the new user name.

Since the file system tracks file and folder ownership by "User ID" which is a number rather than a name, it's quite possible that the update assigned the same number to your new name that was previously used by the old one. Try navigating into the folder with the old name and see if you can view the properties of any files there. If the number was reused, it should show your new name as the owner of the file -- and if it does, you can simply copy the files from the old directory over to the new one to bring everything back.

However, be sure to back up everything in both directories before you try this, just in case anything goes wrong. Keep in mind that many of the settings will be in "hidden" files whose names begin with a period; press ctrl-h when viewing the folder content to make them visible, and don't forget to include all of them in the backup too.

If the UID number did not get reused, the recovery will be a bit more complicated, but so long as the files are still in the old directory, they're not lost and you WILL be able to recover them. We'll cross that bridge if it becomes necessary.

Keep us posted on developments...

---

### Post by Nesaskewatch on 2011-10-16
> **JKyleOKC said:**
> Try looking in the /home folder, you should see at least two directories there, one with your original user name and the other with your new user name. 

It exists!

> **JKyleOKC said:**
> Try navigating into the folder with the old name and see if you can view the properties of any files there. If the number was reused, it should show your new name as the owner of the file -- and if it does, you can simply copy the files from the old directory over to the new one to bring everything back.

I can view file properties just fine, and the new user name is the "owner" under the permissions tab.  I have successfully copied a .png file that I was using as desktop wallpaper for the old user name over to my current desktop.  So far so good.


> **JKyleOKC said:**
> However, be sure to back up everything in both directories before you try this, just in case anything goes wrong

Upgrading with a separate /home partition had become so routine that I stopped backing up anything!  This is a little reminder that Murphy still lurks at every turn.  I copied the entire file to a thumb drive.  

> **JKyleOKC said:**
> Keep us posted on developments...

I will hunt around for a while and see if I can find where the emails may be.  I will repond back here shortly.  At least it appears I did not lose anything.  Huge relief over here!

Cheers!

---

### Post by Lisiano on 2011-10-16
I'll just note that most settings (Evolution and chrome included) are stored in /home/$USER/.config
Firefox stores it's settings in /home/$USER/.mozilla
Pidgin stores it's settings and chat history in /home/$USER/.purple

---

### Post by Nesaskewatch on 2011-10-16
Yep.  Looks like just about everything is still contained in the old user file.  It is a bit over 16 gigs in size.  I am finding all sorts of stuff that I had saved, but finding things like saved emails is way above my pay-grade.  I wonder if I could use that old user file as a login somehow?  Maybe if I create a user in "User Accounts" using the same name as the old user file?  Probably best to wait for any further advice before I do anything permanent.  At least I know the stuff is still there!  I have an old laptop that I never use any longer, so I may start using it as a backup.  Good excuse to finally get around to setting up my home wireless network.  I have a USB transfer cable, but it would be nice to simply send files etc over a wireless network.  Funny how mistakes wind up being valuable learning experiences.  

Cheers again very much!

---

### Post by JKyleOKC on 2011-10-16
Look in the new folder for the files named by Lisiano in post #6 above; if they are there, copy them onto a flash drive in case you need to undo the next step. If not, don't worry. Then switch to the old folder, look for them again there, and copy each of them to the new folder. Finally, log out and back in, or just restart the system. The missing mails should have re-appeared. If you run into problems getting back into your system at the re-login or restart, which isn't very likely to happen, you can copy the files back from the flash drive to undo the changes. If not, you can delete them from the flash drive.

Creating another user with the old user name would not help, since this newly-created user would have a different UID. However copying the needed files from old to new will probably take care of things. Logging in with the old user name might work, however -- might not, either, since the new system probably doesn't have a password for the old user in it.

A separate /home directory doesn't eliminate the need for backups of anything you consider important. All hard drives eventually wear out (although I have some that are more than 10 years old and still working although I don't use them daily, just kept them as backups of what I put on them back then when I junked the rest of the machines that contained them originally) and when the one with your /home partition goes, so does all your data. It's essential to put the backup on a different device to protect against such happenings!

---

### Post by Nesaskewatch on 2011-10-16
I will attempt to do as suggested.  I will report any results shortly.

Thanks for the good advice!

---

### Post by Nesaskewatch on 2011-10-16
A small bit of clarification if I may.  When copying files from old to new, should I copy the entire folder?  Like for Firefox, I copy the whole home/$user/.mozilla file?  Or should I copy only a sub folder -- such as; home/$user/.mozilla/firefox/d3y460yk.default/bookmarkbackups for moving the bookmarks from old to new.  The bookmarks are all I care about there, and I see the version was updated with the new distro.  Would copying the whole .mozilla folder mess up Firefox?.  But I guess for Evolution I should copy the whole folder as I want pretty much the whole app, yes?  

Hope that makes sense.

---

### Post by JKyleOKC on 2011-10-16
> **Nesaskewatch said:**
> A small bit of clarification if I may.  When copying files from old to new, should I copy the entire folder?  Like for Firefox, I copy the whole home/$user/.mozilla file?  Or should I copy only a sub folder -- such as; home/$user/.mozilla/firefox/d3y460yk.default/bookmarkbackups for moving the bookmarks from old to new.  The bookmarks are all I care about there, and I see the version was updated with the new distro.  Would copying the whole .mozilla folder mess up Firefox?.  But I guess for Evolution I should copy the whole folder as I want pretty much the whole app, yes?This is where things can get complicated. If you copy the whole folder, then configuration settings for the newer program will be overwritten by those for the old -- but if you copy only a sub-folder, there might be links that no longer work properly. Specifically, I'm a bit concerned by that "d3y460yk.default" part of the name you cited. That looks like a "unique" name that quite possibly won't be present in the new folder, but there should be a "bookmarkbackups" folder somewhere beneath ".mozilla" in the new one -- and copying just that subfolder from the old directory to replace the one in the new folder should do the trick.

I believe there's an option somewhere in Firefox to import bookmarks from another instance of Firefox, which might be a lot simpler and more foolproof in case they've changed the internal format of the bookmark files. I'm on 10.04 LTS rather than 11.04 or 11.10 so my Firefox is still an older version, so I can't be more detailed than that.

I think the whole folder for Evolution should do what you want. Again, I'm using TBird at an older version so don't know for sure...

---

### Post by gsmanners on 2011-10-16
I think for mozilla, I would rename the new folder to something like .mozilla-new and then simply copy the old .mozilla to the new home folder. Then try running Firefox.

---

### Post by Nesaskewatch on 2011-10-16
I tried just replacing the bookmarks backup folder and it made no difference.  If I look inside the new .mozilla it now shows a .json file that contains all my old bookmarks but in Firefox it only displays the bookmarks added yesterday and today.  I even went into the new folder and removed any .json files dated Oct 14th and on.  Still just the recent "new" bookmarks.  I am going to try replacing the entire .mozilla folder exactly as gsmanners suggests.  If that does not work I will see if there is a way of importing them.  If not, I see all of my old bookmarks buried in the script inside the .json file.  I can go through that and copy out what I need into the address bar then bookmark the old fashioned way.

Once finished with that I will tackle the emails and address book in Evolution.  I'll report any progress.

I'll be back.

---

### Post by Nesaskewatch on 2011-10-16
I copied all the bookmarks from the .json file from the old .mozilla.  It took a while to read an active java script but it worked.  As far as evolution goes I installed a fresh version on the new user from software center.  I then tried replacing the whole evolution file in new .conf with the old one and nothing.  Evolution opens but does not have the email I had stored there nor the address book.  The original is still intact over in the old user file.  I just renamed the new file to "evolution-new" as suggested, them copied over the old file.  No luck I'm afraid.  Any other ideas?  I tried to use the import feature in evolution but it doesn't seem to recognize anything I point to in the old .conf.  Is there another location for the sorts of files it will recognize?  Is .conf truly where stored emails and address book data would be residing?  I just had a thought; is this down to permissions?  I am attempting to access files that were behind an elaborate password prior to my creating the new user and password during the upgrade.  I have been surprised at how much I can look at in the old user file without entering the old password.  Could that have anything to do with why I am failing here?  Just a thought...

Thanks for the continuing help.

---

### Post by gsmanners on 2011-10-16
I'm guessing you have the same userid (1000) as before, and that's why you have no trouble accessing your old files. It's just in another folder is the only real difference (other than the contents, of course).

I highly doubt anything in Evolution will import without having first exported it in some manner (which is basically the same deal with Firefox, but I happen to notice that Firefox usually does a good job of updating your .mozilla folder... well, YMMV).

---

### Post by Lisiano on 2011-10-16
I don't have my desktop near me so I can't check this idea but, AFAIK Evolution is always on, maybe try killing it with ```
killall -9 evolution
``` Copy the old configuration folder and restarting it? I might be wrong about the executable name btw.

---

### Post by Nesaskewatch on 2011-10-16
Re the userid thing from gsmanners.  That makes sense.  Unbuntu simply views all contents of the entire disk and all partitions(?) as accessible to the sys admin.  I probably should start using a guest account.  LOL  And I did get my bookmarks back, but with some fun as the file I was copying from was clearly in use.  It kept turning blue and was slow as molasses.  I collected the links I really needed and had no hope of ever finding again, then closed it before I wrecked something.  We have liftoff on the Firefox front.

As to Evolution and the shutting down thereof.  Much appreciated Lisiano.  I got the following terse response from terminal when I ran the kill command; ```
evolution: no process found
```
I guess that means it is not running.  I did a reboot just to be certain things "took" before opening Evolution again.  No joy in Evolution land...  While retrieving the links in Firefox was a joy, that pales in comparison to my desire to retrieve some of the saved emails I had.  I remain hopeful that they are still there, and just need to be coaxed out of their hiding place.  

I remain grateful for the help

---

### Post by Lisiano on 2011-10-16
A quick
```
locate evolution
```
Showed me 3 folders of rough interest (Netbook, clean install, old /home)
/home/$USER/.config/evolution
/home/$USER/.local/share/evolution
/home/$USER/.gconf/apps/evolution
Remembering gconf is useless since it's mainly configs, .config failed in your attempt so I try to ls ~/.local/share/evolution
```
lisiano@Lisiano-eM350:~/.local/share/evolution/mail/local$ ls
Drafts                  Inbox.ibex.index        Sent.cmeta
Drafts.cmeta            Inbox.ibex.index.data   Sent.ibex.index
Drafts.ibex.index       Outbox                  Sent.ibex.index.data
Drafts.ibex.index.data  Outbox.cmeta            Templates
folders.db              Outbox.ibex.index       Templates.cmeta
Inbox                   Outbox.ibex.index.data  Templates.ibex.index
Inbox.cmeta             Sent                    Templates.ibex.index.data
```
And echo goes the terminal.

---

### Post by JKyleOKC on 2011-10-16
That ertainly looks like the right place! Glad you stepped back in, since I'm using an older version of Xubuntu and also a different mail program.

---

### Post by Lisiano on 2011-10-16
One of the reasons I hate using my android phone to reply on Ubuntu forums (I'm quite fast on the soft keyboard though) is that I can't use locate, man, apt-get and can't copy paste output.
Ontopic: I tried to nano folder.db, found a SQLite DB which had a line about Welcome to Evolution or something, so jackpot I say.

EDIT: Can't resist cating Inbox
```
From evolution@novell.com Wed Sep 06 07:45:12 2006
Return-Path: <evolution@novell.com>
Received: from pop.novell.com (IDENT:mail@localhost [127.0.0.1]) by pop.novell.com (8.9.3/8.9.3) with ESMTP id HAA20680; Wed, 14 Mar 2007 07:45:12 -0400
Received: from smtp.novell.com (smtp.novell.com [141.154.95.10]) by pop.novell.com (8.9.3/8.9.3) with ESMTP id HAA20659 for <evolution@novell.com>; Wed, 14 Mar 2007 07:45:10 -0400
Received: (qmail 5610 invoked from network); 14 Mar 2007 12:00:00 -0000
Received: from smtp.novell.com (HELO localhost) (141.154.95.10) by pop.novell.com with SMTP; 14 Mar 2007 12:00:00 -0000
From: "The Evolution Team" <evolution@novell.com>
To: Evolution Users <evolution@novell.com>
Content-Type: multipart/related; type="multipart/alternative"; boundary="=-t4dRE6cqcdSBHOrMdTQ1"
X-Mailer: Evolution 2.24.0
Date: 14 March 2007 12:00:00 +0000
Message-ID: <1001418302.27070.20.camel@spectrolite>
Mime-Version: 1.0
Subject: Welcome to Evolution!
Sender: evolution@novell.com
Errors-To: evolution@novell.com
X-Mailman-Version: 1.1
Status:   
X-Evolution-Source: pop://rupert@pop.novell.com/inbox
X-Evolution: 00000002-0000


--=-t4dRE6cqcdSBHOrMdTQ1
Content-Type: multipart/alternative; boundary="=-2gZ1roA/HoYrlRDVGyiM"


--=-2gZ1roA/HoYrlRDVGyiM
Content-Type: text/plain
Content-Transfer-Encoding: 7bit


The Evolution Team is proud to welcome you to Evolution, a complete system
for managing your communications and personal information.

```Snipped ofc to the juicy bit.

---

### Post by JKyleOKC on 2011-10-16
> **Nesaskewatch said:**
> Unbuntu simply views all contents of the entire disk and all partitions(?) as accessible to the sys admin.  I probably should start using a guest account.  
Actually, you already **are** running a limited (guest) account with any Linux system. That's why you have to use the "sudo" prefix when you want to make any changes to a system file, or in a very few cases to even read a specific file (such as the /etc/shadow file, that holds user password information). The first user created at install time automatically becomes a member of the group that's authorized to use "sudo" and it's not available to any user added later, unless that first user, with the aid of "sudo," adds him to that group manually.

The general approach is that everything is made available to anyone able to log into the system, but only the Super User is allowed to change system files or directories. Similarly, only the owner of a home directory is allowed to write into it or change its content. The reason that you're able to see so much of the old user's data is that your new user has the same UID, 1000, and that's how the file system keeps track of who's who. Thus you own both of those home directories now, rather than the normal single one -- but only because you created a different user (but with the same UID) when you installed 11.10. Other users might not be able to see nearly as much of the data!

---

### Post by Lisiano on 2011-10-16
There is also a reason for owning by UIDs instead of usernames. You can use the same /home on any number of distributions and if they all share the same UID, the home becomes usable regardless of the username. This can also lead to some unexpected and sometimes funny situations like if you try to view the home directory of the first user (UID 1000) it would be the postgres user on BackTrack. While if you look at the folder from the Ubuntu LiveCD/USB you will see that it is owned by a unknown user with UID 1000. Also this lets you change your username on the same install without having to modify every file you own. Regardless, root (Be it local or root from a LiveCD) can see all files and modify anything. If you are paranoid or wish to secure your home, you should encrypt it, then ONLY you can access it using your password. Well, anyone that knows your password that is. Also changing your password (For example root uses passwd on your user) will keep the files encrypted under the old password.

---

### Post by Nesaskewatch on 2011-10-16
I am liking what I am seeing here.  I am away from my laptop right now, but Lisiano appears to have nailer her!  I will race home and check that code out.  

Gimme an hour.
Cheers!!!!

---

### Post by dFlyer on 2011-10-16
Copy what ever information you need from the old user to the new user account using:

sudo cp -R /home/oldusername/folder /home/newusername/testfolder

Than:

cd /home/newusername/testfolder

sudo chown newusername:newusername -R /folder

this will assign you as the new owner of the folder and you can than move it into your new home folder.

---

### Post by alphacrucis2 on 2011-10-16
If it were me I would have just booted a live CD. Then delete /home/<newuser> from the HD. Then rename /home/<olduser> on the HD. Reboot from HD. If the newuser had a different UID just change owenership of /home/<olduser> incl all subdirs and files first.

---

### Post by Nesaskewatch on 2011-10-16
Some interesting new ideas have surfaced.  Many thanks to dFlyer and alphacrucis2 for some valuable tips.  I'll tackle the job tomorrow.  Long day here and I'm knackered.  I have found the files thanks to Liriano and should have no trouble importing them now that they have been exposed to the light.  I imported one just to be sure and it went smooth as could be.

I can't thank you guys enough.  As I said earlier, I have an old laptop that is in need of a purpose in life, and a backup is as worthy a life as any for an old, beat up MSI.  I will not get so complacent again when it comes to such things.  I had not had a single issue with upgrading for quite a while so I stopped going through the hassel of backing up things.  Never again.

Cheers folks!  This is what makes Ubuntu so great.

---

### Post by Lisiano on 2011-10-17
"Liriano" at your service *Bows*.
Glad you found your E-mails, btw I deleted the / on my netbook then installed 11.10, giving it my username. No need to dig in files and everything is remembered.

---

### Post by Nesaskewatch on 2011-10-17
LOL  Lisiano!  I actually knew someone named Liriano.  The human mind has an enormous capacity for error.  Like the shrinks say; it's all down to memories.  

BTW.  I have all the emails nicely ensconced in their new home(s).  I am going to fool around with the ideas from dFlyer and alphacrucis2.  Good things to know.

Cheers!

---

### Post by JKyleOKC on 2011-10-17
Glad to hear of a successful recovery!

---

