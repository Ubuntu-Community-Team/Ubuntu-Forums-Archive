---
title: "Suggestions: Changes and Additional Packages to be made for the next Ubuntu release"
date: 2011-05-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sostentado on 2011-05-16
I'll start!

I want Gnome Shell to be stable. I mean, no bugs! :))

---

### Post by Johnsie on 2011-05-16
Gambas3

---

### Post by Lucradia on 2011-05-16
Remove shotwell, and put GIMP back in.

Remove Empathy, put Pidgin back in, the indicator applet now accepts pidgin. (Only reason why Ubuntu doesn't want Pidgin back is because the devs won't use encryption: [http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords), until someone does it for them. Also, see the list (which includes Windows Live Messenger 2011) of IM Clients that don't actually use encryption.)

---

### Post by FuturePilot on 2011-05-16
> **sostentado said:**
> I'll start!

I want Gnome Shell to be stable. I mean, no bugs! :))

Good luck finding anything with no bugs.

---

### Post by Lucradia on 2011-05-16
> **FuturePilot said:**
> Good luck finding anything with no bugs.

Plus one.

Nothing is without bugs to be honest.

---

### Post by RiceMonster on 2011-05-16
> **Lucradia said:**
> Plus one.

Nothing is without bugs to be honest.

I hope at the very least your food is.

---

### Post by tmette on 2011-05-16
> **lucradia said:**
> remove shotwell, and put gimp back in.

Remove empathy, put pidgin back in, the indicator applet now accepts pidgin. (only reason why ubuntu doesn't want pidgin back is because the devs won't use encryption: [http://developer.pidgin.im/wiki/plaintextpasswords](http://developer.pidgin.im/wiki/plaintextpasswords), until someone does it for them. Also, see the list (which includes windows live messenger 2011) of im clients that don't actually use encryption.)

+1

---

### Post by ZarathustraDK on 2011-05-16
- 7zip installed by default
- +1 on the Gimp
- Tear out gnome-games-package, there are fresher games out there
- Guayadeque instead of Banshee
- VLC instead of Totem
- Qalculator instead of Calculator
- Thunderbird instead of Evolution
- Integrate wicd instead of current network-config-thingy
- Deluge instead of Transmission

Overall: There are too many Gnome-apps installed by default simply because they're Gnome-apps. Go for the "best of breed" and let the Gnome-folk focus on the DE/WM instead of how a select group of applications integrate with it. I recon Unity will focus a lot on that particular aspect. Too many cooks and all that.

In my fantasy-future:
- Wayland handling graphics perfectly instead of Xorg
- Nouveau and OSS ATI-drivers on par with their proprietary ethos
- Magic Video/VOIP-chat-protocol that is Open Source and adopted by people instead of Skype (will Google save us?)
- Unity much improved

---

### Post by dniMretsaM on 2011-05-16
GIMP needs to be put back in. Thunderbird instead of Evolution, Pidgin instead of Empathy, qBittorrent instead of Transmission. 7Zip maybe. I haven't come across many .7z files though. Python 3 is a must (although I believe that's already been addressed).

---

### Post by leviathan8 on 2011-05-16
I would like to see [ubuntu-tweak]("http://ubuntu-tweak.com/") in the official repositories.

---

### Post by ZarathustraDK on 2011-05-16
> **dniMretsaM said:**
> GIMP needs to be put back in. Thunderbird instead of Evolution, Pidgin instead of Empathy, qBittorrent instead of Transmission. 7Zip maybe. I haven't come across many .7z files though. Python 3 is a must (although I believe that's already been addressed).

It's not so much for the 7z-extension, it's rather the host of other extensions it also supports. It's annoying to install modular apps designed for one specific extension whenever you happen upon some obscure package-format.

Haven't tried qBittorrent, what's its strengths?

+1 on the Pidgin over Empathy.

---

### Post by Bandit on 2011-05-16
> **lucradia said:**
> remove shotwell, and put gimp back in.

Remove empathy, put pidgin back in, the indicator applet now accepts pidgin. (only reason why ubuntu doesn't want pidgin back is because the devs won't use encryption: [http://developer.pidgin.im/wiki/plaintextpasswords](http://developer.pidgin.im/wiki/plaintextpasswords), until someone does it for them. Also, see the list (which includes windows live messenger 2011) of im clients that don't actually use encryption.)

+2

---

### Post by Lucradia on 2011-05-16
> **dniMretsaM said:**
> GIMP needs to be put back in. Thunderbird instead of Evolution, Pidgin instead of Empathy, qBittorrent instead of Transmission. 7Zip maybe. I haven't come across many .7z files though. Python 3 is a must (although I believe that's already been addressed).

Indicator applet gets wonky if you remove evolution completely (including core libs for evolution.) If you remove evolution completely in Ubuntu, it's still in the Ubuntu menu. (Gives an error if you try to launch it.)

---

### Post by magneze on 2011-05-16
Thunderbird over Evolution? Haven't Mozilla killed Thunderbird? :confused:

[http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/](http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/)

---

### Post by ZarathustraDK on 2011-05-16
> **magneze said:**
> Thunderbird over Evolution? Haven't Mozilla killed Thunderbird? :confused:

[http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/](http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/)

Wow...news to me :D

---

### Post by Merk42 on 2011-05-16
> **ZarathustraDK said:**
> - VLC instead of TotemPretty sure this can't happen because VLC comes with non-free codecs

> **magneze said:**
> Thunderbird over Evolution? Haven't Mozilla killed Thunderbird? :confused:

[http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/](http://www.theregister.co.uk/2011/04/05/mozilla_messaging_folded_into_labs/)
Read the article...
> As a result, the Mozilla Messaging moniker will be ditched and development of Thunderbird will continue at the organisation in a much more measured fashion.

"Email is a solid and foundational technology which retains immense value," said Mozilla Foundation chair Mitchell Baker in a blog post.

"We intend to continue our work with the Thunderbird email product to meet this need," she said.

---

### Post by el_koraco on 2011-05-16
> **Lucradia said:**
> Indicator applet gets wonky if you remove evolution completely (including core libs for evolution.) If you remove evolution completely in Ubuntu, it's still in the Ubuntu menu. (Gives an error if you try to launch it.)

That's just not true. There's a evolution indicator package or whateva, you remove it and it's gone from the indicator. There are some other evolution packages that threaten to remove a host of things, like gnome panel and the applet indicators, though.

---

### Post by dniMretsaM on 2011-05-16
> **ZarathustraDK said:**
> It's not so much for the 7z-extension, it's rather the host of other extensions it also supports. It's annoying to install modular apps designed for one specific extension whenever you happen upon some obscure package-format.

Haven't tried qBittorrent, what's its strengths?

+1 on the Pidgin over Empathy.

What other extensions do you get? I didn't see any (other than .7z) added to my archiving options when I installed it. Anyway, qBittorrent is a lot like Deluge. I like the interface a little better. It's a bit more colorful (menu icons and stuff) which I really don't care about. I wouldn't mind Deluge, but it gives me problems so I just use qBittorrent instead. Also, I'd like to see the new version of Eclipse in the repos. And +1 on Ubuntu Tweak being in the repos. 

> **Merk42 said:**
> Pretty sure this can't happen because VLC comes with non-free codecs.

Couldn't they do a stripped-down version of VLC and include the rest of  the codecs in a separate package like VLC Restricted Codecs or  something? Or just include it in the restricted extras package since  most people install that anyway.

---

### Post by murderslastcrow on 2011-05-16
Pretty much everything in the community repo for Arch (not a lot extra). And maybe a few things from the AUR like plasmoids for KDE 4 and the such. Altogether it's not that bad, but nothing really matches availability and flexibility when it comes to using AUR. You can essentially have multiple versions of the same program installed with different compilation methods if you REALLY wanted to. And now Arch has some good GUI package managers that integrate with AUR, so it's no biggy.

I definitely think all of the Elementary stuff should be brought in, too (Postler, Dexter, etc.).

---

### Post by vehemoth on 2011-05-16
Right click make to make a tarball into a .deb
I know it has ppa and all that but sometimes this would just be easier.

---

### Post by Lucradia on 2011-05-16
> **vehemoth said:**
> Right click make to make a tarball into a .deb
I know it has ppa and all that but sometimes this would just be easier.

giftwrap does it via GUI.

---

### Post by vehemoth on 2011-05-16
> **Lucradia said:**
> giftwrap does it via GUI.

Looks promising, hope to see it in the next version of Ubuntu, especially if it has a menu when you right click a tarball.

---

### Post by IWantFroyo on 2011-05-16
A lot of stuff could be added...

For example ***WARNING: RANDOM AND POSSIBLY STUPID IDEAS AHEAD!***

- A netinstall version of Ubuntu could be added as one of the ISO's in the    main downloads page.

- In the proposed netinstall, why not put default application groups like Ubuntu Studio has? (Examples: Developers, Digital Artists, etc.)

- Or just allow us to choose our own applications from a group, like SuseStudio does, except during the hopefully to-be-added netinstall.

---

### Post by Lucradia on 2011-05-17
> **vehemoth said:**
> Looks promising, hope to see it in the next version of Ubuntu, especially if it has a menu when you right click a tarball.

It doesn't have a right-click. It also does not search for deps on the make, so if it fails, usually you're missing a depends for making the DEB.

GiftWrap cannot make clean either: [https://bugs.launchpad.net/giftwrap/+bug/485320](https://bugs.launchpad.net/giftwrap/+bug/485320)

---

### Post by sostentado on 2011-05-17
> **FuturePilot said:**
> Good luck finding anything with no bugs.

Of course they can make it perfect. If microsoft can, ubuntu will.

---

### Post by sostentado on 2011-05-17
Brainstorming is really nice here...

---

### Post by Throne777 on 2011-05-17
> **Lucradia said:**
> Remove shotwell, and put GIMP back in.


Replacing Shotwell with what? GIMP isn't a photo manager.

---

### Post by Mr. Picklesworth on 2011-05-17
> **Lucradia said:**
> Remove Empathy, put Pidgin back in, the indicator applet now accepts pidgin. (Only reason why Ubuntu doesn't want Pidgin back is because the devs won't use encryption: [http://developer.pidgin.im/wiki/PlainTextPasswords](http://developer.pidgin.im/wiki/PlainTextPasswords), until someone does it for them. Also, see the list (which includes Windows Live Messenger 2011) of IM Clients that don't actually use encryption.)

There's also that whole thing with video chat, which it happily supports through a growing number of protocols ;)

Empathy / Telepathy has a better architecture for Ubuntu's social desktop idea, since Empathy is strictly a buddy list (and it could definitely be replaced by a prettier buddy list). Your actual connections are handled by Telepathy, which is a separate service that everything which wants instant messaging type stuff can plug into. (Folks is using this for a global contacts list). Someone suggested actually renaming Empathy to reflect what it is, and I really hope that happens.

I don't remember plain text passwords being a major issue, with the reason being that Firefox is just as bad. I think desktop operating systems (and software) really don't take this seriously enough. In Ubuntu we have this wonderful system for putting passwords under a secure password store ([s]a system Windows lacks[/s] [(no it doesn't!)]("http://ubuntuforums.org/showpost.php?p=10829491&postcount=32")), and we're happy with Firefox totally ignoring it and now thinking about shipping *Thunderbird* which also totally ignores it. End users kind of make the assumption that the operating system will do the right thing with their personal data, but as soon as a malicious user gains access, every scrap of personal information is fair game.

So, uh, my wish: keep Evolution where it is (3.2 has some pretty mockups that might actually happen. I'm excited!) and convince Firefox to use the native password store like Chromium does :)

---

### Post by el_koraco on 2011-05-17
> **murderslastcrow said:**
> I definitely think all of the Elementary stuff should be brought in, too (Postler, Dexter, etc.).

Sure, as soon as they're out of the 0.1.1 versions :D

---

### Post by dniMretsaM on 2011-05-17
I think that Audacity should be installed by default. Tons of people use it and it's a great program. Also BleachBit. Very useful and should definitely be a default program.

---

### Post by teachop on 2011-05-17
I would love to see repos have arm-elf and/or arm-eabi gcc cross compilers (for stand alone targets, already have linux cross for arm in there) with matching newlib, binutils.

---

### Post by tekstr1der on 2011-05-17
> **Mr. Picklesworth said:**
> In Ubuntu we have this wonderful system for putting passwords under a secure password store (**a system Windows lacks**)

Mr. P: I find your posts regularly helpful and/or informative. Sorry to call you out, and to defend MS Windows here, but Windows Vista/7 includes a great system which can store website, service, network passwords, PKI certificates, etc. aptly named Credential Manager (aka "Vault" in Win7).

Passwords stored here are stored encrypted in a key ring similarly to Ubuntu's.

Some reference:
[http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/](http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/)


Sorry again. I'm a Ubuntu user personally, but a Windows systems admin by trade, and can't help but dispel misinformation if possible.

---

### Post by Mr. Picklesworth on 2011-05-17
> **tekstr1der said:**
> Mr. P: I find your posts regularly helpful and/or informative. Sorry to call you out, and to defend MS Windows here, but Windows Vista/7 includes a great system which can store website, service, network passwords, PKI certificates, etc. aptly named Credential Manager (aka "Vault" in Win7).

Passwords stored here are stored encrypted in a key ring similarly to Ubuntu's.

Some reference:
[http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/](http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/)


Sorry again. I'm a Ubuntu user personally, but a Windows systems admin by trade, and can't help but dispel misinformation if possible.

Ah, thanks for the dose of factual accuracy. I remember searching about and never really found anything. Now I know!
(Though ours is in action from the start. I wonder why theirs isn't?)

---

### Post by Lucradia on 2011-05-17
> **tekstr1der said:**
> Mr. P: I find your posts regularly helpful and/or informative. Sorry to call you out, and to defend MS Windows here, but Windows Vista/7 includes a great system which can store website, service, network passwords, PKI certificates, etc. aptly named Credential Manager (aka "Vault" in Win7).

Passwords stored here are stored encrypted in a key ring similarly to Ubuntu's.

Some reference:
[http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/](http://4sysops.com/archives/windows-vault-windows-stored-user-passwords/)


Sorry again. I'm a Ubuntu user personally, but a Windows systems admin by trade, and can't help but dispel misinformation if possible.

Windows Live Messenger doesn't encrypt passwords though ;)

---

### Post by Arla on 2011-05-17
> **Throne777 said:**
> Replacing Shotwell with what? GIMP isn't a photo manager.

Have to agree, I'd much rather see Shotwell replaced with Digikam, than going for GIMP if we're going for a photo management system rather than a editing program.

---

### Post by Lucradia on 2011-05-18
> **Arla said:**
> Have to agree, I'd much rather see Shotwell replaced with Digikam, than going for GIMP if we're going for a photo management system rather than a editing program.

A photo management is only as smart as the person who uses it. I think that the file manager for the system is as good a photo manager as shotwell.

---

### Post by sostentado on 2011-05-19
> **Throne777 said:**
> Replacing Shotwell with what? GIMP isn't a photo manager.

+1 for that :)

---

### Post by teh603 on 2011-05-19
So here's one for the installer:

Allow the user to choose whether or not they use the Gnome Panel or Unity, before installing the OS, and include both packages on the iso.

---

### Post by Merk42 on 2011-05-19
> **teh603 said:**
> So here's one for the installer:

Allow the user to choose whether or not they use the Gnome Panel or Unity, before installing the OS, and include both packages on the iso.
GNOME Panel won't be in 11.10, unless you mean the GNOME Panel which is really a fallback for GNOME Shell.

Either way, options during install will. not. happen.

---

### Post by magneze on 2011-05-19
I'd like to see an easy way to have a separate /home partition and to have that encrypted.

---

### Post by teh603 on 2011-05-19
> **Merk42 said:**
> GNOME Panel won't be in 11.10, unless you mean the GNOME Panel which is really a fallback for GNOME Shell.

Either way, options during install will. not. happen.Fine, then I'll keep steering people toward Kubuntu, which actually has a decent full-featured user interface by default.

---

### Post by cariboo on 2011-05-19
> **magneze said:**
> I'd like to see an easy way to have a separate /home partition and to have that encrypted.

Debian squeeze gives you the option to create a separate home partition during the install process, hopefully we'll see it in Oneiric.

---

### Post by teachop on 2011-05-19
Installer option to do a secure wipe first, defaulting to "OFF".  Not a frequent need, but sometimes it would be nice to be sure nothing is left laying about from prior systems, and is in keeping with the need to move towards higher privacy/security.

---

### Post by MonsterTrimble on 2011-05-19
Possible:
Lubuntu become a official member of the *buntu family
KDE's semantic desktop disabled by default
Clementine replacing Amarok

Pie In The Sky:
Kopete development restarting (Skype integration & working file transfer)
Thunderbird having built in social-networking contact sync (Facebook, Twitter, Flickr, Pidgin, Kopete)

---

### Post by seeker5528 on 2011-05-19
> **cariboo907 said:**
> Debian squeeze gives you the option to create a separate home partition during the install process, hopefully we'll see it in Oneiric.

It's easy when installing Ubuntu as well, you just have to choose the correct partitioning option when the question comes up that allows you to create/select the partitions you want to use and where they should be mounted.

Don't know about the encryption part of the equation, I never really looked at that. 

Later, Seeker

---

### Post by tekstr1der on 2011-05-19
> **cariboo907 said:**
> Debian squeeze gives you the option to create a separate home partition during the install process, hopefully we'll see it in Oneiric.

> **seeker5528 said:**
> It's easy when installing Ubuntu as well, you just have to choose the correct partitioning option when the question comes up that allows you to create/select the partitions you want to use and where they should be mounted.

Don't know about the encryption part of the equation, I never really looked at that. 

Later, Seeker

Yeah, this is very easy with ubuntu's ubiquity. Encryption as well. I've been doing the separate ~/ with ecryptfs at install time for the past few releases. Seems to be made even easier with each new version.

---

### Post by Squonk07 on 2011-05-20
> **MonsterTrimble said:**
> Possible:
**Lubuntu become a official member of the *buntu family**
KDE's semantic desktop disabled by default
Clementine replacing Amarok

Pie In The Sky:
Kopete development restarting (Skype integration & working file transfer)
Thunderbird having built in social-networking contact sync (Facebook, Twitter, Flickr, Pidgin, Kopete)

You must have missed the good news :):

[http://ubuntuforums.org/showthread.php?t=1757242]("http://ubuntuforums.org/showthread.php?t=1757242")
[https://wiki.ubuntu.com/Lubuntu/Specs/IntegrateUbuntuEcosystem]("https://wiki.ubuntu.com/Lubuntu/Specs/IntegrateUbuntuEcosystem")
[http://www.omgubuntu.co.uk/?p=14640]("http://www.omgubuntu.co.uk/?p=14640")

---

### Post by PcMojo on 2011-10-05
I hope this is the correct place to submit my suggestions, I know the thread is a few months old. I've recently had to install / reinstall Ubuntu (10.10 & 11.04) multiple times on multiple Pc's and ran into a few issues that I think can be greatly improved with very little programming and would be helpful for everyone during the install process, but especially people new to Linux. 

During the Ubuntu install process, there are a few things that are unclear or could be made to be much more straight forward, in my opinion. All of these have to do with installing Ubuntu along side of Windows. In the examples I will be using, I have a 240GB hard drive (sda), Windows is installed on sda1 (ntfs) and the user wants to allocate 200GB for this Windows partition and 40GB for Linux which is partitioned as sda3 2GB swap and sda4 38GB for the root install.

1) If the user currently has the entire drive allocated for Windows (in our example 240GB), the installation process is a breeze and has always worked flawlessly for me. A simple slide-bar interface pops up with a suggested size breakdown and the user can adjust the sizes very simply and visually. But having had to reinstall Ubuntu several times I've found it has a problem detecting partitions already formatted for Linux and/or unallocated space. If you had already installed Linux, and had ext4 partitions (in our example, sda3 2GB for swap and sda4 38GB for the actual Ubuntu install - with a possible sda2 as a 40GB extended "container" partition which may or may not be present), the initial installation re-partitioning program ignores these partitions. The slide-bar interface will show the size of the ntfs partition (in our example 200GB), not the whole drive, and when you are done your sda1 ntfs Windows partition will be 160GB and you will have two sets of Linux partitions! And the partitions containing Ubuntu are not at the end of the drive but in between the ntfs and unused original Linux partitions, forcing a move and making a simple resizing impossible. 

2) After doing this a few times, I found current documentation in several places stating that Ubuntu (versions 10.04, 10.10, & 11.04) will automatically try to install on unallocated space. I tried it several times with several of the versions and it never worked out without my manual intervention. I deleted my Linux partitions and turned the 40GB to unallocated space and the automatic installer would show the available space as 200GB, which was the size of sda1, my Windows ntfs partition, but not show the 40GB unallocated, which was where I wanted to install Ubuntu. Again, I had to adjust this manually, through the advanced options, where a total noob could easily trash his system.

3) If you are re-installing or read some documentation prior to installing Ubuntu and partitioned your drive "getting ready for Linux", the automated installer ignores these partitions, as I previously stated, and you are forced to use the "advanced / manual" partition utility. When choosing the "along side Windows" install there is also an option for a manual method. If you chose "along side Windows" the next screen will give you an "advanced partitioning" option. Either option will bring you to the same partitioning utility, which I like, but has one problem that terrifies noobs. While the manual / advanced partitioning utility clearly shows your partitions, it never really tells the user "this is the partition where Ubuntu will be installed, OK?" They actually choose where they are installing Ubuntu by clicking on the partition and choosing root ("/") from the drop down box. But there are no confirmation dialog boxes stating, (as in our example) "Ubuntu will be installed on sda4, is this correct?" I was talking somebody through an install on the phone, (after they had encountered the problems I mentioned earlier where Ubuntu kept taking space from their ntfs partition instead of from partitions meant for the install) and they were afraid of going any further because they were afraid it would install over their ntfs partition because there was not a confirmation dialog box clearly stating that Ubuntu was going to be installed on sda4.   

I hope a programmer involved in the Ubuntu installation/partitioning programs sees this post and finds it useful. I am not writing it to be critical, only to help improve Ubuntu. If I knew more about programming, I would be more than happy to write the code myself. I am utterly amazed every time I use a Live CD or do an Ubuntu install at how it is able to detect all of the hardware, the network settings, and everything else it does seemingly "auto-magically". If you were going to install an OS by itself on a PC, Ubuntu is by far the easiest to install. What does it take? For or Five clicks of the mouse? And some of those clicks are things like "what time zone are you in"? Truly unbelievable. Everybody involved is deserving of our admiration and appreciation. I just hope this could be one of my small contributions to the community. I just want to make Ubuntu more user friendly, especially for noobs. I am the computer geek of my family and have spent thousands of hours "un-infecting" Windows. I came to Linux via the rescue CD's.  I started installing Linux on every on of my family and friends PC's to make it easier for me to clean their Windows not IF, but WHEN they got infected. ;)  The thought occurred to me recently, that if I were to push these people into using Ubuntu, they would not be getting infected and I would have thousands of hours of free time!

These are my suggestions, rants, opinions and ramblings....thanks for listening!

PcMojo

---

### Post by cariboo on 2011-10-05
Thank you for your comments, but unfortunately most developers don't read the forums. The best way to get your concerns seen, is by creating bug reports. If you don't already have an account, you can create one at:

[https://launchpad.net](https://launchpad.net)

and report bugs at:

[https://bugs.launchpad.net](https://bugs.launchpad.net).

---

### Post by SushiR on 2011-10-05
[LIST]
[*]I vote for Guayadeque to replace Banshee. It's an awesome player/music organizer. The GUI could uses some polish and the music store(s) are not integrated yet, but else...best music player around.
[*]Chromium to replace Firefox
[*]Improve Shotwell. It has it's moments, but as a photo manager Digikam is superior
[*]VLC to replace Totem
[*]Integrate G+ in gwibber (although I didn't use gwibber)
[*]Bring back GIMP!
[*]some other stuff I cannot quite remember yet
[/LIST]

---

### Post by Glenn nl on 2011-10-05
-Replace Firefox with Chromium
-Remove Totem (Banshee plays video too)
-Replace Empathy with Pidgin
-Remove the remote desktop apps

---

### Post by seeker5528 on 2011-10-05
> **Glenn nl said:**
> -Remove Totem (Banshee plays video too)

Does it do it well?
Does it do it without wanting to index/import all your media?
Does it start up reasonably quickly?

Later, Seeker

---

### Post by SirDrexl on 2011-10-05
> **seeker5528 said:**
> Does it do it well?
Does it do it without wanting to index/import all your media?
Does it start up reasonably quickly?

Later, Seeker

Yeah, I've always used two different apps for music and video.  I know some can play both, but it just feels wrong to me.

---

### Post by jbicha on 2011-10-05
> **SushiR said:**
> 
[LIST]
[*]I vote for Guayadeque to replace Banshee. It's an awesome player/music organizer. The GUI could uses some polish and the music store(s) are not integrated yet, but else...best music player around.
[*]Chromium to replace Firefox
[*]Improve Shotwell. It has it's moments, but as a photo manager Digikam is superior
[*]VLC to replace Totem
[*]Integrate G+ in gwibber (although I didn't use gwibber)
[*]Bring back GIMP!
[*]some other stuff I cannot quite remember yet
[/LIST]


Sorry, GIMP will not return to the default CD. It's way too complicated for Ubuntu's target users. Think more "Simple Scan", less "xsane".

I'm not going to bother commenting on Chromium vs. Firefox as that should probably be its own thread.

Gwibber can't integrate G+ until Google bothers releasing a useful API. And as soon as that happens, I'm sure it will be included as it's extremely popular among the tech crowd.

Guayadeque looks quite out of place on Ubuntu; perhaps it's the wxWidgets. Another major hiccup is that I don't think anyone wants to port the Ubuntu One music store to yet another music player.

VLC does have some advantages for videos, but it doesn't have media library capabilities which makes it lacking. It brings in a bunch of dependencies and I don't know how many of those are needed, and how much it "cripples" the app if those aren't installed.

Honestly, there needs to be a real good reason to change the "core" (my word) default desktop apps. The best video app for Ubuntu will likely be discussed at UDS as there are concerns that Totem 3.2 now requires the clutter-gst backend which some fear may not work as well on some computers (especially ARM). Some prefer a separate video player; others think playing music and videos in the same app is better.

---

