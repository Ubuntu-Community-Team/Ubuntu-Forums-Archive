---
title: "Laptop cutting out."
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Zerochilli on 2013-05-11
Hello,

I'm running ubuntu 13.04 64-bit and my laptop keeps cutting out in the middle of doing something it's really annoying, at first I thought it was overheating but it never happened on windows or linux mint or no other OS, just ubuntu any help would be appreciated.

Also how to install amd graphics drivers? Cuz It don't show up my driver on proprietary software :/. 

Thanks.:P

---

### Post by QIII on 2013-05-11
Hello!  Sorry you are having problems.  You're just lucky, I guess!  ;)

Could you better describe "cutting out"?  Is your machine crashing?  Freezing?  Do applications crash and the OS doesn't?

With regard to graphics drivers, could you give us some information about your graphics controller?

Thanks

---

### Post by Zerochilli on 2013-05-11
It just goes off completely no freezes no warnings nothing, just like a power cut it just goes off the OS is fine runs fine and everything. It's just this instant power off, I don't get any errors when I load back up either.

My graphics card is a AMD Radeon 3100. Sorry for less info :/.

---

### Post by QIII on 2013-05-11
Oh, boy.

I can say with pretty good confidence that the trouble is due to your graphics card and the version of Ubuntu you are using.

You can't find an additional driver for that card because there isn't one that will work with 13.04, so there is none in the repository for you to install.

AMD/ATI has moved all cards prior to the HD 5000 series to a legacy driver branch.   That means they are doing no more development on it.  Unfortunately, since then Ubuntu (among other Linux distros) moved to X Server 1.13 and the old driver will not work.  So, for Ubuntu, your card is unsupported by ATI for any version of Ubuntu from 12.04.2 onwards.  12.04 and 12.04.1 and previous are supported.

There is what is called the "legacy driver", but to use it requires that you downgrade X Server and patch the kernel.  While there were some people doing it to get 12.10 to work (and I advised against it), you are now on 13.04 -- yet another step along.  The reason I recommend against doing that is there is no way to predict what future consequences there may be in continuing forward with what is essentially a broken installation of Ubuntu.  We just don't know what a mess might be found with regard to dependencies and such as things are updated.

Anyway -- 

You are probably experiencing a thermal shutdown because without the ATI driver the GPU tends to heat up, which heats up everything else.  This is particularly true with APUs since the GPU and CPU are on the same die.

I can't tell you what to do, of course, but you might think about going back to 12.04 (but make sure you don't install 12.04.2).

Your card is still supported by an ATI driver that will work through 12.04.1 -- an LTS release that will be supported until 2017.

I wish I had better news.

Best wishes.

---

### Post by Zerochilli on 2013-05-11
Thanks for that.

When 14.04 comes out the next LTS Would I be able to use that? or would that be the same because I really like ubuntu :/.

Also could you offer a bit of help could I use lubuntu or is that the same as ubuntu 13.04 If It is ill have to use mint :/?

---

### Post by QIII on 2013-05-11
Unfortunately, that will not be the case.

The issue is ATI's support for that card.  Canonical, which produces Ubuntu, can do nothing about that.

Like I said, though, 12.04.1 will be supported until April, 2017.  That's four years to enjoy a supported version of Ubuntu with your current hardware.

13.04 is only supported for 9 months, by the way...  12.04 will still be going strong.

It isn't likely that you will find another distro that is based on 13.04 that does not use X Server 1.13.  Most distributors of derivatives are interested in modifying what is already available, not downgrading.

You might try Bodhi Linux, which is based on Ubuntu 12.04 and uses the Enlightenment desktop shell.  It may not be as configurable as a full DE, but it is very nice.  Bodhi Linux calls itself "semi-rolling", by which they mean that they will update their repos with newer versions of software when the Ubuntu repos are not updated -- but only if you installed with their installer.  Otherwise, the 12.04 repos are available.

---

### Post by Zerochilli on 2013-05-11
Ok thanks for your help, that is a shame ):P

---

### Post by pqwoerituytrueiwoq on 2013-05-11
[**[COLOR=#C61919][B]@QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")
how can 12.04.1 still support it and 12.04.2  not and 12.04.1 still be supported without installing the normal updates

the op may want to get a newer AMD gpu or or a nvidia gpu, or try debian stable

---

