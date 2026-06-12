---
title: "How to update programs in ubuntu?"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by asiancraig2 on 2013-12-28
how do i upgrade programs in ubuntu?  i've installed some programs like codeblocks a while back and now new versions came out and i don't know how to install them. on windows xp, all i had to do was download the new .exe program and install it, but on ubuntu i don't know how.    I installed it codeblocks and the other ubuntu programs using "ubuntu software center".   but now when i use the ubuntu software center, it shows that i've already installed the programs and it old shows the old versions when i know that new ones came out.  There is no option to update!

---

### Post by hoopia on 2013-12-28
first:
sudo apt-get install update

followed by:
sudo apt-get install upgrade

---

### Post by Impavidus on 2013-12-28
The update system doesn't automatically provide new releases of software, just the bug fixes and security patches. Upgrading to the latest Ubuntu release may get you later versions, not necessarily the latest, and it's a bit like using a bazooka to kill a mosquito. Firefox is one of a few exceptions, which is upgraded automatically. To get the latest version of programs automatically it is recommended to install PPAs for them – if available – or you can install them manually.

---

### Post by asiancraig2 on 2013-12-28
> **Impavidus said:**
> The update system doesn't automatically provide new releases of software, just the bug fixes and security patches. Upgrading to the latest Ubuntu release may get you later versions, not necessarily the latest, and it's a bit like using a bazooka to kill a mosquito. Firefox is one of a few exceptions, which is upgraded automatically. To get the latest version of programs automatically it is recommended to install PPAs for them &#8211; if available &#8211; or you can install them manually.

i can't find ppa for newest codeblocks.

So i can't get newer versions unless i upgrade ubuntu OS?  seriously, upgrading ubuntu is a mess...  I upgraded from ubuntu 10.04 to 12.04 reluctantly cause i wanted some newer version of my programs and it was a whole mess.  THe whole unity thing, the ubuntu one and etc, so much unnecssary change and annoying ones too.  I had to go through alot of trouble to get ubuntu 12.04 working, feeling and looking my ubuntu 10.04 which i loved.  So i'm not going through that mess again.  

but like you said, newer version of programs come out quickly, so even upgrading my ubuntu didn't do it for me :( since new one came out out fast.  I wished installing and removing and upgrading programs on ubuntu were easy like windows xp and weren't so dependent on the OS version it self since not even program have good PPAs.

---

### Post by sandyd on 2013-12-28
> **asiancraig2 said:**
> i can't find ppa for newest codeblocks.

So i can't get newer versions unless i upgrade ubuntu OS?  seriously, upgrading ubuntu is a mess...  I upgraded from ubuntu 10.04 to 12.04 reluctantly cause i wanted some newer version of my programs and it was a whole mess.  THe whole unity thing, the ubuntu one and etc, so much unnecssary change and annoying ones too.  I had to go through alot of trouble to get ubuntu 12.04 working, feeling and looking my ubuntu 10.04 which i loved.  So i'm not going through that mess again.  

but like you said, newer version of programs come out quickly, so even upgrading my ubuntu didn't do it for me :( since new one came out out fast.  I wished installing and removing and upgrading programs on ubuntu were easy like windows xp and weren't so dependent on the OS version it self since not even program have good PPAs.

Ubuntu does not update programs instantly so that all users can use programs that are already tested to be stable and bug free. New releases of programs will need to be tested to be stable and bug free before they will be updated in the repos.
That being said, code:blocks does provide nightly builds [http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu)

---

### Post by whitesmith on 2013-12-28
> **asiancraig2 said:**
> how do i upgrade programs in ubuntu?  i've installed some programs like codeblocks a while back and now new versions came out and i don't know how to install them. on windows xp, all i had to do was download the new .exe program and install it, but on ubuntu i don't know how.  . . . There is no option to update!Quite correct, by design. As #sandyd said, a goal of Linux is to be rock-solid. This requires exhaustive testing to avoid regressions, so Linuxware is not updated as often as its Win counterparts. One of the safest ways to install sw with the option of later uninstallation is going through the Ubuntu Software Center, which will tell you if a given package is--or isn't--on your system. To uninstall simply click the Uninstall button. Clicking Install puts the latest version on your system. Windows, by contrast, is a confusing muddle that can lead to back-revs, DLL hell and other problems that we in this community happily avoid. Cheers!

---

### Post by monkeybrain20122 on 2013-12-28
You can either use a ppa, there are a few but those are all daily or nightly builds (i.e betas), or download the debian binary from code:blocks' website (which is a tarball consisting of a bunch of .debs but for 32 bits only) Or you can compile it yourself.

---

### Post by monkeybrain20122 on 2013-12-28
> **whitesmith said:**
> Quite correct, by design. As #sandyd said, a goal of Linux is to be rock-solid. This requires exhaustive testing to avoid regressions..

Yeah I wish that is true, sometimes things in the repo don't even work. It is 'stable' only in the sense of being predictable, including predicatably broken. :) If I want the latest I will always get it, either through ppa or compile myself. My system has been very stable.

---

### Post by deadflowr on 2013-12-28
> **rushi4687 said:**
> first:
sudo apt-get install update

followed by:
sudo apt-get install upgrade

simply
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
I don't know if there is a package you can install called upgrade or update.;)

---

### Post by newb85 on 2013-12-28
Predictably broken is much better than unpredictably broken.  Predictably broken makes it much easier for community support to repeat/identify/diagnose problems.

---

### Post by monkeybrain20122 on 2013-12-29
> **newb85 said:**
> Predictably broken is much better than unpredictably broken.  Predictably broken makes it much easier for community support to repeat/identify/diagnose problems.

Well if it is predictably broken you would think that they would have fixed the problem already, and often they do just that you have to get the new version for the fix. I disagree that predictably broken is better, broken is broken and it is worse to tell people to stick with it for some weird ideological reason while a fix is very likely already available.

There is always a small risk of regression, but it would be ridiculous to tell people to ALWAYS use old software for fear of regression. If the new version doesn't work you can always downgrade given that the old version is always available in the repo. It is not the 'linux way' to be ultraconservative in installing up to date software, just the way of some distros, Arch definitely doesn't adhere to that, and neither does Fedora (even as a static distro)

---

### Post by newb85 on 2013-12-29
> **monkeybrain20122 said:**
> It is not the 'linux way' to be ultraconservative in installing up to date software, just the way of some distros, Arch definitely doesn't adhere to that, and neither does Fedora (even as a static distro)

You're absolutely right there.  But I would contend that it *is* the Ubuntu way.  And the forum code of conduct does mention something about that...

---

### Post by monkeybrain20122 on 2013-12-29
> **newb85 said:**
> You're absolutely right there.  But I would contend that it *is* the Ubuntu way.  And the forum code of conduct does mention something about that...

It is not even the Ubuntu way, just one way of using Ubuntu. If it is the Ubuntu way launchpad won't be hosting any ppa (Debian, for example has no such things and is actually against it) there won't be those tutorials for compiling the latest xyz and the repo wouldn't come with so many build tools and different versions of compilers(e.g Fedora only has the default version of gcc while Ubuntu has 3 or 4). A rich ecosystem of ppa is in fact a most attractive feature of Ubuntu, it provides a convenient way to selectively upgrade to the latest and greatest and a way to roll back (ppa-purge). It is a happy middle ground between the arch way (rolling everything) and the Debian way (never upgrade anything) 

The 'Ubuntu way" is being flexible. If "rock stable" (like a fossil) is the only consideration one should be using Debian stable instead of Ubuntu. :)

The advice I often hear by some very conservative people is the logical equivalent to "if you go out you may get robbed or hit by cars so better sit home and lock all the doors and windows." If this is "the Linux way" I can't see how it would be appealing to new users.

---

### Post by Bucky Ball on 2013-12-29
As mentioned:

```
sudo apt-get update
sudo apt-get upgrade
```

This will get you to the latest in your current release (not upgrade you to a newer release). If you want the absolutely latest bleeding edge of everything, install the nightly builds. ;)

---

### Post by laura.gildelaserna on 2013-12-30
You can do both actions (update & upgrade) if you write ";" between codes. To me, this way save time. ;)


```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by monkeybrain20122 on 2013-12-30
> **laura.gildelaserna said:**
> You can do both actions (update & upgrade) if you write ";" between codes. To me, this way save time. ;)


```
sudo apt-get update; sudo apt-get upgrade
```

Or you can do ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by deadflowr on 2013-12-30
Maybe instead of typing long statements over and over again, it would be wise to suggest using the software-updater/update-manager.
That's what it's there for.

---

### Post by vasa1 on 2013-12-30
> **asiancraig2 said:**
> ... shows the old versions when i know that new ones came out.  There is no option to update!
During the life of a release, the only updates are for critical bugs or security. Also, the updates are only for officially supported software. In other words, each time a new release is available, there's a chance of all the software being updated (provided these software updates are available before the freeze date).
As others have pointed out, if you want the latest software which isn't available from the standard repository, learn how to install such software yourself, whether by using ppas or by compiling from source.

---

### Post by philinux on 2013-12-30
> **asiancraig2 said:**
> i can't find ppa for newest codeblocks.

So i can't get newer versions unless i upgrade ubuntu OS?  seriously, upgrading ubuntu is a mess...  I upgraded from ubuntu 10.04 to 12.04 reluctantly cause i wanted some newer version of my programs and it was a whole mess.  THe whole unity thing, the ubuntu one and etc, so much unnecssary change and annoying ones too.  I had to go through alot of trouble to get ubuntu 12.04 working, feeling and looking my ubuntu 10.04 which i loved.  So i'm not going through that mess again.  

but like you said, newer version of programs come out quickly, so even upgrading my ubuntu didn't do it for me :( since new one came out out fast.  I wished installing and removing and upgrading programs on ubuntu were easy like windows xp and weren't so dependent on the OS version it self since not even program have good PPAs.

ppa 

[http://forums.codeblocks.org/index.php?topic=17634.0](http://forums.codeblocks.org/index.php?topic=17634.0)

and [http://ubuntuforums.org/showthread.php?t=2113262](http://ubuntuforums.org/showthread.php?t=2113262)

---

