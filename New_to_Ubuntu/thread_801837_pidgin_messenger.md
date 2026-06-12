---
title: "pidgin messenger"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by jacklsw2008 on 2008-05-20
does pidgin messenger has buzz/nudge? i can't seem to find this feature in pidgin but kopete has it.

---

### Post by iaculallad on 2008-05-20
Here's how you could enable it with pidgin:

On the Terminal, input these commands.

**wget [http://www.overinter.net/deb/pidgin-yahoobuzz_1.0-1_i386.deb](http://www.overinter.net/deb/pidgin-yahoobuzz_1.0-1_i386.deb)**

**sudo dpkg -i pidgin-yahoobuzz_1.0-1_i386.deb**

Start Pidgin and open the Plugins window (Tools->Plugins) and you will see a plugin called "Buzz support for Yahoo".

---

### Post by jacklsw2008 on 2008-05-21
somehow i got some errors installing it. can you solve for me? 

Selecting previously deselected package pidgin-yahoobuzz.
(Reading database ... 107161 files and directories currently installed.)
Unpacking pidgin-yahoobuzz (from pidgin-yahoobuzz_1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin-yahoobuzz:
 pidgin-yahoobuzz depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
dpkg: error processing pidgin-yahoobuzz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin-yahoobuzz

---

### Post by sdennie on 2008-05-21
I would try:

```

sudo apt-get install -f

```

That might clear up your installation problems.

---

### Post by Maestro23 on 2008-05-21
Also can go into Synaptic and search "pidgin".  Will find all kinds of plugins/add-ons for it.

---

### Post by iaculallad on 2008-05-21
> **vor said:**
> I would try:

```

sudo apt-get install -f

```

That might clear up your installation problems.

Second to this: sudo apt-get install -f will fix it for you.

---

### Post by jacklsw2008 on 2008-05-21
> **jacklsw2008 said:**
> somehow i got some errors installing it. can you solve for me? 

Selecting previously deselected package pidgin-yahoobuzz.
(Reading database ... 107161 files and directories currently installed.)
Unpacking pidgin-yahoobuzz (from pidgin-yahoobuzz_1.0-1_i386.deb) ...
dpkg: dependency problems prevent configuration of pidgin-yahoobuzz:
 pidgin-yahoobuzz depends on libglib1.2 (>= 1.2.0); however:
 ** Package libglib1.2 is not installed**.
dpkg: error processing pidgin-yahoobuzz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin-yahoobuzz

somehow i cant install the plugin even though i got the libglib1.2 from synaptic

---

### Post by iaculallad on 2008-05-21
Try this to install the dependecy file:
**sudo apt-get install libgdk-pixbuf2 libglib1.2 libgtk1.2 libssl0.9.6**

---

### Post by jacklsw2008 on 2008-05-21
Package libglib1.2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libglib1.2ldbl
E: Package libglib1.2 has no installation candidate

this error msg comes out. i think the plugin is old version already?

---

### Post by iaculallad on 2008-05-21
Try uninstalling pidgin then re-install it again (that could do the trick on missing dependency):

sudo apt-get remove pidgin

Afterwards, re-issue the command to install the buzz addon for your pidgin.

---

### Post by jacklsw2008 on 2008-05-21
no use. the synaptic stil won't install the plug-in.

---

### Post by iaculallad on 2008-05-21
> **jacklsw2008 said:**
> no use. the synaptic stil won't install the plug-in.

If it's the buzz plugin you're saying. Considering you have successfully installed Pidgin: Try using the post I posted 3 hrs ago:

 	

Here's how you could enable it with pidgin:

On the Terminal, input these commands.

wget [http://www.overinter.net/deb/pidgin-...1.0-1_i386.deb](http://www.overinter.net/deb/pidgin-...1.0-1_i386.deb)

sudo dpkg -i pidgin-yahoobuzz_1.0-1_i386.deb

Start Pidgin and open the Plugins window (Tools->Plugins) and you will see a plugin called "Buzz support for Yahoo".

---

### Post by jacklsw2008 on 2008-05-21
hmm do i have to install the plugin package after i remove pidgin then only i reinstall pidgin?

---

### Post by jacklsw2008 on 2008-05-21
i think libglib1.2 is not included in hardy heron

Edit: nevermind. i figured out that to buzz a contact i need to type '/buzz' in pidgin. so no plugins whatsoever. thanks for help anyway :) but it's kinda troublesome to type out rather than click a button :)

---

### Post by sdennie on 2008-05-21
Wow, if something is depending on glib 1.2, it's probably old, outdated and no longer maintained.  I wouldn't bother to even try to install it but instead find something similar that is not so antiquated.

---

