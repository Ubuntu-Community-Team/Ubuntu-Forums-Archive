---
title: "virtualbox how?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by silverjohnlong on 2008-05-10
Wonder if anyone could point me to an easy to follow tutorial which covers the installation of VirtualBox and how to get it up and running?

---

### Post by brettg on 2008-05-10
Hmmm, you pretty much just install it from the repos and run it. It will tell you you need to make a user group and put your user in that group and then you are done. 

That's basically it, I'm not sure there is enough material there to justify a howto.

---

### Post by billgoldberg on 2008-05-10
Installation:

"sudo apt-get install virtualbox-ose"

After it's install it should be accessable from "applications -> system tools".

Before you can use it, go to "system -> administration -> users and groups".

Highlight your username, and then press "manage groups", add virtualbox... to it.

It could be that you'll have to log out and log back in.

Then it's a matter of starting the program and doing what it asks.

---

### Post by Mze on 2008-05-10
Take a look at the [sticky]("http://ubuntuforums.org/showthread.php?p=4606825") in the Virtualization section of the forum.

---

### Post by sunbird on 2008-05-10
The [VB website]("http://virtualbox.org/") has some good information. There are two versions, one is open source and available from the repos. The other is not open source, but is free for non-commercial use and has more features. 

The VB gui is pretty easy to use, so I would just check out the VB website, read the FAQ there, and if you have specific problems with the config, just post them here.

---

