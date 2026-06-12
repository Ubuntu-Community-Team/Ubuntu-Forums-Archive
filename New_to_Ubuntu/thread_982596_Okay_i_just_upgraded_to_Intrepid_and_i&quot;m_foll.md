---
title: "Okay i just upgraded to Intrepid and i&quot;m following this link:"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by robfindlay on 2008-11-14
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#ubuntu_intrepid_sources.list](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#ubuntu_intrepid_sources.list)

Added those repo's 

But I get an error when I try to execute this command: 

slag@slag-desktop:~$ wget -q [http://playonlinux.botux.net/pol.gpg](http://playonlinux.botux.net/pol.gpg) -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.


Then this error on gpupdate: 
W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/Release.gpg](http://playonlinux.botux.net/dists/hardy/Release.gpg)  Could not resolve 'playonlinux.botux.net'

W: Failed to fetch [http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2](http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'playonlinux.botux.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.


Obviously because I don't have the gpg key, does someone have an update link or can tell me if I even NEED that repo? 

TIA

Rob

---

### Post by jimmy the saint on 2008-11-14
wow, thats a lot of repos.  Unless you specifically need an app from the specific repo, you shouldn't add it.  For example, if you absolutely need an updated version of an app that is not available in Ubuntu's repos, then add the projects repo.  If you just add a big list of repos, every time you udate, who knows where it will come from.  This can be both a security risk and make your system usntable.  Plus who wants to wait around for an hour while the repos update!

You should just start out with the basic repos and maybe add medibuntu for some media and third party apps.  Other than that, just do it on a as needed basis.  The fewer the better I say!

---

