---
title: "Ubuntu - can't update or download apps. - dependency error"
date: 2017-10-02
forum: New to Ubuntu
---

### Post by terence4 on 2017-10-02
Hi,

A few months ago I tried to update all my apps.

The updates begin then just hang. I don't get the screen where I put in my password to add or update an app.

When trying to fix I got this message; 

```
terence@terence-LIFEBOOK-A514:~$ sudo apt-get install -f
[sudo] password for terence: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 mod-pagespeed-stable:i386 : Depends: apache2.2-common:i386 but it is not installable or
                                      apache2-api-20120211:i386
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
terence@terence-LIFEBOOK-A514:~$ 
```

I have no idea how to proceed from here.

Any ideas?

---

### Post by ian-weisser on 2017-10-02
That's a version conflict.
You installed a package (usually from a non-Ubuntu repository) that conflicts with the version in the Ubuntu repositories.
The package manager is stuck until you resolve the conflict by uninstalling the non-Ubuntu package and deleting the non-Ubuntu repository.

What did you install before this happened?

---

### Post by terence4 on 2017-10-03
Thank you for the reply. I'll have to wrack my brains to remember now.
I think I first noticed it when I tried to download the GIMP image editor and it wouldn't work.
If I can find the dates I downloaded previous programs it may be the one before that.
Is there a way to find the dates?

---

### Post by ian-weisser on 2017-10-03
Oh dear. Let's try a different approach.

1) Which release of Ubuntu are you running?
2) Please show us the complete contents of your /etc/apt/sources.list file.
3) Please show us the complete directory listing of your /etc/apt/sources.list.d/ directory.

---

### Post by terence4 on 2017-10-03
Ok this will take me a bit of time but I'll get started in 1/2 hr.

---

### Post by terence4 on 2017-10-03
1) 16.04LTS

I can't remember how to put in the password in terminal. Keyboard doesn't seem to work.

---

### Post by QIII on 2017-10-03
Hello!

That is normal.  Just type your password and press Enter.  Nothing will echo on the screen, but the input is being taken.

---

### Post by terence4 on 2017-10-03
1) 16.04LTS

I can't remember how to put in the password in terminal. Keyboard doesn't seem to work. 
Thanks for that. Now I don't seem to have the command right.

terence@terence-LIFEBOOK-A514:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
terence@terence-LIFEBOOK-A514:~$ list
No command 'list' found, did you mean:
 Command 'gist' from package 'yorick' (universe)
 Command 'hist' from package 'loki' (universe)
 Command 'bist' from package 'bist' (universe)
 Command 'dist' from package 'nmh' (universe)
 Command 'last' from package 'util-linux' (main)
 Command 'lift' from package 'lift' (universe)
 Command 'klist' from package 'heimdal-clients' (universe)
 Command 'klist' from package 'krb5-user' (universe)
 Command 'flist' from package 'nmh' (universe)
list: command not found
terence@terence-LIFEBOOK-A514:~$ sources.list
sources.list: command not found
terence@terence-LIFEBOOK-A514:~$

---

### Post by ian-weisser on 2017-10-03
You display the contents of a file using 'cat', 'less', 'more', 'head', 'tail', or any text editing application.
You display the files in a directory using 'ls -a'
Then copy-and-paste the text. Please avoid bandwidth-wasting screenshots of text. Use [code] tags to preserve the formatting.

---

### Post by terence4 on 2017-10-03
Thanks for the reply, however;

I still have a knowledge gap here I'm afraid. 

Do I run a command in the terminal or open a text editor and search my C drive?

---

### Post by ian-weisser on 2017-10-03
'C drive' is a Windows thing. It refers to your primary Windows partition.
In Linux, everything is in the path from /. You already know the path - no need to search.

If you have a text editor (like Gedit), then yes - open the file in that.

Er, when you download-and-install software (like Gimp), or 'update your apps', how exactly do you do so?
Version conflicts often happen when new users, led astray by their Windows skills, make things unnecessarily complicated.
Both are actually very, very easy when you are doing them right.

---

### Post by Impavidus on 2017-10-04
Run those commands in the terminal. "Display the contents of /etc/apt/sources.list" translates to
```
cat /etc/apt/sources.list
```
"Display the directory listing of /etc/apt/sources.list.d/" translates to
```
ls -a /etc/apt/sources.list.d/
```
Copy and paste to your post. You can copy from the terminal using ctrl+shift+c, right mouse click->copy or simply select and paste with a middle mouse click. Use code tags to make your post easy to read. If you click on "Reply with Quote", you can see how I used code tags in this post.

---

### Post by terence4 on 2017-10-04
> **Impavidus said:**
> Run those commands in the terminal. "Display the contents of /etc/apt/sources.list" translates to
```
cat /etc/apt/sources.list
```
"Display the directory listing of /etc/apt/sources.list.d/" translates to
```
ls -a /etc/apt/sources.list.d/
```
Copy and paste to your post. You can copy from the terminal using ctrl+shift+c, right mouse click->copy or simply select and paste with a middle mouse click. Use code tags to make your post easy to read. If you click on "Reply with Quote", you can see how I used code tags in this post.

Thanks Impavidus.
Does this give any clues?

terence@terence-LIFEBOOK-A514:~$```
 cat /etc/apt/sources.list
```
```
# deb cdrom:[Ubuntu 16.04.1 LTS _Xenial Xerus_ - Release amd64 (20160719)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```
terence@terence-LIFEBOOK-A514:~$ ```
 ls -a /etc/apt/sources.list.d/
```
.  ..  google-earth.list  google-earth.list.save

Hi Ian,

I missed the cat & ls bit, or where to put it.

I do, as you suggest have a Windows hangover which is taking a while to get rid of as I use it at work every day.

I cheat and use the Ubuntu software centre to download programs - but hopefully one day will be able to do it the "easy" way.

Thanks again - I think there is some progress above - Google earth?

---

### Post by ian-weisser on 2017-10-04
The progress above is exactly what the file _should_ look like if you have not added any new sources.
That's both good and bad.

The 'bad' part is that it means you are downloading software off the dirty, dirty internet in the Windows way. Down that path lies a broken system...which is what you have.
In this case, it looks like you downloaded a 32-bit package of mod-pagespeed-stable from ...someplace. That's what seems to be causing the problem.

Are you really running a 32-bit system?
Are you willing to uninstall mod-pagespeed-stable? (since it's not working anyway)

If so, try
```
sudo dpkg --purge mod-pagespeed-stable:i386
```

It's not difficult to learn both Windows and Linux. Many of use here use both daily. The trick is simply to realize that neither is 'right' or 'wrong', both are simply 'different', and to use each  in the way that works best for it.

---

### Post by terence4 on 2017-10-05
Many thanks for your time and help. 

I entered the code you gave me and "Bingo" it all works again. It removed the program very quickly - unlike Windows.
I've downloaded GIMP and all works fine.

I don't even remember downloading mod-pagespeed-stable, or what it is. It would have been from the software centre which I thought was all "clean" stuff.

Just one question - how did you know what I downloaded and what was wrong from the list copied above? Is there a link in there somewhere?

---

### Post by ian-weisser on 2017-10-05
The answer is buried in the original error message:

> **terence4 said:**
> 
When trying to fix I got this message; 
```
The following packages have unmet dependencies.
 **mod-pagespeed-stable:i386** : Depends: apache2.2-common:i386 but it is not installable or
                                      apache2-api-20120211:i386
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```

That package 'mod-pagespeed-stable' does not exist in the Ubuntu repositories. Never has. So you didn't find it in the Software Center.
(If it *were* in the Ubuntu repositories, it would be a version that wouldn't cause a conflict. Preventing version conflicts is one purpose of Linux distro repositories)

A quick search-engine of the name revealed it's probable origin...and the instructions you probably followed. More importantly, it revealed that there was no repository to remove from /etc/apt/sources.list* . That made the fix much, much easier.
The simplest way to resolve a version conflict is to delete the non-Ubuntu source repository, then uninstall the packages provided by that source. If you don't delete the repo, the system will promptly try to re-install the conflicting packages again. In this case, there was no repo to delete.

---

### Post by terence4 on 2017-10-05
Right, that makes sense.

Thanks again - much appreciated.

---

### Post by linuxissuperawesome on 2017-10-09
Try To Not Install Programs From Foriegn Repositories

---

