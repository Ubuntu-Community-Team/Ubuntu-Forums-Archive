---
title: "Do I have to have Wine to run Firefox? Problems with Flash crashing since upgrade to"
date: 2015-03-12
forum: New to Ubuntu
---

### Post by benawhile on 2015-03-12
Do I have to have Wine to run Firefox? I have been having increasing problems with Flash crashing since I upgraded to 14.04 from 12.04. I don't think I had Wine when I used 12.04.
 I keep getting this message when I try to watch youtube on full screen:
 

 &#8220;The program pluginloader.exe has encountered a serious problem and needs to close&#8221; &#8220;This can be caused by a problem in the program or a deficiency in Wine&#8221;
 

 I tried to uninstall Wine but I still have the problem as though Firefox still wants to run in Wine.

AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ × 2 
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
32 bit OS
MSI K9VGM mobo with Graphics chip: K8M890CE
Gnome metacity desktop. (since upgrade other desktops don't work well for some reason)

---

### Post by dino99 on 2015-03-12
no need of wine to get firefox on ubuntu

as usual do some system cleanings: sudo apt-get clean ... autoclean .. autoremove
you can also use gtkorphan (gnome DE) to remove some more ones.
if you are using synaptic, then search for the installed 'flash' packages, then purge them, and finally install 'pepperflashplugin-nonfree'

you should then, after a log out/in, get a more stable installation.

note: why not upgrading to utopic or even better vivid which is very stable

---

### Post by dbknox on 2015-03-12
I gave up using Firefox for just that reason, I installed Google chrome and it seems to work well.

---

### Post by benawhile on 2015-03-12
Before i try that can you tell me this: Did Wine come as default with 14.04? If not, what was the bundled way to use Flash in Firefox? And how did I run Flash in Firefox on 12.04? I would like to go back to that first as I don't know what pepperflash is. 
I did do this as a system clean "sudo apt-get clean ... autoclean .. autoremove" before I tried to uninstall wine. Now I don't even know if it's installed or not.
Thank you for tip about utopic and vivid, but right now I am hoping for a quick solution.

BTW my system is this:
AMD Athlon(tm) 64 X2 Dual Core Processor 4000+ × 2 
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
32 bit OS
MSI K9VGM mobo with Graphics chip: K8M890CE
Gnome metacity desktop. (since upgrade other desktops don't work well for some reason)

---

### Post by ajgreeny on 2015-03-12
Sorry 9d9, but the firefox default flash package is **flashplugin-installer** and the **pepperflash-plugin** will not work in normal circumstances in firefox but is the default for chromium and google-chrome.

However it is possible to add the ppa from [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) to get a wrapper that allows you to install **freshplayerplugin** package that puts a wrapper round pepperflash and allows it to work pretty well in firefox; I'm using it at the moment with no real problems at all in my Xubuntu 14.04.

I do wonder, however, if your hardware is a bit weak for flash and if the athlon cpu is sse2 enabled; what does command ```
cat /proc/cpuinfo | grep sse2
``` show you in its output?

I also am not sure about the llvmpipe driver shown in your information.

---

### Post by Impavidus on 2015-03-12
Indeed, no reason to run wine. I never have.

Firefox can use the flash player when you install the package **flashplugin-installer**. It will get you flash version 11.2, which is old, but works on most sites and still receives security updates. You can also install google chrome (from their site), which comes with a flash player build in and will add itself to your software sources to update automatically, or you can install chromium and install **pepperflashplugin-nonfree**, which gets the flash player build into chrome and makes it available to chromium. It's a bit more involved to get this update automatically, but it's possible. Finally there are some hacks to get the latest flash working in Firefox, but I never looked into those. Some of these hacks may involve using wine. Edit: And ajgreeny just referred to another hack.

Besides, you don't need flash to watch youtube.

---

### Post by benawhile on 2015-03-12
cat /proc/cpuinfo | grep sse2
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv vmmcall


sse2 was highlighted in red in the terminal.

Well, I'm not sure about my hardware either but it was fine for 12.04, even with unity. Flash crashes and script errors are happening more and more often. I have a spare slot for a better graphics card but I wouldn't know what to get. Present mobo was bought 8 yr ago but don't have time for an upgrade project yet.
THere is a bit of history which I can assemble and post later, I am very confused about compholio, pipelight, silverlight etc. and whether I have  or need them.

---

### Post by benawhile on 2015-03-12
Is this any help as background?

June 2014

 After install 14.04 had to do hal this way to get Channel 4 OD:


     sudo add-apt-repository ppa:mjblenner/ppa-hal
     sudo apt-get update && sudo apt-get install hal


 Resolution poor (jerky picture)so tried this


 sudo add-apt-repository ppa:pipelight/stable
 sudo apt-get update
 sudo apt-get install --install-recommends pipelight-multi
 sudo pipelight-plugin –update


 Made no difference to resoltion.!
 Only watchable in small screen
 

 July 9 2014 posted this and got interesting answer but haven't followed up  [http://ubuntuforums.org/showthread.php?t=2233592](http://ubuntuforums.org/showthread.php?t=2233592)

---

### Post by buzzingrobot on 2015-03-12
> **benawhile said:**
> 
 

 &#8220;The program pluginloader.exe has encountered a serious problem and needs to close&#8221; &#8220;This can be caused by a problem in the program or a deficiency in Wine&#8221;
 

 

Wine is not included in any official Ubuntu install.  I'd guess the above message is a result of not completely uninstalling Wine that was installed on 12.04.


Firefox packaged for Ubuntu does not use pepper-flash, which is intended for Chrome/Chromium and the result of an agreement between Google and Adobe.  Install the "flashplugin-installer" package.  Close and reopen Firefox and you should see Flash listed as a plugin in Addons.

The addition of HAL from a PPA and Pipelight perhaps complicate identifying the cause of this problem.

---

### Post by ajgreeny on 2015-03-12
I have hal installled from that same ppa, and for the same reason, ie, to get the UK TV catch-up service 4oD to work, and all my flash plugins work with no problem.  I do not have pipelight installed and have no need for it, so as buzzingrobot says that may be your problem.

So my current situation which is all working well is:-
In firefox I now have the freshplayerplugin working fine, ie the wrapper for pepperflash-plugin version 15.0.0.239 according to the adobe site.
In chromium I have pepperflash-plugin also version 15.0.0.239.

---

### Post by Mike_Walsh on 2015-03-12
> **ajgreeny said:**
> 

I do wonder, however, if your hardware is a bit weak for flash and if the athlon cpu is sse2 enabled; what does command ```
cat /proc/cpuinfo | grep sse2
``` show you in its output?

The Athlon 64 X2 dual-core not only has SSE2's, it has SSE3's. I run a single-core Athlon 64, which has SSE3's; the dual-core was exactly that.....two Athlon 64 cores on a single die, with both cores sharing the L2 cache.

[http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%204000%2B%20-%20ADO4000IAA5DD%20(ADO4000DDBOX).html](http://www.cpu-world.com/CPUs/K8/AMD-Athlon%2064%20X2%204000%2B%20-%20ADO4000IAA5DD%20(ADO4000DDBOX).html)

I've never had the slightest problem watching flash in FF. Notwithstanding the fact that I use Chromium 95% of the time, my FF flash player is, if anything, even smoother than the highly acceptable playback I **already** have in Chromium with pepperflash...


Regards,

Mike. :)

---

### Post by Bill Tetzeli on 2015-03-12
Did you do an online upgrade to 14.04 or a fresh installation?  If it was online, this may be one of those instances of glitches that can occur, especially going from one LTS version to the next. In any event, if you're going to hold on to 14.04 for the next few years, it'd be a good idea to back up any data you want to save and doing a fresh install of 14.04.  My guess is the firefox program will go away and you'll be sparing yourself other problems as time goes on.

---

### Post by Roger Cook on 2015-03-13
open fire fox, on the address line type in** about:config** hit enter when it comes up tell it **I will be careful** OK.
right click in the body of the the info given and click **new** **  Boolean** then type in this **Extensions.blocklist.enabled** and hit enter
Reboot

---

### Post by benawhile on 2015-03-13
To Roger Cook: Please explain why I should do this.

---

### Post by benawhile on 2015-03-13
I have  Removed Pipelight as here:

 sudo add-apt-repository -r ppa:mqchael/pipelight

sudo add-apt-repository -r ppa:ehoover/compholio
with no effect, problem remains.

 To AJGreeny and buzzingrobot: Could you say a bit more about the Gallium 0.4 llvmpipe driver? I have found a post about replacing it with Intel haswell here:
 [http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed](http://askubuntu.com/questions/436374/how-to-get-rid-of-the-gallium-0-4-on-llvmpipe-llvm-0x300-driver-intel-needed)

 but don't know if I can do same with my old system.

 It seems I have sse2, am I right?

 Buzzingrobot, thanks, I must have installed Wine separately.

 I interprete buzzingrobot's post to mean I should get rid of Wine properly and install flashplayerplugin.exe and that freshplayer is not needed unless I use Chrome, which I don't at present. Am I right?
 I noticed on my plugin list I have Shockwave Flash twice, 11.2.202.451 and 16.0.0.235. Both always activated. Should I get rid of one of them or “never activate”? I set the 11.2.202 to never activate but youtube crashed firefox and on restart it was still crashing when going to full screen.

 I request advice on getting rid of Wine properly.
To Bill: It was a fresh install, the old 12.04 was wiped, so it couldn't have been residual Wine.
Thanks to Mike, Buzzingrobot and AJGreeny

---

### Post by buzzingrobot on 2015-03-13
> **benawhile said:**
> I have  Removed Pipelight as here:

 sudo add-apt-repository -r ppa:mqchael/pipelight

sudo add-apt-repository -r ppa:ehoover/compholio
with no effect, problem remains.

That only removes the entry for the PPA's server URL (its repository), it does not remove the packages installed from that repository.

The ppa-purge tool is often used to remove both a PPA's repository entry and the packages installed from it.  You'll need to install it from the standard repos.  It's a command line app that's run by supplying it with the name of the PPA.

Unfortunately, it depends on the presence of the repository entry, so you would need to use add-apt-repository to add it back.

 
> 

 I interprete buzzingrobot's post to mean I should get rid of Wine properly and install flashplayerplugin.exe and that freshplayer is not needed unless I use Chrome, which I don't at present. Am I right?
 I noticed on my plugin list I have Shockwave Flash twice, 11.2.202.451 and 16.0.0.235. Both always activated. Should I get rid of one of them or “never activate”? I set the 11.2.202 to never activate but youtube crashed firefox and on restart it was still crashing when 

Linux can't run any ".exe" file unless something like Wine is installed to emulate Windows.

The version 16.0.0.235 flash is the pepper-flash package intended for use with Chrome/Chromium.  As far as I know, Firefox can't use it (short of some kind of hack.)  The 11.2.202.451 version is the version Firefox expects to use.  I'd disable the pepper-flash version in Firefox.  If you aren't going to use Chrome/Chromium, consider deleting it.

---

### Post by benawhile on 2015-03-13
Thank you, this has certainly helped. Now I appreciate the difference between v11 and v16, but I am not sure exactly what is happening now.  
 

 Both versions, 11 and 16, on “never activate”
 Restart: both remain greyed out. Youtube OK on full screen. Jerky, but has been like this since 14.04 upgrade anyway. Actually less jerky than before, probably about 8 frames per second, the best I could get previously was more like 4 f.p.s.
 

 Change version 11 to “Ask to activate”.  
 Restart FF. Version 16 found to have followed v 11 and is also on “Ask”
 Youtube viewer now blank and has “Activate Flash” click box.I clicked, had to reload the page and the video started. No way of telling which version started. When I clicked on full screen I got the old serious error message, including the “defiency in Wine” message. See screenshot. So I guess it is v16 that is trying to run, and looking for Wine.
 

 V11 to “Always”, v16 to “Never”
 First restart causes BOTH to disable.
 Reset 11 to “Always”
 Now restart causes both to Activate. This carries on with alternate restarts.
 

 Set v16 to “never” and v11 to “Always” without restarting FF, Youtube is again working OK.
 

 In time maybe I will be able to figure out whether v11 on makes any difference to anything else.
 So all I know now is:
 better with v11 and v16 both off.
 If I turn v11 on or “Ask to activate” I am OK until I restart FF, but then v16 will default on as well and I will get crashes.
 

 Could any of this be due to Wine and Pipelight not uninstalled properly/
 

 I don't understand how I can watch youtube without Flash.
 

 I don't fully understand the pipelight removal instructions and will need to be talked through but I can leave that for now. Same for Wine.
 

 I did at least already understand that .exe is a Windows program and will only run with Wine.
  [ATTACH=CONFIG]260594[/ATTACH]

---

### Post by buzzingrobot on 2015-03-13
Youtube recently moved to default to using HTML5 instead of Flash.  When I disable Flash in Firefox here, videos on Youtube work.

Video performance is going to depend on a mix of things, including the capabilities of the video card and the capabilities of the driver that's in use.  I'd suggest starting a new thread to address that issue.  Be sure to include your system specs.

---

### Post by benawhile on 2015-03-13
Actually it's not as good as I thought. Sometimes the pause and skip buttons don't appear. I can't play a youtube playlist in full screen, only the current movie, and then it stops. And there has been one Firefox crash.  
 Btw I have Firefox 36.0.1 Mozilla Firefox for Ubuntu Canonical 1.0 and I use Adblock.
 Are there two different Ubuntu versions of Firefox, one to run in Ubuntu and one to run in Wine?
 

 I removed the Flash Plugin Installer via the Software Centre but it only removed v11. V16 is still there. Even google search for &#8220;uninstall shockwave flash 16.0.0.235&#8221; shows nothing to actually uninstall it. I would like to uninstall it. It's disabled anyway.
 

 So I seem to be getting less crashes. And I can watch full screen, but not on a playlist or repeat.

---

### Post by buzzingrobot on 2015-03-13
The pepperflash packages in the repos is titled "pepperflashplugin-nonfree". If you know you installed it from the repos, try "sudo apt-get remove pepperflashplugin-nonfree" in a terminal. (It's also installed when you install Chrome, which is not in the repos and needs to be installed directly from Google or, I believe, a PPA where someone has made it available. I don't know if removing Chrome also removes pepperflash.)

Pepperflash and the Flash Adobe releases for Linux (which is packaged by Ubuntu and other Linux distributions) are both versions of Flash, but they are two distinct products. The version released by Adobe has, for some time, only been updated with new security fixes, but no new features or capabilities. The version released with Chrome as pepperflash includes both. Adobe has plans to discontinue *any* support for its version of Flash for Linux.

Further complicating matters:  Chromium is the fully open-source browser on which Google Chrome is based. Chromium does not ship with either version of Flash.  The pepperflash that ships with Chrome works in Chromium and is repackaged for the convenience of Chromium users who want to use Flash.

Only one version of Firefox is in the Canonical repos.  Any version that requires Wine would be a Windows version.

---

### Post by benawhile on 2015-03-13
I ran "sudo apt-get remove pepperflashplugin-nonfree"

Got "Package 'pepperflashplugin-nonfree' is not installed"

It still shows in the Firefox plugin list as Shockwave Flash 16.0.0.235

---

### Post by buzzingrobot on 2015-03-13
How did you install pepperflash?

[OK, this -- [https://helpx.adobe.com/security/products/flash-player/apsb14-27.html](https://helpx.adobe.com/security/products/flash-player/apsb14-27.html) says 16.0.0.235 is the current version of Flash for *Windows* and also the version released with Chrome.  Don't know which one you've got got there, and I don't know if/why Firefox for Linux is recognizing the Windows version, if it's insstalled, but if you want to delete it I suspect you'll need to hunt down the pieces and manually delete them.  Unless it was installed by the Ubuntu package manager, you won't by able to use Software Center/Synaptic/apt to remove it.]

"apt-cache seach <keyword> searches for packages that match "keyword".  Try "apt-cache search flash".  If it returns a package that is clearly the version 16 package, you can delete that.

---

### Post by benawhile on 2015-03-13
Regret I have no recall of how I installed pepperflash. All my relevant activity history I can find is in a previous post in this thread, 

*June 2014.* [I]After install 14.04 had to do hal this way to get Channel 4 OD:

     sudo add-apt-repository ppa:mjblenner/ppa-hal
     sudo apt-get update && sudo apt-get install hal

 Resolution poor (jerky picture)so tried this

 sudo add-apt-repository ppa:pipelight/stable
 sudo apt-get update
 sudo apt-get install --install-recommends pipelight-multi
 sudo pipelight-plugin &#8211;update[/I]

and I have these screenshots, the one of my file system I just did and shows that something to do with pipelight happened on 13th Jan at 12.44, the next shows that I took a picture of a compholio problem a few minutes later the same day.
[ATTACH=CONFIG]260600[/ATTACH][ATTACH=CONFIG]260601[/ATTACH]


apt-cache search flash returned about 4 pages of results including those below but doesn't say where they are. I uninstalled plugin installer a couple hours ago in the software centre, but THAT is still showing as well!

pepperflashplugin-nonfree - Pepper Flash Player - browser plugin
flashplugin-installer - Adobe Flash Player plugin installer
flashplugin-downloader - Adobe Flash Player plug-in installer (transitional package)
flashplugin-nonfree-extrasound - Adobe Flash Player platform support library for Esound and OSS
gnash - GNU Shockwave Flash (SWF) player
gnash-common - GNU Shockwave Flash (SWF) player - Common files/libraries
gnash-cygnal - GNU Shockwave Flash (SWF) player - Media server

---

### Post by buzzingrobot on 2015-03-13
Sorry, I was wrong about apt-cache search.

Try this:```
dpkg -- get-selections | grep flash 
```

The first part lists all installed packages and the second part filters for "flash" (or any other word supplied there).

The package you want to have installed to supply Flash from the Canonical repos for Firefox from the Canonical repos is "flashplugin-installer".

---

### Post by benawhile on 2015-03-13
Only got this:
dpkg: error: need an action option

Type dpkg --help for help about installing and uninstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

OK so I need to get flashplugin-installer back to get Flash 11, but have to sort this out first as Flash 16 is messing everything up.

---

### Post by benawhile on 2015-03-13
Think I figured out the error, deleted a space before "get"
Now got this

dpkg --get-selections | grep flash
flashplugin-installer                deinstall
gnome-session-flashback                install

---

### Post by buzzingrobot on 2015-03-13
Give "sudo apt-get install flashplugin-installer" a try. Firefox needs to restart to be aware of it.

---

### Post by benawhile on 2015-03-13
Are we on a different track now? I thought you were helping me to first uninstall Shockwave Flash 16, pepperflash, so that I can reinstall Flash 11, because pepperflash was interfering with Flash 11. I thought I should solve this before I get the plugin installer? I want the plugin installer later to reinstall flash 11, right?

---

### Post by benawhile on 2015-03-13
OK now I get

dpkg --get-selections | grep flash
flashplugin-installer                install
gnome-session-flashback                install

Not sure where we're going here, we are still trying to uninstall pepperflash, so that I can reinstall Flash 11 and get it to work without pepperflash interfering, yes?
Very appreciative of your time, notwithstanding!

---

### Post by buzzingrobot on 2015-03-13
Looks like it's installed.  Check Addons->Plugins, assuming you've restarted Firefox.

"dpkg --get-selections | grep flash" isn't showing that the pepperflash plugin from the Canonical repos is installed.  If Firefox shows it is, I can only guess it was installed some other way than with a Ubuntu package.

Not sure what, if anything, Firefox will do with the bits and piece of Pipelight, etc., on the system.

Also: Firefox creates a batch of configuration files in your home directory, inside the hidden directory ".mozilla". I.e., /home/<YourUserName>/.mozilla/firefox.  (Tell the file manager to display hidden files.)  Deleting that Firefox directory is brute force, but when you then relaunch Firefox it will be as if it is launched for the first time. That Firefox folder will be recreated. You will lose bookmarks, etc., and need to redo any personalization,  But, if something in the current config files is causing strange problems, this wipes the slate clean.

---

### Post by benawhile on 2015-03-13
I could try that I suppose. I have backed up my bookmarks. Do I delete the entire mozilla foilder in "Home"? But there is a pipelight file in the /usr/lib mozilla folder and I can't delete that, won't that cause a problem?

What about a complete reinstall of FIrefox?

---

### Post by buzzingrobot on 2015-03-13
Just the Firefox folder inside the .mozilla folder.

A reinstall, if memory serves, will leave the config files in place.  (You have to explicitly use the --purge option to apt-get, e.g., "sudo apt-get --purge remove <packagename>", to delete them.  The thinking seems to be that a user's personalizations should not be removed unless the user actaully says so.)

/usr/lib contains system files you shouldn't remove manually.  You can't, anyway, unless you run as root because ordinary users don't have permission to delete them (That's a Good Thing.)  Your system maintains a database of packages that have been installed from the repositories and PPA's. If files contained in those packages are manually removed, it won't know that, which can cause a bit of havoc down the road.

---

### Post by benawhile on 2015-03-13
OK done all that, deleted profile folder, no change! Guess you did al you can? Will leave thread unsolved for a while in case anyone else writes back.
So next thing is to try a reinstall and purge? What do I use for package name, mozilla or firefox?

---

### Post by benawhile on 2015-03-14
For what it's worth, I have gone to settings>software and updates, on the "other software" tab pipelight was still there as a ppa so I removed it. Stupidly I didn't make a note of exactly where it was from. Probably launchpad.
But even after another purge, it still shows up in Firefox and the files are stil there in /usr/lib, some in mozilla and more in a pipelight folder. I note that the mozilla one is actually called pipelight-flash.so.
I am thinking of finding out how to delete them as "root" but first want to see what "ubuntu tweaks" makes of it. Last time I ran tweaks, which you have to run as root, I got a warning "you are running pipelight as root, which is not a good idea". I didn't know what to make of that so I just closed tweaks down and left it, that issue is still unsolved too. Maybe I will try again and ignore the warning.

---

### Post by buzzingrobot on 2015-03-14
> **benawhile said:**
> For what it's worth, I have gone to settings>software and updates, on the "other software" tab pipelight was still there as a ppa so I removed it.

This only removes the URL of the server that hosts the PPA.   The software installed from PPA remains on the system.  ppa-purge removes both the URL and software you've installed from that PPA. That's why you're stilling see pipelight. 

All PPA's on Launchpad.net.  You can run a search there to locate one.

Your system uses a "package manager" to install software. In Linux, packages are archives of software that also contain configuration info and scripts to ensure all the components are installed in the correct place in the file system.  The package manager will also determine which, if any, other packages are required by the one you are installing, and locate, download, and install them automatically.   The package manager maintains a database of all packages currently installed. It locates and downloads packages from lists of repositories (Ubuntu and PPA servers, e.g.) maintained on the system.

The package manager also cleanly removes software. This does not happen when a user manually deletes files. One obvious risk of manually deleting files is that those files may be required by another package. The package manager will "know" if that's the case, but users probably won't. Also, the package manager is not aware files have been manually removed, which can cause problems later.

The software installation, deletion, and update tools in Ubuntu -- Software Center, apt-get, Synaptic, etc. -- are all front ends to the same package manager.

---

### Post by benawhile on 2015-03-14
Ah ha! So do I just put ppa-purge in the terminal or will that delete all the other ppa software I have? I am looking at the launchpad site too. I will not delete anything manually following your advice. AN old Windows trick in this situation was to reinstall the software if it had been badly uninstalled, and then uninstall it again properly. Is this relevant to my problem?

---

### Post by buzzingrobot on 2015-03-14
You run ppa-purge in a terminal and supply it with the same PPA name used to install that PPA.  E.g., "sudo ppa-purge <name of ppa>". It only affects that PPA.  I remember it being picky about getting the name exactly right. (Try a "man ppa-purge".)  A I mentioned earlier, you need to re-add the address of the PPA before ppa-purge will work.

uninstalling and reinstalling might work.  Recall that any configuration/personalization done is maintained in config files that are not normally removed when you remove a package. If those config files have been causing problems, those problems will come back after the reinstall. These config files will be removed if you use the '--purge' option to apt-get.  E.g., "sudo apt-get --purge remove <packagename>".  I don't believe, but may be wrong, that the Software Center app enables that function.

---

### Post by benawhile on 2015-03-14
man ppa-purge
returned this:
No manual entry for ppa-purge
I tried installing synaptic package manager according to this: (For Synapse)
[http://askubuntu.com/questions/449285/is-synapse-application-launcher-available](http://askubuntu.com/questions/449285/is-synapse-application-launcher-available)

According to terminal it was installed but clicking on the icon, in Applications>accessories, opened a tiny window where I typed "pipelight" and it returned "mqchael-pipelight-trusty.list. Nothing else in the window was clickable.

Could you explain a bit more about geting the ppa name and address right?
having trouble as you can see:

ben@ben-MS-7253:~$ man ppa-purge
No manual entry for ppa-purge
ben@ben-MS-7253:~$ sudo ppa-purge [https://launchpad.net/pipelight](https://launchpad.net/pipelight)
[sudo] password for ben: 
sudo: ppa-purge: command not found
ben@ben-MS-7253:~$ sudo ppa purge [https://launchpad.net/pipelight](https://launchpad.net/pipelight)
sudo: ppa: command not found
ben@ben-MS-7253:~$

---

### Post by buzzingrobot on 2015-03-14
Synapse is not Synaptic.  Synaptic is in the standard Ubuntu repos and can be installed from there.

With ppa-purge, as mentioned more than once, you use the same ppa name you used to install that ppa, which is what you did with apt-add-repository.  As mentioned, all ppa's are hosted on launchpad.net, which is searchable. A ppa's page there will provide the correct name to use, if you've lost track of how you installed it in the first place.

---

### Post by benawhile on 2015-03-14
Sorry, I know I have to find the name, but I don't know how. I am on the pipelight ppa page
[https://launchpad.net/pipelight](https://launchpad.net/pipelight) 
and can't aee anything other than "pipelight"

ben@ben-MS-7253:~$ sudo ppa-purgepipelight
[sudo] password for ben: 
sudo: ppa-purgepipelight: command not found
ben@ben-MS-7253:~$ sudo ppa-purge pipelight
sudo: ppa-purge: command not found
ben@ben-MS-7253:~$ 

Why does terminal say "command not found" for ppa-purge? Is that just because I don't have the right name?

---

### Post by dino99 on 2015-03-14
you probably already have used google , right ?

so search for ppa+launchpad+yourunknownpackageyouwanttopurge

i suppose you know what you want to purge :lolflag:

---

### Post by benawhile on 2015-03-14
I installed synaptic package manager from software centre and it found pipelight and removed it, and now shockwave flash v16 no longer shows, so that is this problem solved. Thank you very much for your time. Still not sure about finding the correct name for it as in my above post but maybe the job is done now.

---

### Post by benawhile on 2015-03-14
to 9d9:
Yes, I did that, I found the actual launchpad ppa page for pipelight, but terminal doesn't recognise it, as posted above. What else can I put in to terminal apart from "pipelight"?
Anyway got rid of it with synaptic package manager

---

### Post by buzzingrobot on 2015-03-14
You need to install ppa-purge.

The URL of a PPA page on launchpad.net is *not* what you're looking for.  It will be a formulation like "ppa:<SomeName>" and that can be found on that PPA's page on launchpad.net, or from the source you used to install pipelight originally.

---

### Post by benawhile on 2015-03-14
OOOOOOOOOOOOk! It's done now with synaptic. Maybe the name that synapse returned would have done it IF I had ppa-purge installed!!!

---

