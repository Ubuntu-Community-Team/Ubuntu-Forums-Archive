---
title: "How to verify download?"
date: 2017-04-11
forum: New to Ubuntu
---

### Post by xipho2 on 2017-04-11
Hi, 

I was just about to download Ubuntu Desktop and read a lot about verification. The Ubuntu site says: "**Tip:** On non-Linux systems, you might need to download the GPG  tools for this next step. To check if you have the GPG tools installed,  run the command gpg --version or gpg2 --version."  I have Win7 and GPGtools seems to be for Mac. Can I do the same with  GPG4Win? The instructions on the Ubuntu site are a bit meagre, do you  know sites with step-by-step instructions? 
Someone posted this:
[https://www.reddit.com/r/linuxquestions/comments/55b9re/how_to_verify_ubuntu_server_download/](https://www.reddit.com/r/linuxquestions/comments/55b9re/how_to_verify_ubuntu_server_download/)
Fact or fiction?
Thanks for reading and suggestions.

---

### Post by leunam12 on 2017-04-11
why do you want to verify the download? Download the ISO file that you need, burn the image to a USB stick and boot it. If you experience installation problems you may want to verify the download as part of the troubleshooting process. If you want to verify now from Windows, download a file checksum verifier utility for windows. Microsoft provides one:

[https://www.microsoft.com/en-us/download/details.aspx?id=11533](https://www.microsoft.com/en-us/download/details.aspx?id=11533)

---

### Post by xipho2 on 2017-04-11
> **leunam12 said:**
> why do you want to verify the download? Download the ISO file that you need, burn the image to a USB stick and boot it. If you experience installation problems you may want to verify the download as part of the troubleshooting process. If you want to verify now from Windows, download a file checksum verifier utility for windows. Microsoft provides one:

[https://www.microsoft.com/en-us/download/details.aspx?id=11533](https://www.microsoft.com/en-us/download/details.aspx?id=11533)

Because of integrity and authenticity of the file. Verifying a checksum is simple-have you ever tried fingerprint, .sig, signature keys, WebofTrust? Not so trivial!
A good file prevents loosing time and temper with a damaged OS afterwards. Unless you are a professional who knows that a flaw is caused by a corrupt file and not something else. Therefore I posted it here: "New to Ubuntu".

---

### Post by TheFu on 2017-04-11
Another option.

At the boot of Ubuntu Desktop from any ISO, there is an option at the bottom to "Check media" - run that.  This is a common option for all desktop Linux distros.

In 20+ yrs of downloading and running Linux, I remember 1 time when the download wasn't valid. That was back in the 1990s.

I always validate at least 1 of the signatures. ALWAYS.

---

### Post by xipho2 on 2017-04-11
"Check media"-what is this doing-exactly?

---

### Post by oldos2er on 2017-04-11
> **leunam12 said:**
> why do you want to verify the download  

Why would you not?

---

### Post by RobGoss on 2017-04-11
You never know when a bad ISO file will slip threw, that is why they have the verification process in place just in case

---

### Post by mastablasta on 2017-04-13
to verify iso on Windows check this page 

[SIZE=2][https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


[/SIZE]under the title **MD5SUM on Windows**

---

### Post by mastablasta on 2017-04-13
> **TheFu said:**
> 
At the boot of Ubuntu Desktop from any ISO, there is an option at the bottom to "Check media" - run that.
.

is that Check disk for defects? because that one just check the disk, it doesn't match the hashes.

in any case downloading ISO with official torrent is safest. the hash is checked during download. so it Will be a good one when download is finished. but it is still good to check the hash, just to make sure no one tampered with the image.

---

