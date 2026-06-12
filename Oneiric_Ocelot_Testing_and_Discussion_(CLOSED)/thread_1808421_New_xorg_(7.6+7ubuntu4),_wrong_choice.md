---
title: "New xorg (7.6+7ubuntu4), wrong choice"
date: 2011-07-20
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-20
New xorg (7.6+7ubuntu4) package forces you to install xdiagnose.
Actually X11-common now depends on it (instead of recommending it).

> * debian/control:  Add Depends on xdiagnose, to ensure it always gets
    installed.

This may be debian policy, but now I have less freedom of choice.
I do not need xdiagnose, I do not even use apport.

But because I now have to install xdiagnose, I now have apport. And apport pulls in these:
python-apport
python-httplib2
python-keyring
python-launchpadlib
python-lazr.rsstfulclient
python-lazr.uri
python-oauth
python-pkg-resources
python-problem-report
python-simplejson
python-wadllib
python-zope.interface

None of which I need.

---

### Post by dino99 on 2011-07-20
dpkg dont deal with dependencies, so you might remove those unneeded packages.

---

### Post by xebian on 2011-07-20
> **dino99 said:**
> dpkg dont deal with dependencies, so you might remove those unneeded packages.

Try removing it (and x11-common) will trash your system.

---

### Post by xebian on 2011-07-20
> **Harry33 said:**
> New xorg (7.6+7ubuntu4) package forces you to install xdiagnose.
Actually X11-common now depends on it (instead of recommending it).



This may be debian policy, but now I have less freedom of choice.
I do not need xdiagnose, I do not even use apport.

But because I now have to install xdiagnose, I now have apport. And apport pulls in these:
python-apport
python-httplib2
python-keyring
python-launchpadlib
python-lazr.rsstfulclient
python-lazr.uri
python-oauth
python-pkg-resources
python-problem-report
python-simplejson
python-wadllib
python-zope.interface

None of which I need.

Exactly.  Why???  I can't remove them as they take down so many kde* stuff trashing system.

:confused:

---

### Post by Harry33 on 2011-07-20
> **dino99 said:**
> dpkg dont deal with dependencies, so you might remove those unneeded packages.

I think dpkg may force remove them, but then it leaves broken packages.
Just like installing with dpkg packages without all the dependencies.

The issue here is that x11-common should only recommend xdiagnose, not depend on it.
Like it was before.

---

### Post by seeker5528 on 2011-07-20
> **Harry33 said:**
> This may be debian policy, but now I have less freedom of choice.
I do not need xdiagnose, I do not even use apport.

That package doesn't even seem to exist in Debian, so it's not Debian policy.

Since apport and xdiagnose are tools to help you help the developers by collecting and supplying better/more complete information when you submit a bug report, which may be automatically triggered by something crashing or a package failing to install, I don't see it being a big deal that these things would be considered dependencies.

If you are really *that* opposed to it being installed you could use equivs to create a dummy package, it doesn't look like it should be all that hard to create a dummy of the xdiagnose package.

[http://manpages.ubuntu.com/manpages/natty/man1/equivs-build.1.html](http://manpages.ubuntu.com/manpages/natty/man1/equivs-build.1.html)
[http://manpages.ubuntu.com/manpages/natty/man1/equivs-control.1.html](http://manpages.ubuntu.com/manpages/natty/man1/equivs-control.1.html)

Later, Seeker

---

### Post by Quackers on 2011-07-20
xdiagnose appeared in my gnome-shell Applications screen a couple of weeks ago, I would estimate. It has a blurry icon in the menu. Not a clue why it appeared.

---

### Post by Harry33 on 2011-07-20
> **seeker5528 said:**
> 
...
Since apport and xdiagnose are tools to help you help the developers by collecting and supplying better/more complete information when you submit a bug report, which may be automatically triggered by something crashing or a package failing to install, I don't see it being a big deal that these things would be considered dependencies.
...
Later, Seeker

I understand and accept your point.
However, that is not the issue.
My problem is that I do not have a choice whether to install or not the package xdiagnose.

---

### Post by mc4man on 2011-07-20
> My problem is that I do not have a choice whether to install or not the package xdiagnose.
You could file a bug on, maybe they'll set back, see no reason to.
Don't really see why you or anyone thinks they should have a choice here.
(and you do have the choice to adjust for yourself in several ways

---

### Post by seeker5528 on 2011-07-20
According to '/usr/share/doc/xdiagnose/README'... > This is a failsafe-mode for Xorg, that will be called when Xorg is
unable to start due to misconfiguration. ...so I doubt that it's status as a depencency of x11-common will be changed.

EDIT: On a barely related note... I just had a flash back of all those people using Windows that "deleted something they didn't use" who then had to bring their PCs to me to fix. 

Later, Seeker

---

### Post by Harry33 on 2011-07-21
> **mc4man said:**
> You could file a bug on, maybe they'll set back, see no reason to.
Don't really see why you or anyone thinks they should have a choice here.
(and you do have the choice to adjust for yourself in several ways

I don't think this is a bug, it is intentional.
We have less and less choice, year after year.

---

### Post by dino99 on 2011-07-21
> **Harry33 said:**
> I don't think this is a bug, it is intentional.
We have less and less choice, year after year.

Sure, and more and more noobs users in our expanding community, thanks ubuntu :)
But on the other hand, a huge part of bugs reported are due to unskilled tweaking giving false positive bugs, slowing down the real devs work.

So they have learn the meaning and chosen to iron the system. Thats the price of success :(

---

### Post by jbicha on 2011-07-21
Harry33, why do you hate apport so much? Do you prefer other people to report your bugs for you?

---

### Post by Harry33 on 2011-07-21
> **jbicha said:**
> Harry33, why do you hate apport so much? Do you prefer other people to report your bugs for you?

First of all. I never said I hate apport.
Secondly, I do not use apport nor any other automated bug reporting system.
I debug the bugs I find myself, manually.
Also, I report bugs manually too.

Up to date, I have reported some hundreds of bugs to Launchpad.
I have also helped a number of users to solve their problems in this very Forum.
And yet, all that without apport.

So it is just that I do not need apport.
I also prefer to use a minimalistic setup.
But that is just me. And I prefer to decide that myself.

---

### Post by Harry33 on 2011-07-21
> **dino99 said:**
> Sure, and more and more noobs users in our expanding community, thanks ubuntu :)
But on the other hand, a huge part of bugs reported are due to unskilled tweaking giving false positive bugs, slowing down the real devs work.

So they have learn the meaning and chosen to iron the system. Thats the price of success :(

You are right about that.

---

### Post by jbicha on 2011-07-21
Apport significantly improves bug reports by automatically including all the relevant logs (that it's been programmed for). By the way, what is your launchpad username?

If you're tired of the apport bug popups, it is very easy to disable apport: 
sudo nano /etc/default/apport... and change enabled from "1" to "0". It is disabled by default for released versions of Ubuntu.

---

### Post by xebian on 2011-07-21
But what good does xdiagnose do if X is not running/behaving properly?

A GUI tool to diagnose  X (aka GUI) problems?

---

### Post by Harry33 on 2011-07-21
> **jbicha said:**
> Apport significantly improves bug reports by automatically including all the relevant logs (that it's been programmed for). By the way, what is your launchpad username?

If you're tired of the apport bug popups, it is very easy to disable apport: 
sudo nano /etc/default/apport... and change enabled from "1" to "0". It is disabled by default for released versions of Ubuntu.

Like I said, I prefer to do this my way.

---

### Post by seeker5528 on 2011-07-21
> **xebian said:**
> But what good does xdiagnose do if X is not running/behaving properly?

A GUI tool to diagnose  X (aka GUI) problems?

Because it's part of the failsafe, that gives you choices on how to proceed if your login failes.

I thought the blurb from the README that I posted [earlier in the thread](http://ubuntuforums.org/showpost.php?p=11069152&postcount=10) was a better description than the package description.

> This is a failsafe-mode for Xorg, that will be called when Xorg is
unable to start due to misconfiguration.

Seems to be an update to the bullet-proof-x stuff implemented in a less GDM/Gnome specific way than whatever it is replacing. 

If the current configuration doesn't work, it will try to fall back to something that does work, then give you some options on how to proceed, at least that is what it sounds like to me.

Later, Seeker

---

### Post by jbicha on 2011-07-21
Harry33, if you don't use ubuntu-desktop this has been fixed now. Give it a couple hours to build and get published but now ubuntu-desktop depends on xdiagnose instead of having xorg depend on it.

---

### Post by Harry33 on 2011-07-22
> **jbicha said:**
> Harry33, if you don't use ubuntu-desktop this has been fixed now. Give it a couple hours to build and get published but now ubuntu-desktop depends on xdiagnose instead of having xorg depend on it.

Right, now the choice of freedom is back.
I can now update xorg.
However, the latest version 7.6+7ubuntu5 is exactly the same as 7.6+7ubuntu3.
Anyways, issue solved.

---

### Post by mc4man on 2011-07-22
> the choice of freedom is back.
In a roundabout way - same difference I guess

---

### Post by Harry33 on 2011-07-22
> **mc4man said:**
> In a roundabout way - same difference I guess

Before the latest x11-common update, you could not uninstall apport nor xdiagnose.
Now you can uninstall both of those applications.
Uninstalling ubuntu-meta (ubuntu-desktop, ubuntu-standard, ubuntu-minimal) has always been possible.

---

### Post by xebian on 2011-07-22
> **seeker5528 said:**
> Because it's part of the failsafe, that gives you choices on how to proceed if your login failes.

I thought the blurb from the README that I posted [earlier in the thread](http://ubuntuforums.org/showpost.php?p=11069152&postcount=10) was a better description than the package description.



Seems to be an update to the bullet-proof-x stuff implemented in a less GDM/Gnome specific way than whatever it is replacing. 

If the current configuration doesn't work, it will try to fall back to something that does work, then give you some options on how to proceed, at least that is what it sounds like to me.

Later, Seeker

xdiagnose is an application that requires X to be running to run. So how am I going to use xdiagnose to diagnose an X that doesn't want to run?

---

### Post by seeker5528 on 2011-07-22
> **xebian said:**
> xdiagnose is an application that requires X to be running to run. So how am I going to use xdiagnose to diagnose an X that doesn't want to run?

Since we have some information on how bullet proof X worked in the past...

[http://arstechnica.com/open-source/news/2007/08/ubuntu-xorg-maintainer-demonstrates-bulletproof-x.ars](http://arstechnica.com/open-source/news/2007/08/ubuntu-xorg-maintainer-demonstrates-bulletproof-x.ars)

And the description in the README that identifies it as a fallback.....

file:///usr/share/doc/xdiagnose/README   <<<- copy and paste in the address bar of a new tab

I think we could probably say it would less often be something you would use and more often an automated response that falls back to something that theoretically should work so that you can be presented with some options

[img]http://home.comcast.net/~seeker5528/Screenshot-Xdiagnose.png[/img]

Those are the options you get when you run it, which may or may not be the same options you get when there is an automated response to a problem.

If X won't even run with the VESA or VGA driver and minimalistic, low color, low resolution X session, then you have bigger problems which require a different kind of response. Not working for extreme problems, doesn't make it less useful in the significant percentage of cases where the fallback works.

What it can or can't/will or won't do relative to the previous bullet proof X thing is a whole other question. The package description would seem to imply that it is not intended to be the exact equivalent to the previous thing and things Xorg are supposed to be handled a little more automatically now than in the days where you always had an xorg.conf file. The only configuration in my xorg.conf is ```
 Section "InputClass"
    Identifier          "Keyboard Defaults"
    MatchIsKeyboard     "yes"
    Option              "XkbOptions" "terminate:ctrl_alt_bksp"
EndSection
```


Later, Seeker

---

### Post by Harry33 on 2011-07-22
New version of xorg (7.6+7ubuntu6) removes xdiagnose from recommends too.

> xorg (1:7.6+7ubuntu6) oneiric; urgency=low

  * debian/control: Remove Recommends on xdiagnose as well; apparently it
    still causes gtk3 to be included for kubuntu.  Derivative distros will
    need to opt-in with their seeds if they wish to have X diagnostics
    included, or users will have to manually install xdiagnose themselves.

---

