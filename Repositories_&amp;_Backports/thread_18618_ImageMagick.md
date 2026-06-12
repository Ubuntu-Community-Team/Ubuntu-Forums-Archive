---
title: "ImageMagick"
date: 2005-03-07
forum: Repositories &amp; Backports
---

### Post by DudeMcGee on 2005-03-07
I read the before you post and I'm not sure whether or not Ubuntu supports imagemagick. When I do a apt-get imagemagick it comes back telling me 

```
"Depends: libmagick6 but 5:6.0.2.5-1ubuntu1.4 is to be installed"
```

Does that mean the imagemagick is not supported by ubuntu, and is there anyway I can get it to install. I just need it for one feature, but it's a pretty vital one.

Thanks,
DudeMcGee

---

### Post by WW on 2005-03-07
Yes, imagemagick is supported in ubuntu, and you should be able to install it with no problem.

Are you using warty or hoary?

Have you modified /etc/apt/sources.list, or have you modified your repositories by editing the Settings->Repositories in Synaptic?

---

### Post by DudeMcGee on 2005-03-08
I'm using warty. I modified the sources to include universe, not just main and restricted. I have libmagick6 5:6.0.2.5-1ubuntu1.4 installed.

Any ideas?

Thanks

---

### Post by Claus Cyrny on 2005-03-13
Hi,

I'm having the same problem :| ! While ImageMagick *does* show up in Synaptic, after selecting it I get the error message that the 'deb' file could not be downloaded. What can I do to solve this problem?  :-s

---

### Post by WW on 2005-03-13
In warty, the latest versions of imagemagick and libmagick6 are 5:6.0.2.5-1ubuntu1.4.  These are in the warty-security repository.  Do you have warty-security in your list of repositories?

---

### Post by Claus Cyrny on 2005-03-13
[QUOTE=WW]In warty, the latest versions of imagemagick and libmagick6 are 5:6.0.2.5-1ubuntu1.4.  These are in the warty-security repository.  Do you have warty-security in your list of repositories?[/QUOTE]

Yes, I have [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) for 'deb' and 'deb-src'. After selecting 'imagemagick' I get the message 'failed'. I added the 'universe' repositories today by uncommenting the two lines

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe 

in '/etc/apt/sources.list', but there I am getting two error messages as well ('file or directory not found').  :neutral:

---

