---
title: "Update Error on ubuntu 13.04"
date: 2015-02-09
forum: New to Ubuntu
---

### Post by moutaman_elbadawi on 2015-02-09
Hello,
I am trying to update ubuntu using (sudo apt-get update), but every time i get this error.

Here is the result of the sudo apt-get update command:

```

Hit http://archive.canonical.com raring Release.gpg
Ign http://archive.ubuntu.com raring Release.gpg
Hit http://archive.canonical.com raring Release
Ign http://archive.ubuntu.com raring-updates Release.gpg
Hit http://archive.canonical.com raring/partner amd64 Packages
Ign http://archive.ubuntu.com raring-backports Release.gpg
Hit http://archive.canonical.com raring/partner i386 Packages
Ign http://archive.ubuntu.com raring-security Release.gpg
Ign http://archive.ubuntu.com raring Release
Ign http://archive.ubuntu.com raring-updates Release
Ign http://archive.ubuntu.com raring-backports Release
Ign http://archive.ubuntu.com raring-security Release
Ign http://archive.canonical.com raring/partner Translation-en_US
Ign http://archive.canonical.com raring/partner Translation-en
Err http://archive.ubuntu.com raring/main Sources     
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign http://archive.ubuntu.com raring/main Translation-en_US
Ign http://archive.ubuntu.com raring/main Translation-en
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/multiverse Translation-en
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en
Err http://archive.ubuntu.com raring-updates/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://archive.ubuntu.com raring-updates/main Translation-en
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://archive.ubuntu.com raring-updates/universe Translation-en
Err http://archive.ubuntu.com raring-backports/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-backports/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://archive.ubuntu.com raring-backports/main Translation-en
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://archive.ubuntu.com raring-backports/universe Translation-en
Err http://archive.ubuntu.com raring-security/main Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/restricted Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/universe Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/multiverse Sources
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/main amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/universe amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/main i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/restricted i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/universe i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Err http://archive.ubuntu.com raring-security/multiverse i386 Packages
  404  Not Found [IP: 91.189.88.149 80]
Ign http://archive.ubuntu.com raring-security/main Translation-en_US
Ign http://archive.ubuntu.com raring-security/main Translation-en
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-security/restricted Translation-en
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US
Ign http://archive.ubuntu.com raring-security/universe Translation-en
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/main/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W:  Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/restricted/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/raring/universe/source/Sources  404  Not Found [IP: 91.189.88.149 80]

W:  Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/universe/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-updates/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/universe/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-backports/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/main/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/source/Sources   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-amd64/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/universe/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/raring-security/multiverse/binary-i386/Packages   404  Not Found [IP: 91.189.88.149 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by slickymaster on 2015-02-09
Hi moutaman_elbadawi, welcome to the forums.

You're trying to update a Ubuntu version that is EOL since January 27, 2014, that's why you're getting those errors.

I advise you to upgrade to a supported release.
12.04.5 LTS : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)
14.04.01 LTS : [http://releases.ubuntu.com/14.04/](http://releases.ubuntu.com/14.04/)

---

### Post by Elfy on 2015-02-09
You could use [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) and change your sources to suit.

But to get to a supported release you would need to 13.04 > 13.10 > 14.04

You'll likely be better off backing up your data and doing a clean install to a supported version.

That is 14.10 and the 2 slickymaster mentions, 14.10 goes EOL in July so probably not a good idea.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

