---
title: "Strange instructions in verify ubuntu.iso tutorial?"
date: 2020-07-07
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-07
**Note: I use the names Ubuntu and Canonical interchangeably in the post below so there may be a couple of technical inaccuracies**

Hello everyone,

So as I said in my other thread, I downloaded the 20.04 .iso file the other day and burned it to a usb, but not before authenticating and checking the sha256 hash - which was all okay.

Today I've been going over the tutorial [found here]("https://ubuntu.com/tutorials/how-to-verify-ubuntu#1-overview") to get a better understanding of how it works, as I know a tiny bit about cryptographic hashes and gpg, but it's obviously very convoluted (by design I guess) and its still confusing when I come to dealing with it.

Basically on page 4 there is a section which to me seems to defeat the purpose of the authentication part, under the heading "if you don't have the keys..." which reads...

[B][I]"If there is no public key for Ubuntu already present, you will get an error message... this is actually a really useful message, as it tells us which key or  keys were used to generate the signature file. Knowing these ID numbers  (46181433FBB75451 and D94AA3F0EFE21092 in the example), means we can  request them from the Ubuntu key server"
[/I][/B]
Now I find this confusing as surely it undermines the whole process, because instead of acquiring a known good public key from Canonical and then using that to verify that the private key used to create the sha256 hash file's signature is the correct one, it instead suggest that the reader downloads the public key counterpart to *whatever* *private key was used to generate the signature file, *thus automatically assuming the signature was made by Canonical. This would mean that the signature is guaranteed to match when checked, regardless of who created it.

Is it not the case that a bad actor could just generate a key pair using a fake name and email that gave the impression it was an official Ubuntu key, modify Ubuntu to some malevolent end, distribute it along with a sha256 hash file signed with his new key and then when unsuspecting users download his illicit modified version and then verify it using the above advice, they would simply be fetching said bad actors public key and using that to verify the hash file was signed by his private key, all while believing they had actually just fetched the appropriate public key from canonical. They would then go on to check the hashes which would match (despite both being non-genuine) and be pleased as punch with the integrity of the .iso and simply install it.

I'm sure I'm wrong but I'd like someone to point out why please!

---

### Post by Holger_Gehrke on 2020-07-07
You might want to read the next bit of the instructions. It tells you:
> 
This is done with the following command. Note that the ID numbers are hexadecimal, so we prefix them with 0x:

gpg --keyid-format long --keyserver hkp://keyserver.ubuntu.com --recv-keys 0x46181433FBB75451 0xD94AA3F0EFE21092


This command tells gpg to download the keys with the given fingerprint from keyserver.ubuntu.com.  Who do you think controls keyserver.ubuntu.com ? An attacker would have to get control of this server and insert his key.

Holger

---

### Post by jcdenton1995 on 2020-07-07
But do the keyservers not hold lots of different keys? I thought anyone could upload their key to a keyserver?

Obviously I Realise uploading a public key called 'Ubuntu key' would be majorly suspicious.

---

### Post by Holger_Gehrke on 2020-07-08
Yes, you're right, the keyserver is public. In that case you can only follow the "web of trust". Each key can be signed by other keys (you can see the signatures by opening keyserver.ubuntu.com in a browser and entering the ID in the search field with a 0x prefix for hexadecimal; the output will show a list of the signatures on that key). By following the chain(s) of signatures until you find key(s) you trust you can establish the trustworthiness of a key. AFAIK gpg does that and will give different output depending on whether the trustworthiness of a key can be established or not. In theory people should only sign (and trust) keys they have personally checked by meeting the owner of the key in person and making certain of their identity (checking ID documents and key-fingerprint at a key-signing party, signing the key of a friend ...). pgp uses your personal keyring (and the trustworthiness you set for the keys on that ring) and tries to establish the trustworthiness of a key you tell it to use. If you don't have any keys you trust or there's no way to follow the chain of signatures from the used key to a key you trust then the signature is no better than a checksum. It establishes the integrity of the file but does not verify it's origin.

Holger

---

### Post by jcdenton1995 on 2020-07-08
Thanks. That explains a lot, and its an interesting system.

It still appears that the scenario I outlined in my original post is possible when the linked instructions are followed by a newbie like myself who likely wont understand how the system works as a whole and isn't aware of the web of trust.

The tutorial does touch briefly on countersigning the public key but basically says it doesn't matter don't worry about it.

Is it not reasonable to think that the tutorial should make it clear that there is some responsibility on the readers part to verify the authenticity of the signing key itself? Otherwise the solution is not 'water-tight' 

Dont get me wrong, I'm not complaining for myself as I think if one downloads the .iso, hashfile and signature file from the official Ubuntu website then there isn't too much to worry about, but not every person who follows the guide will have done that.

---

### Post by Holger_Gehrke on 2020-07-08
If I was paranoid enough and had no way of verifying the keys through the web of trust, I'd download the .iso through Bittorrent. Torrents have hashes for each and every block, piece - multiple blocks make up a piece, the number of blocks per piece depends on the size of the whole torrent and is configurable when setting it up - and file; as far as getting the file you want without any changes this is probably the best option; all torrent-clients check the sums during download; mismatching data - at any of the levels of hashing - gets discarded and peers who send mismatching data too often get banned on the client. Since the torrent is created by Canonical, the hashes in the torrent file should be correct.

 After downloading the iso I'd get the various checksums and signatures each from a different mirror. If I don't happen to pick a broken, out of date or hacked mirror for one of them, they should all agree. The probability of any attacker corrupting multiple mirrors and the torrent is rather small, I think.

Beside the set of instructions you linked to there's also a [page on the topic in the community wiki]("https://help.ubuntu.com/community/VerifyIsoHowto") which does at least mention the need to verify the keys and links to information on how to do that.

Holger

---

