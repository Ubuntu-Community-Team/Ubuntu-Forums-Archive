---
title: "How to build a .deb package from Git repo?"
date: 2011-01-04
forum: Packaging and Compiling Programs
---

### Post by jasiu85 on 2011-01-04
Hey guys,

I work at a small company where we use to deploy things by just checking out the repo and copying stuff to production servers. This has to come to an end, enter .deb packages! 

So I'm wondering what's the best procedure to do that. I already know how to create .deb packages, most of our stuff is Python and we're going to use python-support and cdbs. But how to maximally automate this?

We have a Git repo and ideally the whole thing should work like this:
* a tag is created in the Git repo (the version can be provided manually)
* some file like 'version.py' is created so that setup.py and the packaged software can refer to it and know the tag
* changelog is created from the Git commit logs
* the package is built (that's the part I've worked out - python-support and cdbs are involved here)
* optionally, the package is uploaded somewhere

There's a .deb package named 'git-buildpackage', is it suitable for this task? So far I can tell that it has one drawback - it looks for the 'debian/' directory in the root of the repository, which is not the case - our repo consists of several subdirectories, each contains a subproject that will be packaged independently.

Regards,

Mike

---

### Post by SevenMachines on 2011-01-04
Don't really know much about git but i've done something like this before

# Add changelog entry based on git commit messages
$ git-dch

# Build debian package, add git tag and push to remote server 
$ git-buildpackage --git-tag --git-posttag="git push && git push --tags"

Not sure about creating version.py or how it would work with a number of packages in the same repository though. Perhaps the --git-prebuild command might help? something like
$ git-buildpackage --git-prebuild="creates_version_script"

Note theres some scripts in /usr/share/doc/git-buildpackage/examples which might be worth a look

---

