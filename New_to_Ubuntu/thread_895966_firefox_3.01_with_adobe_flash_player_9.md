---
title: "firefox 3.01 with adobe flash player 9"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-20
i use ubuntu8.04.i installed adobe flash player 9, flashplugin non-free,libflashsupport,and got flash videos working.but,once in a while,while i am watching videos,firefox crashes,i mean gets terminated on its own,why does this happen.will upgrading to flash player 10 help?how can i install adobe flash player 10,will i have to reinstall flashplugin,libflashsupport?

---

### Post by tuxxy on 2008-08-20
Flash 10 may improve some aspects, you could always try and see, [heres a guide]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html") to help you install it if you do, I currently use Flash 9 and works fine.

---

### Post by stonecoldjha on 2008-08-20
that's for 64 bit ubuntu.

---

### Post by t0p on 2008-08-20
Flash 9 is the problem.  **Flash 10 is the answer!!!**

[Here is a guide]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472") to setting up Flash 10 on Hardy (8.04).  My firefox used to crash when I opened pages of video.  So I followed the advice in that link and now Flash 10 works perfectly.

---

### Post by aysiu on 2008-08-20
> **stonecoldjha said:**
> i use ubuntu8.04.i installed adobe flash player 9, flashplugin non-free,libflashsupport,and got flash videos working.but,once in a while,while i am watching videos,firefox crashes,i mean gets terminated on its own,why does this happen.will upgrading to flash player 10 help?how can i install adobe flash player 10,will i have to reinstall flashplugin,libflashsupport?
Can you close Firefox, open [a terminal](http://www.psychocats.net/ubuntu/terminal), paste in the command ```
firefox
``` and when it crashes, paste the terminal output back here?

---

### Post by stonecoldjha on 2008-08-21
the following is the output:
[B]
sonu@sonu-desktop:~$ firefox
/home/sonu/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/sonu/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/sonu/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/sonu/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(firefox:6120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:6120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault
sonu@sonu-desktop:~$ 
[/B]
and then the firefox crashed.

---

### Post by StOoZ on 2008-08-21
> **tuxxy said:**
> Flash 10 may improve some aspects, you could always try and see, [heres a guide]("http://www.myscienceisbetter.info/2008/05/install-adobe-flash-player-10-on-ubuntu-using-nspluginwrapper.html") to help you install it if you do, I currently use Flash 9 and works fine.

its for 64bit , how to install in on 32bit 8.04?

---

### Post by silkstone on 2008-08-21
I hope aysiu will be able to suggest a way of curing this, but I was not able to with Flash 9 on 32-bit Hardy.

I installed Flash 10 using the method towards the end of the following post, under the heading 'Troubleshooting - Adobe Flash Player'.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

The version I installed was Flash 10 beta 1, and I have had no crashes or unexpected behaviour at all with that . The only problem is that this version does not support transparency, but neither does Flash 9.

Unfortunately, the later versions of Flash 10 - beta 2 and now the Release Candidate - have not worked for me - the 'unexpected closing' problem returned. So, if nobody has a better idea, my suggestion would be to find the beta 1 version and use that - you only need the file libflashplayer.so.

---

### Post by stonecoldjha on 2008-08-21
but then how do i uninstall adobe flash player 9,and everything like flashplugin non-free?i want to uninstall it completely.and then how can i install flash player 10(the stable beta 1 version)?i would prefer going through an easy guide to do that,u see i am a newbie.

---

### Post by kansasnoob on 2008-08-21
If nothing else has worked please try this, type (or cut-n-paste) in terminal:

```
sudo apt-get remove --purge flashplugin-nonfree libflashsupport
```

Then:

```
nspluginwrapper
``` No need or desire for sudo here!

If it's installed you'll see this:

[ATTACH]82340[/ATTACH]

And then you'll want to do this:

```
sudo apt-get install --reinstall nspluginwrapper
```

If it's not, well, it'll tell you it's not, and you'll want to do this instead:

```
sudo apt-get install nspluginwrapper
```

Then:

```
sudo apt-get install libflashsupport
```

And finally:

```
sudo apt-get install flashplugin-nonfree
```

Then close Firefox. Restart Firefox now and see if that helped.

I can't explain why but it's worked for me in both Hardy and Mint Elyssa.

---

### Post by stonecoldjha on 2008-08-21
this is the terminal output i got:

sonu@sonu-desktop:~$ sudo apt-get remove --purge flashplugin-nonfree libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages will be REMOVED:
  libflashsupport*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107220 files and directories currently installed.)
Removing libflashsupport ...
sonu@sonu-desktop:~$ nspluginwrapper
bash: nspluginwrapper: command not found
sonu@sonu-desktop:~$ sudo apt-get install --reinstall nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
sonu@sonu-desktop:~$ sudo apt-get install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper

---

### Post by philinux on 2008-08-21
Are you running 32bit? If so nsplugin.. is not needed.

---

### Post by elmoosecapitan on 2008-08-21
Just a point of interest, Firefox 3.0.1 does crash occasionally. It is still a little buggy and thus isn't entirely stable. It works and does it's job, but often enough it WILL crash.

---

### Post by stonecoldjha on 2008-08-21
i would really appreciate if someone could tell me a complete solution to watching youtube videos,and other flash videos in a trouble free manner without crashing firefox?nothing has worked so far.i even tried installing the flash player 10 by running the script in the terminal(though i did not remove flash 9),but nothing saves ff3 from crashing.does being a linux user deprive me of the right to watch flash videos online without any troubles?i am really frustrated.

---

### Post by stonecoldjha on 2008-08-21
in my firefox,i opened about:plugins,and saw things pertaining to both flash player 10 and flash player 9.

---

### Post by stonecoldjha on 2008-08-21
what about gnash?does it work well,or is it just as niggling?is there something else that can be tried?

---

### Post by kansasnoob on 2008-08-21
> **philinux said:**
> Are you running 32bit? If so nsplugin.. is not needed.

I know, but read here:

[http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox](http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox)

> He utilizes nspluginwrapper as a interface layer between libflashsupport and Pulseaudio. What makes it special, is that nspluginwrapper originally serves as a wrapper to include 32bit Flash into 64bit Firefox. It wasn't meant to run at 32bit Ubuntu, but it still works.

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> this is the terminal output i got:

sonu@sonu-desktop:~$ sudo apt-get remove --purge flashplugin-nonfree libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed
The following packages will be REMOVED:
  libflashsupport*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 107220 files and directories currently installed.)
Removing libflashsupport ...
sonu@sonu-desktop:~$ nspluginwrapper
bash: nspluginwrapper: command not found
sonu@sonu-desktop:~$ sudo apt-get install --reinstall nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
sonu@sonu-desktop:~$ sudo apt-get install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper

You notice that even right after the first command you get this:

> apt-get remove --purge flashplugin-nonfree libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-nonfree is not installed, so not removed

The important part of that is, "Package flashplugin-nonfree is not installed".

Then also this:

> E: Couldn't find package nspluginwrapper

is telling me that nspluginwrapper is not even in the repositories.

Now, give me a few minutes, I have to check in some freight, but I'm not abandoning you!

In the meanwhile install ubuntu-restricted-extras:

```
sudo apt-get install ubuntu-restricted-extras
```

Then check your software sources (System > Administration > Software Sources), example:

[ATTACH]82349[/ATTACH]

[ATTACH]82350[/ATTACH]

[ATTACH]82351[/ATTACH]

and then:

```
sudo apt-get update
```

Then see if you can install nspluginwrapper & libfashsupport & flash-plugin-nonfree as previously instructed.

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> what about gnash?does it work well,or is it just as niggling?is there something else that can be tried?

Gnash doesn't work worth a darn! It should be removed!

---

### Post by stonecoldjha on 2008-08-21
i installed ubuntu restricted extras,then checked my software sources>third party software,in that, the box against medibuntu was checked,which meant that the repository was added,then i reloaded to update package information,and thus got the following error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

and then i tried installing nswrapperplugin,but it said that there was no such package.what do i do now?

---

### Post by kansasnoob on 2008-08-21
Was this an upgrade from Gutsy to Hardy?

It probably doesn't matter much, I'll find the GPG Key and get right back to you.

---

### Post by kansasnoob on 2008-08-21
Read this all before you do it!

Well this worked for me:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

But my error was:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

So it might be necessary to remove the old Gutsy Medibuntu repo and replace it with the new Hardy Medibuntu repo.

Give me a few minutes to look at some things.

---

### Post by stonecoldjha on 2008-08-21
it wasn't an upgrade,but a plain installation from the live cd of hardy.i used that command,and it executed well without any download error,and then i retried,but the final output is

sonu@sonu-desktop:~$ sudo apt-get install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
sonu@sonu-desktop:~$

---

### Post by kansasnoob on 2008-08-21
OK obviously this:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

is different than this:

> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

in one huge way! Gutsy vs. Hardy!

Are you absolutely sure you're using Hardy? If this was an upgrade then lets "untick" the Gutsy Medibuntu repo in software sources and install the Hardy repo:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

It would probably be better to completely remove the Gutsy repos but I don't know how to do that.

I want to be sure what we have before I give any more advice.

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> it wasn't an upgrade,but a plain installation from the live cd of hardy.i used that command,and it executed well without any download error,and then i retried,but the final output is

sonu@sonu-desktop:~$ sudo apt-get install nspluginwrapper
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
sonu@sonu-desktop:~$

Well somehow you ended up with a Gutsy Medibuntu repo.

Medibuntu is not installed by default from the Live CD. Did you install Medibuntu?

---

### Post by philinux on 2008-08-21
In software sources if you enable hardy backports you will get flash 10 appear in synaptic.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by stonecoldjha on 2008-08-21
i am dead sure that i am using ubuntu 8.04.
medibuntu is added as a repository in my software sources,of course not from that installation cd.

---

### Post by kansasnoob on 2008-08-21
> **philinux said:**
> In software sources if you enable hardy backports you will get flash 10 appear in synaptic.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

That's cool!

I'm only trying to outline what I've done successfully. As always there is more than one way to get a desired outcome in Linux:)

Would you happen to know how to deal with the Gutsy Medibuntu repo in Hardy dilemma?

---

### Post by stonecoldjha on 2008-08-21
how can hardy backports be enabled?also,if i am to install flash 10,i need to uninstall flash 9.itried doing that,i mean uninstalled the flashpluginnonfree,libflashsupport,but i still had videos working on youtube,though with the same frequent crashing.

---

### Post by kansasnoob on 2008-08-21
> **philinux said:**
> In software sources if you enable hardy backports you will get flash 10 appear in synaptic.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

I'm also curious, if I enable "backports" and let ALL updates run what is the likelihood that I'll end up with a broken Ubuntu:confused:

---

### Post by philinux on 2008-08-21
> **kansasnoob said:**
> I'm also curious, if I enable "backports" and let ALL updates run what is the likelihood that I'll end up with a broken Ubuntu:confused:

Non. You might be thinking of proposed see my signature.

Read the link I gave you.

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> how can hardy backports be enabled?also,if i am to install flash 10,i need to uninstall flash 9.itried doing that,i mean uninstalled the flashpluginnonfree,libflashsupport,but i still had videos working on youtube,though with the same frequent crashing.

If you look at the third sreenshot of mine about software sources you'll see you can select "Unsupported Hardy Backports". But I really don't recommend it!

You be your own judge but I know what I'm suggesting works. I've done it on more than a dozen Hardy installs and one Mint Elyssa.

But you must straighten out that Medibuntu problem or it will bite you in the rear!

Just an "aside" but only about two weeks ago I was so disgusted with this Flash problem that I downgraded a couple of puters to Gutsy, and installed Gutsy to a spare partition on my own. That's when I got serious about finding a "work-around". I've since felt brave enough to upgarde several more Gutsy installs to Hardy with no problem.

---

### Post by stonecoldjha on 2008-08-21
i want to manually uninstall completely the flash player that's working presently,and then install(manually)flash 10,how can that be done?or,alternatively,can u give me an appropriate link toget the nspluginwrapper?

---

### Post by kansasnoob on 2008-08-21
Comment #16 here:

[http://ubuntuforums.org/showthread.php?t=876177&page=2](http://ubuntuforums.org/showthread.php?t=876177&page=2)

It works, as far as getting Flash 10 Beta installed!

But it still crashed for me.

I'm telling you that if you don't get that Medibuntu probleem solved you're going to have problems, but I'm done!

---

### Post by stonecoldjha on 2008-08-21
how do i solve that medibuntu problem?and what's wrong with it?

---

### Post by stonecoldjha on 2008-08-21
oh,i just checked the box against medibuntu([http://packages.medibuntu.org/hardy](http://packages.medibuntu.org/hardy) free-nonfree and also against [http://packages.medibuntu.org/hardy/hardy](http://packages.medibuntu.org/hardy/hardy) free-nonfree ( source code),and reloaded package information.this time there were no errors at all.and i tried installing that wrapper by
sudo apt-get nspluginwrapper,but the output was:

sonu@sonu-desktop:~$ sudo apt-get install nspluginwrapper
[sudo] password for sonu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nspluginwrapper
sonu@sonu-desktop:~$

---

### Post by stonecoldjha on 2008-08-21
i think nothing can make flash good on mu ubuntu......please see my last post.

---

### Post by philinux on 2008-08-21
> Backports is an official Ubuntu repository and maintained by knowledgeable Ubuntu developers who are often present on IRC and other communications media. But note that software in backports will not receive review or updates from the Ubuntu security team itself. 

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Not to be confused with proposed repos which is explained in the link above.

Once enable and you run 

sudo apt-get update && sudo apt-get upgrade

or use the update manager.

Flash amongst other apps that fit this category "Programs that can be updated without replacing a large part of the operating system that would affect stability of the whole system" will get  upgraded.

---

### Post by stonecoldjha on 2008-08-21
my problem is that when i open addons(from tools in ff3),i see two shockwave flash plugins:
shockwave flash 9.0 r124
and,shockwave flash 10.0.0 d569


is this creating any trouble?

---

### Post by kansasnoob on 2008-08-21
> **philinux said:**
> [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Not to be confused with proposed repos which is explained in the link above.

Once enable and you run 

sudo apt-get update && sudo apt-get upgrade

or use the update manager.

Flash amongst other apps that fit this category "Programs that can be updated without replacing a large part of the operating system that would affect stability of the whole system" will get  upgraded.

I did not know this! I'm adding it to my knowledge base.

If this solves the flash problem that's great, but wouldn't you agree that having a Gutsy Medibuntu repo in Hardy is a bad thing?

I do know that on the successful Gutsy to Hardy upgrades I've done I just "unticK" the old Gutsy medibuntu repo and then install the Hardy repo.

But thanks!

I might add though that I've been at this for several months and the OP said they needed detailed steps so it's easy to see how a misunderstanding occurred.

---

### Post by stonecoldjha on 2008-08-21
i just downloaded a document titled"nspluginwrapper_0.9.91.5-2ubuntu2.diff.gz".what should i do next?

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> i just downloaded a document titled"nspluginwrapper_0.9.91.5-2ubuntu2.diff.gz".what should i do next?

I don't know!
I'm running Hardy with nothing but The proper Merdibuntu repo added and it's in Synaptic:

[ATTACH]82372[/ATTACH]

---

### Post by stonecoldjha on 2008-08-21
but can u please give me the commands that can install medibuntu?

---

### Post by kansasnoob on 2008-08-21
Plaese post the output of:

```
lsb_release -a

```

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> but can u please give me the commands that can install medibuntu?

Post #24 in this thread.

---

### Post by stonecoldjha on 2008-08-21
here is the output


sonu@sonu-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
sonu@sonu-desktop:~$

---

### Post by kansasnoob on 2008-08-21
> **stonecoldjha said:**
> here is the output


sonu@sonu-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
sonu@sonu-desktop:~$

OK, so lets install the new Medibuntu!

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
```

And the gpg key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Then restart Ubuntu and see if you get any errors!

Whether you do or not run:

```
sudo apt-get update
```

And then:

```
sudo apt-get upgrade
```

---

### Post by kansasnoob on 2008-08-21
Well, I don't know what's going on here but my two oldest fainting goats seem to have a problem and I'm gonna be out with them until the vet shows up!

---

### Post by philinux on 2008-08-22
These are the instructions from medibuntu.

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

However nspluginwrapper comes not from medibuntu but is a hardy package.

---

### Post by stonecoldjha on 2008-08-22
oh,i just downloaded the package nspluginwrapper_0.9.91.5.orig.tar.gz.now how,should i install the nspluginwrapper?

---

### Post by stonecoldjha on 2008-08-22
the package of nspluginwrapper that i downloaded was not from synaptic,though i got the medibuntu repository installed.kindly,tell me how to proceed with the installation.
by the way,just a couple of minutes ago,i installed skype from the synaptic which is also from medibuntu.does that not mean that i have medibuntu repository?

---

### Post by philinux on 2008-08-22
[http://packages.medibuntu.org/hardy/index.html](http://packages.medibuntu.org/hardy/index.html)

Only a small list you'll see.
Google is a good friend. All I searched for was medibuntu packages.

Read the main page too. Interesting.
[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by stonecoldjha on 2008-08-22
yeah,i saw the list,apparently nspluginwrapper is not there.i downloaded the tar.gz of nspluginwrapper.how do i install this?

---

### Post by philinux on 2008-08-22
Enable the multiverse repo it's already in synaptic then.

---

### Post by stonecoldjha on 2008-08-22
the multiverse repository is already enabled,but i don't get any search results for nspluginwrapper in the synaptic.

---

### Post by stonecoldjha on 2008-08-22
hee is the screenshot

---

### Post by stonecoldjha on 2008-08-22
here is another screenshot that proves that medibuntu is enabled.and the other that i don't get any search results for nspluginwrapper

---

### Post by philinux on 2008-08-22
Run this

sudo apt-get update && sudo apt-get upgrade
then search again

---

### Post by stonecoldjha on 2008-08-22
i have somehow downloaded the tar.gz package of nspluginwrapper,but don't know how to install it.what should i do to install it?

---

### Post by stonecoldjha on 2008-08-22
even after having run successfully sudo apt-get update && sudo apt-get upgrade,i don't get nspluginwrapper,but can't i install it with the tar.gz file that i already have on my desktop,if yes,how?

---

### Post by philinux on 2008-08-22
> **stonecoldjha said:**
> even after having run successfully sudo apt-get update && sudo apt-get upgrade,i don't get nspluginwrapper,but can't i install it with the tar.gz file that i already have on my desktop,if yes,how?

Yes - I need more coffee, I think that's a 64bit repo only app.

I'm not even sure if what your attempting will work anyway. But anyway what the heck.

Just double click the tar file it's basically the same as a zip file.
Choose extract and it will extract the file into another folder that you can then browse. There maybe even a readme file.

---

### Post by stonecoldjha on 2008-08-22
the readme file says:

To simplify the build of the 32-bit viewer, a minimal subset of LSB
Desktop 3.1 is included in this distribution. Hence, you only have
to proceed as follows:

$ ./configure
$ make
# make install

its there on my desktop.
how do install,i mean i can't comprehend anything from that.

---

### Post by philinux on 2008-08-22
You dont need the tar if you follow this from the link way back in the thread.

```
To use his work around, follow these steps:

1) Close Firefox
2) Install Conn's nspluginwrapper package
wget http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2... dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb

3) Remove flashplugin-nonfree
sudo apt-get remove --purge flashplugin-nonfree

4) Install flashplugin-nonfree again
sudo apt-get install flashplugin-nonfree

I had one Firefox crash since testing Conn's workaround, immediately after installing his package. Flash still crashs from time to time, immediately after starting a video for example. You'll be presented with a grey box where your video used to be, but you just need to reload the page to fix that problem. Not a single crash of Firefox since hours of testing.

Thanks for the great solution, Conn!


```

---

### Post by stonecoldjha on 2008-08-22
i have already tried thsi,and i tried again,which got me the following output:

sonu@sonu-desktop:~$ wget [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2)... dpkg -i nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb
--22:15:00--  [http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2](http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2)...
           => `nspluginwrapper_0.9.91.5-2ubuntu2...'
Connecting to 144.16.192.247:8080... connected.
Proxy request sent, awaiting response... 404 Not Found
22:15:01 ERROR 404: Not Found.

--22:15:01--  [http://dpkg/](http://dpkg/)
           => `index.html'
Connecting to 144.16.192.247:8080... connected.
Proxy request sent, awaiting response... 503 Service Unavailable
22:15:01 ERROR 503: Service Unavailable.

nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb: No such file or directory
No URLs found in nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb.

FINISHED --22:15:01--
Downloaded: 0 bytes in 0 files

---

### Post by philinux on 2008-08-22
Looks like that server is off. Back to the tar file. Hope is contains a deb file or a readme.

---

### Post by stonecoldjha on 2008-08-22
any other link for that?

---

### Post by stonecoldjha on 2008-08-22
why is there no open source flash player that works just as good as adobe flash.gnash lets you down.and even flashplugin of adobe for linux is buggy,would it ever be fixed?would it not be better to develop a new quality open source flash player that can easily be integrated into ff?

---

### Post by maniheer on 2008-08-22
You can try this..... might as well

```

sudo apt-get purge flashplugin-nonfree libflashsupport

```

then

```

sudo nautilus --no-desktop

```

It should open the file manager (you can delete anything and everything so be careful).

Browse to /usr/lib/flashplugin-nonfree and delete anything that has the word flash in it. Or even better, delete the whole flashplugin-nonfree folder.

then

```

sudo apt-get install flashplugin-nonfree

```

If it doesn't work without crashing then flash hates you, coz it wrks on konqueror flawlessly (that too on kde 4) \\:D/ chakde

---

### Post by maniheer on 2008-08-23
I just remembered, flash 9 had a problem with pulseaudio, and it crashed every time I changed the video on youtube (now I'm using KDEmod and don't have pulseaudio)

Try 

```

sudo rm /usr/lib/flashplugin-nonfree/libflashsupport.so

```

and see if it crashes

Launchpad [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)

---

### Post by gjoellee on 2008-08-23
in Linux Mint this is absolutely no problem at all! Flash runs like in Windows/Mac. However there are a lot of improvements in Flash 10! It is the default flash player in Intrepid!

---

### Post by kansasnoob on 2008-08-23
Sorry to jump the bus but I've been busy with sick goats.

Just to back up a bit, what I suggested in post #10 in this thread has worked for me in both Hardy and Mint Elyssa. Something I didn't say was that the "crash" was different in Elyssa than it was in Hardy.

In Hardy Firefox would close. In Elyssa, which was using Flash 10 beta, only Flash would close and then I'd have to manually restart Firefox to get Flash back. The remedy I outlined in post #10 did work in both without changing anything in the repos!

Now, unless I skimmed through the new replies too fast, the OP still does not have nspluginwrapper in the repos (we can argue later whether it's needed or not), and remember that we had a Gutsy Medibuntu repo in there!

I'm confused! The nspluginwrapper is in the repo by default. everything we'd need (other than Flash 10 beta) is in the repos! Or i guess I should say, "it should be".

Something is NOT right with the repos on this install! If one thing is missing how many other libraries might be missing?

---

