---
title: "Path choice for extracting tarballed programs."
date: 2012-09-23
forum: New to Ubuntu
---

### Post by riX2000 on 2012-09-23
(See bottom for tl;dr-version).

I just installed Ubuntu as my home system (used Windows before but have limited Linux experience from running live CD's and installs in virtual machines). After a couple of weeks my home folder is getting cluttered, since I've "installed" some programs from tarballs, which I have put in ~/appname .

What is the recommended path for putting precompiled or non-installable programs downloaded in tarballs? By non-installable I mean python programs that have all their files they need in the extracted directory or similar.
An example would be WikidPad ([http://wikidpad.sourceforge.net/](http://wikidpad.sourceforge.net/)).

(Please don't answer that I should use the Software center or look for ppt's, deb-files or similar, this question is about programs where those options are not applicable.)

This were the path choices I started out with:

/opt
/bin
/sbin
/usr/local
/usr/bin
/usr/sbin
$HOME
$HOME/bin
$HOME/sbin
$HOME/opt
$HOME/.local

After googling and reading the Filesystem Hierarchy Standard ([http://www.pathname.com/fhs/](http://www.pathname.com/fhs/)), I've come to this conclusion:

/opt - (large) programs not made for non-Ubuntu systems, like windows (via wine) and other Linux distributions. 
/bin - should not be used for this purpose
/sbin - should not be used for this purpose
/usr/bin - should not be used for this purpose
 - single-file compiled programs or soft-links to (executable) files in other directories
/usr/sbin - single-file scripts or soft-links to (executable) script files in other directories
/usr/local - ? (should probably only contain the default directory structure)
/usr/local/bin - single-file compiled programs or soft-links to (executable) files in other directories
/usr/local/sbin - single-file compiled programs or soft-links to (executable) files in other directories (system-related)
$HOME - basically I don't want anything except directories here
$HOME/bin - I read some post of a user that thought this was a better alternative to other */bin paths.
$HOME/sbin - see $HOME/bin
$HOME/opt - see $HOME/bin
$HOME/.local - what about this?
$HOME/.local/bin - what about this?
$HOME/.local/sbin - what about this?


I've noticed some people uses ~/Downloads, personally I use that as a tmp folder for web related files.

I found an outdated deb-file for an older version of WikidPad ([http://pkgs.org/ubuntu-11.10/getdeb-apps-i386/wikidpad_2.1-1~getdeb1_all.deb.html](http://pkgs.org/ubuntu-11.10/getdeb-apps-i386/wikidpad_2.1-1~getdeb1_all.deb.html)), which puts it in /usr/bin and /usr/share/*, but I feel that doing this manually would clutter the system unnecessarily, the deb-file, I assume, would create uninstall instructions somewhere.

So, is there a right/better/only way to do it?
How do you do it, pros and cons?

A pro for me would be a folder inside $HOME, since I tend to make small modifications in progarms, and it would be nice to be able to easily back that up without having to include random system folders in the backup set.

Right now I'm thinking that $HOME/.local/appname with symbolic link to the executable in $HOME/.local/bin might be a good choice.

Of course, the best would be to learn how to create deb files and do that, which I probably will, but I need to get this right first :)


tl;dr-version:
Where should I extract tar-archives that doesn't need to be compiled? $HOME/appname clutters my system :/
Is $HOME/.local/appname with a symbolic link to the executable in $HOME/.local/bin a good choice?

---

### Post by diesch on 2012-09-23
In your $HOME you are free to do whatever you like.

*$HOME/.local/appname* may be used by the program itself so I wouldn't use that.


I'm using* ~/software/programs/appname* and manage symlinks into *~/software/bin*, *~/software/lib*, ... using [GNU Stow](http://manpages.ubuntu.com/manpages/precise/en/man8/stow.8.html)

---

### Post by mansonfan78 on 2012-09-23
> **diesch said:**
> In your $HOME you are free to do whatever you like.

*$HOME/.local/appname* may be used by the program itself so I wouldn't use that.


I'm using* ~/software/programs/appname* and manage symlinks into *~/software/bin*, *~/software/lib*, ... using [GNU Stow](http://manpages.ubuntu.com/manpages/precise/en/man8/stow.8.html)

That's good advice for permanent installs, however I think it would be a good idea to create a new folder and extract any new tarballs into that folder first so you can make sure there's nothing malicious in there (rare, but it does happen).  Once you're sure it's safe you can move the files to a more permanent location.

---

### Post by vasa1 on 2012-09-24
> **riX2000 said:**
> ...
tl;dr-version:
Where should I **extract** tar-archives that doesn't need to be compiled? $HOME/appname clutters my system :/
Is $HOME/.local/appname with a symbolic link to the executable in $HOME/.local/bin a good choice?

Both your title and the tl;dr version refer to **extract** as opposed to **install**.
I have very limited experience in this matter but I **extract** to an appropriately named temporary folder in my home and delete once I'm done. Where I **install** it is the big question.
I have three examples. Firefox, Seamonkey, and LibreOffice. I prefer these programs direct and not from a ppa. 

For Firefox, extract to a temp folder and then copy the relevant folders to a "permanent" folder, MyFox  ~/MyFox.
For Seamonkey, first part as above but then into /usr/local/seamonkey.
For LibreOffice, the extraction results in .debs which look after themselves.

Of course, there's the whole mystery of whether what has been installed will be elevated to the status of **registered application** by Ubuntu.

---

### Post by riX2000 on 2012-09-24
> **diesch said:**
> In your $HOME you are free to do whatever you like.

*$HOME/.local/appname* may be used by the program itself so I wouldn't use that.


I'm using* ~/software/programs/appname* and manage symlinks into *~/software/bin*, *~/software/lib*, ... using [GNU Stow]("http://manpages.ubuntu.com/manpages/precise/en/man8/stow.8.html")

Right, that might be one of the best solutions, I just wanted to make sure none of the existing directories I listed above was actually intended for this. I'll check out GNU Stow, thanks.

> **mansonfan78 said:**
> That's good advice for permanent installs,  however I think it would be a good idea to create a new folder and  extract any new tarballs into that folder first so you can make sure  there's nothing malicious in there (rare, but it does happen).  Once  you're sure it's safe you can move the files to a more permanent  location.

Of course, unless I feel I can trust the source enough to run the  program directly, I usually look through the source or test in a safe  place.

> **vasa1 said:**
> Both your title and the tl;dr version refer to **extract** as opposed to **install**.
I have very limited experience in this matter but I **extract** to an appropriately named temporary folder in my home and delete once I'm done. Where I **install** it is the big question.
I have three examples. Firefox, Seamonkey, and LibreOffice. I prefer these programs direct and not from a ppa. 

For Firefox, extract to a temp folder and then copy the relevant folders to a "permanent" folder, MyFox  ~/MyFox.
For Seamonkey, first part as above but then into /usr/local/seamonkey.
For LibreOffice, the extraction results in .debs which look after themselves.

Of course, there's the whole mystery of whether what has been installed will be elevated to the status of **registered application** by Ubuntu.

Right, it's *extract *or *permanently-move-the-folder* or whatever I'm interested in i.e. your ~/MyFox example, I interpret *install* as configure+make+make install or running an install script or a .deb.

---

