---
title: "Do you like KDE?"
date: 2009-12-11
forum: Recurring Discussions
---

### Post by cguy on 2009-12-11
Then you MUST try out openSUSE! :D
That distro really puts Kubuntu to shame in terms of speed.

On the downside, it has problems Ubuntu (minus Karmic :P) has fixed a long time ago and its package management is HORRIBLE. Really horrible!

---

### Post by jdrodrig on 2009-12-11
I think this is better suited for The Community Cafe...

---

### Post by Jazzy_Jeff on 2009-12-11
I personally like the simplicity of Gnome. KDE is ok, just not for me.

---

### Post by ElSlunko on 2009-12-11
Yeah I gotta admit OpenSuse has a very good KDE distro. I'm on it right now and though I miss the simplicity of Gnome, this KDE distro has given me nearly zero problems so I haven't felt the desire to switch back, yet. One thing that opensuse doesn't have is the huge Ubuntu community.

---

### Post by HappyFeet on 2009-12-12
No!

---

### Post by Wiebelhaus on 2009-12-12
> **jdrodrig said:**
> I think this is better suited for The Community Cafe...

And like a 3 year backward time travel.

---

### Post by Tamlynmac on 2009-12-12
> jdrodrig
I think this is better suited for The Community Cafe... 	

+1

The Community Cafe / Recurring Discussions.

Last I checked this is the Ubuntu Forums.

---

### Post by DeusExM1 on 2009-12-12
i would like KDE but their menus are horrible. I dont really like gnome too much i think its too simple, but KDE is even worse imo. The menus just take way too long to navigate. Really pisses me off.

---

### Post by Sef on 2009-12-12
> I think this is better suited for The Community Cafe...


Close.  Recurring Discussions as this has been covered before.

---

### Post by kevCast on 2009-12-12
OpenSUSE, the new Arch Linux?

---

### Post by ~sHyLoCk~ on 2009-12-12
> **kevCast said:**
> OpenSUSE, the new Arch Linux?

I fell off my chair :lolflag:

---

### Post by SuperSonic4 on 2009-12-12
*Points to sig*

Also yast is *horrible*. Long live Pacman!


*waits for hoppipolla to see this thread :p*

---

### Post by ~sHyLoCk~ on 2009-12-12
Hi cguy, I hope you don't mind me replying to your PM here, I thought of making it public since others may also have some opinions to share. So here goes:


> That tray applet didn't search for new versions of the installed software, but only for patches. Why?

I'm not sure which softwares you are talking about but often software upgrades,i.e. version upgrades are just simple patches which help fix bugs,etc. Not necessarily you have to re-download the entire source code/ binary package. Also, openSUSE tries to provide you with only  stable packages. you will notice this that the Firefox version doesn't get upgraded unless you explicitly choose the new version in YaST. You will find multiple versions of a single package, this is the reason. 

> One day a "dummy package for update applet" appeared as a patch; it was not installable and it broke the applet until restart.
It disappeared after I changed the engine of the update applet.


Never happened with me. One TIP: Keep the update applet switched off. Why should you let it waste your bandwidth every hour or so to check for patches? The patches are rare and you should check for them manually when you want using ```
zypper pchk
```
Btw, I think you don't know or are misinformed: That maybe an update applet as it claims but it actually is a patch check applet, it only checks for necessary security patches at regular intervals and not software upgrades. This is no rolling release distro. *cough .arch..cough* :P

> I added two official KDE repos. Only after clicking "switch system packages to the version in this repository" did YaST update the DE.
Why doesn't "Right click > All items in this list > Update if a newer version is available" do the same thing?

1st of all there is only one official KDE repo, you must have added the KDE43 repo and then switched packages.
[http://en.opensuse.org/KDE/Repositories]("http://en.opensuse.org/KDE/Repositories")
Which repos did you add?
Btw, this switching of packages isn't really officially supported or encouraged. If something is messed up, it is your own fault, not openSUSE's. You can't use ppa repos and blame ubuntu for any failure. Similar situation here. KDE4.3.1 that comes with openSUSE is a perfectly stable polished desktop release.

> Once updated to KDE 4.3.4 I see that there is a newer version of Network Manager in the default repo. I couldn't update it unless I selected "Switch system packages to the version in this repository" which would have downgraded my KDE.

Yes you can, just goto that repo, download the rpm and necessary dependencies and install them. Again, this is not officially supported.

> To conclude, one day later I was installing Xubuntu. :-/

That's the bottomline, you should have spend more time with it. May I suggest another try sometime when you have time?

Regards

---

### Post by ~sHyLoCk~ on 2009-12-12
> **SuperSonic4 said:**
> 
Also yast is *horrible*. Long live Pacman!


Lame comparison. You should rather compare shaman with Yast. YAST owns here. And zypper with Pacman, pacman pawns here. :lolflag:

---

### Post by SuperSonic4 on 2009-12-12
> **~sHyLoCk~ said:**
> Lame comparison. You should rather compare shaman with Yast. YAST owns here. And zypper with Pacman, pacman pawns here. :lolflag:

It's a fair cop. I don't mind shaman that must though

---

### Post by cguy on 2009-12-12
> **~sHyLoCk~ said:**
> 
1st of all there is only one official KDE repo, you must have added the KDE43 repo and then switched packages.
[http://en.opensuse.org/KDE/Repositories]("http://en.opensuse.org/KDE/Repositories")
Which repos did you add?
**The stable KDE repo & the backports repo.**

Updating KDE may not be officially supported, but you know how some people are: we always want the latest and greatest (and stable) :D
And to get that was cumbersome in my opinion.

I've spent a full month with openSUSE, no other OS-es, and I liked every piece of it except for the few bugs and the software management.
I'll almost surely try it out again when it ships with KDE 4.4. :)

---

### Post by ~sHyLoCk~ on 2009-12-12
> **cguy said:**
> Updating KDE may not be officially supported, but you know how some people are: we always want the latest and greatest (and stable) :D
And to get that was cumbersome in my opinion.

I've spent a full month with openSUSE, no other OS-es, and I liked every piece of it except for the few bugs and the software management.
I'll almost surely try it out again when it ships with KDE 4.4. :)

Bleeding edge + stability is a myth. Forget it, its never gonna happen. Bleeding edge packages are unstable since they are not tested thoroughly. No distro can provide you with bleeding edge packages and keep things stable at the same time for everyone. It's a price you must pay for trying out bleeding edge, hemorrhaging stuffs.

---

### Post by SuperSonic4 on 2009-12-12
> **~sHyLoCk~ said:**
> Bleeding edge + stability is a myth. Forget it, its never gonna happen. Bleeding edge packages are unstable since they are not tested thoroughly. No distro can provide you with bleeding edge packages and keep things stable at the same time for everyone. It's a price you must pay for trying out bleeding edge, hemorrhaging stuffs.

+1

Too many people seem to think they can have the best of both worlds. I know full well my system isn't stable but I do know it's new

---

### Post by cguy on 2009-12-12
> **~sHyLoCk~ said:**
> Bleeding edge + stability is a myth. Forget it, its never gonna happen. Bleeding edge packages are unstable since they are not tested thoroughly. No distro can provide you with bleeding edge packages and keep things stable at the same time for everyone. It's a price you must pay for trying out bleeding edge, hemorrhaging stuffs.

After the upgrade everything was as stable as before, if not more stable (no more Plasma crashes IIRC).
Kinda cliche what you're saying :P

---

