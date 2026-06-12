---
title: "Export Firefox/Thunderbird Windows Profile to Ubuntu"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-08
Hi - I want to export my email account settings and emails from Windows Thunderbird to Ubuntu. I would also want to export my bookmarks and saved passwords from firefox to Ubuntu as well.

I know Windows has MozBackup, but I can't find a Linux version of it.

Any ideas how I would go about this?

---

### Post by ichbinesderelch on 2008-05-08
you could just copy your profile folder form firefox/thunderbird to the linux mozilla thunderbird directory, that would do the bookmark trick and mail trick, i'm unsure about passwords though

---

### Post by freesitebuilder on 2008-05-08
This has info on converting from Windows:
[https://help.ubuntu.com/8.04/switching/index.html](https://help.ubuntu.com/8.04/switching/index.html)
including email.

---

### Post by hyper_ch on 2008-05-08
you can just copy the user profiles for ff and tb over to linux.

---

### Post by confused_user on 2009-11-17
does anyone know how to go the other way?

i've got windows 7 on dual boot (for work reasons / i am not happy at having to defile my netbook with that pos) and would like to export my firefox config (as much as possible,extensions, bookmarks, everything else) over to my windows install.

any ideas?

---

### Post by oldfred on 2009-11-17
I was getting my wife to convert several years ago, so I have a share partition with the profile directories and I just edited the profile.ini with the correct path. They were different between windows and linux but easy to set up. It has worked thru upgrades and different versions for short periods on windows and Ubuntu.


[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)


Linux profile.ini for thunderbird,  firefox is similiar

Edit:
I also modified the profile.ini on our windows portable and when we travel I just copy the entire profile directories over to the portable and then back when we get home. Never had an issue once I got the profile.ini set up correctly.

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

---

### Post by confused_user on 2009-11-20
Thanks OLdfred, i tried this, I get the vanilla / default ubuntu firefox bookmarks and what not when i do this and my users profile?

THis is great since it seems like it is possible but i cant figure out whats going wrong?

ANy ideas?

edit; It's ok i got it working, i was pointing it at the wrong profile.

For anyone else looking to share their linux firefox profile (bookmarks, extensions, saved passwords - everything) here is what i did.

1: I use ext2 volume manager to mount my ext3 /home partition in windows 7
[http://www.ext2fsd.com](http://www.ext2fsd.com)

2: backup your C:\Users\matt\AppData\Roaming\Mozilla\Firefox\profiles (my username is matt)

3; your profile file looks like this

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=Profiles/j0zg5dyb.default

4: All you need to do is change the Path to point at your ubuntu firfox profile.

Mine is located in F:\matt\.mozilla\firefox\6rkdyos0.default since i used ext2fsd to mount my /home partition on F:/

5: MY new profile file looks like this 

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=F:\matt\.mozilla\firefox\6rkdyos0.default
Default=1

6: Bask in the glory of having the same bookmarks, saved passwords and, extensions (addblock filter!!) and everything else on both your windows and your ubuntu OS.

Thanks for the info OLdfred :)

---

### Post by oldfred on 2009-11-20
When you open firefox or thunderbird they create new profile directories and a profile.ini that points to the file. 

The links I provided above should get you to further explanations.

The profiles in Linux are in your home folder as hidden files. You can use your nautius file browser, turn on show hidden files in view and these two directories are where the profiles are:

I have both 3 & 3.5
/home/fred/.mozilla/firefox-3.5
/home/fred/.mozilla/firefox

/home/fred/.mozilla-thunderbird

You edit profile.ini, the isrelative is if the profile is not in the current directory.

---

