---
title: "security.ubuntu.com mirrors?"
date: 2006-02-09
forum: Repositories &amp; Backports
---

### Post by deelow on 2006-02-09
hello, after many lengthy Synaptics downloads, i realised what I was doing wrong. During installation, i told Ubuntu that I was in the UK (as this is my home country), but I am currently living in China. My reasons for this were a mix of patriotism, and the fact that my Chinese language skills are not enough to use a Chinese XP, let alone a Chinese Linux (as his is my first Linux experinece).

Anyway, today I edited "gb.archives.ubuntu.com" to the obviously faster-if-you-are-in-China  "cn.archives.ubuntu.com". 

I then tried adding this "cn" prefix to "security.ubuntu.com", but this didn't work. So i did the obvious and added this ".cn" to the end of the address. This worked great, and now my downloads from security.ubuntu.com.cn average about 100kB/s.

My only concern is that this site might not be offcially supported by Ubuntu as I have not seen it mentioned anywhere. I experimented with a few other alternatives, but they do not exist(security.ubuntu.tw, security.ubuntu.co.uk, etc).

So, after all that, my question is this: IS SECURITY.UBUNTU.COM.CN AN OFFICIAL MIRROR?

I am a newbie so I'm not too sure about the security authentication malarky in the repositories options. But im guessing that because there is autentication by Synaptics, that this is indeed an official (yet unmentioned from what ive seacrhed) mirror.

Thanks. Now back to trying to solve this Synaptics touchpad mess....

---

### Post by aysiu on 2006-02-09
I live in the US, and I haven't found the US mirrors to be any faster than the regular Ubuntu mirrors (which I think are in the UK or somewhere in Europe). In fact, the US ones I've found a little unreliable.

---

### Post by deelow on 2006-02-11
hmm, after getting the ubuntu.security.com.cn mirror working, i then downloaded and used automatix. Now this program is great, but i didn't realise it would get so involved with my repository list. (repository sounds a little too similar to suppository for my liking).

Anyway, after foolishly deleting all the repositories that Automatix had installed, and then running Automatix, it was unsurprising that it didn't work. Then after messing about with apt-get f-install (or something like that), i eventually got it to download apps from the ".cn" repos.

I tried getting Firefox 1.5, but this has now turned into a mess as i didn't install Sun Java beforehand, and now Firefox doesn't want to run. So then I tried uninstalling automatix, and it wouldn't let me (i think its cos i changed the repo lists manually). I tried to reinstall it hoping it would reinstate its repo lists, but the stubborn thing wouldn't.

So after trying to uninstall other stuff that i put in with automatix, i was successful with uninstalling the old Firefox. But i think 1.5 was still lurking in places, i have yet to learn the Linux file system properly.

I tried to sort things out with Synaptics and reinstall the old, slow Firefox 1.01(?), but when I enter "security.ubuntu.com.cn/ubuntu" in the repo address, the listing in the repos list changes so it looks different to the others (they are usually a nice neat paragraph, with a suitable title, but now the title of security is the URL). So now the repo doesn't work. I am very confused as to why? Did Automatix mess up the authentication for security.ubuntu.com.cn, or did some of the general updates I made change something?

The way its looking now, im just tempted to do a fresh install, and try it all again Reinstalling Firefox 1.01 using hasn't helped. It will start to open, and then nothing, it just disappears. I think it might be cos of the problems with Java, but when i try to install it with automatix, it complains to me, and wont do it(i cant remember quite what about). Even installing opera to try to have a working browser didn't work, it wouldnt open either. So I am currently in XP, which has saved my *** more than once!

Anyway, whats the deal with this security.ubuntu.com.cn repo. Should it work? Is it official? And why could it have stopped working now? 

Thanks.

---

### Post by jdong on 2006-02-11
Note that security.ubuntu.com is just an alias to archive.ubuntu.com (they are interchangeable), so any archive.ubuntu.com mirror that has the "breezy-security" distro is fine. Guess and check from there :)

The only officially supported irror would be the security.ubuntu.com, but that doesn't mean that unofficially mirrored repositories are any worsely maintained. Since now APT packages and lists are all signed with GPG keys, there's virtually no risk of tampering (the original reason Debian had a specific security.debian.org).

---

### Post by deelow on 2006-02-12
thanks for that jdong. i am back in ubuntu after reinstall number 2 (i know that Linux users can repair instead of reinstall, but the force is still not strong with me).

Anyway, spooky happenings have since unfolded, and now when i enter the now infamous URL "security.ubuntu.com.cn", the extensive ubuntu file directories that were there a few days ago have now disappeared. It is now full of some weird symbols and stuff that i assume would be the Chinese language if i had the correct fonts installed. Is it just a coincidence that the mirror has gone offline since my query, or have the Ubuntu police shut this shady free-software-dealing server down?

Nevermind, back to achingly slow downloads from the regular security mirror. :(

PS: I apologise for the ramblings of my previous post, but i had been locked onto my computer for many hours solid trying to sort out my ubuntu, and i had lost touch with reality a little. Hence my slip of the three-lettered word. Sorry admin.

---

### Post by jdong on 2006-02-12
Try using 

deb [http://archive.ubuntu.com.cn/ubuntu/](http://archive.ubuntu.com.cn/ubuntu/) breezy-security main restricted universe multiverse


it seems to exist from here.

---

### Post by ceb on 2007-01-13
Thanks, I found this thread very helpful.

I live in China, and switching to [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/) for both [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) and [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) has worked well for me. 

I have found that some packages do not seem to be present on this mirror, but that could be temporary or I could be mistaken.


Additionally, this thread might help someone living in China to obtain new versions of Ubuntu:
[http://forum.ubuntu.org.cn/about35622.html&highlight=mirror](http://forum.ubuntu.org.cn/about35622.html&highlight=mirror)

---

### Post by Omarkj on 2007-01-24
> **jdong said:**
> Note that security.ubuntu.com is just an alias to archive.ubuntu.com (they are interchangeable), so any archive.ubuntu.com mirror that has the "breezy-security" distro is fine. Guess and check from there :)

The only officially supported irror would be the security.ubuntu.com, but that doesn't mean that unofficially mirrored repositories are any worsely maintained. Since now APT packages and lists are all signed with GPG keys, there's virtually no risk of tampering (the original reason Debian had a specific security.debian.org).

What..Really? I've been using Ubuntu since Warty and I've always been using security.ubuntu.com instead of my local mirror, is.archive.ubuntu.com for security updates (and the speed difference is huge). Thanks, I now spend less time downloading, that's always good news.

---

### Post by jdong on 2007-01-24
The only "downside" to using a different mirror than security.ubuntu.com is that there can be lagtime (mirrors synchronizing) to getting security updates, and a mirror problem can lead to not getting security updates... In addition in the incidents where an update is found to be problematic, they may be disabled on security.ubuntu.com instantly while that change would take time, or even never, propagate to mirrors.

That's the rationale  for using the main security.ubuntu.com mirror. Let your own paranoia be the judge of whehter or not it's worth the slower access :)

---

