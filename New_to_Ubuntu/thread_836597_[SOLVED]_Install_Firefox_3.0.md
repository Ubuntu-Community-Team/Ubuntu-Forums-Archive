---
title: "[SOLVED] Install Firefox 3.0?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by dalezjc on 2008-06-21
I've tried installing Firefox 3.0 both from Synaptics Manager and from the command line (sudo aptitude install Firefox-3.0) but both install Firefox 3 Beta 4.  

I've also downloaded firefox-3.0.tar.bz2, but I don't know how to install this.

Any help is appreciated.

Dale

---

### Post by drs305 on 2008-06-21
> **dalezjc said:**
> I've tried installing Firefox 3.0 both from Synaptics Manager and from the command line (sudo aptitude install Firefox-3.0) but both install Firefox 3 Beta 4.  

I've also downloaded firefox-3.0.tar.bz2, but I don't know how to install this.

Any help is appreciated.

Dale

You can get the Firefox 3.0 'final' version from the repositories. Just make sure the 'hardy-updates' block is ticked in the Synaptic, Settings, Respositories, Updates. (If you are using hardy. If it's a previous version, look for the applicable setting.

---

### Post by mivo on 2008-06-21
Are you using Gutsy still?

---

### Post by dalezjc on 2008-06-21
> **drs305 said:**
> You can get the Firefox 3.0 'final' version from the repositories. Just make sure the 'hardy-updates' block is ticked in the Synaptic, Settings, Respositories, Updates. (If you are using hardy. If it's a previous version, look for the applicable setting.

I look there and the update checkbox is selected.

Dale

---

### Post by dalezjc on 2008-06-21
> **mivo said:**
> Are you using Gutsy still?

Yes.

---

### Post by mivo on 2008-06-21
3.0 final isn't in the Gutsy repository yet. I imagine it will be added eventually. I'm not sure there's a backport available. Another alternative is to upgrade to Hardy.

---

### Post by drs305 on 2008-06-21
Composed while previous entries were being typed. This post applies only to hardy... 

On my system, the beta is still listed in the main hardy repository and if I select 'firefox' or 'firefox-3.0' it is shown as being in the hardy updates repository. The version is listed as 3.0+nobinonly-0ubuntu0.8.04.1

You might try reloading synaptic to refresh it or try a different repository (although I would expect they all have the FF3 release by now). To change repositories: synaptic, settings, repositories, Download From > click on the selected server, choose Other, then select another server.

mivo, how did you know he was using gutsy?

---

### Post by Foster Grant on 2008-06-21
> **mivo said:**
> 3.0 final isn't in the Gutsy repository yet. I imagine it will be added eventually. I'm not sure there's a backport available. Another alternative is to upgrade to Hardy.

I'm not planning to do that until 8.04.1 drops later this summer.

Is there a "backdoor" way to do it?

---

### Post by dalezjc on 2008-06-21
> **drs305 said:**
> Composed while previous entries were being typed. This post applies only to hardy... 

On my system, the beta is still listed in the main hardy repository and if I select 'firefox' or 'firefox-3.0' it is shown as being in the hardy updates repository. The version is listed as 3.0+nobinonly-0ubuntu0.8.04.1

You might try reloading synaptic to refresh it or try a different repository (although I would expect they all have the FF3 release by now). To change repositories: synaptic, settings, repositories, Download From > click on the selected server, choose Other, then select another server.


I tried various other servers, but they all have just the beta version.  But I've downloaded the tar.bz2 file from Mozilla's site.  How do I install this?

Dale

---

### Post by drs305 on 2008-06-21
> **dalezjc said:**
> I tried various other servers, but they all have just the beta version.  But I've downloaded the tar.bz2 file from Mozilla's site.  How do I install this?

Dale

I wrote my response before becoming aware you were using gutsy. Although I recommend waiting for FF3 to get to the repositories, here is a link on how to compile from source:

[URL="https://help.ubuntu.com/community/CompilingSoftware"]	ubuntu.com/community/CompilingSoftware
[/URL]

---

### Post by dalezjc on 2008-06-21
> **drs305 said:**
> I wrote my response before becoming aware you were using gutsy. Although I recommend waiting for FF3 to get to the repositories, here is a link on how to compile from source:

[URL="https://help.ubuntu.com/community/CompilingSoftware"]	ubuntu.com/community/CompilingSoftware
[/URL]

Yikes!  I think I'll wait till it shows up in the repository.

Thanks,
Dale

---

### Post by Foster Grant on 2008-06-21
> **dalezjc said:**
> Yikes!  I think I'll wait till it shows up in the repository.

Thanks,
Dale

I started poking around on that page and found something interesting.

If you have gutsy-backports enabled in apt/Synaptic, FF3 is available. :)

EDIT:

Sort of. It's Beta 4. :(

---

### Post by aysiu on 2008-06-21
If you're using Ubuntu 7.10 (Gutsy Gibbon) and already have the .tar.bz2 downloaded to your home directory, follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).

If you're using Ubuntu 8.04 (Hardy Heron), go to System > Administration > Software Sources, and make sure the Hardy *proposed updates* repository is checked (I think it's the second or third tab), click Reload, use Update Manager to check for and install updates for Firefox only. Then go back to Software Sources and uncheck the proposed updates.

---

### Post by dalezjc on 2008-06-21
> **aysiu said:**
> If you're using Ubuntu 7.10 (Gutsy Gibbon) and already have the .tar.bz2 downloaded to your home directory, follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).


Perfect!  I followed the instructions and now I'm running FF 3.0.

Thanks!!

Dale

---

### Post by Foster Grant on 2008-06-21
> **aysiu said:**
> If you're using Ubuntu 7.10 (Gutsy Gibbon) and already have the .tar.bz2 downloaded to your home directory, follow [these instructions](http://www.psychocats.net/ubuntu/firefox#terminal).

This works.

Note to Canonical: It's perfectly acceptable to put current software in repositories for distributions you still support.

---

### Post by tarpon_bill on 2008-07-07
I haven't done anything with backports before, so a couple of simple questions ... I am not sure what backports are.

Is there any known problems with FF3 from the backports for Gutsy? 

If you wanted to go back to FF2 is that possible? 

Can the two versions FF3 and FF2 be run on the same machine?

Thanks in advance ... Bill

---

