---
title: "[SOLVED] Update broke openoffice! HELP!!"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Stunts on 2008-06-18
Hi all!
I have just made the most recent updates for Ubuntu 8.04 AMD 64. They included an openoffice update.
Everything was going smooth, until I tried to get openoffice up and running. It didn't. I tried to reboot, just to make sure it wasn't temporary. No luck there...
When I try to run 'openoffice' from a terminal I get the following:
```

francisco@MegalaptopII:~$ openoffice
francisco@MegalaptopII:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f26e6fd397c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f26e6fd3a15]
#2 /usr/lib/libX11.so.6 [0x7f26eac9d323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f26eac94d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f26e6b7dc05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f26e220c4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f26e6011bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f26e6025386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f26e60270d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f26e6027483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f26e21fd957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f26e25b576d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f26e25b616a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f26e25b682b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f26e258ef64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f26ee53a4ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f26ee4cf322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f26ee50c1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f26dac3b084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f26dae0fdb4]

```

And it just sits there...
I have to hit ^C to stop it...
I really need this thing back up, I have my MSC thesis defence very soon and I need to finish the oo.org impress presentation.

Help anyone??

---

### Post by Stunts on 2008-06-18
Update:
I've tried to purge openoffice.org with synaptic package manager (complete removal) and manually deleted all the files in ~/.openoffice2.
After a reinstall I still get the very same error...

---

### Post by iaculallad on 2008-06-18
Try to create another account on that system then you logout and log back in using your newly created account. Try to launch your OpenOffice from that account and if successful, logout and re-login using your own account.

---

### Post by Stunts on 2008-06-18
Will try just that.
I'll report my result in a few minutes.
Thanks!

---

### Post by Stunts on 2008-06-18
OK, so Openoffice works in my new account. Phew, at least I can work in there if I have to.
But how do I get it back to work in my regular account?
It's still not running in here.
At leats now I also know it's some trouble in a local config file.
What next?

---

### Post by iaculallad on 2008-06-18
Using your own account, open up your terminal and remove openoffice.org-gtk.

```
sudo apt-get remove openoffice.org-gtk
```

If that does not work, then, you have to uninstall-reinstall your OpenOffice Apps :)

---

### Post by Stunts on 2008-06-18
It Works!!!
Thank you!
What the hell did that package (openoffice.org-gtk) do anyway?

Thank you again!!

Update: I found out what it did. Now openoffice doesn't look integrated into my ubuntu desktop and impress will stay below the gonome panel when in full screen mode. Is there a way to mess with openoffice.org-gtk's configuration in order to make it work? Any ideas on where it keeps its files?
I can just try to get the configuration form the newly created account.

---

### Post by vanadium on 2008-06-18
Try now to reinstall the gtk-integration:

sudo apt-get install openoffice.org-gtk

Chances are things will work again as before. If not, try again, but this time "purge" the files (i.e. remove all config files):

sudo apt-get purge openoffice.org-gtk
sudo apt-get install openoffice.org-gtk

---

### Post by Stunts on 2008-06-18
I've tried both those approaches and the result is the same.
I get Gtk integration in my new account, but in my regular account, oo.org doesn't run when the package is installed.
Even with purge and reinstall I get no sucess.
I have even tried to use a copy of the ~/.openoffice.org2 folder from my new account into the old one and the result is the same.
Edit: and yes, it's chown'ed =-)
Any more ideas?

---

### Post by Stunts on 2008-06-18
Any more ideas anyone?

---

### Post by TeAq on 2008-06-18
hello,
I got the same problem.
If I run "openoffice" in a terminal I also get these error-messages, but if I remove the file ~/.openoffice.org2/.lock then I get an additional error:
```

~$ openoffice 
javaldx failed! 
~$ Locking assertion failure.  Backtrace:

```
and then the output on console is the same as the one from Stunts.

(sorry for my probably not very perfect english)

---

### Post by Stunts on 2008-06-18
In your system, does it work if log in as a different user?
Or is it not working at all?
This should be simple to solve... It's not like it's beyond repair, it works fine on a different user in the same computer...
Since the issue is with the window manager, I've tried to disable compiz, but it didn't make any difference either... Plus, compiz is enabled in my second account and all works fine...

---

### Post by TeAq on 2008-06-18
yes - login as a newly created user works, also if desktop-effects are set to extra.

---

### Post by Stunts on 2008-06-18
I've also tried to reste the appearance settings back to the default "Human" theme, but this also didn't provide a solution...
Any more wild guesses?

---

### Post by Stunts on 2008-06-18
Just another piece of information... If I run oo.org as root (sudo openoffice) it runs fine with openofice.org-gtk installed.
It also clamied that the user settings were locked, but my guess is that it was looking for the settings in /root/.openoffice.org2
Any new ideas now?

Could this possibly be a permissions issue??
I've also tried to remove the ~/.openoffice.org2 directory. This just makes oo.org create a new one when I run it, but still no luck.

---

### Post by Stunts on 2008-06-18
I have filled a bug report on launchpad:
Bug #185311 in libxcb (Ubuntu)
They seem to be working on it but I can't seem to relate the presented solutions to my problem, since most problems there are java related and in i386 versions...

---

### Post by jss167 on 2008-06-18
Not sure if the same or not.  When I open OO, it tells me that it doesn't know which language to use.  Refuses to start.  I want American English.  I could have sworn that I saw the GB(British English) language pack download, then the US one.  Maybe this caused an issue?  I was never asked to select a language.  Can't do anything.

---

### Post by Stunts on 2008-06-18
Try to install the language packs you want to use in oo.org from synaptic and see if that solves the issue.
Just search for openoffice.org and they will show up eventually.
Hope it helps!

---

### Post by iaculallad on 2008-06-18
Hi Stunts;

What if you do a reinstall for your OpenOffice applications so as to have a "fresh" settings. Try to remove all traces of your OpenOffice using Synaptics and follow this manual installation [guide]("http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html").
I hope that will provide a final solution to your problem :)

---

### Post by Stunts on 2008-06-19
Hi again Iaculallad,

I've tried to do that using apt-get purge openoffice-* and then reinstall the packages using the same method.
I'll try to do it using synaptic this time around.
This is however a known bug, according to the latest reports on launchpad.
Maybe this workaround will do the trick...

Thanks anyway!

---

### Post by Stunts on 2008-06-19
Tried your suggestion...
No use. I guess I'll just have to wait for this bug to be fixed... I'll keep tracking it's status on launchpad...

[https://bugs.launchpad.net/xorg-server/+bug/185311](https://bugs.launchpad.net/xorg-server/+bug/185311)

---

### Post by calc on 2008-06-19
For people who are seeing the libxcb-xlib crash does rebooting your system cause the problem to go away? It may be that some stale file in /tmp is causing the problem.

---

### Post by exssnrg on 2008-06-19
Reboot did not work for me.  I did a fresh install of 8.04, and the first boot openoffice worked just fine.  I was soon notified of changes needed so I allowed that process to happen again.  Right after, openoffice apps just bring up an empty window and freeze.  

unloading the gtk integration as described above gets me working again.  I'm not certain what I'm missing functionally yet.

---

### Post by Stunts on 2008-06-20
Ditto exssnrg.
I have tried rebooting too and no avail.
GTK integration makes oo.org look like your desktop, uses gnome-picker for opening and saving files and makes impress go above the gnome-panel when in presentation mode.
Could do more things, but these are the ones I am missing right now. Especially the one from impress, since I've been working on it and have a presentaion scheuled for soon.

---

### Post by jss167 on 2008-06-20
I tried reporting my issue with the broken OO, and it not starting due to the system not knowing which language pack to use.  

OpenOffice was fine, then I did the update the other day. Magically now it doesn't work. It only works as root. I tried removing the other English packages(GB/AU/ZA), only leaving the US version, but no good. Tried removing the lib GTK package(as was suggested), no good.  Also took OO completely out and put back, no good. Now it looks differently, but still only works as root. This is a major problem, as the update corrupted everything for OO. I doubt I am the only one with an issue. 

I am now using KOffice, which does work, but it doesn't have all the features I need.

---

### Post by Stunts on 2008-06-20
Hi jss167!

Just to make sure it's the same issue as we are experiencing:
When you type ```
openoffice
```
In a terminal, what do you get?
When you removed openoffice, how did you do it? Did you use the purge command, or just the remove? (synaptic package manager's equivalents are remove for remove and complete removall for purge).
Did you also try to remove the folder ~/.openoffice.org2  ? (or at least rename it, in order to be able to recover any lost settings)

---

### Post by exssnrg on 2008-06-21
I'm surprised there is not more comment about this. There are probably lots of broken openoffice out there.  Maybe this time of year many people aren't using these applications, so they don't know they are broken.  I ran into it by accident, ...I use this machine mainly for web browsing and email.

---

### Post by Stunts on 2008-06-21
I'm not 100% sure, but this seems to be affecting only x64 hardy.
Anyone with an i386 Hardy experiencing this issue?

---

### Post by emaxx on 2008-06-21
I have the same problems on an Intel core2duo Thinkpad T61P with KDE. openoffice.org-gtk and openoffice.org-gnome aren't installed at all (and never have been installed), so thats for sure not the root cause.

I remember, I had an open file in oocalc and saved it. Later then I **rm**'ed that file from disk using the shell while it was still openend (but not changed) in oocalc, and then i closed oocalc without further saving. Ugly workflow, yes, but was done by accident.

Did anybody else do sth. similar?

BTW: oocalc works on all my files as a different user.

---

### Post by Stunts on 2008-06-21
Did you try to replace the file you rm'ed?
It's what I'd do. =-)
Is oocalc the only affected app?
What do you get when you type ```
openoffice
``` in konsole?

---

### Post by emaxx on 2008-06-21
Yes i tried :-), but didnt help. Maybe due to different content (I just took a copy of another oocalc file).

I cannot "openoffice" in console at the moment, because I am just about to purge/reinstall openoffice-*

---

### Post by philinux on 2008-06-21
Looks like this bug has been around for a while.
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676](https://bugs.launchpad.net/ubuntu/+source/openoffice.org-amd64/+bug/236676)

I'm not having any problems. Very weird. I've got proposed and backports open too.

---

### Post by emaxx on 2008-06-21
Ok, here my results:

purging/reinstalling openoffice-* worked for me. I then renamed .openoffice-org2/ and restored my previously saved one. Again it worked, but came up with the "recovery" screen (presumably due to the previous crashes). I "recovered" the "untitled1" document and now everything is fine.

---

### Post by bwallum on 2008-06-21
I'm stuffed too. It's limited to 64bit Hardy. I did this:

[http://ubuntuforums.org/showthread.php?t=835630](http://ubuntuforums.org/showthread.php?t=835630)

Guess we have to put up with a non integrated but fully functional OOo until its fixed.

---

### Post by emaxx on 2008-06-21
> **bwallum said:**
> It's limited to 64bit Hardy.[/url]


Its not. See above. Intel core2duo, 32 Bit, Hardy.
```

ed@summini:~$ uname -a
Linux summini 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux
ed@summini:~$ 

```

---

### Post by bwallum on 2008-06-21
Very interesting. Is your machine a 64bit dual processor? I have a 32bit machine that is not affected.

---

### Post by emaxx on 2008-06-21
Whats about reading ? :-)

I think i wrote it above.

---

### Post by Stunts on 2008-06-21
emaxx,
I think what he means is that is is a 64bit processor using a 32bit OS.
Maybe the bug is affecting 64bit processors only... regardless of the OS being 32 or 64bit.
Then again, maybe not. =-p
In launchpad, they say that another workaround is to ssh into your local machine:
```
ssh -Y localhost
```

I haven't tried it yet since I must enable remote logins, but can someone else maybe try this?

---

### Post by emaxx on 2008-06-21
Ok,

I'm running 32bit Hardy on a Thinkpad T61P (see above) which has an Intel T7700 @ 2.4GHz core2duo processor.

I must admit, that i really didn't ever care for the 64bit question. It has an "Intel (R) 64+/-" Logo on [that page]("http://www.intel.com/products/processor_number/chart/core2duo.htm"), whatever that means. :-)

Since here everything is allright now, the ssh test won't make much sense, I guess ...

---

### Post by exssnrg on 2008-06-21
I think I'm running 32bit.  Problem affected me with a default build plus the update.

---

### Post by Stunts on 2008-06-21
@emaxx:
All inter core 2 processors are 64bit, so, you know what you got now.

@exssngr:
in order to be sure about your system, just paste the output of:
```
uname -a
```
typed in a terminal.
This will tell you what OS version you are running.

---

### Post by Stunts on 2008-06-21
I've tried the ssh -Y localhost workaround. It works very well, considering you don't mind using a shell.

All you have to do is install ssh in synaptic or apt-get and it's ready to use.
Just type in the console: ```
 ssh -Y localhost 
```
Then just type openoffice after you are logged in and it's done! Pretty openoffice again!

---

### Post by exssnrg on 2008-06-21
$ uname -a
Linux mypc 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

This is running on an old Pentium 4 machine.  Processor and hardware come up as "unknown"

---

### Post by emaxx on 2008-06-21
> **Stunts said:**
> @emaxx:
All inter core 2 processors are 64bit, so, you know what you got now.

Thanks, my system feels much more performant now :mrgreen:

You know, software professionals never worry about processors. They only worry about design :mrgreen: :mrgreen:

Anyway, maybe it has something to do with 64bit hardware, I don't know. For me, it works now and I'm quite sure the oo-guys will fix it soon: there are quite some google hits concerning that problem.

---

### Post by exssnrg on 2008-06-21
I'm going to leave well enough alone for now.  Thanks to iaculallad for the suggestion to remove the gtk integration.  I'm hopeful the oo guys will fix this problem.

---

### Post by bwallum on 2008-06-22
please discard, posted in the wrong place

---

### Post by emaxx on 2008-06-22
Ok, my problem is back again.

After booting this morning, same behaviour: 
```

ed@summini:~$ oocalc
ed@summini:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb6018767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb601881e]
#2 /usr/lib/libX11.so.6 [0xb69c0518]
#3 /usr/lib/libX11.so.6(XCreatePixmap+0x26) [0xb6997dc6]
#4 /usr/lib/openoffice/program/libvclplug_gen680li.so [0xb42eba8a]
#5 /usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN11X11SalFrame4InitEmiP16SystemParentDatab+0x976) [0xb42af176]
#6 /usr/lib/openoffice/program/libvclplug_gen680li.so(_ZN11X11SalFrameC2EP8SalFramemP16SystemParentData+0x2c3) [0xb42b0fd3]
#7 /usr/lib/openoffice/program/libvclplug_kde680li.so [0xb6aa01e8]
#8 /usr/lib/openoffice/program/libvclplug_kde680li.so [0xb6aa025b]
#9 /usr/lib/openoffice/program/libvcl680li.so [0xb7e70194]
#10 /usr/lib/openoffice/program/libvcl680li.so [0xb7dff33c]
#11 /usr/lib/openoffice/program/libvcl680li.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x6f) [0xb7e405cf]
#12 /usr/lib/openoffice/program/libsvx680li.so [0xb14ae677]
#13 /usr/lib/openoffice/program/libsvx680li.so [0xb16b0f0a]
#14 /usr/lib/openoffice/program/libsvx680li.so [0xb16b2828]
#15 /usr/lib/openoffice/program/soffice.bin(_ZN7desktop19impl_callRecoveryUIEhhh+0x5d8) [0x8074ed8]
#16 /usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9SaveTasksEv+0x22) [0x80752a2]
#17 /usr/lib/openoffice/program/soffice.bin(_ZN7desktop7Desktop9ExceptionEt+0x2a5) [0x80769b5]
#18 /usr/lib/openoffice/program/libvcl680li.so [0xb7c887bb]
#19 /usr/lib/openoffice/program/libvos3gcc3.so(_ZN3vos26signalHandlerFunction_implEPvP13oslSignalInfo+0x18) [0xb73ed098]

```
Strongly reminds me of windows :mad:

---

### Post by darkworld on 2008-06-22
Ive just stripped out fiesty and installed hardy. I now have problems, more than one and im not sure if they are connected. I have the open office problem as above.

my machine is:> 2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux


my output from starting openoffice in terminal: > $ openoffice
javaldx: Could not find a Java Runtime Environment! 
darkworld@darkworld-desktop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f50a1eb197c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f50a1eb1a15]
#2 /usr/lib/libX11.so.6 [0x7f50a5b7b323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f50a5b72d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f50a1a5bc05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f509d0ea4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f50a0eefbcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f50a0f03386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f50a0f050d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f50a0f05483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f509d0db957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f509d49376d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f509d49416a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f509d49482b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f509d46cf64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f50a94184ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f50a93ad322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f50a93ea1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f5096398084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f509656cdb4]


Its all a bit above me. Thought I would post outputs in case it adds info to help people solve problem.

---

### Post by Lutin on 2008-06-22
Just my two pennies worth -

No problems with my Acer laptop x86_64, with the latest updates.

However, I am having problems with my old P4 i686.

So, not directly related to 64 bit - at least in my experience.

---

### Post by Stunts on 2008-06-22
I guess the question now is only - what do all these systems have in common?
Someone at launchpad mentioned it could be related to the nvidia drivers.
Anyone with ATI or Intel graphics having this issue?
Or anyone with Nvidia not having it?
Either way, post if you have problems, and which driver you are using - open source, restricted or maybe envy.

I have the issue and I'm using Nvidia with envy drivers.

Just so that I can feed some more info on launchpad

---

### Post by silkstone on 2008-06-22
Not sure how much help I can be as I don't know the inner workings of Ubuntu, but I have...

32-bit Hardy (clean install)
Intel i386 (E4600)
Nvidia restricted drivers (installed automatically - not with Envy)

... and all OpenOffice apps appear to work fine.

---

### Post by darkworld on 2008-06-22
I kicking myself a bit because I did fresh install and then I installed nvidia drivers using envy. Wish I had tried everything before adding drivers. 1st time with envy so not sure about getting back to the start to see if its linked to that install.

Var\crash reveals nothing so its not a crash. Lingot doesnt work on this install, appears and runs but then any attempt to change lingot settings makes that disappear like openoffice, cant see that the problems related though.

---

### Post by emaxx on 2008-06-22
Ok folks, since i cannot allow to tinker around with my office-system, i will try to downgrade oo.

Can anybody tell me how i can do this and how i can block the faulty version to be installed in the future?

---

### Post by Sbarton on 2008-06-22
For what it is worth, I have AMD64 O/S is hardy 64 bit, I do not seem to have any problem so far with Open office. Yet if I type in Terminal- openoffice I get.... javaldx: Could not find a Java Runtime Environment! and then Open Office opens and I can select which item I want to. I do have JRE installed via synaptic. I have Nvidea 6200 card installed.
regards

---

### Post by silkstone on 2008-06-22
Confirmed - I get the same message when I enter openoffice in the Terminal, but otherwise OOo runs OK.

---

### Post by silkstone on 2008-06-22
And if I start OpenOffice and go to Tools > Options > java, there is no JRE showing as installed.

---

### Post by Sbarton on 2008-06-22
Difference here is that mine shows installed, see attachment,
regards

---

### Post by Sbarton on 2008-06-22
Hopefully the attachment is now uploaded and shows JRE as Installed.
Anyway take it as installed.

---

### Post by silkstone on 2008-06-22
From the OOo Tools > Options > Java window I tried adding the JRE that really is installed by navigating to the java folder file at /usr/lib/jvm/java-6-sun/jre/bin/java, but it wouldn't accept it. I also tried the parent folders, but still no deal.

I'm not sure if I will ever need to use Java in OOo so for now I've unchecked the box for using JRE.

---

### Post by Sbarton on 2008-06-22
Attachment test!

---

### Post by silkstone on 2008-06-22
Ah - no - it's not there! That screen should show the JRE version etc in the main part of the box. It's the same as mine - blank. :)

---

### Post by emaxx on 2008-06-22
Gentlemen,

your Java issue hasn't anything to do with the oo-crash, its just an informative message that you do not have a jre installed. That will inhibit macro-execution, but not crash oo.

---

### Post by darkworld on 2008-06-22
Is this a crash? If it was, wouldnt there be a crash log in Var\crash? mines empty.

I have jre installed after the problem occurred, its say installed in options but with the blank box.

If removing OO-gtk allows OO to run then the bug is in that???? But that cant be the issue because some peeps are running ok. Theres a common thread somewhere, hardware? drivers?

---

### Post by silkstone on 2008-06-22
> **emaxx said:**
> Gentlemen,

your Java issue hasn't anything to do with the oo-crash, its just an informative message that you do not have a jre installed. That will inhibit macro-execution, but not crash oo.

But I do have a JRE installed, and I can run .jar applications, but the JRE does not show in OOo.

---

### Post by emaxx on 2008-06-22
> **darkworld said:**
> Is this a crash? If it was, wouldnt there be a crash log in Var\crash? mines empty.

I have a 19-frame backtrace and core-dumps. Is it a crash?

JRE: yes, you might have one, but oo doesn't know about it. Not a problem, just a configuration entry in oo options.

---

### Post by silkstone on 2008-06-22
Solved the missing JRE in OOo...

Go to Synaptic and install openoffice.org-java-common. That will also install a few additional files.

When OOo is restarted, go to Tools > Options > Java and the details of the JRE should now appear in the box.

---

### Post by bwallum on 2008-06-22
> You have 9 broken packages on your system! Use the "Broken" filter to locate them.

This error message received when updating, broken packages appear to me OOo. How do I use the "Broken" fiolter and remove them?

---

### Post by emaxx on 2008-06-22
I did it my way and downgraded. 

Pinning was sth. new for me, but i finally managed to pin the versions i want. It was a boring job, since you have to look up the versions in synaptic an try and retry over and over again until you found all packages affected and the corresponding version-numbers as well (they may differ from package to package). To make things simple for you, I paste /etc/apt/preferences file, but be aware that i use german localization (-de files) which you might have to change for your own localization. my installtion is still running, so i do not yet know wether this solves the problem. I'll post a success or failure message anyway:

/etc/apt/preferences:
```

Package: openoffice.org
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-base
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-base-core
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-filter-binfilter
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-calc
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-writer
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-common
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-core
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-draw
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-help-de
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-help-en-gb
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-help-en-us
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-impress
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-java-common
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-kde
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-l10n-common
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-l10n-de
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-l10n-en-gb
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-l10n-en-za
Pin: version 1:2.4.0-3ubuntu1
Pin-Priority: 1001

Package: openoffice.org-math
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-style-crystal
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-style-human
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-I10n-de
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-I10n-common
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: openoffice.org-officebean
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

Package: python-uno
Pin: version 1:2.4.0-3ubuntu6
Pin-Priority: 1001

```

---

### Post by emaxx on 2008-06-22
Ok,

works so far, even after reboot.

Seems to be solved for me. Hope my preferences-file will help you guys. Good luck.

---

### Post by pcowley on 2008-06-23
I, too, am having issues with OO which started after a very recent update.

The application starts OK, and I can open and edit documents, but it keeps locking up and stops responding.  Eventually a pop up says it has stopped responding and I am able to kill it.  But is is very frustrating as I use OO a lot!

Uname -a says ...  2.6.24-19-generic #1 SMP Wed Jun 4 15:10:52 UTC 2008 x86_64 GNU/Linux

Cheers
Pete

---

### Post by paulderol on 2008-06-23
i've been selling this bug all night, but many of you with a locking assertion failure may be suffering from [ this bug ]("https://bugs.launchpad.net/ubuntu/+source/libxcb/+bug/185311")

---

### Post by gruntlips_ on 2008-06-23
I am running hardy heron on a 64 bit system76 serval.  When I type openoffice in the terminal I get a locking assertion failure (output below).  Is there a fix yet?  Thanks.

- Chris

javaldx: Could not find a Java Runtime Environment! 
coldwater@coldwater-laptop:~$ Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0x7f8d6d40597c]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x15) [0x7f8d6d405a15]
#2 /usr/lib/libX11.so.6 [0x7f8d710cf323]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x44) [0x7f8d710c6d54]
#4 /usr/lib/libgdk-x11-2.0.so.0(gdk_window_new+0x395) [0x7f8d6cfafc05]
#5 /usr/lib/libgtk-x11-2.0.so.0 [0x7f8d6863e4c8]
#6 /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x10f) [0x7f8d6c443bcf]
#7 /usr/lib/libgobject-2.0.so.0 [0x7f8d6c457386]
#8 /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x875) [0x7f8d6c4590d5]
#9 /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x83) [0x7f8d6c459483]
#10 /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0x77) [0x7f8d6862f957]
#11 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8d689e776d]
#12 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8d689e816a]
#13 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8d689e882b]
#14 /usr/lib/openoffice/program/libvclplug_gtk680lx.so [0x7f8d689c0f64]
#15 /usr/lib/openoffice/program/libvcl680lx.so [0x7f8d7496c4ed]
#16 /usr/lib/openoffice/program/libvcl680lx.so [0x7f8d74901322]
#17 /usr/lib/openoffice/program/libvcl680lx.so(_ZN9TabDialogC2EP6WindowRK5ResId+0x5f) [0x7f8d7493e1cf]
#18 /usr/lib/openoffice/program/libsvx680lx.so [0x7f8d61682084]
#19 /usr/lib/openoffice/program/libsvx680lx.so [0x7f8d61856db4]

---

### Post by paulderol on 2008-06-23
> **emaxx said:**
> Ok folks, since i cannot allow to tinker around with my office-system, i will try to downgrade oo.

Can anybody tell me how i can do this and how i can block the faulty version to be installed in the future?

if you go into synaptic, in the menu there is a "history" button.

i belive you can remove and re-adjust packages from there. 

if not, there is probably an archive within the OOO site which has .debs of previous versions, which you may install instead, after uninstalling [but not completely removing the ooo packages. 

also, check the bug i linked earlier, there is i believe a workaround and a discussion on repairs. 

i can offer more help if needed. it's late.

---

### Post by Stunts on 2008-06-23
There are in fact several workarounds for this:
1 - Create a new user account and use oo.org from there. It will work fine;
2 - 'sudo apt-get remove opeonoffice.org-gtk'. It will look uglier, but work just fine;
3 - Use 'ssh -Y localhost' from the console. This reuires you to install ssh-server. Then just type openoffice from the console and it runs fine as well.
4 - Run in a terminal ```
cd /usr/lib/openoffice/program/
./soffice.bin

```
Kudos to Marcus Scholl from launchpad for this workaround.

In order to turn this into a shortcut, just copy and paste this text into gedit and save it anywhere you like.
Then make it executable with chmod (or nautilus  -> right click it  -> Permissions -> allow to be executed)
after this all you have to do is drag and drop it on the gnome panel. Name it, choose an icon, and there you go. Openoffice.org is back!
Hope this helps!


This is a very strange bug, which seems to be affecting mostly 64 bit systems.
Some people (on launchpad) are working on a solution, but they are still stumbling on a few issues before the patch can be supplied upstream...

---

### Post by Lutin on 2008-06-23
To add some more information to the discussion regarding nVidia drivers, here's what I have on my two systems -

1) Acer laptop AMD64 running 64 bit Ubuntu Hardy and the 169.12 nVidia driver - **NO** problems with OpenOffice. This system is regularly updated and the OO version is shown as 2.4.1 (ie latest I think).

2) 3 GHz P4 running 32 bit Ubuntu Hardy and again the nVidia 169.12 driver - had loads of problems with OpenOffice (would run if kicked off from the command line though). Eventually, because of other problems, re-installed and updated everything except OpenOffice. OO version is 2.4.0 and everything is fine.

Hope this helps.

---

### Post by WijbrandSchaap on 2008-06-23
Hi, 
same here in Hardy on AMD 64 with nvidia
Thanks for the workaround (removed openoffice-gtk)!
Hope they come up with a solution.
Wijbrand

---

### Post by darkworld on 2008-06-23
Its a bit worrying that people new to Ubuntu could run smack bang into this one.

It only seems to be a problem in the desktop of the user who updated it, other users on same box unaffected.

Lauchpad reports seem to be implying its caused by a combination of things, can anybody explain to me in laymens terms what the actual cause is?

Seems to be quiet a few work rounds but no hard solution but hey total respect for the guys who are trying to sort.

---

### Post by Stunts on 2008-06-23
I've been folowing launchpad closely.
I'm no expert either, but it seems that the real experts can't reproduce the bug on their machines.
The cause for the bug is not yet fully known, but several appraoches are being attempted...

Hope they get somewhere soon, cause the tone is not going any merrier in there...
Some people are being over critic in my opinion...

---

### Post by kobutak on 2008-06-24
New Install 64 bit 8.04 Ubuntu.  All synaptic updates applied (one day ago) and OO was working.  Installed nvidia drivers from nvidia website and OO stopped working receiving the Locking assertion error.  If I sudo openoffice, it works.

Anyone noticed the same only after installing the nvidia drivers?

Intel Q6600 quad processor, 4gb ram, ASUS P5N-T Deluxe Motherboard, EVGA e-GeForce 9600 GT Superclocked 512Mb.

---

### Post by Stunts on 2008-06-24
This bug is also affecting some people using ATI drivers.
It's not just nVidia. It is also only affectiong 64bit capable processors.
I just haven't heard of anyone using Intel graphics with this bug...

In my case I used envy to install my nVidia drivers, but it was done long before the update.

---

### Post by dvhart on 2008-06-25
Just wanted to report that this bug also exists on non 64 bit systems that use neither nvidia nor ati proprietary drivers.  

model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz

Linux aeon 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

01:00.0 VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5200]

Using the radeonhd driver

Confirmed that removing openoffice.org-gnome "fixed" the problem for my user and that a different user was able to run oo without any changes.  I have removed all my .openoffice* directories several times.  I do not see any messages to the console when starting oocalc or oowriter, they just return and the opened window doesn't get refreshed and must be forcibly killed.

According to synaptic history, I last updated openoffice on June 19th with 1:2.4.1-1ubuntu1.  I installed a new kernel on June 23rd (2.6.24-19.34).  And today I upgraded python-central to 0.6.7ubuntu0.1.  Unfortunately I can't say when oo broke :-(  Hope that helps.

---

### Post by TeAq on 2008-06-25
I am no expert, too, but I now tried all the workarounds (which work for me, too) and the interesting one is the one, typing
```
/usr/lib/openoffice/program/soffice.bin
```

All the other openoffice commands are links or shellscripts opening /usr/lib/openoffice/program/soffice which is a shellscript.
Could it be, that this script (which I do not really understand, but which has a lot of if/else-s and does not start soffice.bin in any case) is responsible for the problem?
Maybe all the other workarounds cause some variables to have values which do not cause the crash?

---

### Post by TeAq on 2008-06-25
ok - the script opens
/usr/lib/openoffice/program/oosplash.bin
before soffice.bin - and if I open oosplash.bin manually all the error-messages occur.

---

### Post by Stunts on 2008-06-25
This is way beyond my skills!
But what you are saying makes sense.
Since all useres on the same computer share that script, but some get the error and some don't, I'm inclined to say it's something to do with permissions...
But well... I really can't be sure..

---

### Post by itisthus on 2008-06-26
I am having a similar(?) problem; when I click on a menu item in open office it causes it to drop out to a file recovery screen, on restarting the program it recovers the file and then drops out again as soon as I click on a menu item.

Interestingly this problem only seems to occur if I access my document by clicking on its icon, starting through the open office icon in the applications menu starts a fully functional open office.

The problem was 'solved' for me by removing openoffice.org-gtk and openoffice.org-gnome, leaving things a little ugly.

System = 64bit processor and 64bit Hardy dist, nvidia graphics drivers.

An additional 'error' in open office's running is that it fails to load the icon pictures in open file browser window - I don't know if this is related to the gtk integration problem. - Update - like the crash problem this does not occur if I open through applications menu and is fixed by openoffice.org-gtk removal.


Regards.

---

### Post by DarinB on 2008-06-26
I am running Hardy Heron Clean install on a Pentium 4 756 Ram 32bit version.
trying to open OO from launchers causes the program to freeze. only fix reboot. 
none of the posts have helped. 
i can get to a new doc by opening an old one then choosing new, after the reboot........
This just started last week. i have no idea why i don't add or remove packages i simply browse the web read email listen to podcasts. 
i need help and am kind of pissed off. i still love Ubuntu i think!!!

---

### Post by Stunts on 2008-06-26
I think you may be having a different bug...
What do you get when you run oo.org from a console?
(Just type:
```
openoffice
```

in a terminal)

If you get a crash you can Ctrl + c in the terminal to kill openoffice and no need to reboot.

---

### Post by DarinB on 2008-06-26
openoffice in terminal nothing happens 
i will reboot and try again

---

### Post by DarinB on 2008-06-26
soffice in terminal works 
now how do i get it to work with the launchers

---

### Post by DarinB on 2008-06-26
i don't know if this matters but openoffice in terminal also works no crash

---

### Post by Stunts on 2008-06-26
It is probably an issue with your launchers.

What happens when you try in a terminal:
```
 openoffice -writer 
```
The same goes for 'soffice' instead of openoffice.

After this let's see what we can do for your launchers.

---

### Post by silkstone on 2008-06-26
Not sure if this helps - not having a problem with OOo myself - but there's another thread here...

[http://ubuntuforums.org/showthread.php?t=835630](http://ubuntuforums.org/showthread.php?t=835630)

... where someone has solved it by removing 2.4 and installing 3 beta.

---

### Post by DarinB on 2008-06-26
openoffice -writer in terminal crashes
soffice and openoffice works

---

### Post by Stunts on 2008-06-26
Does it crash with an error message, or it just plain stops?
If it is with an error message, can you please post it here?

---

### Post by DarinB on 2008-06-26
the window border opens and nothing else and it freezes then i have to force quit after that i can not open even a document i have to reboot to be able to open a document.

---

### Post by Stunts on 2008-06-26
@ DarinB
I think you ahave a different error on openoffice...
Try to use synaptic to do a "Complete removall". Then restart and use synaptic again to install it. Chances are it will solve your problem.

@ Everyone!
Good news everyone!
With a bit of luck we will have an update by tomorow that will fix our bug!
Keep your fingers crossed!

---

### Post by DarinB on 2008-06-26
no didn't work i even manually removed the .office.org2 folder> 
no change 
someone recommended OO3 beta i installed it and at least i was able to create a lancher.

---

### Post by Stunts on 2008-06-27
At least you have it functioning now, DarinB.
Hope it works out for you.

---

### Post by Spydr4590 on 2008-06-27
I did a fresh install of ubuntu 8.04 with all updates and this was broken for me. Thanks for recommending removing gtk. That seemed to help till this is fixed.:popcorn:

---

### Post by darkworld on 2008-06-28
It seems a fix is on its way! 

Chris Cheney ( launchpad ) wrote:

> This will be fixed in openoffice.org 1:2.4.1-1ubuntu2 uploaded to the
archive later today. It will take a while to build so please be patient.

:)

---

### Post by Stunts on 2008-06-28
The fix will be on Hardy Proposed repository, so if you want to get is ASAP, you must activate that repository.
It also means it will be under "testing" just to make sure it's the right fix for everyone.

---

### Post by DarinB on 2008-06-30
i am running Hardy is there anything i need to do to get this miracle cure?????

---

### Post by bwallum on 2008-06-30
Just wait a bit, it seems. The fix is committed apparently.

---

### Post by DarinB on 2008-06-30
i am sorry for being such a noob what is "the fix is being committed"

Do i have to go to Bellvue to get it? or will i end up there if it doesn't work lol

---

### Post by Stunts on 2008-06-30
Ok everyone!
We have a fix.
It is now in Hardy proposed.
In order to activate it do the folowing:
System -> Administration -> Software sources;
Select the 'Updates' Tab;
Select 'Pre reselase updates' (make sure it's ticked)
Click 'Close' and 'Reload' after it.
Download the new updates.
Off you go!

Yay! Openoffice.org is back!

A Big Thanks you to Chris Chaney at launchpad for commiting this fix.
That's it everyone, I think I can mark this thing solved.

BTW, I have defenden my MSc thesis today, and it went great. Thanks for all the work arrounds that enabled me to use oo.org with GTK integration, which combined with Compiz, dazzeled the whole audience.

---

### Post by DarinB on 2008-06-30
did not help at all!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by vanadium on 2008-06-30
You might need to wait a day or so until the update gets into your local repository mirror.

---

### Post by Spydr4590 on 2008-06-30
Worked for me. Thank you!

---

### Post by DarinB on 2008-06-30
hey it works gotta love open source
i tried going back and there were an additional 19 packages and now it works great.
i did an install on a friends computer should i have him do the update?????
or leave it until i hear a complaint????

---

### Post by Stunts on 2008-07-01
If he says something's not working make the update. Chances are by the time he discovers it the fix will have been placed in the 'regular' updates.
But this is just my opinion!
=-)
Severeal people have said how it's working now. I think it's time to mark this thread 'Solved'!
Thanks everyone for your participation.

---

### Post by bwallum on 2008-07-02
I'm sorted too with the numerous OpenOffice proposed updates. New version for Gnome integration:- openoffice.org-gtk 1:2.4.1-1ubuntu2

Thanks to all for the fix!

---

### Post by cupcake4170 on 2008-11-27
That happened to me too, and that's how I fixed it.

---

