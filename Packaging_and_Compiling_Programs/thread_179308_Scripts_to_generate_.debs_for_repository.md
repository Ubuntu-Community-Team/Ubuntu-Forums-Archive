---
title: "Scripts to generate .debs for repository"
date: 2006-05-19
forum: Packaging and Compiling Programs
---

### Post by byteshack on 2006-05-19
This is probably not the correct forum to talk about this.  Pelase feel free to point me in the right direction.

So, vim 7 is out.  Debian unstable has it and I want it.  The only catch is I refuse to install things from source any more, and there are just too many headaches from installing things from Debian. Then I started wishing....

This is a scenario that I've found myself in a couple of times.  The pattern is somewhat like this:

* Ubuntu has version N of package
* Upstream has N + (>0) out
* I want to try version N + (>0) out

Now, the usual thing that I've done in the past is to either compile the package myself or make a .deb package and install that.

A while back I took a detour to Gentoo, and I was really impressed with how fast things got into their tree.  Their tree is really just a collection of scripts to compile the source!  Neato!  That means short turnaround between upstream and repository....

... then I wondered... wouldn't it be nice if package maintainers in Ubuntu/Debian were required to publish a script (plus additional patch files possibly) used to generate the packages found in the repositories?  I have looked all over for such a collection of scripts, but there seems to be none.  The nice thing about having such packages is that any one could technicall reporoduce the .debs that are in the repository.  Or even better, make new .debs, which are configured the same as previous releases of the packages are, but with new sources.

Does this sound interesting to someone? I realize this channel is not full of developers, but maybe someone can pick up the "signal" here and get me into the correct environments to make this request.

Cheers,
Daniel

---

### Post by ubuntu_demon on 2006-05-19
We have backports :
[http://www.ubuntuforums.org/forumdisplay.php?f=47](http://www.ubuntuforums.org/forumdisplay.php?f=47)

You can request backports at launchpad :
[https://launchpad.net/projects/ubp](https://launchpad.net/projects/ubp)

Or you can try to create your own backport. Here's some information about that :

[http://www.ubuntuforums.org/showthread.php?t=154433](http://www.ubuntuforums.org/showthread.php?t=154433)

---

### Post by ubuntu_demon on 2006-05-19
oops I accidentally moved this thread to "repository support" instead of "Packaging and Compiling Programs". fixed :)

---

### Post by byteshack on 2006-05-20
Backports don't quite cut it when you are working with unstable.  The idea of having the scripts to generate the current packages in the repository is that it would allow/encourage more people to contribute to them.  If one has a script that generates version N of a package, it is not very hard to modify the script to also generate version N+1 of that package.  The advantage is that scripts that have generated current .debs are already doing a lot of work to make sure the package is adhering to the distro's stadandars.

---

### Post by ubuntu_demon on 2006-05-20
You are right. A script to do it easily yourself would be nice. 

This seems scriptable :

[quote=jdong]
(1) apt-get source <packagename>

(2) Go into newly unpacked folder

(3) Edit debian/changelog. Add "~0custom1" to the version number in parentheses.

(4) Run [b]apt-get build-dep <packagename>

(5) Run dpkg-buildpackage -rfakeroot -b


You're done :)
[/quote]

Here's the location of that post :
[http://www.ubuntuforums.org/showpost.php?p=1006647&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1006647&postcount=9)
which belongs to the thread I mentioned previously :
[http://www.ubuntuforums.org/showthread.php?t=154433](http://www.ubuntuforums.org/showthread.php?t=154433)

Here's a relevant thread :
[http://www.ubuntuforums.org/showthread.php?t=103209](http://www.ubuntuforums.org/showthread.php?t=103209)
With this post announcing such a script :
[http://www.ubuntuforums.org/showpost.php?p=573229&postcount=6](http://www.ubuntuforums.org/showpost.php?p=573229&postcount=6)
And this post that it won't make Dapper :
[http://www.ubuntuforums.org/showpost.php?p=894289&postcount=24](http://www.ubuntuforums.org/showpost.php?p=894289&postcount=24)

---

### Post by byteshack on 2006-05-20
Not quite what I was looking for, but a LOT more.  Thanks!  I've already done a few :)  This really rocks.

---

