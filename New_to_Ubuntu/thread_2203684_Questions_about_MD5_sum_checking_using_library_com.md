---
title: "Questions about MD5 sum checking using library computer"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-02-04
I am presently using Ubuntu 12.04 LTS, which seems to work fine. I downloaded and burned a Ubuntu 12.04 LTS DVD using a library computer, but I did not check the MD5 sum after downloading; I was not that sophisticated. I downloaded from an approved North American mirror. I am using the library computer since they have much higher bandwidth that I do. (I have ~1.3 Mbps of download speed.) The library computers also have DVD burners and iso image burning software. I can only burn CDs.

**A post I read indicated I am taking a chance with security by using a Linux boot disk that has not had the MD5 sum checked.**

QUESTION #1: Do you think I should reburn a 12.04 LTS DVD that has had the MD5 sum checked for security purposes? 

If I do reburn such a DVD for the purposes of MD5 sum check, I would like suggestions as to how to do this: it seems to me that I could do it in a couple of ways: 

1) Download 12.04 LTS using the library's computer and check the MD5 sum using a Windows-based MD5 Sum checker on the library computer-- IF the library computers have such a Sum checker. If they do not have such a sum checker, then it will not be possible to install it unless the library wants to. 

2) Download 12.04 LTS using the library's computer, copy and paste the iso image file to my own hard drive (via a thumb drive) and check the MD5 sum using the Linux-based MD5 Sum checker on my own computer that is in the current version of Ubuntu 12.04 LTS. 

3) Download 12.04 LTS using my own computer (by hooking up to the library's wireless or ethernet cable internet) and check the MD5 sum using the  Linux-based MD5 Sum checker on my own computer that is in the current  version of Ubuntu 12.04 LTS. Then copy and paste the iso  image file to a library hard drive (via a thumb drive) for DVD burning.

For all of the above 1), 2) & 3), I would If the MD5 test is passed, I would burn the iso image to a DVD using the library's computer. I can burn my own CDs, (and I suppose there may be an iso image burner with Ubuntu 12.04 LTS or I may be able to download one). But I don't see a downloadable version of Ubuntu 12.04 LTS small enough for a CD. 

QUESTION #2: Does anybody have any comments or suggestions as to which of the above methods, or any other method, I should use to be sure my Ubuntu 12.04 LTS is secure?

BTW, I don't think I can boot off a thumb drive through a USB port. I think my computer is too old, circa early 2006. The boot options are 1)HDD, 2)CD/DVD 3)LAN and 4)FDD.

Thank you,

R.M.

---

### Post by Dave_L on 2014-02-04
You should be able to validate the existing DVD without downloading a new .iso.

Refer to the "Check the CD" section of [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by AbleTassie on 2014-02-04
Thanks Dave. It looks like a real possibility. 

QUESTION: I don't want to be too compulsive about the security issue, but is there any risk in having "the disk check itself?" That is, in having the MD5 checksum program in Ubuntu 12.04 that came originally from the DVD disk itself, go back an check the DVD (MD5 sum) in the DVD disk itself. 

Of course, in one of the methods I listed in my original post, I am using an MD5 checksum program that came from the same DVD (or a Windows checksum program on a library computer) to check a new downloaded copy of the iso file. So I guess there is a risk there too. 

Thanks,

RM

---

### Post by Dave_L on 2014-02-04
If you're checking the DVD from Windows, I would use a Windows MD5 utility for calculating it.

If you're doing it from Ubuntu, and you don't trust the source that provided the md5sum executable, you could extract the file /usr/bin/md5sum from one of the packages here: [http://packages.ubuntu.com/precise/coreutils](http://packages.ubuntu.com/precise/coreutils)

---

### Post by AbleTassie on 2014-02-04
Thanks Dave, it sounds like it could be complicated. My Windows XP is currently not functioning. And since the Windows File Checksum Integrity Verifier (FCIV)  is a command-prompt utility ([http://support.microsoft.com/kb/841290](http://support.microsoft.com/kb/841290)) I don't think I could use a library computer to use it. 

Sorry, I did not read your previous post closely enough. I would download the entire coreutils, extract the files and then use the file /usr/bin/md5sum file. The /usr/bin/md5sum file would it have to be installed after download and extraction, would it not?

Thanks,

RM

---

### Post by Dave_L on 2014-02-04
/usr/bin/md5sum is the one to use.

On reflection, though, if you can't trust the md5sum utility that's on the DVD, then you can't anything else, including the "stuff" that processes commands. So maybe using a separate md5sum utility on an untrusted system is pointless.

Maybe you can't trust me either. :)

---

### Post by Impavidus on 2014-02-05
MD5 sums are mostly meant to check for accidental errors in the DVD, caused either during download or whilst burning. These errors can cause all kinds of strange bugs. As your system seems to work fine, it's unlikely, although not impossible, such an error was present.

If you are concerned about security, yes, it is possible some evil entity replaced the .iso on the american mirror with a tweaked version containing a backdoor so that this entity can gain access to your computer. But I think that this entity would also be able to tweak the md5sum tool or modify the posted md5 sums so that you wouldn't detect it. The entity could even tweak the .iso in such a way that the md5 sum didn't change, as the md5 algorithm has been busted and isn't recommended for security purposes any more.

Keep in mind that I could be somebody hired by this evil entity trying to convince you that you shouldn't worry.

---

### Post by mastablasta on 2014-02-05
> **Impavidus said:**
> Keep in mind that I could be somebody hired by this evil entity trying to convince you that you shouldn't worry.

you shouldn't have revealed that.

anyway there is portable md5sum check software that can be run from thumbdrive (no need to install anyhting on library computer. in fact there are more programes like that in linux world. they are made to run directly from thumbdrive using only the OS. they dont' leave a trace on main computer after you close them as everything is done on thumbdrive. so you could use one of those on downloaded .iso

but as Impavidus said md5sum is mostly there to help you check for any download errors. using a torrent on your connection would download the iso overnight. well in a couple of hours. and torrent is checking md5sum on download.

---

### Post by Dave_L on 2014-02-05
Just noting that if you don't trust MD5, there are more secure alternatives (SHA1, SHA256) available for the Ubuntu releases:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

GPG signatures are also available there.

---

### Post by AbleTassie on 2014-02-06
> **Dave_L said:**
> Just noting that if you don't trust MD5, there are more secure alternatives (SHA1, SHA256) available for the Ubuntu releases:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

GPG signatures are also available there.

Thanks Dave. The Intel Desktop  CD release there does not seem to make a distinction between 64-bit and 32-bit. Is the release for both 32-bit and 64-bit?

Bob

---

### Post by AbleTassie on 2014-02-06
> **mastablasta said:**
> you shouldn't have revealed that.

anyway there is portable md5sum check software that can be run from thumbdrive (no need to install anyhting on library computer. in fact there are more programes like that in linux world. they are made to run directly from thumbdrive using only the OS. they dont' leave a trace on main computer after you close them as everything is done on thumbdrive. so you could use one of those on downloaded .iso

but as Impavidus said md5sum is mostly there to help you check for any download errors. using a torrent on your connection would download the iso overnight. well in a couple of hours. and torrent is checking md5sum on download.

Thanks MastaBlasta, that is good to know. Are the other more secure alternative signature utilities, as SHA as Dave mentioned in a later post, also available for use on a thumb drive?

Thanks,

Bob

---

### Post by Dave_L on 2014-02-06
> Thanks Dave. The Intel Desktop CD release there does not seem to make a distinction between 64-bit and 32-bit. Is the release for both 32-bit and 64-bit?

If you're talking about the items labelled "AMD64", those apply to Intel 64-bit as well as AMD.  I think the "AMD" label is just an old naming convention that was never changed.

---

### Post by AbleTassie on 2014-02-06
[SIZE=3]> **Dave_L said:**
> If you're talking about the items labelled "AMD64", those apply to Intel 64-bit as well as AMD.  I think the "AMD" label is just an old naming convention that was never changed.

No, that's not what I mean Dave. When I downloaded the file to burn the DVD for Ubuntu 12.04 LTS (that I am currently using) I had to choose either 64-bit or 32-bit. See drop down menu under "choose our flavour" at [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) . There was no single Ubuntu 12.04 LTS file that could be used for both 32-bit and 64-bit computers that I could see at the official Ubuntu website I downloaded from.

The webpage you cited does not have anything about a distinction between 32-bit or 64-bit files. And I assume SHA scores, MD5 scores/sums, etc. will differ between 32-bit files and 64-bit files. But there is only one score given for the files on the page you cited. I would need to use a 32-bit Ubuntu, so I am interested in the scores or sums for 32-bit Ubuntu OS files.

QUESTION: Am I missing something?

Thanks,

R.
[/SIZE]

---

### Post by Dave_L on 2014-02-06
The 32-bit Ubuntu .iso can be used on either a 32-bit or 64-bit computer. The 64-bit Ubuntu .iso can only be used on a 64-bit computer.

The files MD5SUMS, SHA1SUMS and SHA256SUMS at [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) contain the hashes for all the .iso, .xz and .exe files on that page.  They're plain text files, so you can view them to see what I mean.

---

### Post by deadflowr on 2014-02-06
You can find the hashes here
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

You need to look for the exact Ubuntu iso.
the desktop would be either ubuntu-11.11-desktop-amd64.iso or i386.iso
The key is the -desktop reference.
With Precise, you'll need to know which version or point release.

---

### Post by AbleTassie on 2014-02-06
[SIZE=3]> **Dave_L said:**
> The 32-bit Ubuntu .iso can be used on either a 32-bit or 64-bit computer. The 64-bit Ubuntu .iso can only be used on a 64-bit computer.

The files MD5SUMS, SHA1SUMS and SHA256SUMS at [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) contain the hashes for all the .iso, .xz and .exe files on that page.  They're plain text files, so you can view them to see what I mean.

OK Dave, I think I understand.** I think what you are saying is that the only downloadable i386 Desktop version of Ubuntu 12.04.4 LTS (Precise Pangolin; ubuntu-12.04.4-desktop-i386.iso)**[/SIZE]**[SIZE=3] on the [/SIZE]**[SIZE=3]**[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/) page is probably 32 bit, since it would work on both 32 & 64 bit machines and it is the only i386 desktop available there.** And links to text files for the MD5 Sum and SHA Sums, etc, for that [/SIZE][SIZE=3]Ubuntu 12.04.4 LTS (Precise Pangolin; ubuntu-12.04.4-desktop-i386.iso) [/SIZE][SIZE=3]are given [/SIZE]
[SIZE=3]on the [/SIZE][SIZE=3]http://releases.ubuntu.com/precise/ page.[/SIZE][SIZE=3] 

QUESTION: Is that correct? Perhaps "i386" means 32-bit (intel)?

Thank you,

R.

[/SIZE]

---

### Post by Dave_L on 2014-02-06
That's all correct.

ubuntu-12.04.4-desktop-i386.iso is 32-bit.  Sorry if I wasn't clear on that.

The link deadflowr posted also has the MD5's, but not the SHA1's or SHA256's.

---

### Post by mastablasta on 2014-02-07
AMD64 is 64 bit. the naming is there because AMD came out with 64 bit CPU's first. but AMD's are x86 (Intel) compatible. Or shoudl i say that in this case Inttel is comaptible with AMD. :-) more here: [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by AbleTassie on 2014-02-10
> **mastablasta said:**
> you shouldn't have revealed that.

**anyway there is portable md5sum check software that can be run from thumbdrive (no need to install anyhting on library computer. in fact there are more programes like that in linux world. they are made to run directly from thumbdrive using only the OS.** they dont' leave a trace on main computer after you close them as everything is done on thumbdrive. so you could use one of those on downloaded .iso

but as Impavidus said md5sum is mostly there to help you check for any download errors. using a torrent on your connection would download the iso overnight. well in a couple of hours. and torrent is checking md5sum on download.

How do I learn more about these md5sum check (and other more secure scores such as SHA scores or sums) that can be run from a thumbdrive? Do I need to have the Ubuntu operating system on the thumbdrive to determine the md5sum or SHA sum or score?

Thanks,

Bob

---

