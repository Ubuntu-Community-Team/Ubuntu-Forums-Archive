---
title: "[SOLVED] Setting default ubuntu session"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by peterjakey on 2008-08-13
Hi, I have Kubuntu, but decided to install the ubuntu-desktop. How can I set the default session to KDE and remove GNOME from list of options as I have removed it?

---

### Post by alienexplorers on 2008-08-13
Have you tried running the script for removing gnome on this page: [http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by peterjakey on 2008-08-14
> **alienexplorers said:**
> Have you tried running the script for removing gnome on this page: [http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

Thanks for your reply, I ran the script and it cleaned my system free of gnome, however KDE now crashes and the outside of windows dont appear so I cant minimize, close or drag windows. The only way i can use the system is through the terminal outside of an X-server session. Ive tried running the fix x utiltiy from recovery mode and that didnt work, I also tried installing kde4-core  but I got the same behavior as kde3. Is there a simple fix to this or will I need a clean install?

---

### Post by TheMaxzilla on 2008-08-14
> and the outside of windows dont appear so I cant minimize, close or drag windows.
```
sudo kde-desktop-decorator
sudo kde-desktop-decorator --replace
```

---

### Post by peterjakey on 2008-08-14
> **TheMaxzilla said:**
> ```
sudo kde-desktop-decorator
sudo kde-desktop-decorator --replace
```

I tried that and the command was not found

---

### Post by TheMaxzilla on 2008-08-14
Whoops! Forgot something...

```
sudo apt-get install kde-desktop-decoration
kde-desktop-decoration
kde-desktop-decoration --replace
```
This should work- I don't think sudo will work with it. :)

---

### Post by peterjakey on 2008-08-14
> **TheMaxzilla said:**
> Whoops! Forgot something...

```
sudo apt-get install kde-desktop-decoration
kde-desktop-decoration
kde-desktop-decoration --replace
```
This should work- I don't think sudo will work with it. :)

sorry but the package was not found? do I need to add any repositories to my sources.list?

---

### Post by TheMaxzilla on 2008-08-14
*poof* Sorry, I screwed up (again).
```
sudo apt-get install kde-desktop-decorator
kde-desktop-decorator
kde-desktop-decorator --replace
```

Now it WILL work.

---

### Post by peterjakey on 2008-08-14
> **TheMaxzilla said:**
> *poof* Sorry, I screwed up (again).
```
sudo apt-get install kde-desktop-decorator
kde-desktop-decorator
kde-desktop-decorator --replace
```

Now it WILL work.

sorry to be a pain, but its still coming up as package not found

---

### Post by hosk on 2008-08-14
kde-desktop-decorator is provided by compiz, you could try installing compiz and see if that helps.

sudo apt-get install compiz-kde

---

### Post by peterjakey on 2008-08-14
> **hosk said:**
> kde-desktop-decorator is provided by compiz, you could try installing compiz and see if that helps.

sudo apt-get install compiz-kde

I installed compiz-kde but the kde-desktop-decorator --replace command was still unknown

---

### Post by hosk on 2008-08-14
well, you could try compiz --replace && emerald --replace

but if that doesn't work your system might not work with compiz, which means we'd just have to find you a new window decorator.

---

### Post by anjilslaire on 2008-08-14
make sure all of kubuntu-desktop is installed:

```

sudo apt-get install kubuntu-desktop

```

I wouldn't mess with compiz just yet; you want KDE functioning correctly 1st.

After kubuntu-desktop is properly installed again, do this:
```

sudo dpkg-reconfigure gdm

```

It may need to be run as kdm instead of gdm depending on which is currently in use. Either way, set it to kdm. Then, when you login in, you can select Sessions and set KDE as default.

---

### Post by peterjakey on 2008-08-15
> **anjilslaire said:**
> make sure all of kubuntu-desktop is installed:

```

sudo apt-get install kubuntu-desktop

```

I wouldn't mess with compiz just yet; you want KDE functioning correctly 1st.

After kubuntu-desktop is properly installed again, do this:
```

sudo dpkg-reconfigure gdm

```

It may need to be run as kdm instead of gdm depending on which is currently in use. Either way, set it to kdm. Then, when you login in, you can select Sessions and set KDE as default.

I tried installing kubuntu-desktop again but im still having problems, the system seems to be unstable as most programs crash or just simply wont load. I cant even type in the terminal unless i do it outside of the gui

---

### Post by peterjakey on 2008-08-17
I guess ill just do a reinstall...is it possible to do a repair instalation like windows?

---

