---
title: "Basic question: What do we do when an apt-get update fails to find stuff?"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by Jim_Granite on 2013-12-30
Whenever I run "sudo apt-get update", some packages fail; but I'm not sure if that's normal, nor, what I should do about it.
```

$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Ign http://extras.ubuntu.com saucy InRelease                                   
Ign http://ppa.launchpad.net saucy InRelease                                   
Ign http://security.ubuntu.com saucy-security InRelease  
... lots and lots of these presumably successful updates ... but then ... 
Err http://ppa.launchpad.net saucy/main amd64 Packages
  404  Not Found
Hit http://ca.archive.ubuntu.com saucy-updates/restricted Translation-en
Err http://ppa.launchpad.net saucy/main i386 Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/saucy/main/binary-amd64/Packages  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/saucy/main/binary-i386/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
etc.

```

What's the significance of the failures above anyway?

---

### Post by jeffreyjensen1989 on 2013-12-30
Check up on your manually added repo's The wseverin ppa is probably not well maintained and is not up to saucy yet

EDIT: Just went to [http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/](http://ppa.launchpad.net/wseverin/ppa/ubuntu/dists/) in browser and it's not updated to saucy yet. If your existing packages from that repo still exist on your installation I would just continue to use them. Unless they stop working for some reason you'll have to find the source and recompile it. I would just ignore it unless it becomes an eyesore and it's not updated soon, Then I would remove it from my sources.list and move on

---

### Post by deadflowr on 2013-12-30
The best thing to do when the ppa is not functional on your system is to simply disable it.
You can do this by opening up the program "software and updates".
In here go to "other software" and locate the ppa in the listing, then uncheck(you will need to enter your password).

Secondarily, if you really need it you could edit the file located in the /etc/apt/sources.list.d folder.
There would be a file with the ppa name in here.Open it and edit(you'll need to be root)
You would just change the release name(example for this would be to change it from saucy to raring)

Personally, though, I'd disable it and keep my eye out for when it gets a saucy update.

---

