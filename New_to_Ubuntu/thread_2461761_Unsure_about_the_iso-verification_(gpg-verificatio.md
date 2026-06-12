---
title: "Unsure about the iso-verification (gpg-verification)"
date: 2021-05-06
forum: New to Ubuntu
---

### Post by fj7hUtJ83S@ on 2021-05-06
Hello community,

I'm really looking forward to try (K)ubuntu but I've got a problem with understanding the verification of the iso... 

In general I understand what I have to do:

1) download iso, sha256 and gpg-file
2) then verify the sha256-checksum-file with help of the gpg file
3) then verify the iso file with the sha256-checksum-file

I'm using these instructions: [https://ubuntu.com/tutorials/how-to-verify-ubuntu#5-verify-the-sha256-checksum](https://ubuntu.com/tutorials/how-to-verify-ubuntu#5-verify-the-sha256-checksum)

After adding the server-keys to my "keyring" (step 4), I type "gpg --keyid-format long --verify SHA256SUMS.gpg SHA256SUMS.txt" in the console to verify the checksumfile. My output is something like this:

"gpg: Signature made 01.04.2021 18:12:56 Mitteleuropäische Sommerzeit                    using RSA key ID D94AA3F0EFE21092
gpg: Good signature from "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" [unknown]
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092"

This seems good to me... _But:_ I only get the verification for this one "RSA Key ID D94...." In the Description theres another second "DSA key ID 46..." in the output-message. Another description I found also says that I have to check the _two_ "Good Signature from..." Messages.
Why don't I get the OK for both keys? Is my file okay? I added both keys to my "keyring" like in the description before... Why are there two btw?

Btw I tried it with Ubuntu and Kubuntu 20.04.2 LTS.

Thanks a lot for your support and excuse my english. Its not my home-language.

Cheers

Thanks a lot

---

### Post by Xian on 2021-05-06
It just means the mostly deprecated DSA key was not used for verification. 
DSA keys were provided on Trusty but [soon] afterwards no longer used.

The tutorial you reference does correctly state (my emphasis):
"...tells us **which key or keys** were used to generate the signature file."

So in this case it is the RSA key.

---

### Post by fj7hUtJ83S@ on 2021-05-07
Great. Thank you!

So this one key is sufficient, and tells me, that the checksum file is correct and original, right?

And just to make sure, that I understood the last step correctly: In the last step (6) I compare the checksum in the checksum-file with the checksum of the iso. The command "sha256sum -c SHA256SUMS 2>&1 | grep OK" doesn't work. Probably because the program sha256sum is missing. Is it also a possible way to use the command "get-filehash ubuntu......iso" in windows powershell? My output then is a sha256 checksum.
When my output checksum then matches with the checksum in the checksum-file, it's safe!?


Thanks again. After this info the topic is solved.

---

### Post by Dennis N on 2021-05-07
There is also a little utility named **GtkHash** that does all the work.

---

