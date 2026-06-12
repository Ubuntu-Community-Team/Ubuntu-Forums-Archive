---
title: "Using VLC contribs."
date: 2014-03-07
forum: Packaging and Compiling Programs
---

### Post by ron998 on 2014-03-07
Hi
When building VLC using contrib method, it's documented...
Here ---> [https://wiki.videolan.org/UnixCompile/#The_.22Contrib.22_method](https://wiki.videolan.org/UnixCompile/#The_.22Contrib.22_method)
```
% mkdir native
% cd native
% ../bootstrap
% make
```
But doing this, it compiles a whole bunch of libs.

Is it possible to pick and choose?

For example, if gnutls is needed (because Ubuntu's is too old).
Could I compile only gnutls from contribs?

[COLOR=#ff0000]**_EDIT_**[/COLOR]
gnutls needs nettle, and nettle needs gmp.
So I'd need to build gmp then nettle then gnutls. :-?

---

### Post by andrew.46 on 2014-03-08
I have never really looked at using the contribs (although I pillage the rules.mak files for the options that the vlc developers use!) but if you run *make list* there should be a list of available packages. For gnutls you should be able to then simply run *make gnutls* to compile only gnutls, but as you have mentioned you will need to have all the appropriate -dev files preinstalled... Might be just as easy to compile your own or simply wait for Trusty!

Beyond that I am no more help I am afraid :(. Looks like make only downloads the files, patches them and places them in native, perhaps the vlc compile process looks here and compiles?

---

