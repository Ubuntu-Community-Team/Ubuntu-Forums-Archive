---
title: "Upgrading to 12.04 LTS Failed - no user account"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by tweaked on 2012-05-04
I too am having nearly the same problem. I don't know why I did it, I have never, in 7 years using Ubuntu , ever, ever gotten an upgrade to work, I am an idiot for thinking otherwise and I really don't know why Ubuntu even offers this.

My screen froze at the Time Zone/copying files screen. I waited an hour or more and shut it down. It boots to 12.04 but since there were no user accounts setup, I cannot access any files. 

How can I create an user account without the root password it keeps requesting? At a minimum, before I am forced to clean install, I would like to see the files again.

An alternative would be to revert back to 10.04. How would I do this?

---

### Post by mörgæs on 2012-05-04
There is no way to roll back to an older installation other than a fresh install.

---

### Post by oldfred on 2012-05-04
Your issue is different and the possible solutions are different than the thread you were in, so I created a new one for your.

Have you tried recovery mode?

You may have to chroot into your system from a liveCD or USB and finish the update from that or create a new user account. Is any user in /home?

To chroot into your system:
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot - these just update system but not add a admin user:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by tweaked on 2012-05-04
Thanks for that, I did see my home folder. although I did not have access to the files to copy. 

The problem now is when booting, I get a command line for grub.

---

### Post by tweaked on 2012-05-04
I got through Grub and it boots fine. 

Now back to the original question, how do I set up a superuser account as a Guest, preferably the same one?

---

### Post by oldfred on 2012-05-04
I have never added a user other than at install.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

---

### Post by tweaked on 2012-05-04
> **oldfred said:**
> I have never added a user other than at install.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

It appears I will need to go into Recovery and fiddle with /root.

---

