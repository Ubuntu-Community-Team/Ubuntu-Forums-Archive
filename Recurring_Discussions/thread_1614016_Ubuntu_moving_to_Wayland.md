---
title: "Ubuntu moving to Wayland"
date: 2010-11-05
forum: Recurring Discussions
---

### Post by meborc on 2010-11-05
As there is no discussion yet, I thought I start a thread

Here is Mark's post - [http://www.markshuttleworth.com/archives/551](http://www.markshuttleworth.com/archives/551)

Also Phoronix news - [http://www.phoronix.com/scan.php?page=news_item&px=ODc1Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODc1Ng)

Wayland webpage - [http://wayland.freedesktop.org/](http://wayland.freedesktop.org/)

Any thoughts? :P

---

### Post by Starks on 2010-11-05
This... This is huge.

I haven't heard of Wayland being used for anything more complex than a simple X environment.

To run a distro on it... My god.

---

### Post by Bou on 2010-11-05
I didn't even know Wayland existed until now. Could someone explain the benefits to the end user, as well as the risks it could bring?

---

### Post by ssj6akshat on 2010-11-05
[http://www.omgubuntu.co.uk/2010/11/unity-to-embrace-wayland-display-server/](http://www.omgubuntu.co.uk/2010/11/unity-to-embrace-wayland-display-server/)

---

### Post by Grenage on 2010-11-05
[http://ubuntuforums.org/showthread.php?t=1614016](http://ubuntuforums.org/showthread.php?t=1614016)

---

### Post by Starks on 2010-11-05
Not much is known about Wayland other than its light footprint and flicker-free promise.

Most people still consider it an infant pet project.

---

### Post by meborc on 2010-11-05
:) and I thought moving to Unity was big... now it looks like a minor change in comparison

as Mark said in the blog - it might not be there for Natty, BUT we sure should see some development in that area

also I think Wayland would get a boost in development because of the spotlight it is in :)

---

### Post by MacUntu on 2010-11-05
Getting a little boost from the world's biggest distribution is nice for the project for sure, but I won't start caring until we see something in a usable state.

---

### Post by 3rdalbum on 2010-11-05
This is excellent. I still like X, I think it's an awesome piece of desktop infrastructure.

But to throw so much support behind Wayland is very good; hopefully it'll really get Gnome and KDE developers to come on board with Wayland too, and we'll all benefit from a more featureful and reliable desktop.

---

### Post by V for Vincent on 2010-11-05
Interesting, to say the least. I like how ubuntu is not afraid to push new technologies. Not because newer necessarily means better, but because any software project needs sufficient support to attain its full potential.

---

### Post by NCLI on 2010-11-05
And people say Canonical never contributes to new, unstable projects:
[QUOTE="Mark Shuttleworth"][CENTER]**[SIZE=5]Unity on Wayland[/size]**
[COLOR="DimGray"]Thursday, November 4th, 2010[/COLOR][/center]

The next major transition for Unity will be to deliver it on Wayland, the OpenGL-based display management system. We’d like to embrace Wayland early, as much of the work we’re doing on uTouch and other input systems will be relevant for Wayland and it’s an area we can make a useful contribution to the project.

We’re confident we’ll be able to retain the ability to run X applications in a compatibility mode, so this is not a transition that needs to reset the world of desktop free software. Nor is it a transition everyone needs to make at the same time: for the same reason we’ll keep investing in the 2D experience on Ubuntu despite also believing that Unity, with all it’s GL dependencies, is the best interface for the desktop. We’ll help GNOME and KDE with the transition, there’s no reason for them not to be there on day one either.

Timeframes are difficult. I’m sure we could deliver *something* in six months, but I think a year is more realistic for the first images that will be widely useful in our community. I’d love to be proven conservative on that  but I suspect it’s more likely to err the other way. It might take four or more years to really move the ecosystem. Progress on Wayland itself is sufficient for me to be confident that no other initiative could outrun it, especially if we deliver things like Unity and uTouch with it. And also if we make an early public statement in support of the project. Which this is!

In coming to this view, several scenarios were considered.

One is the continued improvement of X, which is a more vibrant project these days than it once was. X will be around a long time, hence the importance of our confidence levels on the idea of a compatibility environment. But we don’t believe X is setup to deliver the user experience we want, with super-smooth graphics and effects. I understand that it’s *possible* to get amazing results with X, but it’s extremely hard, and isn’t going to get easier. Some of the core goals of X make it harder to achieve these user experiences on X than on native GL, we’re choosing to prioritize the quality of experience over those original values, like network transparency.

We considered the Android compositing environment. It’s great for Android, but we felt it would be more difficult to bring the whole free software stack along with us if we pursued that direction.

We considered and spoke with several proprietary options, on the basis that they might be persuaded to open source their work for a new push, and we evaluated the cost of building a new display manager, informed by the lessons learned in Wayland. We came to the conclusion that any such effort would only create a hard split in the world which wasn’t worth the cost of having done it. There are issues with Wayland, but they seem to be solveable, we’d rather be part of solving them than chasing a better alternative. So Wayland it is.

In general, this will all be fine – actually *great* – for folks who have good open source drivers for their graphics hardware. Wayland depends on things they are all moving to support: kernel modesetting, gem buffers and so on. The requirement of EGL is new but consistent with industry standards from Khronos – both GLES and GL will be supported. We’d like to hear from vendors for whom this would be problematic, but hope it provides yet another (and perhaps definitive) motive to move to open source drivers for all Linux work.[/QUOTE]
[Source]("http://www.markshuttleworth.com/archives/551")

---

### Post by rudihawk on 2010-11-05
This is fantastic! Can't wait :)

---

### Post by forrestcupp on 2010-11-05
Next thing you know, they'll be ditching the Linux kernel, too.

---

### Post by NCLI on 2010-11-05
> **forrestcupp said:**
> Next thing you know, they'll be ditching the Linux kernel, too.
Really doubtful, unless a better, faster, more stable kernel comes along with more software support, at which point I think Linus himself would switch too.

---

### Post by NightwishFan on 2010-11-05
I doubt it, though it is a possibility. Freebsd on Debian is quite nice actually.

---

### Post by ronacc on 2010-11-05
Oh boy this looks like we will be having lots of fun for the next few dev cycles . I wonder what effect this will have on the Linux community at large ? And is Ubuntu prepared to go it alone if most or all of the other major distros don't follow our lead .

---

### Post by teh603 on 2010-11-05
> **Starks said:**
> Not much is known about Wayland other than its light footprint and flicker-free promise.

Most people still consider it an infant pet project.But will it be able to provide 3D accelleration on my intel chipset? /hmm

---

### Post by kaldor on 2010-11-05
> **NightwishFan said:**
> I doubt it, though it is a possibility. Freebsd on Debian is quite nice actually.

BSD for Human Beings?

---

### Post by NightwishFan on 2010-11-05
If the fates decree, then yes. :)

---

### Post by Helkaluin on 2010-11-05
Sounds exciting. Really hope it goes well, though I have my doubts given the current state of the FOSS drivers...

---

### Post by kaldor on 2010-11-05
Ubuntu's really becoming it's own OS as opposed to just another distro.

I love this :)

---

### Post by Simian Man on 2010-11-05
> **kaldor said:**
> Ubuntu's really becoming it's own OS as opposed to just another distro.

I agree, it seems to be at least *trying* to live up to its hype lately.  I wish them well :).

---

### Post by VMC on 2010-11-05
This should shake up the rest of the Linux world. Seemingly out of the blue comes X replacement. Ever since XFree86 died, X hasn't had any competition, which is needed to drive forward to better yourself. Wayland may wake up X.

---

### Post by 3Miro on 2010-11-05
With Unity, 11.04 looked like half of a disaster. With Wayland it will be a complete disaster. 11.10 will be better, but many major issues will persist. Hopefully, they will be able to polish it enough for a stable 12.04, otherwise we will have to wait to 12.10 for the next LTS.

---

### Post by whoop on 2010-11-05
X forwarding over ssh? I must be old school, but I do this now and then...
Wayland forwarding, anyone?

---

### Post by meborc on 2010-11-05
> **whoop said:**
> X forwarding over ssh? I must be old school, but I do this now and then...
Wayland forwarding, anyone?

there was a bit of discussion in the comments section of Mark's blog about this issue... I hope that whatever gets implemented is backward compatible

---

### Post by whoop on 2010-11-05
> **meborc said:**
> there was a bit of discussion in the comments section of Mark's blog about this issue... I hope that whatever gets implemented is backward compatible

Ah yes, I'm reading it now, thanks...

B.T.W. am I the only one that thought/thinks that Wayland was intended for mobile phones and stuff. It only uses a subset of OpenGL used for embedded devices.
It's quite interesting, first unity, which comes from net books, now Wayland. Good times :-D...

---

### Post by Zlatan on 2010-11-05
> **meborc said:**
> As there is no discussion yet, I thought I start a thread

Here is Mark's post - [http://www.markshuttleworth.com/archives/551](http://www.markshuttleworth.com/archives/551)

Also Phoronix news - [http://www.phoronix.com/scan.php?page=news_item&px=ODc1Ng](http://www.phoronix.com/scan.php?page=news_item&px=ODc1Ng)

Wayland webpage - [http://wayland.freedesktop.org/](http://wayland.freedesktop.org/)

Any thoughts? :P

Geez, and after current state of UNE I was afraid I made a wrong decision with Ubuntu... Now I'm so happy about it:) 
Will certainly have couple of beers to Mark & Ubuntu team tonight!

---

### Post by dino99 on 2010-11-05
hm, i feel we dont get it soon, need a bunch of work :(

Looks like Mark try to find its way :)

---

### Post by cecilpierce on 2010-11-05
is there any way to try it ? i tried the web site info and got lots of errors, finally got down to just dri i810 errors after 3 hours of messing, i gave up !!!

---

### Post by andamaru on 2010-11-05
I'm more interested in if Fedora or someone else follows them. I'm all for a change from X.org

> **Simian Man said:**
> I agree, it seems to be at least *trying* to live up to its hype lately.  I wish them well :).
I don't think it's hype, the features of Wayland are what everyone has been trying to force into X.org for the last couple of years.

EDIT: Decided to use English instead of smashing my head on the keyboard

---

### Post by kaldor on 2010-11-05
> **3Miro said:**
> With Unity, 11.04 looked like half of a disaster. With Wayland it will be a complete disaster. 11.10 will be better, but many major issues will persist. Hopefully, they will be able to polish it enough for a stable 12.04, otherwise we will have to wait to 12.10 for the next LTS.

Why is it headed for disaster? At least Ubuntu is finally deviating away from the rest of the Linux projects.

So what if one release is flaky? If 11.04 allows 11.10 to work well, I'll be content.

---

### Post by whoop on 2010-11-05
> **kaldor said:**
> Why is it headed for disaster?
That remains to be seen, although I can understand people calling this strange. Using a desktop (unity) derived from a netbook interface and a display server (wayland) which seems/seemed to be intended for embedded devices like mobile phones...

I for one am enjoying this. The biggest desktop distro is certainly stirring things up :-)

---

### Post by Simian Man on 2010-11-05
> **andamaru said:**
> I don't think it's hype, the features of Wayland are what everyone has been trying to force into X.org for the last couple of years.


No I mean that, really for the first time ever, Ubuntu is doing something to set itself apart from other Linux distros.  The hype I was discussing was about Ubuntu itself.

---

### Post by Starks on 2010-11-05
Only if Fedora doesn't manage to ship Wayland first.

---

### Post by Red_Steve on 2010-11-05
"mark says: (permalink) 
November 5th, 2010 at 4:01 pm
@Tim

It&#8217;s highly unlikely that the default Ubuntu install in a year will be on Wayland. It&#8217;s possible that there will be versions of Ubuntu that use it, or proof-of-concept images, by then. More importantly, we won&#8217;t make it the default until it really is widely supported and supportable, by folks using a wide variety of hardware providers. And as for network connectivity, there&#8217;s sufficient time between now and then for these problems to get solved.

And finally, you&#8217;ll still be able to host an X application on a Wayland desktop in Spain. It will feel a little old, perhaps, because everything else on your machine in Spain will be crisper, but you&#8217;ll still be able to do it."
-http://www.markshuttleworth.com/archives/551#comments

No need to fear anything. Let's lay back and have them work it out ;)

---

### Post by MasterNetra on 2010-11-05
> **whoop said:**
> that remains to be seen, although i can understand people calling this strange. Using a desktop (unity) derived from a netbook interface and a display server (wayland) which seems/seemed to be intended for embedded devices like mobile phones...

I for one am enjoying this. The biggest desktop distro is certainly stirring things up :-)

+1

> **Grenage said:**
> [http://ubuntuforums.org/showthread.php?t=1614016](http://ubuntuforums.org/showthread.php?t=1614016)
+1

*pokes a admin for a thread merge*

---

### Post by CharlesA on 2010-11-05
Threads merged. I'm leaving it in the cafe for the moment.

---

### Post by NCLI on 2010-11-05
> **3Miro said:**
> With Unity, 11.04 looked like half of a disaster. With Wayland it will be a complete disaster. 11.10 will be better, but many major issues will persist. Hopefully, they will be able to polish it enough for a stable 12.04, otherwise we will have to wait to 12.10 for the next LTS.
Please read the blog before posting. This won't hit Ubuntu as the default display server for at least two releases.
> **whoop said:**
> Ah yes, I'm reading it now, thanks...

B.T.W. am I the only one that thought/thinks that Wayland was intended for mobile phones and stuff. It only uses a subset of OpenGL used for embedded devices.
It's quite interesting, first unity, which comes from net books, now Wayland. Good times :-D...
Well, that subset is(naturally) focused on power saving and being lightweight. I'd say that's a good thing for a display server, but I will admit that I'm no expert.

---

### Post by andamaru on 2010-11-05
> **Simian Man said:**
> No I mean that, really for the first time ever, Ubuntu is doing something to set itself apart from other Linux distros.  The hype I was discussing was about Ubuntu itself.

Sorry, about that. I haven't been myself all day

---

### Post by sudoer541 on 2010-11-05
Does this mean that Flash will work better than before?

---

### Post by cariboo on 2010-11-05
Probably not, I personally can't wait for the day when flash is completely gone.

---

### Post by Lancro on 2010-11-05
It sounds great, but aplications made for X will be compatible?, full compatible?, I mean, I want aplications made for linux too, not only the ubuntu ones, I think Im not understanding it nice, I have to improve my english...

---

### Post by cariboo on 2010-11-05
> **Lancro said:**
> It sounds great, but aplications made for X will be compatible?, full compatible?, I mean, I want aplications made for linux too, not only the ubuntu ones, I think Im not understanding it nice, I have to improve my english...

Go back to the [first]("http://ubuntuforums.org/showpost.php?p=10074911&postcount=1") post, and click the third link. That should answer some of your questions, the conversion to Wayland is at least a year away,so there's lots of time to get more info.

---

### Post by lightningfox on 2010-11-05
Will Wayland work with current proprietary Linux graphic card drivers (eg Nvidia) ?

---

### Post by ubudog on 2010-11-05
> **cariboo907 said:**
> Probably not, I personally can't wait for the day when flash is completely gone.

Me either.  I have had a lot of trouble with it over the years....

---

### Post by mmix on 2010-11-05
[http://www.osnews.com/story/23998/Finally_Ubuntu_Ditches_X_Switches_to_Wayland](http://www.osnews.com/story/23998/Finally_Ubuntu_Ditches_X_Switches_to_Wayland)

I love it!!!

FBUI, wayland, DirectFB, ... YEAH!!

---

### Post by sudoer541 on 2010-11-05
its nice to see ubuntu making some drastic changes! Looks like Canonical never intended to create a an ordinary Linux OS to begin with (which is good!!!).  
I am glad to see that X has a competitor now (just like open office with libre office
Ohhh!!! maybe Adobe may release a better flash player for ubuntu (since Wayland is less complex than X)
Does Abobe Flash depend on X server at all? Does anyone know btw?

---

### Post by ubudog on 2010-11-05
> **sudoer541 said:**
> its nice to see ubuntu making some drastic changes! Looks like Canonical never intended to create a an ordinary Linux OS to begin with (which is good!!!).  
I am glad to see that X has a competitor now (just like open office with libre office
Ohhh!!! maybe Adobe may release a better flash player for ubuntu (since Wayland is less complex than X)
Does Abobe Flash depend on X server at all? Does anyone know btw?

YEAH!  [-o< (prays for new flash player)

---

### Post by mmix on 2010-11-05
no need flash player(zeroday), instead,
vlc for wayland/fbui/directfb, youtube-dl/chromium url, winff, etc

---

### Post by ubudog on 2010-11-05
> **mmix said:**
> no need flash player(zeroday), instead,
vlc for wayland/fbui/directfb, youtube-dl/chromium url, winff, etc

Is zeroday any good?

---

### Post by mmix on 2010-11-05
[http://www.thesecurityblog.com/2010/11/zero-day-flash-bugs-squashed-by-adobe/](http://www.thesecurityblog.com/2010/11/zero-day-flash-bugs-squashed-by-adobe/)

Adobe seems fixed it, anyway, i don't trust closed-source software.
Always, dirty works need some security holes, intended or not.

---

### Post by 3rdalbum on 2010-11-06
I am hoping it will push the Xorg developers to improve X so that Ubuntu doesn't have any reason to adopt Wayland.

I doubt Ubuntu will be the first desktop distro to ship with Wayland. Probably Fedora.

---

### Post by ssj6akshat on 2010-11-06
> **NCLI said:**
> Really doubtful, unless a better, faster, more stable kernel comes along with more software support, at which point I think Linus himself would switch too.

Wins 3 internets.

---

### Post by ssj6akshat on 2010-11-06
I have an urge to interview the creator of Wayland, gimmie support.

---

### Post by madhi19 on 2010-11-06
If Cannonical manage to pull this off it going to be big especially if they manage to do it before other major distro! It would set Ubuntu as a leader instead of the follower label that some peoples have attached to the project. And nobody will be able to say that it just a debian derivative anymore!

---

### Post by MasterNetra on 2010-11-06
> **madhi19 said:**
> If Cannonical manage to pull this off it going to be big especially if they manage to do it before other major distro! It would set Ubuntu as a leader instead of the follower label that some peoples have attached to the project. And nobody will be able to say that it just a debian derivative anymore!

It still originally came from and still is largely based on Debian regardless if it uses Wayland or not. So I respectively disagree with your last statement. A mere follower Ubuntu is not, but a Debian derivative it still is.

---

### Post by MisterGaribaldi on 2010-11-06
Well, I dunno about any of the rest of you guys, but I'm looking forward to it. I think my post on Mark's blog really says it all, but to just recap one part, it is important for there to be some movement in the fundamental structures of Linux, and sometimes it takes a major "mover and shaker" to make it happen. I'm glad Mark isn't shirking away from that.

---

### Post by sudoer541 on 2010-11-07
Anyone know if Compiz depends on X server at all?
Does that mean that they will get rid of Compiz? :0

---

### Post by NightwishFan on 2010-11-07
Compiz is going to be the base of the Ubuntu desktop soon, so I doubt it. :)

---

### Post by chessnerd on 2010-11-07
Interesting.

We'll see how this goes. I'm still skeptical that Ubuntu can have Unity ready on X by 11.04 (Natty Narwhal), let alone spending any time developing for Wayland (even if that development is going towards future builds). However, this is big news nonetheless.

To me, 12.10 (Quizzical Quail?)  looks like the next build that could implement Wayland as I would hope they wouldn't use it in the 12.04 (Perfect Penguin?) LTS unless it had already been successfully implemented by 11.10 (Outrageous Orangutan?), which to me seems unlikely.

I am glad that Ubuntu is looking at Wayland, though. When the Wayland team can say that the most widely used Linux desktop distro is planning on implementing their work, that makes the project a lot more attractive to developers and investors.

---

### Post by MisterGaribaldi on 2010-11-07
While I know they're switching to Unity for the next release, I've read nothing that suggests Mark thinks they're actually going to roll out Wayland for quite a while. His time line seems to be somewhere in the 1-4 year range, which is fine. Something like this shouldn't be rushed at all.

---

### Post by ssj6akshat on 2010-11-07
> **sudoer541 said:**
> Anyone know if Compiz depends on X server at all?
Does that mean that they will get rid of Compiz? :0

smspillaz said the due to the new architecture in 0.9, they can remove X out of the core and move it to plugins instead.

---

### Post by v1ad on 2010-11-07
:D i'm happy, and we should have it by 11.10

---

### Post by meborc on 2010-11-07
> **v1ad said:**
> :D i'm happy, and we should have it by 11.10

I hope we will get some dev PPA or something to test the development already in this cycle... :)

---

### Post by cecilpierce on 2010-11-07
+1 
me to !

---

### Post by nerdopolis on 2010-11-07
There is a PPA here, 
[https://launchpad.net/~xorg-edgers/+archive/wayland/+packages](https://launchpad.net/~xorg-edgers/+archive/wayland/+packages)

The packages have not competed building yet, so you cant install it just yet...

---

### Post by NCLI on 2010-11-07
> **nerdopolis said:**
> There is a PPA here, 
[https://launchpad.net/~xorg-edgers/+archive/wayland/+packages](https://launchpad.net/~xorg-edgers/+archive/wayland/+packages)

The packages have not competed building yet, so you cant install it just yet...

PPAs are awesome.

---

### Post by ubudog on 2010-11-07
> **NCLI said:**
> PPAs are awesome.

Yeah...

---

### Post by cecilpierce on 2010-11-08
any body trying this ? i added the ppa and when i try to install it i get wayland:
 Depends: libeagle-dev  but it is not installable !!!

---

### Post by NightwishFan on 2010-11-08
I do not think the ppa is ready yet, might want to wait a bit. Though others can confirm.

---

### Post by Johnsie on 2010-11-08
I'm thinking that Ubuntu is clearly starting to go off the rails. Purple backgrounds, gwibber, unity and now this. Time to jump ship methinks.

---

### Post by NightwishFan on 2010-11-08
> **Johnsie said:**
> I'm thinking that Ubuntu is clearly starting to go off the rails. Purple backgrounds, gwibber, unity and now this. Time to jump ship methinks.

Do not let the door hit you on the way out.

---

### Post by Johnsie on 2010-11-08
The ugly purple door or the ugly brown one? ;-)

---

### Post by cecilpierce on 2010-11-08
> **NightwishFan said:**
> I do not think the ppa is ready yet, might want to wait a bit. Though others can confirm.

i guess your right, i just tried it in Natty and it don't show up in the package manager at all !
i like trying new stuff even if i don't like it.

---

### Post by ZarathustraDK on 2010-11-08
Refreshing news for once.

I've had my fair share of headaches with X.org (up for calculating modelines for unknown displays? Anyone?).

Worst-case scenario: it fizzles. NVidia has (at this point in time) said that they wont support Wayland with driver (that could change though).With it, Unity fizzles, and Kubuntu will take the lead as the *buntu of choice. People want a composited desktop, wasting CPU-power on rendering windows is silly, that's what the GPU is for. As the prevalence of composite-desktops become more frequent, Gnome 2.3 will start looking like Windows XP with yodm3d running.

Best-case scenario: The Noveau-drivers are brought up to feature-parity with the proprietary ones. Wayland and Unity integrate like a hand in a glove. We get the replacement for the Gnome 2.3 desktop we've always wanted.

I really like how this move is enticing "stuff we want" to get made. New X-server, open source graphics-drivers, a worthy composited Gnome 2.3-replacement, HELL YEAH!

---

### Post by kaldor on 2010-11-08
> **NightwishFan said:**
> Do not let the door hit you on the way out.

I agree with Christopher Lee.

What does a default wallpaper have to do with quality?

---

### Post by whoop on 2010-11-08
> **Johnsie said:**
> I'm thinking that Ubuntu is clearly starting to go off the rails. Purple backgrounds, gwibber, unity and now this. Time to jump ship methinks.

It's about time some distro got off rails, they're all the same now :-D

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-11-08
First they change our sound server. Then they change our default IM apps. Then they remove GIMP from the .iso. Now they're changing the GNOME shell AND the display server.

What's next, ubuntu abandoning Linux kernel and using Hurd instead? If their track record of adopting early-alpha software for production releases is anything to go by...

---

### Post by vexorian on 2010-11-08
Oh fun with slippery slopes, but you'd be surprised - I'd love them to ditch Linux and go with Solaris or even Hurd actually. The Linux kernel is by far one of the greatest reasons of rants about Ubuntu. 

The move to Wayland is a longer term than usual thing Canonical is doing. Mark gave a estimate of a whole year wait and it is goign to be subject to delays if it is still unstable then. Plus Wayland's architecture makes more sense for what ubuntu intends to be. X server will still be available and ready for people that intend to use thin clients and things like that or want to be nostalgic about it. 

Overall, it can only add competition in an area in which GNU/Linux has been VERY stagnant. I think that X being the ONE and only graphics server used in Linux distros has allowed the project to go into complacency which is not really what we see in other areas (like desktop environments and apps). Some healthy competition and new choices in regards to graphics servers will improve Linux in the long term.

Which leads me back to the kernel. I wish we had two GPLed kernels competing with each other because Linux could use some help...

Thanks for reminding us about pulseaudio... It caused a lot of headaches at first but now after the years it just works great in comparison to what we had before the bold move...

> It's about time some distro got off rails, they're all the same now:)
Innovation needs projects to take risks and I think that we can all agree that innovation is necessary in Ubuntu. I can't tell for now if the switches are going to be good or bad. But I do think both Unity and Wayland have potential in what ubuntu was aiming to be. Only time can tell. I liked the purple background, but you can change the background and I bet you that you will be able to use ubuntu with gnome (betting there will be a official Canonical distro that does that). As well as you can use KDE if you wish and I also bet that using X will not be banned or anything. There are blogs out there mentioning the words 'dumping' which is not remotely the case.

---

### Post by bapoumba on 2010-11-08
Welcome to our recurring discussions. Please have a seat.

---

### Post by cecilpierce on 2010-11-08
where is it going next ? been moved 3 times !

---

### Post by bapoumba on 2010-11-08
> **cecilpierce said:**
> where is it going next ? been moved 3 times !
Not that I can see. Threads have been merged in, but it is the first move. Well, there is nothing to see below recurring ^^

---

### Post by simpleblue on 2010-11-08
> **sudoer541 said:**
> Anyone know if Compiz depends on X server at all?
Does that mean that they will get rid of Compiz? :0

Here is an article on it:


Compiz to be Rewritten for Ubuntu Wayland

[http://ostatic.com/blog/compiz-to-be-rewritten-for-ubuntu-wayland?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ostatic+(OStatic](http://ostatic.com/blog/compiz-to-be-rewritten-for-ubuntu-wayland?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ostatic+(OStatic))

---

### Post by bonixavier on 2010-11-08
> **3rdalbum said:**
> I doubt Ubuntu will be the first desktop distro to ship with Wayland. Probably Fedora.

> **madhi19 said:**
> If Cannonical manage to pull this off it going to be big especially if they manage to do it before other major distro! It would set Ubuntu as a leader instead of the follower label that some peoples have attached to the project. And nobody will be able to say that it just a debian derivative anymore!

I still need to read way more before I'm convinced that Wayland is here to replace X. Ubuntu may be the biggest distribution, but it does not dictate the standards. If it were Patrick Volkerding or the Debian developers saying they believe Wayland is the future, I'd believe it in a heart-beat, but Canonical...

---

### Post by Decatf on 2010-11-08
> **simpleblue said:**
> Here is an article on it:


Compiz to be Rewritten for Ubuntu Wayland

[http://ostatic.com/blog/compiz-to-be-rewritten-for-ubuntu-wayland?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ostatic+(OStatic]("http://ostatic.com/blog/compiz-to-be-rewritten-for-ubuntu-wayland?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+ostatic+%28OStatic"))

Misleading blog is misleading.

---

### Post by cecilpierce on 2010-11-09
how do i fix this ?

error while loading shared libraries: libwayland-server.so.0: cannot open shared object file: No such file or directory

---

### Post by nerdopolis on 2010-11-09
Wait 10-20 minutes, It was a problem with the way the package was built.

It seems that a change has been tried, but the new package needs to start building, and seems to be scheduled to start soon


Then do a sudo apt-get update && sudo apt-get dist-upgrade

---

### Post by cecilpierce on 2010-11-09
> **nerdopolis said:**
> Wait 10-20 minutes, It was a problem with the way the package was built.

It seems that a change has been tried, but the new package needs to start building, and seems to be scheduled to start soon


Then do a sudo apt-get update && sudo apt-get dist-upgrade

Thanks, I was getting head aches !

---

### Post by nerdopolis on 2010-11-09
I had to manually install libgles2-mesa, because the now finished updated Wayland needed it.

It also appears the clients have not built properly

---

### Post by cecilpierce on 2010-11-09
Now I get this ?

DRI2: failed to authenticateSegmentation fault

---

### Post by amauk on 2010-11-09
[http://www.phoronix.com/scan.php?page=news_item&px=ODc2Nw](http://www.phoronix.com/scan.php?page=news_item&px=ODc2Nw)

---

### Post by Nightstrike2009 on 2010-11-09
My opinion is as long as the ATI and NVIDIA (and other GPU) drivers are supported in both open-source and closed-source drivers, wayland shouldn't be a problem, compiz is now supported by Ubuntu so I doubt Compiz will have issues with Wayland.

---

### Post by bonixavier on 2010-11-09
Linux Mint already said they have no plans of jumping on that boat. [http://www.omgubuntu.co.uk/2010/11/linux-mint-no-to-unity-no-to-gnome-shell/](http://www.omgubuntu.co.uk/2010/11/linux-mint-no-to-unity-no-to-gnome-shell/)

---

