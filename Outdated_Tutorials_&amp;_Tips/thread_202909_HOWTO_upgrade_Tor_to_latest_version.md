---
title: "HOWTO upgrade Tor to latest version"
date: 2006-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by shamael on 2006-06-24
The standard dapper repositories have an old version of tor (0.1.0.16) and it seems that it could take a while before we see an up to date one in there, so I suggest everybody who uses tor to read [this]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian") page of the tor wiki to get the latest stable.
They have i386 and amd64 debs for both dapper and breezy, while if you have something different just follow the steps on the bottom of the page. They worked on my PPC powerbook.

You might also want to read [this]("http://ubuntuforums.org/showthread.php?t=10825") thread for privoxy and tor configuration.

Happy anonymous surfing! :D

---

### Post by cbudden on 2006-06-24
Thanks for the link.  Make sure to add the gpg key otherwise you'll get apt-get errors.

---

### Post by cor2y on 2006-06-24
thanks for info but when i try to get the gpg key this is the error i get.

$ gpg --keyserver subkeys.pgp.net --recv 94c09c7f gpg: requesting key 94C09C7F from hkp server subkeys.pgp.net
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 5F skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2E skipped
gpg: invalid radix64 character 2D skipped
gpg: invalid radix64 character 3A skipped
gpg: invalid radix64 character 3B skipped
gpg: malformed CRC
gpg: read_block: read error: invalid keyring
gpg: Total number processed: 0

Anyone has an idea what is wrong?

---

### Post by cor2y on 2006-06-24
Ok it seems to have been the server itself just tried it again and it works

---

### Post by heman on 2006-06-25
Great!  Adding the dapper source seemed to work perfect.  Now, how do I install privoxy?

---

### Post by heman on 2006-06-26
Figured out how to install Tor / Privoxy in just 12-steps.  There's now a really crappy how-to on my blog:

[http://ubn00b.blogspot.com/2006/06/installing-torprivoxy-in-dapper.html](http://ubn00b.blogspot.com/2006/06/installing-torprivoxy-in-dapper.html)

---

### Post by shamael on 2006-06-26
> 
[http://ubn00b.blogspot.com/2006/06/i...in-dapper.html](http://ubn00b.blogspot.com/2006/06/i...in-dapper.html)

Hmm... you don't have to use the debian package for privoxy, 3.0.3 (latest) is in the ubuntu repos

Btw, I like QuickProxy for FF a lot, you might want to give it a try if you don't like TorButton

---

### Post by heman on 2006-06-26
[QUOTE=shamael]Hmm... you don't have to use the debian package for privoxy, 3.0.3 (latest) is in the ubuntu repos[/QUOTE]

Which repos is that in?  I'm just learning about the concept.  By default, privoxy doesn't seem to be available.  Also, what are the downsides to adding other repositories?  Which ones are most widely accepted?

---

### Post by shamael on 2006-06-26
I think Privoxy is in the universe repository, if you need help adding universe or multiverse you can read [this]("http://ubuntuforums.org/showthread.php?t=177905") very good post.

I don't know any downside in adding new repos besides probably a longer search time, so I think you should definitely enable universe and multiverse

---

