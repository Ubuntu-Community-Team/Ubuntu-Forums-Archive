---
title: "HOWTO revive your thunderbird (profile)"
date: 2005-07-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu_demon on 2005-07-07
Hi,

I had some troubles with thunderbird today so I wrote this howto.

go to ~/.mozilla-thunderbird  by :
$ cd ~/.mozilla-thunderbird
Write down the strange named directory for example : dgojgbe.default (this is your profile directory) 

Create a new profile (Thunderbird profile manager --> create)

go to ~/.mozilla-thunderbird  by :
$ cd ~/.mozilla-thunderbird

Now you'll see a new strange named directory for example aaap.default (this is the new profile)

Go to the written down strange named directory :
for example :
$cd dgojgbe.default

Now it's time to move your mail and settings back :

Copy your Mail and prefs.js to the new profile for example aaap.default  (that other stranged named directory) . 
for **example ** (you have to adapt it to your strange names):

```

$cp -R ~/mozilla-thunderbird/dgojgbe.default/Mail ~/mozilla-thunderbird/aaap.default

$cp ~/mozilla-thunderbird/dgojgbe.default/prefs.js ~/mozilla-thunderbird/aaap.default

```

Now start up the new profile. 

With a bit of luck you can get in again :).

---

