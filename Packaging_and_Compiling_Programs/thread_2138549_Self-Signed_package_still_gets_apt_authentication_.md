---
title: "Self-Signed package still gets apt authentication warning"
date: 2013-04-24
forum: Packaging and Compiling Programs
---

### Post by tombert on 2013-04-24
I did create a gpg key using "gpg --gen-key", here is the listing:

    ```
> gpg --list-keys
    /home/<user>/.gnupg/pubring.gpg
    --------------------------------
    pub   2048R/99EDE0B7 2013-02-05
    uid                  Some Company
    sub   2048R/97337D10 2013-02-05

```

I exported the public key using:

    ```
> gpg --output key.pub --armor --export 99EDE0B7

```

I signed a deb package using:

    ```
> dpkg-sig --sign builder -k 99EDE0B7 mypackage.deb

```

I can verify the signing on the same controller:

```
> dpkg-sig --verify mypackage.deb 
    Processing mypackage.deb...
    GOODSIG _gpgbuilder 31C631682D8C1DC833576A283C9A9AA799EDE0B7 1366790488

```

I import the public key on a different controller:

```
> apt-key add key.pub
    OK
    > apt-key list
    /etc/apt/trusted.gpg
    --------------------
    pub   2048R/99EDE0B7 2013-02-05
    uid                  My Company
    sub   2048R/97337D10 2013-02-05

```

But when I verify the package on this new controller the signing is unknown:

```
> dpkg-sig --verify mypackage.deb 
    Processing mypackage.deb...
    UNKNOWNSIG _gpgbuilder 99EDE0B7

```

I must use "gpg --import" to actually verify the package:  

```
gpg --import key.pub

```

Then the verification works:

```
> dpkg-sig --verify mypackage.deb
Processing mypackage.deb...
 GOODSIG _gpgbuilder 980CDF084EC87D4C003E020C4B324EFB85743C26 1366872932

```

   But when using apt to install the package I get an authentication error:

```
> apt-get install mypackage
 Reading package lists...
 Done Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
   mypackage
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
 Need to get 0 B/12.0 kB of archives. After this operation, 0 B of additional disk space will be used.
 WARNING: The following packages cannot be authenticated!
   mypackage
 Install these packages without verification [y/N]?

``` 

And I can not figure out why :-(

thx!

---

### Post by tombert on 2013-05-02
I think I figured it out myself. apt does not check authentication on individual packages but only on the Release files.

---

