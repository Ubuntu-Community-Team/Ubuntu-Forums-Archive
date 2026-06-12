---
title: "Spotify for Linux PPA help"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2012-07-20
Spotify has instructions that are imcomplete for installing the app. They show:

Debian
# 1. Add this line to your list of repositories by
#    editing your /etc/apt/sources.list
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

# 2. If you want to verify the downloaded packages,
#    you will need to add our public key
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59

# 3. Run apt-get update
sudo apt-get update

# 4. Install spotify!
sudo apt-get install spotify-client

but I know there is a command line way to add the repo line, I just don't know it. Also, doesn't the GPG key need to be installed first?

---

### Post by FatFrog on 2012-07-20
couldn't you 
sudo add-apt-repository ppa:... ?

---

### Post by oldos2er on 2012-07-20
```
sudo add-apt-repository http://repository.spotify.com
``` should work. The gpg key can be added at any time.

---

### Post by Mark_in_Hollywood on 2012-07-20
I guess they don't know how to work with Linux/Debian.

mark@Lexington-19:~$ sudo add-apt-repository [http://repository.spotify.com](http://repository.spotify.com)
[sudo] password for mark:
mark@Lexington-19:

mark@Lexington-19:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.zbbuvh8P9z --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 94558F59
gpg: requesting key 94558F59 from hkp server keyserver.ubuntu.com
gpg: key 94558F59: public key "Spotify Public Repository Signing Key <operations@spotify.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


mark@Lexington-19:~$ sudo aptitude update

W: Failed to fetch [http://repository.spotify.com/dists/precise/main/source/Sources](http://repository.spotify.com/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://repository.spotify.com/dists/precise/main/binary-i386/Packages](http://repository.spotify.com/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by oldos2er on 2012-07-20
Did you run the command I gave you? [s]The spotify repo isn't a PPA.[/s]

---

### Post by Mark_in_Hollywood on 2012-07-20
I cut & pasted the 'argument' into the terminal. It ran. I next ran the gpg line, as shown in my above post. It returned no errors or warnings. I then ran sudo aptitude update. Then I got the W and E problem.

---

### Post by oldos2er on 2012-07-20
I was wrong, they do have a PPA. This finally worked for me: ```
echo "deb http://repository.spotify.com stable non-free" | sudo tee -a /etc/apt/sources.list

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59

sudo apt-get update && sudo apt-get install spotify-client
``` Sorry for the confusion.

---

### Post by Mark_in_Hollywood on 2012-07-20
It did make a difference.

mark@Lexington-19:~$ echo "deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free" | sudo tee -a /etc/apt/sources.list
[sudo] password for mark: 
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free

mark@Lexington-19:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.FNqPtEHaQ4 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 082CCEDF94558F59
gpg: requesting key 94558F59 from hkp server keyserver.ubuntu.com
gpg: key 94558F59: "Spotify Public Repository Signing Key <operations@spotify.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

looks good so far.

mark@Lexington-19:~$ sudo aptitude update

...
W: Failed to fetch [http://repository.spotify.com/dists/precise/main/source/Sources](http://repository.spotify.com/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://repository.spotify.com/dists/precise/main/binary-i386/Packages](http://repository.spotify.com/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

UH-OH! but I went ahead and:

mark@Lexington-19:~$ sudo aptitude install spotify-client
The following NEW packages will be installed:
  libavcodec53{a} libqt4-webkit{a} spotify-client 
0 packages upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
Need to get 33.9 MB of archives. After unpacking 79.6 MB will be used.
The following packages have unmet dependencies:
 libavcodec-extra-53 : Conflicts: libavcodec53 but 4:0.8.3-0ubuntu0.12.04.1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:  
1)     libavcodec53 [Not Installed]                         

     Leave the following dependencies unresolved:           
2)     spotify-client recommends libavcodec53 | libavcodec52


Accept this solution? [Y/n/q/?] Y

The following NEW packages will be installed:
  libqt4-webkit{a} spotify-client 
The following packages are RECOMMENDED but will NOT be installed:
  libavcodec53 
0 packages upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 28.1 MB of archives. After unpacking 65.0 MB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe libqt4-webkit i386 4:4.8.1-0ubuntu4.1 [7,740 B]
Get: 2 [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free spotify-client i386 1:0.8.4.103.g9cb177b.260-1 [28.1 MB]
Fetched 28.1 MB in 46s (605 kB/s)                                                                                                                            
Selecting previously unselected package libqt4-webkit.
(Reading database ... 364455 files and directories currently installed.)
Unpacking libqt4-webkit (from .../libqt4-webkit_4%3a4.8.1-0ubuntu4.1_i386.deb) ...
Selecting previously unselected package spotify-client.
Unpacking spotify-client (from .../spotify-client_1%3a0.8.4.103.g9cb177b.260-1_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up libqt4-webkit (4:4.8.1-0ubuntu4.1) ...
Setting up spotify-client (1:0.8.4.103.g9cb177b.260-1) ...
                                         
mark@Lexington-19:~$

Spotify now appears under Multimedia in the panel drop down menu.

Thanks OldDos-er.

---

### Post by oldos2er on 2012-07-20
Glad you figured it out.

---

### Post by cpxondo on 2012-07-29
Thanks! It worked for me

---

### Post by Mark_in_Hollywood on 2012-08-09
As of 1 August 2012, the Update Manager reports an E: and a W: that the spotify repos are not working any longer. Is this a packaging problem or is something more serious afoot?

---

