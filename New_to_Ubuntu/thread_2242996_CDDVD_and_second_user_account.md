---
title: "CD/DVD and second user account"
date: 2014-09-05
forum: New to Ubuntu
---

### Post by rod52 on 2014-09-05
I am having problems with cd/dvd drives that appear to only happen with a second user account. When logged in as primary account.  I can eject cd and dvd etc.  But when logged in under second user. Those options to eject etc. does not appear. I am migrating from XP to Lubuntu.  The primary account is for me so I can maintaine the machine and keep it updated.  The second account is for the actual user.  So when I copy photos, pictures etc. into the second user account,  I can only do this once, then have to re-boot because the cd drive no longer responds to the eject button. I try the botton because, as I stated before, there is no eject or unmount option when logged in under second account. As the super user, I did go into User and Groups (advanced) and checked the following privileges boxes:  Use CD-ROM, Access external storage devices automatically and a few others, but not all.  Just the ones for normal usage, no file share or Mount user-space filesystems.  I did not go into Account Type: Custom and check either Administrator or Desk Top User.  Does any of this sound familiar, does anyone have any thought?  Also, when the cd is removed, the file manager latches on to the files that were on the cd as if the cd was still in the drive.

---

### Post by yancek on 2014-09-05
Check the /etc/group file to see if you have a cdrom group entry.  Check then to see if you second user is listed.  If not open this file as root (using sudo) and add your second user to that line.

---

### Post by rod52 on 2014-09-05
Thanks, there is a line for cdrom:x:"number":"primary name","secondary name".  So that does not appear to be the problem.

---

### Post by rod52 on 2014-09-05
Sorry, don't know why the mad icon appeared.  I must have hit the wrong key.

---

