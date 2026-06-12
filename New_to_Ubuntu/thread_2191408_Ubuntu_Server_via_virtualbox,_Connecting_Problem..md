---
title: "Ubuntu Server via virtualbox, Connecting Problem."
date: 2013-12-02
forum: New to Ubuntu
---

### Post by olivier.janssens19 on 2013-12-02
I am currently using **ubuntu server in virtualbox** experimenting before I start on my server.
The problem is that I use the  **command "sudo apt-get install openjdk-6-jre"** but in the end nothing happens. 
The last thing it said was: **"0% [Er wordt verbinding gemaakt met be.archive.ubuntu.com (91.189.92.156)]"** 
Furthermore  nothing happened,  with some other **"apt-get install"** I have this too. What's the problem?
excuse me, I'm Dutch, and I use ubuntu in dutch.

---

### Post by newb85 on 2013-12-02
Welcome!  You don't need to apologize for using Ubuntu in your own language.  That's the reason those language options are there!

It claims a connection has been made to the repository mirror, and at the very least, we can be sure you are connecting to the web, since the hostname was resolved to an IP address.  It could be that more time is required to download the packages.  (You didn't say how long you waited.)  It's possible there's something wrong with that mirror, which could be resolved by switching to another nearby mirror.  There is a list of other mirrors available at [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors).  As you're running server edition, you'll need to run a command-line text editor, such as vi.  Vi has a fairly easy-to-use search-and-replace feature.

First, open your source list with
```
sudo vi /etc/apt/sources.list
```

Once the file is open, you can run a search and replace (I'm using the Nucleus mirror from Belgium as an example)
```
:%s#be.archive.ubuntu.com#ubuntu-archive.mirror.nucleus.be
```
and hit Enter.  Once all entries have been replaced, save and close the file with
```
:wq
```
and hit Enter again.

---

### Post by jdeca57 on 2013-12-03
Since you want to use a server, I suppose you chose bridged networking in Virtualbox. 
Secondly, again for a server, I suppose you configured an IP manually (fixed IP) so that you know the address of your server. (instead of the dhcp way). Dhcp is standard and should work, but if you entered your own values, specially for dns, the problem might be there. But you give preciously little information about the way you installed the network. 
Anyhow, if what I suppose is right, [http://ubuntuserverhelp.com/setting-up-a-static-ip/](http://ubuntuserverhelp.com/setting-up-a-static-ip/) may be of help.

---

