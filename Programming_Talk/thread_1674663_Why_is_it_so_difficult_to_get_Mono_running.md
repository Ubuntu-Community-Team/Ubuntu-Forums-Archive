---
title: "Why is it so difficult to get Mono running?"
date: 2011-01-24
forum: Programming Talk
---

### Post by JHorrocks on 2011-01-24
Back in October 2010, I changed over all my servers (7 at the moment), 12 staff PC's and around 5 laptops over to ubuntu 10.04 (servers) and 10.10 (desktop)... all fine for the servers and the staff for except me.

I am a Microsoft developer and for the past xxx amount of years been using visual studio, sql server etc... 

So, swapping to ubuntu for me had only the 1 issue, installing Mono 2.8 (because I develop .NET framework 4.0) and also MonoDevelop... I am still trying to install a working copy of Mono and MonoDevelop that i can use so that I can 100% get rid of my Windows 7 virtual PC.

I have followed 100's of tutorials, ran scripts made by people that auto install etc... and each one has its issues.

I wish to thank everyone who has ever posted info on how to do it etc, but I just for the life of me cannot get a working copy.

Is there a virtual image I can download that is already setup and working? I would pay for this if there is.. If not, when will it ever be available in the repository?

---

### Post by directhex on 2011-01-24
> **JHorrocks said:**
> Is there a virtual image I can download that is already setup and working?

Of SUSE, yes. [http://ftp.novell.com/pub/mono/appliance/2.8.2/Mono-2.8.2-vmx.zip](http://ftp.novell.com/pub/mono/appliance/2.8.2/Mono-2.8.2-vmx.zip)

> If not, when will it ever be available in the repository?

[http://wiki.debian.org/Teams/DebianMonoGroup/DonationRegistry](http://wiki.debian.org/Teams/DebianMonoGroup/DonationRegistry) is a good way to encourage development.

---

### Post by JHorrocks on 2011-01-24
@[directhex]("http://ubuntuforums.org/member.php?u=176650"), it is too early in the morning to say I love you.... so thanks for the advise and the 2 links.

I am downloading the vmx now (will take a while) and after I have set it up and played around with it, I will report back my finding incase others are interested.

As for the encourage development link, I think I get what thats about.. I can click on amazon and buy them a book/dvd etc... right?

Thanks again for the help :)

---

### Post by kemra on 2011-01-25
Someone wrote a script to help compile it from source under Ubuntu and Fedora:

[http://www.integratedwebsystems.com/2010/10/mono-2-8-install-script-for-ubuntu-fedora/]("http://www.integratedwebsystems.com/2010/10/mono-2-8-install-script-for-ubuntu-fedora/")

The  mainter of the Mono 2.8 package said it would be a long time before it was available in a ppa, so who knows how long until it makes it into the official repos?

---

### Post by JHorrocks on 2011-01-25
Thanks for your help, infact the link u sent was the original script that I followed back in October 2010 and thanks to Nathan, who wrote the script replied to many of my questions and helped loads. But still never managed to get everything working.

What I mean by that is after weeks of running scripts like nathans, and configuring everything like apache, mono embodiment etc nothing ever did run. Sometime mono would run in 2.8, but then monodevolop wouldnt run, changed the environment and then debug wouldn't run.

The list is endless as I have been trying since October. So I would like to go back to my original question which was why is it so difficult on ubuntu? I was sent a link to download a virtual image today via this thread which after starting wasn't ubuntu 

Is there something I need to know why ubuntu doesn't have support for mono/monodevolop ?

---

### Post by directhex on 2011-01-25
> **JHorrocks said:**
> Is there something I need to know why ubuntu doesn't have support for mono/monodevolop ?

It has plenty of support. It's shipped with Mono apps out of the box for 5 years.

What it doesn't have is rapidly available packages for new Mono releases - the focus is on bug-fixing and stability for the *apps*, with development environment stuff really as a secondary.

And the root problem?

[img]http://schoolloans.org/blog/wp-content/uploads/2009/06/money_tree.jpg[/img]

A volunteer effort happening in spare time. There are limits on how much can be done.

In the case of 2.8+, it presents a manpower problem. In Debian/Ubuntu we run a single-classlib setup, so users will ONLY have libraries for one version of .NET installed at once. Currently, that means .NET 2.0 - but in Mono 2.8, the default becomes 4.0, and in order to provide a single classlib, then every Mono package (about 100) needs to be rebuilt, in the correct order, using the 4.0 compiler; fixing bugs along the way. Not to mention the work on the mono package itself - porting our array of patches from 2.6.7, for example.

Doing the work in Ubuntu is not feasible for manpower reasons - and doing it in Debian is on hold until Debian 6.0 releases in 2 weeks' time. But the entire transition, all 100 packages, needs to happen within a single release cycle - otherwise with a mix of 2.0 and 4.0 libraries required, the Mono apps installed by default in Ubuntu will bloat up too far to be used.

Realistically, I don't think it will officially make it into Natty (perhaps a PPA, though).

Of course, there's a side issue, and the problem you had with *using* your 2.8. There's a workaround which not ONE "easy mono 2.8" script has ever used, which removes all the pain. But I don't really want to share it out loud, since I'm the bugger who has to deal with all the bug reports when people have weird issues on mixed systems.

---

### Post by JHorrocks on 2011-01-25
The root problem, each time i run the same script can be different each time (same script). 

I can start over 1 more time, new install of ubuntu, run the script from nathan and can give you at least 5 different errors as I install.

As a commitment to this community, I will put a fresh install of ubuntu 10.04, and run the script you tell me to run... I can tell you 100% it will fail... BUT.... can you please tell me what I need to report from the errors in order to help make the install better?

Which logs, where to look etc...

If I could create this install and help others I would gladly obligize, but without knowing how this is supposed to install, i am in the dark.

Thanks guys (maybe girls) for all your comments and help..

James

---

### Post by JHorrocks on 2011-01-25
[@directhex]("http://ubuntuforums.org/member.php?u=176650")

You are without a doubt trying to help with this issue, and in no way am i criticizing the way mono/monodevelop works at the moment.

In fact, I am shocked that community people like yourself are able to even think of getting something like this working, never mind actually doing it!!!!!

As a business owner who wants to shift over to ubuntu(or any linux flavour that supports .NET 4.0) I am greatful for any input, help, advice etc and if I can be at all any help in trying to do setups.... reporting issues etc.. please let me know how I can do (I have been in the IT game for over 17 years, I understand nothing is sooooo straight forward)

---

### Post by directhex on 2011-01-25
> **JHorrocks said:**
> The root problem, each time i run the same script can be different each time (same script).

I don't write or use these scripts, so that's the one thing I can't help on. You'll need to talk to the script authors for that.

HOWEVER.

Here's how to cleanly(ish) enable a second Mono runtime, with clean GAC duplication - the holy grail no script writer has ever done.

First, configure/make/make install 2.8 (well, 2.10rc1 is out now) to a prefix in /opt, e.g. "./configure --prefix=/opt/mono-2.8.2"

That'll give you a Mono which runs fine if you call /opt/mono-2.8.2/bin/mono, but only has 188 assemblies in its GAC, which is not the same as your main distro GAC.

Here's the magic:

"cp /usr/share/cli-common/runtimes.d/mono /usr/share/cli-common/runtimes.d/mono-2.8.2"

then open /usr/share/cli-common/runtimes.d/mono-2.8.2 in an editor, and change every instance of "/usr/bin/gacutil" to "/opt/mono-2.8.2/bin/gacutil" and every instance of "/usr/bin/mono" to "/opt/mono-2.8.2/bin/mono". Oh, and near the top, change the name from "Mono" to "Mono 2.8.2" so you know what's going on.

Still with me?

Run "/usr/share/cli-common/gac-install mono-2.8.2" - the argument there is the name of the file you used in runtimes.d. Bam, you now have every library from your "main" GAC added to your paralle GAC.

Before:

```
$ /opt/mono-2.10~rc1/bin/gacutil -l | tail -1
Number of items = 188
```

After:

```
$ /opt/mono-2.10~rc1/bin/gacutil -l | tail -1
Number of items = 299
```

And this will be kept up-to-date in BOTH, for any future package installs/removals. e.g.

```
$ sudo aptitude install libboo2.0.9-cil 
...
* Installing 8 assemblies from libboo2.0.9-cil into Mono
* Installing 8 assemblies from libboo2.0.9-cil into Mono 2.8.2
```

All that remains is switching the default Mono runtime used by apps on the system. You want to do two things here - edit your environment so the prefix in /opt is added to the start of $PATH, and change the /usr/bin/cli symlink (which points to the system's default .NET runtime) as follows:

```
update-alternatives --install /usr/bin/cli cli /opt/mono-2.8.2/bin/mono 50
```

That should cover both scenarios regarding running apps. All apps are *supposed* to be patched to use /usr/bin/cli to start, but some just run "mono". If your environment is good and symlink set up, both scenarios are caught.

YMMV. IANAL. IDDQD. But that should enable a full switch to 2.8+ with dependency tracking intact and working.

---

### Post by JHorrocks on 2011-01-27
Wow, the most detailed help I have ever seen on any post haha... thanks @directhex.

At the moment I am not at the office till Saturday, so I will reinstall new ubuntu 10.04 and follow your instructions as per post.

P.S. Do you know what, even though I still dont have a working copy of Mono/MonoDevelop on Ubuntu yet... wait till Saturday ;) , I feel I 100% made the best change of my life, to swap from Windows over to Ubuntu, where there are people like yourself who spend endless amounts of time to helping users like myself.... So what do you want for Christmas? hahaha!!

---

### Post by juancarlospaco on 2011-01-27
Forget the mammals, go reptile... ;)

---

### Post by directhex on 2011-01-27
Was up until 2:15am bughunting in 2.10~rc1. There are bugs, oh yes. At least in the test suite, which is meant to be the bit that reports bugs, not contains them!

---

### Post by JHorrocks on 2011-02-08
@directhex Sorry for the late reply, I got sidetracked on a project.

I followed your instructions and bam.... its working. So now I have a working copy of mono 2.8.2 and a copy of MonoDevelop 2.4.x (cannot rememeber the x, I am not at the machine right now).

But anyway, can create .NET 4.0 applications and run on apache2... great.

Thanks for the help, I just now need to find out how to debug directly on apache2, not on the xsp webserver as I use subdomains in my webcode for testing, and [http://127.0.0.1:8080](http://127.0.0.1:8080) on the xps server is no good for me... but that is a whole new story.

So getting back to the point, thanks :)

---

