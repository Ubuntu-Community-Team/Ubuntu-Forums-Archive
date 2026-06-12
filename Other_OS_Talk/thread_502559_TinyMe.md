---
title: "TinyMe"
date: 2007-07-16
forum: Other OS Talk
---

### Post by RAV TUX on 2007-07-16
[http://tinyme.mypclinuxos.com/](http://tinyme.mypclinuxos.com/)

Anybody try out TinyMe?

> **Mini Review of a Tiny PCLOS**

                                                 Submitted by srlinuxx on Mon, 07/02/2007 - 03:35.[LIST]
[*][pclos]("http://www.tuxmachines.org/taxonomy/term/107")
[*][Reviews]("http://www.tuxmachines.org/taxonomy/term/101")
[*][-s]("http://www.tuxmachines.org/taxonomy/term/102")[/LIST][[IMG]http://www.tuxmachines.org/gallery/d/27422-2/41.jpg[/IMG]]("http://www.tuxmachines.org/gallery/v/tinyme/41/desktop.jpg.html")TinyMe is a scaled down version of PCLinuxOS 2007. The latest version is delivered as a 177 MB liveCD and features the Lightweight X11 Desktop Enviroment, Synaptic, and the PCLinuxOS Control Center. It comes with a few applications, so it could be a really light version of PCLOS for older computers or a foundation on which to build your own system as you choose.
 The boot screen and silent boot splash are straight from PCLOS, but the window manager login screen is quite different. TinyMe 4.1 comes with LXDE and Openbox and so the LXSession is the graphical login manager. It works well and looks fairly good, but has some extraneous entries listed. The LXdesktop is a standard setup: a panel at the bottom with a start button and some quick launchers, pager, clock and network applet. TinyMe developers have included a nice wallpaper of rain drops on glass with a blue sky background. The TinyMe acorn logo sits in the middle. It didn't scale for my 1280x800 screen resolution, but no biggie. Version 4.1 comes with a Home icon and gkrellm.
 The menus are quite sparce, but most applications installed end up with link. As delivered, GQView is included as for image viewing and medit for text editing or simple document creation. The Settings heading contains About Me, Password, Redo MBR, and Openbox Configuration Manager. System tools include Configure Your Computer (PCLOS Control Center), Disk Management, PCMan File Manager, Root Terminal, Run as Different User, Searchmonkey, and Synaptic Package Manager. Under Network is Opera and TightVNC. Under the hood we find Linux 2.6.18.8, Xorg 7.1.1, and GCC 4.1.1.
 [[IMG]http://www.tuxmachines.org/gallery/d/27437-2/stuff1.jpg[/IMG]]("http://www.tuxmachines.org/gallery/v/tinyme/41/stuff1.jpg.html")
Some Stuff There is no entry in the menu for the hard drive installer, but it can be found at /usr/sbin/draklive-install. It is the same PCLOS customized Mandriva Live installer found in PCLinuxOS and works just as well. With such a small system to install, it finished in just a few minutes. I setup the bootloader to be installed onto the root partition and that worked out really well. I had no problems with any of it.
 The installed system boots on my laptop in 19 seconds and takes up about 700 MB of space. I opened Synaptic to install a few things and found PCLOS software repositories already set up. The Gimp I installed while running the liveCD was transferred to the harddrive install and I followed it up with Gnome. I wasn't able to locate a Gnome meta package so I checked most of the important Gnome packages. It downloaded about 150 MB of software and installed without issue. Gnome didn't show up in the LXSession menu, so I had to choose Text.Console and start it manually. One could probably install the Gnome login manager if they seriously wanted to use Gnome. I just speculated that this TinyMe might be the perfect start for the user wishing to run PCLOS under the Gnome desktop without any of the KDE baggage that's so hard to remove completely. And my results were such that I believe it would work out well for that very purpose. Even with Gnome installed the system still weighed in at less than one gig. Apps opened immediately and the system as a whole was very stable.
 [[IMG]http://www.tuxmachines.org/gallery/d/27505-2/gnome.png[/IMG]]("http://www.tuxmachines.org/gallery/v/tinyme/3x/gnome.png.html")
Gnome TinyME might make a good start for a server as all the important LAMP packages are in the PCLOS repositories as well. One doesn't need all the extra goodies that come with the big desktops these days for a server and LXDE would be good for those that like graphical server tools such as webmin. 
 I didn't have an older computer handy on which to test it, but I imagine it would be great for it. PCLOS developers build support for about everything into their kernels and LXDE only requires a Pentium II and 128 MB ram if one wishes to use like Firefox or OpenOffice.org. It is said that LXDE alone can run in as little as 64 MB ram.
 TinyME might be useful to those folks that commonly use ftp or net installs because they prefer to only download what they use. This way, they can still test hardware support before installing without downloading 700 MB.
 As it was on my modern HP laptop, hardware support was great. My sound, graphics, and wired ethernet chip were auto-configured. For my wireless chip I easily used Ndiswrapper to load the drivers and had no issue with WPA or WEP. Battery monitoring and cpufreq were accomplished at the commandline as well with the default system. Removeable media is seen, but there are issues with the file manager. Directories show up in PCMan, but clicking on them shot an error. Other media, such as ondisk partitions mounted and opened without issue just by clicking on them.
 All in all, it's a fairly neato little image. It's fun to play with as it is or could be a great start to your very own system. See some more [screenshots in the gallery]("http://www.tuxmachines.org/gallery/v/tinyme/").  Visit the [TinyMe Homepage]("http://tinyme.mypclinuxos.com/") for downloads.


[http://www.tuxmachines.org/node/17717](http://www.tuxmachines.org/node/17717)

---

### Post by exploder on 2007-07-16
I tried Tinyme on an old PIII 500 system, it shows real promise. Tinyme also looks very nice compared to other operating systems of this type.

---

### Post by xpod on 2007-07-17
I`m gonna have a wee look myself.
I`m currently downloading so i`ll see for myself what it`s like shortly.

It`ll be going on(?) the old Dell c600 i have here which only has 128Mb & 700Mhz.
Puppy runs great on it so i`m hoping this is on par with that to some degree.

I`ve actually ordered a bit more RAM for it just to run Ubuntu but i dont even know why i bothered,theres so many of these little disrto`s out that are perfect for the job.

It`s only downloaded quicker than i wrote the post so here goes.....

---

### Post by DreamcastJack on 2007-07-17
i'm gonna give it a shot later today.  already d/led the ISO.

---

### Post by xpod on 2007-07-17
lol...it took nearly two minutes before i got to login screen ......with homers lovely xray:)
It then took another 20.30 secs getting to the desktop.:(

Set my nic for the static ip this particular line uses but when i try use Mozilla to get online nothing at all happens

Trying to start synaptic but it wont accept the root password i reckoned i`d set at the logon screen.Tried "tiny" which is the one i set plus just "root" itself but obviously i need to go read some docs

I like the desktop wallpaper,It`s the closest i`ve been to any "rain effect" even with beryl & compiz(no pixel shading apparently)

Looks good although puppy is just sooooo much quicker it seems(even from cd)
I`ll play about with it for the rest of the night and see how it goes.

Just need to find that root password first...:rolleyes:

EDIT:Now why does that image of homers skull seem sooo damn appropriate.
Anyway,i`m currently posting this just fine from opera via tinyme:)
Heres hoping it`s a wee bit faster once installed.

---

### Post by RAV TUX on 2007-07-17
> **xpod said:**
> lol...it took nearly two minutes before i got to login screen ......with homers lovely xray:)
It then took another 20.30 secs getting to the desktop.:(

Set my nic for the static ip this particular line uses but when i try use Mozilla to get online nothing at all happens

Trying to start synaptic but it wont accept the root password i reckoned i`d set at the logon screen.Tried "tiny" which is the one i set plus just "root" itself but obviously i need to go read some docs

I like the desktop wallpaper,It`s the closest i`ve been to any "rain effect" even with beryl & compiz(no pixel shading apparently)

Looks good although puppy is just sooooo much quicker it seems(even from cd)
I`ll play about with it for the rest of the night and see how it goes.

Just need to find that root password first...:rolleyes:

EDIT:Now why does that image of homers skull seem sooo damn appropriate.
Anyway,i`m currently posting this just fine from opera via tinyme:)
Heres hoping it`s a wee bit faster once installed.Got a screenshot?

---

### Post by DreamcastJack on 2007-07-18
> **xpod said:**
> lol...it took nearly two minutes before i got to login screen ......with homers lovely xray:)
It then took another 20.30 secs getting to the desktop.:(

Set my nic for the static ip this particular line uses but when i try use Mozilla to get online nothing at all happens

Trying to start synaptic but it wont accept the root password i reckoned i`d set at the logon screen.Tried "tiny" which is the one i set plus just "root" itself but obviously i need to go read some docs

I like the desktop wallpaper,It`s the closest i`ve been to any "rain effect" even with beryl & compiz(no pixel shading apparently)

Looks good although puppy is just sooooo much quicker it seems(even from cd)
I`ll play about with it for the rest of the night and see how it goes.

Just need to find that root password first...:rolleyes:

EDIT:Now why does that image of homers skull seem sooo damn appropriate.
Anyway,i`m currently posting this just fine from opera via tinyme:)
Heres hoping it`s a wee bit faster once installed.

the live cd booted up rather quickly for me. and I absolutely loved it. I wont be installing it over PCLOS.. but man its nice.

---

### Post by xpod on 2007-07-18
> Got a screenshot?

Sorry rav,i forgot how much you like your screenies.:wink:

[ATTACH]38520[/ATTACH]

[ATTACH]38521[/ATTACH]

[ATTACH]38522[/ATTACH]

Nothing fancy i`m afraid....not that this old things capable of anything fancy mind you:)
Done the complete install without a hitch and it now boot`s to login in around 30 secs and a further 10 mabey before the desktop appears.

Everything seems to be working okay(that i`d ever use)but i`m not sure what the score is with the sloooow synaptic???
It seems to take quite a while for stuff to install from synaptic for some reason,i`m talking like 5 minutes before synaptic finishes what it`s doing in the cases so far....nfs, gimp & amsn.

> the live cd booted up rather quickly for me. and I absolutely loved it. I wont be installing it over PCLOS.. but man its nice.

Yeah,it`s a lot faster on my other machines at booting up but i was kinda hoping it`d be on par with puppies boot times on here.

No big deal though and overall it seems like a really nice distro for anyone low on oomph.
Being a mini PCLinuxOS it`s so simple to use & setup and even a first timer would`nt have too much trouble finding their way around i dont think.

My lads also installed it on his own machine  and he aint shouted on me so far ....tick tock:)

EDIT:Problems so far

When i first installed yesterday the Tinyme grub setup failed to pick up Puppy or Ubuntu(or I failed) which are also on the machine.
After editing the menu.lst accordingly all 3 worked great.Booting the pc today though the UBuntu option had just vanished from grubs list of options.
Puppy was still available but Ubuntu had been eaten apparently....:)

Cant complain though i suppose as it`s the first  grub problem i`ve  actually had.
Another curioisty is a proper shutdown option.I can only "log off" back to the logon screen but theres no option there or the desktop for just shutting down or rebooting?
A great feature for you guy`s who never switch your computers off it seems.

---

### Post by RAV TUX on 2007-07-18
> **xpod said:**
> Sorry rav,i forgot how much you like your screenies.:wink:

[ATTACH]38520[/ATTACH]

[ATTACH]38521[/ATTACH]

[ATTACH]38522[/ATTACH]

Nothing fancy i`m afraid....not that this old things capable of anything fancy mind you:)
Done the complete install without a hitch and it now boot`s to login in around 30 secs and a further 10 mabey before the desktop appears.

Everything seems to be working okay(that i`d ever use)but i`m not sure what the score is with the sloooow synaptic???
It seems to take quite a while for stuff to install from synaptic for some reason,i`m talking like 5 minutes before synaptic finishes what it`s doing in the cases so far....nfs, gimp & amsn.



Yeah,it`s a lot faster on my other machines at booting up but i was kinda hoping it`d be on par with puppies boot times on here.

No big deal though and overall it seems like a really nice distro for anyone low on oomph.
Being a mini PCLinuxOS it`s so simple to use & setup and even a first timer would`nt have too much trouble finding their way around i dont think.

My lads also installed it on his own machine  and he aint shouted on me so far ....tick tock:)

EDIT:Problems so far

When i first installed yesterday the Tinyme grub setup failed to pick up Puppy or Ubuntu(or I failed) which are also on the machine.
After editing the menu.lst accordingly all 3 worked great.Booting the pc today though the UBuntu option had just vanished from grubs list of options.
Puppy was still available but Ubuntu had been eaten apparently....:)

Cant complain though i suppose as it`s the first  grub problem i`ve  actually had.
Another curioisty is a proper shutdown option.I can only "log off" back to the logon screen but theres no option there or the desktop for just shutting down or rebooting?
A great feature for you guy`s who never switch your computers off it seems.so would you say you like it better then Puppy?

---

### Post by DreamcastJack on 2007-07-18
> **RAV TUX said:**
> so would you say you like it better then Puppy?

my experience I liked it better than Puppy.  puppy is a little faster not much more though.

---

### Post by dptxp on 2007-07-19
I tried to install Puppy twice, on two different machines (2.15). I had Ubuntu and XP on them, puppy did not do justice to the GRUB.

It is a bit poor on net connectivity too, needs manual configuration (DSL modem, LAN).

---

### Post by xpod on 2007-07-19
> so would you say you like it better then Puppy?

(climbs on the fence)....I would`nt say i like one too much better than the other RT as their both great little disto`s in their own right:)
For speed alone it has to be Puppy,Puppy boots faster,loads apps faster and allows me to install stuff from the package manager a hell of a lot faster too.
For some reason synaptic takes forever in Tinyme,It`s actually quicker booting Tiny than what it is loading synaptic and installing anything takes a seriously long time to complete.....shockingly long it feels like.

I`ve just installed vlc and all it`s depedancies and it`s taken about  7-8 minutes to complete.
Just downloading may take longer for many users of course so the times are only relative to my own  experiences.

If i _had_ to actually choose ,then i`d still stick with puppy just now i think.

> I tried to install Puppy twice, on two different machines (2.15). I had Ubuntu and XP on them, puppy did not do justice to the GRUB.

It is a bit poor on net connectivity too, needs manual configuration (DSL modem, LAN).

I was the same with Puppy and Tinyme.The both failed to detect the other distos during  grub setup so i had to do it all myself.

I would`nt exactly call it "poor" but Tinyme was the same as Puppy in that we have to set auto dhcp manually.:???:Simple enough to do in both though so not really an issue
I use a static ip on this particular Tinyme install so would do that manually anyway but my lad also had to chase the settings down for his auto dhcp connection.

---

### Post by RAV TUX on 2007-07-19
> **xpod said:**
> (climbs on the fence)....I would`nt say i like one too much better than the other RT as their both great little disto`s in their own right:)
For speed alone it has to be Puppy,Puppy boots faster,loads apps faster and allows me to install stuff from the package manager a hell of a lot faster too.
For some reason synaptic takes forever in Tinyme,It`s actually quicker booting Tiny than what it is loading synaptic and installing anything takes a seriously long time to complete.....shockingly long it feels like.

I`ve just installed vlc and all it`s depedancies and it`s taken about  7-8 minutes to complete.
Just downloading may take longer for many users of course so the times are only relative to my own  experiences.

If i _had_ to actually choose ,then i`d still stick with puppy just now i think.



I was the same with Puppy and Tinyme.The both failed to detect the other distos during  grub setup so i had to do it all myself.

I would`nt exactly call it "poor" but Tinyme was the same as Puppy in that we have to set auto dhcp manually.:???:Simple enough to do in both though so not really an issue
I use a static ip on this particular Tinyme install so would do that manually anyway but my lad also had to chase the settings down for his auto dhcp connection.

I would like to know how you find [Wolvix]("http://wolvix.org/") and [Wolvix Cub]("http://wolvix.org/") compare to Puppy and TinyMe?

---

### Post by DreamcastJack on 2007-07-20
is this recent release of TinyMe a final or just beta?

---

### Post by Frak on 2007-07-20
Haven't tried it yet, but I know have a very strong urge too. :D

---

### Post by xpod on 2007-07-20
> I would like to know how you find Wolvix and Wolvix Cub compare to Puppy and TinyMe?

Tried cub in a virtual machine at first but kept getting weird characters as i tried to type the user/password in.
So...burned to disk and gave it a whirl(from cd) on the same old Dell as the tinyme/puppy installs.

It booted to Logon in aboout 40 seconds with another 15 to either the flux or xfce desktops
Everything feels a lot snappier than tinyme but i`d really  need to install it i think.

The first thing i would normally do is find a network manager and set my dhcp/static ip accordingly but nowhere in either of the desktops is there any kind of network manager applet.:confused:
[ATTACH]38679[/ATTACH]               [ATTACH]38680[/ATTACH]
[ATTACH]38681[/ATTACH]               [ATTACH]38682[/ATTACH]

The laptop uses a static ip so just out of curiosity i tried the cub virtual machine again,the Ubuntu machine it`s  on has 2 nic`s with one for incoming internet via dhcp(the other used for sharing net etc).
The cub live cd running inside the vm  has obviously detected the dhcp on eth1 ok as i can get online with firefox just fine..

Bar that though it`s all looking good.It has all the basics anyone could need and unlike tiny me you can even turn the thing off.

You`ve just gave me a dillema as to which of these little things i should use on that old Dell:)
I have extra memory for it so running ubuntu etc would`nt be a problem......but.:-k

What do *you* thinks better??

---

### Post by Wiebelhaus on 2007-07-20
OMG , I'm sure it's nice and I thank whomever put the time into it  but for crying out loud , do we need another distro....seriously.

---

### Post by xpod on 2007-07-20
> OMG , I'm sure it's nice and I thank whomever put the time into it but for crying out loud , do we need another distro....seriously.

OMG
I dont see what the problem is personally???
Try it, or not...use it, or dont.

As far as Tinyme is concerned i`m sure the PCLiuxOS lovers with crappy old machines would love to have a scaled down version of their favorite disto,thats just an opinion of course.  
I thought the whole point of "open souce" though was so people could make "another distro" if they so pleased or anything else besides so i dont really see what the issue is.

Good luck to them all i say.
Mines is not to reason why....mines is but to do or try:wink

EDIT Was Ubuntu "needed" prior to it`s release i wonder...some would say not apparently.

---

### Post by RAV TUX on 2007-07-20
> **xpod said:**
> Tried cub in a virtual machine at first but kept getting weird characters as i tried to type the user/password in.
So...burned to disk and gave it a whirl(from cd) on the same old Dell as the tinyme/puppy installs.

It booted to Logon in aboout 40 seconds with another 15 to either the flux or xfce desktops
Everything feels a lot snappier than tinyme but i`d really  need to install it i think.

The first thing i would normally do is find a network manager and set my dhcp/static ip accordingly but nowhere in either of the desktops is there any kind of network manager applet.:confused:
[ATTACH]38679[/ATTACH]               [ATTACH]38680[/ATTACH]
[ATTACH]38681[/ATTACH]               [ATTACH]38682[/ATTACH]

The laptop uses a static ip so just out of curiosity i tried the cub virtual machine again,the Ubuntu machine it`s  on has 2 nic`s with one for incoming internet via dhcp(the other used for sharing net etc).
The cub live cd running inside the vm  has obviously detected the dhcp on eth1 ok as i can get online with firefox just fine..

Bar that though it`s all looking good.It has all the basics anyone could need and unlike tiny me you can even turn the thing off.

You`ve just gave me a dillema as to which of these little things i should use on that old Dell:)
I have extra memory for it so running ubuntu etc would`nt be a problem......but.:-k

What do *you* thinks better??

Install Wolvix it is simply awesome the Dev is awesome and it is based on Slackware. Everybody I have recommended to it has fallen in love with it. ;)

---

### Post by xpod on 2007-07-20
> Install Wolvix it is simply awesome the Dev is awesome and it is based on Slackware. Everybody I have recommended to it has fallen in love with it. 

It was installed some hours ago now...about 10 minutes after i first tried it in the VM again in fact.:)
I`ve not really done much with it since though as my own wee cubs(girls) are just back from  holiday so it`s been a wee bit hectic to say the least.

Anyway RT ,do you know what the script is with the missing network manager??
What is everyone using to configure nic`s? or are they all happy with dialup and the auto dchp that seemingly works out the box.:)

I`ll figure it out tommorow as i`ts past my bed time.

---

### Post by RAV TUX on 2007-07-21
> **xpod said:**
> It was installed some hours ago now...about 10 minutes after i first tried it in the VM again in fact.:)
I`ve not really done much with it since though as my own wee cubs(girls) are just back from  holiday so it`s been a wee bit hectic to say the least.

Anyway RT ,do you know what the script is with the missing network manager??
What is everyone using to configure nic`s? or are they all happy with dialup and the auto dchp that seemingly works out the box.:)

I`ll figure it out tommorow as i`ts past my bed time.


Auto dchp has always worked for me.

You can ask the Dev directly, at #wolvix on freenode about your question. Also [bodhi.zazen]("http://ubuntuforums.org/member.php?u=89054") who is a Mod here also uses Wolvix and is probably more fimiliar then I if you have any technical questions.

Glad you like Wolvix. Wolvix has gained a awesome community of loyal users, primarily because so much care is put into it.

---

### Post by xpod on 2007-07-21
> Auto dchp has always worked for me.

You can ask the Dev directly, at #wolvix on freenode about your question. Also bodhi.zazen who is a Mod here also uses Wolvix and is probably more fimiliar then I if you have any technical questions.

Glad you like Wolvix. Wolvix has gained a awesome community of loyal users, primarily because so much care is put into it.

Problem solved....
Auto dhcp works great on it but on this release setting the static ip`s & dns servers that i need to use is`nt too simple.

I found the "netconfig" tool at the terminal which let me do the static ip,subnet mask & gateway ok but nowhere for the alternative dns servers which i need on that line.Found a couple of  solutions though...

[http://wolvix.org/node/449](http://wolvix.org/node/449)

EDIT:Just downloaded the 1.1.0 RC2 which has a more fully featured control panel it seems....incliding the missing network manager amonst others:)
Works fine(online with static ip)from cd sooo.....on it goes(in place on 1.0.5).

---

### Post by urukrama on 2007-12-27
I installed TinyMe on a spare computer I have. It is a very nice Openbox distrubution. Though it took me a while to get installed, and crashed on me twice once it was installed, I find it quite polished. TinyMe comes with some neat configuration windows and settings (which I assume come from its parent distro, PCLinuxOS?). Very fast too.

I find it a very  (new-) user friendly distro, and I'm quite confident it will have matured by the time it reaches a stable version. This is definitely a distro I will keep an eye on.

I liked it a lot more than Fluxbuntu.

---

### Post by LaRoza on 2007-12-27
[http://pcfluxboxos.wikidot.com/tinyflux](http://pcfluxboxos.wikidot.com/tinyflux)

TinyFlux is another good PCLinuxOS based OS

---

