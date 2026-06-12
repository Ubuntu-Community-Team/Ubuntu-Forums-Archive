---
title: "Need help with key-based SSH auth"
date: 2016-07-25
forum: New to Ubuntu
---

### Post by steve234 on 2016-07-25
Hi there,

I have just got a new phone and am trying to set up an app called FolderSync to access my Ubuntu laptop via SSH. I use this to transfer media to my phone nightly.

The setup is:
Server - Ubuntu 14.04 Laptop.
Client - Android Phone via "FolderSync" app.

I'm currently just using password based auth, and I don't want to do  this for long. I have previously used key-based authentification but now it is not working.

I had key-based auth working nicely on my old Android phone with the same app, so I copied my (backed up) id_rsa file to the new phone, but it just says "auth failed" or "Could not authenticate SSH client: FAILED".

I generated new keys on my laptop (server) but the new id_rsa didn't work either.

I've now got to a point where I've genrally made a mess of my .ssh folder and files on my laptop (server) by following various tutorials. 

Is anyone able to give me some hand-holding with getting some keys generated and putting them in the correct places with the correct permissions? I will need to use the *server* machine to do this as my Android phone (the client) is not rooted and doesn't have busybox.

---

### Post by ubudog on 2016-07-26
I'd start from scratch, and do it like this:

On your server/laptop:
```

cd /home/user
mv .ssh .sshbak
mkdir .ssh
cd .ssh
ssh-keygen -t rsa -b 4096
cp id_rsa.pub authorized_keys

```

Then copy your id_rsa (private key) to your phone, and make sure it is in the right place for the app to find.  Also be sure that your ssh server is running on the laptop.

---

### Post by steve234 on 2016-07-26
Thanks that's jogged my memory! Everything worked on my laptop and the file copied over ok, however the app still gives me the message "Could not authenticate SSH client: FAILED". 

I see there is a space for a "Known hosts file, perhaps that's the missing piece (screenshot of app below):

[IMG][[IMG]http://i1375.photobucket.com/albums/ag450/thephatmaster1/Screenshot_20160726-204034_zpsriaiasr7.png[/IMG]]("http://s1375.photobucket.com/user/thephatmaster1/media/Screenshot_20160726-204034_zpsriaiasr7.png.html")[/IMG]

---

### Post by ubudog on 2016-07-27
Strange... you might get a more detailed error message if you tried to ssh using an app such as ConnectBot.

---

### Post by CantankRus on 2016-07-27
Might be obvious but app shows you haven't put in a login name.
I tested the app on my android phone and works fine with a key-file and my login name.

---

### Post by steve234 on 2016-07-28
CantankRus you win the prize - somehow I thought that ssh keys were device specific... I guess everything (especially on Unix based systems) is user specific. 

Solved - syncs like a champ and I've been able to turn off passwords in /sshd_config for extra security.

---

