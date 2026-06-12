---
title: "Aptitude, apt and synaptic"
date: 2011-10-03
forum: Recurring Discussions
---

### Post by chaffdog on 2011-10-03
Hiya,

could someone please explain these three package management tools to me.  Specifically:

I understand that the synaptic package manager is a GUI interface for apt, while aptitude is a separate program with a separate database.  Is this correct?

If I install a package with apt, will it show as installed in aptitude?

If I add a repository with apt, will it be added in aptitude?

If the databases are separate for apt and aptitude, is there a way to syncopate them?

---

### Post by MG&amp;TL on 2011-10-03
Errr..apt-get vs. aptitude:

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Synaptic is just a graphical frontend to apt. Like the software centre.

And I don't know, but I think you probably mean *synchronize*, not *syncopate*-slightly different things....;)

---

### Post by TeoBigusGeekus on 2011-10-03
Aptitude's just a front-end to apt.

---

### Post by haqking on 2011-10-03
aptitude is apt with aptITUDE

apt is yum which is a modified rpm similar to a zyppy Yast but pacman would eat them all unless you got PETget....dont you love choice ;-)

---

### Post by TeoBigusGeekus on 2011-10-03
> **haqking said:**
> aptitude is apt with aptITUDE

apt is yum which is a modified rpm similar to a zyppy Yast but pacman would eat them all unless you got PETget....dont you love choice ;-)

[IMG]http://www.scenicreflections.com/ithumbs/Pacman_-Syu_-_Transparent_Wallpaper_xx0kn.jpg[/IMG]

---

### Post by chaffdog on 2011-10-03
> **MG&TL said:**
> Errr..apt-get vs. aptitude:

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Synaptic is just a graphical frontend to apt. Like the software centre.

That's very helpful, thank you.

> And I don't know, but I think you probably mean *synchronize*, not *syncopate*-slightly different things....;)

Yes, that's what I meant. I didn't get much sleep last night...

> **TeoBigusGeekus said:**
> Aptitude's just a front-end to apt.

Ok, so does that mean changes made in apt will be reflected in aptitude (i.e. new packages, repositories etc).  I've read in other places that they use separate databases so using both can screw things up, so I'm trying to get the story straight.

---

### Post by MG&amp;TL on 2011-10-03
> **haqking said:**
> 

apt is yum which is a modified rpm similar to a zyppy Yast but pacman would eat them all unless you got PETget....dont you love choice ;-)

If distros were cars, redhat would have a few more rpm than ubuntu.

---

### Post by TeoBigusGeekus on 2011-10-03
> **chaffdog said:**
> Ok, so does that mean changes made in apt will be reflected in aptitude (i.e. new packages, repositories etc).  I've read in other places that they use separate databases so using both can screw things up, so I'm trying to get the story straight.
I don't know about that; I just know that aptitude is a ncurses front-end for apt.
Just use apt if you ask me.

---

### Post by MG&amp;TL on 2011-10-03
> **chaffdog said:**
> I've read in other places that they use separate databases so using both can screw things up, so I'm trying to get the story straight.

If I were you, I'd choose one or the other, then get on with it. :)

---

### Post by mibart on 2011-10-03
Packages in Ubuntu are managed (I mean: installed and removed, upgraded etc.) by tool dpkg. You hardly ever directly use dpkg itself.

Apt is command line front end for dpkg. It can search for packages in repositories (defined in apt's configuration), download packages and install them, and check for dependencies and resolve them. Dpkg itself also checks for dependencies during install, but simply refuse to install package if dependencies are not met (apt would download and install required packages in that situation)

Aptitude is front end for dpkg as well as apt. Aptitude can be used as command line tool, but also has pseudo-GUI interface (text based, in ncurses I guess) and that interface is rather non-intuitive and not very user-firendly.

Synaptic is GUI front end for apt.

Generally speaking, changes made in one package management tool should be visible in the others. Anyway it is good idea to stick to that one You prefer the most.

Personally I use Synaptic whenever I can. If I can't use Synaptic for any reason I use apt (very unlikely).

---

### Post by mcduck on 2011-10-04
> **MG&TL said:**
> Errr..apt-get vs. aptitude:

[http://pthree.org/2007/08/12/aptitude-vs-apt-get/](http://pthree.org/2007/08/12/aptitude-vs-apt-get/)

Synaptic is just a graphical frontend to apt. Like the software centre.

And I don't know, but I think you probably mean *synchronize*, not *syncopate*-slightly different things....;)

That is rather outdated article. :D

At the moment the only practical difference between apt and aptitude is that aptitude has a ncurses-based terminal "gui" if you want one.

Apart from that it really is just a question of personal preferences, both tools do the same things.

---

### Post by haqking on 2011-10-04
Aptitude has all the interactive features of dselect with the command line options of apt-get.

Synaptic is a GUI-X based APT

---

### Post by philinux on 2011-10-04
You can use either. It's just down to personal preference now.

See here for more discussion.
[http://ubuntuforums.org/search.php?searchid=83287522](http://ubuntuforums.org/search.php?searchid=83287522)

Moved to Recurring.

---

