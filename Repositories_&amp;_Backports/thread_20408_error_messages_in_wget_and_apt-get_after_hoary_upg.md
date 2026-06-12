---
title: "error messages in wget and apt-get after hoary upgrade"
date: 2005-03-16
forum: Repositories &amp; Backports
---

### Post by nottaclew on 2005-03-16
Hiyas,

As will become abundantly obvious, I am a newbie who has just upgraded from Warty to  Hoary and would appreciate some advice. Since then, wget and apt-get seem not to be able to' connect'. My internet connection is via LAN/cable modem.

The error message for wget is: 

Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number.

When running apt-get update, I get a whole swathe of this:

Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
(this comes up for every repository as far as I can tell).

Although Hoary seems to work, it seems a little 'odd' or incomplete (e.g. no synaptic, local language support is inconsistent, 3d rendering does not work and the machine tells me there is no xserver-xorg installed....)

Thanks in advance

S

---

### Post by mike998 on 2005-03-16
[QUOTE=nottaclew]When running apt-get update, I get a whole swathe of this:

Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
(this comes up for every repository as far as I can tell).
[/QUOTE]

You may want to change your apt-sources list.  There are no backports for hoary and you will need to install pgp for the nerim repositories to work.

---

### Post by nottaclew on 2005-03-16
Hiya,

THanks for the advice. I have double checked sources.list (against the GuideToHoary Wikipg) and tried to install pgp....still the same:

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Thanks

S

---

