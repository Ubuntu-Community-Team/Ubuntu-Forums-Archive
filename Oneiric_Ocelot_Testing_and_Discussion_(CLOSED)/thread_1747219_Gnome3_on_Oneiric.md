---
title: "Gnome3 on Oneiric"
date: 2011-05-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by pAsM on 2011-05-02
Hello,
[INDENT]It is nice to see that Oneiric is off to a great start, I would just like to offer a bit of feedback.
 
Currently there are 2 types of people out there, those who LOVE Unity and those that dont, I happen to be the latter. I slapped Gnome3 onto my laptop (with Natty) and am in blissful heaven.
 
Now replacing Unity with Gnome3 was a great solution for me personally, I fear it is not best for all. There is also no way to switch between Unity and Gnome3 as well. Can the next version of Ubuntu support both Unity and Gnome3?
[/INDENT]

---

### Post by ZarathustraDK on 2011-05-02
I believe I heard 11.10 would come with Unity3d, Unity2d, and "classic" Gnome 3.

Not a confirmation, just saw it somewhere on the forums.

---

### Post by Harry33 on 2011-05-02
Oneiric will have Unity (GTK+3) as a default desktop shell.
The fallback option is Unity2D (qt-based) for the hardware not capable for 3D and Compiz.
Gnome2-panel (GTK+2) is now discontinued and removed.

Vanilla Gnome3 does have Gnome-shell (GTK+3) as a default shell.
The fallback option is Gnome3-panel (GTK+3).

I haven't found info on Gnome3-panel (classic) being pulled into Oneiric, however.

---

### Post by CreativeReach on 2011-05-02
+1 for Unity on (GTK+3)!

---

### Post by seeker5528 on 2011-05-02
> **Harry33 said:**
> Gnome2-panel (GTK+2) is now doscontinued and removed.

Synaptic still shows me gnome-panel 2.32.1 being installed, so the Gnome 3 version hasn't replaced it yet, unless my mirror is not as up to date as the one you are using.

If you use one of the PPA's so you can run gnome-shell before it hits the official repositories, the Gnome 2 version of gnome-panel may (probably) have been replaced by a Gnome 3 version provided through that PPA.

Later, Seeker

---

### Post by xebian on 2011-05-02
> **pAsM said:**
> Hello,
[INDENT]It is nice to see that Oneiric is off to a great start, I would just like to offer a bit of feedback.
 
Currently there are 2 types of people out there, those who LOVE Unity and those that dont, I happen to be the latter. I slapped Gnome3 onto my laptop (with Natty) and am in blissful heaven.
 
Now replacing Unity with Gnome3 was a great solution for me personally, I fear it is not best for all. There is also no way to switch between Unity and Gnome3 as well. Can the next version of Ubuntu support both Unity and Gnome3?
[/INDENT]

On the logon screen you chose which session you want- unity or gnome shell.

---

### Post by jtfolden on 2011-05-02
I'm certainly hoping that 11.10 provides a good GNOME 3 (including Shell) experience for those who want it.

For the first time in years I've had to go elsewhere for Linux and it would be nice to have the choice of possibly returning to Ubuntu six months from now if other distros don't quite work out.... but at this point, a solid and complete Gnome 3 installation (including apps) is more important than the underlying distribution.

---

### Post by seeker5528 on 2011-05-02
> **jtfolden said:**
> I'm certainly hoping that 11.10 provides a good GNOME 3 (including Shell) experience for those who want it.

That's the expectation, which hopefully means better sharing between the relevant Ubuntu and Debian devs. Apparently when the newer Gnome stuff is not in a state that makes it a priority for the devs in either distro, one has the newer stuff in experimental and the other in a PPA, it makes sharing patches more difficult.  

> For the first time in years I've had to go elsewhere for Linux

If new and shiny is more important to you than waiting until there is time to do proper integration and testing, then ya gotta do what ya gotta do.

Even if there had not been so much emphasis put on Unity during the Natty development cycle, I think there was too much uncertainty about what shape Gnome 3 would be in to make it a realistic goal for Natty. 

Later, Seeker

---

### Post by jtfolden on 2011-05-02
> **seeker5528 said:**
> That's the expectation, which hopefully means better sharing between the relevant Ubuntu and Debian devs. Apparently when the newer Gnome stuff is not in a state that makes it a priority for the devs in either distro, one has the newer stuff in experimental and the other in a PPA, it makes sharing patches more difficult.  

Indeed, both seemed far behind last I looked. Fedora and OpenSUSE already have the bugfix 3.0.1 release readily available. In the past Ubuntu has been rather aggressive about pushing the latest Gnome down the pipe and one would assume/hope they will return to that for later releases.


> If new and shiny is more important to you than waiting until there is time to do proper integration and testing, then ya gotta do what ya gotta do.


It's less a case of being 'new and shiny' and more of a case of simply wanting to use what works for me best. I've always preferred Gnome but v2 was rather utilitarian no matter how you cut it. Gnome 3 has been a huge improvement. My main machine runs OS X, the cell phones we use around the office run WebOS. Gnome 3 just fits right in. It's the closest a *NIX DE has come to fitting my workflow.

So far, Gnome 3 has performed fine running on Fedora here and the only major flaws I found with it vanished once I left the incomplete Ubuntu PPA behind. Right now, Ubuntu just doesn't have anything else worth "waiting" with... (Unity is interesting but it's hardly forward thinking).


> Even if there had not been so much emphasis put on Unity during the Natty development cycle, I think there was too much uncertainty about what shape Gnome 3 would be in to make it a realistic goal for Natty. 


Possibly...

---

### Post by Harry33 on 2011-05-03
> **seeker5528 said:**
> Synaptic still shows me gnome-panel 2.32.1 being installed, so the Gnome 3 version hasn't replaced it yet, unless my mirror is not as up to date as the one you are using.
If you use one of the PPA's so you can run gnome-shell before it hits the official repositories, the Gnome 2 version of gnome-panel may (probably) have been replaced by a Gnome 3 version provided through that PPA.
Later, Seeker

Well aren't we are talking about Oneiric here, not Natty any more.
Then the roadmap is that Gnome2-panel is discontinued and will not be part of Oneiric.

---

### Post by alphacrucis2 on 2011-05-03
Give the devs a break. They have only just started on this. There are still quite a lot of decisions to be made yet. I'm sure GTK+3 will arrive soon enough in the repos along with plenty of breakage to go around. :P

---

### Post by CreativeReach on 2011-05-03
Gnome3 [desktop] should not be an option by default, but a separate download available on the software center.

---

### Post by bmbaker on 2011-05-03
I would love to see the continuity of gnome and ubuntu continue and have the gnome 3 desktop as well as the gnome-shell as a login option not as something extra to be installed from the software center.

---

### Post by jtfolden on 2011-05-03
> **bmbaker said:**
> I would love to see the continuity of gnome and ubuntu continue and have the gnome 3 desktop as well as the gnome-shell as a login option not as something extra to be installed from the software center.

I agree... though we may not see it for 'political' reasons.

---

### Post by CreativeReach on 2011-05-03
Unity is evovleing into something far better then Gnome3's Interface

---

### Post by Harry33 on 2011-05-03
Unity is only an alternative shell for Gnome. Canonical has decided not to use the default shell (Gnome-shell) in Ubuntu's Gnome.

However, Unity is also a continuity or enlargement of Compiz.
Is Compiz future?
If Canonical thinks so, I guess they made the right move with Unity.

Whereas Gnome.org thinks Clutter and Mutter is the future.
If they are correct, they made the right move with Gnome-shell.

Either way, these are separate paths and they divide users into two groups.

---

### Post by jtfolden on 2011-05-03
> **CreativeReach said:**
> Unity is evovleing into something far better then Gnome3's Interface

If only that were true. I'm afraid I don't share your opinion *at all*.

---

### Post by Starks on 2011-05-03
but mutter is a slow and lumbering beast for some hardware.

compiz is well-supported.

---

### Post by christoph411 on 2011-05-03
> **CreativeReach said:**
> Unity is evovleing into something far better then Gnome3's Interface

Just for future reference, Gnome 3 is an underlying platform (GTK3) while Gnome Shell is the DE that you are referring to, so, they are two completely different things.

---

### Post by espenfjo on 2011-05-03
Also, gnome3 comes with the fallback mode, which makes it almost as usable as gnome2.
Unity does sadly not come with such mode, and Unity, as it is today is completely useless on workstations, and not just surf machines.

---

### Post by alphacrucis2 on 2011-05-03
> **espenfjo said:**
> Also, gnome3 comes with the fallback mode, which makes it almost as usable as gnome2.
Unity does sadly not come with such mode, and Unity, as it is today is completely useless on workstations, and not just surf machines.


It does actually. There is unity 2D if 3D graphics isn't supported.

---

### Post by celticbhoy on 2011-05-03
I have been using Gnome Shell as my UI for a fair bit of time now, and although I preferred the look and feel of Shell previously, I still think it is a better option than Unity right now. During this Dev cycle that may change, but I will be happy enough with full Gnome3 being available in the repo's.

---

### Post by espenfjo on 2011-05-04
> **alphacrucis2 said:**
> It does actually. There is unity 2D if 3D graphics isn't supported.

But 2d and 3d are basicly  the same, just in 2d instead of 3d..
So no, thats not the same as gnomes fallback mode.

---

### Post by haydoni on 2011-05-04
> **espenfjo said:**
> But 2d and 3d are basicly  the same, just in 2d instead of 3d..
So no, thats not the same as gnomes fallback mode.

So... Unity's fallback is more **consistent** than Gnome Shell's, surely consistency is a good thing for users!

---

### Post by Harry33 on 2011-05-04
> **haydoni said:**
> So... Unity's fallback is more **consistent** than Gnome Shell's, surely consistency is a good thing for users!

It is, indeed.
But let us not forget that in Unity the fallback session is more important and more widely used.
Unity itself is a 3D shell, while Unity2D is of course 2D to provide larger hardware support.

However, in Gnome3 both the Gnome-shell and Gnome3-panel are only 2D sessions.

---

### Post by gnomeuser on 2011-05-04
> **Harry33 said:**
> 

However, in Gnome3 both the Gnome-shell and Gnome3-panel are only 2D sessions.

Wrong. Gnome-shell requires 3d acceleration.

---

### Post by Harry33 on 2011-05-04
> **gnomeuser said:**
> Wrong. Gnome-shell requires 3d acceleration.

Which effect is 3D in Gnome-shell?

---

### Post by Harry33 on 2011-05-04
To answer myself, I quote the text from live.gnome.org.
We can see from the text below, that actually Gnome-shell does not have modern 3D effects, instead it uses some primitive 3D cababilities.
I would not call that a 3D Desktop shell.

However, Unity possesses a true 3D environment.

> 
It is our primary focus to build a modern operating environment, platform, and user experience. It doesn't make sense to target the hardware of the past. GNOME Shell uses relatively primitive 3D capabilities that have been available from essentially all computing devices made in the last 4 or 5 years. This includes most desktop and laptop computers, mobile devices, phones, tablets, and netbooks.

Specifically:

We can't take advantage of the capabilities of graphics acceleration in the user interface design unless we can count on it - otherwise the graphics acceleration is at best tack-on eye candy.
Developing two separate code paths for accelerated and non-accelerated graphics is also a large increase in development resources.
Virtually all machines produced currently, or in the last 5 years have sufficiently powerful graphics to meet our needs. In some cases, free software drivers that can access this hardware don't exist are or still in an early stage. But we can't offer someone with shiny new hardware a desktop that looks like they have a 10 year old machine.
Buy hardware from friendly companies
Fix the free drivers for other hardware
If necessary and desired, offer users ways to install non-free drivers before they get to the desktop.


---

### Post by matthewbpt on 2011-05-04
I have been using gnome-shell for a week after updating all my gnome packages on Arch (this  wasn't accidental, I wanted to get all the Gnome3 packages in and the shell). At first I thought the Gnome developers must have been on crack when designing and coding it ... but the more I use it the more I like it. The way the activities are handled, and the workspaces and dash, is quite good for productivity in my view, and while there are still things that need ironing out with the UX etc, it's still early days so I have a lot of optimism for gnome-shell. What I really hope is that they make it more customizable! This is my only gripe for now, I don't want to have to mess with JavaScript and CSS code to customize my interface. But I'm sure these issues will be sorted as it develops more.

When KDE4 first came out people hated it, but now it's one of the best DE's out there I think, certainly better than Gnome2 for those with better hardware. Give Gnome a bit of time and I'm sure it will have won people over again.

You know what? Unity is great too! I hate to see all this animosity between the Unity - Gnome crowd. Choice is always better for the user IMO, so two shells for the Gnome environment is not a bad thing, and I think both sides can learn from each others design.

It's sad to see the old Gnome die, but it had to happen or else Gnome would stagnate IMO.

PS: Yes gnome-shell does require 3D acceleration, I think anyone using it properly would realise this ...

---

### Post by Harry33 on 2011-05-04
> **matthewbpt said:**
> 
...
PS: Yes gnome-shell does require 3D acceleration, I think anyone using it properly would realise this ...

How does Gnome-shell need 3D acceleration?
Does it have a 3D Desktop like Compiz?
Can you rotate the Desktop like a cube or ball?
The fairly primitive 3D capabilities it needs does not contain accelerated 3D.
Gnome-shell is so slow that one can hardly speak of a 3D accelerated Desktop.


The 2D acceleration (like video acceleration) is totally a different matter.

---

### Post by Frogs Hair on 2011-05-04
I won't speculate about what may available in 11.10 and beyond . I have only been using Ubuntu for just over a year and I'm on my forth release.
 
I remember discussions about the Gnome shell in 10.10 and other speculations that never came to pass . Waiting for an official official announcement works best for me.

I was very negative when it was announced that Unity would be default in 11.04 and now that I am using it I have no interest in using Classic Gnome anymore.

---

### Post by Harry33 on 2011-05-04
As I see this, the future desktops will contain modern 3D technology.
Also gaming has required modern 3D technology a long time now.

Now we know that Canonical has chosen (with Unity) Compiz for a compositing manager.
Unity will also use the latest gnu tool kit, GTK+3.

The question is now, will Compiz fulfill the needs of a modern 3D desktop technology.
Is there a rational alternative to it?

At least it is hard for me to see that the evolution from metacity to mutter would be an answer to this.

---

### Post by tnt533 on 2011-05-04
You keep arguing about whether gnome shell uses advanced desktop effects when the point is that it still requires acceleration. Even you made that determination with your earlier post quoted below. Try running gnome shell in a VM without good acceleration and you'll see for yourself. Whether it looks fancy and spins like a top or not, it's still a 3d shell.

I use unity and hated it at first but I'm actually really enjoying it after giving it a few days. I don't plan on going back to standard gnome. After going through the available tweaks through compiz I see no reason why unity can't be used on a work station where gnome 3 with the shell could be. If the workstation doesn't have acceleration the 2d shell or classic gnome works just fine and represents one additional choice than gnome 3 does. 

I checked out gnome shell on a live suse distribution the other day and thought it to be non-intuitive but it's probably just me. An earlier poster expressed his happiness that there were options available and how it was a good thing to have choices and I tend to agree. Both should be available without one breaking the other and if we have patience I'm sure that, eventually, this will be the case. People expect instant results but remember how radical these changes really are to a landscape that has been stagnant and slow to change for years now.  Patience is key here. 

I'm sure Canonical and the Gnome group will eventually come to a middle ground for the sake of cross development but things have to pan out first. 

> **Harry33 said:**
> To answer myself, I quote the text from live.gnome.org.
We can see from the text below, that actually Gnome-shell does not have modern 3D effects, instead it uses some primitive 3D cababilities.
I would not call that a 3D Desktop shell.

However, Unity possesses a true 3D environment.

---

### Post by Harry33 on 2011-05-04
> **tnt533 said:**
> You keep arguing about whether gnome shell uses advanced desktop effects when the point is that it still requires acceleration. Even you made that determination with your earlier post quoted below. Try running gnome shell in a VM without good acceleration and you'll see for yourself. Whether it looks fancy and spins like a top or not, it's still a 3d shell.
...


The point is not the fact that GS requires some 3D capabilities.
But as live.gnome.org points out:
> 
GNOME Shell uses relatively primitive 3D capabilities that have been available from essentially all computing devices made in the last 4 or 5 years.


Read again - computing devices 4 or 5 years ago. Well that is not very much I think.

Once again, the point is can we call Gnome-shell a modern 3D shell or not.

---

### Post by seeker5528 on 2011-05-04
> **Harry33 said:**
> Well aren't we are talking about Oneiric here, not Natty any more.
Then the roadmap is that Gnome2-panel is discontinued and will not be part of Oneiric.

That's what the roadmap says, or that's just how you interpreted it?

Since gnome-panel is required for the fallback mode from Gnome shell to metacity+panel, it doesn't seem likely that it will be removed.

Not including it on the Ubuntu install disk and by extension in an Ubuntu install is not the same as removing it.

And sure the version will be gnome-panel_3.x.x instead of gnome-panel_2.x.x which might make it technically correct that gnome-panel version 2.x.x is discontinued but, to my way of thinking, saying 'Gnome2-panel is discontinued' gives the wrong impression. It's not like it's Firefox or Apache or something where you expect to have more than one supported version around.

Later, Seeker

---

### Post by DogMatix on 2011-05-04
Initially I was not a fan of the Unity Desktop especially in its 10.10 netbook incarnation. However, I have grown to like it and use it all the time in Natty.

Today out of curiosity I installed Fedora 15 beta on a USB stick, mainly to check out Gnome 3, and spent a few hours poking around getting the feel of things.

Personally, I am now quite excited to see what Unity could become with GTK3+ under the hood. So +1 for that.

---

### Post by Harry33 on 2011-05-05
> **seeker5528 said:**
> 
...
And sure the version will be gnome-panel_3.x.x instead of gnome-panel_2.x.x which might make it technically correct that gnome-panel version 2.x.x is discontinued but, to my way of thinking, saying 'Gnome2-panel is discontinued' gives the wrong impression. It's not like it's Firefox or Apache or something where you expect to have more than one supported version around.

Later, Seeker

I did mean (and I also wrote so) that Gnome2-panel will be discontinued.
So, we will not see that in released Oneiric, which will have Unity3D and as a fallback Unity2D shells. Porting Gnome3 in Oneiric has already began:
 - [https://launchpad.net/ubuntu/oneiric/+source/gedit/3.0.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gedit/3.0.2-0ubuntu1)
 - [https://launchpad.net/ubuntu/oneiric/+source/eog/3.0.0-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/eog/3.0.0-1ubuntu1)
 - [https://launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/3.0.0.1-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-settings-daemon/3.0.0.1-1ubuntu1)
 - [https://launchpad.net/ubuntu/oneiric/+source/gnome-power-manager/3.0.0-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-power-manager/3.0.0-1ubuntu1)

In vanilla Gnome3 we will not see Gnome2-panel (GTK+2 version). It will be discontinued.
Instead we will see Gnome-shell and as a fallback Gnome3-panel (GTK+3 version).

I do not think this gives a wrong impression.

---

### Post by CreativeReach on 2011-05-05
> **DogMatix said:**
> Initially I was not a fan of the Unity Desktop especially in its 10.10 netbook incarnation. However, I have grown to like it and use it all the time in Natty.

Today out of curiosity I installed Fedora 15 beta on a USB stick, mainly to check out Gnome 3, and spent a few hours poking around getting the feel of things.

Personally, I am now quite excited to see what Unity could become with GTK3+ under the hood. So +1 for that.

I think those who aren't comfortable with unity will be by 11.10 with all the "fixed" features it will have.

---

### Post by NCLI on 2011-05-05
> **Harry33 said:**
> To answer myself, I quote the text from live.gnome.org.
We can see from the text below, that actually Gnome-shell does not have modern 3D effects, instead it uses some primitive 3D cababilities.
I would not call that a 3D Desktop shell.
Funny, that's exactly the same thing Unity requires:
> The need for frame buffer objects and ARB shader programs is enough to disqualify some old GPUs from running Unity. For instance, Unity will have trouble running on any GPU from NVidia and AMD that is older than 5 years. Beyond 5 years, it is doubtful that GPUs have the processing power and the memory requirements to support Unity's with acceptable results.
[Source]("http://www.inalogic.com/component/content/article/34-general/63-demystifying-unitys-graphics-hardware-requirements")

> However, Unity possesses a true 3D environment.
The bottom line is that neither Unity 3D or Gnome Shell will run on a system with no 3D acceleration. IOW: They're 3D desktops.

---

### Post by Johnsie on 2011-05-05
> Gnome3 [desktop] should not be an option by default, but a separate download available on the software center.


I think it should be an option until Unity matures. The reason I am getting involved with testing is to make sure that occurs.

---

### Post by jbicha on 2011-05-05
Ubuntu 11.10 cannot include Unity and Gnome Shell on the CD. Besides the confusion of shipping 4 different desktop environments: Ubuntu, Ubuntu 2D, Gnome Shell and Gnome Fallback (aka Gnome Panel 3), there simply is not room on a 700MB CD for all this and the useful software Ubuntu includes by default. And there are no plans to switch to a DVD install.

Fedora is now a 1GB ISO but Ubuntu will try to be "disciplined" in Mark's words, for as long as it continues to make sense. Having a CD-size install has numerous distribution benefits even if it doesn't matter to many US, Europe, Japan, etc. users.

---

### Post by barid42 on 2011-05-05
I hope everyone is looking forward to the next release of Ubuntu 11.10. As a user-driven OS, it doesn't serve anyone to look backward.

That being said, as background, I run Ubuntu Natty with Gnome-shell. I abandoned Unity partially because it seemed clunky, but more importantly because it was unstable on my system. I fully plan on using Unity again when the Ocelot comes out.

I expect both Unity and Gnome-shell to change significantly in the coming months, as more users and developers get their hands on the products. In time, they may even converge naturally in their focus and (hopefully putting pride secondary to common goals) might merge back into a single product. Does Unity-shell have a nice ring to anyone else?

I hate to see fighting amongst two forward-thinking, modern, freedom-loving groups of advocates. We seem to be falling into patterns more suited for competing corporations, or sports teams. Our goal is one and the same: create a desktop that is stable, usable, efficient and modern. We all want to leave old technology where it belongs, without forgetting where we come from. We all want to make a desktop that we love, and that we can be proud to recommend as an alternative to commercial O$'s.

Division can be good. We can use this as an opportunity to learn from one another, whether it's pitfalls to avoid, or good ideas to emulate. We can forge two desktops stronger than the first.

I agree with much of what's been said. We cannot have two completely independent desktops on a single CD, but we should be able to have these desktops coexist, so that people can choose for themselves. I hope to see Gnome3 (including gnome-shell) included in the official Ubuntu repositories, rather than being relegated to a PPA. 

"A person with Ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed."

Let's make Unity and Gnome-shell the best they can possibly be, for the good of the community and of each other.

Thank you,

inb4 TL;DR

Dave

---

### Post by barid42 on 2011-05-05
I had to put that message out to calm the waters, and I meant every word.

On another note: 
What's the big deal on having a "true" 3d desktop? Aside from looking nice (really, really nice), does it provide any significant benefit to usability? If anyone has found that it does, then please share.

Looking at up-and-coming operating systems, specifically Google Chromium/ChromeOS, 3d is less of a priority, and the focus seems to be more on getting the computer out of the way of progress. Both Unity and Gnome-shell seem to work toward this idea, so 3d "eye-candy" would be counter-productive. The 3d should be focused more toward applications that use it.

I hope we're not getting stuck on a 3d desktop as a goal in and of itself. 

Thanks again :D

Dave

---

### Post by buzzmandt on 2011-05-05
I think the real question to ask is, is compiz being ported to gnome 3 (as in will compiz work with gnome 3 panel)?  Unity is a plugin for compiz, if no compiz for gnome 3 how will they do unity gnome 3?

---

### Post by Harry33 on 2011-05-05
> **barid42 said:**
> I had to put that message out to calm the waters, and I meant every word.

On another note: 
What's the big deal on having a "true" 3d desktop? Aside from looking nice (really, really nice), does it provide any significant benefit to usability? If anyone has found that it does, then please share.

Looking at up-and-coming operating systems, specifically Google Chromium/ChromeOS, 3d is less of a priority, and the focus seems to be more on getting the computer out of the way of progress. Both Unity and Gnome-shell seem to work toward this idea, so 3d "eye-candy" would be counter-productive. The 3d should be focused more toward applications that use it.

I hope we're not getting stuck on a 3d desktop as a goal in and of itself. 

Thanks again :D

Dave

What you said is, after all, a matter of taste and preference.
Don't forget the **freedom of choice** principle, the most valuable one.
If that has no value, we might as well install Windows7.

---

### Post by Harry33 on 2011-05-05
> **buzzmandt said:**
> I think the real question to ask is, is compiz being ported to gnome 3 (as in will compiz work with gnome 3 panel)?  Unity is a plugin for compiz, if no compiz for gnome 3 how will they do unity gnome 3?

Well sure it is, if you mean porting to GTK+3.
Otherwise there would be no Unity GTK+3.

Gnome3 is a Gnome desktop with Gnome-shell, all ported to GTK+3.

---

### Post by Harry33 on 2011-05-05
Now also gnome-keyring and libgnome-keyring has been ported to GTK+3.

 - [https://launchpad.net/ubuntu/oneiric/+source/gnome-keyring/3.0.0-3](https://launchpad.net/ubuntu/oneiric/+source/gnome-keyring/3.0.0-3)
 - [https://launchpad.net/ubuntu/oneiric/+source/libgnome-keyring/3.0.0-2](https://launchpad.net/ubuntu/oneiric/+source/libgnome-keyring/3.0.0-2)

---

### Post by barid42 on 2011-05-05
Harry33-

Freedom of choice is exactly the point. Having a choice between Unity and Gnome-shell (why stop there, we could also choose KDE, LXDE, XFCE, the list goes on) is a good thing. And even bringing the name Window$ into this post makes me feel kinda dirty.

I started hearing fan-boys trying to flame one another, and that's not the point. Be constructive.

I may have overstated the possibility that Gnome-shell and Unity could be one and the same (I'm a little skimpy on the underlying incompatibilities of mutter and compiz), but maybe not.

I'm not a software engineer, programmer, whatever.

I'm a nerd.

Dave

---

### Post by CreativeReach on 2011-05-05
For those that love Gnome3 for *some reason*, Canonical should make an official release called Gubuntu.'

personally I love the newest official vanilla Ubuntu.

---

### Post by DogMatix on 2011-05-05
> **CreativeReach said:**
> For those that love Gnome3 for *some reason*, Canonical should make an official release called Gubuntu.'

personally I love the newest official vanilla Ubuntu.

+1

And therein is what is great about a free (as in 'dom') OS, I can install the bare bones then do the hell I want with it. This shouldn't be forgotten or ignored.

---

### Post by seeker5528 on 2011-05-05
> **Harry33 said:**
> In vanilla Gnome3 we will not see Gnome2-panel (GTK+2 version). It will be discontinued.
Instead we will see Gnome-shell and as a fallback Gnome3-panel (GTK+3 version).

I do not think this gives a wrong impression.

Do you make a point of telling people Gedit2, Eog2, Nautilus2, Brasero2, etc... will be discontinued?

I can't imagine why you would, so why do it for gnome-panel? Gnome-panel will live on for the foreseeable I-can't-see-very-far-but-expect-some-number-of-years future.

You don't think that calling it Gnome2-panel instead of gnome-panel 2 and saying it's discontinued gives a similar kind of wrong impression people had the many times people said Gnome 3 when they meant Gnome-shell and said Gnome 2 when they meant 'Metacity'+'gnome-panel'?  

Later, Seeker

---

### Post by seeker5528 on 2011-05-05
> **CreativeReach said:**
> I think those who aren't comfortable with unity will be by 11.10 with all the "fixed" features it will have.

But people want dynamic features. :P

Later, Seeker

---

### Post by CreativeReach on 2011-05-05
> **seeker5528 said:**
> But people want dynamic features. :P

Later, Seeker

Sorry, I love customize-ability too! what I meant by "fixed" was "not broken features"

---

### Post by Harry33 on 2011-05-06
> **barid42 said:**
> Harry33-

Freedom of choice is exactly the point. Having a choice between Unity and Gnome-shell (why stop there, we could also choose KDE, LXDE, XFCE, the list goes on) is a good thing. And even bringing the name Window$ into this post makes me feel kinda dirty.
I started hearing fan-boys trying to flame one another, and that's not the point. Be constructive.
...
Dave

I did reply to your words:
> What's the big deal on having a "true" 3d desktop? Aside from looking nice (really, really nice), does it provide any significant benefit to usability? If anyone has found that it does, then please share.

So, what I mean is that users may and can choose what they prefer.
If someone likes eye-candy, so what.
That is just as valuable preference than the significant usability you did mention.
:guitar:
Harry

---

### Post by Harry33 on 2011-05-06
> **seeker5528 said:**
> Do you make a point of telling people Gedit2, Eog2, Nautilus2, Brasero2, etc... will be discontinued?

I can't imagine why you would, so why do it for gnome-panel? Gnome-panel will live on for the foreseeable I-can't-see-very-far-but-expect-some-number-of-years future.

You don't think that calling it Gnome2-panel instead of gnome-panel 2 and saying it's discontinued gives a similar kind of wrong impression people had the many times people said Gnome 3 when they meant Gnome-shell and said Gnome 2 when they meant 'Metacity'+'gnome-panel'?  

Later, Seeker

Seeker,
gedit, eog and other applications do remain even if they are ported to GTK+3.
I was not talking about that.

What I did mean is that there will no longer be an option in default Ubuntu to choose a classic session like it is now. With classic session I mean Gnome2-panel.

There will be Unity3D and Unity2D sessions. In this context, Gnome2-panel session (classic session) will be discontinued.

This roadmap is, however, not what I want. I would prefer the Gnome3-panel choice too, from official Ubuntu repos.

---

### Post by buzzmandt on 2011-05-06
afaik unity is going to be running on gnome 3, it will be the ui instead of gnome-shell, gnome shell should be no more than a sudo apt-get install gnome-shell away. or something similar as such.

---

### Post by Atsuisofu on 2011-05-06
Gnome3 was a big let down in my eyes. I would want to stick with Unity or Gnome2 I have always loved Gnome but I have no idea what they were thinking with Gnome3 it needs alot more work in my eyes before it is up to snuff for ubuntu.

---

### Post by cariboo on 2011-05-06
@Atsuisofu, What was it about Gnome3 that disappointed you? There is more to Gnome3 than Gnome-shell.

---

### Post by seeker5528 on 2011-05-06
> **Harry33 said:**
> Seeker,
gedit, eog and other applications do remain even if they are ported to GTK+3.
I was not talking about that.

Gnome-panel will still be available, it's required in Gnome 3 for the fallback if you can't run Gnome-shell, or if you force the fallback.

> What I did mean is that there will no longer be an option in default Ubuntu to choose a classic session like it is now. With classic session I mean Gnome2-panel.

People seem to continually get confused by that when it is indicated that something will be removed, when in fact it's not being removed, just not being included in the default Ubuntu install.

Gnome-panel changes a little in Gnome 3, but there is only one gnome-panel that changes from version 2.x.x to 3.x.x so I don't know why you say gnome2-panel and gnome3-panel.

> There will be Unity3D and Unity2D sessions. In this context, Gnome2-panel session (classic session) will be discontinued.

This roadmap is, however, not what I want. I would prefer the Gnome3-panel choice too, from official Ubuntu repos.

If Debian provides a metacity+panel session option, it doesn't seem likely that the Ubuntu devs will get rid of the option when they sync with Debian. If Debian doesn't provide a session option for it, I don't know if I really see the Ubuntu devs providing a session for it either.

And since it looks like Debian won't be providing an option for it, most likely if you want that you will have to create a custom session that doesn't use gnome-session for session management, learn more about how gnome-session works so you can use it in a custom session without it trying to load gnome-shell, or log in to the 'Gnome' session provided and set the option for Gnome to use the fallback mode.

There is probably some gsettings voodoo you could do at the command line to set the option to force the fallback mode if you had to.

Gnome-shell has it's own way of providing a panel that is not gnome-panel, the shell's panel is created using features provided by Gnome-shell so not likely to be able to be used independently. 

Gnome-panel is only used in the fallback mode in gnome 3 to provide an environment that is the same as the default stock gnome environment in Gnome 2.

So again it doesn't make sense to me to confuse the issue by referring to gnome-panel as gnome2-panel and gnome3-panel when if you want to talk about differences it's more clear to say gnome-panel 2.x.x and gnome-panel 3.x.x the same way you would talk about any other app.

It's not like this is Fringe where Walter/Walternate and Olivia/Fauxlivia type namings have reference to alternates that are expected to have a continued ongoing existence independently of each other. :P

Later, Seeker

---

### Post by CreativeReach on 2011-05-06
If you cant get used to unity just install kubuntu or xbuntu, but don't continue to bash Unity.

---

### Post by Harry33 on 2011-05-07
> **seeker5528 said:**
> Gnome-panel will still be available, it's required in Gnome 3 for the fallback if you can't run Gnome-shell, or if you force the fallback.
...
Later, Seeker

Seeker,
I put this very simple now.
Ubuntu 11.10 will not have Ubuntu Classic session. There will only a Unity3d and Unity2D as a fallback. No other fallbacks.
The default installation is Unity3D and Unity2D. See what has been dropped, if you compare with Ubuntu 11.04.

Then, if you want to use Gnome-shell and its fallback Gnome3-panel in Ubuntu, you will not find it from Ubuntu official repos. You will have to use a PPA for that.

Once again, Canonical will drop the Classic session from Ubuntu.

---

### Post by Harry33 on 2011-05-07
> **CreativeReach said:**
> If you cant get used to unity just install kubuntu or xbuntu, but don't continue to bash Unity.

This is very true.
Canonical believes in Unity and concentrates on that.
In future, Unity may be more widespread, than we see now.
Ubuntu does not need Gnome-shell.

---

### Post by jtfolden on 2011-05-07
> **Harry33 said:**
> Then, if you want to use Gnome-shell and its fallback Gnome3-panel in Ubuntu, you will not find it from Ubuntu official repos. You will have to use a PPA for that.


This is completely untrue... there has been NOTHING stated that Gnome-Shell/Panel will not be in the official repos for 11.10 at all. Indeed, there is every expectation that they will. The latest interview with Shuttleworth backs this up, if I recall correctly.

---

### Post by Harry33 on 2011-05-07
> **jtfolden said:**
> This is completely untrue... there has been NOTHING stated that Gnome-Shell/Panel will not be in the official repos for 11.10 at all. Indeed, there is every expectation that they will. The latest interview with Shuttleworth backs this up, if I recall correctly.

OK, that may be the future.
Until then, I do not see anything like that, when I look at Ubuntu Ocelot repos right now.

---

### Post by Harry33 on 2011-05-07
Perhaps the Developer Summit on May 12th will shed some light on this issue.

---

### Post by jtfolden on 2011-05-07
Some comments from Mark Shuttleworth:

[I]i'm looking forward to having all of GNOME3 in Ubuntu	

you will certainly be able to have a close-to-vanilla GNOME3 experience in 11.10

contrary to popular belief, even distros that claim to be vanilla, often carry a lot of patches so i feel that gnome-in-ubuntu will be faithfully conveyed[/I]

complete interview:
[http://irclogs.ubuntu.com/2011/05/04/%23ubuntu-classroom.html](http://irclogs.ubuntu.com/2011/05/04/%23ubuntu-classroom.html)

---

### Post by Johnsie on 2011-05-07
Gnome-Shell isn't in the repos because it hasn't been packaged yet for Ocelot. Neither has Gnome3. They will be packaged soon. Give them some time. At the moment the packages that have been posted for Ocelot are the core essentials to get Linux running and compiled. The other stuff will follow.

---

### Post by screaminj3sus on 2011-05-07
> **Harry33 said:**
> Seeker,
I put this very simple now.
Ubuntu 11.10 will not have Ubuntu Classic session. There will only a Unity3d and Unity2D as a fallback. No other fallbacks.
The default installation is Unity3D and Unity2D. See what has been dropped, if you compare with Ubuntu 11.04.

Then, if you want to use Gnome-shell and its fallback Gnome3-panel in Ubuntu, you will not find it from Ubuntu official repos. You will have to use a PPA for that.

Once again, Canonical will drop the Classic session from Ubuntu.

Gnome 3 isn't in the 11.04 repos because it would be a huge undertaking to add it, as ubuntu is still based on gnome 2. All those libraries would have to be updated, and as the gnome 3 ppa has shown this breaks gnome2/unity. There is a very good reason why its not in the 11.04 official repos. Of course it will be there for 11.10, which will be based on gnome 3 libraries.

---

### Post by Harry33 on 2011-05-07
> **screaminj3sus said:**
> Gnome 3 isn't in the 11.04 repos because it would be a huge undertaking to add it, as ubuntu is still based on gnome 2. All those libraries would have to be updated, and as the gnome 3 ppa has shown this breaks gnome2/unity. There is a very good reason why its not in the 11.04 official repos. Of course it will be there for 11.10, which will be based on gnome 3 libraries.

First of all, I was not talking about Gnome3 nor its applications.
I was talking about the shells of Gnome3 (Gnome-shell and Gnome3-panel).

And as far as Ubuntu reps are conserned, there are already a lot of Gnome3 packages and all of the GTK+3 (Gimp Tool Kit): gnome-dev-tools, gnome-keyring, libgnome-keyring, gsettings-desktop-schemas, gnome-desktop-data, libgtksourceview, mutter ...
and
dependency waiting: eog, gedit, gnome-power-manager, gnome-settings-daemon ...

People here seem to mix Gnome3, Gnome-shell, GTK+3 many different ways.

---

### Post by jbicha on 2011-05-07
Harry33, please don't spread your wild speculations around on these forums. People might believe you although I believe people are smart enough not to. Nobody official has ever even hinted that Gnome Shell & Gnome Panel 3 will not be in the 11.10 repositories; in fact many times many developers have said that it will definitely happen. They will not be on the default CD and that's ok; there's a lot of good stuff not on the CDs because 1 CD cannot contain all the wonderful stuff we have available to us.

The reason they are not there yet is because the release cycle has just started. Developers were busy recovering after the 11.04 release (a little break is good, don't you think?), getting foundational stuff into 11.10 (like the initial building infrastruture), and preparing for UDS and the rest of the cycle.

---

### Post by buzzmandt on 2011-05-07
Harry spreadin fud?

---

### Post by Harry33 on 2011-05-08
> **jbicha said:**
> Harry33, please don't spread your wild speculations around on these forums. People might believe you although I believe people are smart enough not to. Nobody official has ever even hinted that Gnome Shell & Gnome Panel 3 will not be in the 11.10 repositories; in fact many times many developers have said that it will definitely happen. They will not be on the default CD and that's ok; there's a lot of good stuff not on the CDs because 1 CD cannot contain all the wonderful stuff we have available to us.

The reason they are not there yet is because the release cycle has just started. Developers were busy recovering after the 11.04 release (a little break is good, don't you think?), getting foundational stuff into 11.10 (like the initial building infrastruture), and preparing for UDS and the rest of the cycle.

> **buzzmandt said:**
> Harry spreadin fud?

Both of you fellows,
I have told people here my opinions and also text I have read elsewhere.
Then I also know that Gnome-shell and Unity do not work together very well now.
Also, Unity is not very ready ATM, so it will take devs time now and in the future too.
I do not spread here "any wild speculations", do you?

I think I have every right to express my views here.
I do not accept you fellows tell me otherwise.
If you cannot accept my text and views, do not read it, just go on your with life or find a new one.

---

### Post by jbicha on 2011-05-08
Harry33, yes, you're of course fully entitled to have your opinion. We're just saying that your opinion that Ubuntu will prevent Gnome Shell & Gnome Fallback from being in the 11.10 repositories has no basis in reality. And we'd prefer you not mislead others in this.

Gnome Shell & Unity work fine together. Admittedly, until earlier this week, carelessly installing the Gnome 3 PPA meant you couldn't boot Unity but that is fixed now.

---

### Post by Mr. Picklesworth on 2011-05-08
> **Harry33 said:**
> Then I also know that Gnome-shell and Unity do not work together very well now.

To the contrary, they work just fine together. The major problem is dependencies: Natty ships Gnome 2.32 and Debian can't handle Gnome 3 packages parallel to those. That's what will be sorted out early on in Oneiric.

There are some disagreements here and there &#8212; Gnome Shell uses a persistent notification daemon while Unity uses notify-osd with transient notifications. Unity uses dbusmenu / libindicate for some types of persistent notifications and for menus in the top panel, Gnome Shell has those menus baked in. However, fundamentally, they coexist fine and those differences don't really spill outwards. Unity and Gnome Shell (and Gnome Panel) are just different windows to the same place.

---

### Post by Harry33 on 2011-05-08
> **Mr. Picklesworth said:**
> To the contrary, they work just fine together. The major problem is dependencies: Natty ships Gnome 2.32 and Debian can't handle Gnome 3 packages parallel to those. That's what will be sorted out early on in Oneiric.

There are some disagreements here and there — Gnome Shell uses a persistent notification daemon while Unity uses notify-osd with transient notifications. Unity uses dbusmenu / libindicate for some types of persistent notifications and for menus in the top panel, Gnome Shell has those menus baked in. However, fundamentally, they coexist fine and those differences don't really spill outwards. Unity and Gnome Shell (and Gnome Panel) are just different windows to the same place.

Gnome-shell does not work fine even alone ATM.
It is sluggish, the animations are way too jerky.
And of course there are problems with Unity too, not nearly fluent enough IMO.
This may be due Compiz itself.

I use simplified Gnome2-panel in my main setups and of course without Compiz.

What you supposed to say, was that they may be installed together, but I would not say they coexist fine.

---

### Post by ranch hand on 2011-05-08
> **Harry33 said:**
> OK, that may be the future.
Until then, I do not see anything like that, when I look at Ubuntu Ocelot repos right now.
That is funny, gnome-desktop-environment is in the repo for my install of 11.10.  Or at least it was 2 minutes ago.

There is a dependency problem right now with a seahorse plugin but that is to be expected at this point in development.

The package gnome-core (goes with the gnome-desktop-environment) provides the panel mechanisms as in the past.

I do not like Unity a bit but hysteria is just silly.

---

### Post by buzzmandt on 2011-05-08
> **Harry33 said:**
> Both of you fellows,
I have told people here my opinions and also text I have read elsewhere.
Then I also know that Gnome-shell and Unity do not work together very well now.
Also, Unity is not very ready ATM, so it will take devs time now and in the future too.
I do not spread here "any wild speculations", do you?

I think I have every right to express my views here.
I do not accept you fellows tell me otherwise.
If you cannot accept my text and views, do not read it, just go on your with life or find a new one.
thank you harry for your opinion, i do welcome it and that the point of these forums.  it's when you begin pushing and repeating that opinion when others opinions are in opposition that it becomes, well.... pushy.  I like your opinion and i like what you have to say.  but once i read it once reposting and rehashing without point is unnecessary.


what i want at the end of this series is at login to have the option for unity, kde, gnome-shell and each one work and function correctly.  kde is still my first choice but i'm here for testing and testing i'll'a do.

Unity is going to work on gnome3, therefore it should be easy to have gnome-shell, which is a part of gnome3, just work.

---

### Post by Harry33 on 2011-05-08
> **ranch hand said:**
> That is funny, gnome-desktop-environment is in the repo for my install of 11.10.  Or at least it was 2 minutes ago.

There is a dependency problem right now with a seahorse plugin but that is to be expected at this point in development.

The package gnome-core (goes with the gnome-desktop-environment) provides the panel mechanisms as in the past.

I do not like Unity a bit but hysteria is just silly.

?
Right Ranch Hand, I know package gnome-desktop-environment_2.30+7ubuntu3 is in official repos of Ocelot. That is the GTK+2 meta package.

I was talking about Gnome-shell GTK+3 and Gnome-panel GTK+3 versions.
I do not see the Gnome-panel GTK+3 even in the Gnome3 PPA (Natty).
That PPA is not yet for Ocelot.

---

### Post by jtfolden on 2011-05-08
> **Harry33 said:**
> 
I was talking about Gnome-shell GTK+3 and Gnome-panel GTK+3 versions.
I do not see the Gnome-panel GTK+3 even in the Gnome3 PPA (Natty).
That PPA is not yet for Ocelot.

Indeed, it doesn't seem the PPA should be needed for 11.10 at all, considering Gnome 3 (including shell, etc...) will be in the official repos.

---

### Post by jtfolden on 2011-05-08
> **Harry33 said:**
> Gnome-shell does not work fine even alone ATM.
It is sluggish, the animations are way too jerky.


That's YOUR experience with it. Here, Gnome-Shell is not sluggish at all, even on a 5 or 6 year old Dell Optiplex GX280 with i915G it is smooth and with little hesitation (except for a few seconds immediately after startup).

---

### Post by Harry33 on 2011-05-08
> **buzzmandt said:**
> thank you harry for your opinion, i do welcome it and that the point of these forums.  it's when you begin pushing and repeating that opinion when others opinions are in opposition that it becomes, well.... pushy.  I like your opinion and i like what you have to say.  but once i read it once reposting and rehashing without point is unnecessary.


what i want at the end of this series is at login to have the option for unity, kde, gnome-shell and each one work and function correctly.  kde is still my first choice but i'm here for testing and testing i'll'a do.

Unity is going to work on gnome3, therefore it should be easy to have gnome-shell, which is a part of gnome3, just work.

Sorry for being pushy, though. I had no intention for that.
I also think it would be great to have as many options for different sessions as possible.
But of course, provided they do work well.

Up to this day, I haven't seen a fluently working Gnome-shell.
And it should work really well in my hardware:
- Gigabyte GA-MA790XT-UD4P
- AMD Phenom II X4 955 BE 3,2 Ghz
- Kingston HyperX DDR3 1,625 Mhz
- NVidia GTX285 1 Gb
- Western Digital Velociraptor 10,000 rpm SATA II HDD

I use Gnome-panel GTK+2 for now.
Actually I do not need a fancy desktop with eye candy.
But I do need fast and reliably working applications with a very good graphical properties. I demand a high class HD video capabilities with a true HiFi sound.
Now if I use Gnome-shell or Compiz, it is good bye to HD videos.
And I do not accept that.

---

### Post by Harry33 on 2011-05-08
> **jtfolden said:**
> That's YOUR experience with it. Here, Gnome-Shell is not sluggish at all, even on a 5 or 6 year old Dell Optiplex GX280 with i915G it is smooth and with little hesitation (except for a few seconds immediately after startup).

That may also be a nvidia proprietary driver issue.
But I do need very fine graphics.

---

### Post by buzzmandt on 2011-05-08
i know on my laptop with intel graphics unity, gnome-shell (the jhbuild one) and kde4 (my pref for now) all show effects very good and have no sluggishness to my system.  not sure what the prob is but def could be nvidia issues.  this laptop is a $300 laptop, very far from top of the line but works very good.

---

### Post by screaminj3sus on 2011-05-09
> **Harry33 said:**
> Sorry for being pushy, though. I had no intention for that.
I also think it would be great to have as many options for different sessions as possible.
But of course, provided they do work well.

Up to this day, I haven't seen a fluently working Gnome-shell.
And it should work really well in my hardware:
- Gigabyte GA-MA790XT-UD4P
- AMD Phenom II X4 955 BE 3,2 Ghz
- Kingston HyperX DDR3 1,625 Mhz
- NVidia GTX285 1 Gb
- Western Digital Velociraptor 10,000 rpm SATA II HDD

I use Gnome-panel GTK+2 for now.
Actually I do not need a fancy desktop with eye candy.
But I do need fast and reliably working applications with a very good graphical properties. I demand a high class HD video capabilities with a true HiFi sound.
Now if I use Gnome-shell or Compiz, it is good bye to HD videos.
And I do not accept that.

I've used it on opensuse and arch and it was acceptable for me on my hd2600 using the opensource drivers. I also just tried it with the new cat 11.5 drivers released today and it was incredbily smooth, but unfortunately the activities bar is still b0rked with cat :(

---

### Post by Harry33 on 2011-05-09
In this thread I have received a lot of criticism, when I have written my views on what will happen to Gnome-shell (GTK+3), Gnome-panel (GTK+3) and Gnome-panel (GTK+2).

Now for your entertainment, I have some news from the UDS (Ubuntu Development Summit).
- Work on Unity 2D (the fallback session) will go on further. It will use Compiz as a window manager instead of Metacity. Metacity will be dropped from live-CD.

- The Ubuntu-classic fallback session will be eliminated in Oneiric Ocelot (11.10).
   Well this is in line with this:
>   Comment 5 for bug 739812
Mark Shuttleworth wrote on 2011-03-31:	 #5
We made very good progress on a11y in Natty, but will miss the goal of
perfect a11y. We'll nail it in Oneiric. That's OK, because we have the
Classic desktop fallback in Natty, but will not in Oneiric.
Mark


See more:
[http://www.phoronix.com/scan.php?page=news_item&px=OTQxOQ](http://www.phoronix.com/scan.php?page=news_item&px=OTQxOQ)

---

### Post by CreativeReach on 2011-05-09
> **Harry33 said:**
> In this thread I have received a lot of criticism, when I have written my views on what will happen to Gnome-shell (GTK+3), Gnome-panel (GTK+3) and Gnome-panel (GTK+2).

Now for your entertainment, I have some news from the UDS (Ubuntu Development Summit).
- Work on Unity 2D (the fallback session) will go on further. It will use Compiz as a window manager instead of Metacity. Metacity will be dropped from live-CD.

- The Ubuntu-classic fallback session will be eliminated in Oneiric Ocelot (11.10).
   Well this is in line with this:


See more:
[http://www.phoronix.com/scan.php?page=news_item&px=OTQxOQ](http://www.phoronix.com/scan.php?page=news_item&px=OTQxOQ)

Happy to see the whole desktop moving to compiz!

---

### Post by Harry33 on 2011-05-10
> **CreativeReach said:**
> Happy to see the whole desktop moving to compiz!

Yes this is the plan. Simple and reasonable.

---

### Post by jtfolden on 2011-05-10
@Harry33: This doesn't change the fact that Gnome 3 (including Gnome-Shell, etc, will be in the official repos). I believe that was the only thing that people point out to you.

We've known for quite some time that Unity 2D will be the fallback option on the CD. However, anyone should be able to install Gnome 3 in its entirety without having to resort to a PPA or other repos.

---

### Post by Harry33 on 2011-05-10
> **jtfolden said:**
> @Harry33: This doesn't change the fact that Gnome 3 (including Gnome-Shell, etc, will be in the official repos). I believe that was the only thing that people point out to you.

We've known for quite some time that Unity 2D will be the fallback option on the CD. However, anyone should be able to install Gnome 3 in its entirety without having to resort to a PPA or other repos.

Of course people may install additional components too outside of official repos, from a PPA for example.
I have never said this would cease to exist.
But default sessions are Unity and Unity2D only. For most Ubuntu users this is the only reality.
Canonical is marketing Ubuntu this way too. And this is what I am talking about.

Lastly, I do support the freedom of choice. So, while I admit Gnome-panel (GTK+2) will soon be history, I still want to see the possibility to install Gnome-panel (GTK+3) into Ubuntu in future.

---

### Post by jbicha on 2011-05-10
Harry, 2 desktop environments (really 1 with a fallback for less graphics-intensive computers) is plenty. The goal is to only offer 1 program to do 1 thing on the CD. We have 1 web browser, 1 text editor, 1 wordprocesing app, 1 movie player and 1 music player (& even those final 2 might merge into 1).

I don't understand why including Gnome Shell & Gnome Fallback fully supported in the default repositories are not good enough for you. Some user doesn't know how to install software in his Ubuntu. Who cares? Ubuntu has to make choices on defaults and there will always be people who prefer an alternative. Shipping everything is not possible.

---

### Post by Johnsie on 2011-05-10
Does compiz work on older hardware?

---

### Post by Harry33 on 2011-05-10
> **jbicha said:**
> Harry, 2 desktop environments (really 1 with a fallback for less graphics-intensive computers) is plenty. The goal is to only offer 1 program to do 1 thing on the CD. We have 1 web browser, 1 text editor, 1 wordprocesing app, 1 movie player and 1 music player (& even those final 2 might merge into 1).

I don't understand why including Gnome Shell & Gnome Fallback fully supported in the default repositories are not good enough for you. Some user doesn't know how to install software in his Ubuntu. Who cares? Ubuntu has to make choices on defaults and there will always be people who prefer an alternative. Shipping everything is not possible.

Did I say it would not be good enough for me?
I have written about how I feel will happen, not what I wish.
I do not actually care about Gnome-shell, but including it into official repos makes more freedom of choice and thus it would be good.

This is my opinion. You do not have to like. Stop weaning about it.

---

### Post by seeker5528 on 2011-05-11
> **Johnsie said:**
> Does compiz work on older hardware?

Currently I think there is only one backend with the packages supplied in Ubuntu so you need OpenGL support, it works on older hardware, it depends on how well that hardware and it's driver support OpenGL.

But if you had followed the link....

[> - Rather than using Metacity or any other non-accelerated window manager, Compiz will be used. While Compiz is commonly used as a compoisiting window manager for OpenGL / OpenGL ES, it does support different back-ends. Compiz can target X Render or even the CPU-based QPainter. A goal will be to use Compiz with a non-accelerated back-end as a new fall-back.](http://www.phoronix.com/scan.php?page=news_item&px=OTQxOQ)

Xrender should work for the bulk of people who have no or slow OpenGL support. What FX work with what backends would be a whole other question.

Later, Seeker

---

### Post by seeker5528 on 2011-05-11
> **Harry33 said:**
> Did I say it would not be good enough for me?
I have written about how I feel will happen, not what I wish.
I do not actually care about Gnome-shell, but including it into official repos makes more freedom of choice and thus it would be good.

This is my opinion. You do not have to like. Stop weaning about it.

If you stopped talking about it as if it wasn't going to be in the repos when we have some indication that it will be and none that it won't then people would stop telling you it will be available.

There may or may not be a session option for the Gnome fallback mode, in which case you would have to run the normal Gnome environment and set the option to force the fallback mode, but that is a whole different thing than not having the software in the repos.

I have not seen anything indicating what kind of session options will be available for people who want to run Compiz without Unity, there are instructions for creating a customized Compiz session.

[https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)

Later, Seeker

---

### Post by Harry33 on 2011-05-12
> **seeker5528 said:**
> If you stopped talking about it as if it wasn't going to be in the repos when we have some indication that it will be and none that it won't then people would stop telling you it will be available.

There may or may not be a session option for the Gnome fallback mode, in which case you would have to run the normal Gnome environment and set the option to force the fallback mode, but that is a whole different thing than not having the software in the repos.

I have not seen anything indicating what kind of session options will be available for people who want to run Compiz without Unity, there are instructions for creating a customized Compiz session.

[https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)

Later, Seeker

The fact is no one knows for sure ATM, I assumed people here would understand that.
So this is all speculation now.
I have my own opinion and I intend to keep it too, whether you like it not.

---

### Post by seeker5528 on 2011-05-12
> **Harry33 said:**
> The fact is no one knows for sure ATM, I assumed people here would understand that.
So this is all speculation now.
I have my own opinion and I intend to keep it too, whether you like it not.

But we know the issues that led to gnome 3 not being fully integrated in the last cycle will be worked on in this cycle, so no reason to think to think Gnome Shell would not be included since it was the integration of the stack on not any issues with Gnome Shell that kept Gnome Shell out.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3)

[http://www.ubuntuvibes.com/2011/05/uds-updates-gnome-3-stack-to-land-in.html](http://www.ubuntuvibes.com/2011/05/uds-updates-gnome-3-stack-to-land-in.html)

Later, Seeker

---

### Post by BigCityCat on 2011-05-12
People that can't admit when they are wrong bother me. Very immature.

---

### Post by kansasnoob on 2011-05-12
> **CreativeReach said:**
> For those that love Gnome3 for *some reason*, Canonical should make an official release called Gubuntu.'

personally I love the newest official vanilla Ubuntu.

Gubuntu was tried and failed:

[https://bugs.launchpad.net/ugr-meta/+bug/755189](https://bugs.launchpad.net/ugr-meta/+bug/755189)

But UGR lives on:

[http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/)

Still in very early development but it's definitely alive :)

---

### Post by kansasnoob on 2011-05-12
> **BigCityCat said:**
> People that can't admit when they are wrong bother me. Very immature.

To whom do you refer?

90% of what I've read here has been based on opinion. How can an opinion be wrong?

---

### Post by cecilpierce on 2011-05-13
any body try gNatty ?

[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

---

### Post by kansasnoob on 2011-05-13
> **cecilpierce said:**
> any body try gNatty ?

[http://ubuntuforums.org/showthread.php?t=1754198](http://ubuntuforums.org/showthread.php?t=1754198)

I looked but I already have UGR running fine in "forced-fallback mode" with gnome-panel + metacity :)

People need to stop freaking out about the loss of the traditional Gnome DE.

---

### Post by screaminj3sus on 2011-05-13
> **kansasnoob said:**
> I looked but I already have UGR running fine in "forced-fallback mode" with gnome-panel + metacity :)

People need to stop freaking out about the loss of the traditional Gnome DE.

Agreed. Natty still includes the full vanilla gnome 2 desktop so its certainly not the issue people have made it out to be. And I am sure it will be extremely easy to install gnome 3 in oneric since it will be based on gnome 3 rather than gnome 2.

---

### Post by CreativeReach on 2011-05-13
I tested out gnome3 and its defiantly has qualities that I like but I still prefer Unity for regular use.

But I am glad to here that Shuttleworth said we could install nome3 easily in Ubuntu 11.10!

---

### Post by Mblackwell on 2011-05-14
Honestly, having contributed to Gnome 3 I'm a bit biased but I'll say a couple things:

1) Progress is ongoing with speed. Most users should get a completely smooth experience. NVIDIA users should be using a fairly recent driver to get good performance. If your system can run Compiz it can run Mutter/Clutter. The major speed overhaul happened (or at least was done by) last October.

2) Using Shell gives me roughly a 10% performance drop in graphics intensive applications (read: Unigine Heaven Benchmark). This translates to roughly 5fps. Most apps see no difference in performance. The difference is slightly purposeful in that the ability to unredirect fullscreen windows was dropped from development as time grew tight.

3) Everything Unity does could be done as Extensions to the Shell, with theming for branding.

---

### Post by lucazade on 2011-05-14
> **CreativeReach said:**
> I tested out gnome3 and its defiantly has qualities that I like but I still prefer Unity for regular use.

But I am glad to here that Shuttleworth said we could install nome3 easily in Ubuntu 11.10!

MS said a different thing.. 11.10 will be based on GNOME3 and Unity.
Only gnome-shell is not installed by default, available in repos and installable side by side with Unity.

[https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3)

---

### Post by jjcv on 2011-05-14
> **Mblackwell said:**
> 

3) Everything Unity does could be done as Extensions to the Shell, with theming for branding.

I wonder how long it will take for someone to implement Unity as an extension of Gnome-Shell?

---

