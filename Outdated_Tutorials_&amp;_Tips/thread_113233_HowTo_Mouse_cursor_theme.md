---
title: "HowTo: Mouse cursor theme"
date: 2006-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2006-01-06
I use a different GNOME mouse theme in another distro and decided to port it over to Ubuntu. 

The default mouse theme, Human, is located at [COLOR="Blue"]/usr/share/icons/Human/cursors[/COLOR]
 
Open up a root terminal, input your [COLOR="DarkOrange"]su[/COLOR] password
```

cd /usr/share/icons/Human
makdir old-cursors
cd /usr/share/icons/Human/cursors
mv * /usr/share/icons/old-cursors
cp [COLOR="Lime"]/home/{your username}/green[/COLOR]/* /usr/share/icons/Human/cursors

```

logout, login. 
It's got two different watches, though, the SuSE animated blue and the small regular (which only seems to work within FireFox). But the cursors are in green. 

For me the green cursors go great with my green scroll bars from Gentoo's GNOME flavour of Linux. 

Here are the green cursors:

---

