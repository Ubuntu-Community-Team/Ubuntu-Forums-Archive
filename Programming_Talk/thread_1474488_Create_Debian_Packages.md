---
title: "Create Debian Packages"
date: 2010-05-06
forum: Programming Talk
---

### Post by any.linux12 on 2010-05-06
Hello programmers!

I did today my first debian and I think it's amazingly easy to create the package. Then I created an apache server, made the tree and placed the Package file + the deb.

At first I had some problems with the directory tree and the Package file but now the only problem I have is the intalled-size as I get the error:

W: Failed to fetch [http://*******.dyndns.org/debians/dists/testing/***/binary-amd64/tcpfortuneclient.deb](http://*******.dyndns.org/debians/dists/testing/***/binary-amd64/tcpfortuneclient.deb)
  Size mismatch

First I tried to enter the size as it says in the debian doc page. I saw the size in the property windows and also used the command "du" but nothing did it. Then I read that the installed-size is not mandatory. Is that correct?

Can someone with more experience tell me how to do it?

Thanks

by the way. I forgot to say that it just doesn't work from the synaptic manager..if I have the deb locally it works just fine

---

### Post by gmargo on 2010-05-07
Are you generating the "Packages" file correctly? And regenerating it after changing the .deb file? It contains file size and checksums, so I suspect that's where the mismatch is coming from.

---

### Post by any.linux12 on 2010-05-07
> **gmargo said:**
> Are you generating the "Packages" file correctly? And regenerating it after changing the .deb file? It contains file size and checksums, so I suspect that's where the mismatch is coming from.

Hi!

sorry about the delay but I have been busy with other stuff.

I will post my Package file:
> 
Package: tcpfortuneclient
Version: 1.0
Section: TEST 
Priority: optional
Architecture: all
Filename: dists/testing/***/binary-amd64/tcpfortuneclient.deb
Maintainer: Ruben Rodrigues [ruben.rodrigues@***]
Description: Small TCP example programmed in QT and also my first attempt to create a debian package.

I removed the installed-size because I saw that was not mandatory but before I tried a lot of time and I always check that the install-size on the Package file was the same as that parameter on the control from the debian.

Can you tell me how to do the checksum? I can't find much about that and it's possible that it is the problem right here because I haven't set that.

Thanks

---

### Post by any.linux12 on 2010-05-07
hi again.

I already figured out how this works...it is a really good tool. In my opinion the best thing that ubuntu has against windows...

---

