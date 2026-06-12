---
title: "Is the ISO supposed to be downloaded over https or http?"
date: 2020-04-15
forum: New to Ubuntu
---

### Post by kreaturesclone on 2020-04-15
When I go to download ubuntu: 
[https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64)

This page then redirects to a mirror to download ubuntu and https anywhere is telling me it's unencrypted

[I]HTTPS Everywhere noticed you  were navigating to a non-HTTPS page, and tried to send you to the HTTPS  version instead. The HTTPS version is unavailable. Most likely this  site does not support HTTPS, but it is also possible that an attacker is  blocking the HTTPS version. If you wish to view the unencrypted version  of this page, you can still do so by disabling the 'Encrypt All Sites  Eligible' (EASE) option in your HTTPS Everywhere extension. Be aware  that disabling this option could make your browser vulnerable to [network-based downgrade attacks]("https://en.wikipedia.org/wiki/Downgrade_attack") on websites you visit.
                 URL: [http://ubuntu-releases.cs.umn.edu/18.04.4/ubuntu-18.04.4-desktop-amd64.iso](http://ubuntu-releases.cs.umn.edu/18.04.4/ubuntu-18.04.4-desktop-amd64.iso)[/I]

So is it safe to download the ISO?

---

### Post by CatKiller on 2020-04-15
Works fine for me with HTTPS Everywhere, but then I probably don't get redirected to whichever mirror you do. You could try a different mirror, but BitTorrent would probably be better: each chunk gets checksummed that way.

---

### Post by SeijiSensei on 2020-04-16
I download ISOs from [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/) all the time. Never had a worry. If you're concerned about the integrity of the ISO image, you can calculate its MD5 or SHA1 signature and compare them to those on the download site.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

```

$ sha1sum focal-desktop-amd64.iso
e7698c3e1bc7e9de8a6644b06f17123d624db5ba  focal-desktop-amd64.iso

```

(This is not the signature for the current version of focal-desktop-amd64.iso. It changes every day until release.)

---

