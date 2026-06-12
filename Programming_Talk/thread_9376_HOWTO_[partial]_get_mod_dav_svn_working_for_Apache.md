---
title: "HOWTO: [partial] get mod_dav_svn working for Apache 2 and Subversion 1.0.6"
date: 2004-12-28
forum: Programming Talk
---

### Post by offby1 on 2004-12-28
This is VERY limited, just a few pointers in the right direction.

First, you need to install both Apache and Subversion.  Ideally you'd be custom building these, but I'm not sure how to do custom builds of packages on Ubuntu (I can do it from tar, but A) I'm an RPM expatriate and B) the dpkg thing just doesn't click for me.  I'd love to see an upgrade to this that does work with the .deb files instead, using apt-get source and proper building.)

Next, in $HOME do:
```

mkdir ${builddir}
cd ${builddir}
apt-get source subversion
sudo apt-get build-deps subversion
cd subversion-1.0.6/
tar zxf subversion-1.0.6.tar.gz
cd subversion-1.0.6/
./configure --with-ssl --with-apxs=/usr/bin/apxs2
make

```

Now you should have mod_dav_svn.so in
```

./subversion/mod_dav_svn/.libs/mod_dav_svn.so
./subversion/mod_authz_svn/.libs/mod_authz_svn.so

```

These should be copied to /usr/lib/apache2/modules and chmod -x'd

Then, they should be configured (I'm not too clear on the config model used in Ubuntu's Apache2 install -- there's modules.enabled in /etc/apache2, but as to what it's doing there, I don't know)

That's where you come in, folks -- I have them built, now someone who knows more than I do can tell me how to configure them :)

---

