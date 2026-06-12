---
title: "network-admin autostart"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by cong06 on 2008-05-19
I want the program "network-admin" to load on startup.

It happens to be the program that allows one to set up the network (from System->Admin->Network), and in my case will remind me to make sure i have my connection only on wireless or Ethernet when I startup.

I went to /etc/rc.local and typed in:

network-admin (since I was told that it was run as sudo)

That failed...so I tried:

/usr/bin/network-admin

But in both cases, the program didn't show up. Maybe it has something to do with loading in the xserver?

---

### Post by RealPSL on 2008-05-19
I believe that the /etc/rc.local is probably loaded before the GUI starts. Even if it did not I do not think it would load in your X session. Why not load it by adding it as a program in your startup (System > Preferences > Sessions). The only down side to this is you will need to type the password when it starts.

---

### Post by cong06 on 2008-05-23
> **RealPSL said:**
> I believe that the /etc/rc.local is probably loaded before the GUI starts. Even if it did not I do not think it would load in your X session. Why not load it by adding it as a program in your startup (System > Preferences > Sessions). The only down side to this is you will need to type the password when it starts.

I was sure that I had tried this already, but it took forever to confirm it.

This does, in fact not work. putting it in System > Preferences > Sessions as  "sudo network-admin" and "network-admin"

Really all I want is a way to disable all internet on startup forcing me to re-enable it...setting it right.

Opening network-admin would be best, but disabling internet, forcing me to open network-admin would work too...(I think)

---

### Post by PinkFloyd102489 on 2008-05-23
Use gksudo instead of sudo.

---

