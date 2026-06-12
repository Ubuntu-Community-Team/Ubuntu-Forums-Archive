---
title: "Mozilla firefox install"
date: 2023-04-05
forum: New to Ubuntu
---

### Post by jim Kane on 2023-04-05
following the Mozilla link to install this, there are two folders not installed in Xubuntu /opt which I have done, but not sure of the code needed to install usr/ local/share/applications
Thanks for your help

---

### Post by Holger_Gehrke on 2023-04-06
'/usr/local/' is a subtree of '/usr/' which mimics the structure of '/usr/'. It is meant for programs installed system-wide but not through the package manager. '/usr/local/share/applications/' is the place where *.desktop files for these programs go. *.desktop files are text-files that contain the information for starting applications in a graphical environment. The structure of these files is described at [https://specifications.freedesktop.org/desktop-entry-spec/latest/](https://specifications.freedesktop.org/desktop-entry-spec/latest/) .

I'm a bit surprised that you say '/usr/local/share/applications/' doesn't exist on your system; I'm running Xubuntu 22.04 and it does exist on my system and I don't recall creating it myself. You could just create the directory with ```
'sudo mkdir -p /usr/local/share/applications'
``` That should create the directory with 755 permissions (rwx for user root, r-x for group root, r-x for everyone else).

But unless you have a very specific need for Firefox installed in this way, I'm not quite sure if you should do it that way. Following the instructions from Mozilla, you end up with a system-wide installation of Firefox in the directory /opt/firefox owned by your normal user account. This means other users can use Firefox, but if your user account runs Firefox you can update it (that's good) and malware running in your browser can potentially change the browser installation and spread itself from your user to other users on your machine (that's bad). That might not be a problem if you're the only user on your machine, but if you do have multiple users it is. There are two ways out of this: either chown and chmod /opt/firefox to be owned by root and only readable (and executable for the files which need it) for everyone else or make a user specific installation in some subdirectory of $HOME for each and every user. The first solution breaks updating, the second solution can be a colossal waste of space (a separate 240 MB Firefox installation for each and every user, and this only stops the in-system spread of Malware between users, not the manipulation of one installation by malware running inside it). Both installation through snap - which is default on newer versions of Ubuntu - and from the PPA (which is more fiddly to set up but avoids the problems posed by snap constraints) have neither of these problems.

Holger

---

### Post by jim Kane on 2023-04-06
Thanks for your comprehensive reply
 I have sorted it now (no other users but me) im getting old with some memory problems which makes using terminal a bit risky unless I have a clear description to follow,  I am using an older PC which firefox Snaps crashes so wanted to try Mozilla Firefox which works fine now 
as a PS what does the -P command do cant find any reference to it ?

---

### Post by monkeybrain20122 on 2023-04-06
actually, if you are the only user of the machine there is no reason to install it to /opt and make links to /usr/local (which requires sudo) all you need is to uncompress the tar file somewhere in your $HOME, put the .desktop file in ~/.local/share/applications (change the Exec=line to Exec=path/to/firefox-bin %u) That's it.

---

### Post by Holger_Gehrke on 2023-04-07
If you mean the '-p' in the mkdir command I gave, that's not a command it's an option to mkdir and you'll find it in the manual page for mkdir (man mkdir). This option makes mkdir create all the directories along the given path which don't already exist. So if you only had /usr/ but no local/ inside that, the mkdir command would create /usr/local, /usr/local/share/ and /usr/local/share/applications/.

Holger

---

