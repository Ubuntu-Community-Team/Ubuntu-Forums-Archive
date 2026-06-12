---
title: "Rolling a package with dpkg-deb"
date: 2009-09-12
forum: Packaging and Compiling Programs
---

### Post by internalkernel on 2009-09-12
I've been all over trying to figure this one out. Perhaps I'm stuck on not really understanding the difference between what dh_make does and dpkg-deb. I've read the Debian policy guide, maintainer's guide, and the complete ubuntu packaging guide. Most of those guides were focused on using dh_make which seems to fail for me. 

Here's what I'm trying to do... I have a couple scripts that I've written for the computers at my house, work and my friends that I've converted... Most of them want simple stupid stuff. So, I try to maintain things like ppa sources and various other configs - things I don't feel like doing across 15 machines. I'm hoping to kind of automate this process with a package. 

So, my folder hierarchy looks something like this: 

* support-pack_0.1
     - DEBIAN
     - etc/apt/sources.list.d/support.sources.list
     - etc/cron.daily/support.daily
     - usr/bin/several random scripts
     - usr/bin/share/applications/ .desktop
                     - pixmap/ icon
                     - keyrings/ gpg keys for the support.sources.list

I attached my control file, I have postinst and preinst scripts that run and those works fine. Everything builds just fine, and it will work MOST of the time... I run into a strange problem when I go to upgrade sometimes. The support.sources.list file I am trying to copy into the directory doesn't seem to make it. It just doesn't happen... Everything else will install just fine. 

I've tried using dh_make in this scenario and it will build the deb (after heavily commenting the rules file) but it doesn't seem to grab any of the files in /etc. I'm wondering if I am missing some syntax in the control file around the depends and replaces fields.

I'm somewhat new to this, I've read everything I can - if there is some guide out there that may be helpful please send it this way... I'm kinda stumbling through this... 

Any help is appreciated... thanks...

---

