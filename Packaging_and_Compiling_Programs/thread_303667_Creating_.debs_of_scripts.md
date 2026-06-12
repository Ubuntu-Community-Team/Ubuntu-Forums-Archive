---
title: "Creating .debs of scripts"
date: 2006-11-20
forum: Packaging and Compiling Programs
---

### Post by mssever on 2006-11-20
I have several bash scripts and one ruby script that I want to package up for easy syncronization between my computers. I want to have one .deb per script and a meta-package that depends on them all.

I've read (most of) the Debian New Maintainers Guide, plus whatever else I could find by searching Google and the forums and wiki. Everything I've found deals with making typical binary packages, but I can't find any guidance for how I could provide simple installation instructions for my scripts. All they need to do is copy the file to /usr/bin and chmod +x.

I suppose I could create a Makefile of some sort, but that seems to me to be the incorrect way to approach this (since not every program uses make, there must be a more general way to instruct APT). Besides, I'd have to read up on how to create Makefiles, which seems like a waste of time given that it's not the best way to do what I'm trying to do, anyway.

Can somebody point me in the right direction?

---

### Post by RAOF on 2006-11-23
It seems that **dh_install** is what you want to be looking at.  In particular, you could have a debian/rules file that runs "dh_install *script* /usr/bin", I think.

You could check out the **mplayer-skins** package.  That's an example of a data-only package.

---

### Post by jpkotta on 2006-11-23
Why not make an installer script?  Yes, .debs are more powerful and they have the advantage of using the package management system, but it seems like overkill for such a simple task.  And installer scripts will work for any distro.

Put all the scripts in a directory.  Then add installer.sh to the directory:
```
#!/bin/bash

this_script=$0
cd `dirname $this_script`

for i in * ; do
  if [[ ! x"$i" = x`basename $this_script` ]] ; then
    cp -v $i /usr/bin
    chmod 555 /usr/bin/$i
    chown root:root /usr/bin/$i
  fi
done

```

Then make installer.sh executable and run it as root.  Put it in a zip file or tarball and move it to all of your machines.

---

### Post by mssever on 2006-11-23
@jpkotta, The reason I'm trying to make debs is so that I can put then in a repository and have them auto-updated. AFAIK I can't do that with a simple installer script.

@RAOF, Thanks for the tip! I'm able to generate a source package now, but I keep getting the following errors in pbuilder: ```
<snip>
 debian/rules build
mkdir -p debian/tmp/usr/local/bin debian/tmp/usr/share/doc/shred-recursive
cp shred-recursive debian/tmp/usr/local/bin
cp debian/copyright debian/changelog debian/tmp/usr/share/doc/shred-recursive
chmod 755 debian/tmp/usr/local/bin/shred-recursive
 fakeroot debian/rules binary
mkdir -p debian/tmp/usr/local/bin debian/tmp/usr/share/doc/shred-recursive
cp shred-recursive debian/tmp/usr/local/bin
cp debian/copyright debian/changelog debian/tmp/usr/share/doc/shred-recursive
chmod 755 debian/tmp/usr/local/bin/shred-recursive
#dh_install --autodest
dh_install shred-recursive /usr/local/bin
 dpkg-genchanges
dpkg-genchanges: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
dpkg-architecture: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
dpkg-parsechangelog: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
debian: warning: no utmp entry available and LOGNAME not defined; using uid of process (1234)
dpkg-genchanges: failure: cannot read files list file: No such file or directory
pbuilder: Failed autobuilding of package
W: no hooks of type C found -- ignoring
 -> Aborting with an error
<snip>
```Here's my debian/rules file (I'm mostly guessing as to the content here, since there seems to be a dearth of documentation): 
```
#!/usr/bin/make -f

package = shred-recursive
docdir = debian/tmp/usr/share/doc/$(package)
instdir = debian/tmp/usr/local/bin

build:
        mkdir -p $(instdir) $(docdir)
        cp $(package) $(instdir)
        cp debian/copyright debian/changelog $(docdir)
        chmod 755 $(instdir)/$(package)
clean:
        dh_clean

#binary-indep: build install
binary: build install

install:
        #dh_install --autodest
        dh_install $(package) /usr/local/bin
```I tried it first with dh_install --autodest, then changed it to the second version after re-reading your post. It didn't seem to make any difference.

Why can't I build this? The dpkg errors are really opaque to me.

---

### Post by mssever on 2006-11-29
bump

---

### Post by RAOF on 2006-11-29
The error's opaque to me, too.  Have you checked out the mplayer-skins source yet, though?  That does almost exactly what you want to do, and works :).

---

### Post by mssever on 2006-11-30
> **RAOF said:**
> The error's opaque to me, too.  Have you checked out the mplayer-skins source yet, though?  That does almost exactly what you want to do, and works :).

Before when I looked at that package, I couldn't figure it out. I guess I've learned a bit since then, though. I copied the debian/rules package from there and got a working deb.

Now, I want to set up a local repository. I've noticed that a lot of people seem to be using falcon for this--including you. However, I can't find falcon anywhere. It isn't in any repository I have, and I can't find it via Google. The Launchpad project page has nowhere to download the package from, as far as I can tell, amd the author's website is down. Where can I find it? Or, is there a better way to run a local repo?

---

### Post by RAOF on 2006-11-30
I really like falcon.  It works, is simple, and featureful.

```
# Falcon is toooooo cool
deb http://mirror.ubuntulinux.nl edgy-seveas extras
deb-src http://mirror.ubuntulinux.nl edgy-seveas extras

```

Is where I get my falcon from.

---

### Post by mssever on 2006-12-01
> **RAOF said:**
> I really like falcon.  It works, is simple, and featureful.

```
# Falcon is toooooo cool
deb http://mirror.ubuntulinux.nl edgy-seveas extras
deb-src http://mirror.ubuntulinux.nl edgy-seveas extras

```Is where I get my falcon from.

Thanks! Falcon is up and running now. Project finished.

---

