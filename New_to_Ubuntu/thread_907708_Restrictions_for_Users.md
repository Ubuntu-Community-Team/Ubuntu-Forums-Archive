---
title: "Restrictions for Users"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by moose4204l on 2008-09-01
Ok, I have my own user account on my ubuntu server box. I just added a guest account through the adduser utility. I set up the guest account so I can have my friends svn or scp files into the server box. Is there a way I can restrict them from going anywhere else on the computer or do I have to chmod 700 -R /home/moose so they cant have access to my stuff?

Thanks

---

### Post by moose4204l on 2008-09-01
bump

---

### Post by cszikszoy on 2008-09-01
I don't recommend changing the file permissions on your home directory.  I believe GDM complains if they aren't set to 644.

I could be wrong about this though...

You might want to check out the new features of Intrepid Ibex (8.10) which will be launching soon.

They plan to fully integrate a guest account, and it looks like this is pretty much what you're looking for.

More information here: [https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount](https://wiki.ubuntu.com/DesktopTeam/Specs/Intrepid/GuestAccount)

---

### Post by moose4204l on 2008-09-01
Thats pretty interesting but not quite what I am looking for. I have a text server box that I leave running. I want my friends to be able to log into it remotely or ssh, scp, or WinScp and be able to add files to their /home/guest/workspace folder so they dont have to email it or use a flash drive, etc. But I want the protection of them not being able to cd to my directory or view anything outside there /home/moose/workspace directory.

---

### Post by egalvan on 2008-09-01
Try posting a similar question over on the SERVER forum.

I know this is possible, it forms the basis of (true) multi-user systems.
I just haven't reached that level of knowledge yet.

ErnestG

---

### Post by moose4204l on 2008-09-01
its not reall a server question as it is just a user account and admin related

---

### Post by ds[de] on 2008-09-01
There's no need to bump your thread every few minutes if nobody has answered. It's getting a little annoying, please read the Sticky 'Forum DO'S and DON'T's'.

_DON'T_
```
8) Bump your posts too often (around once every 24 hours is recommended)
```

---

### Post by moose4204l on 2008-09-01
people have answers they are neglecting me, i also kind of need this tonight thats why. its a bit of a high priority for me.

---

### Post by egalvan on 2008-09-01
> **moose4204l said:**
> people have answers they are neglecting me, i also kind of need this tonight thats why. its a bit of a high priority for me.

No one is "neglecting" you. They are all volunteers.
Treat them with respect. They deserve it.

ErnestG

---

### Post by moose4204l on 2008-09-01
> **egalvan said:**
> No one is "neglecting" you. They are all volunteers.
Treat them with respect. They deserve it.

ErnestG

dude, i wasnt that serious. I been apart of these forums forever and i know all of that. please follow the forum rules and stay on topic ;)

---

### Post by ds[de] on 2008-09-01
IMO, the forums are for more in-depth problem descriptions.
If time is of the essence I usually refer to #ubuntu on irc.freenode.org.

---

