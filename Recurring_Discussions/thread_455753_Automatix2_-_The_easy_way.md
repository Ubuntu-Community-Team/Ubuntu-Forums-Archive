---
title: "Automatix2 - The easy way"
date: 2007-05-26
forum: Recurring Discussions
---

### Post by ryanVickers on 2007-05-26
I've seen various posts all over the place on the best way to install this, and they are all hard, problem prone, etc.  so I come to you with a solution!

Simply select one of these links, save it, and install!  Just make sure to pick the right distro and especially arch (i386 or AMD64)

Feisty:
[AMD 64]("http://www.hotlinkfiles.com/files/429265_khv1a/automatix2_1.1-4.6-7.04feisty_amd64.deb")
[i386 (32 bit)]("http://www.hotlinkfiles.com/files/429339_mozo4/automatix2_1.1-4.12-7.04feisty_i386.deb")

Edgy:
[AMD 64]("http://www.hotlinkfiles.com/files/429337_srlco/automatix2_1.1-4.3-6.10edgy_amd64.deb")
[i386 (32 bit)]("http://www.hotlinkfiles.com/files/429338_mxwzz/automatix2_1.1-4.11-6.10edgy_i386.deb")

Dapper:
[AMD 64]("http://www.hotlinkfiles.com/files/429336_4bnhn/automatix2_1.1-4.3-6.06dapper_amd64.deb")
[i386 (32 bit)]("http://www.hotlinkfiles.com/files/429335_5iqjb/automatix2_1.1-4.2-6.06dapper_i386.deb")

---

### Post by taurus on 2007-05-26
And why would you want to install Automatix2 to have it modify your /etc/apt/sources.list (and who knows what else) since you can install everything that you need from Add/Remove, synaptic, apt-get, or aptitude?

---

### Post by ryanVickers on 2007-05-26
Those are excellent, and they are so much easier than the old days when you had to hunt down everything manually, but automatix provides a few more packages that don't show up in those managers.  I think many people will agree, it's for the extra addons that those can not provide.  And you don't have to get it, I'm just putting this up here so that the people who have had so many problems can now find a extremely simple solution; but it's a good idea to post your ideas too, it's good to have something to think about first.

---

### Post by aysiu on 2007-05-26
I disagree with this thread's sentiment strongly.

Automatix has its uses in some special cases, but in the vast majority of cases where I've seen it recommended, installing the needed package directly is always faster and more straightforward.

More details here:
[http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/](http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/)

---

### Post by Polygon on 2007-05-27
> **taurus said:**
> And why would you want to install Automatix2 to have it modify your /etc/apt/sources.list 

maybe its because it adds safe repos?

> 
#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END


somehow i dont think repos from canonical.com or ubuntu.com are going to screw over your system.

---

### Post by mar225 on 2007-05-27
I tried automatix once and it made a mess of my system and before I was through I ended up doing a reload. Never had that problem with apt-get

---

### Post by aysiu on 2007-05-27
I think you're forgetting a few repositories: ```
jason@jason:~$ sudo aptitude update
Get:1 http://www.getautomatix.com feisty Release.gpg [189B]
Ign http://www.getautomatix.com feisty/main Translation-en_US
Ign http://www.getautomatix.com feisty/main Translation-en_US
Get:2 http://www.getautomatix.com feisty Release [6738B]
40% [Connecting to us.archive.ubuntu.com (91.189.88.31)] [Waiting for headers] [
Get:3 http://www.getautomatix.com feisty/main Packages [9348B]
Get:4 http://security.ubuntu.com feisty-security Release.gpg [191B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:5 http://us.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Get:6 http://www.getautomatix.com feisty/main Packages [9348B]
99% [Waiting for headers] [Waiting for headers] [Connecting to elisa.fluendo.combzip2: (stdin) is not a bzip2 file.
Err http://www.getautomatix.com feisty/main Packages
Sub-process bzip2 returned an error code (2)
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:7 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty Release
Hit http://security.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://security.ubuntu.com feisty-security/restricted Packages
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Ign http://elisa.fluendo.com feisty Release.gpg
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Ign http://elisa.fluendo.com feisty/main Translation-en_US
Hit http://elisa.fluendo.com feisty Release
Ign http://elisa.fluendo.com feisty/main Packages
Hit http://elisa.fluendo.com feisty/main Packages
Fetched 16.3kB in 1s (13.5kB/s)
Reading package lists... Done
W: Duplicate sources.list entry http://www.getautomatix.com feisty/main Packages (/var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
```

More details [here](http://ubuntuforums.org/showthread.php?t=455686)

---

### Post by Polygon on 2007-05-27
?

Ive used automatix and i dont have that fluendo repo. But i know it uses the mediubuntu repo as well, but it removes it after it is done. But whatever you made your point, it uses some third party repos which cant be supported. continue.'

and also automatix makes time based backups before it adds anything, i mentioned that in that guys support post

---

### Post by ryanVickers on 2007-05-27
I didn't expect such a discussion, but I believe this might come in usefull to everyone anyways.  Might have to change the heading though :p

---

### Post by Spr0k3t on 2007-05-27
I don't like Automatix.  It messed up one of my computers.  I gave information to Arnie and others but no solution came of it.  I've found it's loads easier to install the individual packages themselves.  Also, with Fiesty, I see no reason at all to use Automatix2.  I've created a list of packages to install that I keep as a bash script in my /home/.  Only takes 10 seconds to open the terminal and type the command.

---

### Post by BigSilly on 2007-05-27
OK I'm a bit of a Linux noob (and I suppose I will be for many years), but what's with the Automatix hatred? It was recommended to me from a friend, I followed the instructions to install it, and I've had no problems at all. It just seems to me to be an alternative bag of software, that may or may not come in handy. In my case, it proves very useful, since I'm a noob as I say.

So what gives? Is there something wrong with it, or otherwise surreptitious? For Ubuntu newcomers it seems to me to be a very useful thing indeed to install, particularly when you consider how easy it is to use.

---

### Post by Polygon on 2007-05-27
it can sometimes screw up your sources.lst cause of conflicting packages or some other reason

for some people it works, for some people it screws things up. But the only people you ever hear are the people who had problems with it so it seems that everyone is having problems when thats not really the case

but the fact that it can and has caused problems is a bit of an issue... i hope that this can be resolved in some way cause automatix is pretty nifty.

---

### Post by frodon on 2007-05-27
In many cases all you need is the link below, and in those case you take more time to install a third party tool than following the instruction of this page which are officially supported :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Spr0k3t on 2007-05-27
> **BigSilly said:**
> So what gives? Is there something wrong with it, or otherwise surreptitious? For Ubuntu newcomers it seems to me to be a very useful thing indeed to install, particularly when you consider how easy it is to use.

It's another level of redundancy.  I've had it cause more problems on a system than it was worth.  The scripts are nothing more than a way to install the packages from  your sources.list.  Once I figured the correct method of installing/updating/removing, there was no reason to even use automatix.  It took more time to search through automatix than it did for synaptic package manager or aptitude.  Not to mention, trying to fix an issue when automatix was part of the initial cause is not an easy problem to trace down to the root.  The only thing I've found good about Automatix... checking out other packages I was  unaware of.

---

### Post by Jenda on 2007-05-27
Automatix as a whole is just going in the wrong direction. You shouldn't need a third party script to do these things for you!
Ubuntu is a free and open source operating system. Many of you are or will one day be direct developers of the system, and all of you have the opportunity to contact the current developers directly.
What we should aim for is fixing the deficiencies automatix attempts to fix within Ubuntu itself - and when there's a legal problem - fix that too. The current 'restricted drivers' manager model seems to fit even the most questionable legal cases we might encounter - with the exception of software you'd have to "pirate" to get, and automatix won't help you there either.

---

### Post by ikonia on 2007-05-27
I have no idea why this is constanly discussed on ubuntu forums.

Drop the topic, take it to the automatix forum.
Ubuntu as a product should distance the whole progect (forum included) from it.

too many people think its an ubuntu (or supported) product.

---

### Post by fire3 on 2007-05-27
I don't like automatix..I just want to open the terminal ant type in my command...

---

### Post by starcraft.man on 2007-05-27
I just wanted to weigh in on this. I also don't like automatix2, I have an additional reason though. First and foremost, while the defenders of Automatix can complain all they want that we blame it too unfairly, I've seen too many threads with problems with people who had automatix, and they tried to install exactly the same things one could do with apt/synaptic. Since, they had trouble, and those who used apt didn't, I can't really see how it couldn't have been automatix in the wrong.

Second and more importantly, I don't think it was mentioned but what I really don't like about Automatix2 is it creates a strong reliance on the unofficial program, I would even go so far as to say addiction/dependence. I remember a while ago, the Automatix service was just down, for week(s)/days. People thought the program had collapsed and was over (in fact it came back after a week or two later) and they came here wondering what to do and panicking. The point is, people have become dependant on this program, and its bad that they have. Automatix isn't the only way to install extra software, its not even the easiest... it just looks easier cuz it has a nice simple GUI with icons and a nice tree menu. I wonder what will happen if it ever really does go away for good....

Oh and bigsilly... [Ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by ikonia on 2007-05-27
Starcraft man - exactly.

This is partly my point,

if we consistantly answer (or blame) automatix2 queries software issue on an ubuntu system then ubuntu is essentially supporting it.

Automatix has its own forum, its own support channels and its own views on how it should develop. The sooner the ubuntu community are pointed to these resources without a "yes I'll help" or "automatix2 sux" style comment the better..

Process should be standard. 

Automatix2 installed - please visut [http://bla](http://bla) bla for support issues. As once its installed its unfair to ask the ubuntu community to support it and keeps this constant "you said it does/doesn't work" style discussion going.

Ubuntu as a community/software/project should distance its self and just let the guys who like and want to support and develop it get on with it.

---

### Post by starcraft.man on 2007-05-27
I agree with you too ikonia, we really do need to stop answering queries about automatix here... its hard to tell people to just go to another site, but in reality, it isn't part of Ubuntu, and it isn't our fault if it broke your system.

Oh and I think you meant send them [here]("http://www.getautomatix.com/forum/") :). Thats about it.

---

### Post by BigSilly on 2007-05-27
Don't misunderstand me, I don't rely on it, or even use it that much. It was just handy to get the codecs (legal I believe here in the UK) when I first installed Ubuntu. I came here from Freespire, and all's you did there was use CNR which I thought was excellent. Automatix was useful at first, but I've used Add/Remove and Synaptic much, much more since. 

You have to remember, that for many of us Linux is a learning experience. As time goes on you realise that things like CNR and Automatix are indeed perhaps a bit redundant. This is because you have learned more. For first time users searching for those awkward codecs etc, something like Automatix can be very useful. Other than those things though, there's not much else on there really. Nothing you can't find elsewhere just as easily.

I've just discovered a site called GetDeb, which has really surprised me. I didn't know there was a way of downloading a program, and double clicking it to install like in Windows. I can understand a long-term Linux users frustration at that sentence! But the truth is, many people want an easier way into Linux use. Little things like this make you think "why have I been messing about with Windows, when Linux is this simple"? This is a really, really good thing and should be celebrated. After years of being told Linux is impossible, only then finding it can be the easiest thing in the world! 

There's a huge knowledge base out there for Linux, but for a first timer who's sick of Windows, it's seemingly impossible to penetrate it and get what you need to know. For me, I am trying to make time to learn, but it's not always easy to find patient tutors, if you know what I mean. Everyone here seems to know all  about Linux - inside out, and often get frustrated sharing with newbies. My point is, that many first timers appreciate an easier way in and sometimes stuff like Automatix can represent that.

---

### Post by PriceChild on 2007-05-27
> **Polygon said:**
> maybe its because it adds safe repos?

somehow i dont think repos from canonical.com or ubuntu.com are going to screw over your system.It adds more than repos from canonical.com It adds wine repos, its own and possibly more but my memory fails me.

 History has shown that **3rd party repos have broken systems** by acciadent and **on purpose**.

---

### Post by Adamant1988 on 2007-05-27
There are a series of issues involving Automatix, some of them are within the code itself, many are not.  Automatix is **known** to cause issues with upgrading.   I have been shown how Automatix can **break** dpkg just through regular use, by Ubuntu developers.  So, I know that the code is not as high-quality  as you would be led to believe by the developers of the application. 

This is strictly just leaving out the unsavory behavior by people who are responsible for the development of the application.

---

### Post by arnieboy on 2007-05-27
> **Polygon said:**
> But i know it uses the mediubuntu repo as well
Automatix uses a few medibuntu packages.. not the repository itself. The only repository that it uses apart from its own and official Ubuntu repositories is the wine repository which is maintained by Scott Ritchie, a noted Ubuntu contributor. His packages have never been known to break anything.. 
As for the packages maintained by Automatix, we do our best to make sure we do not break Ubuntu systems like Ubuntu MOTU does through some of their Universe and Multiverse packages in every release.

---

### Post by ikonia on 2007-05-28
the point is not what breaks what, but the fact that ubuntu is being asked to support a 3rd party, none authorised package.

Ubuntu resources, forum, irc, paid support, mailing lists, whatever, can't be expected to support none ubuntu products, 

I'm not saying any product is good or bad I have my views and I'm not trying to impose them on anyone. 

The part I am being vocal about is remove the automatix issues/support from ubuntu resouces, just direct them to the automatix resources, in which case the guy at automatix can field issues in their specialist field (automatix) listen to the community and grow the product as they want to.

Automatix is not an ubuntu product so should not be support on the ubuntu resources. 

Many people have a negative view of it, so rather than keep a constant debate on it being good or bad, lets just remove it from ubuntu's radar.

---

### Post by aysiu on 2007-05-28
While I do agree that the Automatix forums are probably the *best* place to direct Automatix support requests, I don't agree that the forums don't or shouldn't support third-party applications (or "non-Ubuntu products"). If you look through the vast majority of the threads, you'll see the problems occur mostly with third-party applications. How often do you see someone turn down a support request for Adobe Reader, Skype, Opera, or PDFedit? None of those is a Ubuntu "product," but all of them get 100% support on these forums.

Automatix support requests should go to the Automatix forums because those forums are most likely to have solutions, and I believe the developers of Automatix itself are active on those forums.

---

### Post by 23meg on 2007-05-28
[QUOTE=ikonia]Ubuntu resources, forum, irc, paid support, mailing lists, whatever, can't be expected to support none ubuntu products, [/QUOTE]

[QUOTE=ikonia]Automatix is not an ubuntu product so should not be support on the ubuntu resources. [/QUOTE]

Most of what's covered by the forums and other support resources are non-Ubuntu products by that definition, since most of what makes up Ubuntu comes from upstream. It's impossible to stick to this logic.

---

### Post by aysiu on 2007-05-28
I agree with you in general, 23meg (see post above), but a repository application in Universe or Main makes sense to support here, since those repositories are maintained by the community and Ubuntu.

Those I would qualify as being separate in some way from non-community or unofficial repository items (like the ones I cited above)... even though I do think those should be supported here as well.

---

### Post by ikonia on 2007-05-28
yes, perhaps I should have been a little more clear about what I was defining with 3rd party applications.

Flash for example is not an ubuntu product, but it is hosted in the official ubuntu repo's as with ati,nvidia, that sort of thing. Skype is a little different in that its not hosted in an ubuntu or ubuntu approved repo - so I guess does that fall into the same catagory, I don't know.

However your right my definition of 3rd party was posted unclear by myself. I also agree with what your suggesting (mostly.)

---

### Post by SoulinEther on 2007-05-28
Not to get too side-tracked on this topic, but why do people like Automatix? I never really knew anything about it until I googled it... and I still don't see any advantage.

---

### Post by aysiu on 2007-05-28
That is way off topic, SoulinEther, which is why I moved your post to a different thread.

There are a few reasons people like Automatix:

1. Back when Automatix was first created, it was extremely useful, because Ubuntu didn't have easy ways to install a lot of stuff (particularly multimedia codecs) in a point-and-click manner, unless you knew specifically what packages to look for. A lot of people got used to "needing" Automatix, and even when Ubuntu's codec installation improved, those people got so used to the crutch, they didn't want to leave it even after their broken leg had healed.

2. There are some situations still (rare though they are) where Automatix comes in handy--for installing some items not available in repositories, for installing 32-bit applications on 64-bit Ubuntu, etc. Surely, Automatix is recommended a lot more frequently than it should be, but there are still some rare instances where Automatix will save you a lot of time and trouble.

3. Hype. Just like Ubuntu, Automatix gets hyped up a lot. So people use it, even if it's not the best tool out there.

---

### Post by SoulinEther on 2007-05-28
Ah, thank you for clarifying.

---

### Post by DJiNN on 2007-05-29
> **starcraft.man said:**
> its not even the easiest... it just looks easier cuz it has a nice simple GUI with icons and a nice tree menu. I wonder what will happen if it ever really does go away for good....


Hmmm, using that very same argument, i wonder what would happen if your Gui didn't work, or Ubuntu just went straight into a Terminal? Not everyone that uses Linux/Ubuntu etc wants to have to learn about the "Command Line".  Synaptic uses a GUi, and although you can use it straight from the terminal as you can with most things, it puts many people "Off" of using Linux in general. 

We're all dependent on something, be it GUi's or Automatix.  You don't need to use a mouse, but the chances are that you do..... and why use 65 million colours when 16 is more than enough..... isn't it? ;)

The potential for "System Damage" is far greater (IMHO) if someone starts to mess around with or alter, the sources list, than if they let a program like Automatix do it instead. Perhaps after it's all installed & working, if they feel so inclined, they can then perhaps find out about other ways to do the same thing. In my opinion some will choose this, many will not. 

I'm not advocating Automatix over using Synaptic or anything else. Rather the "Choice" of being able to use it without being swayed by (For the newbie at least) the unnecessary bias that this program receives here.  

DJiNN

---

### Post by forrestcupp on 2007-05-29
> **ryanVickers said:**
> I've seen various posts all over the place on the best way to install this, and they are all hard, problem prone, etc.  so I come to you with a solution!

go [here]("http://www.getautomatix.com/wiki/index.php?title=Installation").



Boy, ryanVickers, I kind of feel sorry for you.  It looks like you just joined the forums this month, so you had no possible way to know what a volatile subject this has been for a very long time around here.  I'm actually surprised this thread has been as civil as it has been.  I hope people's attitudes about something that you feel is useful don't turn you off of Ubuntu on a whole.  People are generally friendly around here, but there are a few touchy subjects to stay away from.

That doesn't mean you can't use Automatix2, though.  If it's working for you without problems, enjoy.  But if you need help with it, you probably should ask on their forums first if you don't want to get flamed.

---

### Post by frodon on 2007-05-29
> **DJiNN said:**
> The potential for "System Damage" is far greater (IMHO) if someone starts to mess around with or alterThis is an old myth that you need to edit your source.list by hand to add the missing repositories, all you need is to open synaptic (sorry the screenshots are in french) :
[IMG]http://yeknan.free.fr/blog/images/ubuntu7.04/install/synaptic3.png[/IMG]

[IMG]http://yeknan.free.fr/blog/images/ubuntu7.04/install/synaptic4.png[/IMG]

Then when you are just looking for an apps, look how beautiful is the add/remove apps tool, don't you think one should try those 2 tools before looking for 3rd party helper scripts ? :
[IMG]http://images.howtoforge.com/images/the_perfect_desktop_ubuntu7.04/39.jpg[/IMG]

---

### Post by starcraft.man on 2007-05-29
> **DJiNN said:**
> Hmmm, using that very same argument, i wonder what would happen if your Gui didn't work, or Ubuntu just went straight into a Terminal? Not everyone that uses Linux/Ubuntu etc wants to have to learn about the "Command Line".  Synaptic uses a GUi, and although you can use it straight from the terminal as you can with most things, it puts many people "Off" of using Linux in general. 

DJiNN

IF (highly unlikely)I lost my gui, it would be because I did something (the GUI doesn't just fail, you have to modify something) and since I have been using the terminal and learning the underpinnings of linux and how they work, I would fix it myself (likely very quickly, since I know what I modified manually). If the same happened to someone with no experience with the terminal/console (likely by accident), and who was wholly dependant on automatix, I can only imagine how hard it would be... to even begin to figure out what was wrong, and then that person would come here and have to be given a crash course since they knew nothing of the terminal.

In my mind, there is a large difference in dependence between the GUI and automatix. It is like saying someone is dependant on the keyboard as an input, and some other people are dependant on using a touch screen/tablet for their text input. One is standard and expected means, one is superfluous and easier. You could for instance use a tablet your whole life, if you got to a job that needed you to code then or do some other task only via keyboard, you be seriously disadvantaged.

I would disagree with your last statement in there, from my experience people don't get turned off from synaptic, they get turned off because they are long term windows users (10-15 + years) and they expect or believe linux to be a windows clone, which it is not, some simply decide after seeing that they don't want to learn a whole new OS, and if they don't thats their choice too since your all about choice. No OS can get universal appeal, some people just won't use linux ever.

> 
We're all dependent on something, be it GUi's or Automatix.  You don't need to use a mouse, but the chances are that you do..... and why use 65 million colours when 16 is more than enough..... isn't it? ;)

The potential for "System Damage" is far greater (IMHO) if someone starts to mess around with or alter, the sources list, than if they let a program like Automatix do it instead. Perhaps after it's all installed & working, if they feel so inclined, they can then perhaps find out about other ways to do the same thing. In my opinion some will choose this, many will not. 


I've consistently sent people to [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for learning the basics and installing software in the beginning and I've seen few if any (to my knowledge) of them "mess up" their system. I have, on the other hand seen people install automatix and then just happen to have problems after. Perhaps they are both giant coincidences? 

Edit: See frodon, point made.

> 
I'm not advocating Automatix over using Synaptic or anything else. Rather the "Choice" of being able to use it without being swayed by (For the newbie at least) the unnecessary bias that this program receives here.  

I wouldn say its necessary bias, its my experience with it (just like its likely your experience with it, that tells you to recommend it). Just like when you grow up your shaped by what you experience, I can't recommend a program I don't have faith in (I do recommend Envy, because I have faith in that and it does only one thing, install drivers, and does it very well). The truth is with Feisty's integration of the restricted driver management, and the other means of installing it has become very easy to install things. I don't think you absolutely must learn the terminal, but it is a very powerful and helpful tool in Linux. Aysiu already pointed that out, and two other points.

Note to Forest: Yes this thread has been civil, even if people have radically different and opposing views, it doesn't mean they have to flame. I equally don't think the discussion of the subject will turn him off the forums, what would IMO turn him off would be if a mod had locked his thread and told him to get lost >.>.

Note to Frodon: Thank you for pointing that out, there is in fact a very easy GUI for new people to edit the source list. Once one adds a few extra repos that way, he can use either synaptic/ add/remove to his hearts content and install almost anything via that.

---

### Post by DJiNN on 2007-05-29
starcraft.man. thanks for a prompt and really well laid out reply. It was a pleasure and a delight to read. I agree with all that you have said, but i still feel that Automatix is a valuable & useful tool for beginners.  (in my experience, but then that is all i will ever have to judge things on, much like most people. )

I am not in defense of Automatix, any more than i would defend Ubuntu when people say it is a "Dumbed down Debian", for both of these are able to defend themselves (Should the need arise) by their own words & actions. 

But i did feel the need (albeit temporarily) to express my feelings about something that has helped me a great deal in the past, especially when i first started using Ubuntu. Things have most certainly changed & i notice that Ubuntu (Feisty) now sports much of what Automatix used to cover, thus negating the need for Automatix (in many cases). 

It's somewhat unnecessary (IMO) to vehemently berate something (As has been done on several occasions in these forums, albeit not in this thread itself) when it's only purpose is to help those that are either unwilling or unable, to do the job themselves. 

Anyhow, i thank you once again for your time & words. They are both appreciated & well received. This debate (whilst interesting to me personally) has probably gone on much longer than anyone ever thought it would/could, which to me says a lot more about the subject matter  than i could ever express anyway. :D

DJiNN

---

### Post by DJiNN on 2007-05-29
> **frodon said:**
> 
Then when you are just looking for an apps, look how beautiful is the add/remove apps tool, don't you think one should try those 2 tools before looking for 3rd party helper scripts ? :
[IMG]http://images.howtoforge.com/images/the_perfect_desktop_ubuntu7.04/39.jpg[/IMG]

frodon, thanks for your reply. I did write a long answer to this, then decided to delete it because i don't want to add any more debate to something that people feel has been debated enough already. :)

I agree with what you're saying. But, i shall still point people (When asked or when i feel it's a good thing to do) to the Automatix forums and recommend this program, because in my experience it works, it's friendly, it's pain free, and for the beginner it can mean the difference between using Ubuntu or not, and although Ubuntu etc has it's problems as do most distros, i feel that it's a great distro with terrific forums & plenty of support. 

DJiNN

---

### Post by aysiu on 2007-05-29
> **DJiNN said:**
> because in my experience it works, it's friendly, it's pain free, and for the beginner it can mean the difference between using Ubuntu or not That hasn't been true in my recent experience--maybe in the Hoary/Breezy days or even Dapper. But Feisty really makes Automatix redundant for the bulk of new user needs. And if users can't be bothered to do a few clicks in Synaptic or Add/Remove or even just try to play an MP3 and follow the prompts to get MP3 playback, then maybe I don't care if they use something other than Ubuntu.

If you want proprietary stuff "out of the box," there are plenty of other distros that will provide such without making you download a third-party script to install them "easily." For those new users, I'd recommend Linux Mint, Mepis, PCLinuxOS, Blag, or Linspire.

I used Mepis my first month of being a Linux user, and it was great for me that first month. Then, the next two years, I used (and continue to use) Ubuntu. If it's meant to be, people will use Ubuntu. And, if not, they can use another Linux distro. And, if not, they can use Mac or Windows.

---

### Post by starcraft.man on 2007-05-29
> **DJiNN said:**
> frodon, thanks for your reply. I did write a long answer to this, then decided to delete it because i don't want to add any more debate to something that people feel has been debated enough already. :)

I agree with what you're saying. But, i shall still point people (When asked or when i feel it's a good thing to do) to the Automatix forums and recommend this program, because in my experience it works, it's friendly, it's pain free, and for the beginner it can mean the difference between using Ubuntu or not, and although Ubuntu etc has it's problems as do most distros, i feel that it's a great distro with terrific forums & plenty of support. 

DJiNN

Your welcome for my reply, I'm always free to talk about such things. Like most philosophical questions (I read/discuss a lot of philosophy), I guess we won't get to an answer in this thread or in the near future. I also agree with you that there shouldn't be blatant flaming/zealous hate on the subject, such comments (as I've seen on the forums elsewhere as you have) really serve no purpose but to antagonize and cause conflict (which I most certainly frown upon, as it will cause nothing good for our wonderful community).

Your perfectly free to recommend automatix to new people (I won't hold it against you), as I will direct them to [ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") and guide them in using official means of installing. I'd make a simple request (albeit one that you could ignore if you choose to I suppose) that if you do recommend automatix to new folk, that you clarify it as an unofficial installer, and that is likely to be best supported by their own forums (should something go wrong with it). As a bonus, it would be nice if you additionally included the option for them to use ubuntuguide or another guide to using official means (especially Feisty, it has become very easy to install things), thats also up to you though, new users should be able to choose what they think is best IMO.

Anyway, I guess thats about it, I'm happy we did stay civil on this topic. I guess that is it then and we shall agree to disagree.

Edit: Agreed with Aysiu, some people simply expect everything to work perfectly (like mac or windows) and linux may just not be for them. You hit the post button before me, I guess I'm getting a bit picky with editing my posts :p.

Edit 2: Oh and I will have to try mint and mepis in my VM, never had a look at them yet :D.

---

### Post by DJiNN on 2007-05-29
> **starcraft.man said:**
> Your welcome for my reply, I'm always free to talk about such things. Like most philosophical questions (I read/discuss a lot of philosophy), I guess we won't get to an answer in this thread or in the near future. I also agree with you that there shouldn't be blatant flaming/zealous hate on the subject, such comments (as I've seen on the forums elsewhere as you have) really serve no purpose but to antagonize and cause conflict (which I most certainly frown upon, as it will cause nothing good for our wonderful community).

This, more than anything else, is what i was attempting to say. If one does not like something, that's OK. If one also feels the need to warn others about problems or feelings then that's fine as well. But as you succinctly stated, the "blatant flaming/zealous hate on the subject serve no purpose but to antagonize and cause conflict". 
Especially over something that has served a very good purpose for sometime & still (for some at least) continues to do so.

> Your perfectly free to recommend automatix to new people (I won't hold it against you), 

Thanks..... ;) :D

>  I'd make a simple request (albeit one that you could ignore if you choose to I suppose) that if you do recommend automatix to new folk, that you clarify it as an unofficial installer, and that is likely to be best supported by their own forums (should something go wrong with it). As a bonus, it would be nice if you additionally included the option for them to use ubuntuguide or another guide to using official means (especially Feisty, it has become very easy to install things), thats also up to you though, new users should be able to choose what they think is best IMO.

I think that's a very fair request and one that i will be more than happy to do.  It is certainly a lot easier in Feisty to do these things and i agree that it should be the choice of the user as to which route they feel they should take, and the better informed they are in this the more able (hopefully) they will be to make the right choice for themselves. 

> Anyway, I guess thats about it, I'm happy we did stay civil on this topic. I guess that is it then and we shall agree to disagree.

As i said, i'm neither defending Automatix or it's creators nor saying that people should use it or not. All i'm saying is that A: it works for me and always has and B: people should be able to choose for themselves as to which way they choose to do a thing without any "Negative bias" from others just because they have issue with it.  As for being civil, i personally would have it no other way. There is no better way to discuss something & regardless of whether the parties agree or not, it always makes for a far more enjoyable discussion IMHO. 

DJiNN

---

### Post by Hex_Mandos on 2007-05-29
> **aysiu said:**
> If you want proprietary stuff "out of the box," there are plenty of other distros that will provide such without making you download a third-party script to install them "easily." For those new users, I'd recommend Linux Mint, Mepis, PCLinuxOS, Blag, or Linspire.


I thought Blag was [100% FLOSS]("http://www.gnu.org/links/links.html#FreeGNULinuxDistributions")

---

### Post by aysiu on 2007-05-29
You can check out [the list of packages on the CD.](https://wiki.blagblagblag.org/60000_Packages) It has and always has had non-free codecs: ```
    * ffmpeg - Utilities and libraries to record, convert and stream audio and video
    * gstreamer-ffmpeg - GStreamer streaming media framework FFmpeg-based plugin
    * gstreamer-plugins-bad - GStreamer streaming media framework "bad" plug-ins
    * gstreamer-plugins-ugly - GStreamer streaming media framework "ugly" plug-ins
    * lame - LAME Ain't an MP3 Encoder... but it's the best of all
``` It also contains a free codec that's a little controversial in terms of its legality: ```

    * libdvdcss - Portable abstraction library for DVD decryption
``` Am I misunderstanding the situation? Are all the "ugly" plugins, etc. free?

---

### Post by ryanVickers on 2007-06-20
Wow, I haven't checked back here in a while; I didn't expect it to be this kind of discussion, just, "wow, that was easy, thanks!" :p

Well, I just offer this info, and you can take it or leave i.  Maybe it is good for people to have something to read beforehand though, so they can decide if they want it.  But once again, I'm just providing the service of the info!  Not trying to imply it's the best, or you need it or anything!

---

### Post by Nekiruhs on 2007-06-20
> **BigSilly said:**
> I've just discovered a site called GetDeb, which has really surprised me. I didn't know there was a way of downloading a program, and double clicking it to install like in Windows. I can understand a long-term Linux users frustration at that sentence! But the truth is, many people want an easier way into Linux use. Little things like this make you think "why have I been messing about with Windows, when Linux is this simple"? This is a really, really good thing and should be celebrated. After years of being told Linux is impossible, only then finding it can be the easiest thing in the world! 
Yeah, about every distro has some form of that, Ubuntu's are .deb (Debian, whcih we are based off of), and many others are .rpm. Basically, those tell apt-get what to download. And when apt-get installs something, it "reads" the .deb in the repo. Thats a fully supported and legit way to install things in Linux. Automatix2 produces a reliance on the program, and has poor code that is known to break your Sources.list and dpkg. .

---

### Post by BrokeBody on 2007-06-20
Well, I also don't like Automatix much, but I use it only because of win32codecs and libdvdcss2 (gstreamer and exstras aren't that smooth yet :p ), but I don't need it anymore. I found this recently

[http://ftp.sunet.se/](http://ftp.sunet.se/)

for debian-multimedia
[http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/)

or just add this to your repo

for i386

```
deb [http://debian.mxchange.org/debian](http://debian.mxchange.org/debian) stable main

deb [http://www.dedale.eu.org/mirror/debian-multimedia/](http://www.dedale.eu.org/mirror/debian-multimedia/) stable main
deb-src [http://www.dedale.eu.org/mirror/debian-multimedia/](http://www.dedale.eu.org/mirror/debian-multimedia/) stable main

deb [ftp://ftp.linux.kiev.ua/pub/mirrors/www.debian-multimedia.org/](ftp://ftp.linux.kiev.ua/pub/mirrors/www.debian-multimedia.org/) stable main
deb-src [ftp://ftp.linux.kiev.ua/pub/mirrors/www.debian-multimedia.org/](ftp://ftp.linux.kiev.ua/pub/mirrors/www.debian-multimedia.org/) stable main
```

and there you have it, win32codecs and libdvdcss2 if you want them. :p

---

### Post by bapoumba on 2007-06-21
@ BrokeBody: please do not recommend going with debian repos.
Both libdvdcss2 and win32codecs are packaged for ubuntu by two (may be three?) ubuntu MOTUs in the medibuntu repos:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Medibuntu continued plf and freecontrib packages for ubuntu when they got stopped last year.

Please read the legal disclaimer regarding these packages.

---

### Post by Johnsie on 2007-06-21
Repositories and Automatix act as middle men between the developers and the users. Personally I prefer to cut out the middle man.

As a developer I would rather control updates for my software rather than let the people at the repo or automatix do it. Having an auto-update facility in my programs is my solution for doing this. Obviously it's not the best solution all the time but it saves me having to rely on external maintainers. Obviously the software has to somehow get on the computer first and for me I find the whole creation of Debs a very tedious task. I develop software for both Windows and Linux and find creating a setup.exe much quicker and easier than creating a deb. I'm not saying setup.exe's ar better for the user, they are just easy for the developer to deploy.

---

### Post by BrokeBody on 2007-06-21
> **bapoumba said:**
> @ BrokeBody: please do not recommend going with debian repos.


Why? It doesn't matter if it's Ubuntu pool or Debian pool... same stuff.

---

### Post by frodon on 2007-06-21
> **BrokeBody said:**
> Why? It doesn't matter if it's Ubuntu pool or Debian pool... same stuff.I think you may not be aware of the risks related to the use of external repositories, using debian repositoies in ubuntu is even more dangerous.
This not the same stuff because the dependency tree is different so it's more likely to brake some packages or create some dependency hell when you will be willing to upgrade to the next ubuntu release.

So to summarize it does matter a lot if you wish to upgrade one day to a different ubuntu version.

---

### Post by scohar70 on 2007-06-21
There has been a lot of discussion in this forum about whether or not this forum should even discuss the topic of Automatix.

FWIW, I found this discussion useful.  I totally understand and agree with the Ubuntu staff's refusal to support Advantix, but I just wanted to chime in that the discussion in the tread **was** useful.

I am a total noob, and loaded Automatix onto my system on the recommendation of a friend.  Through this thread, I have learned, 
 
   (a) that's a bad thing, 
   (b) how to get the packages I want without Automatix, and 
   (c) that I should probably remove Automatix when I get home tonight.

Without the discussion topic here on Ubuntuforums.org, I would have happily kept going with Automatix until something eventually broke.  So, thanks for the discussion.

---

### Post by BrokeBody on 2007-06-21
[QUOTE=frodon]I think you may not be aware of the risks related to the use of external repositories[/QUOTE]

Oh yes, I'm perfectly aware of the risks.

[QUOTE=frodon]using debian repositoies in ubuntu is even more dangerous.[/QUOTE]

It depends from the dependency tree for *some* software.

[QUOTE=frodon]
This not the same stuff because the dependency tree is different so it's more likely to brake some packages or create some dependency hell when you will be willing to upgrade to the next ubuntu release.

So to summarize it does matter a lot if you wish to upgrade one day to a different ubuntu version.[/QUOTE]

Last time when I viewed the sources, when it comes to commercial packages (win32codecs and libdvdcss2 in this case), there is absolutely no difference if you are using Ubuntu or Debian repos *for multimedia*. 

So, to summarize, it doesn't matter if you wish to upgrade one day to a different Ubuntu version, at least for the present versions **when it comes to multimedia repos**.

When it comes to something else, like JDK for instance, it really does matter wether it's Ubuntu or Debian repos. ;)

---

### Post by frodon on 2007-06-21
> **BrokeBody said:**
> So, to summarize, it doesn't matter if you wish to upgrade one day to a different Ubuntu version, at least for the present versions **when it comes to multimedia repos**.

When it comes to something else, like JDK for instance, it really does matter wether it's Ubuntu or Debian repos. ;)Explain that to those who get errors upgrading to feisty or gutsy :-s.

No seriously, i'm not debating how much it is dangerous, i'm just saying it is more than a bad advice for beginners to tell them to use debian repositories in ubuntu, advanced users will always know how to solve unmet dependencies while upgrading

---

### Post by BrokeBody on 2007-06-21
> **frodon said:**
> Explain that to those who get errors upgrading to feisty or gutsy :-s.


That's because they don't have *Debian repos for **multimedia only***, they have for some other software also. Your'e not reading carefully.

What I said is in the case if you have only Debian repos for multimedia only, nothing else.

---

### Post by Foxmike on 2007-06-21
> **BrokeBody said:**
> That's because they don't have *Debian repos for **multimedia only***, they have for some other software also. Your'e not reading carefully.
 
What I said is in the case if you have only Debian repos for multimedia only, nothing else.
 
Maybe a good idea would be to always stick a "Warning: this may break your system" to those posts recommending such procedures on the forums.  I read your posts and it was not obvious that I would have to be careful while adding Debian repos to my Ubuntu sources.list.  While I am aware of it, some may not be.  And the forums are mainly there for help and support, so I think we got to be careful about what we recommend and how it is recommended.

---

### Post by BrokeBody on 2007-06-21
Alright Foxmike, point taken. ;)

Nevertheless, [this](http://ftp.sunet.se/pub/os/Linux/distributions/debian-multimedia/pool/main/) is definitely secure way. :p

:D

---

