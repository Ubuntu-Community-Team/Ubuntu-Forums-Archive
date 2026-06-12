---
title: "Could not authenticate"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by MJunkov on 2008-05-25
If I try to [unlock] the [Services Settings] which I have launched via the KMenu I get the following error:

"Could not authenticate
An unexpected error has occurred"

The same happens if I try to open [Users Settings] and probably others which will have to be [unlocked].

In a terminal window (not as root) I write: 
-------------------------------------------
$ services-admin

which triggers the same window as before. When trying to [unlock] I get this message in the terminal:

** (services-admin:11743): CRITICAL **: The name org.gnome.PolicyKit was not provided by any .service files

If I am root and issue the same command I get:
----------------------------------------------
No protocol specified

(services-admin:8778 ): Gtk-WARNING **: cannot open display: :0.0

Any help appreciated :)

---

### Post by PmDematagoda on 2008-05-25
Can you post the outputs of:-
```
hostname
```
and
```
cat /etc/hosts
```

---

### Post by MJunkov on 2008-05-25
$ hostname
Desktop

$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by MJunkov on 2008-06-04
Solved!

After installing: policykit-gnome (I also got policykit-doc and policykit-gnome-doc in case I had to dig deeper) I am met with a new Authenticate window asking for my password.

---

