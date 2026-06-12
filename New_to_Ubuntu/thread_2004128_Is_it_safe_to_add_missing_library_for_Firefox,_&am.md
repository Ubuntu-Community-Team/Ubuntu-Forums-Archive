---
title: "Is it safe to add missing library for Firefox, &amp; how to do so ?"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by aka-John99 on 2012-06-15
Not sure what to say first. I am new to Ubuntu, and trying to use Firefox Aurora.

I do have canonical Firefox installed, and multiple firefox versions if I boot into Windows, but I would like to be able to run the Mozilla Firefox Aurora channel (which is two releases ahead) on Ubuntu. The Mozilla Firefox releases are almost exclusively 32 bit.

I initially had an error
```
 error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory
```I installed gcc & g++ hoping that may easily and safely provide the required library, because I presume Mozilla Firefox must need a c++ library.

I now get a slightly different error,  presumably because I still do not have the required library
```
XPCOMGlueLoad error for file /home/johnh64admin/.mozilla/fxfx/fxAurora/firefox/libxpcom.so:
libxul.so: cannot open shared object file: No such file or directory
Couldn't load XPCOM.

```I am currently using a 64 bit AMD, and Ubuntu 12.04 LTS

I have seen related information such as
[http://www.betamaster.us/blog/?p=1114](http://www.betamaster.us/blog/?p=1114) 
presumably the library needed will be this one [http://packages.ubuntu.com/precise/libstdc++6](http://packages.ubuntu.com/precise/libstdc++6)

Being new to Ubuntu I am not sure 

[LIST]
[*]how to add the new library, (Will File Roller do this or must CLI be used)
[*]or whether it is safe to do so, (At least seem to have a source for my version)
[*]is there any danger it could replace essential Ubuntu  files with wrong versions if I try this.
[/LIST]
 
Thanks for any advice that you may give. I note you have a firefox mega thread, and another forum for other OS & distros, so I hope I have not posted in the wrong place.

---

### Post by vasa1 on 2012-06-15
AFAIK, Firefox (stable) and Firefox (Aurora) don't have any requirements other than what's present in a default Ubuntu install. At least for 32-bit.

---

### Post by aka-John99 on 2012-06-15
Thanks for the quick reply.

Sorry I only provided part of the information. I am using  64bit version of Ubuntu. And the Firefox install instructions do warn that additional libraries maybe required.

The install instructions (Standard release and probably written for  Version 11)  
[https://support.mozilla.org/en-US/kb/install-firefox-linux](https://support.mozilla.org/en-US/kb/install-firefox-linux)
say > libstdc++5 error As noted above, you need to install the [required libraries]("http://www.mozilla.com/firefox/system-requirements.html") for Firefox to work. Many distributions don't include libstdc++5 by default. 
I also found the old articleRunning 32-bit Applications on 64-bit Debian GNU/Linux [http://www.debian-administration.org/articles/534](http://www.debian-administration.org/articles/534)

---

### Post by vasa1 on 2012-06-15
> **aka-John99 said:**
> Thanks for the quick reply.

Sorry I only provided part of the information. I am using  64bit version of Ubuntu. And the Firefox install instructions do warn that additional libraries maybe required.
...
I suggest you look at the launchpad ppa which should be the safest way to go. You can get beta, Aurora, and nightly, all specifically sorted out for Ubuntu: [https://launchpad.net/~mozillateam](https://launchpad.net/~mozillateam)

I'll try to post a more specific link in a while.

See: [http://www.ubuntuupdates.org/ppa/firefox_aurora?dist=precise](http://www.ubuntuupdates.org/ppa/firefox_aurora?dist=precise)

---

### Post by vasa1 on 2012-06-15
BTW, since I'm still on 32-bit, I don't follow 64-bit news a lot, but there's been some debate about 64-bit builds.

---

### Post by aka-John99 on 2012-06-15
> **vasa1 said:**
> BTW, since I'm still on 32-bit, I don't follow 64-bit news a lot, but there's been some debate about 64-bit builds.

I have not really followed that myself, because until recently I was using  Windows 32 bit XP.

If use the method you suggest is that going to replace my current build with the Aurora version ? I was hoping to be able to install multiple versions, the method I was attempting should have allowed me to keep the ordinary Release, and then launch a totally self contained version from the CLI

---

### Post by vasa1 on 2012-06-15
> **aka-John99 said:**
> I have not really followed that myself, because until recently I was using  Windows 32 bit XP.

If use the method you suggest is that going to replace my current build with the Aurora version ? I was hoping to be able to install multiple versions, the method I was attempting should have allowed me to keep the ordinary Release, and then launch a totally self contained version from the CLI

Yes, it will replace the existing version but, **and this is just a guess**, won't it provide you the library you need?

---

### Post by aka-John99 on 2012-06-15
I am new so maybe not understanding you too well. So

[LIST=1]
[*] I install Aurora using the ppa. It must then work and have required libraries for itself. But I had hoped to keep multiple versions.
[*] I could try running the Mozilla version, and that may then run using the same libraries, but I have then two working Aurora versions.
[*]BUT If I uninstall the Aurora ppa version to replace it with the Firefox ppa version I have at present, presumably any libraries disappear again with the uninstall.
[/LIST]
Is there a way to install both Firefox and Aurora at once  that you are aware of ?
I am quite content to start the alternative one from the CLI and not have it globally installed if that is easier to do.


Although this question relates to Firefox, are there not other instances where people want to have  two different  versions of some application installed. I was hoping there would be a relatively simple and easy solution. 


(The solution in Windows is simply to do a custom install and set up each Firefox version in it's own directory, if you ensure the profiles and command arguments are correct they will even open simultaneously side by side if necessary.)

---

### Post by vasa1 on 2012-06-15
One point that I realised is that only the Firefox installed from the ppa I referred to will be protected by Apparmor. The others may not be. Of course, having a program installed entirely in the user's home has its own protection by way of permissions but I don't know too much about that.

---

### Post by aka-John99 on 2012-06-15
Solved, so thanks for all the help.

As you pointed out Firefox is available as 64bit builds. By default the Mozilla Firefox site offers 32bit although it had detected the OS it did not seem to match the bit size. When I  look at the ppa/canonical User Agent String it is clearly a 64 bit edition on both Release and Aurora Channel.

There may be better methods but this meets my requirements


[LIST=1]
[*]use the ppa Aurora channel as you explained above.
[*]use the Mozilla Firefox; less publicised; 64 bit download and install in a separate directory.
[/LIST]

[LIST]
[*]  this did not require me to sort out any additional libraries
[*]the canonical Aurora runs as the standard browser from the launcher
[*]the current  Mozilla Firefox release runs from the CLI
[/LIST]
Thanks again, John

---

