---
title: "where are thunderbird(and other email) icons stored?"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by Froylan on 2013-01-13
I am making the ultimate(well maybe not :P ) customization of my ubuntu 12.04 and I want to change some things, the most important icon that i want to edit is the one that appears as a notification when you get new email. thanks in advance if you read this.

---

### Post by Lars Noodén on 2013-01-13
You can see all of the files that came with the package Thunderbird using the program [dpkg](http://manpages.ubuntu.com/manpages/precise/en/man1/dpkg.1.html)

```

dpkg -L thunderbird

```

Maybe one of those is the icon you are looking for.

---

### Post by grahammechanical on 2013-01-13
You do realize do you not that the icons will change depending upon the theme chosen?

Go to /usr/share/icons and open a theme folder and look in the status folder. There are icons of different sizes kept together in folders.

You will find the blue envelop icon representing a new message at

/usr/share/icons/ubuntu-mono-dark/status/22. It is called indicator-messages-new.svg. It also appears in the 24 folder. And again in the 16 folder.

Regards.

---

