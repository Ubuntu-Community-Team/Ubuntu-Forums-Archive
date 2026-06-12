---
title: "Problem updating 7.04 to 7.10"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by aarondesk on 2008-08-15
I'm sort of a newbie. I'm trying to upgrade 7.04 to 7.10. I keep getting the following error messages.

[I]Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Release.gpg](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Release.gpg) Could not resolve 'my.favorite.cran.mirror'

Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/en_US.bz2](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/en_US.bz2) Could not resolve 'my.favorite.cran.mirror'

Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Packages.gz](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Packages.gz) Could not resolve 'my.favorite.cran.mirror'[/I]


I gather this means some repositories are not setup correctly, right? 

Could someone help me out and pointing me in the right direction on how to fix this. Do I need to edit /etc/apt/source.list and add some repositories or something?

Thank you,

Aaron

---

### Post by vikramaditya on 2008-08-15
try...
```
sudo apt-get update
```
worked for me on broken repos.

---

### Post by aarondesk on 2008-08-16
Hmm...
  I ran that command it and it looked like it ran some commands, trying to update the repositories. 

I had a few error messages.

[I]Err [http://my.favorite.cran.mirror](http://my.favorite.cran.mirror) feisty/ Packages
  Could not resolve 'my.favorite.cran.mirror'
Fetched 8B in 3s (3B/s)
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Release.gpg](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Release.gpg)  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/en_US.bz2](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/en_US.bz2)  Could not resolve 'my.favorite.cran.mirror'
Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Packages.gz](http://my.favorite.cran.mirror/bin/linux/ubuntu/feisty/Packages.gz)  Could not resolve 'my.favorite.cran.mirror'
[/I]

So it looks like I'm still having problems with these repositories. I tried updating to 7.10 again, but I received the same error messages.

There must be alternative sources than these one, right? Any idea where these are and how I can update them?

I should mention that my system was originally Ubuntu, but I've added on the Kubuntu and Xubuntu extensions, but I don't know if that makes a difference. These packages that are giving problems don't seem flavor specific.

Thanks again,
Aaron

---

### Post by aarondesk on 2008-08-16
Ok, these lines are in my /etc/apt/sources.list that I'm guessing are the problems.

[I]deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) feisty/
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
[/I]

So, I'm guessing that these repositories are kapoot. Are there alternative ones I can use? Where would I even find such information?

---

