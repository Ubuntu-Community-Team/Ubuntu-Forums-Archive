---
title: "HOWTO: E17 using apt and Smoon's repo"
date: 2005-07-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Tab on 2005-07-03
**NOTE: Smoon is no longer maintaining his E17 repository. See [this]("http://ubuntuforums.org/showthread.php?t=61488") thread for a smiliar method using the repository provided by Elive (note that it's not necessary to modify libc6, and this repo can simply be used as a drop-in for Smoon's. Some of the install names have changed, however.)**

Because the other thread is a mess  :p

This HOWTO describes the simple process of installing [Enlightenment DR17]("http://www.enlightenment.org/Enlightenment/DR17/index.html") & related utilities using our own [Smoon]("http://www.ubuntuforums.org/member.php?userid=15862")'s excellent apt repository. Thanks Smoon!

First, add Smoon's repository to your apt sources.list:
```
$ sudo echo "deb http://ubuntu.nooms.de/ hoary/" >> /etc/apt/sources.list
```
Next, create and open the apt preferences file:
```
$ sudo gedit /etc/apt/preferences
```
and tell it to prefer the latest version of Enlightenment:
```
Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999
```
Update apt:
```
$ sudo apt-get update
```
and install!
```
$ sudo apt-get install enlightenment eutils
```
The install should automatically create a new .desktop file in /usr/share/xsessions, so you can now log into E17 from your regular login manager. Log out, log into E, and enjoy!


Optionally, you can also install extra EFL programs & E modules. For more information on these, see [the Get-E user guide]("http://www.get-e.org/User_Guide/English/index.html").
```
$ sudo apt-get install emodules engage entrance eclair elicit entice examine eclips
```
**emodules** - These add functionality and eye-candy to the Enlightenment desktop outside of those included in E.
**engage** - An OSX-style dock.
**entrance** - Login manager.
**eclair** - Media player.
**elicit** - Magnifier/color dropper.
**entice** - Image viewer.
**examine** - Configuration utility.
**eclips** - Another image viewer.

Two other popular EFL-based utilities, the Eterm terminal emulator and  Evidence file manager, can be installed by other means.
Eterm is in Hoary Universe and can be installed via apt. See [How to add extra repositories](http://ubuntuguide.org/#extrarepositories).
```
$ sudo apt-get install Eterm
```
To get Evidence, download the Hoary .deb from [sourceforge](http://prdownloads.sourceforge.net/evidence/evidence_0.9.8-20050305-hoaryGMW_i386.deb?download) and install using dpkg:
```
$ sudo dpkg -i evidence_0.9.8-20050305-hoaryGMW_i386.deb
```

For Enlightenment themes, backgrounds, and more visit [Get-E.org]("http://www.get-e.org/") and the [Edevelop forum]("http://www.edevelop.org/forum/").

---

### Post by Skel on 2005-07-03
Giving it a try logging out now Thank u very much :)


It looks so nice and all but God damm its so complicated to do anything i geuss i will stick ta gnome.. ](*,)

---

### Post by thagame on 2005-07-03
>  Package entrance is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source 

i get that error when trying to install entrance. every package but this is there and installs with no problems.

and i was on get-e.org and it said to add 

>  Package: enlightenment
Pin: version 0.17.0_pre10*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.0_pre10*
Pin-Priority: 999 

to /etc/apt/preferences   file. but has diff repos links to use. gonna try that out and see if it makes a diff.

---

### Post by smoon on 2005-07-03
Thanks Tab, for that great Howto. I was thinking about writing one myself but was too lazy ;)

thagame and everyone else: Don't follow the instructions found at get-e.org or anywhere else that tell you about "Shadoi's repository" or entries like "Pin: version 0.17.0_pre10*" in /etc/apt/preferences! They are refering to the repository for Debian SID, which will NOT work with Ubuntu!
Use the instructions posted by Tab on top of this thread - this is the only way to get Ubuntu packages of e17, its tools and libraries.

thagame, there's no entrance package yet. Only the programs Tab referred to in his Howto are in the repository. I may create a package if you _really_ need entrance though.

---

### Post by tread on 2005-07-03
Does the engage available here load as a module in e17 or is it a standalone application?

---

### Post by smoon on 2005-07-03
[QUOTE=tread]Does the engage available here load as a module in e17 or is it a standalone application?[/QUOTE]

It includes both, the standalone version of engage and the e17 module which can be loaded via ```
enlightenment_remote -module-load engage
```

---

### Post by srt4play on 2005-07-03
I don't think any of us really NEED any of the E17 stuff considering it is pre-alpha software, but it sure is nice to have new stuff to play with.

btw thanks for the repository

---

### Post by smoon on 2005-07-03
[QUOTE=srt4play]I don't think any of us really NEED any of the E17 stuff considering it is pre-alpha software, but it sure is nice to have new stuff to play with.

btw thanks for the repository[/QUOTE]

Yeah, that's exactly why I created the repository: I like to play with new and fancy stuff. I don't use e17 yet and I don't think I'll use it anytime in the future since it's all much too complicated to use. I really like simplicity and that's why I've chosen Gnome to be my desktop of choice.

---

### Post by tread on 2005-07-03
Thanks smoon. The last time I used a repo, engage was standalone only and the modular version is much better integrated and doesn't use fake transparency (I think) .. I ended up compiling the whole thing  :rolleyes: 
Nice to have a repository!

---

### Post by super on 2005-07-03
hey smoon thanks for the repo! it makes things a lot easier.

quick question, what the heck is that pyramid thing at the bottom right of your first screenshot?

---

### Post by thagame on 2005-07-03
its ok i got entrance by doing apt-get after following the instructions on get-e. everything worked out fine and i got the newest versions

---

### Post by Tab on 2005-07-04
[QUOTE=srt4play]I don't think any of us really NEED any of the E17 stuff considering it is pre-alpha software, but it sure is nice to have new stuff to play with[/QUOTE]

Pre-alpha it may be, but it's plenty usable -- it's my main DE :p GNOME is easier, but E17 is just that much *cooler*.

[QUOTE=super]quick question, what the heck is that pyramid thing at the bottom right of your first screenshot?[/QUOTE]

A clock  :) 
It's found [here](http://www.edevelop.org/forum/viewtopic.php?t=1237). It was built into the Ice theme by its creator, but you can get it for the default theme down a few posts.

While I'm at it, Smoon, would you consider including the underscore in e_modules and e_utils in the future, for the sake of consistency? This is how the other repos name these packages.

---

### Post by tread on 2005-07-04
Did anyone get alt-tab working? According to the edevelop forum, enlightenment_remote has that option but I couldn't find it.

---

### Post by Tab on 2005-07-04
[QUOTE=tread]Did anyone get alt-tab working? According to the edevelop forum, enlightenment_remote has that option but I couldn't find it.[/QUOTE]

It's not done from enlightenment_remote, it should work out-of-the-box  :| 

OT: I'm curious to see this "awesome new animation" the guys are raving about at Get-E :O

---

### Post by srt4play on 2005-07-04
[QUOTE=thagame]its ok i got entrance by doing apt-get after following the instructions on get-e. everything worked out fine and i got the newest versions[/QUOTE]

Could you elaborate? I don't see anything on get-e.org about using apt-get , only cvs. Did you scrap your repository installation and do it from scratch with cvs?

---

### Post by smoon on 2005-07-04
[QUOTE=srt4play]Could you elaborate? I don't see anything on get-e.org about using apt-get , only cvs. Did you scrap your repository installation and do it from scratch with cvs?[/QUOTE]

You can install entrance from my repository in a few mins. I'm currently uploading it's package ;) Due to the fact that I'm only able to upload with around 12 kB/s and the package is 4,7 MB in size it takes a while...


*Edit*

Done. You can install entrance from my repository now.
Tab, can you please update your Howto to include entrance in the list of installable applications?

---

### Post by smoon on 2005-07-04
[QUOTE=Tab](...)
While I'm at it, Smoon, would you consider including the underscore in e_modules and e_utils in the future, for the sake of consistency? This is how the other repos name these packages.[/QUOTE]

I could change the packages names, but I don't think I'll do it since this will only confuse people that already got used to my repository. It's not that bad either since searching with `apt-cache search ...' will reveal there package names to new users.

---

### Post by holr on 2005-07-04
woah this is pretty amazing. just installed using this howto (thankyou!) and been tinkering around with enlightenment. Sure is definately alpha, but boy is it gonna be great when its finished! It also feels a lot quicker than kde and gnome, prolly cause half the stuff isnt running lol

worth keeping an eye on for some serious desktop eye candy.

---

### Post by tread on 2005-07-04
> Sure is definately alpha, but boy is it gonna be great when its finished! 

If it ever finishes .. its been going on for god knows how many years :) 
The one thing I hate is that each application needs an eap file .. if there isnt one, you get an ugly ? in engage.

---

### Post by srt4play on 2005-07-04
[QUOTE=smoon]You can install entrance from my repository in a few mins. I'm currently uploading it's package ;) Due to the fact that I'm only able to upload with around 12 kB/s and the package is 4,7 MB in size it takes a while...


*Edit*

Done. You can install entrance from my repository now.
Tab, can you please update your Howto to include entrance in the list of installable applications?[/QUOTE]

Thank you so much! You rock!

It installed without a hitch.. just gotta figure out why my keyboard is disabled when entrance is running.. sure looks good though.

---

### Post by Tab on 2005-07-05
[QUOTE=smoon]Done. You can install entrance from my repository now.
Tab, can you please update your Howto to include entrance in the list of installable applications?[/QUOTE]

Excellent  :)  Will do.

---

### Post by Tamir on 2005-07-06
[QUOTE=Tab]Excellent  :)  Will do.[/QUOTE]
 Smoon :), thank you very much. but can you please make 64bit packages?
I know many peapole that want it, and can't. if I can help with that, just tell me how.

---

### Post by smoon on 2005-07-06
[QUOTE=Tamir]Smoon :), thank you very much. but can you please make 64bit packages?
I know many peapole that want it, and can't. if I can help with that, just tell me how.[/QUOTE]

I don't know exactly how to do this, but I hope it'll be enough to compile the stuff on a 64 system/OS. If you're running a 64bit version of Ubuntu you could try to build packages with the script I created for creating the x86 packages: [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh).

You'll find solutions to the most common problems in this threads:
[http://www.ubuntuforums.org/showthread.php?t=30525](http://www.ubuntuforums.org/showthread.php?t=30525)
[http://www.ubuntuforums.org/showthread.php?t=20216](http://www.ubuntuforums.org/showthread.php?t=20216)

If you get into any other trouble ask me (with a detailed report on your error ;)) for assistance in one if this threads.

When you're done and all packages work for you, I'll upload them to the repository.

---

### Post by czynski on 2005-07-07
smoon, i used your repo a few weeks ago and it worked great. i did a fresh install of ubuntu yesterday and used your repo again but this time i don't have any apps in my configuration tab (like the background selector). does anyone know how i could fix this.

---

### Post by Tab on 2005-07-07
[QUOTE=czynski]smoon, i used your repo a few weeks ago and it worked great. i did a fresh install of ubuntu yesterday and used your repo again but this time i don't have any apps in my configuration tab (like the background selector). does anyone know how i could fix this.[/QUOTE]

You need to rename the .eapps in /usr/share/enlightenment/config-apps/ to .eap. This is probably fixed in CVS. An update to the repo may be worthwhile. Then we'd be getting the mysterious "cool new background-changing animation" and my fixes to Eclair's interface, too :D

---

### Post by Tamir on 2005-07-07
[QUOTE=smoon]I don't know exactly how to do this, but I hope it'll be enough to compile the stuff on a 64 system/OS. If you're running a 64bit version of Ubuntu you could try to build packages with the script I created for creating the x86 packages: [http://nooms.de/misc/e17install.sh](http://nooms.de/misc/e17install.sh).

You'll find solutions to the most common problems in this threads:
[http://www.ubuntuforums.org/showthread.php?t=30525](http://www.ubuntuforums.org/showthread.php?t=30525)
[http://www.ubuntuforums.org/showthread.php?t=20216](http://www.ubuntuforums.org/showthread.php?t=20216)

If you get into any other trouble ask me (with a detailed report on your error ;)) for assistance in one if this threads.

When you're done and all packages work for you, I'll upload them to the repository.[/QUOTE]

Yes, I am running on 64BIT version of ubuntu, so I'll try your script  :smile:
Basicly, You should compile this stuff on 64bit enviroment, or in chroot.

---

### Post by smoon on 2005-07-07
[QUOTE=Tab]You need to rename the .eapps in /usr/share/enlightenment/config-apps/ to .eap. This is probably fixed in CVS. An update to the repo may be worthwhile. Then we'd be getting the mysterious "cool new background-changing animation" and my fixes to Eclair's interface, too :D[/QUOTE]

A few moments after I read about that animations being in CVS I rebuilt the enlightenment packages and tried them, but to my regret there wasn't anything to look at. The only thing was, that I was able to set different backgrounds for different desktops, but there weren't any "cool new background-changing animation", so I decided not to put the new packages in the repository. I'm currently trying to checkout new changes from CVS to build new packages, but there seems to be something wrong with Sourceforge CVS. But as soon as it works again I'll create new packages and upload them ;-)


*Edit*
Ok, after deleting ~/.e and ~/.ecore and using the packages I built a few mins ago I get this nice background-changing effect as well - quite nice. I'm currently uploading new packages of enlightenment, eclair and eutils. They will be ready in about an hour.

---

### Post by czynski on 2005-07-08
does anyone know why i might be having issues with the Eapp Editor? i can't add any programs or change any icons.
      i used to have it working on a different install of e17 but i don't remember how i bult it and got it working last time. other than that problem smoon's repo installs great for me; much easier.

---

### Post by Flane on 2005-07-08
Thanks a lot for this repository.
It worked and enlightenment ist working fine.

unfortunatelly i'm not able to install eterm

```
apt-get install eterm
``` 

doesn't find the package eterm.
My sources.list only contains smoon's repo and the standart packages from ubuntu.

Sorry but i'm quite new to linux and ubuntu, so i'm quite a newbee  \\:D/ 

Thanks a lot for help

Flane

---

### Post by dlpfmVfH on 2005-07-08
smoon, can you please include evidence and eclipse in the repository??

And thank you again for making this repo possible...it rocks...!

---

### Post by tealc_sg1 on 2005-07-08
Absolutely brilliant ! This is the first time I have EVER managed to install E, thanks a lot  :)

---

### Post by smoon on 2005-07-08
[QUOTE=Flane]Thanks a lot for this repository.
It worked and enlightenment ist working fine.

unfortunatelly i'm not able to install eterm

```
apt-get install eterm
``` 

doesn't find the package eterm.
My sources.list only contains smoon's repo and the standart packages from ubuntu.

Sorry but i'm quite new to linux and ubuntu, so i'm quite a newbee  \\:D/ 

Thanks a lot for help

Flane[/QUOTE]

Eterm is not included in my repository since it's already in universe. Check if you've got a line like that in /etc/apt/sources.list "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse". Anyway, i prefer urxvt from the rxvt-unicode package over any other terminal emulator, give it a try, it's in universe as well.

---

### Post by smoon on 2005-07-08
[QUOTE=aboe]smoon, can you please include evidence and eclipse in the repository??

And thank you again for making this repo possible...it rocks...![/QUOTE]

I'll have a look at this packages. But chances that I include evidence are not so good because evidence uses another CVS repository and last time I tried to compile it was nearly impossible, but I'll check that again. Never heard of eclipse in correlation (is that the right term?) with enlightenment, I ever thought the only project called eclipse was this big, slow (mainly Java-)IDE. But I'll have a look at this as well.


*Edit*
eclips (Note, it's not eclipse it's eclips without the trailing e) is now in the repository and installable via apt - everyone who tries it out and likes it should have a look at feh (it's in universe). feh IMHO is much better than eclips.
Since there's already an official evidence package for hoary I'll not build one. To install evidence (for those who not already know: evidence is a filemanager based on the e libs) go to [Evidence's Project Filelist](http://sourceforge.net/project/showfiles.php?group_id=58061), click on "[Download evidence_0.9.8-20050305-hoaryGMW_i386.deb](http://prdownloads.sourceforge.net/evidence/evidence_0.9.8-20050305-hoaryGMW_i386.deb?download)" to download the Hoary package and install it with `sudo dpkg -i /path/to/evidence_0.9.8-20050305-hoaryGMW_i386.deb'. I tried it and it works fine for me.

Tab, maybe you can update your Howto again to include a reference to eclips and how to install evidence? :-P

---

### Post by smoon on 2005-07-08
[QUOTE=tealc_sg1]Absolutely brilliant ! This is the first time I have EVER managed to install E, thanks a lot  :)[/QUOTE]

No problem :-)

---

### Post by abandoned_hussam on 2005-07-08
[QUOTE=smoon]A few moments after I read about that animations being in CVS I rebuilt the enlightenment packages and tried them, but to my regret there wasn't anything to look at. The only thing was, that I was able to set different backgrounds for different desktops, but there weren't any "cool new background-changing animation", so I decided not to put the new packages in the repository. I'm currently trying to checkout new changes from CVS to build new packages, but there seems to be something wrong with Sourceforge CVS. But as soon as it works again I'll create new packages and upload them ;-)


*Edit*
Ok, after deleting ~/.e and ~/.ecore and using the packages I built a few mins ago I get this nice background-changing effect as well - quite nice. I'm currently uploading new packages of enlightenment, eclair and eutils. They will be ready in about an hour.[/QUOTE]
 smoon, will you continue to make updated packages so that we can have the final version when 0.17 is out? thanks again. :)

---

### Post by smoon on 2005-07-08
[QUOTE=hussam]smoon, will you continue to make updated packages so that we can have the final version when 0.17 is out? thanks again. :)[/QUOTE]

Yeah, I think I'll continue updating the packages for a while. Not sure if you'll find the final e17 in my repository though ;-)

---

### Post by Tab on 2005-07-08
Updated, added some descriptions, changed the layout a bit.

Tried Eclips, but it seems a bit redundant with Entice. Still cool.

---

### Post by smoon on 2005-07-08
[QUOTE=Tab]Updated, added some descriptions, changed the layout a bit.

Tried Eclips, but it seems a bit redundant with Entice. Still cool.[/QUOTE]

Thanks alot :-) I think you can remove the part that explains how to add an entry for enlightenment to the display manager since the latest enlightenment-data package installs one on its own:
```
 % dpkg -L enlightenment-data                    
...
/usr/share/xsessions
/usr/share/xsessions/enlightenment.desktop
```
```
 % cat /usr/share/xsessions/enlightenment.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Enlightenment
Comment=Log in using Enlightenment (Version 0.16.999.010)
Type=XSession
Exec=/usr/bin/enlightenment
TryExec=/usr/bin/enlightenment
```

---

### Post by Tab on 2005-07-08
Ah, great! Simplifies things for the user. Thanks for the heads-up.

---

### Post by Tab on 2005-07-08
Just an FYI, I'll be gone for the next two weeks, so this is the last I'll be able to update the HOWTO for now.

---

### Post by vrln on 2005-07-09
[QUOTE=hussam]smoon, will you continue to make updated packages so that we can have the final version when 0.17 is out? thanks again. :)[/QUOTE]

There's not even a speculative release date available, so I wouldn't expect the final version any time soon :) Once E17 is out, all major distributions will probably make official packages for it. Mark Shuttleworth actually even mentioned something about the possibility of a community-driven "E17-Ubuntu" in the slashdot interview.

---

### Post by dlpfmVfH on 2005-07-09
thanks smoon for the packages..eclips and evidence...

also would like to note, there's a new background image at get e....
it's cool cause it's a new animated background that doesn't eat up al cpu-cycles...
and it looks great with the default theme...

check misc galery...[http://ubuntuforums.org/gallery/showimage.php?i=489&c=4]("http://ubuntuforums.org/gallery/showimage.php?i=489&c=4")

---

### Post by gnuageux on 2005-07-12
Thanks for the thread, Ive got e installed - but I cant seem to login through gdm. I select it as my session then when I start it I get an error saying that my x session lasted ten seconds, heres the error from ~/.xsession-errors

/usr/bin/enlightenment: /usr/local/lib/libpng12.so.0: no version information ava ilable (required by /usr/lib/libevas.so.1)
/usr/bin/enlightenment: relocation error: /usr/bin/enlightenment: undefined symb ol: ECORE_X_EVENT_SYNC_ALARM


Anyone seen this? Id like to get E working but dont really know where to go from here. TIA!

---

### Post by Tamir on 2005-07-12
I am not in my ubuntu right now so I am not sure this is the true name of the package, but make sure that you have :

- libpng12 
- libevas0 \ libevas2

use : apt-cache search libpng 
and install what ever with same name of libpng12

---

### Post by gnuageux on 2005-07-12
according to apt I have the most recent version of the libs....

---

### Post by gnuageux on 2005-07-13
BUMP 

anyone?

---

### Post by gnuageux on 2005-07-13
I removed the following symlink: 

 # ls -l /usr/local/lib/libpng12.so.0 
lrwxrwxrwx  1 root root 17 2005-07-11 19:51 /usr/local/lib/libpng12.so.0 -> libpng12.so.0.0.0

and now when I start it the only error thats thrown is 

$ enlightenment 
enlightenment: relocation error: enlightenment: undefined symbol: ECORE_X_EVENT_SYNC_ALARM

Searching but coming up w/ nothing. Any ideas?

---

### Post by gnuageux on 2005-07-17
Still havent come up with a solution. Any thoughts?!?

---

### Post by Stormy Eyes on 2005-07-17
OK, Smoon, I've just installed E17 from your repository. When using e17setroot, the shell bitches about not being able to find Esetroot or edje_cc. Esetroot can be obtained by *sudo apt-get install eterm*, and edje_cc can be obtained by *sudo apt-get install edje0-bin edje0-test*.

When attempting to use Eclair, the app gripes about missing libtag_c.so.0, which can be remedied by doing *apt-get install libtag1 libtag1-dev libtagc0 libtagc0-dev*. (The -dev packages might not be necessary). Eclair also demands libsqlite3.so.0, which can be obtained with *apt-get install sqlite3*. 

If you're making these debs yourself, you might want to update the dependency info. Good work so far, aside from these two kinks.

---

### Post by smoon on 2005-07-18
[QUOTE=Stormy Eyes]OK, Smoon, I've just installed E17 from your repository. When using e17setroot, the shell bitches about not being able to find Esetroot or edje_cc. Esetroot can be obtained by *sudo apt-get install eterm*, and edje_cc can be obtained by *sudo apt-get install edje0-bin edje0-test*.

When attempting to use Eclair, the app gripes about missing libtag_c.so.0, which can be remedied by doing *apt-get install libtag1 libtag1-dev libtagc0 libtagc0-dev*. (The -dev packages might not be necessary). Eclair also demands libsqlite3.so.0, which can be obtained with *apt-get install sqlite3*. 

If you're making these debs yourself, you might want to update the dependency info. Good work so far, aside from these two kinks.[/QUOTE]

Thanks for the hints, I'll fix that ASAP of course.

On a side note: I created a video of enlightenment in action for those who want to see it before installing:
[**Download/Watch Video**](http://nooms.de/misc/e17.avi)

---

### Post by Stormy Eyes on 2005-07-20
[QUOTE=smoon]Thanks for the hints, I'll fix that ASAP of course.[/QUOTE]

No problem. I've noticed that E17 doesn't exactly play nice with xscreensaver, so I've disabled it.

---

### Post by loon on 2005-07-21
[QUOTE=Flane]Thanks a lot for this repository.
It worked and enlightenment ist working fine.

unfortunatelly i'm not able to install eterm

```
apt-get install eterm
``` 

doesn't find the package eterm.
My sources.list only contains smoon's repo and the standart packages from ubuntu.

Sorry but i'm quite new to linux and ubuntu, so i'm quite a newbee  \\:D/ 

Thanks a lot for help

Flane[/QUOTE]


[www.ubuntuguide.org](www.ubuntuguide.org)

Add the extra reps from there.
To use from terminal, do Eterm, not eterm.

- loon

---

### Post by Mgcross on 2005-07-25
I will add my thanks to the many you already have. I just wish that this thing would warp up a little quicker as far as developement goes...I had no problems getting it all to wrk, but, as it stands now...it simply fun to play with/look at. If things speed up, and usabillity ramps up as well, this thing COULD be a world beater.

I know it's pre-alpha...but how long has it been that way. How long before a beta test. Years? What a shame. Losta good stuff there. \\:D/

---

### Post by Tanus on 2005-07-27
Thanks, all other deb packages that just refused to work, these did. However, I'm having a problem with eapps not being available (nothing showing up in the ibar, nothing in the menus). Running entangle shows the eapps are there, but they're just not being picked up at all. I've tried creating a new .eapp, but keep getting an error 
> 
e_util_eapp_edit: relocation error: e_util_eapp_edit: undefined symbol: ewl_entry_text_get


I can open existing eapps with e_util_eapp_edit, but it seems e17's not liking them at all and refuses to show them in menus of any sort, and I can't create new ones due to the error above. Anyone had any of these problems before?

---

### Post by Tab on 2005-07-27
.eapps were changed to .eap a little while ago. If you still have .eapps, you'll have to rename them.

---

### Post by smoon on 2005-07-27
Here's a bash oneliner that renames all files that have .eapp as suffix to .eap files:
```
for i in *.eapp ; do mv $i ${i%.eapp}.eap ; done
```
Maybe someone finds this useful. This one does the same, but recursive (for the current working directory and all its subdirectories):
```
for i in `find . -name "*.eapp"` ; do mv $i ${i%.eapp}.eap ; done
```

---

### Post by loon on 2005-07-27
Also, enable transparent in Eterm and update Eterm command with

"Eterm  -n Eterm --buttonbar 0 --scrollbar 0 -f white -x"


'-n Eterm'  
--puts Eterm in the title or basically names the window

'--buttonbar 0'  
--take menus away

'--scrollbar 0' 
--take scrollbar away

'-f white' 
--changed my text to white since I has a dark background

'-x' 
--borderless

Once the Eterm is up and looking all nice and see through, to move it, hold down alt and drag the window where you would like for it to be placed.

- loon

---

### Post by Tanus on 2005-07-27
[QUOTE=Tab].eapps were changed to .eap a little while ago. If you still have .eapps, you'll have to rename them.[/QUOTE]
 Hmm, good point, I did have a version of e17 from a few months ago, guess I didn't purge my config as first thought. Might be time to get rid of it and let it regen.

---

### Post by Tanus on 2005-07-27
[QUOTE=Tanus]Hmm, good point, I did have a version of e17 from a few months ago, guess I didn't purge my config as first thought. Might be time to get rid of it and let it regen.[/QUOTE]
 Just as a bit of a follow-up, I found the following thread [http://edevelop.org/forum/viewtopic.php?t=1344&highlight=ewlentrytextget](http://edevelop.org/forum/viewtopic.php?t=1344&highlight=ewlentrytextget) that seems to suggest there's been an api change that's not reflected in the e_util_eapp_edit application I'm using.

---

### Post by hal8000 on 2005-07-29
Have followed the howto but when I come to install enlightenment I get:


anc@ganymede:~$ sudo apt-get install enlightenment eutils


Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  enlightenment: Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
  eutils: Depends: libecore0 but it is not going to be installed
          Depends: libedb1 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libengrave0 but it is not going to be installed
          Depends: libepeg0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
          Depends: edje0-bin but it is not going to be installed
E: Broken packages


How can I resolve this? TYhanks in advance using Hoary 5.04

---

### Post by Tanus on 2005-07-29
What sources.list are you using? I was getting the same errors, but after changing to a very stock standard sources.list, things just worked...

Mine:

> 
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted


##############Ubuntu Security##############
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse


---

### Post by hal8000 on 2005-07-30
You may be right, contents of my /etc/apt/sources.lst

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-updates main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

What did you comment out to get this working?

---

### Post by Tanus on 2005-07-30
I only had 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse

and

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

Give that a try.

---

### Post by poofyhairguy on 2005-08-01
Has anyone figured out an elegent (like kompose or skippy style elegant) to swith tasks in enlightenment?

---

### Post by hal8000 on 2005-08-01
[QUOTE=Tanus]I only had 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse

and

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

Give that a try.[/QUOTE]


Hi Tanus, thank you very much, that did allowed me to install E17. I commented out the other repositories in my sources.list so that I can add them back later. Now on to familiarize myself with E17 :)

---

### Post by bjesus on 2005-08-03
I´m using breezy and no matter what I do I keep getting this error trying to apt-get:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  enlightenment: Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
  eutils: Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libengrave0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
          Depends: edje0-bin but it is not going to be installed
E: Broken packages
``` 

I´ve tried shrinking my source.list to the minimum, so now it´s only this:

```
deb http://ubuntu.nooms.de/ hoary/

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted
#deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
``` 

But still I get that error.

I miss E17... I was using it on Gentoo a few months ago and have heard it has matured a lot...

Has anyone succsefully apt-getted E17 on his Breezy setup? Or should I just compile it from source?

Thanks.

---

### Post by bored2k on 2005-08-04
> raf@box:~$ eclair
eclair: error while loading shared libraries: libtag.so.1: cannot open shared object file: No such file or directory
 ?

---

### Post by smoon on 2005-08-05
[QUOTE=bored2k]?[/QUOTE]

You've to install libtag1, libtagc0 along with some more dependencies since the eclair package does not include the dependencies (don't know why, it just don't works. I'll investigate on that ASAP). Here's the dependency list:

```
Depends: libatk1.0-0, libecore0, libedje0, libeet0, libemotion0, libesmart0, libevas0, libglade2-0, libglib2.0-0. libgtk2.0-0, libjpeg62, libpango1.0-0, libtag1, libtagc0, libxml2, zlib1g, libsqlite3-0
```

---

### Post by AndyAWS on 2005-08-05
Hey smoon, thanks again for your e17 repo.

I've only been having one problem, and I can't find any info about it. I don't know if it's a bug or just something I have set wrong. ](*,) 

When I close a program window, it still shows up in the menu under 'windows' as minimized (unchecked)...If I check it's box it sometimes comes back...If I close it again and look back in the menu under windows, there are now two listed...etc.

It appears to me that instead of closing the windows, e17 is just minimizing them or something.

Note: This doesn't happen all of the time, but once it starts it doesn't work right again until I reboot.

Any ideas?...Anyone else seen this?...I've already tried deleting ~/.e to refresh my config.

One more thing...I've enabled the Engage module..is it supposed to start empty?

---

### Post by smoon on 2005-08-06
[QUOTE=AndyAWS]Hey smoon, thanks again for your e17 repo.

I've only been having one problem, and I can't find any info about it. I don't know if it's a bug or just something I have set wrong. ](*,) 

When I close a program window, it still shows up in the menu under 'windows' as minimized (unchecked)...If I check it's box it sometimes comes back...If I close it again and look back in the menu under windows, there are now two listed...etc.

It appears to me that instead of closing the windows, e17 is just minimizing them or something.

Note: This doesn't happen all of the time, but once it starts it doesn't work right again until I reboot.

Any ideas?...Anyone else seen this?...I've already tried deleting ~/.e to refresh my config.

One more thing...I've enabled the Engage module..is it supposed to start empty?[/QUOTE]

Since I only use e17 for a few mins after I build new packages to test, if everything works fine I never noticed this behaviour with windows showing up in the window list even though they were closed. I'll update the packages soon, maybe this was a known bug that is fixed now (remember: e17 is something like pre-alpha at the moment and it's not supposed to work without problems ;)).

You've to create the directory **${HOME}/.e/e/applications/engage** and put a **.order** file in there for engage to show up applications when used as module. For an example of this file see **${HOME}/.e/e/applications/bar/.order**.

---

### Post by AndyAWS on 2005-08-06
Here's a quick way to check for the problem...

 - log in to E
 - start a gome-terminal
 - minimize it
 - go to windows in the menu and restore the terminal
 - close terminal and it will still show up in the windows menu

However if I use alt-tab to restore the window instead of the menu then it closes properly. So it's only an issue if I use the window menu to restore a window...as far as I can tell.


And thanks for the help with Engage  \\:D/

---

### Post by kelean on 2005-08-06
[QUOTE=AndyAWS]Here's a quick way to check for the problem...

 - log in to E
 - start a gome-terminal
 - minimize it
 - go to windows in the menu and restore the terminal
 - close terminal and it will still show up in the windows menu

However if I use alt-tab to restore the window instead of the menu then it closes properly. So it's only an issue if I use the window menu to restore a window...as far as I can tell.


And thanks for the help with Engage  \\:D/[/QUOTE]
 I have installed E-17 and everything went well.  I have it up and running.  I even maneaged to install new themes.  When I try to install other apps for E-17 i cant.

kevin@Klasra:~$ $ sudo apt-get install emodules engage entrance eclair elicit entice examine eclips
bash: $: command not found
kevin@Klasra:~$ $ sudo apt-get install emodules bash: $: command not found
kevin@Klasra:~$ $ sudo apt-get install engage bash: $: command not found
kevin@Klasra:~$

I have smoons repo in my apt list.  Any help would be most aprieated.  
Thank you Kelean

---

### Post by smoon on 2005-08-07
[QUOTE=kelean]I have installed E-17 and everything went well.  I have it up and running.  I even maneaged to install new themes.  When I try to install other apps for E-17 i cant.

kevin@Klasra:~$ $ sudo apt-get install emodules engage entrance eclair elicit entice examine eclips
bash: $: command not found
kevin@Klasra:~$ $ sudo apt-get install emodules bash: $: command not found
kevin@Klasra:~$ $ sudo apt-get install engage bash: $: command not found
kevin@Klasra:~$

I have smoons repo in my apt list.  Any help would be most aprieated.  
Thank you Kelean[/QUOTE]

You should try the commands without the leading dollar sign ($) ;-)
```
sudo apt-get install emodules engage entrance eclair elicit entice examine eclips
```

---

### Post by kelean on 2005-08-07
Thank you smoon.   It is amazing how I can try so hard but overlook the the simple things.

Also thank you for the repo and all the work put into it.

It worked so well when entered correctly.  What a surprize!
Now I just to do some reading and figure out how to use engage amd the other programs.

Once again thank you very much.

Kelean

---

### Post by ykpaiha on 2005-08-07
I don't know why I get a plain black (for one min) then white screen with the mouse working, but no deco ?
any clue?
thanks

I still do not understand....It  worked after a full reboot
Very nice.
I  wiil try to mix it with gnome ...fun linux is fun isn't it!
who dare to say "too  complicated" ?

---

### Post by super on 2005-08-09
i know i shouldn't be asking questions in the 'tips' section but since everyone is doing it...  :smile: 

i finally borked my e17 desktop after having it running great for a few month. when it was first installed i had used the 'soulmachine' repo (smoon's didn't exist yet) and i had installed other things besides just the windowmanager. (eg: eclair, emblem, and a few of the other 'e'-applications. after smoon opened his repo i started using that for the upgrades. eventually however e17 started random crashes, so i decided to get rid of it and install it all over agian using smoon's repo.

well it installed and i can use it but it still pulls random crashes. also i can't get emblem to run. it tells me that it is missing the default theme even though it is installed :???: 

eclair doesn't run, it complains about missing libraries. (i'll post the exact error messages when i get home)

and engage works but not like it used to. before i used it with fvwm to create thumbnails of minimized programs instead of the regular icons like in [this screenshot](http://www.clan-hash.com/~guli/fvwm/OSX-Milky/Fvwm-OSX_Milky-02.jpg) but the eap does not show up anymore. has the path to engage's taskbar changed or something? (right now the images are being copied to ~/.e/apps/engage/launcher and turned into .eap with a fvwm script)

does anyone have any ideas how to fix these probs?  :(

---

### Post by bored2k on 2005-08-09
[QUOTE=super]eclair doesn't run, it complains about missing libraries. (i'll post the exact error messages when i get home)
[/QUOTE]Eclair:
```
 Depends: libatk1.0-0, libecore0, libedje0, libeet0, libemotion0, libesmart0, libevas0, libglade2-0, libglib2.0-0. libgtk2.0-0, libjpeg62, libpango1.0-0, libtag1, libtagc0, libxml2, zlib1g, libsqlite3-0     
``` Install those.

---

### Post by super on 2005-08-09
[QUOTE=bored2k]Eclair:
```
 Depends: libatk1.0-0, libecore0, libedje0, libeet0, libemotion0, libesmart0, libevas0, libglade2-0, libglib2.0-0. libgtk2.0-0, libjpeg62, libpango1.0-0, libtag1, libtagc0, libxml2, zlib1g, libsqlite3-0     
``` Install those.[/QUOTE]

**libsqlite3-0** that's the one!

You da man, bored2k!  :-P

---

### Post by bored2k on 2005-08-09
[QUOTE=super]**libsqlite3-0** that's the one!

You da man, bored2k!  :-P[/QUOTE]
 Actually, smoon is the man here ;)

---

### Post by Neo40 on 2005-08-10
Hi,

I'd like to know if Smoon's repo has the latest CVS? I have installed E17 there are 2-3 weeks ago (I think) and there are no update yet!? 

Thanks!

---

### Post by kvidell on 2005-08-11
How do I make **entrance** work? I have it installed but I'm still getting GDM login screens.

Ideas?
- Kev

---

### Post by darkmatter on 2005-08-12
I have the same question for our resident E experts as kvidell.

How do I enable Entrance as my display manager? I had tried changing the entry in /etc/X11/default-display-manager and ended up having to use nano to reset it to gdm after Ubuntu refused to start my desired DM. :???:

---

### Post by loon on 2005-08-12
Two questions:

Is there anyway we can get the most recent e17 ported over?

and last, how can I download more modules?? Like the weather, fire, etc...

- loon

---

### Post by AndyAWS on 2005-08-12
Give the man time, he does this all himself, and it's only been a couple weeks since the last update.

Modules: In smoon's repo the emodules package has flame, snow, notes and monitor.

```
sudo apt-get install emodules
```

then 
```

enlightenment_remote -module-load [COLOR=DarkGreen]<module name>[/COLOR]
```

---

### Post by loon on 2005-08-12
[QUOTE=AndyAWS]Give the man time, he does this all himself, and it's only been a couple weeks since the last update.[/QUOTE]

whoa whoa whoa... im not rushing anyone. I am speaking in general. It doesnt have to be just him.  And thank you for your hard work btw.


And thank you for the module update.

---

### Post by loon on 2005-08-12
module update says its up to date.... hrmmm. how can I list which ones I have?? or is there a way??


and clair always says its crashed.  *shrugs*

---

### Post by super on 2005-08-12
i've got two questions for the e17 wizards:  :smile: 

will evas ever be able to render the dropshadows onto the applications? currently it seems to only render the shadows on the root window or other EFL based programs. (there are not many)

also i've seen a couple deskshots with the pager oriented vertically as opposed to horizontally. ([for an example see this screenshot](http://get-e.org/Screenshots/User_Submitted/_previews/gagis-e17.png.html) ) is this dependant on the theme being used, or can it be done with any theme. if yes, how?

thanks!  :grin:

---

### Post by AndyAWS on 2005-08-12
[QUOTE=loon]module update says its up to date.... hrmmm. how can I list which ones I have?? or is there a way??


and clair always says its crashed.  *shrugs*[/QUOTE]


The modules included in emodules are:

flame
notes
monitor
snow

I believe there are other modules that come stock...check get-e.org for info.

---

### Post by zencoder on 2005-08-13
[QUOTE=Tab]RE: task switching with ALT+TAB

It's not done from enlightenment_remote, it should work out-of-the-box  :| 

OT: I'm curious to see this "awesome new animation" the guys are raving about at Get-E :O[/QUOTE]


I literally followed this HOWTO, installed E17 and got it running 10 minutes ago.  Alt+Tab works fine (even has a cool pointer relocator when you switch)

---

### Post by Tab on 2005-08-13
[QUOTE=super]will evas ever be able to render the dropshadows onto the applications? currently it seems to only render the shadows on the root window or other EFL based programs. (there are not many)[/QUOTE]
See what I said about transparency. No alpha can be rendered over or in X11 windows, only within the evas canvas. This is why shadows can only be dropped over the desktop/modules. This does create the nice effect of making the windows seem to be on a consistent layer above the desktop.
[QUOTE=super]also i've seen a couple deskshots with the pager oriented vertically as opposed to horizontally. ([for an example see this screenshot](http://get-e.org/Screenshots/User_Submitted/_previews/gagis-e17.png.html) ) is this dependant on the theme being used, or can it be done with any theme. if yes, how?[/QUOTE]
It looks like they just set four vertical desktops rather than four horizontal, as is the default.

---

### Post by zencoder on 2005-08-13
First off, massive whuffie to Smoon and Tab for making this possible.  Thank you for your efforts and contributions to the community.

I tried poofyhairguys HOWTO for Enlightened Gnome for E16 first, and it was ok.  I find E17 much more rewarding, visually, and this HOWTO has made it so ridiculously easy to get working.

However, I have encountered my first problem,  I tried to enable the monitor emodule, and it caused a segfault.  Loading and unloading the module has no ill effects.  It's only when I go to enable the module.

I did receive some error-like output when getting the package from the repo.  For the record, I have only enabled Universe from the default repo's, then added Smoons for E.  The only things I have added beyond the apps in this HOWTO and a default Ubuntu install are kernel 2.6.10-5-686 (from default repos).
Here is the error when installing emodules:
```

zencoder@zen:~$ sudo apt-get install emodules
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  emodules
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 1057kB of archives.
After unpacking 394kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  emodules
Install these packages without verification [y/N]? y
Get:1 http://ubuntu.nooms.de hoary/ emodules 0.0.1-cvs20050813 [1057kB]
Fetched 1057kB in 3s (284kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
(Reading database ... 93973 files and directories currently installed.)
Preparing to replace emodules 0.0.1-cvs20050722 (using .../emodules_0.0.1-cvs20050813_i386.deb) ...
Unpacking replacement emodules ...
Setting up emodules (0.0.1-cvs20050813) ...
zencoder@zen:~$

```

So obviously, it looks like the perl code doesn't like the locale and other settings.  Could that have anything to do with monitor crashing?  I don't think so...but I'm not certain.  I'm not a perl OR an enlightenment module expert.

Thanks for any input you can offer.

---

### Post by smoon on 2005-08-13
[QUOTE=zencoder]First off, massive whuffie to Smoon and Tab for making this possible.  Thank you for your efforts and contributions to the community.

I tried poofyhairguys HOWTO for Enlightened Gnome for E16 first, and it was ok.  I find E17 much more rewarding, visually, and this HOWTO has made it so ridiculously easy to get working.

However, I have encountered my first problem,  I tried to enable the monitor emodule, and it caused a segfault.  Loading and unloading the module has no ill effects.  It's only when I go to enable the module.

I did receive some error-like output when getting the package from the repo.  For the record, I have only enabled Universe from the default repo's, then added Smoons for E.  The only things I have added beyond the apps in this HOWTO and a default Ubuntu install are kernel 2.6.10-5-686 (from default repos).
Here is the error when installing emodules:
```

zencoder@zen:~$ sudo apt-get install emodules
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  emodules
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 1057kB of archives.
After unpacking 394kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  emodules
Install these packages without verification [y/N]? y
Get:1 http://ubuntu.nooms.de hoary/ emodules 0.0.1-cvs20050813 [1057kB]
Fetched 1057kB in 3s (284kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
(Reading database ... 93973 files and directories currently installed.)
Preparing to replace emodules 0.0.1-cvs20050722 (using .../emodules_0.0.1-cvs20050813_i386.deb) ...
Unpacking replacement emodules ...
Setting up emodules (0.0.1-cvs20050813) ...
zencoder@zen:~$

```

So obviously, it looks like the perl code doesn't like the locale and other settings.  Could that have anything to do with monitor crashing?  I don't think so...but I'm not certain.  I'm not a perl OR an enlightenment module expert.

Thanks for any input you can offer.[/QUOTE]

I just tested it again and the monitor module works just fine for me, no segfault or anything. I don't get the perl warnings either, I think it's more likely a apt problem than a problem with the package.
Sorry, but I don't think I can help you. Maybe it works in a few weeks, you should report this to the enlightenment team, I think they will help you and try to fix it.

---

### Post by zencoder on 2005-08-14
[QUOTE=srt4play]Thank you so much! You rock!

It installed without a hitch.. just gotta figure out why my keyboard is disabled when entrance is running.. sure looks good though.[/QUOTE]

Same problem here, keyboard input not working.  I deleted all the /etc/rc*.d/ symlinks go gdm, and created links to entraced.  It works just fine, but no keyboard input is recognized.  Any ideas?

**Monitor**: thanks Smoon.  I'll keep fiddling and trying, and I'll let you know when I make some significant progress.  Thanks again.

---

### Post by darkmatter on 2005-08-14
[QUOTE=zencoder]Same problem here, keyboard input not working.  I deleted all the /etc/rc*.d/ symlinks go gdm, and created links to entraced.  It works just fine, but no keyboard input is recognized.  Any ideas?[/QUOTE]

Actually, I just found a solution to this today. Just set the default-display-manager to entranced instead od the entranced -nodaemon flag. It will work fine on the next reboot.

Now I just need to figure out why the window menu's lose the 'Edit Icon' entry when I run e 17 from entranced (also loose the run command (exige) from the left click menu. Works fine from gdm.

Also, why can I not change sessions from entrance? The session menu doesn't seem to function (does not set the selected WM). The only way I've been able to switch has been editing ~/.xsession.

---

### Post by zencoder on 2005-08-15
[QUOTE=darkmatter]Actually, I just found a solution to this today. Just set the default-display-manager to entranced instead od the entranced -nodaemon flag. It will work fine on the next reboot.
[/QUOTE]

Actually, all I did was set default-display manager to /usr/sbin/entranced with no flags.  As for my sessions, all of that works fine...there's just no keyboard.  And I don't see how using the 'no daemon' flag would change this.

Have you changed anything else?

---

### Post by darkmatter on 2005-08-15
The only other change I mad was an update to rc.d. entrance wouldn't start without it in my case.

---

### Post by darkmatter on 2005-08-16
Sweet, updates.

Nice work smoon! :smile: 

The only bug I've noticed in the new packages is that the weather module display's gibberish instead of degrees. But that's most likely a bug in the module itself.

---

### Post by super on 2005-08-16
i had originally posted this question in the warty thread:

@smoon, or other e17 wizards
i am having problems with some of the e17 configuration apps. whenever i run emblem, e_utils_eapp_edit, etc... i get the following error:
[FONT=Courier New]
No usable themes found
Segmentation Fault[/FONT]

this only seems to occur with config tool because eclips, eclair, etc... all work fine. also evidence works fine but if i select the preferences option from the menu i get the same problem.

any ideas?  :?

---

### Post by oceanelement on 2005-08-17
[QUOTE=zencoder]First off, massive whuffie to Smoon and Tab for making this possible.  Thank you for your efforts and contributions to the community.

I tried poofyhairguys HOWTO for Enlightened Gnome for E16 first, and it was ok.  I find E17 much more rewarding, visually, and this HOWTO has made it so ridiculously easy to get working.

However, I have encountered my first problem,  I tried to enable the monitor emodule, and it caused a segfault.  Loading and unloading the module has no ill effects.  It's only when I go to enable the module.

I did receive some error-like output when getting the package from the repo.  For the record, I have only enabled Universe from the default repo's, then added Smoons for E.  The only things I have added beyond the apps in this HOWTO and a default Ubuntu install are kernel 2.6.10-5-686 (from default repos).
Here is the error when installing emodules:
```

zencoder@zen:~$ sudo apt-get install emodules
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  emodules
1 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
Need to get 1057kB of archives.
After unpacking 394kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  emodules
Install these packages without verification [y/N]? y
Get:1 http://ubuntu.nooms.de hoary/ emodules 0.0.1-cvs20050813 [1057kB]
Fetched 1057kB in 3s (284kB/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory

Preconfiguring packages ...
(Reading database ... 93973 files and directories currently installed.)
Preparing to replace emodules 0.0.1-cvs20050722 (using .../emodules_0.0.1-cvs20050813_i386.deb) ...
Unpacking replacement emodules ...
Setting up emodules (0.0.1-cvs20050813) ...
zencoder@zen:~$

```

So obviously, it looks like the perl code doesn't like the locale and other settings.  Could that have anything to do with monitor crashing?  I don't think so...but I'm not certain.  I'm not a perl OR an enlightenment module expert.

Thanks for any input you can offer.[/QUOTE]

In response to zencoder's problem -> I experienced the same problem. If you answer yes to the few questions I listed then you are possibly experiencing what I had.

1. Running enlightenment with gnome?

2. Have the gnome panel up?

3. Have engage up and running? 

4. Right click the engage docker -> do you have system tray checked?

You can do two things. Either uncheck the system tray option for engage or go to the gnome panel and get rid of notification icon. 

This problem came to mind when I entered top into the terminal and saw that update-manager was using 92 percent of my cpu resources. Somehow there is a leak when engage tries to show that icon in its system tray. 

Hope this works for you  :grin: 

BTW I have the monitor module running now with no problems.

Last but least, Smoon thanks for making the repo for enlightenment. I would have not tried it out without your repo. Its up and running flawlessly as my default system  \\:D//

Oceanelement

---

### Post by jegler on 2005-08-18
I posted this problem in another thread but I thought someone here might be able to help so here it is:

I have a really annoying problem that prevents me from using eclair, I get an error saying that it can't create the table "media_files"

```
$eclair
Database: Unable to create "media_files" table: table media_files already exists
``` 

I was hoping that someone could tell me how to fix this issue.  I am assuming someone at least know how I might get rid of that database.  Any help would be much apreciated.

---

### Post by smoon on 2005-08-18
[QUOTE=jegler]I posted this problem in another thread but I thought someone here might be able to help so here it is:

I have a really annoying problem that prevents me from using eclair, I get an error saying that it can't create the table "media_files"

```
$eclair
Database: Unable to create "media_files" table: table media_files already exists
``` 

I was hoping that someone could tell me how to fix this issue.  I am assuming someone at least know how I might get rid of that database.  Any help would be much apreciated.[/QUOTE]

You can try to delete the directory **${HOME}/.eclair**
It should contain the database file **eclair.db** But I'm not sure if that will fix your problem.

---

### Post by jegler on 2005-08-18
Thanks for the suggestion but I was just on the Enlightenment 17 irc channel from which I learned that eclair is currently broken and media can only be loaded from the command line.  Thanks for everything though Smoon (esp. the repository).

---

### Post by smoon on 2005-08-19
[QUOTE=jegler]Thanks for the suggestion but I was just on the Enlightenment 17 irc channel from which I learned that eclair is currently broken and media can only be loaded from the command line.  Thanks for everything though Smoon (esp. the repository).[/QUOTE]

Oh, I didn't know that. Any idea when this will be fixed?

---

### Post by kevcart3 on 2005-08-19
Hi, I've been using E17 for a few days now, I've been trying to get the Modules (snow, flame, etc) to work and when I try to run them it doesn't give an error, but it doesn't load it either, any sugesstions?

---

### Post by smoon on 2005-08-19
[QUOTE=kevcart3]Hi, I've been using E17 for a few days now, I've been trying to get the Modules (snow, flame, etc) to work and when I try to run them it doesn't give an error, but it doesn't load it either, any sugesstions?[/QUOTE]

I just tried and they work for me. What exactly have you done to load them?

I did the following to load and show the flame module:

1. Open a terminal and type `enlightenment_remote -module-load flame'
2. Right-click on the desktop and select "Modules->Flame->Enabled"

Now the flames show up at the bottom.

---

### Post by kevcart3 on 2005-08-19
It's working now, sorry for wasting your time. I made a very stupid mistake  ](*,)

---

### Post by j.hill on 2005-08-20
I'm a little late getting into the e17 game, so I have two pretty basic questions:

1.  Has anyone else had trouble with themes?  I downloaded two of them (the "clean" and "japan" themes, specifically) and installed them in what I thought was the right place: /usr/share/enlightenment/data/themes.  E, however, refuses to see them.  Only the "default" theme appears on the theme menu when I start E, though the background for the "Japan" theme is available.  As far as I can tell I've set it up correctly...is this a bug, or a problem on my end?

2.  How do you add programs to the menus and the dock?  I couldn't find anything that worked.

---

### Post by kevcart3 on 2005-08-20
1. Try putting the themes in ~/.e/e/themes/

2. There is a menu editor, can't remember exactly where it's located, but it shouldn't be too hard to find, that will allow you to add and remove items to the menu AND dock

Hope this helps.

---

### Post by Neo40 on 2005-08-20
Hi,

I have installed the latest theme "Blue Eyed" at [http://www.get-e.org/](http://www.get-e.org/)
However, I have problem with the fonts. Fonts seem to be cut in half.
Anyone has this problem?

Thanks

---

### Post by darkmatter on 2005-08-20
[QUOTE=Neo40]Hi,

I have installed the latest theme "Blue Eyed" at [http://www.get-e.org/](http://www.get-e.org/)
However, I have problem with the fonts. Fonts seem to be cut in half.
Anyone has this problem?

Thanks[/QUOTE]

Yes. In the title, menu, and any plugins requiring the font used. Haven't found a solution other than decompiling the theme and hacking the fonts.

---

### Post by Salin on 2005-08-20
I'm following along in the code and am having issues with the evas compilation.

I've found the suggestions about removing the pentiumpro optimizations but that still gives me the same error.

```

 x86_64-linux-gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I/usr/include/freetype2 -Wall -g -I/usr/include/freetype2 -include /usr/include/png.h -include /usr/include/freetype2/freetype/internal/ftobjs.h -O3 -mcpu=pentiumpro -MT evas_polygon_main.lo -MD -MP -MF .deps/evas_polygon_main.Tpo -c evas_polygon_main.c  -fPIC -DPIC -o .libs/evas_polygon_main.o
evas_polygon_main.c: In function `polygon_point_sorter':
evas_polygon_main.c:64: error: unrecognizable insn:
(insn:HI 58 57 29 0 0x2a95f9bc60 (set (reg:SI 58)
        (plus:SI (mult:SI (reg:SI 58)
                (const_int 2 [0x2]))
            (const_int -1 [0xffffffffffffffff]))) -1 (insn_list 57 (nil))
    (nil))
evas_polygon_main.c:64: internal compiler error: in extract_insn, at recog.c:2175
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.

```

Any ideas?

EDIT:  Scratch that... I riped out all the optimizations except the -O3 ones

---

### Post by j.hill on 2005-08-20
[QUOTE=kevcart3]1. Try putting the themes in ~/.e/e/themes/

2. There is a menu editor, can't remember exactly where it's located, but it shouldn't be too hard to find, that will allow you to add and remove items to the menu AND dock

Hope this helps.[/QUOTE]

Is that a complete path, or does the tilde represent something that's been elided?

The menu editor doesn't seem to work quite right, but I'll keep playing around with it...

---

### Post by darkmatter on 2005-08-20
[QUOTE=j.hill]Is that a complete path, or does the tilde represent something that's been elided?
[/QUOTE]

Thw tilde represents your home folder. The .e folder is hidden, so just enable 'show hidden files' in nautilus to gain access to it

---

### Post by loon on 2005-08-20
wonderful update Smoon.  Doing a great job man.  Thank you so much for your hard work!!



----

Has anyone got the weather to work?? weather module is so broke for me :(

---

### Post by darkmatter on 2005-08-21
[QUOTE=loon]Has anyone got the weather to work?? weather module is so broke for me :([/QUOTE]

Yep, the weather module is completely busted on this end as well.

There has been a lot of breakage in CVS lately, and considering that anyone who is nice enough to build the .debs (smoon in this case) has to pull the code from CVS first, it's only natural to experience problems.

---

### Post by j.hill on 2005-08-21
What about the menu editor?  Is anyone having any luck there?  It's almost totally unresponsive for me.

---

### Post by loon on 2005-08-21
i have been able to get eclair to work fairly decent.

I have to do

eclair mp3/* &

in terminal with mp3 being a folder with all the mp3s I have.

---

### Post by jml90 on 2005-08-22
I'm having a problem I get an error like this



[HTML]Reading package lists... Error! E: Read error - read (21 Is a directory) E: Problem opening /var/lib/apt/lists/ubuntu.nooms.de_hoary_Packages E: The package lists or status file could not be parsed or opened. [/HTML]

---

### Post by smoon on 2005-08-22
I just wanted to let you all know that I switched to [Arch Linux](http://www.archlinux.org/) today for various reasons and **will not provide any further updates** on e17, its libs and apps. The repository will stay up for a while though.

Who knows, maybe I'll come back to Ubuntu...

---

### Post by christooss on 2005-08-23
[QUOTE=smoon]I just wanted to let you all know that I switched to [Arch Linux](http://www.archlinux.org/) today for various reasons and **will not provide any further updates** on e17, its libs and apps. The repository will stay up for a while though.

Who knows, maybe I'll come back to Ubuntu...[/QUOTE]
 So sorry to hear that. :(

---

### Post by christooss on 2005-08-23
Does any one have will and knowledgement to continue spoon's work?

It would be so nice to have e17 in breezy

---

### Post by darkmatter on 2005-08-24
[QUOTE=christooss]Does any one have will and knowledgement to continue spoon's work?

It would be so nice to have e17 in breezy[/QUOTE]

I'd love to help maintain these packages if others are willing to volunteer as well.

I would do it on my own, but can't afford the extra bandwith.

---

### Post by christooss on 2005-08-24
Maybe guys at backports would share some bandwith?

---

### Post by bored2k on 2005-08-24
[QUOTE=christooss]Maybe guys at backports would share some bandwith?[/QUOTE]
 An official request would be needed in the appropiate forum for JDong to take notice.

---

### Post by Salin on 2005-08-25
Does anybody have the build script that was on like the third page of the thread?  If so I'll build the AMD64 packages...

I'll even see about hosting the packages(AMD64) myself.

EDIT:
Scratch that. I found the script.  Now if someone will help me with setting up a repository...

---

### Post by fenwik on 2005-08-29
So I followed the instructions and I have E17 semi-working.

I can't seem to get emblem to work. Everytime I try to start it I get an error that says "Enlightenment was unable to run the program emblem. The command was not found." Does anybody know what's wrong?

---

### Post by loon on 2005-08-29
[QUOTE=smoon]I just wanted to let you all know that I switched to [Arch Linux](http://www.archlinux.org/) today for various reasons and **will not provide any further updates** on e17, its libs and apps. The repository will stay up for a while though.

Who knows, maybe I'll come back to Ubuntu...[/QUOTE]



Why the switch?? Im always open to other distros.

---

### Post by Tab on 2005-08-30
[QUOTE=fenwik]So I followed the instructions and I have E17 semi-working.

I can't seem to get emblem to work. Everytime I try to start it I get an error that says "Enlightenment was unable to run the program emblem. The command was not found." Does anybody know what's wrong?[/QUOTE]

Did you install eutils?

---

### Post by volvoguy on 2005-08-30
Anybody using Smoon's install script in Breezy yet? All was going fine until I got to "Building .deb of epeg". It exited telling me to check ~/e17install/compile_logs/epeg.log. All the log said was:

found eof where expected first heading at /usr/lib/dpkg/parsechangelog/debian line 136.
dpkg-buildpackage: unable to determine source package is

Anyone know how to troubleshoot this? If so, and I can get it working again, do I need to start from scratch again? I decided to use the install script because it sounds like that is what was used to build the packages in the repo (which I had good luck with on Hoary). I didn't have much luck at all with Rasterman's own get-e.sh script (seemed to only build the bare minimum).

---

### Post by Weav on 2005-08-30
Sorry just a quick question when i try to add Smoon's repository it gives me this error
```

steve@ubuntu:~$ sudo echo "deb http://ubuntu.nooms.de/ hoary/" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

```
and it doesn't even ask me for root password or anything? Anyone know what is going on?

Also i edited the preferences to point to the newest e17 version but when i try to install enlightenment it says i already have the latest version, when i only have e16 on my system.

Thanks a lot!

---

### Post by darkmatter on 2005-08-30
[QUOTE=Weav]Sorry just a quick question when i try to add Smoon's repository it gives me this error
```

steve@ubuntu:~$ sudo echo "deb http://ubuntu.nooms.de/ hoary/" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied

```
and it doesn't even ask me for root password or anything? Anyone know what is going on?

Also i edited the preferences to point to the newest e17 version but when i try to install enlightenment it says i already have the latest version, when i only have e16 on my system.

Thanks a lot![/QUOTE]

If you read elsewhere in this and a few other of the E 17 threads, you will see that smoon has left Ubuntu for the moment.

He is no longer packaging nor hosting the .debs for E 17

---

### Post by bam on 2005-08-31
[QUOTE=darkmatter]If you read elsewhere in this and a few other of the E 17 threads, you will see that smoon has left Ubuntu for the moment.

He is no longer packaging nor hosting the .debs for E 17[/QUOTE]
 well then it seems I will wait for this "problem to be solved" before I try anything

---

### Post by fenwik on 2005-08-31
[QUOTE=Tab]Did you install eutils?[/QUOTE]

Yes I did.

---

### Post by smoon on 2005-08-31
[QUOTE=darkmatter]If you read elsewhere in this and a few other of the E 17 threads, you will see that smoon has left Ubuntu for the moment.

He is no longer packaging nor hosting the .debs for E 17[/QUOTE]

Packages from August the 13. are still in the repository...

---

### Post by smoon on 2005-08-31
[QUOTE=loon]Why the switch?? Im always open to other distros.[/QUOTE]

I can't tell exactly why. Arch just feels better for me. It's a mix of the distros I liked most (before I found Arch) and simplicity. I suggest you check out their [webpages](http://www.archlinux.org/about.php) and try it out if you like.

---

### Post by darkmatter on 2005-08-31
[QUOTE=smoon]Packages from August the 13. are still in the repository...[/QUOTE]

Awesome! :)  Thanks smoon.

I was just wondering, is there a way to access you repo other than apt? (I've tried to access by the web before, but permission was denied)

I'd like to build a local repository for quick and dirty installs, as well as keep hold of the packages for those people who want a no headache install.

---

### Post by darkmatter on 2005-08-31
[QUOTE=darkmatter]Awesome! :)  Thanks smoon.

I was just wondering, is there a way to access you repo other than apt? (I've tried to access by the web before, but permission was denied)

I'd like to build a local repository for quick and dirty installs, as well as keep hold of the packages for those people who want a no headache install.[/QUOTE]

Nevermind, I re-enabled your repository and DL'd the debs again...

---

### Post by christooss on 2005-09-01
Just a question. Which script make a deb packages. I can't find it. Maybe Im lazy or blind.

If I make those deb packages for breezy can than user DL them from Page and dpkg -i packagename.deb

---

### Post by darkmatter on 2005-09-01
[QUOTE=christooss]Just a question. Which script make a deb packages. I can't find it. Maybe Im lazy or blind.[/QUOTE]

I have a copy. PM me your addy and I'll mail it to you. :) 

(all credit to smoon, it's a copy of his script.)

---

### Post by christooss on 2005-09-01
Check PM's

Does this scritpt work in breezy?

---

### Post by darkmatter on 2005-09-01
[QUOTE=christooss]Check PM's

Does this scritpt work in breezy?[/QUOTE]

Checked. Just sent the script.

I haven't tried it in breezy yet, but it should work (hopefully)...

If it doesn't, I'll have to look into hacking it. ;-)

---

### Post by christooss on 2005-09-01
I will try it and I will report to you if installation went well. Another question.

I just have to run this script and I will have E17 installed?

---

### Post by Ride Jib on 2005-09-01
Here are a few issues I have from enjoying E17, maybe someone can shed some light on these...

1. New window auto-focus: when using gaim and I open an IM window, it doesn't put me into that window automatically. I need to click on the window first and then start typing.

2. Window focus, via mouse. There are two problems I have with this.. 
   a.) the window doesn't come to the front unless I click on the top title bar. I want to click anywhere on the window and bring it to the front. And b.) If I am typing in a window and my mouse drifts onto another window, it focuses keyboard input into that window. I only want to focus on windows i click on, not hover over. 

I am sure these are minor issues, but being the newb to enlightenment that I am, I cannot figure them out.

Thanks

---

### Post by Tab on 2005-09-01
[QUOTE=Ride Jib]Here are a few issues I have from enjoying E17, maybe someone can shed some light on these...

1. New window auto-focus: when using gaim and I open an IM window, it doesn't put me into that window automatically. I need to click on the window first and then start typing.

2. Window focus, via mouse. There are two problems I have with this.. 
   a.) the window doesn't come to the front unless I click on the top title bar. I want to click anywhere on the window and bring it to the front. And b.) If I am typing in a window and my mouse drifts onto another window, it focuses keyboard input into that window. I only want to focus on windows i click on, not hover over. 

I am sure these are minor issues, but being the newb to enlightenment that I am, I cannot figure them out.

Thanks[/QUOTE]

These are both the same issue: Enlightenment is configured to use the MOUSE focus policy. You want to use CLICK. Use the command enlightenment_remote -focus-policy-set CLICK, IIRC, to change it. You can see more commands and options by just running enlightenment_remote.

---

### Post by darkmatter on 2005-09-01
[QUOTE=christooss]I will try it and I will report to you if installation went well. Another question.

I just have to run this script and I will have E17 installed?[/QUOTE]

As long as you have cvs, your compilers and the like, yes.

The script will fetch E 17 from cvs, builds .debs from the sources, and installs them on the system.

---

### Post by Ride Jib on 2005-09-01
[QUOTE=Tab]These are both the same issue: Enlightenment is configured to use the MOUSE focus policy. You want to use CLICK. Use the command enlightenment_remote -focus-policy-set CLICK, IIRC, to change it. You can see more commands and options by just running enlightenment_remote.[/QUOTE]

Excellent. Thank you very much, Tab!

---

### Post by EnderTheThird on 2005-09-04
The command for adding Smoon's repository doesn't appear to be working for me:

```
$ sudo echo "deb http://ubuntu.nooms.de/ hoary/" >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
```

Edit:  Did some reading of previous pages.  If Smoon is no longer hosting the repository, what do I need to do to install e17?

---

### Post by SFN on 2005-09-04
[QUOTE=EnderTheThird]Edit:  Did some reading of previous pages.  If Smoon is no longer hosting the repository, what do I need to do to install e17?[/QUOTE]

While you have numerous options, there are two that are well detailed in these forums. One is using CVS via an updater script. That's described [here](http://ubuntuforums.org/showthread.php?t=59568) .

The oether is using the apt repositories available via Elive. That info is [here](http://ubuntuforums.org/showthread.php?t=61488).

Both processes work well for some and not at all for others. I'd recommend reading both threads completely before making your decision.

---

### Post by xequence on 2005-09-05
Thank you for this howto :) E17 beats E16 by alot... It is quite ackward though, ill have to get used to it. Looks cool though :)

---

### Post by caino on 2005-09-12
edit: nevermind, i got it...wow i feel daft.

---

### Post by nebula on 2005-09-14
Hey, I'm running a fresh copy of ubuntu breezy right now, and followed the how-to above but I cannot seem to install my e17. 

This is what I am trying
```
root@localhost:/home/nebula# apt-get install enlightenment eutils
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  enlightenment: Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
  eutils: Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libengrave0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
          Depends: edje0-bin but it is not going to be installed
E: Broken packages
```
sources.list:
```
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/
```

at the bottom of my /etc/apt/sources.list


Can you help me?

Best regards, Nebula

---

### Post by christooss on 2005-09-14
[QUOTE=nebula]Hey, I'm running a fresh copy of ubuntu breezy right now, and followed the how-to above but I cannot seem to install my e17. 

This is what I am trying
```
root@localhost:/home/nebula# apt-get install enlightenment eutils
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  enlightenment: Depends: libevas0 but it is not going to be installed
                 Depends: libecore0 but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
  eutils: Depends: libecore0 but it is not going to be installed
          Depends: libedje0 but it is not going to be installed
          Depends: libengrave0 but it is not going to be installed
          Depends: libepsilon0 but it is not going to be installed
          Depends: libesmart0 but it is not going to be installed
          Depends: libevas0 but it is not going to be installed
          Depends: libewl0 but it is not going to be installed
          Depends: edje0-bin but it is not going to be installed
E: Broken packages
```
sources.list:
```
deb [http://ubuntu.nooms.de/](http://ubuntu.nooms.de/) hoary/
```

at the bottom of my /etc/apt/sources.list


Can you help me?

Best regards, Nebula[/QUOTE]

Its well writen

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

---

### Post by nebula on 2005-09-20
Yeah, my fault. I rearranged my sources.list as descibed earlier and it installed! Threw it off again though because I cannot run e17 full with kubuntu-desktop installed as well. Bummer. Do hope that enlightenment gets released soon though. It is getting better every time!
Thanks for the help anyway!

---

### Post by Cyfr on 2005-09-23
I followed the guide on page 1 and everything installed (execept the Desktop Entry, which I searched for on these forums, and created E17.desktop etc...)

Now.. when I start my laptop and click E17 in the sessions and login, it just loads a black screen which eventually turns white.. Any ideas?

---

### Post by dcmalllory on 2005-09-23
[QUOTE=darkmatter]As long as you have cvs, your compilers and the like, yes.

The script will fetch E 17 from cvs, builds .debs from the sources, and installs them on the system.[/QUOTE]

I found a copy of the "e17install.sh" script, which I believe to be  the correct script being discussed. Executing this script brings down all the files from CVS, and indeed starts compiling/building, etc. However, every time it tries to compile the "imlib2" files, it bombs with syntax errors on the source for the library.

Is this a script problem, a gcc version problem,  or are the sources for the libs just broken this week. I have met all the dependencies for automake, gcc, etc. (at least according to the script). The first two  (edt and eet)  build fine.

If anyone has any ideas how to fix this I would appreciate it - I would really love to get an up-to-date build of E17.

Best Regards,

DCM

---

### Post by dcmalllory on 2005-09-23
[QUOTE=Cyfr]I followed the guide on page 1 and everything installed (execept the Desktop Entry, which I searched for on these forums, and created E17.desktop etc...)

Now.. when I start my laptop and click E17 in the sessions and login, it just loads a black screen which eventually turns white.. Any ideas?[/QUOTE]

I originally had this problem on two different machines. I started up the session as "gnome - just this session" and it came up fine. From that point on I could start up Enlightement on its own with no problems.

Hope this helps.

DCM

---

### Post by angkor on 2005-09-24
I just had to come in here and say thanks for the great howto and smoon's repos. I absolutely love E17 and I'm using it quite often right now. To me it's the best looking desktop I've had so far...and _fast_. I can't wait for the final release, I'm already considering using E17 as default right now. 

Everything works as it should, the only thing I've encountered is that it sometimes crashes when I'm switching tabs in Firefox (which requires a gdm restart from another comp cause the system is hard-locked).

Thanks and keep up the good work!

---

### Post by foxy123 on 2005-09-24
[QUOTE=angkor]I just had to come in here and say thanks for the great howto and smoon's repos. I absolutely love E17 and I'm using it quite often right now. To me it's the best looking desktop I've had so far...and _fast_. I can't wait for the final release, I'm already considering using E17 as default right now. 

Everything works as it should, the only thing I've encountered is that it sometimes crashes when I'm switching tabs in Firefox (which requires a gdm restart from another comp cause the system is hard-locked).

Thanks and keep up the good work![/QUOTE]
Please note that Smoon does not maintain this topic and repository anymore. If you need more up-to-date versions you may consider either use the script in one of the topics or elive repository which is frequently updated. Or you can build it yourself from cvs ocasionally.

---

### Post by angkor on 2005-09-24
[QUOTE=foxy123]Please note that Smoon does not maintain this topic and repository anymore. If you need more up-to-date versions you may consider either use the script in one of the topics or elive repository which is frequently updated. Or you can build it yourself from cvs ocasionally.[/QUOTE]

Ke thanks, I'll look into that.

---

### Post by dvlspawn on 2005-09-29
[QUOTE=darkmatter]I have a copy. PM me your addy and I'll mail it to you. :) 
(all credit to smoon, it's a copy of his script.)[/QUOTE]

w00t.. Thanks for getting me a copy of Smoon's script.  With a few tweaks I was able to get most of E built on Breezy.. minus some of the modules, eclair and entrance which didn't build into debs for me for various reasons.  

But other than that it looks pretty good.  No crashes or weird behavior so far.  If anyone is interested, I can probably set up an apt source.  I'll probably poke a bit more and see about getting the rest compiled as well.

-jason

---

### Post by Tab on 2005-09-29
HOWTO updated to reflect the current status of the repository.

---

### Post by SFN on 2005-09-29
[QUOTE=Tab]note that it's not necessary to modify libc6, and this repo can simply be used as a drop-in for Smoon's[/QUOTE]
:shock: 
Perhaps it's time for a new collaborative HOWTO that encompasses all of the combined info?

---

### Post by Tab on 2005-09-29
The way things are now, we might as well just wait for Breezy.

---

### Post by SFN on 2005-09-29
Mmm, yes. Good point.

---

### Post by dvlspawn on 2005-09-29
I have a Breezy repo for e17 setup at 
```

deb http://ubuntu.codegrinder.com/ breezy/

```

This is the first debian apt repo I've setup, so if anyone has a link to a good howto, I'd appreciate a PM.  I'm not sure if I need the Release.gpg,etc or what it's used for.  

But, I digress, these packages work for me on Breezy.. If they work for you too, awesome :)

---

### Post by Tab on 2005-09-30
Great! Looks like we have our work cut out for us :o

---

### Post by rejser on 2005-09-30
installed today usings smoon's repo, tried it before on the old (before the 13th august debs), but now I can't launch programs, enlightenment kills itself then.
Anyone had similar experience?

---

### Post by Sav on 2005-09-30
[QUOTE=dvlspawn]I have a Breezy repo for e17 setup at 
```

deb http://ubuntu.codegrinder.com/ breezy/

```

This is the first debian apt repo I've setup, so if anyone has a link to a good howto, I'd appreciate a PM.  I'm not sure if I need the Release.gpg,etc or what it's used for.  

But, I digress, these packages work for me on Breezy.. If they work for you too, awesome :)[/QUOTE]

Hi thanks for your work.
I added the repo, but synaptic "likes" the official version. It upgrades only few packages. How can I force to install e17 from your repo?

---

### Post by dvlspawn on 2005-09-30
[QUOTE=Sav]Hi thanks for your work.
I added the repo, but synaptic "likes" the official version. It upgrades only few packages. How can I force to install e17 from your repo?[/QUOTE]
Setup your /etc/apt/preferences as mentioned in the first post of this thread.  Tab's howto should work fine as long as you substitute the breezy repo.

---

### Post by Sav on 2005-09-30
[QUOTE=dvlspawn]Setup your /etc/apt/preferences as mentioned in the first post of this thread.  Tab's howto should work fine as long as you substitute the breezy repo.[/QUOTE]


Thanks I'll try it.

---

### Post by spindley on 2005-09-30
[QUOTE=dvlspawn]I have a Breezy repo for e17 setup at 
```

deb http://ubuntu.codegrinder.com/ breezy/

```
This is the first debian apt repo I've setup, so if anyone has a link to a good howto, I'd appreciate a PM.  I'm not sure if I need the Release.gpg,etc or what it's used for.  
But, I digress, these packages work for me on Breezy.. If they work for you too, awesome :)[/QUOTE]
Your repository worked for me on breezy too, thanks.  However, have you had any luck adding launchers to the ibar, or menu?  I've tried a couple using the manual build way (editing build.sh and creating .eaps). Every single one of them, when launched, freeze up my entire desktop.  But the apps will run from xterm, or "Run Command" in the menu.  Also, the defaults in ibar and the menu run fine (firefox, xchat, etc).
Mike

---

### Post by SFN on 2005-09-30
[QUOTE=Tab]See this thread for a smiliar method using the repository provided by Elive (note that it's not necessary to modify libc6, and this repo can simply be used as a drop-in for Smoon's. Some of the install names have changed, however.)[/QUOTE]

Tab,

I just wanted to check something. Were you able to get e17 working from the Elive repo without updating libc6? If so, was that on a clean install? Or are you just suggesting the Elive repo as a replacement for Smoon's repo if one has already installed from Smoon's?

I've been trying to egt around adding those debs when using the Elive repo without success.

---

### Post by dvlspawn on 2005-09-30
[QUOTE=spindley]Your repository worked for me on breezy too, thanks.  However, have you had any luck adding launchers to the ibar, or menu?  I've tried a couple using the manual build way (editing build.sh and creating .eaps). Every single one of them, when launched, freeze up my entire desktop.  But the apps will run from xterm, or "Run Command" in the menu.  Also, the defaults in ibar and the menu run fine (firefox, xchat, etc).
Mike[/QUOTE]
I was able to create a new eap with  e_util_eapp_edit, but I found that to be a pain since I didn't want different icons.  So, I've taken to copying system one's to /tmp, using  e_util_eapp_edit to edit them and then putting them in ~/.e/e/applications/all .. Adding them to the bar, menu and startup has worked well with either the menu editting tool, or by vi'ing the .order files myself.

I haven't tried the manual way.

---

### Post by rejser on 2005-10-03
anyone that has trouble with eclair?
if I try running eclair I get
*"eclar: error running shared libraries: libtag_c_so.0: Cannot open shared object......"*

Edit: solved the problem, but having big playlist-problems with eclair though.

---

### Post by Tab on 2005-10-05
[QUOTE=SFN]Tab,
I just wanted to check something. Were you able to get e17 working from the Elive repo without updating libc6? If so, was that on a clean install? Or are you just suggesting the Elive repo as a replacement for Smoon's repo if one has already installed from Smoon's?
I've been trying to egt around adding those debs when using the Elive repo without success.[/QUOTE]
It's not a clean install, but I never modified libc6, so I don't see why it would be different (although it may). I'm not sure.
Anyway, I just saw this:
[QUOTE="Smoon"]Once that new server is in place and all the sites have been moved over, I'll be quickly adding support for more Debian architectures, distributions and derivatives like Ubuntu.[/QUOTE]
This is very good news, since Ubuntu will now have an official repository to draw from. It could nonetheless easily leave room for independent repositories like the ones we have now, for a number of reasons. Customizability possibly being one, a faster release cycle being another. We'll have to wait and see. Hopefully this repo will be available on or shortly after the release of Breezy.

---

### Post by SFN on 2005-10-05
Wow. Great news!

Looking forward to that.

---

### Post by foxy123 on 2005-10-05
[QUOTE=Tab]It's not a clean install, but I never modified libc6, so I don't see why it would be different (although it may). I'm not sure.
Anyway, I just saw this:
This is very good news, since Ubuntu will now have an official repository to draw from. It could nonetheless easily leave room for independent repositories like the ones we have now, for a number of reasons. Customizability possibly being one, a faster release cycle being another. We'll have to wait and see. Hopefully this repo will be available on or shortly after the release of Breezy.[/QUOTE]
where did he post that?

---

### Post by Tab on 2005-10-05
[QUOTE=foxy123]where did he post that?[/QUOTE]
His blog, at shadoi.soulmachine.net

---

### Post by Tab on 2005-10-15
Oh no, what might [this]("http://shadoi.soulmachine.net/2005/10/whats-that-smell.html") be?

---

### Post by JOKe on 2005-11-15
how can i start enlightment .. ? 
i fallow the HOWTO and i install everything 
how can i start it .

i try this : login to failsave terminal and type "enlightment" 
i have black screan and white screan after this this was all.

---

### Post by tommie-lie on 2006-02-03
Since smoon is no longer updating his packages and shadoi's packages are too old for me, I looked for smoons installation script and compiled the packages myself. I'll publish them as soon as possible and I hope that I can provide more recent updates than shadoi does (no offence, I perfectly understand that he does not find the time) for a long term.
I will publish informations on [http://www.tommie-lie.de/blog](http://www.tommie-lie.de/blog) and here as soon as there is something to tell.

---

### Post by Tab on 2006-02-03
Great news! Shadoi's update schedule (or lack thereof) was getting to be a real pain. Will you be building for Breezy, or Hoary (since this thread is from way back then)?

---

### Post by tommie-lie on 2006-02-03
I'm only using Breezy, so the only packages I use on my box will be for Breezy (and for Dapper as soon as it is stable).
There were many people in the German Ubuntu forum that had problems with smoon's script, and if I recall correctly they used Hoary (ubuntuusers.de is currently down). So I can't say if the script will work for me or if I can make it work.
My current plan is to provide Breezy packages as long as possible and Dapper packages as soon as possible (and reasonable). That's for sure. As far as Hoary is concerned, I'll try my best but I promise nothing.

---

### Post by Tab on 2006-02-03
Oh, no, I'm not personally interested in Hoary packages (and I would assume most others using such a cutting-edge WM as E17 would have moved on to Breezy anyway). I was just afraid maybe you were only doing packages for Hoary, since this thread is way back in the Hoary forums. Your plan of action sounds great. Can't wait to try some post-October E17. Thanks again!

---

### Post by tommie-lie on 2006-02-04
[QUOTE=Tab](and I would assume most others using such a cutting-edge WM as E17 would have moved on to Breezy anyway)[/quote]Yes, very likely so.

[quote=Tab]I was just afraid maybe you were only doing packages for Hoary, since this thread is way back in the Hoary forums.[/quote]I chose this thread as I use smoon's script and plan to be the successor of smoon, that's all. I could not post in the CVS thread, as it has nothing to do with CVS. The same is true for the ELive and shadoi thread. And I did not want to write an own thread because it is not my nature to cry out loud without having much to show (and the last thing this thread was about was the lack of debian packages ;-)).

---

### Post by tommie-lie on 2006-02-06
Sorry for the delay, but I had some difficulties with missing/empty files after checkout and compilation took longer than I'd expected.
But now, the repository is online!
Thanks to Chris George for providing the webspace and traffic!
To get the repository, put the following line in your /etc/apt/sources.list:
```
deb http://www.enlightenment.technatica.net/breezy/ ./
``` and add the same pinning rules to you apt preferences file like for smoon's repository: ```
Package: enlightenment
Pin: version 0.16.999.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.16.999.*
Pin-Priority: 999
```
Then simply apt-get update your database and get the new enlightenment packages.

The repository is signed against my key. You can find it at [http://www.tommie-lie.de/pub/public.key](http://www.tommie-lie.de/pub/public.key). To add it to apt's key database type: ```
wget http://www.tommie-lie.de/pub/public.key
sudo apt-key add public.key
```

I had to use the emotion version that was updated to CVS two days ago. Someone replaced the requirements from GStreamer 0.8 to 0.10 and broke the current emotion library. I don't know yet what I'll do in the future when emotion has changed so much that other things start to break.


If someone needs packages for Hoary and the ones for Breezy don't work, just raise your arms and I'll do what I can.

---

### Post by Tab on 2006-02-07
Alright, most things work perfectly over here. I upgraded directly from my previous Shadoi-based install. However, a few things that I noticed: the E mouse cursor is stuck in two-color mode, and so I'm forced to use the X cursor theme instead. Don't know if this is a fault with current E CVS or the installation. Second is that Eclair fails to start, complaining about a missing emotion_decoder_xine module. > michael@jo-0533-1:~$ eclair
No module. Error: /usr/lib/emotion/emotion_decoder_xine.so: cannot open shared object file: No such file or directory
DEL: sd->video = (nil)

One other thing is that immediately after install, E refused to start up. I had to force an upgrade to libecore0, bringing with it libdirectfb, otherwise E would fail out before starting with an undefined symbol error with ECORE_EXE_EVENT_DEL. This may have just been an upgrade issue coming from Shadoi's repo.

Otherwise, all's well. Using it as we speak :)

---

### Post by tommie-lie on 2006-02-08
[QUOTE=Tab]Alright, most things work perfectly over here.[/quote]Good to hear. :-)

[quote=Tab]the E mouse cursor is stuck in two-color mode, and so I'm forced to use the X cursor theme instead.[/quote]Yes, I noticed that and thought it only affects my installation. I found a discussion in E's developer mailing list and found that it was my fault. I should've read all the output, even if the libraries compile. Xcursor headers were missing and now there is only the monochrome cursor available. GL and other backends for Evas should not work, either, for the same reason. I'll try to solve it and recompile the packages.

[quote=Tab]Second is that Eclair fails to start, complaining about a missing emotion_decoder_xine module.[/quote]Yes, that's a "known bug", more or less...
Since January 23, emotion depends on libxine 1.1.1 (see [the changes in configure.in](http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/libs/emotion/configure.in?rev=1.30&view=log). Version 1.27 checked for xine 1.0.0, version 1.28 and later checks for 1.1.2 or 1.1.1, respecitively) which is not available in Breezy. You can use gStreamer instead:
```
eclair -m gstreamer
```worked for me.
As already mentioned, newer versions of emotion depend on gStreamer 0.10 which is also not available in Breezy. I don't know how to solve this, yet, so I expect all modules and programs that depend on a working emotion to break upon the next release of my packages (I will see if the old version of emotion that only needs gStreamer 0.8 will do, but if the emotion-API changes, many things will break).

[quote=Tab]One other thing is that immediately after install, E refused to start up. I had to force an upgrade to libecore0, bringing with it libdirectfb, otherwise E would fail out before starting with an undefined symbol error with ECORE_EXE_EVENT_DEL.[/quote]Could be a problem with the missing optional headers mentioned above.

---

### Post by tommie-lie on 2006-02-08
[QUOTE=tommie-lie]You can use gStreamer instead:
```
eclair -m gstreamer
```worked for me.[/QUOTE]Sorry, 
false alarm. eclair starts up but does not play anything. I don't know if this has something to do with gStreamer vs xine or if it's just me.

---

### Post by tommie-lie on 2006-02-19
I almost forgot the packages...
I recompiled them and revisioned them (they now use the "ubuntu1" suffix). However, they are not updated, it is still the same codebase that was used in the previous version, so there are no bugfixes, feature enhancements, whatsoever, that were committed to CVS in the last few days.
I hope they work now.

---

### Post by NoWhereMan on 2006-03-18
apt-get'ing now :) thank you, man :)

**edit:** hmmm
```
DYNAMIC DETERMINED PREFIX: /usr
enlightenment: symbol lookup error: enlightenment: undefined symbol: eet_data_descriptor2_new

```

---

