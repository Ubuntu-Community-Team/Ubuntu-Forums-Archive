---
title: "New default applications, synaptic removed"
date: 2011-06-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-23
New meta-package "ubuntu-meta" brings some changes to the default setup.
Synaptic is removed
Deja-dup, libgail-common and qt-at-spi added

See here:
[https://launchpad.net/ubuntu/oneiric/+source/ubuntu-meta/1.231](https://launchpad.net/ubuntu/oneiric/+source/ubuntu-meta/1.231)

---

### Post by lucazade on 2011-06-23
I hope also gwibber will be wiped out from default install!

---

### Post by Framli on 2011-06-23
Give the incoming new UI a chance :p

---

### Post by lucazade on 2011-06-23
> **Framli said:**
> Give the incoming new UI a chance :p

Is it nice? Links?
However I don't judge it on the appearance, I haven't found it useful and it locks dependencies in indicator-me, which is annoying!

---

### Post by MacUntu on 2011-06-23
I can almost smell the complaints about the removal of synaptic. ;-)

---

### Post by lucazade on 2011-06-23
> **MacUntu said:**
> I can almost smell the complaints about the removal of synaptic. ;-)

more than smell!
people is moving to Arch because of synaptic removal... 
[http://www.webupd8.org/2011/06/synaptic-removed-from-ubuntu-1110-deja.html](http://www.webupd8.org/2011/06/synaptic-removed-from-ubuntu-1110-deja.html)

---

### Post by MacUntu on 2011-06-23
To be honest, I saw this facepalm coming. :P

---

### Post by tjeremiah on 2011-06-23
> **MacUntu said:**
> I can almost smell the complaints about the removal of synaptic. ;-)

the wolfs are coming.

---

### Post by akand074 on 2011-06-23
Well to be honest, I think the general user won't be using synaptic. People don't make any sense. I would still like synaptic on top of the software centre, so after installing 11.10 I'd just sudo apt-get it... defaults are such silly things to switch distros about. Though, I don't really understand Canonical's need to keep the size under 700MB. DVDs are both faster and cheaper than CDs. I always burn every release on a DVD.

---

### Post by donniezazen on 2011-06-23
Software center says bad package to my grand mother.

---

### Post by lucazade on 2011-06-23
> **soham_1207 said:**
> Software center says bad package to my grand mother.

well, some packages could be not packaged correctly, but this doesn't depend on package manager. 

If software center makes some checks before installing and warns you about possible issues in a package is a positive thing. 
Installing a .deb package was done in the past by gdebi and dpkg and not using synaptic.

---

### Post by Harry33 on 2011-06-23
Note that it is only the default setup or installation from where synaptic has been removed.
It will still be in repos.

---

### Post by lucazade on 2011-06-23
> **Harry33 said:**
> Note that it is only the default setup or installation from where synaptic has been removed.
It will still be in repos.

correct and just to be clear Synaptic is still considered the best and powerful package manager for advanced users 
but it is not in the target of non-tech users.

---

### Post by cariboo on 2011-06-23
We were warned that synaptic would be removed from the default install when the Software Center was introduced, but the reactionary users will probably claim they'll move to a different distro, or go back to Windows, just like they did when Gimp was removed from the default install.

---

### Post by chrisccoulson on 2011-06-24
Note, Synaptic is still actually on the CD, at least until apturl is removed (apturl depends on Synaptic, and ubufox depends on apturl, keeping it on the CD). It just isn't seeded by ubuntu-desktop anymore

---

### Post by beew on 2011-06-24
If they want to keep the desktop slim they should have removed the Software Centre instead.  Synaptic hardly requires a rocket scientist to be able to use it. Users are not that dumb.

---

### Post by lucazade on 2011-06-24
> **beew said:**
> If they want to keep the desktop slim they should have removed the Software Centre instead.  Synaptic hardly requires a rocket scientist to be able to use it. Users are not that dumb.

It is not about keeping the desktop slim, Beew.

It is about providing out of the box tools that do general tasks and cover common needs.

If you need an advanced tool to accomplish advanced tasks you're free to install it.

@chrisccoulson
thanks for pointing this out

---

### Post by cariboo on 2011-06-24
> **chrisccoulson said:**
> Note, Synaptic is still actually on the CD, at least until apturl is removed (apturl depends on Synaptic, and ubufox depends on apturl, keeping it on the CD). It just isn't seeded by ubuntu-desktop anymore

Apturl is one of those cool apps that very rarely gets used, we stress not clicking a link until you check it out, and apturl doesn't give any usable information. Most of the time we'll see a direct link to a package on [packages.ubuntu.com]("http://packages.ubuntu.com") before we see an apturl link. I think it could be removed, and no-one would notice it was gone.

---

### Post by beew on 2011-06-24
> **lucazade said:**
> It is not about keeping the desktop slim, Beew.

It is about providing out of the box tools that do general tasks and cover common needs.

If you need an advanced tool to accomplish advanced tasks you're free to install it.

@chrisccoulson
thanks for pointing this out

Yes I know I am free to install it. But IMO 

1) Synaptic is not difficult to use at all and it does a whole lot more, its removal reflects an attitude that I find it troubling, namely to regard the new users as super stupid. Most people who venture out of the comfort zone of Windows and Mac to give Linux a try would expect some learning curve and learning how to use Synaptic for the basic tasks that the SC does is really trivial (comparing to say navigating using Unity)

2) The software centre is just plain crappy and it provides bad user experience and this actually reflects badly on Ubuntu. It takes forever to start and when it start up it uses  ~ 100% cpu on some older machines and it takes forever to install softwares.  It is a bloatware that does little and certainly doesn't show new user Linux's strength.

3) As I said on another thread new users would likely look around for applications like media players to find whatever that best suit their need so the default doesn't really matter. But with system package tools they would likely use whatever just come by default.It is a pity that many new users would not be exposed to better alternatives like Synaptic and gdebi. 

4) I cannot see your point that the default aims at providing tools for common tasks and common needs. Since Synaptic does everything that the SC does (and much more)the common ground is covered, so it doesn't take anything away but it does it more efficiently. So how can something that does more (and cover the common ground more efficiently) contradict the goal of providing tools for common need? It doesn't make logical sense.

---

### Post by lucazade on 2011-06-24
> **beew said:**
> Yes I know I am free to install it. But IMO 

1) Synaptic is not difficult to use at all and it does a whole lot more, its removal reflects an attitude that I find it troubling, namely to regard the new users as super stupid. Most people who venture out of the comfort zone of Windows and Mac to give Linux a try would expect some learning curve and learning how to use Synaptic is really trivial (comparing to say navigating using Unity)

2) The software centre is just plain crappy and it provides bad user experience and this actually reflects badly on Ubuntu. It takes forever to start and when it start up it uses  ~ 100% cpu on some older machines and it takes forever to install softwares. 

3) As I said on another thread new users would likely to look around for applications like media players to find whatever that best suit their need so the default doesn't really matter but with system package tools they would likely to use whatever just come by defaul.It is a pity that many new users would not be exposed to better alternatives like Synaptic and gdebi. 

4) I cannot see your point that the default is aim at providing tools for common tasks and common needs. Since Synaptic does everything that the SC does (and much more)the common ground is covered, so it doesn't take anything away but it does it more efficiently. So how can something that does more (and cover the common ground more efficiently) contradict the goal of providing tools for common need? It doesn't make logical sense.

_synaptic is a great tool and you will never find anyone saying the opposite._

_No one said users are dumbs, only you pointed that out._

For the rest I've already explained you.

---

### Post by beew on 2011-06-24
> **lucazade said:**
> _synaptic is a great tool and you will never find anyone saying the opposite._

_No one said users are dumbs, only you pointed that out._

For the rest I've already explained you.

Explain what? Your purpose here seems to be just to spout the party line. Seeing that you said users should not have any input because only the devs know best (on the other thread) I can't really take you seriously.

---

### Post by lucazade on 2011-06-24
> **beew said:**
> Explain what? Your purpose here seems to be just to spout the party line. Seeing that you said users should not have any input because only the devs know best (on the other thread) I can't really take you seriously.

Explain my thoughts about it..
Beew stay calm!

---

### Post by VinDSL on 2011-06-24
Hrm...  That's odd!

I must have installed Synaptic, and didn't even realize it.  :(


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-24-jun-2011(2)(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-jun-2011(2).png")[/INDENT]


I *know* that I had to install Gimp tonight.

Anyway, Synaptic must have been easy to install, if I don't remember doing it.  LoL!

Oops!  Guess I'd better go pin those drivers... duh!  :D

---

### Post by VinDSL on 2011-06-24
> **beew said:**
> Synaptic hardly requires a rocket scientist to be able to use it. Users are not that dumb.
I swear...

I almost "marked" those drivers for upgrade, when I snapped the screenie - out of habit.

And, I had just rolled them back, 30 minutes ago, so I could install nvidia-current.  LoL!

I don't know about "dumb", but let's just say, things get a little dicey after midnight.

It happens to the best of us, no?!?!?  ;)

---

### Post by jerrylamos on 2011-06-24
> **akand074 said:**
> Well to be honest, I think the general user won't be using synaptic. 

Flame on!

Synaptic for Samba.  This general public uses Synaptic immediately after install, for example Samba synaptic so I can share files with my wife on our local net, and for my other test pc, print on the Windows printer, ...

Synaptic for Flashplugin is another.  I never do games.  I always do internet videos on BBC, ABC, NY Times, Huffington Post, Sydney Morning Herald, on and on.

Synaptic to remove obsolete linux kernels.  Once or twice Computer Janitor did that for me, almost all the time it won't.  Obsolete kernels take up gobs of space.

Libre Office?  I use Write and Calc all the time.  Copying articles from internet, writing documents, you name it.

I"ve tried Software Center a couple times.  For what I was looking for and didn't find, Software Center was s-l-o-w-.

Want to save space?  What on earth are all those Language Packs being dumped in slowing install way down and taking up space when I already specified English?  I'm hundreds of miles from any other country.  Yes I took Spanish in High School and German in College, over 50 years ago, but I'm not conversant and will never be.  

Games?? save space. I don't do games.  Just have them on the Software Center.

Photo's?  The whole family uses Picasa interchangeably on Linux, Microsoft, and Mac.  I've had no use for any of the Linux photo services yet - have them on the Software Center where Gimp is?

Now as a tester I frequently do installs so a "skeleton Ubuntu" just increases my time testing new daily builds as I load on all the stuff an "ordinary user" would try on Ubuntu, examples internet brwose & video, write, email: Yahoo, AOL, Gmail, network file & printer sharing.

By the way, Oneiric still doesn't do network file sharing.  I can copy files from Oneiric but it can't see files on Natty on another pc on the net.  Something about a "share list from the server".  So I do sneaker net.

I'd rather stick with Ubuntu because of the very good forums and occasional launchpad fixes.  I"m not sure what target market Ubuntu  developers are after.  They do have a good set of flavors as is, Lubuntu, Kubuntu, Xubuntu, Edubuntu, ... except for digital TV support which I haven't mastered yet - I can get "TV Viewer" to work.  It's a bit primitive.

Jerry

---

### Post by cgroza on 2011-06-24
I simply  use the command line...

---

### Post by jerrylamos on 2011-06-24
> **Harry33 said:**
> 
Synaptic is removed
Deja-dup, libgail-common and qt-at-spi added


What on earth is "Deja-dup"?  "libgail-common"?  "qt-at-spi"?  Anyone ever use them for anything?

I use Synaptic on every test install for Samba, flashplugin, and on existing installs for removing obsolete linux images that take up tons of space (Computer Janitor doesn't hack it).

Any ideas what these are?  I'll take a look at the URL later.

Jerry

---

### Post by sparker256 on 2011-06-24
> **jerrylamos said:**
> What on earth is "Deja-dup"?  "libgail-common"?  "qt-at-spi"?  Anyone ever use them for anything?

I use Synaptic on every test install for Samba, flashplugin, and on existing installs for removing obsolete linux images that take up tons of space (Computer Janitor doesn't hack it).

Any ideas what these are?  I'll take a look at the URL later.

Jerry
"Deja-dup" is a backup program that I have no idea why it needs to be on a live cd.

Bill

---

### Post by lucazade on 2011-06-24
We don't need also kernel and Xorg, we should remove them.
Leave only synaptic in the iso, nothing else.

::facepalm::

---

### Post by 23dornot23d on 2011-06-24
UNITY ......

No Gimp
No Aptitude
No Synaptic

Development by removal .... will be interesting as time goes on .
( seems to me like one of the main removals going on at the moment is users )

_____________________________________________

Additional things that were added to replace the above  ....

F-Spot
The Software Centre
Young users to buy into Ubuntuone the Cloud etc .....

Might work ..... best of luck but I do not use any of the 3 things above 

It would be interesting to see how many USERS do successfully use these things - as most seem unstable or unusable to me at this moment in time.

____________________________________________________________

If you are going to design the best - you start with a clean whiteboard
and put you best products in it ..... ( which work ..... )

You do not remove the most stable items that people use to replace them
with less stable items or ones that do not function as well IMHO

---

### Post by Rifester on 2011-06-24
I believe Deja-Dup is going to be the default pre-installed back up program in 11.10.   I have been using it for awhile and have been very happy with it.

---

### Post by teh603 on 2011-06-24
Y'know, instead of trimming out packages, we could just go to a DVD iso like Debian, Red Flag, and quite a few other good distros. That way we'd have room for GIMP, and Synaptic, and maybe a few decent games. Who out there doesn't have a DVD burner these days?

---

### Post by Harry33 on 2011-06-24
> **jerrylamos said:**
> What on earth is "Deja-dup"?  "libgail-common"?  "qt-at-spi"?  Anyone ever use them for anything?
I use Synaptic on every test install for Samba, flashplugin, and on existing installs for removing obsolete linux images that take up tons of space (Computer Janitor doesn't hack it).
Any ideas what these are?  I'll take a look at the URL later.
Jerry

Backup:
As explained, Deja-dup is a new default backup tool.

Accessibility:
Libgail-common is Gnome Accessibility Implementation Library, common modules
and
Qt-at-spi is Assistive Technology Service Provider Interface, plugin for Qt.

---

### Post by seeker5528 on 2011-06-24
> **beew said:**
> Yes I know I am free to install it. But IMO 

1) Synaptic is not difficult to use at all and it does a whole lot more, its removal reflects an attitude that I find it troubling, namely to regard the new users as super stupid. Most people who venture out of the comfort zone of Windows and Mac to give Linux a try would expect some learning curve and learning how to use Synaptic is really trivial (comparing to say navigating using Unity)

Are you saying you think people are idiots who would rather search for Gimp and find a software page with an optional list of addons 
[img]http://home.comcast.net/~seeker5528/Screenshot-USC1.png[/img]
instead of searching for it in Synaptic and getting a list of 120 packages?

> 2) The software centre is just plain crappy and it provides bad user experience and this actually reflects badly on Ubuntu. It takes forever to starts and when it starts up it uses  ~ 100% cpu on some older machines and it takes forever to install softwares. It is a bloatware that does little and it doesn't reflect Linux's strength at all.

Maybe people with older machines should upgrade to old machines, or run Lubuntu. :p

> **sparker256 said:**
> "Deja-dup" is a backup program that I have no idea why it needs to be on a live cd.

When your Live CD is an installation CD and the installation is created from the live image, the image needs to include the software that is included in the final installation.

Later, Seeker

---

### Post by iClouseau88 on 2011-06-24
If my memory serves me correctly, in Maverick I had to  install "aptitude" via synaptic before I could do the update or install software applications.

The worst case scenario is that comes October, both "aptitude" and "synaptic" would be kept out of default installation, for some reasons.

I hope this won't happen, unless the Canonical people are out of their mind!

---

### Post by teh603 on 2011-06-24
> **iClouseau88 said:**
> If my memory serves me correctly, in Maverick I had to  install "aptitude" via synaptic before I could do the update or install software applications.

The worst case scenario is that comes October, both "aptitude" and "synaptic" would be kept out of default installation, for some reasons.

I hope this won't happen, unless the Canonical people are out of their mind!Now you know how I felt on my eeePC 701 when I couldn't install GIMP because of two packages that depended upon each other- neither could be installed because the other wasn't already there.

---

### Post by iClouseau88 on 2011-06-24
@teh603:

Mister Shuttleworth: FEEL OUR PAIN!

;-))

---

### Post by jerrylamos on 2011-06-25
> **iClouseau88 said:**
> If my memory serves me correctly, in Maverick I had to  install "aptitude" via synaptic before I could do the update or install software applications.

Aptitude is one of my first apt-get install's since the "Dread Update" has totally sudsed my test systems many times.  I have much much better luck with aptitude's safe-upgrade.

Another early install is Gparted since my view somebody else can test Ubiquity's partitioning.  I've been totally screwed by "install" since it has a lot of trouble understanding at least two hard drives with multiple partitions including in some cases "Windoze 7".  Why do I keep that around? for when I upgrade pc's and can wish "Windoze" off on someone else.

Synaptic?  Is it still going to be around to apt-get install?  I could do the whole thing with apt-get if I knew all the crazy names packages have.  I use Synaptic for it's description of the packages.  Anyone know of another way to find out all the various *.*.*.-.*.xx3 names?

Libre Office?  I use it all the time for saving internet browse articles on health & science & news and whatever as well as writing documents and doing calc.

What on earth is filling up Ubuntu that the stuff I use all the time may be booted out??  

Note, I don't do games, photos I use Picasa which is compatible with the rest of the family on Windoze and Mac.  I'm hundreds of miles from any other country so I only use English so what are all those language packs that take up so so so much time on installs and updates??  I use internet email yahoo, AOL, gmail because I can access everything from more than one computer, and from my daughter's homes in NH, Utah, and even Australia visiting my son.  I have no use for Ubuntu's email facilities which would save space.  

I'm usually running Lucid (downloads updates & iso's faster), Natty (regular workhorse) various OO's on netbook, notebook, and desktop so I have no use for doing pc based email.

I wonder what algorithm Ubuntu uses for what features should be on the base CD.  One reason I like the CD is if they go to DVD's suddenly the distro install will be 4G big and 4G slow...

Oh, well, I'm testing whatever development throws over the fence.  I do like the forums for help when I get in trouble and sharing hints.

Jerry

---

### Post by Bazon on 2011-06-25
> **beew said:**
> 
2) The software centre is just plain crappy and it provides bad user experience and this actually reflects badly on Ubuntu. It takes forever to start and when it start up it uses  ~ 100% cpu on some older machines and it takes forever to install softwares.  It is a bloatware that does little and certainly doesn't show new user Linux's strength.


So it fits perfectly to Unity. 

(I'm so happy there is still XFCE and LXDE, the mainstream Ubuntu development is making me mad....)

---

### Post by 23dornot23d on 2011-06-25
> 
Aptitude is one of my first apt-get install's since the "Dread Update"  has totally sudsed my test systems many times.  I have much much better  luck with aptitude's safe-upgrade.
Exactly .... true ..... 

If I had to build a system up using only apt-get and the Software Centre it would be an interesting challenge.

No doubt that is yet to come .... (for many others) ..... cannot wait for the forum to start 
asking the questions ..... the software centre failed and it hardly says anything as regards the problem ... well you could have used synaptic or aptitude would be my first response.

So ..... what alternatives do I have left to tell them now ......

HOW DO I FIX it ......

Quick answer ...... it takes 30 minutes to re-install a system - or use another one
Linux Mint .... Fedora ..... Sabayon ... who knows .... 

Maybe try re-installing Ubuntu again ...... but what if I get the same problem .....
well you re-install it again ..... :confused:

or

its
sudo apt-get update  
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install synaptic

Now look in synaptic do a screen shot of what you have installed it shows
the version you have and the latest version that will replace it if there is one.

or the alternative in the software centre

Just type in the name ..... it will say yes it will install or give you a dependency problem why it cannot ...... and how do we get around this .....

GO ASK THE DEVELOPERS

---

### Post by lucazade on 2011-06-25
As usual, there's a reason for most every decision.
Following official communications and docs, looking at blueprints and development channels
everyone can have a complete vision of what's happening.

I agree wholeheartedly with Ubuntu's goals.. a perfect mix for new and expert users 
and so flexible that you can build your own distro starting from a mini iso image of 10mb.

---

### Post by 23dornot23d on 2011-06-25
> 
As usual, there's a reason for most every decision.


You must know the reason then ..... without others having to look through all the documentation ....

What in your opinion is it ..... as its eluding me at the moment.

---

### Post by lucazade on 2011-06-25
> **23dornot23d said:**
> You must know the reason then ..... without others having to look through all the documentation ....

What in your opinion is it ..... as its eluding me at the moment.

In the specific case of synaptic the removal has been announced a lot of time ago, more or less when it was announced the software-center.

Has been removed (or better will be officially removed when apt-url won't depend on it) for a lot of reasons, like no gtk3 port, already two package managers installed and included by default, an easy and saner interface of USC for non-pro users (knowing that who usually use synaptic will install it w/o problems)..

USC is preferred because is developed in house, can be adopted from other distros, allow to buy apps and will help to spread new softwares, almost all OS for pc and mobile are employing a market-style application.

Seem good reasons for me.

---

### Post by 23dornot23d on 2011-06-25
I will remove synaptic and have another look at the Software Center as it may have changed in its design and try using it alone for a few days ( to see if I can help sort anything out ).

Obviously if there are no problems caused by it then we will all have happy faces :D

Will do a clean installation and see how easy it is to add a repository to it for some of the things I use ......

---

### Post by cariboo on 2011-06-25
> **23dornot23d said:**
> I will remove synaptic and have another look at the Software Center as it may have changed in its design and try using it alone for a few days ( to see if I can help sort anything out ).

Obviously if there are no problems caused by it then we will all have happy faces :D

Will do a clean installation and see how easy it is to add a repository to it for some of the things I use ......

I really don't understand why you would remove synaptic, if you find it works best for you. I've tried the Software Center, and for me it doesn't work the way I do, it's to simplistic.

---

### Post by 23dornot23d on 2011-06-25
> 
I really don't understand why you would remove synaptic, if you find it  works best for you. I've tried the Software Center, and for me it  doesn't work the way I do, [COLOR=Red]**it's too simplistic**[/COLOR].
Exactly ....  how else do we get a feel for what its going to be like for a first time user.

Someone has to try to look at it from a new users point of view otherwise we just become elitist and then 
( The USERS ) have to come and ask us for the answers ...... 

This should not be the case - if we can get it to work better - then that is development.

Removing packages like Synaptic ..... ( is just removing a useful thing )

If you remove things as a developer - you should ensure that people are not going to get stuck with over simplistic applications that are meant to do the same job as the ones
that are being removed.

Unless we are in fact down grading ......

---

### Post by cariboo on 2011-06-25
If you look a the support forums, there are a lot of users that don't even know that synaptic exists, they are more than happy using the Software Center. I'm just glad I still  have the option to use something else.

---

### Post by novatillasku on 2011-06-25
Synaptic is still installed in oneiric ;-)

---

### Post by lucazade on 2011-06-25
> **novatillasku said:**
> Synaptic is still installed in oneiric ;-)

[http://ubuntuforums.org/showpost.php?p=10974849&postcount=15](http://ubuntuforums.org/showpost.php?p=10974849&postcount=15)

---

### Post by Mr. Picklesworth on 2011-06-25
> **teh603 said:**
> Y'know, instead of trimming out packages, we could just go to a DVD iso like Debian, Red Flag, and quite a few other good distros. That way we'd have room for GIMP, and Synaptic, and maybe a few decent games. Who out there doesn't have a DVD burner these days?

These things are not being trimmed for space reasons. They are being trimmed because Ubuntu needs to provide a streamlined, approachable set of applications out of the box. Shipping on a CD is how the developers hold themselves to it. I, for one, want people using vanilla Ubuntu to feel empowered by their systems. I want people to feel comfortable, knowing that they understand what all that new software does. It's the difference between having a ghettoized *easy zone* (separated by an &#8220;Advanced&#8221; button) and actually being easy to use.

With System Settings (gnome-control-center) hosting lots of things that used to be separate bits of software - including backup settings - we are getting very close to that goal by reducing the set of individual applications floating around out of the box (each one demanding to be understood). I think modern smartphone operating systems like iOS and Android have made it really clear why it helps to be simple from the start: people are much more comfortable with heaps of applications when they are *their* applications.

---

### Post by 23dornot23d on 2011-06-25
> 
(separated by an &#8220;Advanced&#8221; button)
This maybe needs including and soon ...... as the dumbed down version seems to be for all
at the moment  ....

A single key press maybe should take people into a mode where the things they have always been used to - are  still there ......

Or we stay in the Ghetto .... and try to  have some fun with the basics ..... :D

**[COLOR=Red]a ghettoized *easy zone*[/COLOR]**

---

### Post by seeker5528 on 2011-06-25
> **jerrylamos said:**
> Synaptic?  Is it still going to be around to apt-get install?  I could do the whole thing with apt-get if I knew all the crazy names packages have.  I use Synaptic for it's description of the packages.  Anyone know of another way to find out all the various *.*.*.-.*.xx3 names?

Are you talking package names, becasue that seems like an awful lot of dots for a package name. :p

If I have to do much at the command line I like to use [aptsh](http://aptsh.berlios.de/howto.html)

You can use it much like you would the other command line apt stuff ```
sudo aptsh install some-package some-other-package and-yet-another-package
```

But if you run it to enter the pseudo shell it provides, you have tab completion and usage of wild cards, then you could do things like ```
sudo aptsh
show libreoffice
ls *libreoffice* | less
purge *libreoffice*
exit
```

which would first start the aptsh shell interface, show information about libreoffice, show all packages with libreoffice in the name, purge all packages with libreoffice in the name, then exit the aptsh shell.

If you wanted the short description of libreoffice instead of the package information you could use 'whatis' instead of 'show'.

Not 100% sure about wild cards if you issue the command without entering the shell environment, but I think it would do it ```
sudo aptsh purge *libreoffice*
```

Later, Seeker

---

### Post by seeker5528 on 2011-06-25
> **23dornot23d said:**
> Exactly ....  how else do we get a feel for what its going to be like for a first time user.

You have to take into consideration that there are issues during development that people wouldn't often see if they stick to stable releases and official repositories.

If you start adding PPAs to the mix you are adding instability so there is more potential for problems, but that depends on the PPA maintainers and how unstable the software is (how unstable as in new version every week, new version every other month, etc... and how significant are the changes in each version).

Later, Seeker

---

### Post by 23dornot23d on 2011-06-25
Your words are always wise ones .... and I do understand that PPA's can add a risk ....

Maybe they should be evaluated and given some form of respect status .....

:KS:KS:KS Trusted 

:confused: Un-trusted

:KS:KS:KS Stable

:confused: Liable to kill your machine ..........

Many people are using them ...... and do they know the risks .... or is it best not to use them.

(64 bit Flash ,,,, is one I need .... for my SCRABBLE ...... and the official adobe one is useless ....)

So what do I do stop playing SCRABBLE ..... ?

NO of course NOT .....

sevenmachines ppa for 64 bit is the only one that works for me ..... maybe it needs including officially.
( its pretty stable , and you can always remove a PPA once you have what you want .... or should I say you could )


The System could ... add it officially .... once its checked out .... if that is what is required .

__________________________________________

Already I am reading here that people have problems with flash ..... maybe these problems have already
been solved .... and its just a question of adding the right PPA ..... but how do they do that and what 
reassurances do they have that its ok to do so .........

---

### Post by teh603 on 2011-06-25
> **23dornot23d said:**
> Your words are always wise ones .... and I do understand that PPA's can add a risk ....

Maybe they should be evaluated and given some form of respect status .....

:KS:KS:KS Trusted 

:confused: Un-trusted

:KS:KS:KS Stable

:confused: Liable to kill your machine ..........

Many people are using them ...... and do they know the risks .... or is it best not to use them.Wasn't there a labeling system in Synaptic for stuff that was tested by Canonical, and stuff that wasn't? It'll probably be extended to the Software Center.

> (64 bit Flash ,,,, is one I need .... for my SCRABBLE ...... and the official adobe one is useless ....)

So what do I do stop playing SCRABBLE ..... ?

NO of course NOT .....

sevenmachines ppa for 64 bit is the only one that works for me ..... maybe it needs including officially.
( its pretty stable , and you can always remove a PPA once you have what you want .... or should I say you could )


The System could ... add it officially .... once its checked out .... if that is what is required .

__________________________________________

Already I am reading here that people have problems with flash ..... maybe these problems have already
been solved .... and its just a question of adding the right PPA ..... but how do they do that and what 
reassurances do they have that its ok to do so .........
Ironically, I've never been able to get any of the 64-bit flash plugins to work. Although instead of Scrabble, I like playing 3D single-player tank war games. There was a good wireframe one (battlezone?) that never seems to get ported to Linux... hint hint.

Edit: I mean the 1980 version, not the 1998 one.

---

### Post by seeker5528 on 2011-06-25
> **teh603 said:**
> Wasn't there a labeling system in Synaptic for stuff that was tested by Canonical, and stuff that wasn't? It'll probably be extended to the Software Center.

I think it's the same as it has ever been, Canonical supported versus community maintained or in other words, Synaptic has a column in the package listing where an Ubuntu logo will be displayed for things in main or not displayed for everything else.

Not sure for things in the partner repositories, but I expect you don't see the logo.

Later, Seeker

---

### Post by jerrylamos on 2011-06-25
> **seeker5528 said:**
> Are you talking package names, becasue that seems like an awful lot of dots for a package name. :p

If I have to do much at the command line I like to use [aptsh](http://aptsh.berlios.de/howto.html)

You can use it much like you would the other command line apt stuff ```
sudo aptsh install some-package some-other-package and-yet-another-package
```

But if you run it to enter the pseudo shell it provides, you have tab completion and usage of wild cards, then you could do things like ```
sudo aptsh
show libreoffice
ls *libreoffice* | less
purge *libreoffice*
exit
```

which would first start the aptsh shell interface, show information about libreoffice, show all packages with libreoffice in the name, purge all packages with libreoffice in the name, then exit the aptsh shell.

If you wanted the short description of libreoffice instead of the package information you could use 'whatis' instead of 'show'.

Not 100% sure about wild cards if you issue the command without entering the shell environment, but I think it would do it ```
sudo aptsh purge *libreoffice*
```

Later, Seeker

I couldn't find aptsh from the command line nor from the url you quoted.  How and where did you get it?

Thanks, Jerry

---

### Post by 23dornot23d on 2011-06-25
> 
I couldn't find aptsh from the command line nor from the url you quoted.  How and where did you get it?
Its in the repositories use [COLOR=Red]**synaptic**[/COLOR] to find it ..... seems ironic ..... :confused:

Not that it cannot be found using the Software Center too ....

[IMG]http://img121.imageshack.us/img121/1020/softwarem.png[/IMG]


Hope this helps ..[]("http://en.wikipedia.org/wiki/Battlezone_%281980_video_game%29")

---

### Post by seeker5528 on 2011-06-25
> **23dornot23d said:**
> Your words are always wise ones .... and I do understand that PPA's can add a risk ....

Maybe they should be evaluated and given some form of respect status .....

Don't know what the potential for that kind of thing is, it might be nice.

The only PPA I have followed long term at any point to pull backports into a stable release was the Kubuntu PPA, which the developers did a reasonably good job with, being Kubuntu and all, but KDE doesn't seem like the most friendly beast to provide backports of.

Later, Seeker

---

### Post by seeker5528 on 2011-06-25
> **jerrylamos said:**
> I couldn't find aptsh from the command line nor from the url you quoted.  How and where did you get it?

Sorry, I thought ```
sudo apt-get install aptsh
``` went without saying. :P

The link was just to provide some info on what it is.

Normally when I type a command in that is provided by a package that is available but not installed, I expect something like ```
seeker@ubuntu:~$ aptsh
The program 'aptsh' is currently not installed.  You can install it by typing:
sudo apt-get install aptsh
```

But I guess that only works if you type 'some-command' and not when you type 'sudo some-command'. :(

Later, Seeker

---

### Post by Mr. Picklesworth on 2011-06-25
> **23dornot23d said:**
> Its in the repositories use [COLOR=Red]**synaptic**[/COLOR] to find it ..... seems ironic ..... :confused:

Not that it cannot be found using the Software Center too ....

**snip**


Hope this helps

It's in there. It just isn't backed up by an Ubuntu logo. (That presentation is pretty dubious, really).
[ATTACH]195991[/ATTACH]

> **23dornot23d said:**
> Or we stay in the Ghetto .... and try to  have some fun with the basics ..... :D

**[COLOR=Red]a ghettoized *easy zone*[/COLOR]**

You certainly can have fun with the basics! That's pretty well my point. With a simple, clean slate the system is yours to make as complex as you want *on your own terms*! I don't think shipping advanced system tools out of the box helps in the first place, unless the system is so broken it needs them to function (in which case we should all switch to Debian). In particular, I think people who know about package managers have their preferences and stick with them. I think if Synaptic was being replaced with Adept, this same discussion would be happening. Isn't it nicer to strip the extra package manager from the mix, so when you decide to install Synaptic it doesn't feel like a third appendage on top of all the others?

*Sorry about all the editing. I'm finished editing now :)*

---

### Post by screaminj3sus on 2011-06-26
> **lucazade said:**
> more than smell!
people is moving to Arch because of synaptic removal... 
[http://www.webupd8.org/2011/06/synaptic-removed-from-ubuntu-1110-deja.html](http://www.webupd8.org/2011/06/synaptic-removed-from-ubuntu-1110-deja.html)
lol, why would you move from ubuntu to arch because synaptic isn't default? You can still install it.

Those comments are dumb, and I am an arch user myself.

---

### Post by ranch hand on 2011-06-26
Yup, kind of a silly thread.

You either like an OS for the mentally challenged or you have moved on already.

Hopefully Ubuntu will realize that idiots aren't the only folks using computers someday.

---

### Post by lucazade on 2011-06-26
> **screaminj3sus said:**
> lol, why would you move from ubuntu to arch because synaptic isn't default? You can still install it.

Those comments are dumb, and I am an arch user myself.

i'm not moving :)
read: I was ironic, at least I hoped to be.

---

### Post by SeijiSensei on 2011-06-26
> **lucazade said:**
> USC is preferred because is developed in house, can be adopted from other distros, **allow to buy apps** and will help to spread new softwares, almost all OS for pc and mobile are employing a market-style application.

Isn't the primary motivation for the "Software Center" providing the opportunity to "buy apps?"  In-house development, for instance, seems especially unconvincing as a justification when nearly everything else in Ubuntu comes from outside Canonical and is largely supported by third parties.  USC, to me, seem more of a method to help monetize Ubuntu than any great innovation is package distribution.  I'll stick with the ever-improving KPackageKit or install synaptic if I need to.  Most of the time it's "sudo apt-get install" for me anyway.

---

### Post by lucazade on 2011-06-26
> **SeijiSensei said:**
> Isn't the primary motivation for the "Software Center" providing the opportunity to "buy apps?"  In-house development, for instance, seems especially unconvincing as a justification when nearly everything else in Ubuntu comes from outside Canonical and is largely supported by third parties.  USC, to me, seem more of a method to help monetize Ubuntu than any great innovation is package distribution.  I'll stick with the ever-improving KPackageKit or install synaptic if I need to.  Most of the time it's "sudo apt-get install" for me anyway.

Unity and indicators are examples of developed in house softwares, are not coming from outside. USC is the same and this allow Canonical to have a total and granular control of the development.
This means that canonical can schedule development and choose features to be included and not be dependant on other's timeline and roadmap.

I can't say this is a top priority or not for its adoption, for sure is an element to be considered.

---

### Post by Rifester on 2011-06-26
Exactly!   I don't understand why everybody is so hurt by all of this.   Canonical has made it very clear they are going to be THE commercial Linux OS.   They are going to sell apps and music to you for income and they are going to advertise what they sell within their operating system.   Either you want to be apart of that or you move on to another distro.   It is a tough choice for some people who have been supporting Ubuntu for a long time...  But people need to accept where the OS is headed and the fact that we can't change the course.   The software center does not bother me, but I don't like what I see in the Applications dash.   I really don't like the idea of advertising to me when I am doing my work ("Apps available for download") and that is where it is headed....  If you want to offer me a place to browse apps or music (for sale) when I choose, great, but I don't want to see it while I am working.

---

### Post by lucazade on 2011-06-26
@SeijiSensei

only now i realized that you pointed out that grammar issue.
yep, it is not "buy apps" but "sell apps"..
I'm happy when someone corrects my english, this way I can improve it :)

---

### Post by ZarathustraDK on 2011-06-26
> **SeijiSensei said:**
> Isn't the primary motivation for the "Software Center" providing the opportunity to "buy apps?"  In-house development, for instance, seems especially unconvincing as a justification when nearly everything else in Ubuntu comes from outside Canonical and is largely supported by third parties.  USC, to me, seem more of a method to help monetize Ubuntu than any great innovation is package distribution.

As much as I want things free and dandy, I don't mind Canonical making a buck or two on this. It might serve as an incentive for software-makers to port their applications to Linux, which is an important factor for new users coming from other OS'es.

Also (don't know if you've noticed this) the Software Center has the potential to be our very own Steam-like platform, with purchased games and other software being verified through Ubuntu-One.

---

### Post by SeijiSensei on 2011-06-26
> **Rifester said:**
> Canonical has made it very clear they are going to be THE commercial Linux OS.   They are going to sell apps and music to you for income and they are going to advertise what they sell within their operating system.   Either you want to be apart of that or you move on to another distro.

I don't see any indication that it's "Canonical's way or the highway."  I find it hard to imagine a model for Ubuntu that would keep me from using KDE (or LXDE or Fluxbox or even the command prompt) and ordinary repository tools to maintain an entirely free version of the distro on my machine.  Your suggested strategy would be very dangerous for Canonical to follow since it would alienate a large chunk of the existing user base with little guarantee that a commercialized version of Linux will attract enough users to replace them.  The emigres are also likely to include a lot of the people providing free support in places like Ubuntu Forums.  Canonical would be left with a progressively less-sophisticated user base who'd require more support from Canonical itself.

I have absolutely no problem with Canonical establishing a method to distribute commercial applications and collect some coin along the way as long as I can choose to abstain.  I've worked with Linux for some fifteen years now and haven't bought a piece of commercial software for most of that time.  I don't see that changing for me any time soon.

My experience with in-house development of Ubuntu has not been a happy one -- the replacement of the traditional /etc/init.d system with [Upstart]("http://upstart.ubuntu.com/").  Upstart may make sense in theory, but in practice, it was rolled out way too soon.  Some of the major server apps still use init.d scripts while others use Upstart.  If you read the server threads, you'll see this has  lead to a lot of confusion when a daemon fails to start at boot.  My sense from reading discussions of Unity suggests that it, too, suffers from the problem of releasing too soon and trying to fix bugs later.

A solid commercialized Linux would have long release cycles (three years at a minimum, five would be better) and a strong preference for extensive in-house testing and bug-fixing over rushing to meet arbitrary release dates.  That's not the Ubuntu I see today.  (Yes, I know about LTS releases, but I'd much prefer the type of two-track strategy that RedHat uses for RHEL and Fedora. Instead Ubuntu uses a numbering scheme that will always encourage users to install the next release in the series, buggy or not.)

Oh, and it better have fixes for all the wireless problems we see reported every day in these Forums.  I understand why there are issues, but in a commercialized distribution, connectivity problems are simply unacceptable.

---

### Post by Rifester on 2011-06-26
By commercial, I mean as in making a profit off of selling apps, storage, and music.  I believe Ubuntu as an OS will remain free.    I am however, concerned that in a very short tim, the advertising for profit will be hard to escape.   I also don't fault Canonical for wanting to be profitable and I would in fact support them by purchasing apps and music.  I just hope they are cautious about where and how they advertise.  I also hope that developers can make good money with the sale of their applications...

---

### Post by Rifester on 2011-06-26
> **SeijiSensei said:**
> Your suggested strategy would be very dangerous for Canonical to follow since it would alienate a large chunk of the existing user base with little guarantee that a commercialized version of Linux will attract enough users to replace them.  The emigres are also likely to include a lot of the people providing free support in places like Ubuntu Forums.  Canonical would be left with a progressively less-sophisticated user base who'd require more support from Canonical itself.
.

I think many people feel this is already happening...   Ranch Hand for example is a very smart person (and tester) who has left for Debian.    I have  lot of respect for Ranch Hand, and hate to see people like that leave with their talents.  
We are definitely in interesting times!

---

### Post by VinDSL on 2011-06-26
> **Rifester said:**
> We are definitely in interesting times!
Heh!  :D

> &#23527;&#28858;&#22826;&#24179;&#29356;&#65292;&#19981;&#20570;&#20098;&#19990;&#20154;

---

### Post by mc4man on 2011-06-26
Additionally removed while still useful is gconf-editor, again no big deal, just install.
I do find a bit curious the decision to make 'Startup Applications' invisible to the dash, either from a search or the apps dropdown.
(NoDisplay=true in the .desktop

It's been determined to be too dangerous to the mythical 'target user'

---

### Post by ranch hand on 2011-06-26
Some thoughts on points by SeijiSensei.
> 
Your suggested strategy would be very dangerous for Canonical to follow  since it would alienate a large chunk of the existing user base with  little guarantee that a commercialized version of Linux will attract  enough users to replace them.  The emigres are also likely to include a  lot of the people providing free support in places like Ubuntu Forums.   Canonical would be left with a progressively less-sophisticated user  base who'd require more support from Canonical itself.

This is already happening.  I do not think that Canonical is all that concerned about it as you have always had the option of buying support from them.

That support is probably great and a very good idea.

Treating the members of the Official forum with no respect is loosing forum usage.  This is not good.
> 
I have absolutely no problem with Canonical establishing a method to  distribute commercial applications and collect some coin along the way  as long as I can choose to abstain.  I've worked with Linux for some  fifteen years now and haven't bought a piece of commercial software for  most of that time.  I don't see that changing for me any time soon.

I have to agree with you all the way on that one.   I do think that there are some openings for commercial apps and that encouraging them is a good idea.  Ag targeted apps are available for MS and Mac and they might be easily ported to Linux (usually spread sheet/db based for record keeping).  As these are not general use and do take effort buying them is probably the only way they will ever be available.
> 
My experience with in-house development of Ubuntu has not been a happy  one -- the replacement of the traditional /etc/init.d system with [Upstart]("http://upstart.ubuntu.com/").   Upstart may make sense in theory, but in practice, it was rolled out  way too soon.  Some of the major server apps still use init.d scripts  while others use Upstart.  If you read the server threads, you'll see  this has  lead to a lot of confusion when a daemon fails to start at  boot.  My sense from reading discussions of Unity suggests that it, too,  suffers from the problem of releasing too soon and trying to fix bugs  later.

and
> 
Oh, and it better have fixes for all the wireless problems we see  reported every day in these Forums.  I understand why there are issues,  but in a commercialized distribution, connectivity problems are simply  unacceptable.

Ubuntu seems to be in a race with it self for "improvements" but not interested in outstanding bugs very much at all.

The connection problems have been around for a long time and do not seem to get attention at all.  These do seem to be more prevalent in the Debian branch than the RH branch but I have trouble with the idea that the stuff used in RH could not be used here too.  Have no idea why it is not.  If anyone does I would love to hear about it.

Over all I think you have summed up the challenges of this headlong dash to somewhere very well.

---

### Post by hakermania on 2011-06-27
Wt*?
Synaptic will be installable by the software center so what's the problem?

---

### Post by seeker5528 on 2011-06-27
> **SeijiSensei said:**
> Isn't the primary motivation for the "Software Center" providing the opportunity to "buy apps?"

On it's own, don't really think there is much motivation there, certainly not enough to make it "the primary motivation".

But once you have reviewed the landscape and decided that something like Synaptic is more than what most people are looking for in terms of features, that the majority cares more about software than packages, and that the managers that make an effort to present things in terms of software instead of packages falls short, there was incentive to create something from scratch.

Once that was determined, then providing the opportunity to buy apps makes more sense because it creates more incentive for ISVs who want to make their software available for purchase to Ubuntu users to work with Canonical since there is a more direct line to Ubuntu users who are open to the option and on the other side of the coin, depending on what happens with ISVs there is potential to make Ubuntu more attractive in the mass market if there is an additional range of software available that users are willing to pay for relative to the range of software that is available at no charge.

To me the categories that make the most sense for this would be software that targets a business environment or that target home entertainment.

Later, Seeker

---

### Post by meborc on 2011-06-27
For me losing Synaptic means nothing. Ever since Ubuntu 5.10 when I had serious issues with Synaptic I have reverted to using apt and apt only. As Synaptic is just a front end for apt, I do not feel left out at all.

Having Synaptic and USC both installed seems like an overkill for me, but again, I have no real experience with Synaptic and don't know what great advantages it has compared to apt in command line.

---

### Post by recluce on 2011-06-29
> **beew said:**
> Explain what? Your purpose here seems to be just to spout the party line. Seeing that you said users should not have any input because only the devs know best (on the other thread) I can't really take you seriously.

+ 1

I have given up on Ubuntu future versions, but still come back now and then - to savour the antagonism of the fanbois. 

I have learned from this "community" recently: if you don't contribute code, shut up. The developers are gods and know better anyway. And the fact that Ubuntu is down to #3 on distrowatch is only due to people "looking" at other distros. Yeah, sure....

---

### Post by lucazade on 2011-06-29
> **recluce said:**
> + 1

I have given up on Ubuntu future versions, but still come back now and then - to savour the antagonism of the fanbois. 

I have learned from this "community" recently: if you don't contribute code, shut up. The developers are gods and know better anyway. And the fact that Ubuntu is down to #3 on distrowatch is only due to people "looking" at other distros. Yeah, sure....

-1

This is a mystification of what has been written in order to support personal opinions.

Yeah, can't sleep the night now that Ubuntu on Distrowatch is on 3rd place..
:guitar:

---

### Post by trizrK on 2011-06-29
> **lucazade said:**
> I hope also gwibber will be wiped out from default install!
Whats wrong with it D':

---

### Post by lucazade on 2011-06-29
> **trizrK said:**
> Whats wrong with it D':

Nothing special.. I don't find it so useful cos I don't use social network so much.
I know it could be different for other.
An annoying thing of Gwibber is dependency on Indicator-message for which I never found a real reason to hook to.

---

### Post by jerrylamos on 2011-06-29
> **lucazade said:**
> Nothing special.. I don't find it so useful cos I don't use social network so much.

Only "social network" we use is email, also web sites example for the bicycle club (my wife does updates on events and rides available) and the local Democratic party website events (which she also keeps current.  This is New Hampshire with lots of political interest).

We don't walk down the street chattering away out loud on cell phones either.  It's popular so perhaps there could be options for those who do and those who don't.

Jerry

---

### Post by lucazade on 2011-06-29
> **jerrylamos said:**
> 
We don't walk down the street chattering away out loud on cell phones either.  
Jerry

eehehh.. nice comparision with facebook :)

---

