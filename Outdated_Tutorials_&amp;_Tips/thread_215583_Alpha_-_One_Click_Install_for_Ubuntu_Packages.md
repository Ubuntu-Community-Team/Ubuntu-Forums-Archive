---
title: "Alpha - One Click Install for Ubuntu Packages"
date: 2006-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by KillerKiwi on 2006-07-14
This is a simple prototype of one click install for ubuntu packages

simply download this file unzip and run the install script (no need for sudo)

You should then be able to install packages be cliking on links like below

[install bluefish HTML editor]("install://bluefish")
[install xchat irc client]("install://xchat")
[install tomboy sticky note wiki]("install://tomboy")

More info
[https://wiki.ubuntu.com/aptgetinstallprotocol](https://wiki.ubuntu.com/aptgetinstallprotocol)
[https://launchpad.net/distros/ubuntu/+spec/apt-get-install-protocol](https://launchpad.net/distros/ubuntu/+spec/apt-get-install-protocol)

Good idea ? Bad idea ? Stupid idea ? 

Do you like the concept?, remember the implmentation can change constuctive criticism is good.

EDIT: Code update
[LIST]
[*]Update the install script to install protocol-install.py to /usr/bin and apply correct file permissions (thanks scenestar), anybody know anything more about how the mailto: protocol etc deals with security issues?
[*]Added an uninstall script
[/LIST]

[B]Note: When running random scripts from the internet its as always a good idea to see what they do first ;) 
This only installs packages from repos in your existing sources list using synaptic!, no external binaries are invloved[/B]

---

### Post by petervk on 2006-07-14
Great Idea. I really think this would help the community, and make dapper much easier to use.

For example, the inkscape site could have the usual instruction on how to get their program:

----

**Windows:**
Download this exe, and keep checking back here every week for updates.

**Mac OSX:**
Download this dmg file and run the application, remember to keep checking this site for updates.

**Debian:** 
type: 
```
apt-get install inkscape
```
in a terminal. 
(This will update when you update debian)

**Ubuntu:**
Click this link: [Install Inkscape]("install://inkscape")
(This will automatically be kept up to date)

----

Just my idea.

---

### Post by petervk on 2006-07-14
Lets get this dugg:
[http://digg.com/linux_unix/One_Click_Install_for_Ubuntu_Packages_-_Alpha_Test](http://digg.com/linux_unix/One_Click_Install_for_Ubuntu_Packages_-_Alpha_Test)

---

### Post by Adrian_b on 2006-07-14
Isn't this the exact same thing as Klik? 
[http://klik.atekon.de/](http://klik.atekon.de/)

---

### Post by pchr on 2006-07-14
> **KillerKiwi said:**
> **Note: This only installs packages from repos in your existing sources list !**

Do you mean it's not providing extra functionality it's just a shortcut for apt-get/synaptic?  In that case I suppose I'd use it if such a link was there to be clicked, but I think synaptic's so easy, why bother?  Or am I confused:confused:

---

### Post by I922sParkCir on 2006-07-14
> **Adrian_b said:**
> Isn't this the exact same thing as Klik? 
[http://klik.atekon.de/](http://klik.atekon.de/)

Klik doesn't really install the app in the conventional sense. This just seems like a tie-in to apt. It looks helpfull though.

---

### Post by Janux on 2006-07-14
> **pchr said:**
> Do you mean it's not providing extra functionality it's just a shortcut for apt-get/synaptic?  In that case I suppose I'd use it if such a link was there to be clicked, but I think synaptic's so easy, why bother?  Or am I confused:confused:
Because Synaptic is quite hard to find something but do you don't know its name. Wanna an accounting software, but you are new to Ubuntu? Good luck finding it. With this, we may have a new world of possibilities, think about it. We may have something like a site with software, screenshots, comments, et cetera, a site like the local gnome-app-install but with more options and dinamic content.

---

### Post by petervk on 2006-07-14
Exactly. I think a website could be a lot better then gnome-app-install.

All we need now is a way to search the universe/multiverse package lists when they are not yet enabled and then enable them when the user requests a package contained in them.

Example:
```

sudo apt-get install audacity
...
whatever
...
audacity is part of the universe repo, and you currently do not have it enabled. 
To install audacity you must enable the universe repo.
Enable the universe repo?
(Y)es/(N)o/(T)emporally to install this package

```

So when a user clicks a [Install Audacity]("install://audacity") link, there will be a GUI prompt to ask the user if they want to enable the universe/multiverse, insted of just failing like it currently would.

This is partially covered by:
[https://launchpad.net/distros/ubuntu/+spec/enabling-additional-components]("https://launchpad.net/distros/ubuntu/+spec/enabling-additional-components")
[https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse]("https://wiki.ubuntu.com/AlwaysEnableUniverseMultiverse")

---

### Post by gorilla_king on 2006-07-14
this was a great idea.

---

### Post by pchr on 2006-07-14
> **Janux said:**
> We may have something like a site with software, screenshots, comments, et cetera, a site like the local gnome-app-install but with more options and dinamic content.

Yeah true true, probably was a bit short sighted really.  :-#   

:-k I guess I'm thinking about myself and I'm perfectly happy to go into synaptic and hunt around (actually it's getting a bit of an obsession, while a windows user I used to spend yonks trowling through freeware sites and magazines, now they're all in one place I love it.  I really like right clicking a package and finding out about suggested packages) BUT I can see it'll be a lot easier for newbies, Having a load of links embedded into a newbie user guide would be pretty cool for initially setting up your system with naughty codecs etc...  It'd be a bit like these automatix type things but with a bit more control.

Does it literally go off and install the thing as soon as you click, could be a bit scary for a newbie who accidentally clicks install KDE-Desktop!

---

### Post by scenestar on 2006-07-14
No offense, but this is kinda redundant and not very spectacular at all.

**What you are are trying to do can be easily be achieved using shell scripts and zenity.**

It is however a nice way to handle all those 

> apt-get install foo

boxes on the forums, but really it isn't groundbreaking development.

---

### Post by scenestar on 2006-07-14
And in addition I would like to add the following.

Browsing through the alpha test I imidiately saw that the protocol is installed by a regular user.

**Doesn't anyone see the potential for a SERIOUS security hole?**

just imagine a user browsing to a [www.example.com/malacious/ffox0day](www.example.com/malacious/ffox0day).

All the attacker has to do is replace the install:// handler with his own and users can easily be tricked into installing non official (trojanised) binaries.

As I'm assuming that this "feature" will be aimed at more casual "non-techy" users, who will fail to check if the packages are indeed verified.

Please do not release these alpha's so publicly in order to "protect the innocent"

---

### Post by Lord Illidan on 2006-07-14
It seems handy. However, Klik already seems to the job. Good thinking, though.

---

### Post by KillerKiwi on 2006-07-14
> **scenestar said:**
> And in addition I would like to add the following.

Browsing through the alpha test I imidiately saw that the protocol is installed by a regular user.

**Doesn't anyone see the potential for a SERIOUS security hole?**

just imagine a user browsing to a [www.example.com/malacious/ffox0day](www.example.com/malacious/ffox0day).

All the attacker has to do is replace the install:// handler with his own and users can easily be tricked into installing non official (trojanised) binaries.

As I'm assuming that this "feature" will be aimed at more casual "non-techy" users, who will fail to check if the packages are indeed verified.

Please do not release these alpha's so publicly in order to "protect the innocent"


Im not going to claim this is fool proof at the moment but it does check to see if the passed parameter is a valid package name in the existing repo list before doing anything with it...  Also all the packages actually install through synaptic this is just an easy way or selecting a package

---

### Post by KillerKiwi on 2006-07-14
> **scenestar said:**
> No offense, but this is kinda redundant and not very spectacular at all.

**What you are are trying to do can be easily be achieved using shell scripts and zenity.**

It is however a nice way to handle all those 



boxes on the forums, but really it isn't groundbreaking development.

Ground breaking no, helpful to newbies? I think it would be

btw shell scripts and zenity is exactly how klik handles this, although this is differnt to klik as it does not link to any third party binarys

---

### Post by manicka on 2006-07-14
> **KillerKiwi said:**
> Ground breaking no, helpful to newbies? I think it would be

btw shell scripts and zenity is exactly how klik handles this

so am I understanding this correctly, this script is a front end for klik.

I don't think you can get any easier than clicking on a deb and requesting it to be opened with gbebi

---

### Post by KillerKiwi on 2006-07-14
> **scenestar said:**
> No offense, but this is kinda redundant and not very spectacular at all.

**What you are are trying to do can be easily be achieved using shell scripts and zenity.**

It is however a nice way to handle all those 



boxes on the forums, but really it isn't groundbreaking development.

> **manicka said:**
> so am I understanding this correctly, this script is a front end for klik.

I don't think you can get any easier than clicking on a deb and requesting it to be opened with gbebi

No!, this script is JUST a front end for synaptic simiar to how gnome-application-install works.  

Klik actually downloads binary from the web where as this just triggers synaptic to do its usual thing.

---

### Post by neymac on 2006-07-14
Linspire (former Lindows) does some like this, if you pay for their services.
They call it CNR (click n' run).
You can see at [http://www.linspire.com/products_cnr_whatis.php](http://www.linspire.com/products_cnr_whatis.php)

---

### Post by scenestar on 2006-07-14
> Im not going to claim this is fool proof at the moment but it does check to see if the passed parameter is a valid package name in the existing repo list before doing anything with it... Also all the packages actually install through synaptic this is just an easy way or selecting a package

As a hacker I am going to say this once.

Do it right or don't bother at all.

I don't give a **** how easy it is.

You are allowing others to compromise linux systems.

Fscking end this bullshit or people are going to get pwned

---

### Post by 3rdalbum on 2006-07-15
Great idea, and for such a young project it is well implemented (as far as I can see). I don't see the security risk in installing something from the official Ubuntu repositories, as long as the user is told the actual package name that is being installed.

---

### Post by hornett on 2006-07-15
> **scenestar said:**
> As a hacker I am going to say this once.

Do it right or don't bother at all.

I don't give a **** how easy it is.

You are allowing others to compromise linux systems.

Fscking end this bullshit or people are going to get pwned


Sorry if I'm missing the point here but how is clicking a link to install worse than being told the name of a package to install on a forum?

---

### Post by manicka on 2006-07-15
> **KillerKiwi said:**
> No!, this script is JUST a front end for synaptic simiar to how gnome-application-install works.  

In this case, I don't see any difference between firing up a web browser or gnome-application-install. If both do essentially the same job it seems like a reinvention of the wheel to me.

---

### Post by ewl1217 on 2006-07-15
Personally, I think this would be a great idea. I don't see why everyone sees this as a security issue because it only installs software that's in the repositories. Barring any bugs, this wouldn't allow for anyone to install software outside of the repositories,so this is really just as secure as Synaptic. We just need a dialog box to make sure that users actually know what they are installing, so someone can't trick a user into installing edubuntu-desktop, kubuntu-desktop, and xubuntu-desktop, or anything crazy like that.

Also, I think this would be great for migrating Windows and Mac users. They're so used to going to a website to download the software they want. They would never think to use Synaptic simply because they're not used to that. It would also help keep new users out of the terminal, which none of them are familiar with.

---

### Post by IbeeX on 2006-07-15
Nice idea

only I am using aptitude! Will it suport it? :KS

---

### Post by scenestar on 2006-07-15
Why this whole clink thing is a very bad idea in its current form
Since the protocol is installed as a regular user and not as root i can simply use a remote exploit for mozilla to replace the protocol handler (install_hacked_handler.sh)

so as a quick example

lets say someone runs an old unupdated firefox

I use the exploit found at [http://www.milw0rm.com/id.php?id=1474](http://www.milw0rm.com/id.php?id=1474)

to install install a new handler

----install_hacked_handler.sh----

> #!/bin/bash
LOCATION=`pwd`


gconftool-2 -t string -s /desktop/gnome/url-handlers/install/command "$LOCATION/**install-hacked-protocoll_handler.py** %s"
gconftool-2 -t bool -s /desktop/gnome/url-handlers/install/enabled true
gconftool-2 -t bool -s /desktop/gnome/url-handlers/install/needs_terminal false

-------

It really is that simple to hijack it without any security mechanism holding me back.

Now here is the part where I can do the juicy things.
The protocol handler asks the user for admin priviledges effectively giving me root.

for the hell of it lets place the sources.list file 


All I have to do is add  
> 
import shutil
shutil.copyfile(evilsources.list, /etc/apt/sources.list)

to install-hacked-protocol_handler.py after the user has given permission for the script to execute.

I can now effectively have the user install my own (trojanised) binaries.
**It will take some time before the user finds out while serious damage can be done.**


other funky ideas are having the protocol handler startup vnc deamons or upload their personal files to a remote ftp.

This is probably a bit of an unclear explanation but right now I'm too hungover to go into it more indepth.

---

### Post by lime4x4 on 2006-07-15
just curious if someone installs this and then decides they no longer want it how do u uninstall?

---

### Post by Hg80 on 2006-07-15
seems like a great idea, would like to see more point and click as this is the only way linux will become main stream, i know for a fact my non geek ideas hate the way i install software under linux and as such will not try it

---

### Post by KillerKiwi on 2006-07-15
> **scenestar said:**
> Why this whole clink thing is a very bad idea in its current form
Since the protocol is installed as a regular user and not as root i can simply use a remote exploit for mozilla to replace the protocol handler (install_hacked_handler.sh)

so as a quick example

lets say someone runs an old unupdated firefox

I use the exploit found at [http://www.milw0rm.com/id.php?id=1474](http://www.milw0rm.com/id.php?id=1474)

to install install a new handler

----install_hacked_handler.sh----



-------

It really is that simple to hijack it without any security mechanism holding me back.

Now here is the part where I can do the juicy things.
The protocol handler asks the user for admin priviledges effectively giving me root.

for the hell of it lets place the sources.list file 


All I have to do is add  


to install-hacked-protocol_handler.py after the user has given permission for the script to execute.

I can now effectively have the user install my own (trojanised) binaries.
**It will take some time before the user finds out while serious damage can be done.**


other funky ideas are having the protocol handler startup vnc deamons or upload their personal files to a remote ftp.

This is probably a bit of an unclear explanation but right now I'm too hungover to go into it more indepth.

I see your point :) , I'm guessing that the mailto protocol etc get around this by installing as root.  So guess that would be the best option...

Thanks for the helpful feed back

EIDT: Also whats stopping you from doing this with mailto, http etc as they are also just keys in gconf?

Ie some one with an evil mind could replace the mailto protocol with a call to a script...

---

### Post by KillerKiwi on 2006-07-15
> **lime4x4 said:**
> just curious if someone installs this and then decides they no longer want it how do u uninstall?

Just remove the gonf keys and delete the files

```
gconftool-2 -u /desktop/gnome/url-handlers/install/command
gconftool-2 -u /desktop/gnome/url-handlers/install/enabled 
gconftool-2 -u /desktop/gnome/url-handlers/install/needs_terminal
```

---

### Post by scenestar on 2006-07-19
> EIDT: Also whats stopping you from doing this with mailto, http etc as they are also just keys in gconf?

Because sending an email doesn't have the same impact for the system as installing new software.

---

### Post by brentoboy on 2006-07-19
this is all perfectly simple stuff to avoid.
install the script as root, and dont allow things to read/write it.

only install things that are already in the sources list.
--
as far as "is it easier"
**YES, IT IS**

I dont *need* it, per se, but it is certainly more convenient to click a link and enter my password to install software package such and such.  rather than opening synaptic and finding it and installing it.  more steps = anoying.

its a great idea, it just needs to be given careful security considreation before it is released to the general public.

as a software vendor, I would love to be able to eliminate all the install instructions, and just say  click here to install programX.  and be done with it.

---

### Post by scenestar on 2006-07-19
> as far as "is it easier"
YES, IT IS


Here's an idea for you, open an terminal and su to root.

Cut and pasting commands into a terminal is way easier than having to click around.

Whenenever I use windows the lack of a proper shell and being locked into a point click gui makes me cringe.

Let's not introduce this crap into linux.

Instead of coming up with these godawful hacks you could just get rid of that windows mindset and learn to accept that some "ease of use" will eventually severly affect your own productivity.

---

### Post by brentoboy on 2006-07-19
cutting and pasting into a terminal is what I do now.

it works great for me.

but I have to admit, clicking is faster than cutting and pasting and all that stuff.

and, a nice site, like the unnofficial ubuntu guide, could just have click here links instead of things to enter into the terminal.

no one is forcing you to use it.

this makes it possible for some nice guy to catalog the packages already built into ubuntu, say for games.  He could make a wonderful screenshot for each, a big -- search by game type... and then, when you find one you are interested in, just click "install me"

it aint about "windows" vs "unix" it is about doing things in a way that requires only as much effort as needs to be required.

I dont mind su-ing to root and installing stuff, or even adding things to my sources.list, or editing my own xorg.conf file using nano, but my father, mother, sister, wife, brother-in-law, etc who I support as their "how do I..." guy, this sounds really wonderful, and it would make people really warm up to using ubuntu.

---

### Post by brentoboy on 2006-07-19
> **scenestar said:**
> 
Whenenever I use windows the lack of a proper shell and being locked into a point click gui makes me cringe.


from windows start -> run -> cmd
there's your command prompt.

try it out.  it works great, especially if you remember dos.
(oh, its ipconfig, not ifconfig  and you can use dir instead of ls -- it takes some getting used to, but if you use it for a while, you can go back and forth without any real hickups.)

if you dont like it, dont use it.

--

If you like to use the command line and text editors for everything, use slackware, I here it is faster, and you never have to be bothered by a gui, click-me again.

---

### Post by KillerKiwi on 2006-07-19
> **brentoboy said:**
> 

as a software vendor, I would love to be able to eliminate all the install instructions, and just say  click here to install programX.  and be done with it.


What would be really nice (thinking in the what if universe here), is if every distro had a install protocol linked to thier own package managment system..... software sites could then have

Linux install instructions : click here

---

### Post by airtonix on 2006-07-19
scenstar, right one dude.
brentboy, your logic is flawed, ubuntu is secure because of the way you use it, it is that way because the majority are wanting it that way, if you make this a standard, unsecure users and their habits will become the standard. Thus ubuntu will move into the realm of becoming unsecure.
simple algorythm of momentum, balance and attraction.

And for this to be useful to the linux way of doing things, it needs to have the same information ready to show instantly like when your using the update manager.

It needs to show what servers the packages are coming from

it most absolutley needs to winge and cry when the pgp,md5 or whatever verfication fails.

but if you want to host your own, all you do is put the deb files on your webserver and make links to those files....easy.

---

### Post by Third Thoughts on 2006-07-19
I have to admit, I'm a complete ignoramus when it comes to the technical argument that's going on here. But it sems to me scenestar has a point in terms of the issue of habit forming. If this app becomes widely adopted we'll be training newbies to give their root password out after clicking on a link. It seems to me that sort of training could be abused by those with malice on their minds. Even if there are no security issues with the software itself, the practices it promotes seem unsecure.

~Andrew S.

---

### Post by airtonix on 2006-07-24
Humans are habitually ritualistic. lol...So by concentrating on changing the dominant cultural conditioning as being the only kind, would really be a helpful step towards enriching our gene pool.

Too often the leaders are complacent and are quick to defend their luxury....slow to give meaningful direction for the society in their charge. But once in while they quip up with substance, which upon closer inspection it turns out to be none other than that which would fill their pockets.

Viz: It is in microsofts interest that windows users become habitually dependant on the mantra/doctrine consistantly repeated through out the theme, behaviour and perception of computer networks that it projects to the user. mmm bit like all the guff that decorates a temple(whatEverFlavour,whatEverRank,whatEverStahn).

end rant.

---

### Post by brentoboy on 2006-07-25
> **airtonix said:**
> 
brentboy, your logic is flawed

I cant disagree with that.  :)
> 
ubuntu is secure because of the way you use it, 

No, it is secure becaue of the way it is shipped by default (closed ports)  and because developers actualy think about the security ramifications of their actions.
> 
it is that way because the majority are wanting it that way,

that is interesting, becuase the majority seem to be on my side of the issue if you look up at the poll.
> 
if you make this a standard, unsecure users and their habits will become the standard. Thus ubuntu will move into the realm of becoming unsecure.

there is nothing insecure about allowing a link on a website to make it easy to download and install applications that are already in trusted repostiroties.  Nowhere does it say that a link would be able to add a repo, or even send their own deb file  as though it was trusted!  that would be silly.
> 
simple algorythm of momentum, balance and attraction.

so simple that I have no idea what you are talking about
> 
And for this to be useful to the linux way of doing things, it needs to have the same information ready to show instantly like when your using the update manager.

what... please clarify what you mean -- I dont follow at all.
> 
It needs to show what servers the packages are coming from

no, it just needs to be limited to the servers already listed in the sources.list.  And if it isnt trusted, it could potentially tell you what repo you would have to add if you wanted it to work. (assuming it wasnt in there already)
> 
it most absolutley needs to winge and cry when the pgp,md5 or whatever verfication fails.

ok, I cant disagree there, but, doesnt it already?  The proposed idea just uses apt-get to get the package, which cries and whines if things arent right, as does synaptic.    All this little feature is doing is typeing gksudo apt-get install foo for you.  All the built in safegaurds arent thrown out just becuase it is easy to do.
> 
but if you want to host your own, all you do is put the deb files on your webserver and make links to those files....easy.

no, becuase this little feature only downloads things from trusted repo's. man, read the details before you post.

---

### Post by scenestar on 2006-07-29
> if you dont like it, dont use it.

I left windows a long long time ago. Command.com is completely useless.
Come back once you can come up with a proper POSIX alternative.
> 
No, it is secure becaue of the way it is shipped by default (closed ports) and because developers actualy think about the security ramifications of their actions. 

This includes teaching users proper system administration.

For a so called "software vendor" your arguments are fsckin godawfull.

---

