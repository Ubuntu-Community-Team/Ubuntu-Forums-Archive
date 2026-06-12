---
title: "Ubuntu vs Debian"
date: 2012-02-22
forum: Recurring Discussions
---

### Post by Raevyn on 2012-02-22
Hey all,

I am curious just in general, what the real difference between Debian and Ubuntu actually is? I thought they were basically the same, just different Ubuntu specific software installed on a Debian system but I have come across a few packages that stated they would not work on a Ubuntu system but can on Debian. So Im just confused now.

---

### Post by vasa1 on 2012-02-22
Since they're a few, why don't you mention them? People maybe able to offer specific guidance.

---

### Post by snowpine on 2012-02-22
Ubuntu and Debian are not what is called "binary compatible" meaning a package compiled for a particular Ubuntu release is not guaranteed to work on a particular Debian release (and vice versa). It might work, it might not work, or it might appear to work for a while and then cause problems when you install some other app later on down the road.

Generally speaking you can install software from source on **any** distribution (that meets the dependencies). If the application you need is not in the Ubuntu repositories, and you cannot find a .DEB for your Ubuntu release, then compiling from source may be your best option.

But I agree with the above; why not tell us the secret software you're trying to install, so we can help? :)

---

### Post by Raevyn on 2012-02-22
Oh well thank you.. I was just speaking in general. 

I mean in my head, Ubuntu is an offshoot of Debian so I was thinking that as long as dependencies are met, software from the Ubuntu repositories should work on a Debian system if those PPA's were added to apt obviously LOL

I guess that makes me wonder, if I am making my own distro would it be a good idea to base it from Ubuntu or just modify a Debian installation, huh?

---

### Post by SteveDee on 2012-02-22
> **Raevyn said:**
> ...if I am making my own distro would it be a good idea to base it from Ubuntu or just modify a Debian installation...

Debian has 3 releases:-
 - Stable (Squeeze) which is thoroughly tested.
 - Testing (Wheezy) which is still undergoing testing, prior to becoming the next Stable release.
 - Unstable (Sid) which has the latest applications, but still requires a lot of testing.

Ubuntu is based on Debian Unstable, so again it has the latest applications, but may have problems due to lack of testing and rework.

If stability is of primary importance to you, consider Debian Squeeze.

---

### Post by snowpine on 2012-02-22
If you are considering making your own distro, then I recommend you use whatever you personally use, since you're going to be spending a lot of time supporting others with it. :)

---

### Post by Raevyn on 2012-02-22
Yea I prefer stable definitely. 

Its interesting Ubuntu is based on the newer stuff not proven stable..

---

### Post by snowpine on 2012-02-22
"Unstable" doesn't mean what you think it means. In Debian-speak "stable" means "static" and "unstable" means "fluid."

In other words use Unstable if you want your system to change when new software comes out, or Stable if you want it to stay the same. :)

---

### Post by Neobuntu on 2012-11-13
No it does not!

"unstable" means it may break, and the real translation means, it requires more time, and knowledge

"testing" is about 10 days after "unstable" and has not security upgrades.

So run "stable"! Do not mix testing, or unstable with it. "stable" (now called "Squeeze"), comes with *dynamic* security upgrades.

What is to be emphasized here, is quick, and smooth upgrade dependability. So you stay *dynamically*, ongoing, and stable.

Then, only add, just a few upgrades, and not to the core, to some app, and where you feel you must have the new version; for some *good* reason. 

Compiling into your stable Debian is easy; but you often, do not even have to do that. Many things can be installed, from the stable back-ports; that has compiled them for you. Anything that will not easily compile manually, into your stable Debian, is probably something that is not fully cooked yet, anyway. See? Be patient, it will be here when in a few short months.

Sure, if you are just exploring, developing, or just playing around, go crazy; but not on your main production system. At least, not on that same partition. If you are brand new, see Mint with Mate.

Also: Debian stable can be made like Ubuntu, or Mint, with all the things you might choose; but yes, you have to install them. In the end, it appears to be the same apps. However, what stable really is, is time savings; once custom installed. If you have a life, run Debian Stable, and as your *main* system.

---

### Post by vandorjw on 2012-11-13
I disagree, if you are installing a brand new system now, install debian wheezy:[http://www.debian.org/releases/wheezy/](http://www.debian.org/releases/wheezy/)
Debian 6 is only good for a production enviroment, but for many people on this forum, it lacks newer packages and therefor features.

Wheezy is now in beta and is already very stable.

---

### Post by philinux on 2012-11-13
Moved to recurring discussions.

---

### Post by monkeybrain2012 on 2012-11-13
> **snowpine said:**
> 
Generally speaking you can install software from source on **any** distribution (that meets the dependencies). If the application you need is not in the Ubuntu repositories, and you cannot find a .DEB for your Ubuntu release, then compiling from source may be your best option.



Generally speaking, but it is not always equally easy to find the dependencies. With Ubuntu and Debian I guess it is the same, but I have had packages that I can compile in Ubuntu/Debian but not in Fedora/Centos because of missing dependencies (you can compile those I guess, but it is not as easy when you can just get them from the repos)

---

### Post by mamamia88 on 2012-11-14
> **monkeybrain2012 said:**
> Generally speaking, but it is not always equally easy to find the dependencies. With Ubuntu and Debian I guess it is the same, but I have had packages that I can compile in Ubuntu/Debian but not in Fedora/Centos because of missing dependencies (you can compile those I guess, but it is not as easy when you can just get them from the repos)

one of the main reasons i love arch so much.   a package may not be in the official repos but if i need it you can almost bank on it being in the aur.   and then with a simple yaourt -S it will download all needed dependencies and build from source for me.   on the debian vs ubuntu debate they are mostly the same except debian has 3 branches while ubuntu only has the one. debian stable tends to be kind of outdated if you like the latest and greatest but,theres backports and you can "pin" certain packages to another branch.   for example you mostly prefer the food at one restaurant but prefer the fries from another.  well you can tell debian that you want everything from the first restaurant with the exception of the fries. debian has a slower release cycle and will release when they damn well deem it ready.  ubuntu will release after 6 months ready or not.  personally i prefer the debian method.it can be somewhat more complicated to setup than ubuntu but once done i think it's better.    ubuntu adds a bunch of stuff i personally don't use.

---

