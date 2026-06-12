---
title: "Bzr: &quot;Permission Denied&quot;"
date: 2010-03-17
forum: Programming Talk
---

### Post by Kenny_Strawn on 2010-03-17
How do I edit the permissions on a Launchpad project so that Bazaar is able to push to it?

This is the error I am getting:

[ATTACH]150450[/ATTACH]

I am using my Launchpad login (and I also created the project I am trying to push to), yet it still says "Permission Denied". Why?

I am trying to push to the branch from another machine, and yes, I still initialized the other machine and told Bazaar who I was and what my Launchpad login was. What the he!! am I doing wrong?

---

### Post by Kenny_Strawn on 2010-03-17
What's taking repliers so long?

---

### Post by snova on 2010-03-17
> **Kenny_Strawn said:**
> How do I edit the permissions on a Launchpad project so that Bazaar is able to push to it?

This is the error I am getting:

[ATTACH]150450[/ATTACH]

I am using my Launchpad login (and I also created the project I am trying to push to), yet it still says "Permission Denied". Why?

I am trying to push to the branch from another machine, and yes, I still initialized the other machine and told Bazaar who I was and what my Launchpad login was. What the he!! am I doing wrong?

Based on the error message, I would guess you haven't uploaded an SSH key to Launchpad, or bzr can't find the right one to use. Bazaar authenticates through them.

See [CreatingAnSSHKeyPair]("https://help.launchpad.net/YourAccount/CreatingAnSSHKeyPair") and [UploadingABranch]("https://help.launchpad.net/Code/UploadingABranch").

> **Kenny_Strawn said:**
> What's taking repliers so long?

Based on the fact that both of the posts I can see here are dated "1 Hour Ago", I would guess your patience.

---

### Post by Kenny_Strawn on 2010-03-17
Look here:

[https://launchpad.net/~mango-k/+editsshkeys]("https://launchpad.net/%7Emango-k/+editsshkeys")

I have three SSH keys: one for each project I created. And if I was able to push to the branch from my netbook, how come I can't do it from my desktop?

---

### Post by snova on 2010-03-17
> **Kenny_Strawn said:**
> Look here:

[https://launchpad.net/~mango-k/+editsshkeys]("https://launchpad.net/%7Emango-k/+editsshkeys")

I have three SSH keys: one for each project I created.

An SSH key is more like an identity; there's no reason to have that many keys. One will suffice.

> And if I was able to push to the branch from my netbook, how come I can't do it from my desktop?

My first thought is you didn't copy the key from one computer to the other. Any one of them should work.

Also, try editing ~/.ssh/config as the [UploadingABranch]("https://help.launchpad.net/Code/UploadingABranch") page describes.

And if all else fails, directly copying ~/.bazaar and ~/.ssh from the known-working computer would probably work.

---

