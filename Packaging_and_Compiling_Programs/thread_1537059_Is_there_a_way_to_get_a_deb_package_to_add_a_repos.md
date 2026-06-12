---
title: "Is there a way to get a deb package to add a repository and install a package?"
date: 2010-07-23
forum: Packaging and Compiling Programs
---

### Post by _sluimers_ on 2010-07-23
See my signature for what I want this for. 

As for why, this way someone would always get the newest version available whenever I update the ppa, sparing me from updating posts, links and/or files. 

I thought I solved it by simply adding a preinst file in the package
and write this:

```

#!/bin/bash
sudo add-apt-repository ppa:ika; sudo apt-get install ika

```

But that doesn't work. :(


Does anyone know how it is possible?
I know dropbox does it.

---

### Post by Penguin Guy on 2010-07-23
No. This is a bad idea. Do **not** do it.

The user adds your repository:
```
# add-apt-repository ppa:ika
```

Then installs your package through the repository:
```
# apt-get install ika
```

**Not** the other way round. Instead, post instructions about how to add the repository and install through apt on your website.


**EDIT:** Some links:
[LIST]
[*][ika (homepage)]("http://ika.sourceforge.net/")
[*][ika (sourceforge)]("https://sourceforge.net/projects/ika/")
[*][ika (svn@sourceforge)]("https://ika.svn.sourceforge.net/svnroot/ika")
[*][ika (launchpad)]("https://launchpad.net/~ika")
[*][ika (ppa@launchpad)]("https://launchpad.net/~ika/+archive/ppa")
[/LIST]

---

### Post by _sluimers_ on 2010-07-23
Is there no way then for users to add a repository and install the necessary packages by a click of a button?
There's a lot of users that rather want to click on something then having to type.

[EDIT] Never mind trying to use launchers[/EDIT]

---

### Post by Penguin Guy on 2010-07-23
> **_sluimers_ said:**
> Is there no way then for users to add a repository and install the necessary packages by a click of a button?
There's a lot of users that rather want to click on something then having to type.
You could write a script to do it, but the whole idea of one-click add-repo and install is generally frowned upon as it isn't very transparent. Also, if I understand correctly, this is a game development 'kit' and isn't actually a game in itself, in which case it shouldn't really be a [FONT="Courier New"].deb[/FONT] anyway.

On a side note, it looks like you've got some good code there but little code management, if you started a project on Launchpad and moved the code to a Bazaar branch you'll probably find development much easier and might get a few more people involved.

---

### Post by tgm4883 on 2010-07-23
Totally doable, I'm not sure why penguin guy thinks it's frowned upon. You can't have a package in the official repositories that add another repo, but you could definitely build a package that when it installs it adds the PPA.


I do it for mythbuntu-repos in postinst, take a look at

[http://bazaar.launchpad.net/~mythbuntu/mythbuntu/mythbuntu-repos/annotate/head:/debian/postinst](http://bazaar.launchpad.net/~mythbuntu/mythbuntu/mythbuntu-repos/annotate/head:/debian/postinst)


It does more than just adds a repo, all you really need to do is something like 

```
echo "deb http://$repo/mythbuntu/$version/ubuntu $release main" >> /etc/apt/sources.list.d/mythbuntu-repos.list
```

in postinst. Just make sure you have it remove the file in postrm

---

