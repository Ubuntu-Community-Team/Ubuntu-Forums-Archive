---
title: "Three Xubuntu Questions/Problems"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by UnsafeData on 2008-06-04
EDIT:

I give up. I spent too much time with this and I'm switching over to Debian which I believe is a good option for me since it still supports PowerPC.

---

### Post by myusername on 2008-06-04
1. from what i gather your running on a powerpc. im pretty sure you cant upgrade.

2. open synaptic (system/administration/synaptic) and search for pidgen

3. in synaptic just install ubuntu restricted extras

---

### Post by Maestro23 on 2008-06-04
I believe the text editor installed with Xubuntu is **mousepad**.

---

### Post by UnsafeData on 2008-06-04
When I search for pidgin in synaptic.. nothing comes up.

---

### Post by myusername on 2008-06-04
search for messenger

---

### Post by UnsafeData on 2008-06-04
> **myusername said:**
> search for messenger


Only Gaim (which I have) and Kopete comes up.

---

### Post by myusername on 2008-06-04
do you have all the repos enabled?

---

### Post by myusername on 2008-06-04
also...try to refresh your sources

---

### Post by UnsafeData on 2008-06-04
> **myusername said:**
> do you have all the repos enabled?

Not sure.

How do I check? I am pretty new to this. I've had Ubuntu before but I wasn't actually familiar with stuff like this.

---

### Post by myusername on 2008-06-04
in synaptic go to settings and then to repositories and check all of them that say universe and multiverse.

be sure to refresh your sources after doing this

---

### Post by UnsafeData on 2008-06-04
> **myusername said:**
> in synaptic go to settings and then to repositories and check all of them that say universe and multiverse.

be sure to refresh your sources after doing this

They're all checked.

---

### Post by myusername on 2008-06-04
check all of them then except experimental repos

---

### Post by UnsafeData on 2008-06-04
I did.

---

### Post by myusername on 2008-06-04
well im sorry...i cant help you. just try googling "how to install pidgen on ubuntu"

---

### Post by UnsafeData on 2008-06-04
That's okay. I'll wait and see if someone else replies. I'm doing software updates right now since there's 142 of them.

---

### Post by UnsafeData on 2008-06-04
I want to get gnash to watch YouTube videos.. sadly I can't find ANYTHING in Google.. so I really need help with this.

---

### Post by sayakb on 2008-06-04
For flash:
```
sudo apt-get install flashplugin-nonfree
```I'm not sure whether you have this in Dapper or not.

As for pidgin, try this: [http://drsjlazar.blogspot.com/2007/05/pidgin-for-dapper.html](http://drsjlazar.blogspot.com/2007/05/pidgin-for-dapper.html)

Why don't you backup your data and go for a clean install. Even if you somehow manage to upgrade, there's very less chance that any upgrade would work out perfectly.

---

### Post by Paqman on 2008-06-04
I'd be surprised if Pidgin was in the Dapper repos, tbh. You're probably stuck with Gaim.

You could try compiling Pidgin from source, but you're likely to have a hell of a time with the dependencies.

You may have an upgrade path available to take your system from Dapper straight to Hardy. Open up Update Manager and see if it's advertising the new version as being available.

---

### Post by UnsafeData on 2008-06-04
> **LinuxIsInnovation said:**
> For flash:
```
sudo apt-get install flashplugin-nonfree
```I'm not sure whether you have this in Dapper or not.

As for pidgin, try this: [http://drsjlazar.blogspot.com/2007/05/pidgin-for-dapper.html](http://drsjlazar.blogspot.com/2007/05/pidgin-for-dapper.html)

Why don't you backup your data and go for a clean install. Even if you somehow manage to upgrade, there's very less chance that any upgrade would work out perfectly.






E: Couldn't find package flashplugin-nonfree

---

### Post by Paqman on 2008-06-04
What about the package xubuntu-restricted-extras? That would (on a more recent version) have Flash as a dependency. You install it, you should get the correct Flash package for Dapper.

---

### Post by UnsafeData on 2008-06-04
> **Paqman said:**
> What about the package xubuntu-restricted-extras? That would (on a more recent version) have Flash as a dependency. You install it, you should get the correct Flash package for Dapper.

john@john-desktop:~$ sudo apt-get install xubuntu-restricted-extras
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xubuntu-restricted-extras
john@john-desktop:~$

---

### Post by jw5801 on 2008-06-04
> **UnsafeData said:**
> E: Couldn't find package flashplugin-nonfree

You're probably going to be struggling until you upgrade to at least Gutsy. I think Pidgin replaced Gaim around then (they're one and the same, the project just changed it's name around then). flashplugin-nonfree is also available in Gutsy. I'd be thinking you'd want to install straight to Hardy. Someone correct me if I'm wrong but I think there should be an upgrade path direct from Dapper to Hardy? Otherwise you'll have to go through Edgy, Feisty and Gutsy as well. So you should be able to upgrade without any data loss. Be prepared to do some trouble shooting after the upgrade though, major upgrades like this never go as smoothly as we'd like. Don't forget to back up anything important before you start.

I believe major upgrades can be done through the Add/Remove app. It should have an option in there to complete the major upgrade. I generally do a fresh install (I have /home on a different partition so I don't lose any data or preferences over a fresh install) whenever a major version comes along.

---

### Post by mister_pink on 2008-06-04
You can't upgrade beyond edgy if you're using a powerpc I'm afraid. They dropped support for them in fiesty. Can't really help with any of your specific problem's though really! Sorry.

Looks like all the restricted-extras and flashplugin packages were added in edgy though.

---

### Post by jw5801 on 2008-06-04
> **mister_pink said:**
> You can't upgrade beyond edgy if you're using a powerpc I'm afraid. They dropped support for them in fiesty. Can't really help with any of your specific problem's though really! Sorry.

Looks like all the restricted-extras and flashplugin packages were added in edgy though.

Ah, I missed that. 6.06 is what is supported and recommended for powerpc. So you're already there, but probably won't be able to find much support unfortunately. Perhaps it's time to try a new distro? Debian & Fedora I know off the top of my head still have support for PowerPC. A quick look says that the recently released Fedora 9 has a PowerPC release.

That being said, looking at the Ubuntu Package search I can see lots and lots of packages for PowerPC under the Gutsy category. Nothing under Hardy though. So it is possible that there may be an upgrade path for you!

---

### Post by UnsafeData on 2008-06-04
how do i upgrade then? i remember there was an option when i was doing systme updates byut now i dont see it there anymore

---

### Post by jw5801 on 2008-06-04
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

That's the generic upgrade page. Should apply to you also.

---

### Post by UnsafeData on 2008-06-04
> **jw5801 said:**
> [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

That's the generic upgrade page. Should apply to you also.

Didn't let me. Restored to original state. :(


> Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

Is it because I'm PPC? I know PPC isn't oficially supported anymore.

---

### Post by avtolle on 2008-06-04
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ) UnsafeData, please read. There is some information for you here. Also, join us on the Apple Users Forum for additional support.
[http://ubuntuforums.org/showthread.php?t=427714](http://ubuntuforums.org/showthread.php?t=427714) will give you information as to where to download newer ppc versions of Ubuntu; for Xubuntu, you need to poke around its site for download information (as I recall, there is an Xubuntu 8.04 for ppc, as well as versions newer than 6.06 but older than 8.04).

---

### Post by doorknob60 on 2008-06-04
Meh, everyone here seems to assume he's either using Hardy/Gusty or using i386...sad tbh, read the posts! Pidgin isn't in Dapper's repositories, you can compile it from source if you want. You can probably get most/all of the dependencies with this command:
```
sudo apt-get build-dep gaim
```

If it needs more, use synaptic to search for the dependency it gave an error about (get the -dev package). I compiled pidgin before I knew about apt-get build-dep, and it wasn't too bad, so you should be fine. Also, Adobe doesn't have a flash plugin for PPC, so use something like Gnash. According to packages.ubuntu.com, it's not in Dapper's repositories, so compiling from source would be your option for Flash. I believe it supports Youtube now :)

---

### Post by avtolle on 2008-06-04
If he upgrades to >=7.10 he can get gnash from the repositories.  Yes, doorknob60, it was sad to see the posts, not reading where he stated he was on ppc. Thus, my post above, which I hope he sees and follows the links posted.

@UnsafeData, I'm running 8.04 Ubuntu on two G-4 Cubes, just to establish my *bona fides*. :-)

---

### Post by UnsafeData on 2008-06-04
> **doorknob60 said:**
> Meh, everyone here seems to assume he's either using Hardy/Gusty or using i386...sad tbh, read the posts! Pidgin isn't in Dapper's repositories, you can compile it from source if you want. You can probably get most/all of the dependencies with this command:
```
sudo apt-get build-dep gaim
```

If it needs more, use synaptic to search for the dependency it gave an error about (get the -dev package). I compiled pidgin before I knew about apt-get build-dep, and it wasn't too bad, so you should be fine. Also, Adobe doesn't have a flash plugin for PPC, so use something like Gnash. According to packages.ubuntu.com, it's not in Dapper's repositories, so compiling from source would be your option for Flash. I believe it supports Youtube now :)

how do i compile from source? i'd like to do flash first since i need YouTube., an 8GB hard drive isn't big enough to put music on so music videos are a good option once this is filled up.

---

### Post by avtolle on 2008-06-04
You're going to need to go the gnash site and d/l to compile. I did this on 6.06, IIRC, about a year ago, and it went well. After upgrading, then it was in the repositories, so I've not anything left here about any dependencies, etc. that you might run into. Again, this will be gnash, not Flash, just so you're clear. And, to be fair to you, you're likely to have some problems with YouTube with Gnash, even though it's much better than it was once (kudos to the developers of Gnash, who are tirelessly toiling to make it better).

---

### Post by UnsafeData on 2008-06-04
> **avtolle said:**
> You're going to need to go the gnash site and d/l to compile. I did this on 6.06, IIRC, about a year ago, and it went well. After upgrading, then it was in the repositories, so I've not anything left here about any dependencies, etc. that you might run into. Again, this will be gnash, not Flash, just so you're clear. And, to be fair to you, you're likely to have some problems with YouTube with Gnash, even though it's much better than it was once (kudos to the developers of Gnash, who are tirelessly toiling to make it better).
> 

Development Version

The latest development sources are available via anonymous CVS (enter return for the password):

export CVS_RSH="ssh"
cvs -z3 -d:pserver:anonymous@cvs.sv.gnu.org:/sources/gnash
co gnash

You can also browse the repository on the web.

How do I get the source?

---

### Post by avtolle on 2008-06-04
Try here: [http://www.gnashdev.org/](http://www.gnashdev.org/)

Edit: More precisely, [http://www.gnashdev.org/?q=node/27](http://www.gnashdev.org/?q=node/27)

---

### Post by UnsafeData on 2008-06-04
[ftp://mirrors.kernel.org/gnu/gnash/0.8.2](ftp://mirrors.kernel.org/gnu/gnash/0.8.2)

Here?

---

### Post by avtolle on 2008-06-04
> **UnsafeData said:**
> [ftp://mirrors.kernel.org/gnu/gnash/0.8.2](ftp://mirrors.kernel.org/gnu/gnash/0.8.2)

Here?
That will work, as well as my last link (BTW, if you're brave, you could compile the rc for 0.8.3 and try it out from the official gnash development site. :-) )

---

### Post by avtolle on 2008-06-04
Need to add one more thought; since you're on Dapper, it is possible you might not have all the current dependencies to compile the newer version(s). Hopefully, installing build-essential (if you've not already done so) from the Dapper repositories will be sufficient.

---

### Post by UnsafeData on 2008-06-04
> **avtolle said:**
> That will work, as well as my last link (BTW, if you're brave, you could compile the rc for 0.8.3 and try it out from the official gnash development site. :-) )


I'm gonna need help compiling since I have no idea how to do it.

EDIT: I'm getting the build-essential. :P

---

### Post by avtolle on 2008-06-04
> **UnsafeData said:**
> I'm gonna need help compiling since I have no idea how to do it.

EDIT: I'm getting the build-essential. :P
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) a little something to help you. :-) Not abandoning you, need to leave for the evening. Good luck, post your questions, and I'm sure someone will be able to give you a hand.

---

### Post by UnsafeData on 2008-06-04
Ahh the dependencies. I'm getting them all, I'll report back if i have any problems,. :)

---

### Post by UnsafeData on 2008-06-04
I keep getting these:


        WARNING: You need to have the Ming development and utilities packages
                 installed to run most of the tests in Gnash testsuite.
                 Install it from [http://ming.sourceforge.net](http://ming.sourceforge.net)
                 or .deb users: apt-get install libming-dev
        WARNING: You need to have the MTASC compiler packages installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://mtasc.org](http://mtasc.org)
                 or .deb users: apt-get install mtasc
        WARNING: You need to have the 'swfmill' tool installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://swfmill.org/](http://swfmill.org/)
        WARNING: You need to have 'swfc' from SWFTools installed
                 to run some of the tests in Gnash testsuite.
                 You can install it from [http://www.swftools.org/](http://www.swftools.org/)



I can't get mtasc because I can't find one for Dapper. :(

I need help getting all these packages.

---

### Post by jw5801 on 2008-06-04
That's ok, you shouldn't need all of those if you can't find them. They're part of the gnash test suite in case you want to test the build you compiled. It's not strictly necessary.

---

### Post by UnsafeData on 2008-06-04
> **jw5801 said:**
> That's ok, you shouldn't need all of those if you can't find them. They're part of the gnash test suite in case you want to test the build you compiled. It's not strictly necessary.

[http://paste.ubuntu.com/17055/](http://paste.ubuntu.com/17055/)

That's what I get.

---

### Post by jw5801 on 2008-06-04
> **UnsafeData said:**
> [http://paste.ubuntu.com/17055/](http://paste.ubuntu.com/17055/)

That's what I get.

That's a sharp and sudden stop. Is there a configure script? Can you post the output from that?

Otherwise try:
```
sudo ldconfig
```
Then give it another shot.

---

### Post by UnsafeData on 2008-06-05
> **jw5801 said:**
> That's a sharp and sudden stop. Is there a configure script? Can you post the output from that?

Otherwise try:
```
sudo ldconfig
```
Then give it another shot.

Output is here:

[http://paste.ubuntu.com/17106/](http://paste.ubuntu.com/17106/)

---

### Post by jw5801 on 2008-06-05
> **UnsafeData said:**
> Output is here:

[http://paste.ubuntu.com/17106/](http://paste.ubuntu.com/17106/)

ldconfig won't output anything, it just might help let the linker work properly which is where make died.

What was the output from the configure script? ie. did you run './configure' and what happened when you did?

---

### Post by UnsafeData on 2008-06-05
> **jw5801 said:**
> ldconfig won't output anything, it just might help let the linker work properly which is where make died.

What was the output from the configure script? ie. did you run './configure' and what happened when you did?

That's the output of the configure script. Sorry I should've said which output since you said give an output or do "sudo ldconfig".

That's the output of after I did "sudo ldconfig" and then did "./configure".

---

### Post by mapes12 on 2008-06-05
> Is there a way to upgrade WITHOUT losing all my stuff?

I had the same problem. Move /home to another partition. This is how I did it:

[http://ubuntuforums.org/showthread.php?t=811842](http://ubuntuforums.org/showthread.php?t=811842)

Then do a fresh install on the partition where your filesystem is located.

With the media issues take a look here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by UnsafeData on 2008-06-05
Note: I compiled Pidgin sucessfully. Works fine.

Just need gnash and I'm good.

---

### Post by UnsafeData on 2008-06-05
I've been told in the IRC to look at this:

[https://savannah.gnu.org/bugs/?func=detailitem&item_id=22753](https://savannah.gnu.org/bugs/?func=detailitem&item_id=22753)

And that it appears to be a problem with the building tools on ppc and that there's not much to be done about it.

:(

---

### Post by jw5801 on 2008-06-05
> **UnsafeData said:**
> I've been told in the IRC to look at this:

[https://savannah.gnu.org/bugs/?func=detailitem&item_id=22753](https://savannah.gnu.org/bugs/?func=detailitem&item_id=22753)

And that it appears to be a problem with the building tools on ppc and that there's not much to be done about it.

:(

Yeah, it looks pretty nasty. Normally when make dies you get a reasonable output... that's just gcc piking for no apparent reason. :(

You could try upgrading to Edgy, Feisty or Gutsy using the community supported install CDs that were mentioned earlier in the thread. I'd follow the separate /home partition approach (I have for every other upgrade), it makes life much easier. I'd follow Aysiu's guide to set up a /home partition. It's one of the best around.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

EDIT: Apologies for missing the ./configure output, there were lots of blank lines so I thought it was finished!

Did you try:
```
sudo apt-get install libagg-dev
```

Apparently your AGG version is too old. So we may need to compile a newer version of that as well (if that turns out to be feasible). Not bad if that's the only dependency you need a newer version of. If it has newer dependencies as well though, this could quickly go downhill.

---

### Post by UnsafeData on 2008-06-05
> john@john-desktop:~/Desktop/gnash-0.8.2$ sudo apt-get install libagg-dev
Reading package lists... Done
Building dependency tree... Done
libagg-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
john@john-desktop:~/Desktop/gnash-0.8.2$

.

---

### Post by jw5801 on 2008-06-05
What version does:
```
apt-cache show libagg-dev
```
show?

If it's 2.4 we can try compiling it from somewhere else and see if that gets us anywhere. Otherwise it's not looking promising.

---

### Post by UnsafeData on 2008-06-05
john@john-desktop:~/Desktop/pitfdll-0.9.1.1$ apt-cache show libagg-dev
Package: libagg-dev
Priority: optional
Section: universe/libdevel
Installed-Size: 2532
Maintainer: Debian OpenOffice Team <debian-openoffice@lists.debian.org>
Architecture: powerpc
Source: agg
Version: 2.3-2
Filename: pool/universe/a/agg/libagg-dev_2.3-2_powerpc.deb
Size: 399432
MD5sum: a006e34ef9d524fdfd413ab4a34b6ca3
Description: The AntiGrain Geometry graphical toolkit (development files)
 Anti-Grain Geometry (AGG) is a general purpose graphical toolkit written
 completely in standard and platform independent C++. It can be used in many
 areas of computer programming where high quality 2D graphics is an essential
 part of the project.
 .
 This package contains the development files for building applications using
 agg.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

john@john-desktop:~/Desktop/pitfdll-0.9.1.1$

---

### Post by UnsafeData on 2008-06-05
Ugh, I'm just going to install Debian on this. I'm having too many problems with Xubuntu on an unsupported system.

---

### Post by jw5801 on 2008-06-05
> **UnsafeData said:**
> Ugh, I'm just going to install Debian on this. I'm having too many problems with Xubuntu on an unsupported system.

Yep, that would be my approach. Or you could try the new Fedora. I'd definitely look at going the separate /home route before you trash this install though. It'll make configuration so much easier.

---

