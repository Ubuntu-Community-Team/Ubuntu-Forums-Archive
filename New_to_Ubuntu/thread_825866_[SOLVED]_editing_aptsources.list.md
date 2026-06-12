---
title: "[SOLVED] editing /apt/sources.list"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-11
I have several questions on this:

what does this do?

how do you do it?
(I want to do it because of this:

You can use apt to easily get the latest security updates. This requires a line such as

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib non-free

is there a way to do it other than editing that file?

Thanks!

I'm trying to make my system really secure.

I'm using debian if it matters.

---

### Post by Cypher on 2008-06-11
Systems->Administration->Sources, you can click the appropriate boxes there and that will edit the sources.list for you..

---

### Post by AnLGP on 2008-06-11
I don't have a DE.

---

### Post by wolfen69 on 2008-06-11
```
su
```
```
gedit /etc/apt/sources.list
```
then just add the line in question, and save the file.

---

### Post by AnLGP on 2008-06-11
add it anywhere?  or after a certain point?

---

### Post by overdrank on 2008-06-11
HI and this link may help
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
 To add to wolfen69 I believe that would be nano instead of gedit. gedit is for graphical use.

---

### Post by wolfen69 on 2008-06-11
> **AnLGP said:**
> add it anywhere?  or after a certain point?

you can add it to the bottom of the list.

---

### Post by ibuclaw on 2008-06-11
I prefer to add mine into a separate file inside /etc/sources.list.d folder.

[EDIT]
Works now :)
```
echo "deb http://security.debian.org/ etch/updates main contrib non-free" | sudo tee /etc/apt/sources.list.d/debian-security.list
```
Followed by
```
sudo apt-get update
```
Although, if you are adding it onto Ubuntu, it is not needed.

Regards
Iain

---

### Post by AnLGP on 2008-06-11
ok I've got one final question on this:

which line is the one I want to put in from here

[http://lists.debian.org/debian-security-announce/2008/msg00000.html](http://lists.debian.org/debian-security-announce/2008/msg00000.html)

if any?

This one?

[http://security.debian.org/](http://security.debian.org/) stable/updates main

---

### Post by ibuclaw on 2008-06-11
AnLGP, the **etch** and **stable** repos are identical to one another.
ie: if you've already added one, no point in adding the other.

Regards
Iain

---

### Post by AnLGP on 2008-06-11
ok.  what if I'm running lenny?

---

### Post by ibuclaw on 2008-06-11
If you are running lenny, you do it in the exact same manner, but replace etch/stable with lenny/testing

ie:
```
deb http://security.debian.org/ lenny/updates main contrib non-free
```or```
deb http://security.debian.org/ testing/updates main contrib non-free
```

Iain

---

### Post by AnLGP on 2008-06-16
Thank you very much :)

---

