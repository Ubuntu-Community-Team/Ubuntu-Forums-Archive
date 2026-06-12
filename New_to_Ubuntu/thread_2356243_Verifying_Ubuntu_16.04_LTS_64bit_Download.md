---
title: "Verifying Ubuntu 16.04 LTS 64bit Download"
date: 2017-03-21
forum: New to Ubuntu
---

### Post by westone2 on 2017-03-21
Can someone please explain in simple terms where to find the Check Sum for this and then using this how to run the process for verifying the integrity of the Download. I need to be certain as I am installing on a new laptop. The main Ubuntu download page does not indicate any check sum.
Thanks
westone2

---

### Post by slickymaster on 2017-03-21
Download page: [http://releases.ubuntu.com/16.04/](http://releases.ubuntu.com/16.04/)

MD5SUMS page: [http://releases.ubuntu.com/16.04/MD5SUMS](http://releases.ubuntu.com/16.04/MD5SUMS)

How to use MD5SUM page:[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by howefield on 2017-03-21
For 16.04.2 Go [here]("http://releases.ubuntu.com/16.04.2/") and download the checksum file that you want, eg right click on the SHA256 and select save link as... save the file to the same folder as your Ubuntu iso download. Then from a terminal, navigate to where you have stored the files and use..

```
sha256sum -c SHA256SUMS 2>&1 | grep OK
```

the output should look something like this..

```
sha256sum -c SHA256SUMS 2>&1 | grep OK
ubuntu-16.04.2-desktop-amd64.iso: OK
```

That is about as simple as it gets, but that is for 16.04.2.. if it is 16.04 or 16.0.1 the link to the SHA256SUMS would be different ?

The same command would work for the MD5SUM file if you prefer that..

```
md5sum -c MD5SUMS 2>&1 | grep OK
ubuntu-16.04.2-desktop-amd64.iso: OK
```

And this is for checking the veracity of the iso from Ubuntu, which I'm assuming that you are using.

---

### Post by westone2 on 2017-03-21
Thanks Slickymaster and Howefield. Are MD5SUMS and SHA256SUMS different algorithms for doing the same thing? I'm now busy for a few days but I hope to have got this sorted by the end 
of the week.
westone2

---

### Post by slickymaster on 2017-03-21
> **westone2 said:**
> Thanks Slickymaster and Howefield. Are MD5SUMS and SHA256SUMS different algorithms for doing the same thing? I'm now busy for a few days but I hope to have got this sorted by the end 
of the week.
westone2

Long story short, yes. The primary difference between between them is that MD5 produces a 128-bit output while SHA-256 produces a 256-bit output.

---

### Post by Mark_in_Hollywood on 2017-03-23
I like:

[https://apps.ubuntu.com/cat/applications/precise/gtkhash/](https://apps.ubuntu.com/cat/applications/precise/gtkhash/)

a GUI that has sha256, sha1 and md5.

---

