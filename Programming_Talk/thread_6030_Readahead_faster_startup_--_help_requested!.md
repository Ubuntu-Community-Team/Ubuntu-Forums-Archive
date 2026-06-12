---
title: "Readahead: faster startup -- help requested!"
date: 2004-11-24
forum: Programming Talk
---

### Post by jdong on 2004-11-24
Those who are familiar with Fedora know what 'readahead' and 'readahead_early' are. They start during the init process, caching key files during startup while no hard disk is being used (i.e. hotplug time, DHCP time)
  
 After readahead is done, Fedora is able **to start GNOME in less than 5 seconds**! I'm interested in getting this in Hoary.
 
  I ported this system over to the point that it installs fine on Ubuntu, but I need to tweak the file list.
  
  Obviously, Fedora and Ubuntu have different paths/files loaded at startup!
  
Hmm, dead link.... nuked my server last week. Will come back with new and improved version.
  
  I gave a link the the source. Do a **make;make install. **Link /etc/init.d/readahead to /etc/rc2.d/S00readahead and /etc/init.d/readahead_early to /etc/rcS.d/S00readahead_early.
  
  The list of files to cache during runlevel 2 is in **/etc/readahead.files **and the files to cache before runlevel 2 is in **/etc/readahead.early.files**. Please tweak these! Thanks
 
 ****DISCLAIMER****: This is **experimental software*. ***I simply stripped this from Fedora's kernel-utils srpm, scribbled a quick makefile for it, and posted it for development. Though incapable of damaging/writing to anything, this should not be deployed (yet) on production systems.

---

### Post by dataw0lf on 2004-11-24
Excellent!  I'm going to take a look at it after I get off work (only a half day today!).  
dataw0lf

---

### Post by jdong on 2004-11-24
Hmm, there's got to be a good way of seeing which files are loaded at startup... GDM, gnome-session, and all the pictures are good candidates...

Would any Ubuntu developers be interested in helping?

---

### Post by Daniel G. Taylor on 2004-11-29
I recently read on a mailing list somewhere that the redhat guys are implementing some sort of "popularity" list of files being loaded at startup for a particular system and then using the readahead for those files, since it can be quite system-specific. I think there was also a recent story on Planet GNOME or some other news site about it, and they went from grub to browsing in Firefox in like 40 seconds.

I would assume their work could also be adapted for Ubuntu and made mostly automatic. Cool stuff :)

---

### Post by jdong on 2004-11-29
if you can find relevant links, I'd be glad to take a look!

---

### Post by Daniel G. Taylor on 2004-11-30
[QUOTE=jdong]if you can find relevant links, I'd be glad to take a look![/QUOTE]
Sure thing. I think all the work is currently optimized for specific systems, but it should be possible to get a generic list of files to be preloaded for new systems, and then rearrange/edit the list as the system is booted a few times and we see exactly what the system generally needs.

Test and optimizations done by David Zeuthen
[http://www.redhat.com/archives/fedora-devel-list/2004-November/msg01374.html](http://www.redhat.com/archives/fedora-devel-list/2004-November/msg01374.html)

Original message by Owen Taylor (announcing the challenge and some ideas)
[http://www.redhat.com/archives/fedora-devel-list/2004-November/msg00447.html](http://www.redhat.com/archives/fedora-devel-list/2004-November/msg00447.html)

To be honest I haven't looked into this stuff that much, but it's very interesting indeed, and would be a welcome addition to Ubuntu. As always I'm willing to help out with anything I can :)

---

### Post by jdong on 2004-12-02
Hmm, we need some way to make lists of files accessed during bootup.

I see two ways:

1) OProfile was mentioned. Never used it, barely heard of it! Perhaps it has some sort of way of monitoring disk access?

2) Hack the kernel to dump the name of any file accessed into a textfile.... Prefer not to do it this way unless necessary!

---

### Post by Lovechild on 2004-12-02
There is already a patch that makes the kernel print every file it opens I think, even in mainline if I'm not mistaken.

---

### Post by Daniel G. Taylor on 2004-12-02
Well, has anyone tried contacting David Zeuthen? He _has_ done it before so he should be able to help us pretty easily. According to those messages he used a modified init script so we should be able to do the same.

Also, this doesn't necessarily have to do with the readahead, but is anyone working on optimizing the bootup's processor and network usage? Ideally we would have the processor, network, and disk usage all maxed out for the shortest possible amount of time as everything that can possibly load in parallel does so.

Hey Lovechild, been a while ;)

EDIT: Actually, if readahead is done right and there are no blocks on reads I suppose it would come close to maxing out the processor usage. I do notice during startup that the network daemons are started linearly, though. Any chance of parallelizing them???

---

### Post by Lovechild on 2004-12-02
Do I know you?

Anyways I think it's good that overall performance and boottime is being considered a target now in many distros, it has really gone unnoticed that our boottime has increased over the years. 

Personally I think we might need to consider Seth Nickell's SystemServices for a modern replacement to our initsystem, with dbus and the kevent layer I'm sure we can shave time off that boot just by using the new information we are able to reach.

---

### Post by Daniel G. Taylor on 2004-12-02
> Do I know you?

Gentoo forums a while back. I co-created and developed Porthole ([http://porthole.sf.net](http://porthole.sf.net)) and created the Lila themes project ([http://lila-theme.uni.cc](http://lila-theme.uni.cc)). While I don't use Gentoo anymore the projects do live on :)

---

### Post by Lovechild on 2004-12-03
What's with Gentoo and purple.. it's a horrid color - perhaps the ugliest color in the world.

Porthole was nice, but never innovative, and it kept crashing on me when I used it, that could have changed as I only tried 0.2 or something like that. I was however the first python app I ever read, as I was writting my own portage + gui clone in C#, that got about.. 6 steps into the design phase then I scraped the idea thinking people would never use it.  ](*,) 

Anyways I'll help out this little speed project anyway I can, just pm me.

---

### Post by AndersAA on 2004-12-04
You might wanna look at gentoo's info on this aswell:
[http://bugs.gentoo.org/show_bug.cgi?id=64724](http://bugs.gentoo.org/show_bug.cgi?id=64724)

---

