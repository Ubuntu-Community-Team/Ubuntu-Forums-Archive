---
title: "DVDs don't play..."
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Innocent Abroad on 2012-05-02
DVDs don't play, even though the media player is installed.  Am playing discs that I get from commercial sources. 

I have read threads on here, but get no result when trying to follow them. ** I need plain, straightforward English, and step-by-step help.  Please don't assume I know what stuff means and how to do things**. eg what is kubuntu??!

Have 11.10 on my pc.  Use dongle, so pages can be slow to use.  Cannot get cable connection at the moment.  

**Thanks.** ](*,)  :p

---

### Post by Ghost_Mazal on 2012-05-02
My first thought is that you short libdvdcss and libdvdnav.

See if you can install those two packages.

If you have the data and connectivity I highly recommend this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It prevents many a multimedia problem

---

### Post by Baldrick_NZ on 2012-05-02
Also, make sure you have "Ubuntu Restricted Extras" installed from the software centre.

---

### Post by PriceChild on 2012-05-02
Have you used the wiki before?

Check out [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by 3rdalbum on 2012-05-02
Press Control-Alt-T to open a terminal. Copy and paste the following into it:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

(it seems like a lot, but it's one step in the terminal rather than 10 steps in the GUI).

You will be asked for your password - just type it in and bear in mind that it won't show any indication that you've typed anything. Press Enter and wait until the whole process has finished. Then copy and paste this in:

```
sudo apt-get install vlc libdvdcss2
```

So what does all this do? It tells the Ubuntu system where to find another software repository called Medibuntu. It also enables some extra security for this repository and gets the list of packages from it.

The second command installs VLC from the normal Ubuntu repository, and the DVD decryption support from Medibuntu. You should use VLC for DVD playback as the default Totem media player doesn't work so well for DVDs.

---

### Post by Frogs Hair on 2012-05-02
Follow 3rdalbum's instructions , you will need that package to play many DVDS.

---

### Post by Innocent Abroad on 2012-05-07
> **3rdalbum said:**
> Press Control-Alt-T to open a terminal. Copy and paste the following into it:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

(it seems like a lot, but it's one step in the terminal rather than 10 steps in the GUI).

You will be asked for your password - just type it in and bear in mind that it won't show any indication that you've typed anything. Press Enter and wait until the whole process has finished. Then copy and paste this in:

```
sudo apt-get install vlc libdvdcss2
```

So what does all this do? It tells the Ubuntu system where to find another software repository called Medibuntu. It also enables some extra security for this repository and gets the list of packages from it.

The second command installs VLC from the normal Ubuntu repository, and the DVD decryption support from Medibuntu. You should use VLC for DVD playback as the default Totem media player doesn't work so well for DVDs.
Thanks for your reply.  Please, what password?  My ubuntu forum one?  My pc one?  I tried using my pc password, got lots of lines of stuff appear in the Forum, but nothing actually happened. Thanks.

---

### Post by Innocent Abroad on 2012-05-07
> **PriceChild said:**
> Have you used the wiki before?

Check out [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
Yes, have looked on the forums, but as I said, I don't understand anything I found, and I need simple and clear help.  Thanks for your reply.

---

### Post by Innocent Abroad on 2012-05-07
> **Ghost_Mazal said:**
> My first thought is that you short libdvdcss and libdvdnav.

See if you can install those two packages.

If you have the data and connectivity I highly recommend this:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

It prevents many a multimedia problem
Thanks for your reply.  However, I don't understand what you meant when you wrote: 'My first thought is that you short libdvdcss and libdvdnav', please can you explain it to me?  Please use very plain language, as if you are explaining it to your gran - Iam old enough to be a gran actually... :))

---

### Post by Innocent Abroad on 2012-05-07
> **Baldrick_NZ said:**
> Also, make sure you have "Ubuntu Restricted Extras" installed from the software centre.
Thanks for your reply.  It is installed.  DVDs don't play  I get a message that says that the dvd won't play, perhaps because it is encrypted. What do you suggest?  Thank you.

---

### Post by Innocent Abroad on 2012-05-07
> **3rdalbum said:**
> Press Control-Alt-T to open a terminal. Copy and paste the following into it:

```
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

(it seems like a lot, but it's one step in the terminal rather than 10 steps in the GUI).

You will be asked for your password - just type it in and bear in mind that it won't show any indication that you've typed anything. Press Enter and wait until the whole process has finished. Then copy and paste this in:

```
sudo apt-get install vlc libdvdcss2
```

So what does all this do? It tells the Ubuntu system where to find another software repository called Medibuntu. It also enables some extra security for this repository and gets the list of packages from it.

The second command installs VLC from the normal Ubuntu repository, and the DVD decryption support from Medibuntu. You should use VLC for DVD playback as the default Totem media player doesn't work so well for DVDs.
Thanks for your reply.  Please, what password?  My ubuntu forum one?  My  pc one?  I tried using my pc password, got lots of lines of stuff  appear in the Forum, but nothing actually happened. Thanks.

---

### Post by Innocent Abroad on 2012-05-11
Help! I looked at this and it's all Greek to me eg what does 'repo' mean?  

Please advise.

---

### Post by anewguy on 2012-05-11
Repo, in Ubuntu terms, is a shrunk-down version of repository.  A repository in ubuntu's case is where you get software from - think of it kind of like your local library except you get software, not books from it.

Anywhere you see "sudo" or "gksudo" in these forums it is being used to grant you temporary super user rights to your system.  The super user basically has the rights to do anything on the system - like access system files that you really shouldn't mess around with.

These 2 command prefixes will ask for a password - it is your normal log in password.

There is also 1 step not mentioned directly here (unless that has changed for 12.04 - but I doubt it due to legalities with different countries).  The wiki should tell you that step, or search the web for:

ubuntu read dvd

and it should come up with it.  I'm not mentioning it as I don't know if we are allowed to or not on the forum since it deals with something that may not be legal in your country.

Dave

---

