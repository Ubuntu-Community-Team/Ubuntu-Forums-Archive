---
title: "Where do I download the public key that is used to signed Ubuntu cdimages?"
date: 2013-06-13
forum: New to Ubuntu
---

### Post by regency on 2013-06-13
Hi,

I am new to Ubuntu but this much I know: all Ubuntu cdimages are signed by someone before they are uploaded to Ubuntu's servers and mirrors, am I right?

If that is the case, could someone tell me where I can download the public key used to sign the ISO images, especially 12.04.2 LTS (Precise Pangolin)?

The reason is I use Gpg4win 2.1.1 to verify the authenticity of downloaded ISO images on my Microsoft Windows platform before burning them to DVD or USB.

I try not to use MD5 checksums as MD5 has been compromised by hackers. My friends have advised me to trust and use SHA1 hashes instead.

N.B. There is a similar thread to my request here: [http://ubuntuforums.org/showthread.php?t=1993040](http://ubuntuforums.org/showthread.php?t=1993040). Unfortunately, it is closed.

---

### Post by slickymaster on 2013-06-13
[Verify Iso Howto]("https://help.ubuntu.com/community/VerifyIsoHowto#Obtain_the_public_key_from_the_Ubuntu_key_server")

---

### Post by regency on 2013-06-13
Thanks for the link.

However I wish to report some bizarre finding.

I imported the public key 0xFBB75451 into GPA of Gpg4win 2.1.1 successfully.

Next I issued the command:

C:\> gpg --verify e:\ubuntu\sha256sums.gpg e:\ubuntu\sha256sums

The result is a good signature.

The bizarre discovery is that the e:\ubuntu\ does **NOT** even contain any of the ISO (cdimage) files to be verified.

Apparently SHA256SUMS.gpg is being verified against SHA256SUMS and **NOT** the ISO.

What gives?

---

### Post by slickymaster on 2013-06-13
The GPG public key validates the integrity of the MD5SUMs file. The file MD5SUM contains MD5 hashes of the ISO images. Run md5sum on the ISO and compare the result with the relevant line in MD5SUM.

---

### Post by regency on 2013-06-13
Thanks for your help.

---

### Post by slickymaster on 2013-06-13
No need to thank me.
Please don't forget to mark the thread as SOLVED. Follow the link in my signature if you don't know how to.

---

