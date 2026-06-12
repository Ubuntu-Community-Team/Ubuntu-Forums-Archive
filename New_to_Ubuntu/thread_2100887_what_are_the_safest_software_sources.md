---
title: "what are the safest software sources?"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by iMac71 on 2013-01-03
after having read [post=12434950]this post[/post] and visited [this site]("https://sites.google.com/site/easylinuxtipsproject/fatalmistakes") I'm a bit confused: what are the safest software sources that I can use/enable without risks or at least with few risks? It seems to me that I can enable the backports ones, the partners ones and the independent ones.

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> It seems to me that I can enable the backports ones, the partners ones and the independent ones.
Correct. :)

Of course there are also other safe repo's like the Google Chrome repo, the Duinsoft repo (Java) and the Dropbox repo. But in general, external repo's have to be treated with caution. Especially PPA's.

---

### Post by iMac71 on 2013-01-03
> **Pjotr123 said:**
> Correct. :)

Of course there are also other safe repo's like the Google Chrome repo, the Duinsoft repo (Java) and the Dropbox repo. But in general, external repo's have to be treated with caution. Especially PPA's.even transmissionbt and libreoffice ppas should be considered dangerous? They are the only ppas I use.

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> even transmissionbt and libreoffice ppas should be considered dangerous? They are the only ppas I use.

Not all PPA's are equally risky, of course.... But I'd only use those if I had a good reason for it. For example a genuine problem with the LibreOffice version and the Transmission version in the official repo's, which would only be solved by using those PPA's.

In the end it pays when you learn to treat your system like a careful system administrator, at least on your production machines and other important computers. What you do on your test machines and non-essential "play boxes" is quite another cup of tea, naturally... :)

---

### Post by zombifier25 on 2013-01-03
> **iMac71 said:**
> even transmissionbt and libreoffice ppas should be considered dangerous? They are the only ppas I use.
Yep. Remove them right now or sooner or later they'll get to yer children.

Just kidding, the trustworthiness of a PPA is basically the same to the trustworthiness of a Windows application you download from the web. Stick to the popular PPAs made by trustworthy people (your LibreOffice PPA, for example), and they should probably be covered by a major news blog (e.g. OMG!Ubuntu)

I have yet seen a PPA made with malevolent intentions though.

---

### Post by Pjotr123 on 2013-01-03
> **zombifier25 said:**
> I have yet seen a PPA made with malevolent intentions though.

So do I. But I have seen many PPA's with broken and buggy software that was badly (if at all) maintained. With nasty side effects on the system as a whole.

Ubuntu is a fixed release *for a reason*. The official repo's are there *for a reason*. As said: test boxes can be used freely in the wildest of experiments. Not so for production machines and important computers in general, at least if one values a stable and reliable system on those. Which one should.

---

### Post by iMac71 on 2013-01-03
many thanks to both of you.
Even if I use my iMac at home, and therefore it could be considered a "play box" since I don't use it for my work, I prefer a safe install.
Well, I've found what to do this evening: make a clean install of Ubuntu.

---

### Post by Zill on 2013-01-03
> **iMac71 said:**
> ...what are the safest software sources that I can use/enable without risks or at least with few risks? It seems to me that I can enable the backports ones, the partners ones and the independent ones.
If you are *really* looking for the safest sources then I suggest you should not enable backports.
> [Stability of Backports]("https://help.ubuntu.com/community/UbuntuBackports")

When using Backports, it is important to understand that there is an inherent risk in backporting software. Although backported packages are tested by the community before they are included in the repository, there are very occasionally bad interactions with the older software on your system that are overlooked.
Of course, as has been pointed out, if the machine is non-critical or you do not care about breakage then backports are generally fine.

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> many thanks to both of you.
Even if I use my iMac at home, and therefore it could be considered a "play box" since I don't use it for my work, I prefer a safe install.
Wise choice. :)

> Well, I've found what to do this evening: make a clean install of Ubuntu.
In this case, that probably won't be necessary, because only two PPA's are concerned. It will presumably suffice to install this package from Software Center:
```
ppa-purge
```

---

### Post by Pjotr123 on 2013-01-03
> **Zill said:**
> If you are *really* looking for the safest sources then I suggest you should not enable backports.

They have become much less risky.... not so long ago they have been issued a low and harmless priority. That's why they are enabled by default nowadays. :)

To check the priority of Backports yourself, you can run the following command in a terminal:
```
apt-cache policy | grep backports
```

Now you'll see that the priority of the Backports repository is pinned to 100 for everything except the translations (in a localized system). Other repositories (and the translations in Backports) have the default priority 500.

This means that you have to explicitly choose to install the backport version of a package, if another version of that package also exists in a non-backports repository. 

The advantage of this is twofold: it won't easily mess things up on your system, and if a package is only available in Backports, you'll be able to install it without modifying anything else. 

In my opinion that's a reasonable compromise, so I keep them enabled nowadays. :)

---

### Post by iMac71 on 2013-01-03
> **Zill said:**
> If you are *really* looking for the safest sources then I suggest you should not enable backports.thank to you too for your suggestion.
I prefer to have something less but a safe installation than to have something more but risky.

---

### Post by iMac71 on 2013-01-03
Just to explain what are my needs: when I was an Apple user, I used aMule and transmission for downloading audio and video files, iTunes for playing audio, QuickTime with some extensions for playing videos, LibreOffice as office suite.
Now that I've installed Ubuntu, I use Rhythmbox for audio and Totem for playing videos with Medibuntu extensions for encrypted dvds.
Is there perhaps any security issue by using Medibuntu? I didn't have any problem until now.

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> Is there perhaps any security issue by using Medibuntu?

No. Medibuntu is quite safe. :)

---

### Post by zombifier25 on 2013-01-03
> **iMac71 said:**
> many thanks to both of you.
Even if I use my iMac at home, and therefore it could be considered a "play box" since I don't use it for my work, I prefer a safe install.
Well, I've found what to do this evening: make a clean install of Ubuntu.

And why do you wish to reinstall?

---

### Post by iMac71 on 2013-01-03
"quite safe" is sufficient for my security standards (even because, at least IMHO, doesn't exist an "absolutely safe" software).

---

### Post by Zill on 2013-01-03
> **Pjotr123 said:**
> They have become much less risky.... not so long ago they have been issued a low and harmless priority. That's why they are enabled by default nowadays...
Agreed!  However, if backports *are* enabled it is still possible for users to "tinker" with pinning and, if they don't know what they are doing, they can easily end up in "dependency hell"!
> [Warning]("http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_tweaking_candidate_version")

Use of apt-pinning by a novice user is sure call for major troubles. You must avoid using apt-pinning except when you absolutely need it.
Personally, I would still not have backports enabled on a production system.

---

### Post by iMac71 on 2013-01-03
> **zombifier25 said:**
> And why do you wish to reinstall?because so I'm sure to remove all potentially dangerous software (see also [post=12435549]this post[/post] of Pjotr123).
It's a "fee" that I have to pay because of my ignorance about what is safe to install in Ubuntu.

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> because so I'm sure to remove all potentially dangerous software (see also [post=12435549]this post[/post] of Pjotr123).
It's a "fee" that I have to pay because of my ignorance about what is safe to install in Ubuntu.

As I said, in your case I wouldn't reinstall, but simply install ppa-purge.... :)

---

### Post by iMac71 on 2013-01-03
> **Pjotr123 said:**
> As I said, in your case I wouldn't reinstall, but simply install ppa-purge.... :)Hoping I'm not wrong, I guess that ppa-purge is somehow the reversal of apt-add-repository + apt-get update + apt-get upgrade, thus it should be sufficient to type in a Terminal window:```
sudo ppa-purge <ppa name>
```for having the downgraded (i.e. originally installed) version of software.

---

### Post by Pjotr123 on 2013-01-03
No; this should possibly be enough:
```
sudo apt-get install ppa-purge
```

I'm not quite sure, as I've never needed to use it myself. Perhaps installing is all it takes...

You can read the manual:
```
man ppa-purge
```

---

### Post by iMac71 on 2013-01-03
> **Pjotr123 said:**
> No; this should be enough:
```
sudo apt-get install ppa-purge
```Sure, first of all I have to install ppa-purge as shown by you, but then? I think I should use the command I wrote in my previous post for purging all unwanted ppas, don't I?

---

### Post by Pjotr123 on 2013-01-03
> **iMac71 said:**
> Sure, first of all I have to install ppa-purge as shown by you, but then? I think I should use the command I wrote in my previous post for purging all unwanted ppas, don't I?

Possibly; I've never needed to use it myself.... You can read the manual:
```
man ppa-purge
```

---

### Post by iMac71 on 2013-01-03
> **Pjotr123 said:**
> Possibly; I've never needed to use it myself.... You can read the manual:
```
man ppa-purge
```from [the online manual page of ppa-purge]("http://manpages.ubuntu.com/manpages/precise/en/man1/ppa-purge.1.html"): it> provides a bash shell script capable of automatically downgrading all packages in a given PPA back to the ubuntu versions.So, thanks to your suggestions and to the ones of the other forum users, I won't need to make a clean install, but I'll have only to use ppa-purge for all unwanted ppas.

---

### Post by zombifier25 on 2013-01-03
This is still extreme paranoia IMO. You only use two PPAs that are pretty much well-known, trusted, tested, etc. etc.. I use about a dozen.

Makes me think you should be using Debian Stable :P

---

### Post by Zill on 2013-01-03
> **zombifier25 said:**
> Makes me think you should be using Debian Stable :P
...but the current Stable (squeeze) will superseded very shortly by the current Testing (wheezy). ;-)
[LIST][*][DebianWheezy]("http://wiki.debian.org/DebianWheezy")[/LIST]

---

### Post by iMac71 on 2013-01-04
> **zombifier25 said:**
> This is still extreme paranoia IMO.you might be right... :D > **zombifier25 said:**
> Makes me think you should be using Debian Stable :Punfortunately Debian seems not to work properly on my iMac :( .

---

