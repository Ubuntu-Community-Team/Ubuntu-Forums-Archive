---
title: "Half-Rolling Distro"
date: 2011-06-15
forum: Recurring Discussions
---

### Post by dh04000 on 2011-06-15
I was reading the Chakra Linux FAQ, and I have become very interested in their "half-rolling" distro concept. If your not familiar with this concept, then I'll try to describe it. A rolling distro updates all packages as they are produced, core packages and applications (Arch follows this). A non-rolling distro creates 6 or month release. Packages both core and applications are not updated between releases (ubuntu follows this). The difference between a half-rolling distro and the normal two options are that it is a "rolling distro, but the core packages are not-updated until a stable version is released, while applications are updated as they are produced. The half-rolling concept keeps essential core packages stable while keeping users up to date with applications.

I think that the half-rolling distro is the best for the user, providing stability and access to new applications. Access to new applications is currently an issue on ubuntu. I think that Ubuntu should have a half-rolling option. The Long-Term_Support option should still be an option for users that don't want to risk stability in any fashion, but the current non-LTS versions of Ubuntu should have the option to be half-rolling. That way they roll into the next LTS version, and the user can decide whether to keep rolling, or stay with the current LTS.

I think that a half-rolling distro with LTS versions every few years would provide the best experience for ubuntu users. What do you all think?

DISCUSS!

---

### Post by 8_Bit on 2011-06-15
This is a great concept and I'm honestly surprised so few distros have taken it up. I definitely support this idea.

---

### Post by qamelian on 2011-06-15
Actually, the current release model is one of the reasons I prefer Ubuntu.

---

### Post by el_koraco on 2011-06-15
> **qamelian said:**
> Actually, the current release model is one of the reasons I prefer Ubuntu.

+1 on that.

---

### Post by dh04000 on 2011-06-15
> **8_Bit said:**
> This is a great concept and I'm honestly surprised so few distros have taken it up. I definitely support this idea.

I'm surprised as well. New applications while maintaining quality and stability? Who wouldn't love that?

---

### Post by tgalati4 on 2011-06-15
I think it creates a lot more work for the maintainers.  I like the concept and I think it would make the transitions between LTS releases less jarring, but there is also potential for breakage.

For the current Ubuntu release system, as the frameworks are frozen upon release, all packages can only be successfully built on those frameworks.  As the frameworks mature, it's difficult to build old packages using new frameworks and it's difficult compile new packages using old frameworks.  The are locked to each other, so the current release system makes sense.  But the LTS system at the end of the 2-year desktop cycle feels old, and there are not enough backports.  As I have discovered, packages that are not backported break in a major way when trying to compile them with older frameworks.  So a half-rolling distro has some appeal in this situation.

Here's an example:

I like zim to take notes.  I have 3 different versions on three different Ubuntu systems:  Dapper Drake is running 0.20.  My Jaunty laptop is running 0.28.  Natty is running (essentially) a fork at 0.57 since it changed languages.  It would be nice to have the same version on all three machines, but there is no way the latest version of Zim will build on Dapper Drake because of all the new dependencies.

A half-rolling distro would give me a chance to build/backport some of these newer packages on older Ubunut systems.

---

### Post by dh04000 on 2011-06-15
> **tgalati4 said:**
> I think it creates a lot more work for the maintainers.  I like the concept and I think it would make the transitions between LTS releases less jarring, but there is also potential for breakage.

For the current Ubuntu release system, as the frameworks are frozen upon release, all packages can only be successfully built on those frameworks.  As the frameworks mature, it's difficult to build old packages using new frameworks and it's difficult compile new packages using old frameworks.  The are locked to each other, so the current release system makes sense.  But the LTS system at the end of the 2-year desktop cycle feels old, and there are not enough backports.  As I have discovered, packages that are not backported break in a major way when trying to compile them with older frameworks.  So a half-rolling distro has some appeal in this situation.

Here's an example:

I like zim to take notes.  I have 3 different versions on three different Ubuntu systems:  Dapper Drake is running 0.20.  My Jaunty laptop is running 0.28.  Natty is running (essentially) a fork at 0.57 since it changed languages.  It would be nice to have the same version on all three machines, but there is no way the latest version of Zim will build on Dapper Drake because of all the new dependencies.

A half-rolling distro would give me a chance to build/backport some of these newer packages on older Ubunut systems.

Exactly! Also it makes sense from a security point of view. Old versions of software create security risks due to lack of updates. A Half-Rolling distro would prevent alot of security risks.

---

### Post by Bandit on 2011-06-15
> **qamelian said:**
> Actually, the current release model is one of the reasons I prefer Ubuntu.

> **el_koraco said:**
> +1 on that.
+2



> **dh04000 said:**
> I'm surprised as well. New applications while maintaining quality and stability? Who wouldn't love that?
Current release is based more less around Gnome release. Which is every 6 months. And No I would not like that idea as rolling release can be to hard to maintain and keep stable. Being a programmer the thought of it just makes my brain bleed!

---

### Post by dh04000 on 2011-06-15
> **Bandit said:**
> 
Current release is based more less around Gnome release. Which is every 6 months. And No I would not like that idea as rolling release can be to hard to maintain and keep stable. Being a programmer the thought of it just makes my brain bleed!

A half-rolling distro helps to prevent issues. It not much different than writing a program to target a certain service pack of windows or the newest OSX release, becuase of the stable core, only moving at stable releases.

---

### Post by sffvba[e0rt on 2011-06-15
Sounds like Tumbleweed by openSUSE... except they refer to it as Troubleweed as this is all it has been for them since the start (going on the reaction by the people on IRC).


404

---

### Post by qamelian on 2011-06-15
> **dh04000 said:**
> Exactly! Also it makes sense from a security point of view. Old versions of software create security risks due to lack of updates. A Half-Rolling distro would prevent alot of security risks.
Not really because security fixes are generally backported to the current version in Ubuntu, hence the various fixes and updates that are offered through update manager. Your system only stops receiving security fixes if you keep using it past end-of-life. 

Also, it isn't always possible to upgrade to a newer version of an app without also upgrading one or more core components of the OS. The "half-rolling" idea might work for some software, but certainly not all.

---

### Post by 3Miro on 2011-06-15
Other distros have similar concepts. Debian has stable and testing versions. Gentoo has the stable and unstable keywords (you can select to upgrade specific packages to unstable/testing versions).

Ubuntu is half-way there with 6 month stable releases and Beta releases in between. (also unofficial ppa, no other distro has as many extra repositories as Ubuntu)

---

### Post by dh04000 on 2011-06-15
> **3Miro said:**
> Other distros have similar concepts. Debian has stable and testing versions. Gentoo has the stable and unstable keywords (you can select to upgrade specific packages to unstable/testing versions).

Ubuntu is half-way there with 6 month stable releases and Beta releases in between. (also unofficial ppa, no other distro has as many extra repositories as Ubuntu)

I basically have a half-rolling distro becuase of all of my ppa's. The very existance of ppa's kind prove the need for a half-rolling distro. Finding all of those ppa's is non very user-friendly. In fact, the need for ppa's and why their applications just don't "upgrade like back on windows and mac" holds linux back for users. A half-rolling distro would fix many of these problems.

---

### Post by Bandit on 2011-06-15
> **dh04000 said:**
> A half-rolling distro helps to prevent issues. It not much different than writing a program to target a certain service pack of windows or the newest OSX release, becuase of the stable core, only moving at stable releases.
I may have miss understood. I will go back and read..

---

### Post by tgalati4 on 2011-06-15
It never occurred to me that PPA's do provide some of that half-rolling behavior.  But PPA's usually push out development code and not something you want to rely on for older machines where you expect stability and a non-changing, yet working, environment.

Another model, which intrigues me, is taken by the [http://bitnami.org](http://bitnami.org) folks.  They push out modern, stable versions of popular services but statically compiled, binary blobs that seem to run just fine under Dapper Drake.  So although it doesn't solve the kernel security issues, it does allow older machines to run the latest version of WordPress.  There's no way you could compile the latest WordPress on a Dapper Drake build environment, but it runs the binary blob of statically-complied code just fine.  It just takes up more disk space since the blobs are large (several hundred MB) and can't share their libraries with other applications.  So running several of these blobs can take up a lot of RAM since there are no usable shared libraries on the old host system.

---

### Post by netJackDaw on 2011-06-16
I think Ubuntu should have a rolling release. People (I) do not want to upgrade, they want to install once and be done with it, after that only updates. Perhaps a more stable approach to rolling would be preferred. Ie new applications at once and base packages with a little more testing. ...or maybe some options to the user to be more or less adventurous in how he/she wants the rolling to work.

If we are talking about a release based half-rolling release I would like the LTS support period to be longer, like seven to ten years. That with the same arguments as above, don't want to upgrade or reinstall... Just want to use it (with the latest applications available).

Just my opinions... (Says he who considers a jump to LMDE).

---

### Post by dh04000 on 2011-06-16
> **tgalati4 said:**
> It never occurred to me that PPA's do provide some of that half-rolling behavior.  But PPA's usually push out development code and not something you want to rely on for older machines where you expect stability and a non-changing, yet working, environment.

Another model, which intrigues me, is taken by the [http://bitnami.org](http://bitnami.org) folks.  They push out modern, stable versions of popular services but statically compiled, binary blobs that seem to run just fine under Dapper Drake.  So although it doesn't solve the kernel security issues, it does allow older machines to run the latest version of WordPress.  There's no way you could compile the latest WordPress on a Dapper Drake build environment, but it runs the binary blob of statically-complied code just fine.  It just takes up more disk space since the blobs are large (several hundred MB) and can't share their libraries with other applications.  So running several of these blobs can take up a lot of RAM since there are no usable shared libraries on the old host system.

Actually, its funny that you mention this website, because "bundles" with all of the dependencies included is how Chakra linux handles some packages that don't agree with the half-rolling release scedule, or are gtk+ apps (they don't want to mix kde and gtk, but that's just hw they prefer their distro).

Yes, I think a bundle like service could be used in Ubuntu as well, to fill in when dependences don't match. Maybe program the software center to check dependences, and if something in the core is too old, it could create a bundle just for that one application. The software center could then go back later after the core is updated and un-bundle the application once the dependencies are matched. So, only a small percentage of the distro would be "bundled" at any one time.

It would cost some extra hard drive space and ram, but it would be amazing for the end user experience.

---

### Post by mips on 2011-06-16
> **dh04000 said:**
> **A non-rolling distro** creates 6 or month release (**Arch follows this**).

DISCUSS!

I seriously think you have lost the plot completely.

---

### Post by dh04000 on 2011-06-16
> **mips said:**
> I seriously think you have lost the plot completely.

Fixed.

---

### Post by snowpine on 2011-06-16
I voted No because I think "backports" is a more descriptive and appealing term than "half-rolling."

---

### Post by AeroZak on 2011-06-16
> **tgalati4 said:**
> I think it creates a lot more work for the  maintainers.  I like the concept and I think it would make the  transitions between LTS releases less jarring, but there is also  potential for breakage.

I completely agree with this, more stress on the maintainers isn't very good, and could be potential for some mishap.

However, it is an extremely good concept, and as long as there is a  strong enough community to make sure no one part of the project is too  overworked, then it would be an excellent choice on how to run a distro.

---

### Post by dh04000 on 2011-06-16
It Canonical starts turning a profit, then they can hire the staff to make a half-rolling distro possible. If the small Chakra linux community can do it, Canonical and the Ubuntu community could do it better! :)

---

### Post by wolfen69 on 2011-06-16
I like this half-rolling release idea. I think it wouldn't be too hard to implement, and would satisfy the whiners who complain about stale apps. Imagine an LTS with up-to-date-apps!

---

### Post by Dustin2128 on 2011-06-16
What's with all the bots lately?

---

### Post by krapp on 2011-06-16
> **snowpine said:**
> I voted No because I think "backports" is a more descriptive and appealing term than "half-rolling."

Yeah, this would be correct analogy facing Debian, not Testing as someone else suggested.

Backports is real an ideal way to keep a system current. If only there were MORE packages in Debian Backports. At least the Mozilla team has done a splendid job.

Canonical should take a few popular PPAs under their arm and maintain/audit them themselves. This would satsify "half-rolling" I think.

---

### Post by uRock on 2011-06-16
> **dh04000 said:**
> I'm surprised as well. New applications while maintaining quality and stability? Who wouldn't love that?

Once softwares start getting updated new bugs get created and stability is lost.

---

### Post by Sef on 2011-06-17
Another what should Ubuntu's release policy be, so moved.

---

### Post by dh04000 on 2011-06-17
....... So the community is not allowed to discuss ideas on release schedules. Only Canonical and canonical employed members can? What harm will dicussion have? Has a half-rolling distro ever been discussed? By anyone?

I'm losing faith in the Ubuntu community, its really sad.


EDIT: I need a mod to contact me with information on how to submit a complaint to the administration of Ubuntu forums.

---

### Post by snowpine on 2011-06-17
> **dh04000 said:**
> ....... So the community is not allowed to discuss ideas on release schedules. Only Canonical and canonical employed members can? What harm will dicussion have? Has a half-rolling distro ever been discussed? By anyone?

I'm losing faith in the Ubuntu community, its really sad.


EDIT: I need a mod to contact me with information on how to submit a complaint to the administration of Ubuntu forums.

Nobody is censoring our conversation; you're over-reacting I think... :)

---

### Post by dh04000 on 2011-06-17
> **snowpine said:**
> Nobody is censoring our conversation; you're over-reacting I think... :)

It definitely feels like censoring. I'm being told what I can and can not discuss, and then my message is being removed from view and buried, because it isn't what the status quo is. 

Sounds like classic censoring to me. Let's see how long it takes me to get banned because I dared to speak out about injustice. Just like in China(except they kill people).

What they forget(which is funny actually) is that the release schedule is not "set in stone". Ubuntu focuses on being the best for users, and if half-rolling was better, and enough people got behind it, the release schedule would be changed. That's how a community is "supposed" to work.

Then, the ironic thing would be that threads that discuss going back to a non-half-rolling, or any other schedule would be silenced.

Silencing should just never happen in the first place. It's wrong in any context. I believe in free speech. Long live free speech!

BTW: I'm not trying to start a fight. I'm not trying to bring down Ubuntu (In fact, i love Ubuntu). I'm not trying to be anti-society. I think a mod just woke up on the wrong side of the bed this morning and over reacted (Please drink a cup of coffee, I'll buy if your in the Newark DE, I'll take you to Brew HAHA). I still need that contact info mods, when you get a moment to do so. Thanks. I believe that all problems should be dealt with following proper protocol, so I need to file a report. If the mods try, they'll find me to be a very reasonable human being.

---

### Post by Simian Man on 2011-06-17
This is a good idea and, interestingly, is the release model Windows uses.  You can update Firefox, Photshop, Office, and all your other programs while still being on Windows XP.  The lack of stable APIs and ABIs will make this much more difficult for Linux to do as well as Windows, however.

---

### Post by snowpine on 2011-06-17
> **Simian Man said:**
> This is a good idea and, interestingly, is the release model Windows uses.  You can update Firefox, Photshop, Office, and all your other programs while still being on Windows XP.  The lack of stable APIs and ABIs will make this much more difficult for Linux to do as well as Windows, however.

I'd have to (respectfully) disagree with this Windows comparison. The difference being that Microsoft does not support Firefox, Photoshop, or Office (at least not as part of XP). There is no comprehensive Software Center or Update Manager and end users are solely responsible for keeping applications up-to-date (often at great risk).

Canonical on the other hand supports each and every application in the Ubuntu repositories. Ubuntu users are guaranteed of bug fixes to Firefox, Gimp, LibreOffice, etc. for the lifespan of the release. Furthermore users are 100% free to install apps from the "upstream" developer (just like in Windows). Having a stable and supported base system does not restrict the user's freedom to perform desired selective upgrades.

---

### Post by Simian Man on 2011-06-17
> **snowpine said:**
> Canonical on the other hand supports each and every application in the Ubuntu repositories. Ubuntu users are guaranteed of bug fixes to Firefox, Gimp, LibreOffice, etc. for the lifespan of the release. Furthermore users are 100% free to install apps from the "upstream" developer (just like in Windows). Having a stable and supported base system does not restrict the user's freedom to perform desired selective upgrades.

If by "support" you mean store in their repositories, then yes.  But bug fixes and security updates are by and large done by independent upstream developers whether for Windows or Linux.  With Linux, there is the added step of the distros packaging things for their users, but there isn't much value added here, and sometimes bugs are actually introduced (the Debian/Ubuntu OpenSSL bug comes to mind).

---

### Post by fuduntu on 2011-06-17
> **dh04000 said:**
> I was reading the Chakra Linux FAQ, and I have become very interested in their "half-rolling" distro concept. If your not familiar with this concept, then I'll try to describe it. A rolling distro updates all packages as they are produced, core packages and applications (Arch follows this). A non-rolling distro creates 6 or month release. Packages both core and applications are not updated between releases (ubuntu follows this). The difference between a half-rolling distro and the normal two options are that it is a "rolling distro, but the core packages are not-updated until a stable version is released, while applications are updated as they are produced. The half-rolling concept keeps essential core packages stable while keeping users up to date with applications.

I think that the half-rolling distro is the best for the user, providing stability and access to new applications. Access to new applications is currently an issue on ubuntu. I think that Ubuntu should have a half-rolling option. The Long-Term_Support option should still be an option for users that don't want to risk stability in any fashion, but the current non-LTS versions of Ubuntu should have the option to be half-rolling. That way they roll into the next LTS version, and the user can decide whether to keep rolling, or stay with the current LTS.

I think that a half-rolling distro with LTS versions every few years would provide the best experience for ubuntu users. What do you all think?

DISCUSS!

We do this at Fuduntu.  We have a stable base, and roll the Kernel, Chromium, and a few other important packages.

---

### Post by snowpine on 2011-06-17
> **Simian Man said:**
> If by "support" you mean store in their repositories, then yes.  But bug fixes and security updates are by and large done by independent upstream developers whether for Windows or Linux.  With Linux, there is the added step of the distros packaging things for their users, but there isn't much value added here, and sometimes bugs are actually introduced (the Debian/Ubuntu OpenSSL bug comes to mind).

The "value added" is that the user can bug-fix each and every installed package with a single click in the Update Manager. This is by far my favorite feature of Linux. :)

---

### Post by dh04000 on 2011-06-17
> **fuduntu said:**
> We do this at Fuduntu.  We have a stable base, and roll the Kernel, Chromium, and a few other important packages.

Really? I think I will be checking out Fuduntu soon. I am really interested in the half-rolling concept. What apps count as "other packages"?

---

### Post by uRock on 2011-06-17
> **Simian Man said:**
> If by "support" you mean store in their repositories, then yes.  But bug fixes and security updates are by and large done by independent upstream developers whether for Windows or Linux.  With Linux, there is the added step of the distros packaging things for their users, but there isn't much value added here, and sometimes bugs are actually introduced (the Debian/Ubuntu OpenSSL bug comes to mind).

I never knew Microsoft did security updates for non-Microsoft products. I've only noticed Chrome, FF and Adobe updates coming from their providers.

---

### Post by Simian Man on 2011-06-17
> **uRock said:**
> I never knew Microsoft did security updates for non-Microsoft products. I've only noticed Chrome, FF and Adobe updates coming from their providers.

By and large the updates come upstream in Linux too, they are just applied by distros.  But that's kind of tangential to my point which is that, in Windows, there is a nice division between applications and your system which is very similar to this idea.

---

### Post by fuduntu on 2011-06-17
> **dh04000 said:**
> Really? I think I will be checking out Fuduntu soon. I am really interested in the half-rolling concept. What apps count as "other packages"?

Shotwell, Vala, Pinta are a few, mostly apps that users deem important enough to ask us to update.

---

### Post by snowpine on 2011-06-17
> **Simian Man said:**
> By and large the updates come upstream in Linux too, they are just applied by distros.  But that's kind of tangential to my point which is that, in Windows, there is a nice division between applications and your system which is very similar to this idea.

I agree with what you're saying except for the word "nice." The division in Windows is that Microsoft does not provide or support end-user applications; because the apps are divided from the OS, each app needs its own apparatus to check for and apply updates, and the end user must stay on top of all the changes piecemeal. There is zero testing that updating Application A won't break Application B, and no accountability that the software is legit and malware-free.

I believe the Linux way of testing OS and apps together as a unified release is superior in terms of stability and ease of administration. A complete-system upgrade from a tested and trusted software repository fits my personal admin "style" perfectly. Furthermore it does not in any way *prevent* anyone from administering their system "The Windows Way" by downloading an installer for each app from the appropriate website.

---

### Post by Simian Man on 2011-06-17
> **snowpine said:**
> each app needs its own apparatus to check for and apply updates, and the end user must stay on top of all the changes piecemeal.

I agree with you there.  My perfect OS would provide a stable base, along with a standard way to install and update 3rd party apps.  That way software developers could have control over updates themselves without annoying the bejeesus out of users :).  It would basically be like Ubuntu if you installed every app from a ppa.

---

### Post by dh04000 on 2011-06-17
> **Simian Man said:**
> I agree with you there.  My perfect OS would provide a stable base, along with a standard way to install and update 3rd party apps.  That way software developers could have control over updates themselves without annoying the bejeesus out of users :).  It would basically be like Ubuntu if you installed every app from a ppa.

Exactly! A half-rolling distro would really be ideal for users. The creation of PPA's are direct evidence of how REAL users want to be able to get new versions of their applications. So why make it hard for users to do so??? Why not just be a half-rolling distro and solve this problem once and for all?  Now, I'm not suggesting this for the server edition of ubuntu. Even half-rolling is too dangerous for them, but the users have already spoken with thier use of PPA's. USERS NEED NEWER VERSION OF THIER APPS!

I think the update manager of Ubuntu should have a little option bubble you can configure to be stable, or half-rolling. Changing this option switches your package versions between these modes. Just like adding and purging ppa's does.

That way EVERYONE could be happy. Enterprise can be 100% stable and users can acquire their apps.


BTW: Canonical just bought a SUPER ARM server to compile applications faster(can't find the link). Why not put it to work compiling new apps as they come out in a half-rolling fashion?

I'm really considering filing this as an idea on Launchpad, or something.

---

### Post by snowpine on 2011-06-17
> **Simian Man said:**
> I agree with you there.  My perfect OS would provide a stable base, along with a standard way to install and update 3rd party apps.  That way software developers could have control over updates themselves without annoying the bejeesus out of users :).  It would basically be like Ubuntu if you installed every app from a ppa.

Let's assume this proposal is "perfect" for some sub-set of Ubuntu users. To play devil's advocate... Why would Canonical ever choose to do this? Why would they hand control over to 3rd party developers and give up control over the finished product? Why would they focus on making Ubuntu *less* stable instead of *more* stable when it is already being criticized for poor quality control and rushed releases?

---

### Post by Simian Man on 2011-06-17
> **snowpine said:**
> Let's assume this proposal is "perfect" for some sub-set of Ubuntu users. To play devil's advocate... Why would Canonical ever choose to do this? Why would they hand control over to 3rd party developers and give up control over the finished product? Why would they focus on making Ubuntu *less* stable instead of *more* stable when it is already being criticized for poor quality control and rushed releases?

This is one big difference between Linux and other OSs.  In Linux there is little differentiation between applications and the OS - but there should be.  Giving, for example, Mozilla control of Firefox updates (which they are the authors of anyway) can't make Ubuntu less stabe because *Firefox is not part of Ubuntu*.  If Ubuntu would focus on just maintaining the base system then (a) their task wouldn't be so unmanageable and (b) there would be much less pressure to release so often because users would be happy with their up to date applications.

---

### Post by snowpine on 2011-06-17
> **Simian Man said:**
> This is one big difference between Linux and other OSs.  In Linux there is little differentiation between applications and the OS - but there should be.  Giving, for example, Mozilla control of Firefox updates (which they are the authors of anyway) can't make Ubuntu less stabe because *Firefox is not part of Ubuntu*.  If Ubuntu would focus on just maintaining the base system then (a) their task wouldn't be so unmanageable and (b) there would be much less pressure to release so often because users would be happy with their up to date applications.

Firefox absolutely is "part of Ubuntu" in my opinion, and Canonical has an obligation to thoroughly test every application included in the base install.

---

### Post by beew on 2011-06-17
> **uRock said:**
> Once softwares start getting updated new bugs get created and stability is lost.

There are always risks in  life. What is the point of "stability" if things don't work or work poorly because important features and new enhancements are lacking?

I should point out especially to new users that "stability" in Linux  talk doesn't mean better or more reliable performance. It means  something predictable and doesn't change.So if something is predictably  and consistently underperforming or broken it is "stable" in  that  technical sense. I can't see how that is desirable for most desktop  users.

Keep in mind that open source has a different development and release method from commercial softwares so examples like many people are still using Office2003 are irrelevant to this discussion.

Commercial softwares have very infrequent releases (who would pay every few months to get a new version?) but they also tend to release only reasonably finished and feature completed products (or people would scream for their money back) On the other hand open source is the opposite, open source softwares tend to release early and frequently so they can get feed back from users concerning bugs and features requests. There is always an unfinished quality to FOSS so chances are there are bugs that won't get fixed and crucial features that are missing that can only be addressed through updates.

FOSS is by nature 'rolling' in that sense. So a new Ubuntu comes out every 6 months whereas it takes years for a new version of Windows to appear. If you can see the logic of Ubuntu having a short and rapid release cycle it should not be hard to see the same logic applies to other softwares as well.

It is also quite odd that you expect people to upgrade the whole OS every 6 months to mostly beta OSes (I am told many times by same people who advise against ppas that non LTS should be considered betas) while complaining that updating end user softwares would bring instability. What can be more unstable than having to upgrade from one beta OS to the next every 6 months?

---

### Post by wolfen69 on 2011-06-17
> **dh04000 said:**
> It definitely feels like censoring. I'm being told what I can and can not discuss, and then my message is being removed from view and buried, because it isn't what the status quo is. 


The forums aren't a democracy. The mods can do as they see fit. Like I've heard the mods say, if you don't like the format here, feel free to go elsewhere where it may better suit your posting style.

---

### Post by dh04000 on 2011-06-17
> **wolfen69 said:**
> The forums aren't a democracy. The mods can do as they see fit. Like I've heard the mods say, if you don't like the format here, feel free to go elsewhere where it may better suit your posting style.


That's all fine and dandy, but I didn't anything wrong. I didn't hurt anyone's feelings, or attack anyone, or attack Ubuntu. I was proposing an alternative view. Apparently being different is a crime here on the forums. And I find that very sad. Very very disheartening indeed. Hurting me was worth more to the mods then allowing me to propose a thought experiment. My words were more dangerous to them and worth more than respecting me as a human being.

I believe in free speech and free expression. I guess they don't hold the same values in South Africa.

---

### Post by uRock on 2011-06-17
If the thread can't stay on topic, then I will close it.

---

### Post by dh04000 on 2011-06-18
> **beew said:**
> .....(More before this, cut to shorten)

It is also quite odd that you expect people to upgrade the whole OS every 6 months to mostly beta OSes (I am told many times by same people who advise against ppas that non LTS should be considered betas) while complaining that updating end user softwares would bring instability. What can be more unstable than having to upgrade from one beta OS to the next every 6 months?

I totally agree with this. I don't believe you can correlate applications with the rest of the OS. Does upgrading firefox make Ubuntu, Windows, or Mac less stable? No. At worst case firefox can pick up a new bug, but that's what bug fixes are for.

I'm beginning to think that this OS vs Apps issue is more wide spread than the ditro level. I think that the fix for this issue needs to come from upstream. The core OS (kernel, gnome, kde, graphics, audio, networking, ect) need to be cleanly defined and separated from applications. That way this culture of moving version numbers cause instability and bugs would not be as powerful and widespread.

And the only way this culture is going to change is if users ask for it. Users are the power of linux. So if we want sanity in the design of our OS, then we need to demand it! If you want the year of the linux desktop, you got to demand it!

---

### Post by screaminj3sus on 2011-06-18
> **qamelian said:**
> Actually, the current release model is one of the reasons I prefer Ubuntu.

Its the reason I currently don't use ubuntu. I always end up clogging my system up with 10,000 ppa's.

---

### Post by dh04000 on 2011-06-19
> **screaminj3sus said:**
> Its the reason I currently don't use ubuntu. I always end up clogging my system up with 10,000 ppa's.

It would be nice if we didn't have to use use many ppa's to keep up with application updates. This article well shows how the intention of ppa's to test new applications that didn't make it in time for a repo lock, is not how people use them. People use them to keep their applications up to date. 

[http://www.omgubuntu.co.uk/2011/05/the-evolution-of-the-personal-package-archive-system/](http://www.omgubuntu.co.uk/2011/05/the-evolution-of-the-personal-package-archive-system/)

---

### Post by dh04000 on 2011-06-19
[http://brainstorm.ubuntu.com/idea/28150/](http://brainstorm.ubuntu.com/idea/28150/)

I made a Ubuntu brainstorm of this idea!  Hit like if you like it!

---

### Post by uRock on 2011-06-19
Programs can be installed and kept up to date without adding a PPA.

---

### Post by beew on 2011-06-20
> **uRock said:**
> Programs can be installed and kept up to date without adding a PPA.

Yes, but whatever you do it would not be the official "Ubuntu way" which keeps the same version for 6 - 18 months and then upgrades the softwares by upgrading the whole OS. The fact that you can have other ways to updates softwares than PPAs is not an argument for the official philosophy of updating softwares via upgrading OS. 

And ppa is the most convenient way to update softwares, I can compile some programs from source but I wouldn't want to do that for all programs I want to keep up to date, and  programs compiled from source don't get automatically updated, you have to compile again (same with .deb though it is a lot easier)

---

### Post by dh04000 on 2011-06-20
Doesn't upgrading a version of an application to later than the official Ubuntu repo version break the package manager's ability to manage the application?

The half-rolling proposal allows the package manager to work as intended and is much more user-friendly than the other method. Non-hard core linux users don't understand the concept of forcing package verions, that's foreign to them. They are used to applications managing their own updates automagically.

---

### Post by uRock on 2011-06-20
> **beew said:**
> And ppa is the most convenient way to update softwares, I can compile some programs from source but I wouldn't want to do that for all programs I want to keep up to date, and  programs compiled from source don't get automatically updated, you have to compile again (same with .deb though it is a lot easier)

I once installed Thunderbird in my /home and it updated itself the same way it does in Windows. Once I noticed it was self updating, I removed it.

I am happy with the way Ubuntu handles packaging. I really do not see the need to be at the bleeding edge with every application. If Canonical were to change over to the half-rolling release, then they would have to drop how many releases are supported at one time. I am sure it would be a real pain in the fourth point of contact to try and update all of the library files that go with each application.

The next question that comes into play is, "How would this effect businesses, which are known to write their own add-ons to softwares such as Firefox to make them do a specific task handle a sudden and unexpected upgrade to a new version of the application?"

Example, the local Carmax still uses IE6 because of security features they have added to the browser. If Ubuntu was to force FF4 on those people using 10.04, which comes with 3.6.*, would Canonical still keep putting out security updates for 3.6 as well? If not, the this would totally mess up the vendor who has a set standard to stay with a certain version of an application. This would break company wide stability and the company would most likely ditch the OS for one with a more stable system.

---

### Post by BrokenKingpin on 2011-06-20
I think it would be great. I hate re-installing every 6 months just to get the newer releases of a few applications.

---

### Post by dh04000 on 2011-06-20
> **uRock said:**
> I once installed Thunderbird in my /home and it updated itself the same way it does in Windows. Once I noticed it was self updating, I removed it.

I am happy with the way Ubuntu handles packaging. I really do not see the need to be at the bleeding edge with every application. If Canonical were to change over to the half-rolling release, then they would have to drop how many releases are supported at one time. I am sure it would be a real pain in the fourth point of contact to try and update all of the library files that go with each application.

The next question that comes into play is, "How would this effect businesses, which are known to write their own add-ons to softwares such as Firefox to make them do a specific task handle a sudden and unexpected upgrade to a new version of the application?"

Example, the local Carmax still uses IE6 because of security features they have added to the browser. If Ubuntu was to force FF4 on those people using 10.04, which comes with 3.6.*, would Canonical still keep putting out security updates for 3.6 as well? If not, the this would totally mess up the vendor who has a set standard to stay with a certain version of an application. This would break company wide stability and the company would most likely ditch the OS for one with a more stable system.

The business issue might be a bad aspect of the half-rolling concept, but as i said in my brainstorm page, there should be a on-off toggle for this behavior. That way its a users decision.

Also, did you see my brainstorm page today? Someone marked it all ready implemented. Turns out some community members have already made a ubuntu-backports repo that does EXACTLY what I have described. It updates user applications while leaving the core un touched. Brilliant!

I just added the repo using the deb(http:ect ect ect ect) to my software sources and did a sudo apt-get upgrade, but nothing happened....

Any ideas uRock? Is there no backports for the current distro?

If I find that this works, I'm considering joining their effort (it was mentioned on my brainstorm page that they need more volunteers). I will have to learn how to compile software and use GIT, but I think this effort is worth my time.

---

### Post by psusi on 2011-06-20
Ubuntu already follows this "half rolling" model; it is called the backports repository.  See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by Tibuda on 2011-06-20
> **psusi said:**
> Ubuntu already follows this "half rolling" model; it is called the backports repository.  See [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Like if it was actively used. The closest thing are ppas.

---

### Post by dh04000 on 2011-06-20
I just took a look at the packages provided in the Ubuntu backports, and there isn't much really.... we need a proper backport repo.

---

### Post by psusi on 2011-06-20
> **dh04000 said:**
> I just took a look at the packages provided in the Ubuntu backports, and there isn't much really.... we need a proper backport repo.

We have one.  If you feel something is missing, file a bug report requesting it.

---

### Post by dh04000 on 2011-06-21
> **psusi said:**
> We have one.  If you feel something is missing, file a bug report requesting it.
I know we have one. I just said I took a look at the package list.

Where's Firefox? Thunderbird? Pidgin? GIMP?

Why aren't any of these applications in the backport repo?

---

### Post by psusi on 2011-06-21
Looks like thunderbird is in the -updates repository:

[https://bugs.launchpad.net/lucid-backports/+bug/658407](https://bugs.launchpad.net/lucid-backports/+bug/658407)

Looks like GIMP is in progress, but needs more testing of packages that depend on it to make sure they don't break:

[https://bugs.launchpad.net/lucid-backports/+bug/729998](https://bugs.launchpad.net/lucid-backports/+bug/729998)

Apparently there are still concerns about firefox 4 being unstable.  I'm not sure how valid that is.

[https://bugs.launchpad.net/lucid-backports/+bug/775204](https://bugs.launchpad.net/lucid-backports/+bug/775204)

No request has been filed for pidgen.

---

