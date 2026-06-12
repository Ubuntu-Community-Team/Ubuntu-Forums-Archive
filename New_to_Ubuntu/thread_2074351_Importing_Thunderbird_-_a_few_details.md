---
title: "Importing Thunderbird - a few details"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by Bartender on 2012-10-21
Hey, good morning!

Here's the scenario.  You're setting up a new PC to replace an older one.  You've installed Ubuntu (or Mint in this case) to the new PC.  Now you want to bring your Thunderbird email client over to the new PC with all the folders, older emails, passwords, etc. so that it comes up on the new rig just like the old one.  

Google "importing Thunderbird to a new PC" and you'll get gobs of hits.  Most of them involve "from Windows" or "from Evolution".  Even the ones that don't are confusing.  At least to me.

So, I'm going to march thru the steps to import a Thunderbird profile to a new PC.  The old PC is running Ubuntu 10.04.  The new PC is running Mint 13.

OLD PC: Close Thunderbird.  The following won't work unless you close it.  It'll look like the profile folder is gonna copy, but then you'll get error messages about "lock".

Open Home Folder.  Go to "View".  Click on "Show Hidden Folders".  Find the folder circled in the screenshot below.  

Plug in a thumbdrive.  It should open in a second file browser window.  **Go to "View" and click on "Show Hidden Folders" again**, or the folder you're copying over will not appear even though you saw it copy! Copy/paste the ".thunderbird" folder shown in the screenshot below to the thumbdrive.

"Eject" or "Safely Remove" the thumbdrive when you see the folder's been moved.

NEW PC: I had not touched the Thunderbird app on the new Mint 13 PC.  Never opened it at all.

I plugged the thumb drive in, went to "View", clicked on "Show Hidden Folders", and found the profile folder.  

Opened the Home Folder, same thing as above, you have to click "View", then click "Show the hidden folders".  I copied the ".thunderbird" profile folder to the Home Folder.  You don't have to worry about putting it in some special spot, just drop it in the Home Folder.

Started Thunderbird for the first time on the new PC.  It didn't ask to create an email profile or anything.  It just opened on the new PC exactly like it did on the old PC.

So, it's really quite simple to import your existing Thunderbird account to a new PC.  5 minute job.  But I didn't close Thunderbird before trying to copy the profile folder, and I forgot to tell the File Browser to show hidden folders when looking at the thumb drive.

---

### Post by daslinkard on 2012-10-22
Definitely enjoyed reading this tutorial...made clear sense as I went through it!  This should definitely be under the tutorial section as many new users & existing users can find this helpful!

Good Job!

---

### Post by drmrgd on 2012-10-22
This is pretty good advice, and is ~almost~ the way it worked for me last time I migrated.  Just to add to it in case someone has a problem:

For some reason, Thunderbird did not pick up the new profile right away, and instead created a new one.  No biggie, though.  If that happens, all you need to do is to patch the profile.ini file to point to the correct profile.  For example on my system, .thunderbird looks like:

```
$ ls
8i2g8fmo.default  Crash Reports  profiles.ini
```

And my profiles.ini looks like:

```
[General]
StartWithLastProfile=1

[Profile0]
Name=Default User
IsRelative=1
Path=8i2g8fmo.default
Default=1
```

Make the "path" variable the same as the profile folder name, and you're good to go.  

I showed the results from the terminal, since I had one open and it was quicker than taking a picture.  Of course, this can just as easily be done from your favorite file manager as well.

---

### Post by Bartender on 2012-10-23
daslinkard, I re-read it, then tried to elucidate a few parts that seemed incomplete.

drmrgd, thanks very much for the additional info.  I wouldn't have had any idea how to find the path & fix it like you did.

---

### Post by mikodo on 2012-10-23
Nice guide, Bartender. Here, have one on me. :wink:

I suppose this will work for .mozilla, with all firefox bookmarks, extensions, etc, too?

Thanks.

---

### Post by mikodo on 2012-10-24
> **mikodo said:**
> Nice guide, Bartender. Here, have one on me. :wink:

I suppose this will work for .mozilla, with all firefox bookmarks, extensions, etc, too?

Thanks.

I guess, as seen here:

[http://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles?esab=a&s=Firefox+backup&r=1&as=s](http://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles?esab=a&s=Firefox+backup&r=1&as=s)

Thanks.

---

### Post by Anuovis on 2012-10-24
> **mikodo said:**
> 
I suppose this will work for .mozilla, with all firefox bookmarks, extensions, etc, too?


Yes, I have been backing up my Firefox like this for a while.

This method also works with Skype and another piece of software I use called Anki. I suspect lots of other applications store their settings and whatnot in hidden folders within Home folder as well.

---

### Post by larrys4227 on 2012-10-24
I've run into the 'path' issue before, and the post above can fix it.  What I do, tho, is before copying all the folder data to the new location, I open Thunderbird and configure it with dummy info (just to get past the initial setup).

This sets the default folder, close T-Bird, copy my files into it, and reopen T-bird.  Works every time.

---

### Post by mikodo on 2012-10-24
> **larrys4227 said:**
> I've run into the 'path' issue before, and the post above can fix it.  What I do, tho, is before copying all the folder data to the new location, I open Thunderbird and configure it with dummy info (just to get past the initial setup).

This sets the default folder, close T-Bird, copy my files into it, and reopen T-bird.  Works every time.
Thanks. So, "dummy info", is just entering in a non-existent email configuration, and then closing Thunderbird?

Why the questions, is that I am putting in a new drive, and doing a clean install of Xubuntu, for the first time (I always just brought my ~/ partition forward, in earlier Ubuntu installs. Time to start fresh, with a clean Xubuntu install.

Thanks.

---

### Post by Bartender on 2012-10-24
> **larrys4227 said:**
> I've run into the 'path' issue before, and the post above can fix it.  What I do, tho, is before copying all the folder data to the new location, I open Thunderbird and configure it with dummy info (just to get past the initial setup).

This sets the default folder, close T-Bird, copy my files into it, and reopen T-bird.  Works every time.

Hey, larrys4227, if you happen to see this -

Do you copy the old profile into the default folder somehow?  Or just drop the old profile into the Home Folder?  Don't you have to go into T'Bird or F'Fox then and tell it to ignore the original "dummy" profile?  I'm confused...

mikodo, if I may make a suggestion, if it were me I'd try importing the old profile before even opening T'Bird, like I did.  If it doesn't work, then try the version with more steps...

Seems to me there should be better documentation for the handful of things that people need to do when moving on to a new PC, or wiping the old one to the bricks then installing fresh.  I've gotta take better notes!

---

### Post by mikodo on 2012-10-24
> **Bartender said:**
> 

mikodo, if I may make a suggestion, if it were me I'd try importing the old profile before even opening T'Bird, like I did.  If it doesn't work, then try the version with more steps... Thanks, will do!

---

### Post by ruud00000 on 2012-10-24
Since I cannot find a button in the forum to start a new thread... 

I just installed Ubuntu 12.04.1 32-bit instead of 12.04.1 64-bit. Made a copy of the thunderbird and Frefox profile before doing so. Now when I open Thunderbird a new defalut profile is created (named m6rzzjis.default instead of the old name el0vempw.default). So I copy the contents of the old default folder into the new one and overwrite anything already there. This works fine for Firefox but doesn't work for Thunderbird: the old mails / settings are not found. Even when I copy the entire folder using the old name and change the reference to it in the profile.ini the old mail and settings don't show.

What's wrong? How to solve?

Thanks.

---

### Post by Bartender on 2012-10-25
Hi, there, ruud0000 -

Take a look at the screenshot below.  Is that button not present in your browser?  It's located at the top of each sub-forum.  

Although hijacking a thread is generally considered bad form, asking about your problem is fine with me.  If someone answers with a solution, then that just makes the thread more useful.

I'm not sure how to solve your problem.  Hopefully someone will respond.  It might help to post a screenshot of your hidden folders.  It sounds like you have at least two Thunderbird profiles now?  I wonder what would happen if you cut/pasted the one you don't want out of your Home Folder and onto some storage device, then restarted the PC and opened Thunderbird?  I don't have a good understanding of how all these folders interact with the program.

And I have no idea whether Thunderbird cares one bit if you're going back and forth between a 32-bit & 64-bit PC, or if that causes trouble??  

The more people who add to this, the more thankful I am that it "just worked" in my case!!

---

### Post by Bartender on 2012-10-25
OK, maybe this will help someone, maybe not.  

On the old PC (see first post) I went to Home Folder>View>Show Hidden Folders.  Opened the ".thunderbird" profile folder, as shown in the screenshot in first post.  

Fortunately, I only have one profile folder.  Maybe that's all that anyone has?

Inside that profile folder, I only have one default user.  I think Thunderbird must have some sort of random name generator for the users?

See how I have one default folder, n5xoy8m0.default.

I then opened the profile.ini folder.  Take a look at the path.  I believe this is what drmrgd was referring to in post #3.  My guess is that Thunderbird looks to the profiles.ini folder first, then looks for the profile folder described in "Path".

ruud0000, maybe you can check this out and see if the Path lines up to the profile folder you want?  I'm not sure if you can just change the Path entry without sudo?  I don't want to try it!

---

### Post by ruud00000 on 2012-10-25
I gave up on it and manually entered settings all over in Thunderbird, taking for granted that I  don have a copy of the mail history now. After doing so, just trying to find out about this issue, I uninstalled Thunderbird again and reinstalled it, after making a copy of the profile folder as just created. 
Then started Thunderbird, stopped it, changing the path entry in the profiles.ini file, just like before, and now it DID work: the settings and test mails entered today would appear now. So somehow the issue seems related to the 32-bit versus 64-bit thing, whether a Ubuntu or Thunderbird issue... 
Doing this with sudo would probably solve the issue but I wouldn't know how to do that. For now I will take my loss.

---

### Post by drmrgd on 2012-10-25
> **ruud00000 said:**
> I gave up on it and manually entered settings all over in Thunderbird, taking for granted that I  don have a copy of the mail history now. After doing so, just trying to find out about this issue, I uninstalled Thunderbird again and reinstalled it, after making a copy of the profile folder as just created. 
Then started Thunderbird, stopped it, changing the path entry in the profiles.ini file, just like before, and now it DID work: the settings and test mails entered today would appear now. So somehow the issue seems related to the 32-bit versus 64-bit thing, whether a Ubuntu or Thunderbird issue... 
Doing this with sudo would probably solve the issue but I wouldn't know how to do that. For now I will take my loss.

That's interesting that it didn't work the first time.  I can't imagine why there would be a difference between 32-bit and 64-bit in that regard.  Perhaps there is a subtle difference that we're unaware of, or perhaps it was as simple as a typo somewhere along the lines or some kind of extra white space somewhere messing stuff up.  Not sure, but it does sound like you got it worked out, which is great!

Also, I wanted to point out that since these files and folders are all owned by you, you not only don't need to use sudo to do this, but also probably don't want to, as a potential side effect is the root will become owner of the files and directories, and you'll not be able to access them as a regular user.  Sudo just grants root level permissions for a specific task, and only needs to be used for system maintenance / tasks, and working with root owned files and directories.

---

### Post by mikodo on 2012-10-25
> **ruud00000 said:**
> So somehow the issue seems related to the 32-bit versus 64-bit thing, whether a Ubuntu or Thunderbird issue... Well, I am going to be going from a Ubuntu 32-bit install to a Xubuntu 64-bit install, so maybe I might run into the same problem. But, if I follow the advice of ** drmrgd** and change the profiles.ini to the original (if, I need to), maybe I will be alright. If not, luckily for me, my emails remain on my IP server.

Thanks, for this thread Bartender, and advice from everyone.

---

### Post by larrys4227 on 2012-10-25
Sorry for getting back so late on this ....

I am copying all the t-bird files INTO the new default folder, from the SAVED default folder ....

The profile.ini already points to whatever the new default folder is, so there is no change.  I'm just overwriting the dummy info already INSIDE of the new default.

By command line, it would be something like this (but I just drag and drop)

cp /media/usb/.thunderbird/xyz123.default/*  /home/larry/.thunderbird/abc123.default/

---

### Post by larrys4227 on 2012-10-25
I'll elaborate one more step ....

Here is my current profile.ini .... lets say I JUST MADE a dummy account.  The default folder is now set (shown below).  Just copy all the files from insidede the OLD default folder ... to inside the NEW default.

Fire up T-Bird and everything will be there without having to fuss with profile.ini


[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=vo4whsuy.default<-----copy/pasta info INTO this folder that was created during the dummy account phase

---

### Post by will1982 on 2012-10-25
This is great.
Thanks :3

---

### Post by Bartender on 2012-10-25
> **larrys4227 said:**
> copy/**pasta** info INTO this folder that was created during the dummy account phase

Hey, thanks to everyone for their input!  larrys4227, can you elaborate on that 'pasta' command?  I'm scared to try it unless I know what it does.

I think I'll open up a nice Merlot first....    

:):):):)

---

### Post by larrys4227 on 2012-10-25
Its an attempt at humor .... :KS

---

### Post by mikodo on 2012-10-25
To recap. Seems there are two ways to approach the transfer of the backup Thunderbird files to a new installed Thunderbird profile.

1. In the new install of Thunderbird, **before opening it**, make sure the path of the T-bird profiles.ini is/or are made to be the same as the old path of the T-bird profiles.ini that is in backup. Then copy the backup files to it and open the new install of Thunderbird.

2. In the new install of Thunderbird **open it**, configure it with dummy info, close it and copy the backup files to it, then re-open up Thunderbird.

Am I getting this right?

---

### Post by Bartender on 2012-10-26
OK, this is gonna get hairy.  Hopefully I can write it down before I forget what happened.

This experiment involves the Old PC described in post #1, plus a third rig.  The Old PC has been our daily-use PC for the last coupla years.  I'm getting ready to swap it out for a newer rig.  Wanted to make a bumpless transfer to the newer PC and this whole T'Bird experiment was part of that effort.  

The third rig (the average vintage of all 3 PC's is 2005, so it's not exactly an impressive bunch) is used for a few specific tasks but we don't rely on it as our daily runner.  So I picked it for today's weird science project.  If I blew up Thunderbird I could just uninstall.  

I'll refer to the Old PC described in post #1 as PC-1 (the daily-use PC with the T'Bird profile I wanted to keep).  

The 3rd rig, described above, will be PC-3.  

PC-3 was updated from 10.04 to 12.04 Ubuntu a few weeks ago.  But Unity was sluggish.  So I installed Lubuntu and have been happy with it so far.  In Lubuntu I made the mistake of opening T'Bird on PC-3.  It wanted to create a new account, etc.  I closed T'Bird.

I still had PC-1's T'Bird profile on a thumb drive.  As described in Post #1.  For lack of a better plan, I went into PC-3's file browser, clicked View>Show Hidden Folders, and renamed .thunderbird to .thunderbird-old.  Then I copy/pasted the PC-1 .thunderbird folder into PC-3's Home Folder, as seen in Screenie1.png.  

I think what I did next was open Thunderbird.  It came up just like I wanted it to!  But check out Screenie2.png.  I added captions to this screenshot for clarity.  In a nutshell, you're seeing the PC-1 .thunderbird folder from the thumbdrive, then below it the PC-3 .thunderbird folder.  It _looks like_ PC-3 is still trying to access the default user that I tried to hide under the renamed 'thunderbird.old' folder.  So it looks like it won't work.  But it was working!

When I clicked on the 'iltclrq0.default' folder I got some kind of error message.  Invalid file path or something like that.

So I logged out of Lubuntu and into Ubuntu.  Look at Screenie3.  Logged into the Ubuntu desktop, the default user looks like it should.  WTH??  I logged back into Lubuntu.

Now take a look at Screenie5.  Logging out of Lubuntu somehow fixed the apparent (but not real) problem of user folders that you see in Screenie2.

I've spent 2 hours on this!  I hope SOMEONE can make use of the info.  I guess there are a couple of things that I learned - you can safely set aside a .thunderbird profile by renaming it.  It appears that dropping a new profile from a different PC does work.  It has for me so far.  If the Path appears to be wrong at first, log out (or just shut down) and restart T'Bird, then recheck the .thunderbird folder.

---

