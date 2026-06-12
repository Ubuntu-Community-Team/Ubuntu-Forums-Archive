---
title: "How does modern Ubuntu compare to modern Fedora?"
date: 2009-11-12
forum: Recurring Discussions
---

### Post by Zenith88 on 2009-11-12
Let me start by stating that I have many years of experience working with Redhat from early versions after working with early Slackware.

Now after about 10 years absence in Linux world I am back as my two kids need their first computers built for doing homework and research for science, math and English classes etc. Of course natural choice is Linux for abundance of free software packages. Although they still need Windows for music applications (and I won't debate this part as yet, being aware of the state of free music software for Linux), Linux will be their primary working environment.

Natuarlly I tried Fedora 10 and then 11 first. You can't imagine how disappointed I am with both!

Of course there is some learning curve after 10 year hiatus, but the sheer amount of bugs totally turned me off. I quickly came to realization that Fedora is NOT Redhat that I used to know in production and at home.

Let me cut the BS short and ask a few important questions in the hope of determining suitability of Ubuntu for my purposes. Considering that the machines will be primarily, almost 100% X workstations,

What installer comes with the distro? (anaconda crashes too much on tasks too simple)
What kind of package management tool does Ubuntu use? (Fedora's yum is crazy)
What is the choice of window managers/desktops? (like kde, but could not get rid of gnome in Fedora)
Can I d/l a kernel from kernel.org and simply compile/copy it, install modules and get a working system? (Fedora process of re-rpming the rpms drove me nuts)
Can I expect traditional Unix administration? (in Fedora ifconfig eth0 up does not really work until interface is brought up from KDE plasmoid)
Does Ubuntu support somewhat modern hardware? (anaconda starts only in lame text mode with limited functionality on Geforce 6800, but works fine on Radeon 9800)

I am sorry if this post sounds snappy, you can see that I am pissed after wasting almost one week trying to get Fedora up and running they way I want it on the following machine: MSI 845E Max mobo, P4-1.5 Northwood, GF 6800, Audigy2, 160 GB Seagate. It was problematic to install, slow to run and full of bugs. Slowness is just horrible, specially in X and during compile.

Now let's here about Ubuntu.

Thank you!
Z88

---

### Post by Tahakki on 2009-11-12
Installer - Not sure about the latest version (my computer won't boot Cds anymore...) but I hear Karmic has some nice slideshow-y things. Having installed previous versions of Ubuntu, I can tell you that installation usually goes flawlessly.

Package - Ubuntu uses Synaptic package manager, with which I've no complaints. It's quick, and now that Karmic adds repo keys automatically, it's quite easy to get exactly what you need.

GUI: There's GNOME by default in Ubuntu, KDE in Kubuntu and XFCE in Xubuntu.

Kernel - No experience, sorry.

Unix admin-ing - Not sure. I do know that the root user is disabled by default - ie you can't log in as him but you can still do stuff as root.

I have an old graphics card, but there are three types of nVidia drivers available, and I think one of them's for newer GPUs.

---

### Post by Zenith88 on 2009-11-12
My grievance with yum is mostly with the way it treats dependencies. For example, if I was to uninstall some obscure Gnome application in Fedora, it would result in almost catastrophic snowballing of packages tagged for erasing, resulting in wiping out almost entire OS. Can you believe that tagging a Gnome MP3 player or CD burner can cause dozens or even hundreds of packages to scroll in front of you each tagged for deletion, eventually leading to wiping out my entire KDE and other stuff? I was sitting there in disbelief, but that's the way it is.

Now I am a bit concerned about disabling root account. Is it disabled from X login or from console too? I assume it is possible to drop from X console into text by Alt-F1-5 and log in as any legitimate user? Sometimes root account is simply necessary.

I tried to play with the partition layout during install, and even such a rudimentary task in Fedora as building software raid on 4 drives sometimes ended in a screen saying 'an error occurred, it is unrecoverable' only due to me going back and forth a couple of times. It is nice if Ubuntu installer is more stable than that.

---

### Post by Tahakki on 2009-11-12
The Ubuntu partition editor is GParted. I use it a lot - it's non-detructive, fast and stable. And it looks pretty. :P

Ctrl+Alt+F[Terminal Number] will drop you into the command line. From there you can type 'sudo -i' to work as root. There's a way to enable the root account in X too, but I can't remember.

As for the packages, if, say, I installed Banshee that depended on gstreamer. Removing Banshee would only get rid of gstreamer if no other package required it.

---

### Post by Zenith88 on 2009-11-12
I wonder would the installer fall into text mode, as it does in Fedora when it can't start X on the video card. Again, my grievance is that the text mode install lacks many features of X installer (which was not the case back when the trees were big, i.e. Redhat 5-6-7) and installs only standard layout (from the installer's POV) and a limited set of packages.

---

### Post by louieb on 2009-11-12
> **Zenith88 said:**
> What installer comes with the distro? 

Ubiquity is the name of graphical installer on the **live CD.** Its all right for simple installs. 

The  **alternate CD** uses the Debian text based (n-cursors) installer. Not as pretty but it has more options. If your using raid this is the way to go. 

> Now I am a bit concerned about disabling root account.

If you can Google you can enable it. Just won't find it here. [forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201") 

It is permitted to say if you run the command **sudo -i **it will give you a root shell.

---

### Post by impert on 2009-11-12
I'm surprised that you've had trouble with Fedora. I  haven't had a lot of trouble with either Fedora or Ubuntu, except that with the change to Grub2 things got a bit iffy.
Perhaps your hardware needs a kernel option. 
I don't know why you'd want to compile a kernel in either Ubuntu or Fedora. In Gentoo it's usual to do it, and it takes hours and often fails. A good way to learn if you have the patience.
Root is not completely disabled in Ubuntu. You can give root a password ```
sudo passwd
``` and then  do ```
su root
```and you'll be root until you exit. sudo gives you **almost** root powers for a limited time.
If RAID is a hassle (I've never done it) try multibooting two or more Linux distros at least one on each HD. A large data folder in one HD, tar backups in the other. Keep nothing in /home/user except user preferences. And don't muck about trying to fix problems - go to the other distro, download a recent live CD, and re-install. Distros are free - have twenty if you like. 
Sound and media players are sometimes a problem for rights reasons, but there are two excellent guides on the forum. [Sound]("http://ubuntuforums.org/showthread.php?t=205449") and [Multimedia]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Zenith88 on 2009-11-24
Interesting how after not working with any Unix for almost 8 years I get strange 'looks' for wanting my own custom kernel. Interesting, because when I was working with unices, it was strange not to compile a custom one.

Right now I am running Fedora 12 with a very customized kernel, although yes, it does take about an hour to configure it properly and probably another hour to tweak it a few times for this and that, but the outcome is very rewarding: performance is great, load time is quick and there is no concern that all that unwanted code in kernel and initrd may mess up things.

Basically if it's Ubuntu philosophy to discourage root, then it's not for me - if I am not a root in my own system, it's not unix from my perspective. Thanks for insight, folks!

;) 
):P

---

### Post by Locke_99GS on 2009-11-24
Many of the larger distro's see the security benefit of sudo and a psuedo-rootless system. It's hardly a hinderance, considering how little root is actually required for.

---

### Post by Zenith88 on 2009-12-02
> **Locke_99GS said:**
> Many of the larger distro's see the security benefit of sudo and a psuedo-rootless system. It's hardly a hinderance, considering how little root is actually required for.

Don't get me wrong, I all for security and stuff, but I genuinely believe that restricting the owner of the actual piece of hardware from accessing anything they want in their system is one of the most blatant manifestations of fascism. Microsoft is therefore one of the most fascist organizations in the world. If Linux projects start following the same ideology, it is a very sad development.

If I own the box, the vendor can't tell me: access denied.

"People willing to trade their freedom for temporary security deserve neither and will lose both."

Give your head a shake.

By the way, how do you switch runlevels on a rootless system?

---

### Post by Locke_99GS on 2009-12-02
Nothing is stopping you from accessing things as root, thats what *sudo* and *su* are for, but an actual root **login** is an unneeded security vulnerability which was removed by default from Ubuntu and many other large distro's. You can still enable it, and the information on how to do this is easily obtained outside of this site. 

"root" is still there, just without an actual login.

I'm not trying to argue with you or sway your ideology, I'm just trying to show you that it is hardly worth not using a distro over. 

When I personally find myself requiring root for many activities, rather than using sudo each time I simple use *sudo su* once to switch to root. When I am done, I simply *exit* the root shell.

---

### Post by QIII on 2009-12-02
Please study the term "fascism".  Thanks.

The creators of Ubuntu have not kept you from logging in as root.  As a security measure, they have simply made it unavailable by default.

If you know what you are doing, you don't have to ask how to do it.  If you have to ask how to do it, you probably don't know what you are doing.

---

### Post by snowpine on 2009-12-02
It's not about "fascism"--it's about having a "sane default." 

Back to the original question, I think Ubuntu and Fedora stack up very nicely against each other. Both are kind of arriving at the same place from a different direction, if that makes any sense.

---

### Post by QIII on 2009-12-02
Yes.  Pardon my interruption.  Back to the task at hand.

How they "stack up" is really a matter of your personal sense of aesthetics.  Both are good.  Each has its pros and cons.

What really matters, in the end, is what is most useful to you.  Use what works for you.  That is the power of choice.

(Just don't make that choice based on whether or not access to the root account is enabled by default.)

---

### Post by mikewhatever on 2009-12-02
> **Zenith88 said:**
> Don't get me wrong, I all for security and stuff, but I genuinely believe that restricting the owner of the actual piece of hardware from accessing anything they want in their system is one of the most blatant manifestations of fascism. Microsoft is therefore one of the most fascist organizations in the world. If Linux projects start following the same ideology, it is a very sad development.

If I own the box, the vendor can't tell me: access denied.

"People willing to trade their freedom for temporary security deserve neither and will lose both."

Give your head a shake.

Ubuntu is a manifestation of fascism?! Are you crazy?! Perhaps what you are saying was cool ten years back, but now it's just retarded.:evil:
Oh, and about root restrictions, run sudo su, and you are root.

---

### Post by QIII on 2009-12-02
Oh, I try to hold back, but sometimes ...

Everyone knows "Fascism" and "Nazi" are bad words.  It's easy to use them incorrectly when one does not know what they mean.

Perhaps the OP really wanted to say "onerous" or "oppressive."  Neither of those is the case, either.  But they are probably more what he wanted.

And I'm not sure if he understood what Franklin was getting at, either.

---

### Post by michaelzap on 2009-12-02
> **QIII said:**
> Oh, I try to hold back, but sometimes ...

Everyone knows "Fascism" and "Nazi" are bad words.  It's easy to use them incorrectly when one does not know what they mean.

Perhaps the OP really wanted to say "onerous" or "oppressive."  Neither of those is the case, either.  But they are probably more what he wanted.

He probably meant "authoritarian" in a broad sense, and I expect that we all agree that's a completely inaccurate description of Ubuntu.

Ubuntu doesn't change use a sudo model in order to control or place limits on its users, but rather to make the default installation a bit more hardened from the outside. You can still access and do everything that you can with a root account-enabled distro, you just do it differently (by taking on root privileges, not actually becoming the user "root"). The theory is that this is a safer model for desktop systems, and yes this theory is debated (and yes you can decide that you disagree and change Ubuntu to have a root account if you prefer one).

---

### Post by Locke_99GS on 2009-12-02
Traditionally, every *nix machine on earth had a user called "root", which obviously had root access. Requiring the knowledge of a username *and* its mated password to login to a system, an attacker already knowing the former must exist and knowing it has the access (s)he is looking for, makes entry far easier. Removing the only known information makes it extremely more difficult to illegally enter a system.

Root still exists on modern systems, and you can switch to it and use it as you could had you logged in as it, but you cannot (by default) log in directly as root.

---

### Post by QIII on 2009-12-02
Locke_99GS, you are completely correct.

A brute force attack attempting to find a combination of two separate words is exponentially more difficult than trying to brute force "root" and then some random combination of characters (assuming a strong password.  Weak passwords would make this fairly easy.)

It is difficult to do 

```

For EveryPossibleCombinationOfCharacters1
      
    For EveryPossibleCombinationOfCharacters2

        CanIGetIn(EveryPossibleCombinationOfCharacters1, EveryPossibleCombinationOfCharacters2)

    Loop

Loop

```

---

### Post by ST3ALTHPSYCH0 on 2009-12-02
@ the OP,
It is also notable to put that you can run 
```
gksudo nautilus
```
and open a file browser as root.
Obviously, you are proficient in the terminal and probably don't require a GUI, but it is available from within any admin's DE.

---

### Post by Zenith88 on 2009-12-21
Back to the question I posed earlier: how does one switch to runlevels 1, 2 and 3 in a rootless Ubuntu system?

---

### Post by Locke_99GS on 2009-12-21
Try *telinit* from tty1.

---

### Post by bodhi.zazen on 2009-12-21
> **Zenith88 said:**
> Back to the question I posed earlier: how does one switch to runlevels 1, 2 and 3 in a rootless Ubuntu system?

What ?

Ubuntu uses upstart, so runlevels do not make sense, and the idea of runlevels is provided only for compatibility issues as the transition is made to upstart, and runlevels 2,3,4, and 5 have all been the same on Ubuntu form many years.

so your question shows you have no understanding of Ubuntu , runlevels, or upstart.

Beyond referring you to upstart documentation, what is it you are trying to do exactly ? I suggest you post a support thread as no one is going to see the question is an Ubuntu vs Fedora thread any way.

[http://upstart.ubuntu.com/](http://upstart.ubuntu.com/)

[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

Speaking of which, time to move this to recurring discussions anyways.

---

### Post by Zenith88 on 2009-12-21
> **bodhi.zazen said:**
> Ubuntu uses upstart, so runlevels do not make sense, and the idea of runlevels is provided only for compatibility issues as the transition is made to upstart, and runlevels 2,3,4, and 5 have all been the same on Ubuntu form many years.

so your question shows you have no understanding of Ubuntu , runlevels, or upstart.

I will not be disputing that I have no understanding of Ubuntu. I installed it how long - 2-3 weeks ago and had a chance to play with it how man - 10-15 times after work for half an hour here and there.

But don't you dare telling me that I have no understanding of runlevels. I am 100% positive that I switched runlevels before you were put into your first diaper.

---

### Post by michaelzap on 2009-12-21
> **Zenith88 said:**
> But don't you dare telling me that I have no understanding of runlevels. I am 100% positive that I switched runlevels before you were put into your first diaper.

Given that:
a) Linux was only invented in 1991, and
b) I'd be willing to bet that bodi is older than 19
your hyperbole is almost certainly inaccurate.

You do seem to be coming at this thread with a bit of a chip on your shoulder, which probably won't encourage people to give you further constructive replies.

I suggest you read up on the sudo model and you'll quickly realize that your question doesn't make all that much sense once you understand how that works. As I mentioned before, you are not limited as to what you can do by using sudo instead of root, you just do it slightly differently. There are many threads in these forums explaining and discussing this already, as well as the pages in the Ubuntu wiki and of course Google for a wider overview.

---

### Post by kevCast on 2009-12-22
The elitism is killing me. To the OP, if you want to try a .deb based system that's not "fascist", you could give Debian a go. It's got root only by default.

If you want Fedora stable, try CentOS.

---

### Post by mickie.kext on 2009-12-22
@OP
Or, try Slackware. You said that you used it before. Or beter yet, ArchLinux. It (still) uses old-fashion init and has old-fashion runlevels so you can switch those all day long. Plus, has Pacman so you get dependencies handling and packages are always new. If you have bias against Ubuntu, then just do not use it:). Simple as that.

> a) Linux was only invented in 1991, and
b) I'd be willing to bet that bodi is older than 19
your hyperbole is almost certainly inaccurate.
It is possible that he was switching runlevels on UNIX box...

---

### Post by houseworkshy on 2009-12-22
One of the things I like about Ubuntu is the friendliness of the community, don't often see people getting cross as above ( frustrated sometimes maybe but that's bound to happen ) Please chill a little.
With respect to the original question I'm probably the least informed in the thread but here's my tuppence.
Due to my ignorance I got to the stage of backing up all my work because I needed to reinstall.  As there was nothing too pressing which needed doing I went distro mad for a couple of weeks, courtesy of distrowatch.  A good site which I recomend
I found for ease of use and installation that Unbuntu, Kubuntu, Debian, Puppy, Artistx to be my favorites.  Black and white was the best of the slackware based ones that I tried but as Debian based systems are all I've used before I found it to be tricky, so as you have the slackware experience you will probably like it.
Artistx has a lot of the sort of applications which your children will like already in it's distro however when I ran clamav on it it found a php file which "may" have had a virus signature.  I got that one from a torrent so don't know how authentic it was.
In Ubuntu, which is my favorite, searching in the repositories for studio pulls up many useful media apps.  However, I have had problems with recent releases of the rt kernel so can't recommend Ubuntustudio which a few versions ago would have been first choice for a media system.  I have also had some problems with 9.10 esp with respect to nvidia drivers ( since fixed ) and haven't got my mind round Grub2 yet.  Ubuntu 8.04 lts is superb.  All the points made about root, sudo and gksu above are valid, as you say it has been a decade and internet connections are now very very fast.  The idea of being online ( and where else is one likely to do ones installation, though files can admitedly be cashed ) in root worries me.  This could be ignorance of course but if I need to use root the information is not secret and one can easily do it.  The policy of not posting the info on the forum is really to protect the many beginners who could easily compromise themselves.  Good safe defaults, such as the pre-configured firewall for example, which can be easily be overridden by experts is a sound policy I think.  Remember many, probably most, users have no interest in programing, they simply want to use the applications with out fuss.
Perhaps your best solution would be a multi machine one.  Something astoundingly easy to use and stable, such as Ubuntu, for your kids who can just get on with their music.  For your self something you can get your codeing teeth into, after being involved I presume you like that sort of thing.  You could even take a real flyer, join launch pad and download the alpha's and be part of the team working on the next release ironing out bugs and developing.  But please be friendly....almost all of the others are.
There you go the opinion of a novice, not utterly worthless as perhaps your kids are novices too.  Whatever you choose good luck with it

---

### Post by Zenith88 on 2009-12-24
It boggles my mind that someone thinks that a pseudo-rootless system is more secure than traditional, while sudo requires the same password as current user's to perform root tasks.

In this modern runlevel-free system, how do you put a box in single-user root-only mode? Are you proposing kicking out users and keeping them out manually? I am afraid that I have tons more real life admin experience than most participants on this thread and am simply more qualified to judge practices for what they worth.

In the past I had boxes under my administration that had to be rebooted maybe once a year or even less frequently because they supported SysV init style and I developed a practice for upgrades that only required a reboot in exceptional circumstances. One of them was accidentally buried into the wall during construction project down the road so no one could find it for more than 2 years until they traced twisted pair thru the trunks. It still routed packets just fine. Today a reboot sounds like panacea.

2nding houseworkshy, deb package management is obviously superior to RPM, so redhat based distros are off the list. RPM used to be stable, it no longer is, and same goes about redhat distros themselves. The more I am looking at things with today's linux, the more I am convinced that tar.gz is the way to go. With online updates things are just freaking scary uncontrollable. I am now totally convinced that we are switching to OpenSolaris, everything else is plain outright scary.

---

### Post by unknownPoster on 2009-12-24
> **Zenith88 said:**
> It boggles my mind that someone thinks that a pseudo-rootless system is more secure than traditional, while sudo requires the same password as current user's to perform root tasks.

In this modern runlevel-free system, how do you put a box in single-user root-only mode? Are you proposing kicking out users and keeping them out manually? I am afraid that I have tons more real life admin experience than most participants on this thread and am simply more qualified to judge practices for what they worth.

In the past I had boxes under my administration that had to be rebooted maybe once a year or even less frequently because they supported SysV init style and I developed a practice for upgrades that only required a reboot in exceptional circumstances. One of them was accidentally buried into the wall during construction project down the road so no one could find it for more than 2 years until they traced twisted pair thru the trunks. It still routed packets just fine. Today a reboot sounds like panacea.

If you're such an expert at System Administration why are you asking so many fairly simple questions...

If you want constructive and helpful answers, it would be better to post with a more positive attitude.

---

### Post by michaelzap on 2009-12-24
> Nan-in, a Japanese master in the Meiji era (1868-1912), received a self-declared expert sysadmin who came to inquire about Ubuntu, Fedora, and the sudo model. Nan-in served tea.

While the OP recounted many tales of his own greatness, Nan-in poured his visitor's cup full, and then kept on pouring. The OP watched the overflow until he no longer could restrain himself. "It is overfull. No more will go in!"

"Like this cup," Nan-in said, "you are full of your own opinions and speculations. How can you learn anything from others when nothing more will fit in your cup?"
...

---

### Post by Zenith88 on 2009-12-24
> **unknownPoster said:**
> If you're such an expert at System Administration why are you asking so many fairly simple questions..

Isn't that obvious? It is stated in one of my very 1st posts: you (as in 'open-source developers') keep changing things and I no longer know where you are.

But there is one consistency: no one is ever responsible, it is always someone else's fault and no forum is proper for asking questions. It is always somewhere else where questions have to be asked and it is always my fault that I am not begging on my knees for help.

Fortunately, I no longer **have to** spend countless hours supporting linux by spending sleepless nights staying on top of new development. There were days when I could type an XF86Config by memory from scratch, while my co-worker could do same for sendmail.cf and we are not very proud of that.

While Linux was relatively unknown, it was maintained by a number of dedicated individuals with expert knowledge. Now that every teenager seems to have it on their desktop (and laptop), open source projects are flooded by individuals with horrible coding style and work ethics, needless to say with overblown ego and attitude.

You can blame me for the format in which I am delivering critique of current state of things with Linux all you want. The end result is, quality of the distros will keep going down for as long as you are refusing to admit that there is a problem.

Although I am very critical of the recent Fedora releases, they are miles ahead of Ubuntu with crash report submission system. They have diagnostics and collect it proactively, while on Ubuntu programs simply disappear from screen with not so much as an error message.

The messianic quote above is so pathetic, but the worst part is that you don't understand, that it applies to the poster and not to me. I own a copy of Windows, as well as Cakewalk, Cubase, Sound Forge, Finale and many other pieces of software and time, that I would have to spend just to be able to use open source is worth much more than what I paid for those packages. Until you realize that, it's foolish to have as much attitude as you do.

Humility is indeed a thing of the past.

---

### Post by bodhi.zazen on 2009-12-24
> **Zenith88 said:**
> It boggles my mind that someone thinks that a pseudo-rootless system is more secure than traditional, while sudo requires the same password as current user's to perform root tasks.

Since your cup overfloweth, I shall answer.

Nobody claimed sudo was "more secure", that is a matter of opinion and debate.

Your mistake is that you ripping sudo out of your system without bothering to leek at the features of sudo or looking at the Ubuntu security model. Your arguments make as much sense as a Windows sys admin new to Fedora asking why Fedora uses bar and not foo like windows.

Experienced sys admins use sudo because of it's flexibility and scalability, one has much much finer grain of control over root access.

Oh, and if you bothered to read the sudo man page you would see it is simple to configure sudo to use root's password rather the the uses if that is what you wish.

Every single old school *nix wizards I have ever met reads man pages.

[http://www.sudo.ws/sudo/man/sudo.html](http://www.sudo.ws/sudo/man/sudo.html)

If you *gash* look at that page you will see an entire section on security ;)

---

### Post by bodhi.zazen on 2009-12-24
> **Zenith88 said:**
> Humility is indeed a thing of the past.

When in doubt, go to the source.

Have you considered your posting style ? Perhaps you would get a different response in the community if you adopted a different posting style.

---

### Post by Tibuda on 2009-12-24
> **Zenith88 said:**
> Although I am very critical of the recent Fedora releases, they are miles ahead of Ubuntu with crash report submission system. They have diagnostics and collect it proactively, while on Ubuntu programs simply disappear from screen with not so much as an error message.

[So does Ubuntu]("https://wiki.ubuntu.com/Apport"), but it is only enabled on the testing releases (lucid).

---

### Post by michaelzap on 2009-12-24
> **Zenith88 said:**
> Humility is indeed a thing of the past.

Wow...

Here's the crux of this thread's issue as I see it: It's not even clear what problem you're talking about, or how anyone can help you, or even why you posted to begin with...

You had a relatively specific question that people answered. Apparently you didn't like the answer that you were given or wanted to comment that it was not a very good answer or... something. You've posted far more text about how knowledgeable and experienced you are than anything related to a question or discussion, for reasons unknown since no one is particularly interested in your qualifications when posting here (I ask simple questions all the time and try to answer whatever I can; I never find it necessary to cite my various computer-related experiences whether asking or answering).

You seem to have doubts about the sudo model. That's a reasonable and widely-debated subject on these and many other forums. My only suggestion would be that you first learn a little more about how it works and spend some time using it before condemning it outright, since several of your posts show that you don't quite understand it yet.

But mostly: Take the chip off of your shoulder. No one here is trying to put you down for not knowing something specific to Ubuntu or the sudo model or wants to debate whether you personally are a smart and experienced individual. The point of these forums is to share knowledge and experience, and that means being open to both teaching and learning.

---

### Post by MarcusW on 2009-12-24
An example on how I believe sudo is more secure:

Let's say someone is trying to bruteforce in to your computer through ssh. Instead of just trying "root" and a random password over and over, he now has to guess the username as well. And ssh won't tell you when you got the username right but the password wrong. So he'll pretty much has to bruteforce one password combined with bruteforcing a word in lower case letters. If the root account existed, he'd just need to get the password right.

---

### Post by Locke_99GS on 2009-12-24
@MarcusW.
A spot on example of sudo's security benefit.
See posts #18 and #19 of this thread on pg. 2.

---

### Post by mickie.kext on 2009-12-24
> **Zenith88 said:**
>  I am now totally convinced that we are switching to OpenSolaris, everything else is plain outright scary.
If you do not like Ubuntu because it won't let you login as root, you are going to hate OpenSolaris because OpenSolaris does not even have root as a user. In Nevada builds of OpenSolaris, root is not a superuser, it is a role. You can not log in as root, but you can use pfexec in terminal to elevate privileges and do one command as root (much like sudo). 

Comand su works both in Ubuntu (when configured with sudo passwd) and OpenSolaris, but you cant login as root in either system. Not by default.

---

### Post by Shibblet on 2009-12-24
I've used Mandriva a Fedora derivitave, and was very impressed by the outward appearance.  But after an installation, it was just REALLY slow.  KDE or Gnome. 

I have wondered if it was because I hadn't set it up properly...  Adding drivers and such, but I started thinking...  You know, Ubuntu kind of takes care of that for you, and I happily came back to Ubuntu.

I still wonder to this day if Mandriva is as slow as I first saw, or if it was my bad user error.  ;)

---

### Post by Zenith88 on 2009-12-26
> **mickie.kext said:**
> If you do not like Ubuntu because it won't let you login as root, you are going to hate OpenSolaris
The worst part is that you are convinced that I 'hate' sudo and that's the root cause. Hint: look amount of bugs in very basic functionality of the modern distros. Redhat 5 was miles ahead in stability.

---

### Post by Locke_99GS on 2009-12-26
Redhat is the stable enterprise arm of Fedora. (Or should I say, Fedora is the cutting edge community developed arm of Redhat?) It is supposed to be more stable.

Ubuntu is (generally) one of those cutting-edge distro's. If you want the upmost stability with Ubuntu at the expense of features, use an LTS release of Ubuntu. Debian Lenny is a great option as well, being the parent distro of Ubuntu but extremely stable. 

There is much more hardware nowadays that must be supported, while still supoprting legacy hardware. Most of the issues here stem from the kernel, not a particular distro. Most larger distro's do patch their kernels, and use some bits from the staging tree, but these patches (hopefully) will make it to the mainline kernel, afterwhich all distro's will benefit.

---

### Post by mickie.kext on 2009-12-26
> **Zenith88 said:**
> Hint: look amount of bugs in very basic functionality of the modern distros. Redhat 5 was miles ahead in stability.
OpenSolaris is tesbed for Solaris like Fedora is for Red Hat EL5. OpenSolaris is no more stable than Ubuntu Server Edition and it is not intended for desktop use. And lacks some functionality, like free (as in beer)and up to date multimedia codecs repository (Ubuntu has Medibuntu for that). Also, be prepared  for hell with NIC drivers if you go OpenSolaris route...  Unless you have 10GbE, those work out-of-the-box. Also, repositores have like 10x less packages than Ubuntu so you will probably need to compile something and compiling is not exactly .cmmi procedure like in linux. 

Just don't say nobody warned you:popcorn:

> **Zenith88 said:**
> The worst part is that you are convinced that I 'hate' sudo and that's the root cause. 
I am not convinced in anything. I just tried to help... to a man who asked for help and then flamed everyone who tried to help:confused:

---

### Post by DZ* on 2009-12-27
> **Zenith88 said:**
> 
If I own the box, the vendor can't tell me: access denied.

"People willing to trade their freedom for temporary security deserve neither and will lose both."

Give your head a shake.


If you want root on Ubuntu, type "sudo su -". Hardly "access denied".

If you want to permanently change it to Fedora way, do "sudo passwd" first.

As far as bugs go, you'll find that Ubuntu will have almost about as many as Fedora: the bugs are mostly application-specific ones rather than OS-specific ones. I have both on my machines and it's mostly the same ones that I have to deal with. Fedora tends to have slightly newer packages, sometimes beta versions. E.g. when released, Fedora 12 packed 3.0 beta Thunderbird, but now it is "3.0" (which broke the calendar extension :)).

---

### Post by Zenith88 on 2010-01-05
> **DZ* said:**
> As far as bugs go, you'll find that Ubuntu will have almost about as many as Fedora: the bugs are mostly application-specific ones rather than OS-specific ones. I have both on my machines and it's mostly the same ones that I have to deal with. Fedora tends to have slightly newer packages, sometimes beta versions. E.g. when released, Fedora 12 packed 3.0 beta Thunderbird, but now it is "3.0" (which broke the calendar extension :)).
[SIZE=1]
Not a big fan of Fedora anyway, why?[/SIZE]

But I am very curious why it was necessary to patch kernel 2.6.31 for Ubuntu Studio in such a way, that it no longer supports same VESA modes as the kernel.org one.

[SIZE=1]What happened to the standards in this world? Are some standards more equal than others?[/SIZE]

---

### Post by Locke_99GS on 2010-01-05
Nothing stops you from compiling your own kernel with whatever patches and compile flags you want, if you don't like the way the provided kernels behave.

---

### Post by Zenith88 on 2010-01-07
> **Locke_99GS said:**
> Nothing stops you from compiling your own kernel with whatever patches and compile flags you want, if you don't like the way the provided kernels behave.

Well, see, this is double talk. When I use a custom kernel, I get lambasted for that as some kind of freaky pervert. When I complain that stock kernel is buggered up, you tell me to compile a custom one.

At least there is a (partially incorrect) write-up for compiling a custom kernel for Fedora. That write-up does not work if followed exactly, but it's not hard to figure what's wrong with it.

Is there a set of rules for doing same for Ubuntu Studio? I would compile my own in a heartbeat, if there was procedure for arriving at similarly configured low-latency RT kernel. I'll say it upfront - I am not familiar with realtime kernels, which are required for audio mastering that my boxes are used for.

---

### Post by Locke_99GS on 2010-01-07
Tonnes of people use custom kernels. No issues with that.

The kernel compiles pretty much as it always has - well, it's easier now.

In a nutshell:
Download the kernel, and any patches you want (rt)
Unpack the kernel somewhere.
Unpack and apply patches.
*make menuconfig* to configure the kernel. (or xconfig, gconfig)
Make sure realtime preemtion is enabled in the config, along with anything else you want.
*make && make modules_install* to compile the kernel and modules.
Link, copy, or move the kernel to /boot
*mkinitrd* to build initrd for kernel, or use some kernel packagin tool such as *make-kpkg* to do this for you.
Reconfigure grub
Cross fingers and reboot.


May want to google around to get more precise instructions.

---

### Post by Zenith88 on 2010-01-08
> **Locke_99GS said:**
> Tonnes of people use custom kernels. No issues with that.

The kernel compiles pretty much as it always has - well, it's easier now.

See, for you and me compiling a custom kernel is a natural thing.
I've spent man-years doing just that.

You should have read the insulting comments addressed at yours faithful in the official IRC support channel of one distro, which I 'deserved' by inquiring about how to compile a custom kernel.

The only thing they have not mentioned was that I burned down an orphanage.

Technically, I am wondering if there is a writeup on getting proper patches for Ubuntu Studio. The maker of that distro is not bothering with his distro specific help, rather deferring it to general ubuntuforums.org.

The kernel is tweaked for audio/video so me going at it with the habits acquired in MySQL/Apache/PHP environment may not be that good idea.

---

### Post by Simian Man on 2010-01-08
> **Zenith88 said:**
> 2nding houseworkshy, deb package management is obviously superior to RPM, so redhat based distros are off the list. RPM used to be stable, it no longer is, and same goes about redhat distros themselves. The more I am looking at things with today's linux, the more I am convinced that tar.gz is the way to go. With online updates things are just freaking scary uncontrollable. I am now totally convinced that we are switching to OpenSolaris, everything else is plain outright scary.
That's completely crazy.  I'm also an old Red Hat user - and a current Fedora user, and I can assure you that RPM is much better now than it used to be - largely because of yum.  Also saying that "tar.gz is the way to go" makes no sense because a tarball can contain anything.  Arch uses tarballs for it's package manager which include dependency information.  But older Linux's used  plain tar.gz's which didn't include dependency info and led to sever frustration.

Also you mentioned that you didn't like how yum sometimes will remove many things when you try to remove some part of the system.  Good luck with apt because it's even worse in that regard :).

> **MarcusW said:**
> Let's say someone is trying to bruteforce in to your computer through ssh. Instead of just trying "root" and a random password over and over, he now has to guess the username as well. And ssh won't tell you when you got the username right but the password wrong. So he'll pretty much has to bruteforce one password combined with bruteforcing a word in lower case letters. If the root account existed, he'd just need to get the password right.

That's a silly argument because even on systems where the root account is activated, it is still simple and good practice to disable root logins in ssh.  You don't need to remove the root account for that.  The real benefit (to Ubuntu) of removing the root password is *not* security, but being less confusing to inexperienced users.

---

### Post by Zenith88 on 2010-01-08
> **Simian Man said:**
> That's completely crazy...  The real benefit (to Ubuntu) of removing the root password is *not* security, but being less confusing to inexperienced users.

See, the argument is centered on the notion that a well educated few can decide for the rest of the unwashed masses. Access denied.

---

### Post by Locke_99GS on 2010-01-08
> **Simian Man said:**
>  The real benefit (to Ubuntu) of removing the root password is *not* security, but being less confusing to inexperienced users.

Can't see how it could ever have been confusing; I also don't recall Ubuntu ever saying that sudo was ever anything but the security tool it is today.



Less confusing than logging in as root. :rolleyes: hah.

---

