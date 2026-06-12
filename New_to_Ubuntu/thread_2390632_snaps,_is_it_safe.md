---
title: "snaps, is it safe?"
date: 2018-04-30
forum: New to Ubuntu
---

### Post by duister on 2018-04-30
I was just testing ubuntu 18.04, and when performing a "df" in the console, I saw many mountpoints. I then looked into snaps, and saw what it was all about.

Now I understand snaps is a solution for a problem. And I don't know much about it yet. But with my limited knowledge I see 2 things. Overhead, which is just a minor thing, really. But the second thing is security. When You install an Operating System, you must trust the company behind it. You would probably trust Ubuntu that it's mirrors/repositories are safe, and you won't get any harmful software from it's repositories. So that's that.

But let's say you use Ubuntu 18.04 for a year or two. And you've installed several snaps. Some well-known, like signal, or firefox, and perhaps some obscure ones, like tools or whatever. Who updates those snaps? And is there any reviewing of these snaps, by for example the ubuntu team,  before you get an update. Would it be theoretically possible that a certain developer of a certain app that you get by snap, could update that snap in a later version with that app that for example steals user data?  

What I really mean is, instead of trusting only Ubuntu and it's software repositories, so only one vendor,  should the user now trust all the snap makers as well? To me this seems like quite a thing. I would think I would lose oversight of my system.

Is it safe, in the long run?

---

### Post by QIII on 2018-04-30
As with anything else, you can count on official Canonical packages to be safe.  You take your chances with third-party packages.

I don't use snaps because of the clutter you mentioned.  On the whole, I think that approach is a solution in search of a problem except in some specific cases.

---

### Post by thenailedone on 2018-04-30
> **QIII said:**
> On the whole, I think that approach is a solution in search of a problem except in some specific cases.

I would love to be able to install games onto my machine that simply work. Currently when the game comes out the current version of Ubuntu may have it working fine, but three Ubuntu versions later and you may find you are out of luck. With a snap (or any of the other two similar implementations) if done right this kind of headache may be solved (or at least lessened).

---

### Post by Claus7 on 2018-04-30
Hello,

I think that canonical is pushing towards a safer snaps packaging system. Yet, it is relatively new, with (relatively) few applications supporting it up to now. I think that the philosophy of the system is that the snap package will have its own libraries and that being in its own "cucumber" it won't affect the security of the system. Theoretically, that is...

If you can stick with deb packages, then follow this route.
If you want a version that will be extremely fresh, then install it via snaps, which also means that it will occupy more space.

Personally I have removed snapd, since it increases my boot time.

Regards!

---

### Post by duister on 2018-05-01
> I would love to be able to install games onto my machine that simply work.

True, and that's what I mentioned, it's a solution to a problem. But is it a dirty solution? And could you accept a dirty solution to a problem?

> I think that canonical is pushing towards a safer snaps packaging system. Yet, it is relatively new, with (relatively) few applications supporting it up to now. I think that the philosophy of the system is that the snap package will have its own libraries and that being in its own "cucumber" it won't affect the security of the system. Theoretically, that is...

Ubuntu 18.04 is an LTS release. If canonical is pushing towards a safer snaps packaging system, why is it in an LTS release? Just because the apps have a read only mountpoint does not mean at all that it won't affect the security of the system.  Apps and libs can include malicious code, and can harm the user by for example stealing user data. After some searching I found [this]("https://mjg59.dreamwidth.org/42320.html") .

> Personally I have removed snapd, since it increases my boot time.
Same here. I reinstalled ubuntu 18.04, and removed snapsd. But only for security reasons.

edit:
I'm all for the idea that people have their own responsibility, but many users might not differentiate between "normal" repositories (since it's not a different interface), and application via the snap infrastructure. So a little warning to users, before using snap, might be an appropriate way of informing the user that these snaps are less monitored and should be installed at own risk.

---

### Post by Claus7 on 2018-05-01
Hello,

> **duister said:**
> 
Ubuntu 18.04 is an LTS release. If canonical is pushing towards a safer snaps packaging system, why is it in an LTS release? 

As mentioned this is supposed to be relatively new. So it has its pros and cons. As long as you install a package using your password there is always a risk. There is not much more to tell, since I have not used it. From your search it seems that one solution would be the mir display server combined with snaps.

Regards!

---

### Post by monkeybrain20122 on 2018-05-01
Maybe too safe. It is sandboxed so for example it has problem accessing peripherals like external drives and dvd drives etc.  (think it might be fixed upstream but will take a while to filter down)

---

### Post by hrsetrdr on 2018-05-01
I haven't installed 18.04 yet, will try it out in a vm first.  I don't expect to have a huge need for snaps, but I will try it out.

---

### Post by duister on 2018-05-02
> Maybe too safe. It is sandboxed so for example it has problem accessing peripherals like external drives and dvd drives etc. (think it might be fixed upstream but will take a while to filter down) 

The "too safe" is not a correct statement. These snaps are just a squashfs way of making the the software available on the system. It's a readonly package, that is mounted.  The application inside it is not really executed sandboxed.  The code is run able. And software That you run from it, can just have access to the areas that you as a user have access to. Otherwise it would be unusable. The firefox snap can for example use your /home/user to write it's profile to. And another snap called "toolX"(example) could theoretically access your firefox profile to read-out your bookmarks. What if the developer of toolX suddenly starts to do that to sell that information. Or the developer of toolX is bought up by a company that starts doing these practices.

> I haven't installed 18.04 yet, will try it out in a vm first. I don't expect to have a huge need for snaps, but I will try it out. 
You can try it out, but for the question I have, this is not really relevant. Since there are probably no issues yet that can be reproduced. But it could become an issue in the near future..

Like I mentioned, I understand that the snaps way solves a problem, and also that the convenience that snaps provides could help to increase the marketshare of linux on the desktop.  But I find it questionable that the linux desktop would default to this way of distributing software, where even the gnomecalculator can have it's own mountpoint, and the way of distribution resembles the windows store way of even the most basal software ( like a calculator).

---

### Post by sp40140 on 2018-05-02
Putting aside the structural concerns of snap, it's as safe as you want it it to be.
I have many applications which are from third party like VMWare Player, Citrix/ICA client, calibre. These are not curated by Ubuntu. But I trust them and manage updates and patches myself.
If you don't trust the software, don't install it in first place.
On a slightly related note: There are lots of software which just die out due to lack of maintenance by dev in repos and can make your system unstable.

Also Linux desktop user community isn't that big, if some questionable application is circulating, it will be found out quickly due to the average linux user is much more aware of what he puts on his machine.

So, it's not that big of a deal.

---

### Post by duister on 2018-05-03
> **sp40140 said:**
> Putting aside the structural concerns of snap, it's as safe as you want it it to be.
I have many applications which are from third party like VMWare Player, Citrix/ICA client, calibre. These are not curated by Ubuntu. But I trust them and manage updates and patches myself.
If you don't trust the software, don't install it in first place.
On a slightly related note: There are lots of software which just die out due to lack of maintenance by dev in repos and can make your system unstable.

Also Linux desktop user community isn't that big, if some questionable application is circulating, it will be found out quickly due to the average linux user is much more aware of what he puts on his machine.

So, it's not that big of a deal.

I think that is quite a good evaluation of this subject. And I agree with all you said there, because all you said is very to the point.

Now personally (which is not so relevant)  I really dislike this way of distributing software, where software from a single source, gets updated by the publishers itself. Now in practice, a user will indeed get 3rd party software from different sources. And the user has to trust that publisher. To differentiate snaps from the repositories, I would have preferred there would be a separate snapstore, so that users more clearly know that this is 3rd party software that is directly pushed by the publisher. This is not only form, but actually makes (new) users aware of the difference. 

The other thing is indeed the structural concern. Most gnu/linux users will not like the fact that a basal application will get its own mount point. It just looks messy. For exceptions, providing an application with static libs, can be a usefull thing. But making that a default way of distributing software just seems like chaotic to me.

To end this topic, I think that I can make a fair conclusion here. It's NOT Ubuntu, it's me. I guess I'm to old fashion to actually use this distro, and I should use a distro that sticks to a certain structure. Thanks for those who participated in this topic!

---

### Post by sp40140 on 2018-05-04
I gather you are concluding the security topic. 
I will add a thought on structure:
Note: I don't have preference (yet) either way.

If you look at enterprise servers, they usually run very limited number of applications with quirky dependencies. Snaps and structure can be really godsent for the admins who have to manage them.
Just ONE example: I worked with an enterprise where one server was running three applications. Two from vendors and one in house. All three JAVA based. and all three worked with very specific version of JAVA. Managing that server was a total mess nobody was interested in managing it.
You could set-up to work. But on going support and upgrades can make you wish for hell to ease pain. IE: when vendor provides new version which works with new java which matches other app. The re-configuration / regression testing it takes.
Now if you have self contained packages, the management is lot less painful.
and since you don't have many applications, you are not very concerned with mount points.

So it is likely that UBUNTU had enterprises in mind along with some apps with old libs for dependencies ( like drivers for Brother printers).
 
Just a different point of view.

---

### Post by grahammechanical on 2018-05-04
Ubuntu provides a tool for creating snap packages. It is called Snapcraft. It will also publish the snap on the snap store. Although I have not studied Snapcraft in detail, I do remember that the author has to create a manifest that lists all the things that the app wants access to. This manifest is used to create the snap. If the manifest lists a function that is not necessary or suitable for that particular application, then Snapcraft will refuse to create the snap package. It also follows that if the author does not list a function in the manifest then that function will not be available in the snap package app.

For example, a photo editing application will need access to the Photo folder but should it also be given access to a users contact list? Should an app try to access areas that it is not authorized to access it will be forced to request user authorization.

Of course, all things are considered safe until someone proves otherwise. 

[https://snapcraft.io/](https://snapcraft.io/)

Regards.

---

### Post by duister on 2018-05-05
> **sp40140 said:**
> I gather you are concluding the security topic. 
I will add a thought on structure:
Note: I don't have preference (yet) either way.

If you look at enterprise servers, they usually run very limited number of applications with quirky dependencies. Snaps and structure can be really godsent for the admins who have to manage them.
Just ONE example: I worked with an enterprise where one server was running three applications. Two from vendors and one in house. All three JAVA based. and all three worked with very specific version of JAVA. Managing that server was a total mess nobody was interested in managing it.
You could set-up to work. But on going support and upgrades can make you wish for hell to ease pain. IE: when vendor provides new version which works with new java which matches other app. The re-configuration / regression testing it takes.
Now if you have self contained packages, the management is lot less painful.
and since you don't have many applications, you are not very concerned with mount points.

So it is likely that UBUNTU had enterprises in mind along with some apps with old libs for dependencies ( like drivers for Brother printers).
 
Just a different point of view.

Yeah I guess it serves a purpose. Snaps is probably technically safe and handy. But, like I already mentioned, it is me that rejects this kind of practice, because I have to admit that I dislike change, especially such a structural change. And I first wanna understand a change and its (future) implications, before I accept it. And for me snaps unlocks a door that I would like to keep locked, namely defaulting to the "misuse" of mount points, and the idea that publishers can directly push updates to my pc. And yes, I can disable that, but like with everything, boundries are always gradually overstepped, and after a while many small changes are real structural changes. That's probably why I have always kept more traditional distro's on my laptop. The reason why I was interested in Ubuntu, is that I wanted to move from win7 to Ubuntu for my game pc. And Ubuntu offered more convenience for such a purpose. Everything was working fine with 18.04 really. and it's a nice piece of work. It's just not my cup of tea. But thanks for the input!

---

