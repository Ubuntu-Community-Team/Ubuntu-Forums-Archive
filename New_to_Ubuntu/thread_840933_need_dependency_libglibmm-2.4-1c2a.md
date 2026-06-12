---
title: "need dependency? libglibmm-2.4-1c2a"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by raker t on 2008-06-25
I have no internet connection on my Ubuntu box, that's a project in itself. So i tried getting a debian package, and a ubuntu package, burning them to a CD, and using synaptic package manager to install them from the CD. Also tried using add/remove programs. In both cases, they tell me they found the CD, but there were no packages on it. Whatever, so I used a flashdrive to park the packages in a directory, then double clicked on them. It looked like it started to install, but there was an error message about dependency not satisfiable: libglibmm-2.4-1c2a

Is this what's called a dependency? Where do I get it? My searches in Google and archives have not turned up what I think I need. Thanks for any help.

I have Fiesty 7.04. The only package that would start to work was architecture i386.

---

### Post by RomeReactor on 2008-06-25
Hi. What are you trying to install? You can search for Ubuntu-specific packages [here]("http://packages.ubuntu.com/") (and [here]("http://mirrors.xmission.com/ubuntu/pool/main/g/glibmm2.4/libglibmm-2.4-1c2a_2.13.3-0ubuntu1_i386.deb") is the package you need).

---

### Post by raker t on 2008-06-26
I'm trying to install Inkscape.

I already have it in a debian package, and a ubuntu package.

Both produce the same error message, maybe slightly different number.

Is libglibmm-2.4-1c2a a depandency?

If so, where can I get it?

---

### Post by drs305 on 2008-06-26
> **raker t said:**
> I'm trying to install Inkscape.

I already have it in a debian package, and a ubuntu package.

Both produce the same error message, maybe slightly different number.

Is libglibmm-2.4-1c2a a depandency?

If so, where can I get it?

ADDED: Sorry, I'm running hardy and didn't notice you have fiesty. I don't know if the packages/libraries are the same.

According to synaptic, it is a dependency. When you have access to synaptic, you learn this by highlighting inkscape and then looking at Properties, Dependencies. 

Also according to synaptic, it's in the repositories so you can just download it from synaptic.

But here's the best part: if you can get an internet connection, inkscape is in synaptic, so just mark that for installation and it will take care of everything for you.

---

