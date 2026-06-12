---
title: "Does Spotify work wth Ubuntu?"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by vtmet on 2012-07-03
I use a music program Spotify on Windows, but I prefer to use my dual-boot computer in Ubuntu mode because audio/video isn't as choppy...

I know a lot of programs designed for Windows don't work with Linux...but according to Spotify, it will work with Ubuntu...I just don't understand their instructions of what I need to do:

>  Spotify for Linux
This is a preview build of Spotify for Linux. As a preview release this version is still unsupported, but we're running it ourselves and will try to make sure it keeps pace with its Mac and Windows siblings.

So how do you get it? We've packaged it for Debian Squeeze/Ubuntu.

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

[http://www.spotify.com/us/download/previews/](http://www.spotify.com/us/download/previews/)

---

### Post by Dlambert on 2012-07-03
The Commands above are for Debian and won't work exactly as-is in Ubuntu. Here you go :)

Open up terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
``` Then: 

```
sudo sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list'
``` Finally:

```
sudo apt-get update && sudo apt-get install spotify-client-qt
```


Source: [http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/)

---

### Post by cipherboy_loc on 2012-07-03
Follow Dlambert's advice.

---

### Post by vtmet on 2012-07-03
> **Dlambert said:**
> The Commands above are for Debian and won't work exactly as-is in Ubuntu. Here you go :)

Open up terminal:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 4E9CFF4E
``` Then: 

```
sudo sh -c 'echo "deb http://repository.spotify.com stable non-free" >> /etc/apt/sources.list'
``` Finally:

```
sudo apt-get update && sudo apt-get install spotify-client-qt
```


Source: [http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/the-quickest-way-to-install-spotify-client-in-ubuntu-12-04-precise-pangolin/)


I just tried the instructions from that link...and it appears like it's going to work and then at the end of the code that it shows on terminal, something seems to not work...It asks a final question with a y or n response, if I hit y it just sits there; if I hit y followed by enter it says "abort":

> Reading package lists... Done
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-21-generic linux-headers-3.0.0-21
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libnspr4-0d libqt4-webkit libqtwebkit4 spotify-client
The following NEW packages will be installed:
  libnspr4-0d libqt4-webkit libqtwebkit4 spotify-client spotify-client-qt
0 upgraded, 5 newly installed, 0 to remove and 21 not upgraded.
Need to get 33.9 MB of archives.
After this operation, 89.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y 
Abort.
   

---

### Post by Dlambert on 2012-07-03
Try capitol Y.

---

### Post by vtmet on 2012-07-03
> **cipherboy_loc said:**
> Assuming you are using ubuntu and not kubuntu (kde):

Open a terminal, and copy and paste the following:
Code:
gksudo gedit /etc/apt/sources.list
Enter to the bottom and scroll to the bottom of the file, and copy and paste the following into the file:
Quote:
# Spotify source
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
Save and exit. Return to the terminal, and copy and paste the following:
Code:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59 && sudo apt-get update && sudo apt-get install spotify-client

Cipherboy

I copied this before you deleted it, just trying to see if it was any different since my first attempt didn't work...

---

### Post by vtmet on 2012-07-03
> **Dlambert said:**
> Try capitol Y.

I didn't notice that it was asking for a capital Y there...and then apparently the next step is a lower case y...

it got further afterwards, but the way that the terminal ended I don't think that it finished setting up spotify:

> Unpacking libqtwebkit4 (from .../libqtwebkit4_2.2~2011week36-0ubuntu1_i386.deb) ...
Selecting previously deselected package libqt4-webkit.
Unpacking libqt4-webkit (from .../libqt4-webkit_4%3a4.7.4-0ubuntu8.1_i386.deb) ...
Selecting previously deselected package spotify-client.
Unpacking spotify-client (from .../spotify-client_1%3a0.8.4.103.g9cb177b.260-1_i386.deb) ...
Selecting previously deselected package spotify-client-qt.
Unpacking spotify-client-qt (from .../spotify-client-qt_1%3a0.8.4.103.g9cb177b.260-1_all.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libnspr4-0d (4.8.7-0ubuntu3) ...
Setting up libqtwebkit4 (2.2~2011week36-0ubuntu1) ...
Setting up libqt4-webkit (4:4.7.4-0ubuntu8.1) ...
Setting up spotify-client (1:0.8.4.103.g9cb177b.260-1) ...
Setting up spotify-client-qt (1:0.8.4.103.g9cb177b.260-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
 

and then my computer name showed up:
username@ubuntu:~ $

---

### Post by Dlambert on 2012-07-03
You're done! it's installed! Open it up. Look in unity.

---

### Post by vtmet on 2012-07-03
> **Dlambert said:**
> You're done! it's installed! Open it up. Look in unity.

I'm gonna sound like a "newbie" on this question...but how do find "unity"?

---

### Post by Dlambert on 2012-07-03
Ubuntu 12.04 correct? Open up wherever you find your applications it will be in there.

---

### Post by vtmet on 2012-07-03
> **Dlambert said:**
> Ubuntu 12.04 correct? Open up wherever you find your applications it will be in there.

actually 11.10 (I recently upgraded that from 10.04)...and I'm still not used to the different look from the older version...

---

### Post by Dlambert on 2012-07-03
Click on the Ubuntu logo and search spotify (just type it). But I would recommend installing 12.04.

---

### Post by vtmet on 2012-07-03
thanks for all of your help...

I just found it and got logged into spotify...

I'll look into upgrading to 12.04 soon...

---

### Post by Dlambert on 2012-07-03
Please Mark this thread as solved. On top of the page, Thread Tools > Mark as Solved.

---

### Post by blueshead on 2012-07-03
Make sure you use this.. It is the new key change..

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 94558F59
```

Spotify runs ok in Ubuntu except for tieing in to your own music library..

---

