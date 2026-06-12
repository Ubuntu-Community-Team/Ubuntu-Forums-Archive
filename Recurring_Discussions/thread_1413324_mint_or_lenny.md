---
title: "mint or lenny"
date: 2010-02-22
forum: Recurring Discussions
---

### Post by shadowlands on 2010-02-22
since Karmic and wubi are a pain are any of the others such as Lenny and mint stable and user friendly?  Can I order the old version before karmic?

---

### Post by atomizer on 2010-02-22
Debian Lenny is know for being stable (not the latest releases of software), and Mint is known for being userfriendly (a lot of codec/ prop. software installed by default)

---

### Post by caravel on 2010-02-22
When it comes to GNU/Linux "user friendly" does not always go hand in hand with "stable".  While Lenny (Debian 5.0) is stable, you may not find it to be as "user friendly" as Ubuntu or Mint.  If it's stability you're after though and if you don't mind a more manual approach to things like installing drivers, etc then I would recommend Lenny.

---

### Post by MontelEdwards on 2010-02-22
May I ask why you don't like Karmic?
And yes, you can download the release before Karmic (Jaunty) [here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/jaunty/")

---

### Post by swoll1980 on 2010-02-22
```
sudo apt-get install ubuntu-restricted-extras
```

would get you all your multimedia functionality with out having to install another distro. Mint is pretty much just Ubuntu with built in multimedia support. Ubuntu is pretty much just Debian unstable with some tools to make things easier.

---

### Post by MontelEdwards on 2010-02-22
> **swoll1980 said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

would get you all your multimedia functionality with out having to install another distro. Mint is pretty much just Ubuntu with built in multimedia support. Ubuntu is pretty much just Debian unstable with some tools to make things easier.
Don't forget to enable Medibuntu!
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update;sudo apt-get -y install ubuntu-restricted-extras
```

Just run that at it'll add the respo and install the extras:D

---

### Post by swoll1980 on 2010-02-22
> **MontelEdwards said:**
> Don't forget to enable Medibuntu!
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update;sudo apt-get -y install ubuntu-restricted-extras
```

Just run that at it'll add the respo and install the extras:D

if you do it from the terminal you don't even have to enable the medibuntu repos

---

### Post by kansasnoob on 2010-02-22
> **shadowlands said:**
> since Karmic and wubi are a pain are any of the others such as Lenny and mint stable and user friendly?  Can I order the old version before karmic?

The older versions of Wubi are here:

[http://sourceforge.net/projects/wubi/files/](http://sourceforge.net/projects/wubi/files/)

I'd recommend either Wubi-9.04.129 because it's supported until October of this year, or Wubi-8.04.506 because it's supported until April of next year.

Just BTW 9.10 Wubi bootloader fix is here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Gone fishing on 2010-02-22
I don't think Karmic is a pain - slight sound problems maybe. Certainly is you think setting up Karmic's a pain Lenny probably isn't for you.

I'm not saying Lenny isn't cool it is but it takes a little tinkering with.

Mint is a good option usually everything works out of the box, but then it is based on Ubuntu.

---

### Post by slakkie on 2010-02-22
Mint or lenny, weird choice iyam.

Lenny (Debian) is DIY. Mint is Ubuntu but even more for people who don't want to DIY. 

The choice is obvious: 

* Want a working system, no hassle with codecs and the like: Mint
* Want a working system, but willing to put in the extra mile: Debian Lenny.

---

### Post by bodhi.zazen on 2010-02-22
Moved to recurring discussions.

Honestly, IMO, Ubuntu is about as new user friendly as they come, and Mint is only "easier" as some things are pre-installed (codics for example).

Debian is a fine distro, but, IMO, not as new user friendly. You should not be running a development release unless you are either testing and willing to accept bugs (or preferably both).

Other Distros to consider would be Puppy linux, Fedora, ZenWalk, Slax.

---

### Post by shadowlands on 2010-02-22
I have had nothing but trouble since Karmic came out and I started using wubi.  Life is happing and a computer program that acts like it hates being used is not on the top of my list of things to worry about, yep that was a small rant.  

I get the thing of looking in the threads but things change so much that you often follow the wrong thread or because you, me, is an end user with out much computer knowledge one often ends up asking the wrong question or get folk who just want to comment and act nasty instead of helping.  I often feel like my question are just pissing folk off because of my lack of understanding of how the stuff works.

Sorry if this seams mean most folk on here are super nice and give good dummy guides. If I dual boot will I not have the same problem with the kernel not loading? > **MontelEdwards said:**
> May I ask why you don't like Karmic?
And yes, you can download the release before Karmic (Jaunty) [here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/jaunty/")

---

### Post by shadowlands on 2010-02-22
I agree and if dual booting will not cause me the same issue I will gladly do that.> **bodhi.zazen said:**
> Moved to recurring discussions.

Honestly, IMO, Ubuntu is about as new user friendly as they come, and Mint is only "easier" as some things are pre-installed (codics for example).

Debian is a fine distro, but, IMO, not as new user friendly. You should not be running a development release unless you are either testing and willing to accept bugs (or preferably both).

Other Distros to consider would be Puppy linux, Fedora, ZenWalk, Slax.

---

### Post by shadowlands on 2010-02-22
Sorry if I sound out of sorts but I keep trying to find the correct stuff to fix the problem and I keep hitting my head against a glass wall.> **shadowlands said:**
> I agree and if dual booting will not cause me the same issue I will gladly do that.

---

### Post by shadowlands on 2010-02-22
WOW THANKS!!  Which one do I use for a 32 bit computer. I think I use the second one but not sure. I have a intel dual core processor.> **MontelEdwards said:**
> May I ask why you don't like Karmic?
And yes, you can download the release before Karmic (Jaunty) [here]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/jaunty/")

---

### Post by shadowlands on 2010-02-22
I posted that quote a couple of weeks ago TU TU has more heart than most folk I have ever read about.  > **bodhi.zazen said:**
> Moved to recurring discussions.

Honestly, IMO, Ubuntu is about as new user friendly as they come, and Mint is only "easier" as some things are pre-installed (codics for example).

Debian is a fine distro, but, IMO, not as new user friendly. You should not be running a development release unless you are either testing and willing to accept bugs (or preferably both).

Other Distros to consider would be Puppy linux, Fedora, ZenWalk, Slax.

---

### Post by kansasnoob on 2010-02-22
Cut the OP some slack (s)he was having trouble with a well known Wubi bug in Karmic :D

Look at my previous post in this thread, and let's all remember we've all been frustrated at one time or other :D

---

### Post by shadowlands on 2010-02-22
What is an OP?  Thanks I took care of one problem, My son's school teacher, so back to the wonderful world of Wubi.> **kansasnoob said:**
> Cut the OP some slack (s)he was having trouble with a well known Wubi bug in Karmic :D

Look at my previous post in this thread, and let's all remember we've all been frustrated at one time or other :D

---

### Post by swoll1980 on 2010-02-22
> **shadowlands said:**
> What is an OP?  Thanks I took care of one problem, My son's school teacher, so back to the wonderful world of Wubi.

op is the original poster, or original post. The person who started the thread.

---

### Post by Zoot7 on 2010-02-22
Odd 2 distros to compare, although they're not that different, Mint coming from Ubuntu and Ubuntu from Debian, they've very different goals.

If you want a more user friendly experience, go with Mint.

As for Debian, while it's more hands on and not as user friendly as others have said, but if you persevere you'll get a far more solid system for a little more work. 
It's fantastic for stability. Few enough distros are as stable as Debian's Stable branch IMO, except an offical release of Slackware.

---

### Post by shadowlands on 2010-02-22
Thanks> **Zoot7 said:**
> Odd 2 distros to compare, although they're not that different, Mint coming from Ubuntu and Ubuntu from Debian, they've very different goals.

If you want a more user friendly experience, go with Mint.

As for Debian, while it's more hands on and not as user friendly as others have said, but if you persevere you'll get a far more solid system for a little more work. 
It's fantastic for stability. Few enough distros are as stable as Debian's Stable branch IMO, except an offical release of Slackware.

---

### Post by XubuRoxMySox on 2010-02-23
Mint is built on Ubuntu, so if Ubuntu is "broken," the corresponding Mint release will likely have all of the same issues!

Mint 8 ("Helena"), based on Ubuntu 9.10, has been so troublesome for alot of people that they've gone back to Min 7 ("Gloria"), which is built on Ubuntu Jaunty. Gloria ran pretty much trouble-free on my computer, as did Jaunty. But Karmic was a major pain.

If you want the stability of Debian Lenny _and_ the newbie-friendliness of Mint, have a look at Mepis! Built on the solid, stable bedrock of Debian Lenny but having a superb implementation of KDE (thanks to some wonderful Warren wizardry), Mepis has become my first choice in introducing newbies to Linux who have only known Windows before.

I think it's unconscionable to include Beta software by default in a distro that claims to be "newbie-friendly," as both Ubuntu and Mint do. It's great *if it works*, but when it doesn't, it gives even experienced Linux users headaches. I've been embarrassed by Ubuntu/Mint too many times when I've used them to introduce people to Linux, because of that buggy, experimental software that makes unwitting guinea pigs out of Linux newcomers. Good grief, you just don't give newbies Beta software and expect them to be fine with it!

-Robin

---

### Post by bodhi.zazen on 2010-02-23
> **dixiedancer said:**
> If you want the stability of Debian Lenny _and_ the newbie-friendliness of Mint, have a look at [s]Mepis[/s] Hardy (Ubuntu 8.04)

I Fixed that for your =).

Now there is nothing wrong with Mepis, it is a viable option and I agree well done.

However, in terms of "stability" you need to compare apple to apples ...

Debian stable (lenny) is roughly = to an Ubuntu LTS.

> I think it's unconscionable to include Beta software by default in a distro that claims to be "newbie-friendly," as both Ubuntu and Mint do. It's great *if it works*, but when it doesn't, it gives even experienced Linux users headaches. I've been embarrassed by Ubuntu/Mint too many times when I've used them to introduce people to Linux, because of that buggy, experimental software that makes unwitting guinea pigs out of Linux newcomers. Good grief, you just don't give newbies Beta software and expect them to be fine with it!

-RobinIf you feel that way, you should certainly advise Ubuntu LTS, Debian Stable, Slackware, or Centos. I do not include Mepis in that list as Mepis is not based on such a solid base as the distros I listed.

Slax is a nice fast OS as well, IMO good for booting from a live CD / USB.

Although I tend to agree with you, IMO it is very nice to have Debian Testing and Ubuntu releases available, use them if you wish, and yes they will be more likely to have bugs.

Linux offers choice, simply select the right tool for the job.

---

### Post by XubuRoxMySox on 2010-02-23
Hardy is pretty stable, I agree. But every release of Ubuntu up to and including Karmic has been built on Debian *Unstable*. Lucid is the first time Ubuntu has been built on Debian *Testing*. What *was* Debian Unstable at the time Hardy was released is now pretty much the same as Debian Stable *today*. But I would certainly not *equate* Hardy with Lenny ([COLOR="DarkGreen"]apples[/COLOR] and [COLOR="DarkOrange"]oranges[/COLOR]!). Besides, the OP titled this thread "*Mint or **Lenny***" - not "Ubuntu or Mint." Ubuntu and Mint are far closer for comparison than either Mint or Ubuntu is with Lenny!

> Ubuntu LTS, Debian Stable, Slackware, or Centos. I do not include Mepis in that list as **Mepis is not based on such a solid base as the distros I listed.**

**Mepis _is_ built upon Debian Stable** (currently "Lenny"). Mepis is *much more* comparable with Lenny than Hardy is in my opinion, because even the latest version of Mepis is built on Lenny, _directly_. And **you won't find Beta software in any release of Mepis.** *That* is what I find so objectionable about Ubuntu: The inclusion of Beta software (Grub2, PulseAudio, etc) in a distro that is supposedly "newbie-friendly." Hey *if it works*, great! But when it doesn't work, even experienced Linux users have difficulty fixing it or finding a workaround. **It ought to be a Linux Law: Don't give newbies Beta software and expect them to be just fine with it.** Even Hardy had Beta software (at the time of release). Mepis *never* does.

Stable **+** Newbie-friendliness **=** [Mepis]("http://mepis.org")!

-Robin

---

### Post by malspa on 2010-02-23
Mint or Lenny?

How about both?!?  Dual-boot 'em, get the best of both worlds, then see for yourself which one you like most!

:cool:

---

### Post by Zoot7 on 2010-02-23
> **dixiedancer said:**
> I think it's unconscionable to include Beta software by default in a distro that claims to be "newbie-friendly," as both Ubuntu and Mint do. It's great *if it works*, but when it doesn't, it gives even experienced Linux users headaches. I've been embarrassed by Ubuntu/Mint too many times when I've used them to introduce people to Linux, because of that buggy, experimental software that makes unwitting guinea pigs out of Linux newcomers. Good grief, you just don't give newbies Beta software and expect them to be fine with it!

-Robin
Could not agree more. Pulseaudio and Grub 2 are prime examples here, the edition in Ubuntu being Beta 4, a beta bootloader doesn't really inspire confidense in any way. Fine if Debian has them, but Debian doesn't advertise itself as an uber noob friendly experience as Ubuntu does.

> **bodhi.zazen said:**
> Debian stable (lenny) is roughly = to an Ubuntu LTS.
It's been maybe 7 months or so since I used Hardy but I remember it pulling in maybe 50-100MBs of updates per week including stuff like the kernel, whereas Lenny only gets security having all the core stuff constant. From a stability standpoint you definitely couldn't equate the two.

---

### Post by bodhi.zazen on 2010-02-23
> **Zoot7 said:**
> It's been maybe 7 months or so since I used Hardy but I remember it pulling in maybe 50-100MBs of updates per week including stuff like the kernel, whereas Lenny only gets security having all the core stuff constant. From a stability standpoint you definitely couldn't equate the two.

> **dixiedancer said:**
> Hardy is pretty stable, I agree. But every release of Ubuntu up to and including Karmic has been built on Debian *Unstable*. Lucid is the first time Ubuntu has been built on Debian *Testing*. What *was* Debian Unstable at the time Hardy was released is now pretty much the same as Debian Stable *today*. But I would certainly not *equate* Hardy with Lenny ([COLOR=DarkGreen]apples[/COLOR] and [COLOR=DarkOrange]oranges[/COLOR]!).

You are both taking my words out of context and seemed to have over looked the word "roughly". I did not make the kinds of claims you are inferring, specifically I never claimed any particular release of Ubuntu was equivalent to any  particular release of Debian.

You may compare debian and ubuntu in many ways. I was referring to "stability" in the context of this thread. In that context, IMO, Debian stable is roughly Ubuntu LTS.

To put my comments in context, I am suggesting if a user is looking for a "stable" Ubuntu release, with minimal testing or beta applications, you should, IMO use a LTS release, rather then 9.10.

Certainly you are not suggesting Debian Stable = Ubuntu 9.10 or that  9.10 is more "stable" then 8.04 ?

---

### Post by malspa on 2010-02-23
> **dixiedancer said:**
> Stable **+** Newbie-friendliness **=** [Mepis]("http://mepis.org")!

Yep!  Long-time Mepis Lover here!) :cool:


> **dixiedancer said:**
> But I would certainly not *equate* Hardy with Lenny ([COLOR="DarkGreen"]apples[/COLOR] and [COLOR="DarkOrange"]oranges[/COLOR]!).

Yeah, they're apples and oranges, but I also agree with this:

> **bodhi.zazen said:**
> if a user is looking for a "stable" Ubuntu release, with minimal testing or beta applications, you should, IMO use a LTS release

Ubuntu LTS and Mint LTS aren't like Debian Stable, especially when they're first released.  But if you wait a couple of months or so after the LTS version is released, and then stick with it for the duration, the overall experience can be, in many ways, similar to sticking with Debian Stable for the duration.  This is how it has seemed to me after rolling with Dapper and Hardy and Elyssa and Etch and Lenny.  Apples and oranges, but in the end, not really all that far apart.

---

### Post by Zoot7 on 2010-02-23
> **bodhi.zazen said:**
> Certainly you are not suggesting Debian Stable = Ubuntu 9.10 or that  9.10 is more "stable" then 8.04 ?
I meant from a *stability* standpoint you can't really compare Ubuntu LTS and Debian Stable. Most releases of Ubuntu tend to take ~1 month to "stabalize" so to speak, whereas Debian with it's "When it's Ready" model will always be a lot more solid.
Besides the LTS doesn't automatically mean stability but rather Long Term Support.

---

### Post by bodhi.zazen on 2010-02-23
> **Zoot7 said:**
> I meant from a *stability* standpoint you can't really compare Ubuntu LTS and Debian Stable.

You should direct that to the OP as it is s/he that is making the comparison.

I am only pointing out that, IMO, if one is going to compare Debian Stable to any particular release of Ubuntu one should use LTS and I am taking issue with the expectation of the OP that Ubutnu 9.10 be as stable as Debian stable.

If you read the thread I think you and I are in agreement.

---

### Post by Zoot7 on 2010-02-24
> **bodhi.zazen said:**
> I am only pointing out that, IMO, if one is going to compare Debian Stable to any particular release of Ubuntu one should use LTS and I am taking issue with the expectation of the OP that Ubutnu 9.10 be as stable as Debian stable.
No argument there, but that's not really how you came across above. Pardon me for splitting hairs. :tongue:

---

