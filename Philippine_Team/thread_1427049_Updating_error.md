---
title: "Updating error"
date: 2010-03-11
forum: Philippine Team
---

### Post by samantha on 2010-03-11
Masters,

Good day, i encounter this error when updating thru terminal respository out of order ba eto?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EF4186FE247510BE

TIA

---

### Post by samantha on 2010-03-11
problem solve, please delete this entry. TIA

:popcorn:

---

### Post by licotto on 2010-10-10
Well, how did the problem get solved??? It's not 'solved' on the forum unless you explain how it got solved...

I am having these exact issues and mine is not magically solved! haha

Please help!

---

### Post by neehs on 2010-10-10
Code:

gpg --keyserver keyserver.ubuntu.com --recv 0c713da6

Code:

gpg --export --armor 0c713da6 | sudo apt-key add -

Do the same for the other key...
Last 8 digits...

I've just google it.

---

### Post by topet2k12001 on 2010-10-23
The help/how-to guide is actually in the PPA page itself. You will see this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=173321&stc=1&d=1287873647[/IMG]
When you hover your mouse on "What is this?", a window will open. This is how it looks like: [https://launchpad.net/+help/soyuz/ppa-sources-list.html](https://launchpad.net/+help/soyuz/ppa-sources-list.html)

Hope this helps. :)

---

