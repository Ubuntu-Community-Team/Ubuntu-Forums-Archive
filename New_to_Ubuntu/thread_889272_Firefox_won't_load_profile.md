---
title: "Firefox won't load profile"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by egalvan on 2008-08-13
Ubuntu 8.04.1

Firefox v3.01, refuses to start with my regular profile.

this is the error:

[B]Firefox cannot use the profile "distributed" because it is in use.
To continue, close the running instance of Firefox or choose a different profile.[/B]


This has been working fine for more than a month, until a power failure.
This problem started immediately after.
Rebooting with full shutdown has not cleared the problem.

**lock** and **.parentlock** are both gone.

Any help/ideas/links?

Thanks

ErnestG

---

### Post by cosine352 on 2008-08-13
got to 
> system --> administration --> system monitor

there click the "process" tab and find firefox and chose it by clicking and end the process by hitting the "End Process" button at the lower right corner

---

### Post by egalvan on 2008-08-13
No firefox shows in the 'process' tab.

ErnestG

---

### Post by cosine352 on 2008-08-14
did you tried to find the PID by command
> ps -A
OR
> top

If you can find firefox there just kill using the PID

> kill PID

---

### Post by Mister.Vash on 2008-08-14
and from the terminal does
```
 ps ax | grep -i fire
```
show anything?

---

### Post by alienexplorers on 2008-08-14
Try starting Firefox in the terminal.  Use the command:
> firefox -profilemanager
Select the profile you want to use and then select to run from profilemanager.  Wait for firefox to startup and then shut it down.
Wait about 10 seconds and then load firefox as you normally would.  It should then start in the correct profile.

---

### Post by egalvan on 2008-08-14
```
[B]ps-A

top[/B]
```

both showed no firefox.



```
**ps ax | grep -i fire**
```

gave the following:

**6820 pts/0    R+     0:00 grep -i fire**


```
**firefox -profilemanager**
```

gave same error result as starting from desktop.

ErnestG

---

### Post by Mister.Vash on 2008-08-14
Under your ~/.mozilla/firefox folder you should have a folder that a string of characters ending in .default for example, something like sdfi723.default
under that folder, do you have a file called lock ?

---

### Post by Dill on 2008-08-14
So you said lock and .parentlock are both gone? Are you looking in ~/.mozilla/firefox/*.default ?

```
cd ~/.mozilla/firefox/*.default
rm lock .parentlock
```

Cheers, 
Dylan

---

### Post by egalvan on 2008-08-14
As I stated in my original post

[B]lock and .parentlock are both gone.
[/B]


ErnestG

---

### Post by Dill on 2008-08-14
Yes, and I was just making sure you were looking in the correct place. If you look right in your home directory, for instance, you aren't going to find files called **lock** and **.parentlock**. I'm not trying to insult your intelligence, just trying to help you out, mate.

You could try some more of the things listed here:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

Or, you could try creating a new profile and copying your existing profile data over:

[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)
[http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

The latter is a bit of a workaround, but it should work.

Cheers, 
Dylan

---

### Post by alienexplorers on 2008-08-14
Why don't you just create a new profile and copy over the relevant info from the old profile to the new profile.

Read this article on what to move:
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox]("http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox")

---

### Post by egalvan on 2008-08-14
> **Dill said:**
> I'm not trying to insult your intelligence, just trying to help you out, mate.

Wasn't saying or implying anything, other than trying to state what steps I have already taken.
BTW. RTM and "Google is your Friend" are also steps I took before posting here. It's where I found out about the locks.

> 
You could try some more of the things listed here:

[http://kb.mozillazine.org/Profile_in_use](http://kb.mozillazine.org/Profile_in_use)

Already tried

> 
Or, you could try creating a new profile and copying your existing profile data over:

[http://kb.mozillazine.org/Profile_Manager](http://kb.mozillazine.org/Profile_Manager)
[http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

The latter is a bit of a workaround, but it should work.

Cheers, 
Dylan

Want to try to solve this problem, before i take the easy way out of making a new profile. I'm learning a lot.

And I'm starting to lean in the direction of bad permissions.
See my next post.

ErnestG

[/I]

---

### Post by egalvan on 2008-08-14
More testing...

Seems to be a permissions problem...

Firefox under XP runs this fine; as is, where is.

Firefox under Ubuntu runs fine if the profile is moved to another drive.

Firefox under Ubuntu shows error if ANY profile/data is moved/copied to the original drive.

Any more ideas?

I'm still working on the solution ](*,)

---

### Post by egalvan on 2008-08-16
Bump ](*,)

---

### Post by egalvan on 2008-08-17
Bump ](*,)

---

### Post by Mister.Vash on 2008-08-17
You say that the firefox loads the profile correctly from a different drive when it has been copied to a different drive?  Is that correct?

What is the location of the profile that is not working?  Is it under your home folder or someplace else?  Is that mounted on a different drive?

Can you post the permissions for the folder that contains the profile and for the parent folders?

---

### Post by egalvan on 2008-08-19
OK, a re-hash of problemn and some up-dated info...

Main (internal) drive
Dual-booting:
WinXP-Pro
Ubuntu 8.04.1.

running Firefox 3.01 on both Win & Ubuntu

External USB drive
profile is on shared file space on this drive


I was running Firefox when the lights went out.
 When the power came back on, I re-booted,
 and Firefox stated that my profile is in use.

I have done the following:

1) Moved profile to main drive -- 'fixes' problem, but I need the mobility of the external drive.

2) Created new profile on USB drive -- does not work

3) Created new profile on DIFFERENT USB drive -- 'fixes' problem, but I want to use the original (large) USB drive.

4) Moved original profile to DIFFERENT USB drive -- again, this works, but I want to use the original (large) USB drive.

Another observation.... NO OTHER PIECE OF SOFTWARE SEEMS TO BE AFFECTED.. Everything seems to work OK, EXCEPT FIRERFOX

My next experiment will be to back-up my original USB drive somewhere, then re-format and try again.

I'll post permissions before I wipe the drive... maybe something is obvious to someone else....
but if it's permissions, then why is Firefox the only program affected (so it seems)?

Many thanks for the insights/ideas/opinions.

I know I seem to be taking the difficult road of finding and fixing the problem,
 rather than simply re-doing the drive,
 but I really want the learning experience..](*,)

---

### Post by AjBaz100 on 2008-08-19
Try creating a new profile then..?

---

### Post by egalvan on 2008-08-19
> **AjBaz100 said:**
> Try creating a new profile then..?

See point #2 above 


:popcorn:

---

### Post by egalvan on 2008-08-22
Bump ](*,)

---

### Post by psyced on 2008-08-27
Same problem here, my computer randomly crashed when I was browsing the web. I have a profile on windows that I use on Ubuntu as well ( [http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/) ).

It seems whenever I run firefox with the windows profile it changes the permissions on the fat32 drive (my windows partition) to read only (I can write files before I try to open firefox but not after).
And when it opens it gives me an error message: "Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

Same error as egalvan when I try to open it a second time.

Aannd now there will be no helpful replies. Thanks!

---

### Post by psyced on 2008-08-27
After I try to open firefox on my XP profile I get the following error when I try to create a file: Error opening file '/media/disk/new file': Read-only file system.

---

### Post by egalvan on 2008-08-27
> **psyced said:**
> Same problem here, my computer randomly crashed when I was browsing the web. I have a profile on windows that I use on Ubuntu as well ( [http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/](http://cybernetnews.com/2007/10/24/cybernotes-share-a-firefox-profile-between-ubuntu-and-windows/) ).

It seems whenever I run firefox with the windows profile it changes the permissions on the fat32 drive (my windows partition) to read only (I can write files before I try to open firefox but not after).
And when it opens it gives me an error message: "Could not initialize the application's security component. The most likely cause is problems with files in your application's profile directory. Please check that this directory has no read/write restrictions and your hard disk is not full or close to full. It is recommended that you exit the application and fix the problem. If you continue to use this session, you might see incorrect application behaviour when accessing security features."

Same error as egalvan when I try to open it a second time.

Aannd now there will be no helpful replies. Thanks!

OK let me explain the differences twixt your problems and my problem.

My computers are quite stable, Firefox under *nix never crashes,
 and under Winders, I've only had one crash in the last year.
 Really.

Next, the "crash" I talk about in my opening post, refers to a POWER OUTAGE...
 just long enough to reboot my machines....:(
 about five three seconds long.

I was running Ubuntu 8.04.1, browsing with Firefox (v3.01),
 referencing a profile on an external USB drive formatted Win-NTFS.

When the power came back on, my problems started,,,,
 but ONLY WITH FIREFOX UNDER *NIX and ONLY ON THAT USB DIRVE.
 NO other software was affected. Firefox under WinXP was NOT AFFECTED.
 And copying that profile to any other drive also "FIXED" the problem.

I have emptied the problematic USB drive, erased it, and re-formatted to NTFS under Windows.
 I am now in the process of returning all software to the USB drive, and will try it out.
 I will post back here with the news, good or bad.


As to your problem, I am thinking that your FAT32 permissions problems may be caused by file system inconsistencies.
 Try running "chkdsk /f" on that drive.
 Also, are you using Sleep or Hibernate modes?
 Remember that you absolutely have to un-sleep or un-hibernate under the same system you used to sleep or hibernate.
 Bad things happen to good drives when you don't follow this rule.

Do you have more than one partition on that FAT32 drive?
 If so, remember that Windows will sometimes (albeit rarely) write past the end of a partition.
 Personally, I put a Linux SWAP partition between Windows stuff and *nix stuff...
That swap area isn't used at all when running WinXP. so it acts as a buffer.

Remember, I am using an EXTERNAL USB HARD DRIVE to hold my Firefox Profiles (among many other things).
 This may, or may not, have any bearing on the problem.

And finally, why are you using FAT on that drive? Compatibility issues?

FAT16/32 file systems are not very stable, to say the least.

ErnestG

:popcorn:

---

