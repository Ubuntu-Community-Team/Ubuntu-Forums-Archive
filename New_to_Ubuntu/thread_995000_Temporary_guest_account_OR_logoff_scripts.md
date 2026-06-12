---
title: "Temporary guest account OR logoff scripts"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Hospadar on 2008-11-27
I'm wondering if there is a way I can set up the login screen in GDM to allow me to go directly into the temporary guest account. 

If not, I'm comfortable setting up a guest account that can login passwordless, but I'd like to be able to run a script (of my own design) on logout to delete any new files the guest user added.

I'd probably just empty out the guest user and copy over a slightly edited version of what's in the /etc/skel skeleton user files.

I just don't want guest users accumulating a bunch of files I don't care about and have to go in by hand and delete.

Thanks
L-tronix

---

### Post by RealPSL on 2008-11-27
I thought Ubuntu 8.10 provided a guest account that does exactly what you described by default. [http://www.ubuntu.com/getubuntu/releasenotes/810overview]("http://www.ubuntu.com/getubuntu/releasenotes/810overview")

---

