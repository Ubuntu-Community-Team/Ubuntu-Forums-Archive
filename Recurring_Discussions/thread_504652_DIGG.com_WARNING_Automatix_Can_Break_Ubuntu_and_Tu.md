---
title: "DIGG.com: WARNING Automatix Can Break Ubuntu and Turn Your Hair Gray"
date: 2007-07-19
forum: Recurring Discussions
---

### Post by ubuntu-geek on 2007-07-19
Interesting Automatix discussion on digg.com today because of an article written by pimpyourlinux.com..

[http://digg.com/linux_unix/WARNING_Atomatix_Can_Break_Ubuntu_and_Turn_Your_Hair_Gray](http://digg.com/linux_unix/WARNING_Atomatix_Can_Break_Ubuntu_and_Turn_Your_Hair_Gray)

[http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/](http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/)

Thoughts?

---

### Post by compiledkernel on 2007-07-19
werd.

---

### Post by Lster on 2007-07-19
Yes, I think there are some bad problems with it. Rythmbox broke (stopped playing songs) last time I used it...

---

### Post by wolfen69 on 2007-07-19
i myself have used automatix for every install and had no problems. everytime i tried to get codecs "the right way", there was always something that wouldnt play. so i download every gstreamer codec ubuntu suggests, and it still wont play. using automatix has made playing various media seemless.

---

### Post by picpak on 2007-07-19
> From the [xubuntu blog](http://xubuntublog.wordpress.com/),

Woah, that threw me off guard for a second there :p

---

### Post by Frak on 2007-07-19
Nobody said upgrading from Edgy to Feisty was completely foolproof.
Do like what is recommended and backup your files, and just do a reinstall.

---

### Post by PatrickMay16 on 2007-07-19
Uh oh! Quick! Shield Arnieboy's eyes.

---

### Post by picpak on 2007-07-19
From the comments:

> Anytime a package is conflicting, I use &#8220;apt-cache policy package&#8221; and see which repositories carry the package. Then I can use &#8220;apt-get package=version&#8221; to install the correct version, and &#8220;apt-cache depends package&#8221; and &#8220;apt-get rdepends package&#8221; to find dependencies. Sometimes I kill the conflicting repository from /etc/apt/sources.list

I did it with Marillat packages and I can do it again. If you can not fix your system because of some weird package and its dependencies&#8230; then you can learn. It is just step by step. I think people using the system doesn&#8217;t have to know how to fix package issues, but people installing packages should.

Well, as if that isn't incredibly convulted. I haven't seen the majority of this documented anywhere, so I don't see how he expects a new user to know it. Personally, I think it's easier through Synaptic:

[LIST=4][*]Go to Status > Installed (local or obsolete)
[*]Choose the package you want to downgrade, and go to Package > Force Version
[*]Choose a version from the Ubuntu repositories
[*]Click OK, click Apply
[/LIST]

---

### Post by Sunflower1970 on 2007-07-19
I've used it when I had Edgy. I had one problem early on with it, (my own fault) but it never broke anything else even with upgrades. One tip I can give though, is before any huge upgrades, uninstall everything Automatix installed. Never had any problems.

---

### Post by compiledkernel on 2007-07-19
> **PatrickMay16 said:**
> Uh oh! Quick! Shield Arnieboy's eyes.

Why?

---

### Post by Frak on 2007-07-19
> **compiledkernel said:**
> Why?
Think about it.
And I hope you are aware that it was created by Arnieboy

---

### Post by az on 2007-07-19
> **Frak said:**
> Nobody said upgrading from Edgy to Feisty was completely foolproof.
Do like what is recommended and backup your files, and just do a reinstall.

That's not what is recommended.  Ubuntu use the best package manager available free software.

To upgrade from one release to the next is easy so long as you don't have stuff installed that is not part of the package manager.

That being said, the article is a little unfair.  The most recent version of Automatix supposedly does use official repos.

---

### Post by az on 2007-07-19
> **Frak said:**
> Think about it.
And I hope you are aware that it was created by Arnieboy

The article calls for better support for Automatix from the Ubuntu community?  Why do you think that hasn't ever happened? 

Because of Arnieboy's attitude.  

It's really unfortunate.

---

### Post by compiledkernel on 2007-07-19
> **Frak said:**
> Think about it.
And I hope you are aware that it was created by Arnieboy

I fail to see why shielding anyone from sensible discussion is needed here. We are all adults here Frak, try to stay on track with that.

---

### Post by tseliot on 2007-07-19
I think that article is a bit of a FUD.

> Breaking Packages:

From the xubuntu blog, Vincent states that Automatix &#8220;gets its packages from sources other than the official Ubuntu ones, it is likely that upgrading to a newer version of Ubuntu will cause problems newbies do not want to deal with.&#8221;

If you update your Ubuntu system frequently, perhaps it is best to stay away from Automatix.
My suggestion is the following:
make a backup of your sources.list before you install and use automatix:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.mybackup
```

Use Automatix to install whatever you need.

then restore the backup:
```
sudo cp /etc/apt/sources.mybackup /etc/apt/sources.list
```

```
sudo apt-get update
```

In this way it is likely that you will not "break" the system with an update.

> Problems with X:

From the Social Discussion blog, Qtwerp states &#8220;I tried Automatix and EasyUbuntu and the script program that is supposed to help install your video card drivers. Each time I ended up with something messed up such as X wouldn&#8217;t start, it would take at least 5 min to fully start up, I still couldn&#8217;t play the movie I wanted to because the software wasn&#8217;t installed, etc. (not all at once)&#8221;

Perhaps the best option for video card installation isn&#8217;t an automatic script, or a program like Automatix, but to actually go out and learn how to install it. This goes back to the old saying, &#8220;feed a man a fish and he&#8217;ll eat for a day, teach a man how to fish, and he&#8217;ll eat for the rest of his life&#8221;. Hopefully this site will enable you to find useful how-tos so that you can learn how to fish.
While one the one hand I agree with the author of the article that learning how to install the drivers is usually better, on the other I think we could sum up this paragraph with "if it doesn't work for me then it sucks". And that's FUD.

**NOTE: I refer to the installation of graphic drivers with Automatix**

If it's true that *sometimes* the installation of graphic drivers with Automatix fails, it is also true that the same can be said of the Restricted Drivers Manager (yes, Ubuntu's official app) and of the methods described in the wikis. Have a look at the "Multimedia & Video" section of this forum to see what I mean.

In my opinion Automatix does its job very well and I use it on all my systems at home even though I know how to do things manually in Ubuntu.

What you should remember is that if you decide to use Automatix or any 3rd party application you'll do it [COLOR="Red"]at your own risk[/COLOR].
[B]
NOTE:[/B] A number of problems can arise when you install the drivers for your graphic card. It doesn't matter which method you choose (the Restricted Drivers Manager, or any other method). That's what I'm talking about. Proprietary drivers do not integrate well with the kernel. We should blame Nvidia and Ati about that. GPL drivers don't cause such problems.

---

### Post by starcraft.man on 2007-07-19
All I will say is I knew from the moment I saw it on digg that someone would post this here :p.

As for the discussion, bleh not really interested. I don't like Automatix that's me, it just doesn't seem needed really... In addition, I'm of the strong opinion that anyone can install in Ubuntu (via regular means) with the right information, that's why I made my guide (in blue).

Oh and Arnie if you are reading this, don't go overreacting again and blast the forum/users over it. That's really getting old. >.>

Edit: Oh and I agree with TS on your last point. If you use Automatix remember that it's at your own discretion and not our responsibility for what it does (good or bad).

---

### Post by ThrobbingBrain66 on 2007-07-19
My comment (first one in the comments) turned out to be not so popular :D

I could have explained myself a bit better.  By "point-and-click" I meant that lots of Windows users will click on any and all executables they see, which obviously is not a good practice.  So instead of learning the correct way to install packages (which is even easier than Windows, I would argue) everyone wants the "total solution" that does everything for them.

---

### Post by Hex_Mandos on 2007-07-19
I'm not pro or anti Automatix, I used it as a newbie and didn't have any problems. Now with Feisty's restricted driver manager and my increased knowledge of Ubuntu I don't have any need for it. However, I'd like to hear from the Automatix haters WHY it's supposed to break updates. I'd like to know how to avoid replicating those errors manually.

---

### Post by xpod on 2007-07-19
12 months,5/6 pc`s,10/12 drives,dozens of different installations............never had a problem with AX.

Always did fresh installs at each new version those first 8 months so upgrading was never a problem.
I liked having absolutely everything i`d ever need(at that time) installed and working as i toddled around the forums etc  learning how to do things these "proper" ways people  spoke of:???:

My pc`s being up and running while many a better man than me came crumbling to the forum seemed pretty "proper" to me at the time i can tell you.

I understand there are some " problems"(i dont know and dont want to know) between certain parties but i still dont understand why so many UN-involved people seem to jump on the bandwagon and start shouting about how evil AX is everytime someone even mentions it.

I`ve also seen a good few new users over the year come on for the first time and ask some simple question about AX(or be advised to use it)  only to have a bunch of "those linux users" all bitching at each other for the next half a dozen pages,with no arnieboy in sight(if thats relevant).....Strange

I dont have AX on my present gutsy/feisty install but it is still on other machines in the house.

---

### Post by ubuntu-geek on 2007-07-20
bump for the people!

---

### Post by Frak on 2007-07-20
I think at least they should come here to gripe about it instead of it not working and just assuming it sucks and  then posting on sites that it sucks and turning away people from AX.

---

### Post by tehkain on 2007-07-20
Eh I have never had a big issue with it. I can see how something may go wrong tho. I just found it easier to type in one apt-get command for all the stuff I needed(tho you have to know what you want so this doe snot work for everyone). I guess I out grew the need.

---

### Post by Gremlinzzz on 2007-07-22
Automatix is a program that installs a myriad programs on Linux distributions. It’s quite useful for people that are fed up with the limited options in the regular Ubuntu package manager. However, as helpful as the program may seem, there exists a problematic side to Automatix. It seems to be breaking systems all over the world. 
[http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/](http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/)

---

### Post by bogolisk on 2007-07-22
> **Gremlinzzz said:**
> Automatix is a program that installs a myriad programs on Linux distributions. It’s quite useful for people that are fed up with the limited options in the regular Ubuntu package manager. However, as helpful as the program may seem, there exists a problematic side to Automatix. It seems to be breaking systems all over the world. 
[http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/](http://pimpyourlinux.com/linux-feature-review/automatix-can-break-your-linux-ubuntu-install/)

I've never liked things like Automatix. The great thing about Debian-based systems such as Ubuntu is the package dependency management system. It help to ensure smooth upgrades. Installing non-packaged software on your system is really *back-stabbing* the package-manager. It's a great recipe for broken upgrades.

If you really wanted to install extra software, learn how to use dh_make/checkinstall. They'll make the package manager aware of the software you installed.

The debian pkg-build system is awesome wrt libraries dependencies (unlike the rpm craps.) It'll automatically generate libraries dependencies for the package by parsing the binaries you just built.

By example, I just built (using dh_make) gimp-dcamnoise2. In the Depends line, I've put
```
Depends: ${shlibs:Depends}, gimp
```

The Debian build system automatically expanded it to
```

Depends: libc6 (>= 2.5-0ubuntu1), libgimp2.0 (<< 2.3.19), libgimp2.0 (>= 2.3.18), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>= 2.10.3), libstdc++6 (>= 4.1.
2), gimp

```

How does it do that? look for the *.shlibs file in /var/lib/dpkg/info/ and you'll understand.

---

### Post by slimdog360 on 2007-07-22
i stopped using it ages ago

---

### Post by Adamant1988 on 2007-07-22
> **Frak said:**
> I think at least they should come here to gripe about it instead of it not working and just assuming it sucks and  then posting on sites that it sucks and **turning away people from AX**.

Which is a move that I completely condone, and even recommend. 

> Oh and Arnie if you are reading this, don't go overreacting again and blast the forum/users over it. That's really getting old. >.>
Actually, I would love to see Arnie come in here and start flaming users.  Maybe if he does it more more people will understand what kind of wannabe tyrant they're feeding by supporting Automatix.
**removed comment**

---

### Post by jrusso2 on 2007-07-22
Never had a problem with Automatix, like everything else use at your own risk.  I have seen synpatic break applications too.

---

### Post by crimesaucer on 2007-07-22
Why use it if you can install everything yourself.

---

### Post by jrusso2 on 2007-07-22
Why use GUI tools?  Why not do everything by hand?  Why not build your own distro you can do everything yourself?

---

### Post by aysiu on 2007-07-22
Red herring.

It's often *easier* to point-and-click "manually" install the desired packages than to visit the Automatix website, download it, install it, and then use it to install those same packages.

The most frequently requested packages people use Automatix for can be done easily through Restricted Drivers Manager, Add/Remove Programs, easy codec installation, and/or Synaptic Package Manager.

---

### Post by Crashmaxx on 2007-07-22
> **aysiu said:**
> 
The most frequently requested packages people use Automatix for can be done easily through Restricted Drivers Manager, Add/Remove Programs, easy codec installation, and/or Synaptic Package Manager.

Exactly, that used to not be true, but as of Feisty, I would consider Automatix obsolete.

---

### Post by jarvis13 on 2007-07-22
[http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released](http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released)

Not only is Automatix horrible, but Arnieboy is a complete douche. 
Check out what he has to say in that digg article from when Automatix for Feisty was released. Guy is a complete idiot.

---

### Post by Adamant1988 on 2007-07-22
> **jarvis13 said:**
> [http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released](http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released)

Not only is Automatix horrible, but Arnieboy is a complete douche. 
Check out what he has to say in that digg article from when Automatix for Feisty was released. Guy is a complete idiot.

Arnav is one of the very few people developing around Ubuntu that I wish would get 'hit by a bus' and not in the metaphorical sense..

---

### Post by jrusso2 on 2007-07-22
I read it and now I am trying to figure out what part he was  a douche in ?

---

### Post by ice60 on 2007-07-22
i tried Automatix for the first time when i did my last ubuntu install and it worked fine. 

probably the problem with it is a lot of noobs use it and noobs tend to break ubuntu with, or without, Automatix.

---

### Post by Steveway on 2007-07-22
When I tried Automatix it broke my package manager.
None of those tricky reconfiguring commands worked then and the only way to make it usable again was by deactivating the automatix repos.
But I don't really need Automatix (How does?) I use Trevinos sources.list and it is a much better way to get repos wich contain all you need, and more.

---

### Post by Frak on 2007-07-22
> **ice60 said:**
> i tried Automatix for the first time when i did my last ubuntu install and it worked fine. 

probably the problem with it is a lot of noobs use it and noobs tend to break ubuntu with, or without, Automatix.
I agree, there are many ways to break your package manager and/or system.

---

### Post by panas on 2007-07-23
Automatix has the essentials 2 clicks away.
The negative is the confirmation during each programs installation.
Yes i could install everything trough synaptic or terminal.
Synaptic=a long time search , point and click.

terminal=ok if i had the commands . 

> can be done easily through Restricted Drivers Manager, Add/Remove Programs, easy codec installation, and/or Synaptic Package Manager.
Can you provide the steps for a working home station with all the programs;
Can you describe the exitment that we get on each installation;
Can you justify the success of automatix;
Can you justify the success of  this forum;

Yes i use the above steps on debian lenny, but guess
what, there is no automatix for unstable-testing version.


I had chozen ubuntu when i made the first steps on linux.
I choose to install it on friends pc ,and automatix is one of the reasons.

Its very easy to turn a success story to just  another distro out there.
Easy task and many volunteers are present .

---

### Post by starcraft.man on 2007-07-23
> **panas said:**
> 
Can you provide the steps for a working home station with all the programs;

Blue link in sig, I explained how to install anything then linked to other sites to get packages, learn more on terminal, etc...

> Can you describe the exitment that we get on each installation;
What excitement? Installing the OS is just something I (and everyone else) do when I have to (i.e. when I can't use a drive image I made). Automatix makes it "exciting" by pushing buttons? 

> Can you justify the success of automatix;
People like easy things no matter if they actually need them (especially once their used to them). People aren't always rational in my experience (arnav's behaviour certainly supports that theory). Some people just don't think they should have to learn anything when switching OSes (Clearly irrational from my POV. Anything a person uses requires some training.) and that "it should just work" and those people are likely better off with a Mac, cuz Linux will always need them to intervene at some point... Automatix doesn't do everything.

> Can you justify the success of  this forum;
People will always have problems with operating systems (that is the nature of software). Windows and OSX also have support forums to my knowledge, that doesn't mean their products are horribly defective (even if I think Vista is...). The forums are here to help those who have trouble, and Automatix certainly doesn't fix all problems, it just installs some things easy.

> 
Its very easy to turn a success story to just  another distro out there.
Easy task and many volunteers are present .

Your point? There are other distros out there that are successful...

Anyway, use what you like. Oh and I dunno why you put semi colons on the end of your questions, instead of question marks...

---

### Post by Adamant1988 on 2007-07-23
> **jrusso2 said:**
> I read it and now I am trying to figure out what part he was  a douche in ?

I'm pretty certain a few of his comments were moderated and removed.  If you notice a few people seem to be replying to attacks from him that you can't find in the discussion.  Probably had his comments dugg-down so much they were removed. 

In any case, his behavior was intolerable on many other occasions.  He's been responsible for a LOT of community drama, and even though he tried to hurt Ubuntu Automatix users they still support him because he'll just  lie about what he was doing.  Then again, for what it's worth, the staff here have taken to telling the exact same lie, so I suppose it wouldn't be that hard to believe it if there weren't available logs pointing to the exact opposite.

---

### Post by compiledkernel on 2007-07-23
> **Adamant1988 said:**
> I'm pretty certain a few of his comments were moderated and removed.  If you notice a few people seem to be replying to attacks from him that you can't find in the discussion.  Probably had his comments dugg-down so much they were removed. 

In any case, his behavior was intolerable on many other occasions.  He's been responsible for a LOT of community drama, and even though he tried to hurt Ubuntu Automatix users they still support him because he'll just  lie about what he was doing.  Then again, for what it's worth, the staff here have taken to telling the exact same lie, so I suppose it wouldn't be that hard to believe it if there weren't available logs pointing to the exact opposite.

Few can forget such behavior, Adamant.

---

### Post by ubuntu-geek on 2007-07-23
I really have to question his statement saying 2 million people are using AX..

[http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released?t=6078756#c6078756](http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released?t=6078756#c6078756)

---

### Post by compiledkernel on 2007-07-23
That shouldnt be hard to prove. 

I think Netcraft lists their site rank as something like 49938. Thats certainly high, but im sure site stats would be easily shown to prove that number "actually" exists.

---

### Post by aysiu on 2007-07-23
> **ubuntu-geek said:**
> I really have to question his statement saying 2 million people are using AX..

[http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released?t=6078756#c6078756](http://digg.com/linux_unix/Automatix2_for_Ubuntu_7_04_Feisty_Fawn_i386_has_been_released?t=6078756#c6078756)
I don't think it matters how many people are using Automatix. For most of them, it's unnecessary. If you're *that* lazy, just use Linux Mint instead of Ubuntu. Seriously.

And if you only want MP3 playback, Flash, Java, and a few other proprietary "essentials," go to Synaptic Package Manager and install *ubuntu-restricted-extras*.

Automatix became popular because of a deficiency in Ubuntu Hoary that lasted until Edgy. With the advent of Feisty, some people are ignoring the fact that Automatix is obsolete for most users. It's inertia. It's familiarity. They've become dependent on Automatix and don't realize its uselessness for their situations. For a lot of users, Automatix is like a bandage they refuse to take off a wound that's already healed.

It also became popular because of controversy/publicity. Arnav has a strong and sometimes offensive personality, which brings Automatix into the limelight, unlike Easy Ubuntu, on which Automatix was based.

There are some rare situations where I'd advise people to use Automatix, but for the most part, people still recommend when the proper procedure (still point-and-click, mind you) would be easier and faster. More here:
[http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/](http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/)

---

### Post by Jellicletrb on 2007-07-23
If it had not been for Automatix, I would have dropped Ubuntu within a couple of days and gone back to windows.  But, AX got everything up and running for me and I stuck with it, and started learning.  I no longer use AX because, crazy as it sounds, I've learned to the point of being able to do those things myself, and I'm learning more all the time.  

I've not seen any kind of numbers or poll results, but I'll bet that Automatix is the only thing that keeps a lot of new users hanging around till they get on their feet with their spanking new OS.

---

### Post by aysiu on 2007-07-23
> **Jellicletrb said:**
> 
I've not seen any kind of numbers or poll results, but I'll bet that Automatix is the only thing that keeps a lot of new users hanging around till they get on their feet with their spanking new OS. Then those people should save themselves some trouble and just use Linux Mint. Why bother going to the Automatix website, downloading their .deb, importing a key, installing Automatix, checking a bunch of checkmarks, and waiting for all those to install... when you can get all that proprietary crap "out of the box"?

---

### Post by Jellicletrb on 2007-07-23
> **aysiu said:**
> Then those people should save themselves some trouble and just use Linux Mint. Why bother going to the Automatix website, downloading their .deb, importing a key, installing Automatix, checking a bunch of checkmarks, and waiting for all those to install... when you can get all that proprietary crap "out of the box"?

Probably for the exact same reason that I didn't.  I'd never even heard of Linux Mint until you posted it just now.:)

---

### Post by aysiu on 2007-07-23
Well, I'm going to propose that if people don't want to bother installing things manually, we should recommend Linux Mint to them. It's the same download time as a Ubuntu .iso, and it comes with all the codecs and such that people expect. It even includes *ndiswrapper* and a graphical editor for /etc/X11/xorg.conf.

---

### Post by ubuntu-geek on 2007-07-23
> **aysiu said:**
> Then those people should save themselves some trouble and just use Linux Mint. Why bother going to the Automatix website, downloading their .deb, importing a key, installing Automatix, checking a bunch of checkmarks, and waiting for all those to install... when you can get all that proprietary crap "out of the box"?
You got a good point..

---

### Post by compiledkernel on 2007-07-23
> **Jellicletrb said:**
> Probably for the exact same reason that I didn't.  I'd never even heard of Linux Mint until you posted it just now.:)

Something a little opening up of Google and typing in the appropriate words would have done. 

Automatix is for the lazy single user, and really if you searched through your documentation a little, youd find that having to go out and download Automatix(2,bleeder,whatever) is an extra step you dont need to take. 

It has no group or large scalability , nor enterprise ability.Iits not any faster  on the enterprise level than it is to use apt-proxy and/or apt-mirror to update massive amounts of machines all on the same relative build of whatever debain based distro your using.

---

### Post by Jellicletrb on 2007-07-23
> **compiledkernel said:**
> Something a little opening up of Google and typing in the appropriate words would have done

But first, you have to know the appropriate words, and like I said, I'd never heard of it.  And don't need it now that I know of, as I've gotten up to speed on getting Ubuntu to work the way I like it without it.  

I do think I might just download Linux Mint and try it out on my antique seldom used laptop, it looks interesting.  :)

---

### Post by aysiu on 2007-07-23
> **Jellicletrb said:**
> But first, you have to know the appropriate words, and like I said, I'd never heard of it.  And don't need it now that I know of, as I've gotten up to speed on getting Ubuntu to work the way I like it without it.  

I do think I might just download Linux Mint and try it out on my antique seldom used laptop, it looks interesting.  :)
There are only two things I *don't* like about Linux Mint, both of which can easily be changed:

1. Its default theme (I switch it to Human)
2. Its Gnome menu, which looks too complicated--a lot like Windows' Start menu (I replace it with the regular Gnome menu)

---

### Post by ubuntu-geek on 2007-07-23
> **aysiu said:**
> There are only two things I *don't* like about Linux Mint, both of which can easily be changed:

1. Its default theme (I switch it to Human)
2. Its Gnome menu, which looks too complicated--a lot like Windows' Start menu (I replace it with the regular Gnome menu)
This is really a good read. I like how you point out how many more steps are involved with installing something with AX then the regular ubuntu tools.

[http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/](http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/)

---

### Post by Jellicletrb on 2007-07-23
> **aysiu said:**
> There are only two things I *don't* like about Linux Mint, both of which can easily be changed:

1. Its default theme (I switch it to Human)
2. Its Gnome menu, which looks too complicated--a lot like Windows' Start menu (I replace it with the regular Gnome menu)


That sounds terrific..if it's all that, maybe we should rec it instead of automatix.  I've started a download already and I'm going to make it tonight's "nothing on TV" project  :popcorn:

---

### Post by matthew on 2007-07-23
> **ubuntu-geek said:**
> This is really a good read. I like how you point out how many more steps are involved with installing something with AX then the regular ubuntu tools.

[http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/](http://ubuntucat.wordpress.com/2007/05/22/why-i-dont-recommend-automatix-not-what-you-may-think/)

He has a gift for explanation.

---

### Post by ubuntu-geek on 2007-07-23
> **Jellicletrb said:**
> That sounds terrific..if it's all that, maybe we should rec it instead of automatix.  I've started a download already and I'm going to make it tonight's "nothing on TV" project  :popcorn:
Really pointing users to this page is a good step. I mean its pretty easy..

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by John.Michael.Kane on 2007-07-23
With the many guides/wikipages/sticky methods for installing programs/codecs/etc 
this is no longer about the program being an easy way to install program X, and  as far as I can see it lost that status along time. 

IMHO it seems the use of this program is based only on coolness or XYZ users friend saying this is how I did, and it will work for you. 

Users new to linux/ubuntu who are told/suggested to use automatix, and lead to believe its the end all be all easy for there install needs will be sadly mistaken. End users need to understand they will eventually need to use synaptic or even the command line. 

Automatix should be the absolute last resort for an end user.

---

### Post by compiledkernel on 2007-07-23
> **SD-Plissken said:**
> 
Automatix should be the absolute last resort for an end user.

Pretty much.

---

### Post by Jellicletrb on 2007-07-23
> **SD-Plissken said:**
> Users new to linux/ubuntu who are told/suggested to use automatix, and lead to believe its the end all be all easy for there install needs will be sadly mistaken. End users need to understand they will eventually need to use synaptic or even the command line. 

Automatix should be the absolute last resort for an end user.

Well, I will admit I came to these forums my first time completely lost, with a system that barely worked and unable to figure out how to get my XP re-installed because I couldn't delete the Linux partition. etc etc etc.  I got a lot of "RTFM", and the people that did try to help were speaking way, way above my head.  So, what I learned the first few days was mostly from using the forum search feature and guessing at search words.  I totally agree that end users need to know far more than AX requires, but a lot of people have gotten so fed up with answering the same questions over and over for every new user that shows up that they let their frustration show, and  there are probably some that simply leave feeling lost and out of the loop.

---

### Post by compiledkernel on 2007-07-23
> **Jellicletrb said:**
> Well, I will admit I came to these forums my first time completely lost, with a system that barely worked and unable to figure out how to get my XP re-installed because I couldn't delete the Linux partition. etc etc etc.  I got a lot of "RTFM", and the people that did try to help were speaking way, way above my head.  So, what I learned the first few days was mostly from using the forum search feature and guessing at search words.  I totally agree that end users need to know far more than AX requires, but a lot of people have gotten so fed up with answering the same questions over and over for every new user that shows up that they let their frustration show, and  there are probably some that simply leave feeling lost and out of the loop.

[http://doc.gwos.org](http://doc.gwos.org)
[http://help.ubuntu.com](http://help.ubuntu.com)
[http://wiki.ubuntu.com](http://wiki.ubuntu.com) 
[http://ubuntuguide.org](http://ubuntuguide.org)

Go there first, then start asking questions on the forums.

Best process that I know.

---

### Post by kelvin spratt on 2007-07-23
Well I use Automatix but only for one thing its the only application that sets up ntfs3g correctly on my system using Ubuntu,  this may be unique to my system but with out it i can't download direct to a ntfs partition so i use it for that and i had a similer problem with etch and again automatix did the trick. but not with Elive, pardus,

---

### Post by bodhi.zazen on 2007-07-23
> **Jellicletrb said:**
> If it had not been for Automatix, I would have dropped Ubuntu within a couple of days and gone back to windows.  But, AX got everything up and running for me and I stuck with it, and started learning.  I no longer use AX because, crazy as it sounds, I've learned to the point of being able to do those things myself, and I'm learning more all the time.

Well, that is the problem with automatix isn't it ?

When you are new to an OS you need to be prepared to learn. If you use automatix :

1. It is more difficult (as has been pointed out on this thread) to learn the the proper tools (apt-get, aptitude, synaptic, add/remove programs).

2. It impedes learning. You said it yourself, " I've learned to the point of being able to do those things myself, and I'm learning more all the time ". The Ubuntu forums staff feel it is important to teach the proper way if you will. Once you use the proper tools, who needs Ax ? IMO Ax is harder then Synaptic, no ? So the question becomes, why Ax at all ? 

3. Automatix causes system breakage. Ax defenders point out so does xyz ... The point is if xyz is an Ubuntu package, the Ubuntu developers will work in it (see reporting bugs and Launchpad) and the Ubuntu forums will support it. The problem is Ax is 3rd party, which means not supported by the Ubuntu developers, launchpad,  or the Ubuntu forums.

4. Biggest problem with Ax is the developers. When they do bother to show up on the forums they freely break the Ubuntu Code of Conduct, the will not admit Ax has problems, and they do not fix problems (usually they just rant).

So why don't the Ax developers join the Ubuntu Developers ? LOL ~ just read thier posts. Not only have the Ax developers not offered one piece of code back to Ubuntu, they are egomanicial, impossible to work with, and not willing to follow the code of conduct (making them undesirable as part of any development team, let alone Ubuntu where we like to be more humane).

Best is Ax is recognized for what it is, an Ubuntu Fork. They need to establish their own site and, if they can not follow the code of conduct, banned from the forums.

Ax was helpful long ago (don't know when) but it is now outdated and detrimental to Ubuntu and the Forums (because of their conduct).

---

### Post by matthew on 2007-07-23
> **Jellicletrb said:**
> I got a lot of "RTFM"
If you ever get that response again on these forums, please report the post immediately. That sort of thing is frowned upon around here.

Sometimes reading documentation is necessary, but we aim for really good customer service and friendliness, while helping people educate themselves. :)

---

### Post by ubuntu-geek on 2007-07-23
Good read! I think there needs to be an initiative to direct the users in the correct way. Showing them how easy it is using the default tool set in ubuntu.

---

### Post by compiledkernel on 2007-07-23
I think the rationale that the default Ubuntu install , as of now, REQUIRES automatix is a rather dim view.  The object of th  project is to improve its ability to function, not hinder itself by depending on extraneous 3rd party software to achieve certain functionalities.  Perhaps those who are desiring certain levels of that functionality spent more time actually collaborating with the community rather than going against it, the same functionality would exist without the need for 3rd party apps. 

*another 2 cents* I gotta be up to at least a dolar by now.

---

### Post by ubuntu-geek on 2007-07-23
> **compiledkernel said:**
> I think the rationale that the default Ubuntu install , as of now, REQUIRES automatix is a rather dim view.  The object of th  project is to improve its ability to function, not hinder itself by depending on extraneous 3rd party software to achieve certain functionalities.  Perhaps those who are desiring certain levels of that functionality spent more time actually collaborating with the community rather than going against it, the same functionality would exist without the need for 3rd party apps. 

*another 2 cents* I gotta be up to at least a dolar by now.
True but I think it's safe to say the default tools provided with Ubuntu can achieve the same result in a much more reliable way. Don't you agree.

---

### Post by compiledkernel on 2007-07-23
.....In a fashion that is officially supported by the official support team, yes. And ultimately every user should follow this path anyway. Relying on third party apps, then trying to get support later, depending on the nature of your problems, can get you into a bind. The IRC team is unlikely to help you. The mailing list will do the same. And in a lot of cases, getting support for such applications even here, can prove to be difficult. Ergo, all the way around its just safer, and more in line to use official means to install applications.

---

### Post by paparucino on 2007-07-23
> **bodhi.zazen said:**
> Well, that is the problem with automatix isn't it ?

When you are new to an OS you need to be prepared to learn. .
You hit the problem.
Some people think that since they are able to click **OK** on a Windows autoinstall tool make them "computer's guru".
Then, since they are "guru" they need to change OS. Linux, mainly Ubuntu, is the first choice. 
But they forget when they learned to use the keyboard and to understand what a file is. They had to learn, to ask, to receive a lot of RTFM answers.
A "guru" cannot study so he searches, when installing Ubuntu, for all the tools which allow him to install everything with a "point & click" as he used with Windows.
There is a program which tries to do the "point & click" installation but it has "some problems" and
after a few days, the "guru" reach the forums to ask for help since the system is working in a strange and, I don't agree with this behaviour, gets some RTFM.

---

### Post by aysiu on 2007-07-23
I disagree completely.

Point-and-click installation is just fine, and that's why Automatix is obsolete. You can do almost everything point-and-click *without* Automatix. The only thing I can think of that you might need to do a little editing of a text config file for is adding the Medibuntu repositories, which is also just copying and pasting (point and click) two commands into the terminal.

---

### Post by compiledkernel on 2007-07-23
[IMG]http://img266.imageshack.us/img266/6735/axic4.png[/IMG]

Wow...just....Wow.

---

### Post by Jellicletrb on 2007-07-23
> **matthew said:**
> If you ever get that response again on these forums, please report the post immediately. That sort of thing is frowned upon around here.

Sometimes reading documentation is necessary, but we aim for really good customer service and friendliness, while helping people educate themselves. :)

I'm sorry, I need to clarify that statement just a tad...it's been many, many months since I have had that response (since Nov I think), and I've not seen it directed at anyone else.  Except for a couple of posters way back when, everyone has been quite helpful.  A little cantankerous at times, but hey, thats allowed  :lolflag:

---

### Post by matthew on 2007-07-23
> **Jellicletrb said:**
> I'm sorry, I need to clarify that statement just a tad...it's been many, many months since I have had that response (since Nov I think), and I've not seen it directed at anyone else.  Except for a couple of posters way back when, everyone has been quite helpful.  
Phew. I'm glad to hear that.
> **Jellicletrb said:**
> A little cantankerous at times, but hey, thats allowed  :lolflag:lol...like parts of this thread? :)

---

### Post by paparucino on 2007-07-23
> **aysiu said:**
> I disagree completely.

Point-and-click installation is just fine, and that's why Automatix is obsolete. You can do almost everything point-and-click *without* Automatix. The only thing I can think of that you might need to do a little editing of a text config file for is adding the Medibuntu repositories, which is also just copying and pasting (point and click) two commands into the terminal.

I agree that Ax is obsolete :-) but I think I wasn't able to explain what I mean which is the wrong approach with a new OS.

---

### Post by kelvin spratt on 2007-07-23
FIRST OF ALL  I'M NOT FLAMING JUST GIVING THE OTHER SIDE OF THE STORY
I think you have freedom of choice if you go to the Automatix site and take time to read it does warn you that some things might not work and you don't have to use it, you choose whether to or not, Its for you to take responsibility for your actions. If you decide to put the wrong tyres on your car and you crash you can't blame the tyres can you, this is just the same you make the decision nobody forces you?.  And to somebody new Synaptic is  just double Dutch it was to me, in windows everything is graphical not everything in Synaptic works  without tweaking so you always  take a small chance, i installed from synaptic once and it just stopped so like an idiot i closed it down couldn't get it to work again panicked  and re-installed Edgy the thing that is  different is i did not come on the forum and blame Synaptic it was my fault!, Ive also used things from Getdeb net that have broke things, and i do believe they actually belong to Conical. Also in windows a good 80% of programs don't do what it says on the box try complaining, it all says it comes with no warranty what so ever and you pay for it. I personally think people are taking things to much to heart over Automatix its only an aid it works for some not for others.and should be left to rest then it will die its own death?

---

### Post by bodhi.zazen on 2007-07-23
> **kelvin spratt said:**
> FIRST OF ALL  I'M NOT FLAMING JUST GIVING THE OTHER SIDE OF THE STORY
I think you have freedom of choice  ...

Yawn ... Ah yes the "freedom" card.

I think you miss the point. The point of the debate is not to restrict your freedom, you can go to the automatix site and install all the third party applications you desire.

The debate it is about support on the Ubuntu forums for third party software that, in the case of Ax, is obsolete, known to cause breakage, and is maintained by a group of folks that is unable to follow the Ubuntu Code of Conduct.

---

### Post by loell on 2007-07-23
these are one of the threads  where ubuntuforum staff showed much participation , who seems to be bound to hate automatix, or is there a staff  out there who has an opposite opiniion over the matter?

if i remember correctly, in pask weeks or so, there was this thread where automatix has been discussed. 
and a staff closed it, for the reason that "**this**" had been disccussed over and over again...


how is this different from the others?  isn't it bias?

so, in the name of fairness and equality, may i request this thread to be close too?

---

### Post by markusf21 on 2007-07-23
First off I have used AX in the past as a newb. I dont use it now at all. I have learned to do those things myself (and have also gotten better at finding help). The problem for newbs is that help is not that easy to find if u have no idea what these commands mean. That being said I feel that automatix is no longer needed by anyone. (as long as they have the right How To:) So why not have the proper How To: be put on the desktop at install? 
for example
How To: play mp3
How To: mount NTFS with read/write permissions
ETC
ETC
ETC
The Common things automatix does. And then we can just watch AX die
Sound like an easy newb friendly fix to me and you can just delete it when you don't need it anymore

---

### Post by rocknrolf77 on 2007-07-23
> **markusf21 said:**
> First off I have used AX in the past as a newb. I dont use it now at all. I have learned to do those things myself (and have also gotten better at finding help). The problem for newbs is that help is not that easy to find if u have no idea what these commands mean. That being said I feel that automatix is no longer needed by anyone. (as long as they have the right How To:) So why not have the proper How To: be put on the desktop at install? 
for example
How To: play mp3
How To: mount NTFS with read/write permissions
ETC
ETC
ETC
The Common things automatix does. And then we can just watch AX die
Sound like an easy newb friendly fix to me and you can just delete it when you don't need it anymore

I like your idea with the document in the desktop. Pclinuxos have one, with the most common questions.

Or maybe a link to [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) :-P

---

### Post by Foxmike on 2007-07-23
> **kelvin spratt said:**
> FIRST OF ALL  I'M NOT FLAMING JUST GIVING THE OTHER SIDE OF THE STORY
I think you have freedom of choice if you go to the Automatix site and take time to read it does warn you that some things might not work and you don't have to use it, you choose whether to or not, Its for you to take responsibility for your actions. If you decide to put the wrong tyres on your car and you crash you can't blame the tyres can you, this is just the same you make the decision nobody forces you?.  And to somebody new Synaptic is  just double Dutch it was to me, in windows everything is graphical not everything in Synaptic works  without tweaking so you always  take a small chance, i installed from synaptic once and it just stopped so like an idiot i closed it down couldn't get it to work again panicked  and re-installed Edgy the thing that is  different is i did not come on the forum and blame Synaptic it was my fault!, Ive also used things from Getdeb net that have broke things, and i do believe they actually belong to Conical. Also in windows a good 80% of programs don't do what it says on the box try complaining, it all says it comes with no warranty what so ever and you pay for it. I personally think people are taking things to much to heart over Automatix its only an aid it works for some not for others.and should be left to rest then it will die its own death?

Speaking about cars.  If you don't know a thing about car, and 10 people you are asking questions suggest you to put on some 4 seasons tires on it, you will end-up believe them.  This is important, tho, that you take informed decision.  If, after, somebody tell you that, with that kind of tire, it's risky to drive in actual winter, then you know about the risk.  I think that it doesn't really matters if you still chose to put on some 4 seasons tires, it is your absolute right.  You know about the risk **_and you assume it._**  

Now, some other car-illetrate get around, asking for questions, and he's been told by some experienced people to put on some winter tires, in order to make the car run well in winter.  Some other experience people suggest to try those kool 4 seasons tires. What if, then, the designer of those tires is going to tell: "You know what, there is nothing wrong with those tires in winter, don't worry..."  even if everybody else is saying not...  that is the problem here.

An informationnal problem about a potentially risky software that is being suggested to newbees instead of the proper way in order to keep things clean.

---

### Post by information_entropy on 2007-07-23
To me, the real question is who is the target market/audience for Automatix and is it meeting the needs of that group.   

In general I would say the the Ubuntu users that are posting questions about compiling there own kernel or asking questions in the Programming Forum are not likely to be using Automatix.  Anyone with a desire to learn about how Ubuntu or Linux works is more likely to want to know how use apt-get, aptitude or the Synaptic Package Manager.  The users that are running multiple distributions of Linux or BSD or Solaris are not likely to use it either.

The primary users of  this Automatix thing appear to me to be the “I just want my YouTube, IM, IRC, MP3 player, video player, CD ripper, Video ripper software to work” group of users.  They do not want to learn anything new they just want their Internet toys to work right now.  

Therefore, the first issue with Automatix is that if it does breaks something, it does so on the systems of those least likely to be able to fix it.  The situation is that there are so many different system configurations that it is for all practical purposes impossible for a small group to people to sufficiently test it.  The more who use it the more breakage will occur.  If it breaks systems, then it fails to meet the needs of those who are most likely to use it.

The second issue is relevance.    As Ubuntu specifically and Linux in general continue to improve their installation methods and procedures,  the need for a program like Automatix is rapidly diminishing.  As applications mature and their developers improve and refine the installation of their software product the need evaporates.

I can think of hundreds of programs that were widely used and relevant at one time, but have simply fallen by the wayside as technology changed and advanced.  Most left their mark and then went quietly into the history of  software development, but a few went down hard, their developers and supporters screaming “we are still relevant” to the bitter end. 

My hair started turning gray long ago.:(
I blame One and his friend Zero.

---

### Post by compiledkernel on 2007-07-23
> **information_entropy said:**
> 
I can think of hundreds of programs that were widely used and relevant at one time, but have simply fallen by the wayside as technology changed and advanced.  Most left their mark and then went quietly into the history of  software development, but a few went down hard, their developers and supporters screaming “we are still relevant” to the bitter end. 

My hair started turning gray long ago.:(
I blame One and his friend Zero.

Microsoft BOB comes to mind, . Boy im showing my age when I say that. Seriously though, while at one point it may have been needed, it isnt needed near on the level that it once was. Perhaps , and Ive said this more than once, its either time for the application mentioned , Automatix, to either evolve or grace away. Either way, lt left its mark, and it made its impression. Do I feel it needs to continue? Not really. But like all things in this world, freedom is the right to choose, and the right to express As I keep on doing right here. 

=)

---

### Post by kelvin spratt on 2007-07-24
Freedom is the right to choose . Freedom is also your right not to be Dictated to as well. so anybody that tries to force their opinion is not only a dictator but is taking away the other persons freedom.
mandog

---

### Post by Jellicletrb on 2007-07-24
> **aysiu said:**
> There are only two things I *don't* like about Linux Mint, both of which can easily be changed:

1. Its default theme (I switch it to Human)
2. Its Gnome menu, which looks too complicated--a lot like Windows' Start menu (I replace it with the regular Gnome menu)

Well, I downloaded Linux Mint, and played with it a bit last night, and a lot this morning.  In fact, I'm posting this from a Mac Mini running Linux Mint in live mode  :)

And so far, I think that it would be an **excellent** OS to recommended to the new folks, instead of pointing them at helper apps like Ax and easyubuntu.  The Mini's wireless even works under the live CD, quite impressive.

..and Aysiu, you are so right..the menu does look very "windowsy".  But, it can be changed in seconds...:lolflag:

---

### Post by compiledkernel on 2007-07-24
> **Jellicletrb said:**
> Well, I downloaded Linux Mint, and played with it a bit last night, and a lot this morning.  In fact, I'm posting this from a Mac Mini running Linux Mint in live mode  :)

And so far, I think that it would be an **excellent** OS to recommended to the new folks, instead of pointing them at helper apps like Ax and easyubuntu.  The Mini's wireless even works under the live CD, quite impressive.

..and Aysiu, you are so right..the menu does look very "windowsy".  But, it can be changed in seconds...:lolflag:

We aim to please in our ability to direct you to the proper resources Jell.

---

### Post by crane on 2007-07-24
To those who are new here, this is an ongoing flame war between many Ubuntu users. I would suggest you read how-to's and learn that setting up your OS is easy an does not require a script that assumes your an idiot.  Your not an idiot, your using Linux which tells me you are looking for a better way. BUT, if you wish to use a script based fixall then by all means ty automatix or any other installer-script-thingy you want. Know this, there have been reports of problems some imediate some will not show up until you update your system but there have been reports of this. So if you use it and it breaks your system don't come back to these forums talking about how Ubuntu/Linux sucks or even how the program you used sucks. Take it to their site, it they don't have an official site supporting their program then I would not suggest trying it.
 Freedom, I love how both side throw this word around. Yes you have the fredom to use ot not use, support or not support, hate/love, dictate or be dicated to. You also have the freedom to seek the easiest path or the path that will lead to greater knowledge. I say leave the freedom card out of this game.

 oh one more thing........
     Always keep in mind.........
               *** There is no spoon***


:)

---

### Post by aysiu on 2007-07-24
With all due respect, crane, I think Automatix doesn't assume you're an idiot at all. It assumes you know how to install .deb files and select from various optional components in order to get Ubuntu "working."

**Beginners who can't be bothered**
If you are a new user who doesn't want to bother with getting things to "just work" with proprietary formats, you should download Linux Mint, which is a customized Ubuntu that includes different artwork, different default applications, and all the popular proprietary codecs to make things "just work."

**Special Situations**
I would recommend Automatix to those who want a lot of specialized things that cannot be easily installed otherwise. For example, commercial software (like Crossover Office) or Flash playback for 64-bit Ubuntu (which ordinarily requires an annoying manual workaround).

**Everyone else**
If you actually don't mind doing one or two things, you should get vanilla Ubuntu and let the built in easy codec installation, Restricted Drivers Manager, and Synaptic Package Manager handle installation for you.

---

### Post by Jellicletrb on 2007-07-24
> **Jellicletrb said:**
> Well, I downloaded Linux Mint, and played with it a bit last night, and a lot this morning.  In fact, I'm posting this from a Mac Mini running Linux Mint in live mode  :)

And so far, I think that it would be an **excellent** OS to recommended to the new folks, instead of pointing them at helper apps like Ax and easyubuntu.  The Mini's wireless even works under the live CD, quite impressive.

..and Aysiu, you are so right..the menu does look very "windowsy".  But, it can be changed in seconds...:lolflag:

OK, I R a dope  #-o

The Mac Mini's wireless** doesn't** work on the live CD....I had forgotten that I'd run a cable to the Mini to speed up a big download over the weekend.  It dawned on me just a minute ago that I'd never entered the passphrase for my network and that something was amiss.

D'oh.

---

### Post by John.Michael.Kane on 2007-07-24
> **aysiu said:**
> With all due respect, crane, I think Automatix doesn't assume you're an idiot at all. It assumes you know how to install .deb files and select from various optional components in order to get Ubuntu "working."

The program does make some assumptions. one of which is that users want the easy way out. 
Two it assumes users who download it do not want to read guides/howto's.  for installing the same programs that it does.

> **aysiu said:**
> **Beginners who can't be bothered**
If you are a new user who doesn't want to bother with getting things to "just work" with proprietary formats, you should download Linux Mint, which is a customized Ubuntu that includes different artwork, different default applications, and all the popular proprietary codecs to make things "just work."

This I will agree with to a certain degree. linux mint solves the codec issue,however. even users of this distro will eventually have to pull a program via synaptic/add remove, As well as have to use to command line. Theres no getting away from it even using this distro.

> **aysiu said:**
> **Special Situations**
I would recommend Automatix to those who want a lot of specialized things that cannot be easily installed otherwise. For example, commercial software (like Crossover Office) or Flash playback for 64-bit Ubuntu (which ordinarily requires an annoying manual workaround).

While I can't speak on crossover office. I can tell you Flash on 64bit does not as you say ( require an annoying manual workaround). it requires the user to download, and run a simple script that walks you through the install process.

---

### Post by misfitpierce on 2007-07-24
Only thing I saw was it didnt install hamachi correct. Other than that everything else works fine on mine and friends computer.

---

### Post by compiledkernel on 2007-07-24
Is the path of least resistence always the more considerable case? 

I understand the concept of special cases, but I believe even those have been given some level of consideration. Where this might not be the case is something that chooses to install via a loki-esque installer. But the steps to install something like that are even mcuh easier than was previous.

---

### Post by ubuntu-geek on 2007-07-24
Hmm so some broken logic.. We are assuming that if the user has the knowledge to install the AX .deb file manually we could also assume the same user has the knowledge to install any other .deb file just as easily.

So, is it really an application for new users or an app for users who are lazy.

---

### Post by John.Michael.Kane on 2007-07-24
> **ubuntu-geek said:**
> Hmm so some broken logic.. We are assuming that if the user has the knowledge to install the AX .deb file manually we could also assume the same user has the knowledge to install any other .deb file just as easily.

So, is it really an application for new users or an app for users who are lazy.

Depends on who you ask.

Then again all one has to do is look at the way it's marketed to the user.

---

### Post by compiledkernel on 2007-07-24
Id have to assume that some level of configuration occurs when installing something with AX. the additional configuration that it provides is part of the motivation. NTFS config would be one example. But im fairly sure that tne NTFS Configuration tool in System under Add/Remove does much of the same as what AX might provide configuration wise. Arnav has stated that certain source packages are installable by Automatix. Id be curious to hear what source packages those are. And why it wouldnt be just as easy to create debs from said source packages to be provided to MOTU , Getdeb.net, or other such resource for user consumption. Because really if you can open up a terminal and sudo dpkg - i automatix.deb, then you can just as easily do that for any other package that comes in a deb format.

---

### Post by compiledkernel on 2007-07-24
> **SD-Plissken said:**
> Depends on who you ask.

Then again all one has to do is look at the way it's marketed to the user.

I dont pay much attention to that. How is it marketed to the user? is the user aware there is an alternative to what they are doing?

---

### Post by Foxmike on 2007-07-24
> **compiledkernel said:**
> I dont pay much attention to that. How is it marketed to the user? is the user aware there is an alternative to what they are doing?
 
That goes down to the main problem, IMHO.  The information.  If the user primary is primarily suggested to use Automatix (or any other "helper-script"), then she is misinformed from the beggining.  How-tos are generally easy to use, event the "sudo dpkg -i automatix2.deb" is quite easy to copy/paste in a terminal, even if you don't have a clue about what is going on.  I came it to Linux not so long ago, whit Breezy, and I do remember to blindly copy/paste terminal commands to the terminal, because I didn't knew about it and I was on a rush to make things works (thanks god, I got wiser with time!;))
 
And because Automatix seems to work well for a lot of people (or it breaks things, but the user is so much used to broken system that she is not aware that there is an actual breakage), it is quite often suggested as "the easy way to go" even if after all, this is not always true.
 
An other thing, to make things clearer, it is important to precisely determine (good word?  I'm native francophone...) the limit where a "helper-script/software" is considered to be dangerous or not.  What about Loki installers.  Those are kind of helper script, no?  And those .run scripts.  I'm bringing the point because I think it might eventually confuse people.  At least me;).
 
Regards,
-FM

---

### Post by Sunflower1970 on 2007-07-24
I hope, after reading all of these pages, those that have a huge dislike for Automatix do not look down upon those who have used it in the past, or are using it now, for whatever their personal reason it is to do so, because some of the posts really made me feel a lesser linux user than those who have never used it at all. I'm sure that was never the intent of their posts, though.

Compiledkernel's siggie says this all best. Simple, straight to the point, gives a link, and doesn't start a love/hate debate over this program. Why not just give that answer to someone who inquires about it instead of all this other 'baggage' that comes with it?

---

### Post by Foxmike on 2007-07-24
@Aysiu: by the way, your habbit to use feminine to talk about an hypothetic 3rd person is very elegant.  Best regards!:)

---

### Post by aysiu on 2007-07-24
> **Sunflower1970 said:**
> I hope, after reading all of these pages, those that have a huge dislike for Automatix do not look down upon those who have used it in the past, or are using it now, for whatever their personal reason it is to do so I don't look down on anyone who uses Automatix. But I feel a lot of people who do it do so not knowing that it is probably not the best choice for them. Everyone is entitled to make her own choices. But they should be informed choices. > **Foxmike said:**
> @Aysiu: by the way, your habbit to use feminine to talk about an hypothetic 3rd person is very elegant.  Best regards!:) You're one of the very few on these forums who looks upon that practice favorably. [I've gotten a lot of flack about that in the past.](http://ubuntuforums.org/showthread.php?t=313881&highlight=third-person+singular+pronoun) You can read more here about my reasons for doing so: [http://ubuntucat.wordpress.com/2006/07/29/why-i-say-she/](http://ubuntucat.wordpress.com/2006/07/29/why-i-say-she/)

---

### Post by Foxmike on 2007-07-24
> **aysiu said:**
> I don't look down on anyone who uses Automatix. But I feel a lot of people who do it do so not knowing that it is probably not the best choice for them. Everyone is entitled to make her own choices. But they should be informed choices. You're one of the very few on these forums who looks upon that practice favorably. [I've gotten a lot of flack about that in the past.]("http://ubuntuforums.org/showthread.php?t=313881&highlight=third-person+singular+pronoun") You can read more here about my reasons for doing so: [http://ubuntucat.wordpress.com/2006/07/29/why-i-say-she/](http://ubuntucat.wordpress.com/2006/07/29/why-i-say-she/)
Wow!  49 posts on that? I don't have time right now to read all that, but I'll look forward those posts as an interesting social phenomenon:D.  Best regards!
 
-FM

---

### Post by compiledkernel on 2007-07-24
Ive always thought Aysiu as elegant in speaking. His ability to write amazes me.

---

### Post by ice60 on 2007-07-24
obiviously i haven't read everything that's been written about AX in the past, but from what i have read it seems the threads used to go like this -

someone says something rude about AX/Arnieboy, then Arnieboy gets side-tracked by that and replies, then everyone goes off slapping each other on the back saying how much they hate him.

it's good to see Arnieboy doesn't take the bait anymore. what we're left with is master baiters :lolflag:

---

### Post by loell on 2007-07-24
i too don't often understand in the past, why others would brag about his "attitude" towards certain individuals,
oh well whatever it is, keeping silent and not retaliating on these kinds of threads is certainly a sign of an improved and good attiude of arnieboy.

---

### Post by Frak on 2007-07-24
> **compiledkernel said:**
> Ive always thought Aysiu as elegant in speaking. His ability to write amazes me.
He's like Cooper and Webster (dictionary) merged together.
Personally, though, I use Automatix still, just because I find it easier. When I'm done, I can just uninstall it.

---

### Post by handy on 2007-07-24
I have used Automatix since I discovered it when I was first using Breezy.  I use it every time I set up a machine on Ubuntu, which has been somewhere around fifteen times, these setups have all been clean installs except one, when I upgraded from edgy to feisty with an expectation of probably trashing my system due to having installed quite a few things via Automatix2.  I had a completely smooth OS upgrade!

Automatix(2) has never caused me any trouble.  It is really convenient when setting up a machine.  I don't know if it has become redundant in Feisty or not, because bugs in Ubuntu won't let me run Edgy or Feisty on my main machine satisfactoraly, & my testing machines have got better things to do.

I don't think personalities should be involved in the Automatix debate.  A person can know that Automatix has helped or hindered them, reacting accordingly & allow others to make the same conclusions from experience.  

As far as the attitudes ranging from the right wing extremes, of everyone should compile all software that is to be installed on a machine themselves, & mouses are evil! To the more common expectations of what ***other*** Linux user's are required to be able to do with the OS to meet someone else's personal standard!  That is just elitist rubbish.  

Use your computer anyway you like & off to the wrathful deities with other people's attitudes on the matter.

---

### Post by starcraft.man on 2007-07-24
> **handy said:**
> 
As far as the attitudes ranging from the right wing extremes, of everyone should compile all software that is to be installed on a machine themselves, & mouses are evil! To the more common expectations of what ***other*** Linux user's are required to be able to do with the OS to meet someone else's personal standard!  That is just elitist rubbish.  


I don't know where you got this, I just went back 4-5 pages and I didn't see anyone saying compile your software from source code. I agree that compiling everything is needless and shouldn't be expected of even experienced users (unless they choose to). You can install everything you need in Ubuntu without going to source code or Automatix (other scripts), thats the gist of what most of the posters want users to realize. 

> Use your computer anyway you like & off to the wrathful deities with other people's attitudes on the matter.

I don't think you get what was said. Most people aren't trying to say you can't use Automatix (if you go back, Aysiu would even suggest it for installing some things in 64 bit Ubuntu), rather that lots of users use it without knowing that regular means aren't that difficult (like I explained in my guide, blue link). I don't mind people suggesting Automatix, but give them an informed choice and point them to how tos (like mine) so they can use regular means if they want to spend the time learning. Freedom is important in Linux, especially being informed when making that choice IMO (cuz we all know how Proprietary companies like to remove your choices).

---

### Post by aysiu on 2007-07-25
**Anti-Automatix FUD**:
It'll break your system. It'll break your system!

**Pro-Automatix FUD**:
It's either Automatix or compiling from source. We don't all want to compile from source or do things through the terminal.

---

### Post by handy on 2007-07-25
> **starcraft.man said:**
> I don't know where you got this, I just went back 4-5 pages and I didn't see anyone saying compile your software from source code. I agree that compiling everything is needless and shouldn't be expected of even experienced users (unless they choose to). You can install everything you need in Ubuntu without going to source code or Automatix (other scripts), thats the gist of what most of the posters want users to realize. 

I was drawing on the Automatix threads & posts that I've seen over the last 20 months or so & stating an extreme view that is held by a few.  I did not read the 100 odd posts in this thread.

I know it can be all done without Automatix.

As previously stated some find it very convenient at what ever stage.  For me, it's usually initial setup of a system.

> **starcraft.man said:**
> 
I don't think you get what was said. Most people aren't trying to say you can't use Automatix (if you go back, Aysiu would even suggest it for installing some things in 64 bit Ubuntu), rather that lots of users use it without knowing that regular means aren't that difficult (like I explained in my guide, blue link). I don't mind people suggesting Automatix, but give them an informed choice and point them to how tos (like mine) so they can use regular means if they want to spend the time learning. Freedom is important in Linux, especially being informed when making that choice IMO (cuz we all know how Proprietary companies like to remove your choices).

Yes, I agree with you.  I also think a whole lot of time & energy has been wasted on the topic of Automatix.  Use it or don't, recommend it or don't, who cares?  It works perfectly for some, & *apparently* has trashed other's systems, that's computing.  

As far as an ordained from above Ubuntu political stance regarding anything & everything to do with Automatix, that is a little complicated due to Arnie having a strong personality & having rubbed other personalities the wrong way.

Automatix is a storm in a teacup.

---

### Post by starcraft.man on 2007-07-25
> **handy said:**
> I was drawing on the Automatix threads & posts that I've seen over the last 20 months or so & stating an extreme view that is held by a few.  I did not read the 100 odd posts in this thread.

Uh, well ok... usually people post on the running topic of conversation, I assumed wrong guess >.>.
> 
I know it can be all done without Automatix.

As previously stated some find it very convenient at what ever stage.  For me, it's usually initial setup of a system.

Ok.
> 
Yes, I agree with you.  
Yay.
> 
I also think a whole lot of time & energy has been wasted on the topic of Automatix.  
Probably, but that's the nature of cafe topics... 

> Use it or don't, recommend it or don't, _who cares?_ 
Well, now that statement I don't like at all. We obviously have to care (else we'd not volunteer here answering questions). Apathy, ignorance and uncaring is what happens on Windows (generalizing, but lots of users I know fit this and don't care that they do) and we know how that goes (I certainly don't want that to happen to Ubuntu in order to expand it). Like I said before, caring and making informed choices and decisions (as a community and individual) is what makes Linux great (and at the same time bad when it splinters horribly).

> It works perfectly for some, & *apparently* has trashed other's systems, that's computing.  
Yup.

> As far as an ordained from above Ubuntu political stance regarding anything & everything to do with Automatix, that is a little complicated due to Arnie having a strong personality & having rubbed other personalities the wrong way.
Big understatement about "rubbing", from everything I seen Arnav brought it on himself overreacting and blowing up... then even making threats and on and on.

> Automatix is a storm in a teacup.

Yup, lots of things are like that though.

---

### Post by compiledkernel on 2007-07-25
> **aysiu said:**
> **Anti-Automatix FUD**:
It'll break your system. It'll break your system!

**Pro-Automatix FUD**:
It's either Automatix or compiling from source. We don't all want to compile from source or do things through the terminal.

Thats quite a brilliant analysis Ays. 

Again, Id be interested to hear what simplications occur between AX and the Official build. Just exactly what goes into the use of one over the other. Ive yet to hear that in this thread at all. 


Ax installs mp3 codec how? 
NonAx install for mp3 codec?

---

### Post by bodhi.zazen on 2007-07-25
> **ice60 said:**
> obiviously i haven't read everything that's been written about AX in the past, but from what i have read it seems the threads used to go like this -

someone says something rude about AX/Arnieboy, then Arnieboy gets side-tracked by that and replies, then everyone goes off slapping each other on the back saying how much they hate him.

it's good to see Arnieboy doesn't take the bait anymore. what we're left with is master baiters :lolflag:

> **loell said:**
> i too don't often understand in the past, why others would brag about his "attitude" towards certain individuals,
oh well whatever it is, keeping silent and not retaliating on these kinds of threads is certainly a sign of an improved and good attiude of arnieboy.

> **handy said:**
> As far as the attitudes ranging from the right wing extremes, of everyone should compile all software that is to be installed on a machine themselves, & mouses are evil! To the more common expectations of what ***other*** Linux user's are required to be able to do with the OS to meet someone else's personal standard!  That is just elitist rubbish.  

Use your computer anyway you like & off to the wrathful deities with other people's attitudes on the matter.

I think you are all missing the point of this thread. This thread is not a restriction of freedom, censureship, or even an opinion article by "the mods"

Have you noticed, the more experienced users tend to advise against Ax ? Why do you think that is ? 

Experienced users are weighing in with information about Ax.

1. It can cause serious problems. Many distro's, including Ubuntu and Mepis are moving away from Ax.

2. It is outdated as Ubuntu now contains equally easy to use tools.

3. Ax is a third party application and is not supported on these forums, irc, or Launchpad (the three pillars of Ubuntu support).

4. Ax has it's own forums for support.

Arnie has not been active on the forums for some time now. His past behavior has not characterized by restraint or maturity.

I would ask Ax fans to : 

1. Tone down the rhetoric. What do any of your posts have to do with the technical merits of Ax ?

2. If you advise Ax to inexperienced users, please warn them of possible system failures that may result, including loss of support via 
launchpad/irc, and future upgrades will likely not be possible if you install Ax.Failure to do so is , IMO, almost unethical.

3. Direct users where to go for support,

What I am saying is the Ubuntu Forums is NOT primarily the place for Ax support. No one here is banning third party applications, non-Ubuntu distros, advocating censureship, or restricting your freedom.

---

### Post by aysiu on 2007-07-25
I don't know about how Automatix's methods differ from official methods, as source code basically makes no sense to me.

By the way, I don't want to make this any more political than it already is, but someone has implied that the personality of a program's creator or lead developer should not have any influence on whether you use the program or not. I don't know if I fully agree with that assumption. If a program's creator is not likely to take criticism very well or isn't willing to cooperate with other developers, that has a direct effect on the program itself and its implementation and interaction with other programs, doesn't it?

Based on what I've seen Arnieboy post in the past and based on its current association with TechAlign, I wouldn't be surprised at all if Automatix started charging money for use (something like CNR) and/or got rewritten so as to be closed source. Pure speculation on my part, of course. Call it FUD if you will. It could be. But my point still remains that a creator and its software are directly related.

I happen to believe in Ubuntu and be confident about the direction its headed in, mainly because of what I've seen Mark Shuttleworth say and do. I don't have that same confidence in Kevin Carmony and Linspire, Steve Jobs and Mac OS X, or Bill Gates and Windows. I'm not saying Mark Shuttleworth can do no wrong, but software doesn't come out of *nowhere*. It comes out of its creator's vision and the developers' desires.

---

### Post by compiledkernel on 2007-07-25
it was my understanding for mp3 codec playback 

Automatix - Install Automatix , import your key or whatever, check codec or whatever in automatix then install. 

NonAutomatix - Open Add/Remove Programs , click on Other, check Ubuntu Restricted Extra , then click apply.

---

### Post by aysiu on 2007-07-25
> **compiledkernel said:**
> it was my understanding for mp3 codec playback 

Automatix - Install Automatix , import your key or whatever, check codec or whatever in automatix then install. 

NonAutomatix - Open Add/Remove Programs , click on Other, check Ubuntu Restricted Extra , then click apply.
Actually, the non-Automatix MP3 playback (for Totem, anyway... not necessarily for Rhythmbox yet) is even simpler. You just double-click on the MP3 and follow the prompts.

More details here:
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

---

### Post by handy on 2007-07-25
> **starcraft.man said:**
> Uh, well ok... usually people post on the running topic of conversation, I assumed wrong guess >.>.


As I said, I've read a LOT of Automatix posts in the past.  That said, I thought I wouldn't have missed much by not reading many of the previous 100+, at the time.

> **starcraft.man said:**
> 
Well, now that statement I don't like at all. We obviously have to care (else we'd not volunteer here answering questions). Apathy, ignorance and uncaring is what happens on Windows (generalizing, but lots of users I know fit this and don't care that they do) and we know how that goes (I certainly don't want that to happen to Ubuntu in order to expand it). Like I said before, caring and making informed choices and decisions (as a community and individual) is what makes Linux great (and at the same time bad when it splinters horribly).

Too much energy going in here IMHO.

If & when Automatix is unsatisfactory or unneeded no one will use it.  Simple.

> **starcraft.man said:**
> 
Big understatement about "rubbing", from everything I seen Arnav brought it on himself overreacting and blowing up... then even making threats and on and on. 

Some of us don't handle stress very well sometimes, or all the time...

[I]**[Edit:]**  In relation to personalities & software; it still comes down to whether the user is happy with the job that the software does. If your best friend writes bad software you will be reluctant to use it.

Automatix will become extinct like the rest of us![/I] :-)

---

### Post by loell on 2007-07-25
> **bodhi.zazen said:**
> I think you are all missing the point of this thread. This thread is not a restriction of freedom, censureship, or even an opinion article by "the mods".

really? and how about those similar automatix debate threads that were closed in the past?
what is the significance of this thread over others? is it because the OP is the current Admin and the outgoing owner of ubuntuforums?

---

### Post by eentonig on 2007-07-25
I've used Automatix in the past. It broke my system (probably my fault anyway back then), reinstalled an used it again. I was happy.

The +1 release and after, I've never used it again. In the first upgrade, I could have still used it, but I got familiar enough to search and do it myself the hard way. Basically because I felt Ax kept me dumb. And I'd rather search and learn how to do it the way it was designed to be.

Every time I've installed afterward, I never felt there was a need for Ax. Ubuntu is already taking me by the hand to make sure I get around. If I type a command in te CLI that's not installed, it offer me how to install it. If I play an mp3 without the codecs, it directs me to the restricted drivers, ...

If there were things why I would still recommend Ax to others, it wouldn't hold me back in proposing it. But at th same time, I would also file a bug or request at launchpad to solve that issue. Ubuntu tends to take very good care of it's users.

---

### Post by compiledkernel on 2007-07-25
> **loell said:**
> really? and how about those similar automatix debate threads that were closed in the past?
what is the significance of this thread over others? is it because the OP is the current Admin and the outgoing owner of ubuntuforums?

Well Loell, I havent really seen this thread -- unlike other automatix threads -- steer wildly out of control. Im still anxious like many users in this thread to hear the techinical merits that are so richly eluded to , but not touched. 

So rather than just saying I use it because it works...speak as to why? I dont think the nature of the OP has anything to do with the nature of the thread at all. 

So now continue with on with your technical analysis.

---

### Post by loell on 2007-07-25
ah i see :)  on to technical and usability side then , perhaps with these, ubuntu can somehow improve
its add/remove applications.



isn't it in add/remove you'll have to search codec to install those ugly codecs?
while in automatix, you are just presented with codecs that users are most likely to install.

---

### Post by sw1995 on 2007-07-25
I wonder, what would happen to Ubuntu if Automatix were to suddenly vanish? Is there any way of accurately assessing the correlation between the success of Ubuntu and the ease/familiarity of a program like Automatix.

I am certain this response is missing the boat on a million different angles, I just wonder: how many users would Ubuntu lose if Automatix vanished? Do the pros outweigh the cons? What am I overlooking here? :)

---

### Post by handy on 2007-07-25
> **sw1995 said:**
> I wonder, what would happen to Ubuntu if Automatix were to suddenly vanish? Is there any way of accurately assessing the correlation between the success of Ubuntu and the ease/familiarity of a program like Automatix.

I am certain this response is missing the boat on a million different angles, I just wonder: how many users would Ubuntu lose if Automatix vanished? Do the pros outweigh the cons? What am I overlooking here? :)

It would make no difference to me now, if Automatix did not exist.  In my early days with Breezy it really did make my life easier, removing some of the stress of learning a completely new OS (Linux).  I would not have given up if Automatix was not there to help me.  I remain grateful for the assistance I received from that piece of software.

I know how efficient the command line is, & I used to do a lot of scripting on the Amiga, & some in DOS.  After some years of windows, for me the need to script virtually disappearing.  So when you are a new user in Linux, there are a LOT of changes hitting you all at once, so many that the learning curve loops the loop!  Any software that can ease that burden on the new ex windows user is of great advantage, in both keeping that user from going back to windows, & in alleviating the stress.

Some say that Automatix & the like, keeps people dumb.  I say we stay as dumb as we want to.  

*The Linux community is being continually diluted with refugees from the windows world.  Which makes the following statement: **That most people who use their computer don't want to be involved in the technical stuff, they just want it to work as easily as possible & to keep on working without causing any technical problems**, more relevant to Linux & Ubuntu every day.*

---

### Post by panas on 2007-07-25
We are  common users with an extra bit of knowledge.
When we give our novice friends an virus free system for their 
use we dont want to spend hours on a setup.
If thats the case they could always go to a  store and buy an antivirus .

If they choose to learn more on a piece of hardware or software that are using, is
their choice.
And as you point to us , the documentation exist, and its well done.

It seems that the preachers here wont everybody to install
a system for breakfast.
If not they must die.

Also as stated before in this forum, witch is not a Ubuntu core piece, the team seems to 
has an extra time for antiautomatix statements.
For as is just a tool for less spending time , for you is another battle;
Is not the linux land full of such fullish battles;
Is that maybe the source code for the development;

##
How many systems did you installed this morning ;

;=? for us the greeks

---

### Post by PartisanEntity on 2007-07-25
I too am of the opinion that Automatix is no longer needed.

When I was new to Ubuntu, namely while using Dapper, I did use Automatix in order to install codecs, drivers and certain applications. But as I became more and more experienced there really was no longer a need for Automatix.

Ubuntu has IMO progressed beyond the need for such scripts. Most new users use it because of its reputation, amongst novices, that it makes installing applications and drivers easier when in fact doing so through a vanilla installation of Ubuntu is just as easy today.

---

### Post by Arwen on 2007-07-25
:-( too late I've seen this thread,I've downloaded  too much stuff by automatix2 but the only wieird thing that happens is mozilla(not downloaded by automatix) suddenly closing when I open new tab and write the http address.It's useful for codecsand players but  I've get used to sudo commands.Thank source nothing has crashed till now :-)

---

### Post by steven8 on 2007-07-25
I've used automatix since day one.  Great tool.  I love it.  No problems.

---

### Post by compiledkernel on 2007-07-25
> **loell said:**
> isn't it in add/remove you'll have to search codec to install those ugly codecs?
while in automatix, you are just presented with codecs that users are most likely to install.

By the first rationale, this assumes you already have Automatix installed. Its installation requires some level of terminal knowledge, weve already stated that once. I thought the object was to be easier on the user. Asking a user to open up a terminal who is already afraid of it to install something isnt much easier in my opinion. 

By the second rationale, we assume then that if you have ubuntu installed, and you open up firefox for the first time, you will be guided here -- [https://help.ubuntu.com/](https://help.ubuntu.com/) , which supplies all the needed information to get you going, this is not limited to and includes installing all the codecs -- 

here - [https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

and 

here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just a few short clicks away. The official documentation that is supported is right there. This also includes and is not limited to 

[https://help.ubuntu.com/7.04/internet/C/web-plugins.html](https://help.ubuntu.com/7.04/internet/C/web-plugins.html) - java , flash, etc. 

[https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html) - how install things properly. 

and for the tech savy 

[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/) - How to use the Command line.

---

### Post by handy on 2007-07-25
I think your ***Why I don't recommend Automatix*** is very fair & even handed ***compiledkernel***.

Many of us do just have an Automatix habit these days.

---

### Post by ice60 on 2007-07-25
> **bodhi.zazen said:**
> I think you are all missing the point of this thread. This thread is not a restriction of freedom, censureship, or even an opinion article by "the mods"
personally i don't care how good/bad Automatix is. my point was more to do with posts like this -
> **jarvis13 said:**
> 
Not only is Automatix horrible, but Arnieboy is a complete douche. 
Check out what he has to say in that digg article from when Automatix for Feisty was released. Guy is a complete idiot.
i just think it's disgusting if mods have read that and can't see anything wrong with it.

i don't care what anyone thinks about anyone else, but i think threads about Automatix should be closely moderated and comments like the above taken out straight away. it just makes the mods look bad i think.

---

### Post by Adamant1988 on 2007-07-25
> **ice60 said:**
> personally i don't care how good/bad Automatix is. my point was more to do with posts like this -

i just think it's disgusting if mods have read that and can't see anything wrong with it.

i don't care what anyone thinks about anyone else, but i think threads about Automatix should be closely moderated and comments like the above taken out straight away. it just makes the mods look bad i think.

I don't see anything wrong with that post either, in fact, I would call it an understatement.

---

### Post by Frak on 2007-07-25
> **Adamant1988 said:**
> I don't see anything wrong with that post either, in fact, I would call it an understatement.
He called Arnieboy a douche. That has nothing to do with Automatix.

---

### Post by Adamant1988 on 2007-07-25
> **Frak said:**
> He called Arnieboy a douche. That has nothing to do with Automatix.

It has everything to do with Automatix.  Arnav (arnieboy) and his creation have been at the heart of a lot of problems in the Ubuntu community.  He has insulted the members of this community, he has deliberately tried to hurt them and lied to cover it up when that failed, and has been the catalyst for a number of big issues in the community.  Yet, the only reason anyone in this world knows or cares that Arnav exists is because of Automatix.

---

### Post by ice60 on 2007-07-25
all i'm saying is a forum should have standards, and it should work both ways - if arnieboy says something out-of-line then that should be moderated too, but he's not here and hasn't said anything in this thread.

i wouldn't want to be a mod because i think it can be a thankless task, but i really think it's about time something was done about this, it can't carry on like this, or can it??

i'm not on either 'side' i just think the mods should come up with a decision about threads to do with Automatix - if a thread starts to get too emotive it should be closed. 

i'll leave you to it, i've said what i wanted to say now.

---

### Post by Frak on 2007-07-25
> **ice60 said:**
> all i'm saying is a forum should have standards, and it should work both ways - if arnieboy says something out-of-line then that should be moderated too, but he's not here and hasn't said anything in this thread.

i wouldn't want to be a mod because i think it can be a thankless task, but i really think it's about time something was done about this, it can't carry on like this, or can it??

i'm not on either 'side' i just think the mods should come up with a decision about threads to do with Automatix - if a thread starts to get too emotive it should be closed. 

i'll leave you to it, i've said what i wanted to say now.
I agree, unless it was stated in the beggining of the thread, leave your problems at home.

---

### Post by bodhi.zazen on 2007-07-25
> **ice60 said:**
> all i'm saying is a forum should have standards, and it should work both ways - if arnieboy says something out-of-line then that should be moderated too, but he's not here and hasn't said anything in this thread.

i wouldn't want to be a mod because i think it can be a thankless task, but i really think it's about time something was done about this, it can't carry on like this, or can it??

i'm not on either 'side' i just think the mods should come up with a decision about threads to do with Automatix - if a thread starts to get too emotive it should be closed. 

i'll leave you to it, i've said what i wanted to say now.

I agree with the need to be even handed. In reviewing the post in question, it is inappropriate.

I will rectify that, but I would also remind you that as a member of the community, if you find a post inappropriate, please report it so it may be reviewed ;)

In terms of even handedness, I have given infractions to both sides of the Ax argument in equal numbers.

---

### Post by bodhi.zazen on 2007-07-25
> **sw1995 said:**
> I wonder, what would happen to Ubuntu if Automatix were to suddenly vanish? Is there any way of accurately assessing the correlation between the success of Ubuntu and the ease/familiarity of a program like Automatix.

I am certain this response is missing the boat on a million different angles, I just wonder: how many users would Ubuntu lose if Automatix vanished? Do the pros outweigh the cons? What am I overlooking here? :)

I do not get it. All I am advocating is full disclosure of the downside of Ax. I do not understand how full disclosure translates into restriction of freedom, banning, or censoreship. Are you saying that the problems with Ax so severe that full disclosure is not reasonable because it would somehow unfairly bias new users ? If Ax were such a good product why then is full disclosure so threatening?

Furthermore I am confident that if Ax were to "suddenly vanish" it would not be detrimental to Ubuntu. IMO Ubuntu has tools that are equally user friendly. Sure there is a learning curve with any new OS or application, but I do not think it is any more difficult to learn/use Syanptic or Add//Remove Programs then Ax.

Even better, why not teach/learn to use Ubuntu the "right way" from day 1 ?

---

### Post by aysiu on 2007-07-25
I stand by my earlier statement that Automatix is the best choice for only a few obscure situations. Most users who can't be bothered with installing things would be better off with a distribution that includes those things already: Linux Mint, Mepis, PCLinuxOS. And other users can use Ubuntu's built-in tools to easily install the necessary codecs and proprietary software.

Imagine if this were the case: Microsoft releases two versions of Windows. One version of Windows is as it is now. It includes Wordpad, MS Paint, and no DVD playback. (In this analogy, this would be Ubuntu.) Another, for the same price, included MS Office, Photoshop, and PowerDVD. (In this analogy, this would be Linux Mint.) Now, someone releases a script that installs MS Office, Photoshop, and PowerDVD for you. (In this analogy, this would be Automatix.) Why would you use that script? It's easy enough to install those things by yourself if you have the disks. And if you don't want to bother with that, just get the version of Windows that already includes those things.

It's about informed choice and picking the best option. If people know what the best options are for their situations and still pick the worst option, then they're entitled to that. But people shouldn't give the impression that the worst option is the best option.

---

### Post by compiledkernel on 2007-07-25
[quote=bodhi.zazen]I do not get it. All I am advocating is full disclosure of the downside of Ax. I do not understand how full disclosure translates into restriction of freedom, banning, or censoreship. Are you saying that the problems with Ax so severe that full disclosure is not reasonable because it would somehow unfairly bias new users ? If Ax were such a good product why then is full disclosure so threatening?[/quote]

Im fairly certain this is a question that has not been asked once, but been asked hundreds of times. Where no positive discussion was bred from it. The owner of the project professes to entertain logical technical discussions about the application, yet I have yet to see anything to that affect (save actually supporting the application here, which for all intents that I am aware of has ceased). Full disclosure, much like proof of the fantastic 2 million users, have shown to be a fools gold search -- no evidence has been shown to prove either of these statements.  Full Disclosure surely never happened in the Automatix-NG/EasyBreezy fiasco for which Venkat aka Robotgeek is most famous for. I doubt seriously it would happen here, despite the obvious benefits of doing so.

To my knowledge the Techboard -- [http://www.ubuntu.com/community/processes/techboard](http://www.ubuntu.com/community/processes/techboard) -- has never approved Automatix code for integration or common use. The support team doesnt supply a nessecary support mechanism for supporting Automatix as a whole on any of its avenues (save the forum, where the Automatix Devs refuse to support the application even now). The one place from within which one might derive such support -- Launchpad -- is not used by the automatix team, nor do they desire to do so. 
The forums possess an official stance on the support of automatix , modified to allow Arnieboy to support the application here, something that has stopped happeing.  Tha mailing lists , populated by a variety of devs, users, and helpers, are virtually bereft of any support for the application. Mere mention of the application in the #ubuntu irc channel (the official support channel for Ubuntu users) will breed a variety of reactions all negative in nature, most supporters there citing official means over using 3rd party applications like automatix (Seveas is the man, but hes not very forgiving to AX users). Contact Global Services Support , and if you have a contract with them, mentioning Automatix will breed the immediate removal of the application and then further support for your issues.  Based on all these facts , its exhaustive to get support for an application that for all intents is so closed minded by its developers, save going over to getautomatix.com to do so.  If even one official source of documentation attempted to successfully support automatix that would probably give some level of legitimacy to the application.

Regardless, Full Disclosure, by all of my experiences - Not ever going to happen.

Referenced links to content 
[http://help.ubuntu.com/](http://help.ubuntu.com/) - Official Support documentation
[http://ubuntuforums.org/announcement.php?f=13](http://ubuntuforums.org/announcement.php?f=13) - Forums stance on Automatix 
[https://answers.launchpad.net/launchpad/+question/4347](https://answers.launchpad.net/launchpad/+question/4347) - Removal request of Automatix by Arnav. 
[https://answers.launchpad.net/ubuntu/+question/10138](https://answers.launchpad.net/ubuntu/+question/10138) - Automatix support request 
[https://answers.launchpad.net/ubuntu/+question/9702](https://answers.launchpad.net/ubuntu/+question/9702) - Automatix support request 
[http://www.ubuntu.com/support/paid](http://www.ubuntu.com/support/paid) - Global services
[https://lists.ubuntu.com/archives/ubuntu-users/](https://lists.ubuntu.com/archives/ubuntu-users/) - Ubuntu-users mailing list

---

### Post by loell on 2007-07-25
> **compiledkernel said:**
> By the first rationale, this assumes you already have Automatix installed. Its installation requires some level of terminal knowledge, weve already stated that once. I thought the object was to be easier on the user. Asking a user to open up a terminal who is already afraid of it to install something isnt much easier in my opinion. 

By the second rationale, we assume then that if you have ubuntu installed, and you open up firefox for the first time, you will be guided here -- [https://help.ubuntu.com/](https://help.ubuntu.com/) , which supplies all the needed information to get you going, this is not limited to and includes installing all the codecs -- 

here - [https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html](https://help.ubuntu.com/7.04/musicvideophotos/C/codecs.html)

and 

here - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Just a few short clicks away. The official documentation that is supported is right there. This also includes and is not limited to 

[https://help.ubuntu.com/7.04/internet/C/web-plugins.html](https://help.ubuntu.com/7.04/internet/C/web-plugins.html) - java , flash, etc. 

[https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html) - how install things properly. 

and for the tech savy 

[https://help.ubuntu.com/7.04/basic-commands/C/](https://help.ubuntu.com/7.04/basic-commands/C/) - How to use the Command line.

true, this assumes that automatix is installed and requires some knowledge of the terminal.
obviously in this part, automatix is not in the advantage as it is not installed by default.

but  i would like to bring the argument in the actual installation or the choosing of the users of sets of programs that they  would like to install,

in

Add/remove applications :  search --> present (a large set) -->  choose to install


while in

Automatix: present( subset) --> choose to install



on a side-topic-- if we would like to continue on a technical and usability discussion shouldn't we atleast change the thread title? imho at some level, the thread title is a flame bait.

---

### Post by compiledkernel on 2007-07-25
> **loell said:**
> true, this assumes that automatix is installed and requires some knowledge of the terminal.
obviously in this part, automatix is not in the advantage as it is not installed by default.
but  i would like to bring the argument in the actual installation or the choosing of the users of sets of programs that they  would like to install,
in
Add/remove applications :  search --> present (a large set) -->  choose to install

while in

Automatix: present( subset) --> choose to install
on a side-topic-- if we would like to continue on a technical and usability discussion shouldn't we atleast change the thread title? imho at some level, the thread title is a flame bait.

if you examine the two interfaces, really I see a stripped down version of gnome-app-install ,and then I see gnome-app-install itself. I honestly see little difference between the two, save that Gnome-app-install is actually more featureful that automatix2 is. 

I tend to believe that the latter, gnome-app-install, is not only more featureful, but more robust. But I also find the only difference between the two is that searching for apps in Gnome-app-install MIGHT make the process last a tiny bit longer, but so fractionally, that I think your spliting hairs on ease of use. An example would be a simple search in gnome-app-install for mp3 breeds Ubuntu Restricted Extras as the Third choice in the list after the search is done. So technically you havent really provided much difference to a user, that would be an indicator of greater ease for using Automatix. Actually using automatix is still harder, you have to get it installed.

---

### Post by loell on 2007-07-25
uhmm, i'm retracting to my prevoius statement that automatix requires command line knowledge, as it is provided as deb package allready.  ;)

---

### Post by compiledkernel on 2007-07-25
[http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Installing_Automatix2_on_.28K.2CX.29Ubuntu_7.04_i386.2CAMD64_.28Feisty.29)

Still requires you to add keys from a terminal. 

try again loell.

---

### Post by Frak on 2007-07-25
I've never since Edgy Eft had to add keys from the terminal. It done it automatically.

---

### Post by loell on 2007-07-25
i'm actually installing it now, just for the sake of comparative discussion  :)

nope it does not require you to add keys to the terminal.

the one that you are referring to installing automatix via APT.

most users are  just downloading the deb package.

---

### Post by compiledkernel on 2007-07-25
*retracted*

---

### Post by loell on 2007-07-25
gnome-app-install is certainly more robust than automatix , and i'd have to agree with that.

ok, back to usabiltiy comparison.

consider the attach sreenshot. in gnome-app-install the internet utilities can be found all in the **Internet** section its verry cluttery in my view, while in automatix it is divided into four popular sections (email clients, chat clients, file sharing, web browser). each section is only filled with a small  popular subset which users are likely to install.

---

### Post by Frak on 2007-07-25
> **loell said:**
> gnome-app-install is certainly more robust than automatix , and i'd have to agree with that.

ok, back to usabiltiy comparison.

consider the attach sreenshot. in gnome-app-install the internet utilities can be found all in the **Internet** section its verry cluttery in my view, while in automatix it is divided into four popular sections (email clients, chat clients, file sharing, web browser). each section is only filled with a small  popular subset which users are likely to install.
I've started using that just know because I was compiling Compiz Fusion when I wanted to listen to my music. I then decided Add/Remove would be fastest to install codecs, to my suprise I found the Restricted Formats package. Much easier.

---

### Post by loell on 2007-07-25
> **Frak said:**
> I've started using that just know because I was compiling Compiz Fusion when I wanted to listen to my music. I then decided Add/Remove would be fastest to install codecs, to my suprise I found the Restricted Formats package. Much easier.

interesting, how did you find and install it? can you post your exact steps? just for comparative purposes.

---

### Post by compiledkernel on 2007-07-26
> **Frak said:**
> I've started using that just know because I was compiling Compiz Fusion when I wanted to listen to my music. I then decided Add/Remove would be fastest to install codecs, to my suprise I found the Restricted Formats package. Much easier.

do tell on your steps here.

---

### Post by Frak on 2007-07-26
Applications->Add/Remove->Show:All Available Applications->Other(on left panel)->Ubuntu Restricted Extras
It may be there because I included the Medibuntu Repos from the source o matic, but thats where I found them. :)

---

### Post by loell on 2007-07-26
if i remember it correctly, i too have installed the restricted package, despite this, the gstreamer plugin of for aac ,xvid,  and mpeg is not installed.

---

### Post by Frak on 2007-07-26
Of course the other method is to try to play the file, then it will search and install the correct codecs.

---

### Post by wersdaluv on 2007-07-26
"automatix sucks" is among the most searched keywords in the Ubuntu Forums.

see the screenshot

---

### Post by compiledkernel on 2007-07-26
I believe thats already been estalished, werdsaluv.

---

### Post by richbarna on 2007-07-26
> **compiledkernel said:**
> I believe thats already been estalished, werdsaluv.

It's a surprise that the word compiledkernel isn't second, as you are always a main player in the anti-ax threads.

I thought all this had ended here on Ubuntu Forums, obviously somebody still has a major problem.

All these anti-ax threads do, is to show the same people over and over repeating the same old tired rubbish. Staff and members. IU wonder when Aysiu is going to merge them all into a "mega-thread".

Why don't you all just treat ax as you would KDE vs Gnome. Some people like it some don't, for some it works, for others it breaks and be done with it.

---

### Post by frodon on 2007-07-26
> **richbarna said:**
> Why don't you all just treat ax as you would KDE vs Gnome. Some people like it some don't, for some it works, for others it breaks and be done with it.To be honest, i think it's different in the way that breaking ubuntu installs damage the ubuntu reputation at the end so it can't fall down in the category you described.

---

### Post by compiledkernel on 2007-07-26
> **richbarna said:**
> It's a surprise that the word compiledkernel isn't second, as you are always a main player in the anti-ax threads.

I thought all this had ended here on Ubuntu Forums, obviously somebody still has a major problem.

All these anti-ax threads do, is to show the same people over and over repeating the same old tired rubbish. Staff and members. IU wonder when Aysiu is going to merge them all into a "mega-thread".

Why don't you all just treat ax as you would KDE vs Gnome. Some people like it some don't, for some it works, for others it breaks and be done with it.

Attempting to carry on a technical discussion richbarna, please try to stay on that track, and steer away from emotional responses.

---

### Post by rajeev1204 on 2007-07-26
> **richbarna said:**
> It's a surprise that the word compiledkernel isn't second, as you are always a main player in the anti-ax threads.

I thought all this had ended here on Ubuntu Forums, obviously somebody still has a major problem.

All these anti-ax threads do, is to show the same people over and over repeating the same old tired rubbish. Staff and members. IU wonder when Aysiu is going to merge them all into a "mega-thread".

Why don't you all just treat ax as you would KDE vs Gnome. Some people like it some don't, for some it works, for others it breaks and be done with it.


.

---

### Post by bodhi.zazen on 2007-07-26
> **richbarna said:**
> It's a surprise that the word compiledkernel isn't second, as you are always a main player in the anti-ax threads.

I thought all this had ended here on Ubuntu Forums, obviously somebody still has a major problem.

All these anti-ax threads do, is to show the same people over and over repeating the same old tired rubbish. Staff and members. IU wonder when Aysiu is going to merge them all into a "mega-thread".

Why don't you all just treat ax as you would KDE vs Gnome. Some people like it some don't, for some it works, for others it breaks and be done with it.

> **rajeev1204 said:**
> I AGREE richbarna .

Technical discussion huh good excuse  .

+1 compiledkernel

richbarna and rajeev if you have something to add regarding the technical merits of Ax I am all ears.

---

### Post by rajeev1204 on 2007-07-26
Hmm

Well the point i would like to make is ...  most probably iam wrong or u  will pull me down whatever

Some issues you staff have and/or had with the creator of the program seems to hugely overshadow the merits of the program like automatix ( Of course with feisty that may be redundant now ) .

Ask any user who has benefited from AX and iam sure he will hate reading these threads .

As far as the technical discussions are concerned , the staff has made it pretty clear through their signatures and/or sticky what they think about AUTOMATIX . 

So do u have to keep repeating it all the time ?

We got the point already  . 

And now so that u dont get angry here is a smiley :)

---

### Post by compiledkernel on 2007-07-26
> **rajeev1204 said:**
> Hmm

Well the point i would like to make is ...  most probably iam wrong or u  will pull me down whatever

Some issues you staff have and/or had with the creator of the program seems to hugely overshadow the merits of the program like automatix ( Of course with feisty that may be redundant now ) .

Ask any user who has benefited from AX and iam sure he will hate reading these threads .

As far as the technical discussions are concerned , the staff has made it pretty clear through their signatures and/or sticky what they think about AUTOMATIX . 

So do u have to keep repeating it all the time ?

We got the point already  . 

And now so that u dont get angry here is a smiley :)

Well said Rajeev. 

But we are still trying to continue the technical discussion.

---

### Post by Foxmike on 2007-07-26
Ì have not seen the Ax source code, and I believe I wouldn't understand it yet I am not programmer.  I wonder, however, if there is a clear distinction between using that software and adding 3rd party repositories directly to the sources.list file.
 
Technically, applications installed from those 3rd partiy repos can break and upgrade, right?

---

### Post by ice60 on 2007-07-26
> **aysiu said:**
> 

Imagine if this were the case: Microsoft releases two versions of Windows. One version of Windows is as it is now. It includes Wordpad, MS Paint, and no DVD playback. (In this analogy, this would be Ubuntu.) Another, for the same price, included MS Office, Photoshop, and PowerDVD. (In this analogy, this would be Linux Mint.) Now, someone releases a script that installs MS Office, Photoshop, and PowerDVD for you. (In this analogy, this would be Automatix.) Why would you use that script? It's easy enough to install those things by yourself if you have the disks. And if you don't want to bother with that, just get the version of Windows that already includes those things.

It's about informed choice and picking the best option. If people know what the best options are for their situations and still pick the worst option, then they're entitled to that. But people shouldn't give the impression that the worst option is the best option.
dell doesn't sell mint and noobs haven't heard of it. there's a need for AX, people use it and people need/want support for it, it's pretty simple.

---

### Post by compiledkernel on 2007-07-26
> **Foxmike said:**
> Ì have not seen the Ax source code, and I believe I wouldn't understand it yet I am not programmer.  I wonder, however, if there is a clear distinction between using that software and adding 3rd party repositories directly to the sources.list file.
 
Technically, applications installed from those 3rd partiy repos can break and upgrade, right?

That has been a consistent fact in the past. A variety of 3rd party repositories (that fall outside of Universe and Multiverse) have been used in the past, only to cause package breakage, though not nessecary system breakage. 

Marillat's (sp?)  repos come to mind there. 

I assume that AX does source installs for software that doesnt appear in any repo other than a 3rd party one?

[quote=ice60]dell doesn't sell mint and noobs haven't heard of it. there's a need for AX, people use it and people need/want support for it, it's pretty simple.[/quote] 

Not part of the "technical" discussion ice, stay on track.

---

### Post by Foxmike on 2007-07-26
The reason I am asking is because I often see suggestion to add to sources.list some 3rd party repos as Trevino's, or other.  There is also that new getdeb.net website out there porposing do download .deb files to be installed.  What about those?  Technically, some 3rd repos can be considered as "clean", but there is always a risk, I guess.  Should those suggestions be considered the same way Ax is considered, strictly technically speaking?

---

### Post by ice60 on 2007-07-26
i really think someone like mark shuttleworth should see this thread and find out if he's proud of this kind of behavior.

compiledkernel, what's your problem? are you ok, or are you ill or something?

---

### Post by richbarna on 2007-07-26
> **rajeev1204 said:**
> Hmm

Well the point i would like to make is ...  most probably iam wrong or u  will pull me down whatever

Some issues you staff have and/or had with the creator of the program seems to hugely overshadow the merits of the program like automatix ( Of course with feisty that may be redundant now ) .

Ask any user who has benefited from AX and iam sure he will hate reading these threads .

As far as the technical discussions are concerned , the staff has made it pretty clear through their signatures and/or sticky what they think about AUTOMATIX . 

So do u have to keep repeating it all the time ?

We got the point already  . 

And now so that u dont get angry here is a smiley :)

I agree (in a technical way), and here's my smiley :D

---

### Post by aysiu on 2007-07-26
> **ice60 said:**
> dell doesn't sell mint and noobs haven't heard of it. there's a need for AX, people use it and people need/want support for it, it's pretty simple.
I don't disagree. Read what I wrote.

An informed choice is the best choice. Not everyone has a Ubuntu Dell computer. If you have a *special* situation, Automatix *may* be the best choice for you. But it is not automatically the best choice for everyone or every newcomer to Ubuntu.

Generally speaking, people tend to be either pro-Automatix or anti-Automatix. I am neither. I believe Automatix is one of many options, and it is often not the best option.

---

### Post by richbarna on 2007-07-26
> **ice60 said:**
> i really think someone like mark shuttleworth should see this thread and find out if he's proud of this kind of behavior.

compiledkernel, what's your problem? are you ok, or are you ill or something?

and another :D

---

### Post by compiledkernel on 2007-07-26
One assumes that for stuff that Automatix installs that comes from an official repo (and I assume there are a few that fall into this category) this isnt an issue no. Anything that Automatix installs that comes from an official repo makes that aspect of Automatix Redudant and not needed. 

 But for things that do not appear in an official repo that in turn AX does install, this could be an issue. I suppose it goes hand in hand regardless of circumstance. If its 3rd party there is a risk of package breakage (and perhaps POSSIBLY system break in some cases, though not all). Source packages and non deb packages that Automatix might install could also create such an additional problem.

---

### Post by Foxmike on 2007-07-26
> **ice60 said:**
> dell doesn't sell mint and noobs haven't heard of it. there's a need for AX, people use it and people need/want support for it, it's pretty simple.
 
I think the "need" consideration is a subjective one, that differes from one's point of view to other's.
 
What if the "need" comes from the fact this is the only solution you know because you have been misinformed?  Or because you always felt you would need it, not knowing that in reality, you don't need it?
 
Need is a very hard thing to gauge IMHO.

---

### Post by ice60 on 2007-07-26
> **aysiu said:**
> I don't disagree. Read what I wrote.

An informed choice is the best choice. Not everyone has a Ubuntu Dell computer. If you have a *special* situation, Automatix *may* be the best choice for you. But it is not automatically the best choice for everyone or every newcomer to Ubuntu.

Generally speaking, people tend to be either pro-Automatix or anti-Automatix. I am neither. I believe Automatix is one of many options, and it is often not the best option.

> **Foxmike said:**
> I think the "need" consideration is a subjective one, that differes from one's point of view to other's.
 
What if the "need" comes from the fact this is the only solution you know because you have been misinformed?  Or because you always felt you would need it, not knowing that in reality, you don't need it?
 
Need is a very hard thing to gauge IMHO.
i'd like to answer :) but one of the mods has told me i shouldn't be talking about this so i'll keep quiet.

---

### Post by aysiu on 2007-07-26
> **Foxmike said:**
> I think the "need" consideration is a subjective one, that differes from one's point of view to other's.
 
What if the "need" comes from the fact this is the only solution you know because you have been misinformed?  Or because you always felt you would need it, not knowing that in reality, you don't need it?
 
Need is a very hard thing to gauge IMHO.
Or you "needed" it for Breezy, Dapper, and Edgy, and so you assume you still need it for Feisty and haven't given Feisty's easy codec installation, restricted-extras metapackage, and restricted drivers manager a chance.

---

### Post by matthew on 2007-07-26
> **ice60 said:**
> i really think someone like mark shuttleworth should see this thread and find out if he's proud of this kind of behavior.

compiledkernel, what's your problem? are you ok, or are you ill or something?Wow. That was a little much.

Compared to the developers and to people much closer to the top (such as anyone in #ubuntu or on the dev mailing lists) this conversation has been amazingly well balanced. I see nothing in compiledkernel's behavior that merits being chastized. So, if you want to contact Mark about the thread, please make sure to spell both of our names correctly, so he doesn't get confused about the person's identity with whom you disagree.

---

### Post by compiledkernel on 2007-07-26
Need vs Want. 

Need is defined classically by the psychological feature that arouses an organism to action toward a goal out of necessity. 

Want is defined as something desired, but not really necessity. 

How can need be determined here? 
I need <application here>, my ubuntu install will not boot or function without it. 

In most cases , audio codecs, video codecs, google earth, or other such related non repo applications are more wants than needs.

---

### Post by compiledkernel on 2007-07-26
> **aysiu said:**
> Or you "needed" it for Breezy, Dapper, and Edgy, and so you assume you still need it for Feisty and haven't given Feisty's easy codec installation, restricted-extras metapackage, and restricted drivers manager a chance.

Aggreed Aysiu.

---

### Post by Foxmike on 2007-07-26
> **aysiu said:**
> Or you "needed" it for Breezy, Dapper, and Edgy, and so you assume you still need it for Feisty and haven't given Feisty's easy codec installation, restricted-extras metapackage, and restricted drivers manager a chance.
Good point.
 
Back to technicalities, all that makes me think about how I personnaly manage my packages.  I wonder if there are other things I shouldn't do without knowing it, as
- Compile some packages from source a certain way (checkinstall or not)
- Download a .deb from getdeb.net (or any other "secure" source for isntance) and double-click-install it
- Other (ran out of idea right now)

---

### Post by compiledkernel on 2007-07-26
To a beginner 

- Compile from source -- Probably not going to happen, actually really not going to happen. 

- Download a deb from a trusted source -- Getdeb.net (big supporter of it myself), Trevino, Or other such non official repository or site containing such debs, Are they really trusted? Officially, No, likely not. Are they safe, they might be. 

- Use a 3rd party app -- Automatix, EasyBreezy (pka Automatix-NG), EasyUbuntu, Envy (video drivers only).  If you can get support for them, but there is a POSSIBILITY of package breakage or system breakage. 

- Use the official repositories -- Main, Universe, Multiverse, Backports, Security-update. Using Synaptic, Aptitude, apt-get, adept, Gnome-app-install to maintain the packages on your system. The safest way to achieve the proper ends.

---

### Post by aysiu on 2007-07-26
So is Multiverse considered an official repo? And does Automatix use Multiverse? I noticed that some people's Automatix-created /etc/apt/sources.list files contain an Automatix repository, too. What packages are in that repository?

---

### Post by compiledkernel on 2007-07-26
My understanding is that Multiverse is community supported. 

Im not sure if Automatix uses mverse or not. 

[http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/](http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/)
[http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/)

---

### Post by Foxmike on 2007-07-26
Ok.  Other than using any "helper" application/script/whatever, is there a proper suggested way to install a package that do not belong to main/universe/multiverse repositories?  Or is there a way anybody should stay away from?
I try to figure out in what cases Ax can really break a system, if it only automatises what a user would have to do manually (apt-get install <package-name>, adding 3rd repos to the sources.list, for ex.), and in what case it can be really relevant to use it, and to those cases, if there is a less risky way to achieve the job.

---

### Post by ice60 on 2007-07-26
> **matthew said:**
> Wow. That was a little much.

Compared to the developers and to people much closer to the top (such as anyone in #ubuntu or on the dev mailing lists) this conversation has been amazingly well balanced. I see nothing in compiledkernel's behavior that merits being chastized. So, if you want to contact Mark about the thread, please make sure to spell both of our names correctly, so he doesn't get confused about the person's identity with whom you disagree.
actually i was thinking earlier that this thread was a lot calmer then most about AX. but, in general threads about it are very immature. i'm not sure what you're on about with the spelling both names correctly :confused:

i don't think compiledkernel should be a mod, he's a bit unbalanced.

---

### Post by Foxmike on 2007-07-26
> **ice60 said:**
> actually i was thinking earlier that this thread was a lot calmer then most about AX. but, in general threads about it are very immature. i'm not sure what you're on about with the spelling both names correctly :confused:

i don't think compiledkernel should be a mod, he's a bit unbalanced.
I have revewed all the thread and I see nothing this personnal judgement can be based on.

---

### Post by matthew on 2007-07-26
> **ice60 said:**
> actually i was thinking earlier that this thread was a lot calmer then most about AX. but, in general threads about it are very immature. i'm not sure what you're on about with the spelling both names correctly :confused:

i don't think compiledkernel should be a mod, he's a bit unbalanced.My silly crack about spelling our names right was a goofy way to try and say, "I'm not really concerned if you or anyone else wants to name drop or report me/compiledkernel/anyone else. No one has done anything out of line here, and I'm sure enough on that point to be willing to have my name connected to the issue if you feel the need to raise it."

Calling a mod imbalanced is against the Forums Code of Conduct. That's twice you have directly insulted him. Stop. If you have an issue with what he says, refute it politely. If you have an issue with his behavior, take it to the Resolution Center.

---

### Post by bodhi.zazen on 2007-07-26
> **compiledkernel said:**
> To a beginner 

- Compile from source -- Probably not going to happen, actually really not going to happen. 

- Download a deb from a trusted source -- Getdeb.net (big supporter of it myself), Trevino, Or other such non official repository or site containing such debs, Are they really trusted? Officially, No, likely not. Are they safe, they might be. 

- Use a 3rd party app -- Automatix, EasyBreezy (pka Automatix-NG), EasyUbuntu, Envy (video drivers only).  If you can get support for them, but there is a POSSIBILITY of package breakage or system breakage. 

- Use the official repositories -- Main, Universe, Multiverse, Backports, Security-update. Using Synaptic, Aptitude, apt-get, adept, Gnome-app-install to maintain the packages on your system. The safest way to achieve the proper ends.

+1 to that as well \o/

The point is not *if* system breakage can occur, as it can and has happened with the official repos as well.

The point is where and how will you get support when breakage does occur. If you use Ax you will lose the support of the forms, Launchpad, and irc. No one here is claiming the ubuntu developers or repositories are error free, but what we are saying is that **if you have a problem we are here to help**.

[This link is insightful](https://www.redhat.com/archives/fedora-test-list/2006-February/msg01565.html) As it is an example, un-rleated to Ubuntu or Ax, that shows exactly the kind of technical problems (and how hard they can be to track) that occurs with third party apps and why they are not supported.

You see the point ? *There is the reason why people who provide technical support, like the mods here, irc, and launchpad will not support Ax.*

IMO the accusation that the staff is anti-Ax is inappropriate. We are raising the awareness of the technical downside(s) of Ax and the fact the newer versions of Ubuntu have supported tools and methods to accomplish the tasks the Ax was designed to solve with 5.04. Ubuntu has come a long way and Ax is both outdated and unnecessary.

The Ax supporters seem not to be able to provide technical merits supporting the use of Ax and play various emotional cards like freedom or censorship or "works for me". Well "works for me" is *not* a good reason to advise Ax without disclosing the potential risks.

Another way to express this to the Ax fans would be to turn the tables. Lets say you are charged with supporting Ax and you find, *after several hours*, that Ax fails due to a conflict with package Y that is not a part of Ax, not is it installed by Ax, and is not maintained by Ax, what would you advise ? And if you started getting multiple requests from additional Ax users all with conflicts arising from package Y ? I'll bet you would start sounding very much like the Ubuntu staff when discussing package Y, namely that it can cause problems, it is not supported by Ax, and you would refer users of package Y to the maintainers of package Y.

This is a very rational process and has nothing to do with freedom or censorship, it is how projects are maintained.

This process of rational system and package maintenance breaks down with the emotional and non-technical comments injected to the discussion of Ax, by *both fans and detractors*.

---

### Post by John.Michael.Kane on 2007-07-26
> **ice60 said:**
> actually i was thinking earlier that this thread was a lot calmer then most about AX. but, in general threads about it are very immature. i'm not sure what you're on about with the spelling both names correctly :confused:

i don't think compiledkernel should be a mod, he's a bit unbalanced.

One must remember it's very hard to tell one's tone from a forum post Vs real time communications.

With that said. I don't see anything wrong  with what was voiced by compiledkernel. He simply said what he felt about the program, As did everyone else in this thread..


Bottom line Automatix should be the absolute last resort for an end user, As for support. users of the program should be kindly redirected to their site for help.

---

### Post by richbarna on 2007-07-26
> **aysiu said:**
> 
Generally speaking, people tend to be either pro-Automatix or VERY anti-Automatix with a passion. I am neither. I believe Automatix is one of many options.

Ok, so I edited it a little, but only to express how I feel. Aysiu and I nearly agreed, so I completed the equasion.


Here's a few figures: [SIZE=-1]Google Search Results **1** - **100** of about [COLOR=Red]**1,070**[/COLOR] for **compiledkernel+automatix**.Quite a keen interest in Ubuntu users' welfare.


Just to keep the thread "technical" and..... so you don't get mad at  me,  ;)[/SIZE]

---

### Post by aysiu on 2007-07-26
You're right--we disagree on that point. I've seen people as insanely pro-Automatix as those who are insanely anti-Automatix. Automatix is not the cure for everything. It is also not the anti-Christ.

---

### Post by Foxmike on 2007-07-26
> **richbarna said:**
> Ok, so I edited it a little, but only to express how I feel. Aysiu and I nearly agreed, so I completed the equasion.


Here's a few figures: [SIZE=-1]Google Search Results **1** - **100** of about [COLOR=Red]**1,070**[/COLOR] for **compiledkernel+automatix**.Quite a keen interest in Ubuntu users' welfare.


Just to keep the thread "technical" and..... so you don't get mad at  me,  ;)[/SIZE]
Im wondering what's the interes of all that, tho.  I see none.  Any chance to keep going now?

---

### Post by richbarna on 2007-07-26
> **aysiu said:**
> Automatix is not the cure for everything. It is also not the anti-Christ.

I'll completely agree with you there, that is a great quote. Isn't everybody fed-up with these automatix good or bad therads now? It reminds me of the old KDE vs Gnome / Linux vs Windows threads of years gone by.

I know some people love these topics with a passion, but these threads eventually get boring once the flame/troll value wears off.

To be honest, everybody has now caught on that ubuntuforums is antiautomatix, doesn't that harm the forum's reputation ?

---

### Post by matthew on 2007-07-26
> **richbarna said:**
> I'll completely agree with you there, that is a great quote. Isn't everybody fed-up with these automatix good or bad therads now? It reminds me of the old KDE vs Gnome / Linux vs Windows threads of years gone by.
lol. You forgot vi vs. emacs.

I think we've covered the installation helper script, its benefits, and potential problems pretty well. Let's all move on.

---

### Post by bodhi.zazen on 2007-07-26
> **richbarna said:**
> I'll completely agree with you there, that is a great quote. Isn't everybody fed-up with these automatix good or bad therads now? It reminds me of the old KDE vs Gnome / Linux vs Windows threads of years gone by.

I know some people love these topics with a passion, but these threads eventually get boring once the flame/troll value wears off.

To be honest, everybody has now caught on that ubuntuforums is antiautomatix, doesn't that harm the forum's reputation ?

The Ubuntu forums is *not* antiautomatix. Ax users are directed to the Ax site for support as it is a third party app.

Individual mods have opinions one way or another, that is different as we are all entitled to our opinions.

The only ones who seem to feel the forums reputation has suffered are the Ax fanatics. Most users probably do not care and membership / usage of the forums seem unaffected either way, in fact, if anything, Ubuntu keeps growing so we must be doing something right ;)

---

### Post by Foxmike on 2007-07-26
> **richbarna said:**
> To be honest, everybody has now caught on that ubuntuforums is antiautomatix, doesn't that harm the forum's reputation ?
Is the forum anty-beryl?  Anti-compiz?  You should see those huge red warning to the how-tos.  I'm pretty sure that those who wrote these how-tos, if they could, they would have made the warnings flashing and bumping all around the screen to make sure they would catch the attention.  For example: "This is ALPHA software!!! If it breaks your computer, you keep both pieces!!!"

So, are the ubuntuforums.org considered anti-beryl???  I guess not.  Not anti-beryl and not anti-Ax.  The mods are just making clear something that is not obvious to some new Ubuntu users: Ax may break the system.  If it does, you got to keep both pieces.

---

### Post by forrestcupp on 2007-07-26
And that's why Compiz-Fusion is installed by default in Gutsy, huh?

I'd say they're probably more anti-AX than they are anti-Beryl.  There have been a lot of heated discussions about Automatix2 and not to many heated ones about Beryl/Compiz

---

### Post by aysiu on 2007-07-26
The discussion in the SocialDiscussion forums of this topic is a good one and relatively cool (i.e., not heated):
[automatix?](http://joindiscussion.com/computers-gadgets/5199-automatix.html)

---

### Post by compiledkernel on 2007-07-26
> **richbarna said:**
> Ok, so I edited it a little, but only to express how I feel. Aysiu and I nearly agreed, so I completed the equasion.


Here's a few figures: [SIZE=-1]Google Search Results **1** - **100** of about [COLOR=Red]**1,070**[/COLOR] for **compiledkernel+automatix**.Quite a keen interest in Ubuntu users' welfare.


Just to keep the thread "technical" and..... so you don't get mad at  me,  ;)[/SIZE]

Honestly RB, thats Red Herring. Has little or no bearing on a technical discussion 

richbarna+automatix - 786 results

Interestingly enough - "george bush"+automatix = 376 results, maybe he cares about the community too?

---

### Post by Foxmike on 2007-07-26
> **forrestcupp said:**
> And that's why Compiz-Fusion is installed by default in Gutsy, huh?

I'd say they're probably more anti-AX than they are anti-Beryl.  There have been a lot of heated discussions about Automatix2 and not to many heated ones about Beryl/Compiz
Heated discussions because of the software?  I remember some heated discussions over the "Compiz-Quinn VS Compiz" subject some time ago...

And those project were and still are clearly presented as "Use at your own risk" and "Alpha" ones.  It is not often the case of Automatix.  I think that is one of the reasons of this discussion.

---

### Post by starcraft.man on 2007-07-26
Wow 20 pages... Sorry, just wow. Nothing else to add, carry on.

*runs off to look at mobo specs*

---

### Post by loell on 2007-07-26
ok, back to the issue of ease...

with libdvdcss2 , automatix makes it a breeze to install, while you have add the medibuntu

**Third Party Repo** to install it. automatix is at the advantage in this area...

thoughts?

---

### Post by forrestcupp on 2007-07-26
> **Foxmike said:**
> Heated discussions because of the software?  I remember some heated discussions over the "Compiz-Quinn VS Compiz" subject some time ago...

And those project were and still are clearly presented as "Use at your own risk" and "Alpha" ones.  It is not often the case of Automatix.  I think that is one of the reasons of this discussion.

But those heated discussions are whether you should use Compiz or Beryl/Compiz-Quinn.  They weren't heated because people were saying you shouldn't use them at all.  Compiz is being pushed by Ubuntu because it is clear that the majority wants the eye candy (I'm sure that some of the outspoken minority would disagree).  It is pushed, but with warning.  

Automatix2 is flat out frowned upon in a vicious way.

---

### Post by loell on 2007-07-26
oh well, on second thought, i'll just have to create another thread,

i find the intentions of the stalves questionable, of its reluctance on changing an obvious flame bait thread title.

---

### Post by matthew on 2007-07-26
> **loell said:**
> oh well, on second thought, i'll just have to create another thread,

i find the intentions of the stalves questionable, of its reluctance on changing an obvious flame bait thread title.The thread title is taken directly from the digg.com thread that is linked in the first post. This thread started as a discussion of the digg.com one, a thread with a title I can only presume was intended to be ironic and amusing in its over the top mockery of modern day news headlines. Sorry you missed the humor in that.

Oh, off topic friendly fyi: the plural of staff is staff. It's one of those odd quirks in the English language that turn up from time to time.

---

### Post by aysiu on 2007-07-26
Isn't *staff* a singular noun that describes one or several people? *Staff members* can be plural, though.

---

### Post by matthew on 2007-07-26
aysiu: touche... "collective noun" would have been a better description.

---

### Post by matthinckley on 2007-07-26
> **forrestcupp said:**
> But those heated discussions are whether you should use Compiz or Beryl/Compiz-Quinn.  They weren't heated because people were saying you shouldn't use them at all.  Compiz is being pushed by Ubuntu because it is clear that the majority wants the eye candy (I'm sure that some of the outspoken minority would disagree).  It is pushed, but with warning.  

Automatix2 is flat out frowned upon in a vicious way.
If there were a different, supported way of doing the exact same thing that Beryl does without running the risk of breaking my system, I think Beryl would be frowned upon as well.

I don't think we should compare Ax to Beryl since there *is* a supported way of doing what Ax does.. there is no supported way to have a transparent cube.

---

### Post by handy on 2007-07-26
> **aysiu said:**
> I don't disagree. Read what I wrote.

An informed choice is the best choice. Not everyone has a Ubuntu Dell computer. If you have a *special* situation, Automatix *may* be the best choice for you. But it is not automatically the best choice for everyone or every newcomer to Ubuntu.

Generally speaking, people tend to be either pro-Automatix or anti-Automatix. I am neither. I believe Automatix is one of many options, and it is often not the best option.

+1

---

### Post by handy on 2007-07-26
Regarding sending people to Automatix forums for support, I copied the following from the getautomatix site:

*We strongly recommend that all users kindly direct Automatix related support questions to the   Automatix Forums   for highly efficient and professional handling. This will be for the benefit of Ubuntu and Automatix users themselves.*

---

### Post by Foxmike on 2007-07-26
> **matthinckley said:**
> If there were a different, supported way of doing the exact same thing that Beryl does without running the risk of breaking my system, I think Beryl would be frowned upon as well.

I don't think we should compare Ax to Beryl since there *is* a supported way of doing what Ax does.. there is no supported way to have a transparent cube.
+1. I completly agree with what you say.

 However, the comparisions stands for those reasons:
- There is a "stable" way of doing things (compiz) versus a new an "unstable" way of doing things (beryl)
- Both sides held/hold supporters that believe they get the only good way and are ready do defend their points an inflamable way (I'm sorry, native francophone here that has a lot of difficulty to make his point clear in english... it's late!:))
- One project derives from the other and the transition has not been smooth.

I guess we could continue to argue on that "side-topic" but it will not bring anything new so I suggest we just keep going with the main thread:).

Regards,
-FM

---

### Post by handy on 2007-07-26
If it helps anyone, the following was added by Automatix to my sources.list: 

[I]#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

#AUTOMATIX REPOS END[/I]

---

### Post by richbarna on 2007-07-27
> **compiledkernel said:**
> Honestly RB, thats Red Herring. Has little or no bearing on a technical discussion 

richbarna+automatix - 786 results

Interestingly enough - "george bush"+automatix = 376 results, maybe he cares about the community too?

Nope. Your name leads to the same sites; Digg and UF

I also tried spam+eggs+automatix and got a few as well, but in that and george bush + RichBarna+ automatix, they all lead to mailing lists, bloggs etc with a variety of topics.

And any way, I have recieved a warning for disagreeing with you....again ;)

As usual, nobody is allowed to defend automatix.

---

### Post by frodon on 2007-07-27
With all due respect, i think the last part of your post belongs to the resolution center and don't seem to add anything to the discussion. Would you please accept to use proper channels for such questions/remarks ?

Thank you

---

### Post by richbarna on 2007-07-27
> **frodon said:**
> With all due respect, i think the last part of your post belongs to the resolution center and don't seem to add anything to the discussion. Would you please accept to use proper channels for such questions/remarks ?

Thank you

Yeah, you are right, i'll edit it. I just wanted to show what everybody already knows (it's been said here, on bloggs, socialdiscussion, other forums) if you backup a-x or disagree with a certain staff member, you will get infraction points.

---

### Post by ubuntu-geek on 2007-07-27
I am going to close this thread now. Thanks to those of you who have made it a personal matter instead of a technical matter. Perhaps sometime in the future a more professional and detailed technical conversation can take place. Until then this thread is closed.

---

