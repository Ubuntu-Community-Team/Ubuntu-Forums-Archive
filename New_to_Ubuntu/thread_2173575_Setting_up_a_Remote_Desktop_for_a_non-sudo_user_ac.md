---
title: "Setting up a Remote Desktop for a non-sudo user account in xubuntu"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-10
Hey guys & gals!

I'm very nearly done creating a super-simple pc for my grandmother to use. I've cut out all of the access, as well as the excess, and the last thing I want to do for this build is to allow remote desktop control. 

I have found and installed Vino on my sudo/adminstrater account. Unfortunately, it either can't be accessed by her account or I don't know how to find it. Also, because her account was created as non-administrater I'm not allowed to download items in the terminal...or, rather, I don't know how. I have since changed her account status to administrater, but it still won't let me download vino through the terminal.

I know that there's probably a very easy explanation that would allow me to do one or both of the things I'd like to do, unfortunately a couple of hours of googling "how to allow temporary administrator rights/sudo access" hasn't brought me any closer to resolution. 

So, I need to be able to:

1) Allow her account access to download vino through the terminal, preferably temporarily.

OR

2) Allow the vino program I've already downloaded on my administrator account to be used by all users.

Any ideas or tutorials are welcome at this point.

Cheers.

---

### Post by mastablasta on 2013-09-10
you install as admin with sudo and you appoint access to user by giving ownership of certain programes to specific user group. i think with chown command but there should be a GUI interface as well. man chown to see a bit what you can do.

but in short install the programme (sudo) and then add user to the group that can launch it/use it. :
[https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)

here is even specific info for xubuntu; [http://askubuntu.com/questions/71309/how-do-i-enable-remote-desktop-connection-on-xubuntu-11-10](http://askubuntu.com/questions/71309/how-do-i-enable-remote-desktop-connection-on-xubuntu-11-10)
and debian/ubutnu (a bit dated): [http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html](http://www.debianadmin.com/remote-desktop-sharing-in-ubuntu.html)

---

