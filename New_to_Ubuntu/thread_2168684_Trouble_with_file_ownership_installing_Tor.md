---
title: "Trouble with file ownership installing Tor"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by JkR4Yne on 2013-08-18
Hello,

In the past I have installed Tor with the following commands:

sudo add-apt-repository ppa:upubuntu-com/tor64 
sudo apt-get update 
sudo apt-get install tor-browser 
sudo chown $USER -R ~/.tor-browser/

I have seen other ways to install it, but this is the only method that has worked for me; iif I didn't use the last command, Tor would install but not work,

The problem I have now there is a Tor upgrade.  Using the same commands, I get error after using sudo chown $USER -R ~/.tor-browser/ .
The error is chown: cannot access ‘/home/name/.tor-browser/’: No such file or directory.
I'm guessing that the Tor files were extracted in a different location than before.  There is a Tor folder in user/bin now, but I'm not sure what to do next.
Any help would be appreciated.

---

### Post by slickymaster on 2013-08-19
Why don't you install it from the repositories:```
sudo apt-get install tor vidalia
```

---

### Post by JkR4Yne on 2013-08-19
> **slickymaster said:**
> Why don't you install it from the repositories:```
sudo apt-get install tor vidalia
```
Thanks for your help, - I thought the command sudo add-apt-repository ppa:upubuntu-com/tor64 added it from the repositories?

I did try sudo apt-get install tor vidalia and got the following errors from Tor:

Warning] /usr/bin/tor-browser/Data/Tor is not owned by this user (usr name, 1000) but by root (0). Perhaps you are running Tor as the wrong user?
and [Warning] Failed to parse/validate config: Couldn't access/create private data directory "/usr/bin/tor-browser/Data/Tor" ,so it looks like ownership is still an issue.

---

### Post by slickymaster on 2013-08-19
That's strange.

After some searching I did found out this, [here]("https://trac.torproject.org/projects/tor/ticket/6259"):
> With Vidalia 0.2.19 and Tor 0.2.3.18-rc, it may be possible to fix this issue by adding a line like the following to the ~/.vidalia/vidalia.conf file in the [Tor] section:
```
DataDirectory=~/.vidalia/data
```

---

### Post by Vladlenin5000 on 2013-08-20
The previous information is quite outdated. Vidalia no longer creates a ~/.vidalia/ folder... Lots of things seem to have changed in this last upadte also :(

---

