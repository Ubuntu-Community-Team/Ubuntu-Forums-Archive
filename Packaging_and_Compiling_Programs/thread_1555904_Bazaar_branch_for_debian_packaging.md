---
title: "Bazaar branch for debian packaging"
date: 2010-08-18
forum: Packaging and Compiling Programs
---

### Post by MrQuincle on 2010-08-18
Dear all,

Recently I switched to Launchpad to maintain a project, see [http://bazaar.launchpad.net/~annevanrossum/robot3d/trunk/files](http://bazaar.launchpad.net/~annevanrossum/robot3d/trunk/files) 

I would like to maintain a separate branch for debian packaging. It don't like it that the trunk has a /debian folder in it. 

[LIST]
[*]How would I initiate the package branch?
[*]Would it only contain the /debian folder? I think that's called "split" mode. I prefer to have also the source code in the packaging folder.
[*]How would I update the package branch from the normal/release branch?
[/LIST]

I would run "bzr export" in the normal/release branch, such that the orig.tar.gz tarball does not contain the debian directory. I can of course "bzr ignore debian", but then the debian directory is not in version control at all. Then I would like to update the package branch, and create my package with "bzr builddeb".

Thanks in advance!

Anne

---

### Post by SevenMachines on 2010-08-20
After a couple of hours trying to bazaar-ify my knowledge (and messing it up a lot :) ) and playing around on launchpad.... you might want to take a look at 'recipes'. You can set up recipes to merge in different packaging branches and nest other bzr branches and suchlike. 

[https://help.launchpad.net/Packaging/SourceBuilds/Recipes](https://help.launchpad.net/Packaging/SourceBuilds/Recipes)

[EDIT] I dont know if you can do this locally too or not, i've only just looked into it

---

### Post by SevenMachines on 2010-08-20
oh! see [https://help.launchpad.net/Packaging/SourceBuilds/BzrBuilder](https://help.launchpad.net/Packaging/SourceBuilds/BzrBuilder)
$ bzr help builder

what great things the bzr and launchpad people have given us to play with :)

---

### Post by MrQuincle on 2010-08-20
> **SevenMachines said:**
> oh! see [https://help.launchpad.net/Packaging/SourceBuilds/BzrBuilder](https://help.launchpad.net/Packaging/SourceBuilds/BzrBuilder)
$ bzr help builder

what great things the bzr and launchpad people have given us to play with :)

Ah, perfect! I hope I can figure this out. I wish there was a guide that was dedicated exactly to having a separate packaging branch. At [https://help.launchpad.net/Packaging/SourceBuilds/KnownLimitations](https://help.launchpad.net/Packaging/SourceBuilds/KnownLimitations) they say this:

> If bzr cannot merge the packaging branch into the base branch (e.g. due to parallel imports), the "nest" command must be used. If the "nest" command is used, the packaging branch must be the contents of the debian directory (rather than containing a debian directory). (Bug #479705)

That helps already. By the way, simply "sudo aptitude install bzr-builder" worked already on my system, so you won't need to actually use their PPA [https://edge.launchpad.net/~dailydebs-team/+archive/bzr-builder](https://edge.launchpad.net/~dailydebs-team/+archive/bzr-builder)

Thanks again for the great pointer! I hope to catch up with you some time. ;)

---

### Post by MrQuincle on 2010-08-20
A kind of tutorial for everyone who was already veering off in another direction, like me... Suppose you want to have a local bazaar branch for Debian, after you have been maintaining it in the trunk for a while... We assume normal practice, namely that you are not working on the trunk itself, but on a separate local branch, and merge so now and then your hacking activities back into the trunk.

**Tutorial**
# We assume you have been working in a local branch and that the trunk is synchronised with that branch
# They will be assumed to be: $PROJECT/trunk and $PROJECT/local

cd $PROJECT
mkdir debian # Or packaging or however you want to call your packaging branch
cd debian
rsync -avzcuL --exclude='*.bzr' ../trunk/debian
bzr add
bzr commit -m "Import stand-alone debianized branch"
bzr push lp:~yourname/yourproject/debian

# Remove debian directory from trunk
cd ../trunk
bzr rm debian
bzr commit -m "Remove debian directory. Will be replaced by nesting"

# Now create a project.recipe somewhere. I added it in the trunk:
vim project.recipe

# Add this
```

# bzr-builder format 0.2 deb-version 0+{revno}+{time}
lp:project
nest debian lp:~yourname/yourproject/debian debian

```

# Test it locally:

mkdir ~/temp

bzr dailydeb robot3d.recipe ~/temp
sudo cowbuilder --build ~/temp/project_0*.dsc

# Don't forget to merge the changes in the trunk back to your local branch:
cd $PROJECT/local
bzr merge ../trunk
bzr commit -m "Removed debian directory"

# Go to your PPA on Launchpad, use edge in the URL!
firefox [https://code.edge.launchpad.net/~yourname/yourproject/trunk](https://code.edge.launchpad.net/~yourname/yourproject/trunk) 

# You will now be able to do the same but than on Launchpad, search for "Create packaging recipe"
# It is explained here: [https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted](https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted)

---

