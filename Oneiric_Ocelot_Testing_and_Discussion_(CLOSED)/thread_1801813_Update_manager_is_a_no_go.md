---
title: "Update manager is a no go"
date: 2011-07-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by CaptainMark on 2011-07-11
Is this a common bug? update manager wont even open, just crashes immediately when i try to open it and have to do update using apt-get

---

### Post by el_koraco on 2011-07-11
not only is it common, but update manager is the least advisable method of updating a development release. the best is apt-get, or synaptic if you want the graphical route. if you're feeling adventurous, you ca use aptitude, but do yourself a favor, and forget about update manager.

---

### Post by dino99 on 2011-07-11
> **el_koraco said:**
> not only is it common, but update manager is the least advisable method of updating a development release. the best is apt-get, or synaptic if you want the graphical route. if you're feeling adventurous, you ca use aptitude, but do yourself a favor, and forget about update manager.

wow, the funniest i've never seen

---

### Post by Harry33 on 2011-07-11
> **el_koraco said:**
> not only is it common, but update manager is the least advisable method of updating a development release. The best is apt-get, or synaptic if you want the graphical route. If you're feeling adventurous, you ca use aptitude, but do yourself a favor, and forget about update manager.

+1

---

### Post by bennachie on 2011-07-11
+1 for Synaptic. Update Manager is seriously broken at the moment.

---

### Post by jerrylamos on 2011-07-11
> **bennachie said:**
> +1 for Synaptic. Update Manager is seriously broken at the moment.

The "moment" is the last several years! from my disasterous experience.
Busted from the word go.

Jerry

---

### Post by teh603 on 2011-07-11
> **el_koraco said:**
> not only is it common, but update manager is the least advisable method of updating a development release. the best is apt-get, or synaptic if you want the graphical route. if you're feeling adventurous, you ca use aptitude, but do yourself a favor, and forget about update manager.I had few problems with it from Jaunty thru Maverick, but that's a couple of releases ago, before Aptitude was removed from the default loadout and Synaptic was scheduled for the axe as well.

The big thing I found was that if it ever offers you a "partial update," hit CANCEL and then run like hell. Partial updates are more evil than GOTO.

---

### Post by Framli on 2011-07-11
Fellow testers, a new version of update-manager has landed a few hours ago. 

Because it's graphical, it won't be as much fun as typing *sudo aptitude update && sudo aptitude full-upgrade -y && sudo reboot*[1], but we should test it and report bugs. :D


[1]If you don't understand this command, don't try it.

---

### Post by tlcstat on 2011-07-11
Greetings, 
Testing the Update manager doesn't preclude using the terminal. After all! The first step is just getting it to open! So far it's a no go. Bug reported to Launchpad.
tlcstat

---

### Post by JRV on 2011-07-11
> **jerrylamos said:**
> The "moment" is the last several years! from my disasterous experience.
Busted from the word go.

Jerry

You got that right!

---

### Post by NightwishFan on 2011-07-11
> not only is it common, but update manager is the least advisable method of updating a development release. the best is apt-get, or synaptic if you want the graphical route. if you're feeling adventurous, you ca use aptitude, but do yourself a favor, and forget about update manager.

This doesn't sound right to me. There is more to upgrading to a newer release than just upgrading the packages right. I recommend update-manager on Ubuntu.

After you upgrade to the development release you will likely get the same results with aptitude as with the update-manager. Just always have it do a safe-upgrade because at times on devel releases you can remove xorg (or etc) and have the system be broken.

Basically (not target at any one in particular) if you do not understand Debian package management I would not use devel releases.

---

### Post by philinux on 2011-07-11
> **NightwishFan said:**
> This doesn't sound right to me. There is more to upgrading to a newer release than just upgrading the packages right. I recommend update-manager on Ubuntu.

After you upgrade to the development release you will likely get the same results with aptitude as with the update-manager. Just always have it do a safe-upgrade because at times on devel releases you can remove xorg (or etc) and have the system be broken.

Basically (not target at any one in particular) if you do not understand Debian package management I would not use devel releases.

Please see the forum sticky re partial upgrades. This is how update mangler causes major problems.

I use aptitude update and safe  or full upgrade as required.

---

### Post by NightwishFan on 2011-07-11
Yes, and a partial upgrade just means that it is asking to remove packages which you can decline to do so on update-manager. ie apt-get update or aptitude safe-upgrade. I prefer apt-get as it rivals aptitude now with dependency resolution and sometimes gets better results in a pinch.

My point is it doesn't really matter.

---

### Post by el_koraco on 2011-07-11
> **NightwishFan said:**
> 
After you upgrade to the development release you will likely get the same results with aptitude as with the update-manager. 


Not really. Update Manager is innthe habit of treating a regular upgrade as a dist-upgrade when stuff hasn't trickled down to the servers in time. Not watching what you do can be troublesome then (the dreaded partial upgrade). Both apt and Synaptic are more exhaustive with info. It's not like I invented this, Kubuntuforums even suggests users don't use anything other than apt. 

Bottom line is, UM was designed to work with stable releases.

---

### Post by NightwishFan on 2011-07-11
Not my experience but I last used Ubuntu 10.04. I think the port to aptd was after that in 10.10?

---

### Post by el_koraco on 2011-07-11
> **NightwishFan said:**
> Not my experience but I last used Ubuntu 10.04. I think the port to aptd was after that in 10.10?

Not sure exactly. But, just to give you an example - the last time I installed Maverick was in February, on my sister's laptop. i hit UM to do its job, and it says something along the lines - you may have requested an impossible situation, try to use sudo apt-get dist-upgrade. If it's refering you to apt, then you get the idea as to which is the smarter one of the pair.

---

### Post by mc4man on 2011-07-11
Unless you accept a 'partial upgrade' that occasionally shows up there is no way for  update manager to screw anything thing up, ever.
And while not the only way it also provides an easy way to view changelogs, either directly or thru active links.
A very useful tool during the dev. period, a "mangler" only by the those that misuse it.

---

### Post by NightwishFan on 2011-07-11
> **mc4man said:**
> Unless you accept a 'partial upgrade' that occasionally shows up there is no way for  update manager to screw anything thing up, ever.

But when I say this I get referred to a sticky post I already understand. :D

---

### Post by seeker5528 on 2011-07-11
> **jerrylamos said:**
> The "moment" is the last several years! from my disasterous experience.
Busted from the word go.

Does update-manager fail to provide an opportunity to cancel the installation if there is a 'partial upgrade' situation?

Does update-manager fail to provide an opportunity to see what changes will be made and give you the option to cancel the installation in situations where new packages will be installed or packages will be removed?

Later, Seeker

---

### Post by teh603 on 2011-07-11
> **seeker5528 said:**
> Does update-manager fail to provide an opportunity to cancel the installation if there is a 'partial upgrade' situation?

Does update-manager fail to provide an opportunity to see what changes will be made and give you the option to cancel the installation in situations where new packages will be installed or packages will be removed?

Later, SeekerUnless they've changed its behavior, its supposed to ask if you want to do a partial upgrade or not, with the usual options to proceed or cancel.

---

### Post by cariboo on 2011-07-11
The problem with update manager is that it doesn't warn you that the system may be unusable if you run a partial upgrade. We see many users doing a partial upgrade, and then having system problems afterwards.

This is really more of an operator error, than a problem with update-manager.

We suggest aptitude safe-upgrade, or synaptic, as both methods show the user what changes will be made, and generally using these methods will result in a update that doesn't cause any problems.

---

### Post by ranch hand on 2011-07-11
Just a note on aptitude/apt-get for upgrading to the next version.  As of the change in Debian to Squeeze as the stable, they recommend apt-get for that job (Squeeze as Testing was the base for 10.04).  Before that the recommendation was aptitude.

I have always used apt-get for doing this job seriously.  I have used Update Mangler for the job too.  Apt-get has a perfect record for success and UM 50%.  You do need to know how to run dpkg --configure -a.

If you don't I would do a clean install rather than risk my data to UM.

---

### Post by cariboo on 2011-07-11
On a released version update-manager has never caused me any problems, although I still prefer using synaptic. I've used update-manager several times to do a dist-upgrade, I'd say that 90% of the time the upgrade is completed properly, but I know enough to check to make sure the upgrade has completed before rebooting.

---

### Post by teh603 on 2011-07-12
> **cariboo907 said:**
> The problem with update manager is that it doesn't warn you that the system may be unusable if you run a partial upgrade. We see many users doing a partial upgrade, and then having system problems afterwards.
True, I don't remember the "unusable system" warning either, but with all the warnings on the board telling people that they shouldn't ever run a partial update, its hard to not click "CANCEL" when presented with that option.

---

### Post by jerrylamos on 2011-07-12
> **ranch hand said:**
> 
If you don't I would do a clean install rather than risk my data to UM.

Ranch Hand. clean installs for whatever reason seem to be a day behind on updates, example A2 has a defective lightdm panel on my Compaq tower but apt-get update apt-get upgrade fixed that.

So if A2 runs as is like on this Aspire one, without updates, fine.  

Daily Build still has 5 July .iso's and it's 12 July already.  A week behind on updates.  Wonder if development is trying to sort out such things as "no keyboard no mouse".  Workaround is pretty simple so I assume they don't want to do that.

Jerry

---

### Post by jerrylamos on 2011-07-12
"Update Manager" has trashed my installs for years.

Somebody tell me why Ubuntu Development continues to put out such a tool?

Thanks, Jerry

---

### Post by coffeecat on 2011-07-12
> **jerrylamos said:**
> "Update Manager" has trashed my installs for years.

Update Manager has never, ever, ever, **ever** trashed any of my systems - installs of versions that have been released, that is. Alpha/Betas and partial upgrades are, of course, another matter.

> **jerrylamos said:**
> Somebody tell me why Ubuntu Development continues to put out such a tool?

Because it works? :)

---

### Post by dino99 on 2011-07-12
Sadly devs cant purge bugs sat on chairs :(, and never been fixed :(

---

### Post by teh603 on 2011-07-12
> **coffeecat said:**
> Update Manager has never, ever, ever, **ever** trashed any of my systems - installs of versions that have been released, that is. Alpha/Betas and partial upgrades are, of course, another matter.Same here. I've had good luck with it, as long as I never tried a partial upgrade. I've actually had more problems with kpackagekit causing trouble with broken PPAs than Update Mangler.

---

