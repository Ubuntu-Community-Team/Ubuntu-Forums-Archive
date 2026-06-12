---
title: "pyGame 1.7 compile nightmare (repost)"
date: 2005-11-19
forum: Programming Talk
---

### Post by Bigglez on 2005-11-19
Hello, I had this posted in Kubuntu Support forum, but had no takers, so took the risk of reposting it here. If there is a way to move threads to other forums, I missed it... 

So here it is:

I have tried and tried to compile pygame 1.7 on Kubuntu 5.04 (Oh damn, just saw this is the 5.10 forum. Sorry.) and I cannot get it working.

I tried to install the pygame 1.7 debian package (not available in ubu repos) but it has deps and those are not available on the ubu repos either. I could force it, but I don't want to break kynaptic.

[Insert: I have used the deb file. It does complain about libc being too old and sdlmixer too. I just ran pygame anyway - and it runs! It's not a nice fix and it still leaves the problem unsolved.]

When I try to compile pygame1.7 using the "python setup.py install" it chokes on environment variables. These ones mainly:
CC, OPT, CCSHARED, SO
How many more, I just don't know. I traced these by following-along in the source code of the various python modules that threw errors.
I tried installing 'gcc' and then faking the flags.
I set CC to "gcc" and to "gcc-3.3" (exporting all the while) to no avail.
I even hacked the python code to make the vars a space " " when the flags were not found in the environment. Errors all the way.

I am used to Linux on Fedora and these flags just work. I am totally at sea on Kubuntu. Can anyone advise me as to what to do?

I tried the pygame IRC and they were stumped. Their opinion of Kubuntu was unflattering to say the least.

Oh yeah - I have all the SDL deps that pygame1.7 (from the source pov) seems to want.

Any boffins out there?
:)

---

### Post by toojays on 2005-11-19
I would recommend you download the source package from Debian and rebuild that for Kubuntu. Going through that process will ensure that you have the right build-deps, and will ensure that the final package is consistent with Debian's python conventions. The main steps involved are: 1) Download the three files the bottom of [Debian's page for the pygame source package]("http://packages.debian.org/unstable/source/pygame"). 2) Use "dpkg-source -x pygame_1.7.1release-1.dsc" to unpack the source tarball and apply debian-specific patches. dpkg-source is in the dpkg-dev package. 3) Go into the directory which is created in the previous step and run "dpkg-buildpackage -rfakeroot". (You need to install the fakeroot package for this). There will probably be a couple of false starts as the build process identifies build-dependencies which you don't have. You can shortcut this by reading the .dsc file. If all goes well you will end up with the deb files you need to install pygame onto your system.

---

### Post by toojays on 2005-11-19
By the way, you can't just install "gcc". You will need to install the "build-essential" package to get some other critical development files.

---

### Post by Bigglez on 2005-11-19
toojays - that sounds a little hairy all in all. I'll give it a bash, but I would like to know how to setup the Kubuntu system so that normal compiling can be done.
If I install that "build-essential" package, will that solve the problem of those missing flags?
(I gather the flags have to be set by some startup script or other, but they are not being set. Wish I had a more technical insight into these mysteries! :D )

Thanks for the feedback.

---

### Post by toojays on 2005-11-19
Yes. Probably the number 1 cause of being unable to compile in Ubuntu is having gcc (or g++) installed, without having installed the rest of the packages pulled in by build-essential.

---

### Post by Bigglez on 2005-11-19
Well - I installed "build-essential" and it pulls in g++ and some other stuff. 
I went to try "python setup.py install" and got all the same old errors. 

Would my posting the error help in any way?

---

### Post by Bigglez on 2005-11-19
toojays - you da daemon ;)
I followed your deb instructions and all has come to pass. The python is gaming and Kubuntu has not choked on its insolent coils!

Thanks for that good info.

---

### Post by Bigglez on 2005-11-19
Just to clarify for others:
It seems all I needed to do was install the following packages:
python2.3-dev 
python2.4-dev
build-essential
and then the compilation of the original pygame 1.7 (from the pygame website) worked fine.

:D

---

