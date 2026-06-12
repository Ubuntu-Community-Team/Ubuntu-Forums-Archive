---
title: "No updating allowed if any sources &quot;untrusted&quot;"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by Horbo on 2012-12-20
I just wanted to update my system (where is the Update Manager in MATE btw?  I had to start it from the terminal because I couldn't find it) but because I have included the Steam repository the manager told me there were untrusted sources included, and cancelled ALL updates!

First, if I included Steam then I trust it, but what I'd really like to see is ALL THE OTHER UPDATES APPLIED! 
Fine, you don't trust a source (even if I do), but for crying out loud why on earth stop updates from all the other sources?

Makes absolutely no sense to me.

---

### Post by monkeybrain2012 on 2012-12-20
Install synaptic and use it for upgrading. With that you can choose what to upgrade. The update manager is not very flexible.

P.S. I don't know about steam but there is probably a gpg key that you forgot to import, hence the warning.

---

### Post by Horbo on 2012-12-20
I'm not 100% sure what you mean monkey, but Steam is definitely the problem (it is listed under Details when I get the "untrusted" message).
I don't know what a gpg key is or whether Steam has one or how to get it, but there was no mention of one where I saw the line to add the Steam repository.

Just a "warning" would be nice, but I don't think that's the right word: it shuts down the entire update.  Nothing is allowed to be updated...

---

### Post by monkeybrain2012 on 2012-12-20
> **Horbo said:**
> I'm not 100% sure what you mean monkey, but Steam is definitely the problem (it is listed under Details when I get the "untrusted" message).
I don't know what a gpg key is or whether Steam has one or how to get it, but there was no mention of one where I saw the line to add the Steam repository.

Just a "warning" would be nice, but I don't think that's the right word: it shuts down the entire update.  Nothing is allowed to be updated...
  Like I said, install the synaptic package manager either from the software centre or the terminal
```

sudo apt-get install synaptic
```

Then open synaptic from the dash,  click "Reload" on the top panel, then check for the updates (choose upgradable on the side panel)

With synaptic, you can choose what to update and in case of "untrusted repositories" it will still allow you to update after showing you the warning message.

It is more flexible than the update-manager and much faster than the Software Centre. I use it exclusively for installing and updating software.

I don't use steam so I don't know how the authentication works, but usually when you add a third party repository it will provide a gpg key for security and verification.

---

### Post by Horbo on 2012-12-20
I will definitely install synaptic, but I really think someone has made a dumb decision in Update Manager by refusing to allow any updates because of a single "untrusted" source.

Incredibly annoying.

---

### Post by mcduck on 2012-12-20
The error message might be a bit confusing here, it doesn't mean you (or Ubuntu's developers) wouldn't trust a certain software source, it means that you have added a repository but you didn't add the signing key used to verify that the packages you download really come from that source (to  prevent [man-in-the-middle]("http://en.wikipedia.org/wiki/Man-in-the-middle_attack") attacks).

Easy thing to solve, just add the missing signing key for the repository you added.

edit: Here are the terminal commands for adding the GPG key you are missing:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7
sudo apt-get update
```

---

### Post by oldos2er on 2012-12-20
You can add the gpg key by running these commands ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F24AEA9FB05498B7

sudo apt-get update
```

---

### Post by Horbo on 2012-12-20
Aaargh!

I've installed Synaptic, and clicked reload in it, but get this message, and of course Synaptic completely stops what it was doing (just skip it and keep going, please!):

**W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) quantal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8**

I only installed Quantal last night, apart from Steam I haven't messed with any repositories at all, what does this mean?
Why is a fresh install missing a gpg/key/signature?
Why couldn't it just ignore the problem and continue with the rest?

This is painful.

EDIT: McDuck and oldos2er, hadn't seen your posts before this one. You have both given different strings at the end of the first line, which do I use?  Will that give me all keys I'm missing, or just the Steam key?

---

### Post by monkeybrain2012 on 2012-12-20
> **Horbo said:**
> Aaargh!

I've installed Synaptic, and clicked reload in it, but get this message, and of course Synaptic completely stops what it was doing (just skip it and keep going, please!):

**W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) quantal InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8**

I only installed Quantal last night, apart from Steam I haven't messed with any repositories at all, what does this mean?
Why is a fresh install missing a gpg/key/signature?
Why couldn't it just ignore the problem and continue with the rest?

This is painful.

EDIT: McDuck and oldos2er, hadn't seen your posts before this one. You have both given different strings at the end of the first line, which do I use?  Will that give me all keys I'm missing, or just the Steam key?

Synaptic will continue if you just click yes.

---

### Post by oldos2er on 2012-12-20
The key given by myself and mcduck is for the Steam repo. The error you posted shows you need the Mate key too ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 68980A0EA10B4DE8

sudo apt-get update
```

---

### Post by Horbo on 2012-12-20
> **monkeybrain2012 said:**
> Synaptic will continue if you just click yes.

No, there's only a Close button... :-(

---

### Post by Horbo on 2012-12-20
> **oldos2er said:**
> The key given by myself and mcduck is for the Steam repo. The error you posted shows you need the Mate key too ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 68980A0EA10B4DE8

sudo apt-get update
```

Thanks oldos2er.  The Steam string you posted is truncated btw - McDuck's worked.

---

### Post by monkeybrain2012 on 2012-12-20
> **Horbo said:**
> No, there's only a Close button... :-(

Yeah you see that warning when you reload, you then close it, then click mark all upgrades (or check only those you want to upgrade) and click apply, it will give you a warning again, and you click yes and it will continue.

---

### Post by Horbo on 2012-12-20
> **monkeybrain2012 said:**
> Yeah you see that warning when you reload, you then close it, then click mark all upgrades (or check only those you want to upgrade) and click apply, it will give you a warning again, and you click yes and it will continue.

I'd have to say for me personally the sources/updating/upgrading is one of the most confusing parts of Ubuntu.

After adding those keys I've just now run "sudo apt-get update" and it seems to have completed fine, then immediately opened Synaptic and clicked "Mark Upgrades" (Reload was greyed out), followed the prompts, and it says 2 new packages will be installed, and 207 will be upgraded.

Are that terminal command and Synaptic doing two different things?  Is there a difference between update and upgrade?

If the solution to my problem was just a single command to fetch a listed key, I don't understand why apt-get/Synaptic doesn't just ask me if I want it to fetch the key when it comes up against that issue, and get it for me.

Would certainly make life easier for newbs.

EDIT: OT a bit, the Australian Ubuntu server is HORRIBLE.  Slow, and keeps dropping out.  I've had to switch over to the main one to stay sane - much, much better.

---

### Post by monkeybrain2012 on 2012-12-20
"update" means updating the database to determine the packages for which new versions are available. Upgrade means actually upgrading to new versions.

"sudo apt-get update" in the terminal is the same as "reloading" in synaptic. "sudo apt-get upgrade" means upgrading all packages for which new versions are available, it is the same as  clicking "mark all upgrades" then click "apply" in synaptic.

"sudo apt-get update x" in the terminal is the same as "checking the box beside package x in synaptic (for upgrade) and click "apply".

  gpg keys may be imported automatically or you may have to add them manually depending on the repository you add. I don't know if you are going to add many ppas, if you do there is a handy script call launchpad-getkeys (so that you don't need to remember the cryptic command that the others have just shown you in case for some reasons the gpg keys fail to import like it was back in 11.04 and 11.10) but you need to add a third party ppa to install it (webupd8) and it only works for ppas hosted by launchpad (don't know if steam is one of them)

---

### Post by Horbo on 2012-12-20
Thanks monkeybrain, very useful info.

---

### Post by vkadal on 2013-01-03
I just installed synaptic package manager and I could solve all my installation problems with respect Ubuntu12.04

---

