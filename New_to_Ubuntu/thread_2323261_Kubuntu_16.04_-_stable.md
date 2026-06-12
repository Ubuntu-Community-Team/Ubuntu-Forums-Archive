---
title: "Kubuntu 16.04 - stable?"
date: 2016-05-04
forum: New to Ubuntu
---

### Post by DerekP on 2016-05-04
Hi everyone,

I'm only a dabbler with Linux. I've been keeping my eye on KDE Plasma 5x for a while because it looks so good, but pre 5.5 i read about a lot of bugs. I haven't been keeping up since then and i thought i'd ask here. I've got 3 questions atm:

1. Is it finally stable/usable enough for a casual user - who just wants to USE his PC (not fix it constantly)?
2. What version of Plasma is used in Kubuntu 16.04?
3. If i use Kubuntu 16.04, can i keep updating Plasma to the latest stable version as they release them (whilst still being on Kubuntu 16.04)? Like using a PPA or something?

Thanks :)

p.s. i should note that i was using a VM at a friends place with Kubuntu 16.04 and some elements within crashed a few times. It still chugged along, but weird errors and such. Being a VM i didn't take it as a completely representative experience.

---

### Post by mastablasta on 2016-05-04
> **DerekP said:**
> Hi everyone,

1. Is it finally stable/usable enough for a casual user - who just wants to USE his PC (not fix it constantly)?



Stable means something else = basically bugs are known and stuff is not changing. Fixes and patches will be made until support period runs out.


> 
2. What version of Plasma is used in Kubuntu 16.04?


Info:
> Kubuntu 16.04 comes with **KDE Applications 15.12**
source: [http://kubuntu.org/news/kubuntu-16-04-lts-release-anouncement/](http://kubuntu.org/news/kubuntu-16-04-lts-release-anouncement/)


> 
**Plasma 5**, the next generation of KDE's desktop has been rewritten to make it smoother to use while retaining the familiar setup.  The [fifth set of updates to Plasma 5 (current release and current bugfixes for January)]("https://www.kde.org/announcements/plasma-5.5.5.php") is the default in this version of Kubuntu. and that is **KDE Plasma 5.5.5**
Source:  [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes/Kubuntu)

> 
3. If i use Kubuntu 16.04, can i keep updating Plasma to the latest stable version as they release them (whilst still being on Kubuntu 16.04)? Like using a PPA or something?


yes there is always that option, just don't complain if it breaks anything as it will no longer be considered stable by Kubuntu ;-) note that PPA can still be considered stable by upstream.

---

### Post by RobGoss on 2016-05-04
Hello and welcome, When you say is it stable you're asking if it has problems well I think it's safe to say every operating system has it's problems the question is does Ubuntu preform well and the answer is yes, with out a dough. Linux has a great group of people here that's always willing to give new and old users a helping hand that makes using it so much easier.

Using a VM machine will not give you the full experience in my option that's why I never use it, not saying that it's not a good tool to use to test drive new distribution when it's available but I feel better when I'm testing it on a real live installation. 

I use Ubuntu everyday and I would have to **98% **of the time I'm enjoying how it preform and all the features it offers and not having to fit things that are broken

---

### Post by neu5eeCh on 2016-05-04
I'm currently using Kubuntu 16.04. The version of Plasma is 5.5.5

I've also been using Plasma 5 since 15.04. I've had no instability issues or problems with it. In fact, I much prefer to 4 and have since 5.1.x. My impression is that most of the problems are for the non-casual user, those using more than one monitor for example. But take a look at this:

[https://btux1984.wordpress.com/2015/10/15/is-the-kde-5-desktop-stable-enough-for-normal-users-or/](https://btux1984.wordpress.com/2015/10/15/is-the-kde-5-desktop-stable-enough-for-normal-users-or/)

Also, if you install 16.04, be sure and revert to (or stay with) Kernel 4.2, [COLOR=#ff0000]**not**[/COLOR] 4.4. The latter is a disaster (which has nothing to do with Ubuntu/Kubuntu). 

See here:

[http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode](http://askubuntu.com/questions/688306/text-missing-garbled-after-laptop-resumes-from-sleep-mode)

And here:

[http://www.spinics.net/lists/intel-gfx/msg82135.html](http://www.spinics.net/lists/intel-gfx/msg82135.html)

Lastly, if you stick with 16.04, there's a new distro/repository starting up called [KDE NEON]("http://neon.kde.org/"). This will be based on Ubuntu 16.04 so that you can either install an upcoming NEON "Distro" or use the NEON repository with your installation of Kubuntu. This will update Plasma for the life of 16.04. No more chasing after Ubuntu releases. The down side is that there is bound to be slightly more instability, but nothing like a rolling release. FYI: NEON is still formative and very BETA.

---

### Post by DerekP on 2016-05-06
Thanks for the advice/info. The commentary on <5.4 seems pretty negative. I suppose it's too much to expect all those issues and doubtless many more to have been resolved in 5.5. God i wish so much that i could get new and awesome + reliability wrapped up nicely :)  I might have to wait another few months for 16.04.x and Plasma 5.7?  Or i can just give it a shot. Currently i have Mint Cinnamon 17.03 on my second boot but i've grown to dislike the file management (Nemo) and the lack of polish vs KDE P5 i experienced in the VM. It's also gotten quite buggy of late. Weird things like fonts being very fuzzy at boot and not shutting down when i ask it to. So using that as an excuse i'll put something else on it. :)

I was reading a separate review from the desk of Dedoimedo on the Unity flavour and he's not at all positive about 16.04 :( Pity, because he loved 14.04.

[http://www.dedoimedo.com/computers/ubuntu-xerus.html](http://www.dedoimedo.com/computers/ubuntu-xerus.html)

He notes that these issues will plague 'downstream' like Kubuntu and Mint. So that sux :(

---

### Post by DerekP on 2016-05-06
> **VTPoet said:**
> Lastly, if you stick with 16.04, there's a new distro/repository starting up called [KDE NEON]("http://neon.kde.org/"). This will be based on Ubuntu 16.04 so that you can either install an upcoming NEON "Distro" or use the NEON repository with your installation of Kubuntu. This will update Plasma for the life of 16.04. No more chasing after Ubuntu releases. The down side is that there is bound to be slightly more instability, but nothing like a rolling release. FYI: NEON is still formative and very BETA.

As clearly evidenced, i'm not an OS expert, but that KDE Neon project seems much like how Windows rolls. Correct me if i'm wrong, but Windows Vista, 7, 8 and 10 all share a near identical kernal and all that has really changed is the UI/DE. Would that be correct?

---

### Post by buzzingrobot on 2016-05-06
I found it quite stable and usable. If a user has issues with KDE, then that user has to depend on KDE, not the distribution that packages it, to address them.

KDE itself seems to be getting to the point that users don't need to run the latest updates simply to get a workable system.

I think I'd avoid Neon until it establishes a track record for its user releases, as opposed to tech preview release targeting devs.

---

