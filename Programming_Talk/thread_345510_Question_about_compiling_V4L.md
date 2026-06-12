---
title: "Question about compiling V4L"
date: 2007-01-24
forum: Programming Talk
---

### Post by 64mgb on 2007-01-24
Hi all -

I'm trying to get a Diamond PVR-560 TV card to work using IVTV/V4L.  I think I'm very close to making it work, but I think I'm at the point where I'm being held back by my lack of knowledge about Linux in general, and the proper way to download and compile source code in particular.  Here's the situation:

I use Mercurial to download the v4l-dvb-kernel tree.  When I do this I am in the /usr/src/linux/drivers folder, so that's where it ends up:

/usr/src/linux/drivers/v4l-dvb-kernel

Under that there are several folders like v4l, linux, v4l_experimental, etc.  To compile, I go into the v4l folder and do make clean, then make and it compiles all the modules, then I do make install.

Here's my question...should I be downloading the source in such a way as to overwrite the source files in /usr/src/linux/drivers, rather than downloading them into their own tree under drivers?  If so, how do I go about doing that?  I believe that when I compile the way I've been doing it, it is actually using the source files in the drivers tree, rather than in the v4l tree.

Sorry if this is a very basic question, and I did not do any searching because I didn't know what terms to use to get meaningful results.  I hope I've explained my situation clearly...if not let me know!

Thanks,
Rich

---

### Post by funkydan2 on 2007-02-07
My understanding is that as long as /usr/src/linux points to the headers of the kernel you are currently running, then it won't matter where you download the updated v4l drivers to.

I reckon you should run mercurial when you are in your home directory (~) or a subdirectory there-of and then you won't be mixing up your new source code with the stuff in the kernel source.

DS

---

