---
title: "Update Manager Question"
date: 2014-05-10
forum: New to Ubuntu
---

### Post by jessemoose on 2014-05-10
Absolute beginner here.  I love the OS, and after a year am having my first issue.  Update manager is showing updates available, but when I engage the update, I get a message after authenticating, UPDATE REQUIRES INSTALLATION OF UNTRUSTED PACKAGES.

 I have gone through and tried to do each update individually, but I get the same message.  Ideas, and what other information is helpful?

Thanks,

---

### Post by Frogs Hair on 2014-05-10
Hello and Welcome

Refresh the source list with the following terminal command . (same as checking for updates) ```
sudo apt-get update 
```

---

### Post by Paulgirardin on 2014-05-10
I have had success in this situation by using the terminal to perform the update.
Start the terminal with Ctrl-Alt-t
Commands:
```
sudo apt-get update
```
then:
```
sudo apt-get upgrade
```
It will ask for your password.

---

### Post by Vladlenin5000 on 2014-05-10
> **Frogs Hair said:**
> Hello and Welcome

Refresh the source list with the following terminal command . (same as checking for updates) ```
sudo apt-get update 
```

... and if you notice errors at the end of the process please post them here.

---

### Post by matt_symes on 2014-05-10
Hi

> I get a message after authenticating, UPDATE REQUIRES INSTALLATION OF UNTRUSTED PACKAGES.

You generally get this message if you are missing some PPA or other keys.

Kind regards

---

### Post by jessemoose on 2014-05-12
Thank you all for the help.  I ran the updates from the terminal, but got the following errors:
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I'm not sure what it means, but would love some ideas.

---

### Post by monkeybrain20122 on 2014-05-12
You can fix this with a long and cryptic command which you can find rather easily by searching for "ubuntu gpg errors" (I can never remember it :)) But if you have a few of them the easiest way to fix it would be to run launchpad-getkeys. First install it
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install launchpad-getkeys
```

Then just run
```
sudo launchpad-getkeys
```
[http://www.webupd8.org/2010/05/automatically-import-all-missing.html](http://www.webupd8.org/2010/05/automatically-import-all-missing.html)

---

### Post by jessemoose on 2014-05-12
monkeybrain20122 - i followed your notes, now I get:
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by ibjsb4 on 2014-05-12
This will fix multiple bagsig errors.

```
sudo -i
mv /var/lib/apt/lists /var/lib/apt/lists.old
mkdir -p /var/lib/apt/lists/partial
apt-get clean
apt-get update

```

---

### Post by jessemoose on 2014-05-12
OUTSTANDING...Now, what exactly did I do?  I'd Love to understand the commands.  Reasource recomenation?

---

### Post by ibjsb4 on 2014-05-12
mv /var/lib/apt/lists /var/lib/apt/lists.old
Moved the offending file to backup state.

mkdir -p /var/lib/apt/lists/partial
Created a new folder.

apt-get clean
Cleaned the cache.

And welcome to the forums :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by matt_symes on 2014-05-13
Hi

> **monkeybrain20122 said:**
> You can fix this with a long and cryptic command which you can find rather easily by searching for "ubuntu gpg errors" (I can never remember it :))

Neither can i, so i set up a whole load of functions and aliases to help my addled brain :)

```
matthew-S206:/home/matthew:0 % fa gkey  
gkey='sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys'
matthew-S206:/home/matthew:0 %
```

```
matthew-S206:/home/matthew:0 % fa lpkey
lpkey () {
        gpg --keyserver pgpkeys.mit.edu --recv-key "$1" && gpg --export --armor "$1" | sudo apt-key add -
}
matthew-S206:/home/matthew:0 %
```

Kind regards

---

