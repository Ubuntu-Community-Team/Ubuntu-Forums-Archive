---
title: "Keyring change = cannot login"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by Ajantis on 2013-03-27
Hi everyone!

I have encountered a pretty nasty problem recently. I played a bit with Ubuntu Keyring (didn't really pay attention to that before) app and I must have screwed up something with passwords... I had this "Local" (or whatever it is called) key base with some of my ftp passwords. Next to it I saw an icon with unlocked padlock. I clicked on it and the icon changed into locked padlock. I wanted to unlock it again to get access to my passwords and I guess I can do that with my Ubuntu user password, but sadly for no avail... The password is wrong. When I rebooted my machine, I couldn't log in to my Ubuntu account.

I launched live cd and changed my user password, now I can log in, but unfortunately, my home is encrypted and I can't see my files...

Some time ago I changed my user password, does that have anything to do with it?

Oh yeah, and I forgot my passphrase :(

Is all my data lost, or perhaps a kind soul could lend me a hand with this problem?

---

### Post by DuckHook on 2013-03-28
Oh my. This is not looking good. No passphrase is, well... not good.

There is only one thing you can try. I'm assuming that you used the native encryption tools that came with your install. Do:```
ecryptfs-unwrap-passphrase /home/username/.ecryptfs/wrapped-passphrase
```where "username" is replaced by your username. Type your old login passphrase (not the new one that you recently created) to reveal the mount passphrase. If you get your passphrase, make an offering to whichever computing gods you worship and *write it down*. If this doesn't return your passphrase, you are simply out of luck and it is impossible to recover your data.

Let's get this step out of the way first before proceeding to the next. You should look over [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory") how-to, but everything is dependent on recovering your passphrase.

---

