---
title: "gftp - can I get this for Ubuntu"
date: 2005-02-02
forum: Repositories &amp; Backports
---

### Post by dickinsd on 2005-02-02
Hello.

I want to use gftp, I use it a lot on my fedora machine, I think its pretty good.

Can I get it for Ubuntu? If so how?

Also, using apt-get, is there a command similar to the yum command

yum list (eg yum list gftp) to get a list of packages with that name?

I ask because I tried apt-get install gftp, it couldn't find it, so I wanted to use the list command to get its full name, 

yum list gftp would produce 
gftp.i386     1:2.0.17-3      installed 
on my fedora box.

thanks

Dave

---

### Post by mendicant on 2005-02-02
Yes, it's available.  I would suggest using either aptitude (curses) or synaptic (GTK+) instead of pure command line stuff for doing most things, as you can get things like changelogs and descriptions.  If you insist, however:

% aptitude search gftp

You might also want to use aptitude because it keeps track of automatically installed dependencies, which is great when you uninstall stuff.

---

### Post by ember on 2005-02-02
gftp is in universe - just uncomment the corresponding line to your sources.list.

To your second question I have no direct answer - yet I think there is some apt-cache search or so.

Best,
ember

---

### Post by mendicant on 2005-02-02
Well, gftp-gtk and gftp-common are available in main and gftp-text is in universe.  So if you want the text client, you'd have to grab it from universe.

---

### Post by Sgood1971 on 2005-02-02
[QUOTE=mendicant]Well, gftp-gtk and gftp-common are available in main and gftp-text is in universe.  So if you want the text client, you'd have to grab it from universe.[/QUOTE]
 apt-cache searc <packagename> and apt-cache show <packagename> are great.

---

### Post by Sgood1971 on 2005-02-02
[QUOTE=ember]gftp is in universe - just uncomment the corresponding line to your sources.list.

To your second question I have no direct answer - yet I think there is some apt-cache search or so.

Best,
ember[/QUOTE]
  apt-cache search <packagename> and apt-cache show <packagename> are great.

---

