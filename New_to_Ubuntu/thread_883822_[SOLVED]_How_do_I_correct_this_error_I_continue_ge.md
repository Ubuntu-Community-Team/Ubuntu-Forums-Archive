---
title: "[SOLVED] How do I correct this error I continue getting in Synaptic?"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by ready4thebreak on 2008-08-08
This may be the wrong place to post this, but I am a beginner just looking for answers...

When I press reload in Synaptic, I keep getting this error, but I haven't the slightest clue as to how to correct this. 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263

Any help is greatly appreciated!

---

### Post by Joeb454 on 2008-08-08
Remove the Wine repository from your sources.list.

Go to System &#8594; Administration &#8594; Software Sources, then under the 3rd Party tab, remove the Wine entries :)

---

### Post by pedro_orange on 2008-08-08
I presume you added budgetdedicated to your apt list without adding a key.

Have a look in:

```
sudo nano -w /etc/apt/sources.list
```

You can either remove it, or add the key to verify it.
After you've done whatever you need to do; do an apt-get update.

---

### Post by ready4thebreak on 2008-08-08
ok I did what you said Joe! Thanks the error is gone. Now will that affect my Wine experience and what should I do if a Wine update comes out? Will I have to keep up with it on my own or something?

---

### Post by Oldsoldier2003 on 2008-08-08
> **ready4thebreak said:**
> ok I did what you said Joe! Thanks the error is gone. Now will that affect my Wine experience and what should I do if a Wine update comes out? Will I have to keep up with it on my own or something?

See [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) for adding the winehq repos. Basically you just needed to add the gpg key. 

edit: Personally I agree with joes advice to remove the repo but if you are wanting the latest greatest version of wine, then this is the way to go

---

### Post by ready4thebreak on 2008-08-08
ok wait now I'm a bit scared.  I get this now that I try to go to Synaptic or Software Sources and Add/Remove Applications is frozen(which may be causing this error message?)

Failed to run /usr/sbin/synaptic as user root.

Unable to copy the user's Xauthorization file.

---

### Post by Dylock on 2008-08-08
Are you trying to run Synaptic and another package manager at the same time? If so I think this causes problems with some sort of 'locking' mechanism. *shrug*

---

