---
title: "update query"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by bob74 on 2008-11-04
I today received the following message following update:-

W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve ‘playonlinux.botux.net’

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘playonlinux.botux.net’

W: Some index files failed to download, they have been ignored, or old ones used instead.

Could some kind person explain what I need to do, if anything. So far everything on Intrepid has worked OK for me so I am puzzled

---

### Post by EdThaSlayer on 2008-11-04
It seems that you are missing some of these "keys" that will allow you to fully access those files you are trying to download.

I recommend replacing your /etc/apt/sources.list with the one that [http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid) provides.I don't know which Ubuntu you use so you might have to just replace Intrepid with Hardy or any of the other names for the Ubuntu distro's.

However, with you I see that you are missing the keys to access the playonlinux database.

Type this in the terminal and it should theoretically work
> wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -

and then try

> sudo apt-get update


I don't know about your other problem though. Sorry :confused:

---

### Post by brian_p on 2008-11-04
> **bob74 said:**
> 

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve ‘playonlinux.botux.net’

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘playonlinux.botux.net’


user@laptop:~$ traceroute [http://playonlinux.botux.net](http://playonlinux.botux.net)
traceroute: unknown host [http://playonlinux.botux.net](http://playonlinux.botux.net)

playonlinux.botux.net cannot be found by the DNS. Your URL is possibly incorrect or the host has disappeared from the internet.

---

### Post by bob74 on 2008-11-05
Just in case you return to this post thanks for your quick responses. Unfortunately I haven't solved the problem and since I don't seem to have any related problems and the whole box of tricks  works OK I'll let well alone.
Thanks again
bob74

---

