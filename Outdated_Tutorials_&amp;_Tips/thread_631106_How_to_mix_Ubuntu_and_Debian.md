---
title: "How to mix Ubuntu and Debian"
date: 2007-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by evilgold on 2007-12-04
How to mix Ubuntu and Debian

Every now and then I'll want a version of somthing thats in debian testing or
unstable but not yet in ubuntu. 

I wrote this based on the info here: [http://moonbase.rydia.net/mental/blog/life/mixing-ubuntu-and-debian.html](http://moonbase.rydia.net/mental/blog/life/mixing-ubuntu-and-debian.html)
but i updated it and used slightly different method which i find to be a little simpler.

I have no idea how (un)safe/stable this could make a system, all i know is
it's worked fine for me on all of the systems i've done it with, YMMV. I've
only tried this using ubuntu 7.10, but there isnt really any reason why it 
wouldnt work on other versions.

Anyways on to the guide!

Open /etc/apt/sources.conf with your favorite editor and add these lines

```


deb http://ftp.us.debian.org/debian testing main non-free contrib
deb http://ftp.us.debian.org/debian unstable main non-free contrib


```

Next download and add the gpg keyring for debian. The latest version can 
always be found at [http://ftp-master.debian.org/](http://ftp-master.debian.org/) 

```

$ wget http://ftp-master.debian.org/archive-key-4.0.asc

```

```

$ gpg --import archive-key-4.0.asc
gpg: key 6070D3A1: "Debian Archive Automatic Signing Key (4.0/etch) <ftpmaster@debian.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

```

check the fingerprint (in this case 6070D3A1)

```

$ gpg --fingerprint 6070D3A1
pub   1024D/6070D3A1 2006-11-20 [expires: 2009-07-01]
      Key fingerprint = A999 51DA F9BB 569B DB50  AD90 A70D AF53 6070 D3A1
uid                  Debian Archive Automatic Signing Key (4.0/etch) <ftpmaster@debian.org>

```

then once your sure you have a good key, add it with:

```

$gpg --armor --export 6070D3A1 | sudo apt-key add -
OK

```

now edit/create /etc/apt/apt.conf and add the fallowing line:
(change to your ubuntu version if needed) This will tell apt to prefer the gutsy version of packages over debian packages,regardless of which is newer.

```

APT::Default-Release "gutsy";

```

Finally run apt-get update to finish up.

Now if you want to use a package from debian testing or unstable, use the
-t option to choose the version you want, like:

```

$ sudo apt-get install -t unstable packagename

```

or to fetch somthing from testing

```

$ sudo apt-get install -t testing packagename

```

---

### Post by bodhi.zazen on 2007-12-05
I have run mixed systems before and would caution that you need to do some reading first and be willing to manually review what is happening with your system when you do this. This means reviewing the changes suggested to the system when you use apt-get :twisted:

Please do not get the impression you can "mix and match" at will [-( . If you do this you should install the minimal packages from Debian (just because they are a .deb does not mean they are compatible across systems [-X ). And please do not give creed to the "works for me" philosophy :

> <bodhi_zazen> !worksforme
<ubotu> Common Sense: Just because you can, does not mean you should (and especially recommend to others). Think before you do. "Works for me" does not mean it is ok. The latest version of everything is not always useful if you aim for stability. Please see [http://geekosophical.net/random/worksforme/](http://geekosophical.net/random/worksforme/)

I also suggest you look at how to put a package on hold as well as pinning:

Hold : ```
echo *package* hold | sudo dpkg --set-selections
```

Release form hold: ```
echo *package* install | sudo dpkg --set-selections
```

Pinning :

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu](http://wiki.serios.net/wiki/Apt-Pinning_on_Ubuntu)

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

---

