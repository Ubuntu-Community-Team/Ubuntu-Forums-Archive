---
title: "could not resolve “in.archive.ubuntu.com”"
date: 2013-07-19
forum: New to Ubuntu
---

### Post by Passiounto on 2013-07-19
**Passiounto** 					  		 			
			Hey,   i just bought new reliance broad band connection and like all the  above mentioned..am trying to get it using packages as mentioned by  you.I downloaded the package on desktop ,copied on my pendrive and  plugged in to my lap.I copied and extracted the files both  in Home  directory.when I open the terminal and say "sudo apt-get install wvdial"
 i get the following:
Reading package lists done&#8230; Done
Building dependency tree
reading state information..Done
the following extra packages will be installed:
libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras
the following new packages will be installed:
libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial
0 upgrade, 4 newly installed,0 to remove and 204 not upgraded
need to get 854kb of archives.
After this operation,2,699 kB of aditional  disk space willl be used.
Do you want to continue [y/n]? y
warning:the following packages cannot be authenticated!
libuniconf4.6 libwvstreams4.6-base libwvstreams4.6-extras wvdial
Install these packages without verification [y/n]?y
Err [http://in.archive.ubuntu.com/ubuntu/oneric/main](http://in.archive.ubuntu.com/ubuntu/oneric/main) libwvstreams4.6-base i3864.6.1-2build1
could not resolve &#8220;in.archive.ubuntu.com&#8221;
Err [http://in.archive.ubuntu.com/ubuntu/oneric/main](http://in.archive.ubuntu.com/ubuntu/oneric/main) libwvstreams4.6-base i3864.6.1-2build1
could not resolve &#8220;in.archive.ubuntu.com&#8221;
Err [http://in.archive.ubuntu.com/ubuntu/oneric/main](http://in.archive.ubuntu.com/ubuntu/oneric/main) libuniconf4.61-2build1
could not resolve &#8220;in.archive.ubuntu.com&#8221;
Err [http://in.archive.ubuntu.com/ubuntu/oneric/main](http://in.archive.ubuntu.com/ubuntu/oneric/main) wvdial i386 1.61-4
could not resolve &#8220;in.archive.ubuntu.com&#8221;
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-base) i3864.6.1-2build1
could not resolve &#8220;in.archive.ubuntu.com&#8221;Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libwvstreams4.6-) extras_4.6.1-2build1_i3864.6.deb could not resolve &#8220;in.archive.ubuntu.com&#8221;
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6.1-2build1_i386deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvstreams/libuniconf4.6_4.6.1-2build1_i386deb)  could not resolve &#8220;in.archive.ubuntu.com&#8221;Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.61-4_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/w/wvdial/wvdial_1.61-4_i386.deb)  could not resolve &#8220;in.archive.ubuntu.com&#8221;
E:unable to fetch some archives, maybe run apt-get update or try with &#8211;fix-missing?

 These are the erros I got..I feel that may be my downloaded package  WVdial_1.60.1_i386 and wvdial_1.61-4_i386..are not good ?so, pleae help  me..and also..should I be the &#8220;root&#8221; when I am installing?
PLEASE HELP ME..!!

---

### Post by mörgæs on 2013-07-19
Moved your post to a new thread. 
Please don't post in a thread if your question is not related to the original one.

---

### Post by newb85 on 2013-07-19
The package repositories for Oneiric are no longer hosted at that location because Oneiric is End-of-Life (no longer supported).  Please upgrade to a supported release (12.04 or newer).

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If you have any questions or problems, post them.

---

### Post by Impavidus on 2013-07-19
Checked that server, the oneiric and hardy repositories haven't been removed yet, although they haven't been updated since May (of course). All other old releases have been removed and they will soon too. The pool directory is there too. The error shows "could not resolve “in.archive.ubuntu.com”", old releases should give the error "404 Not Found", so it makes me think of a network problem. The last of the .debs that fail to be fetched downloads just fine on my computer.

That being said, oneiric is old and it would be best to upgrade (or clean install) to at least 12.04 LTS. That could solve your problem, whatever it is.

Also, I see it tries to load from the oneric directory on the server, not one**i**ric.

---

### Post by newb85 on 2013-07-19
That's odd.  It *is* giving me a 404 not found.

Good catch on the oneiric spelling.

I guess you should also check your DNS server, as I've had one give me fits with Ubuntu servers before.

```
ping in.archive.ubuntu.com
```

You may also want to switch to a different server.

Either way, it is still recommended that you upgrade to a supported release.

---

