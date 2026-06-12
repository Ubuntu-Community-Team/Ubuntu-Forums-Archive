---
title: "How To: Install OpenOffice 3.2"
date: 2010-02-11
forum: Outdated Tutorials &amp; Tips
---

### Post by scouser73 on 2010-02-11
Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file.

**1** - Once you have done that, extract the .deb file, 

> **OOo_3.2.0_LinuxIntel_install_en-US_deb.tar.gz** 

Then you'll see a file called OOO320_m12_native_packed-1_en-US.9483

**2** - You can remove the existing version of OpenOffice if you wish with this command: 

> **sudo apt-get remove openoffice*.***

**3** - Copy and paste OOO320_m12_native_packed-1_en-US.9483 onto the desktop then open Terminal and paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb**

**4** - Then paste this command: 

> **sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb**

Once you've done that you'll find OpenOffice 3.2 in Office.

---

### Post by mrbobhcrhs on 2010-02-11
wow that was nice and easy. I had to do the remove command before it would do the last command.

---

### Post by JackRock on 2010-02-11
For some strange reason, this worked for me.  I've been trying all day to do this, and been using those commands...but  just copied and pasted right now, and it worked.  Maybe I was mistyping...but I don't think I would have gotten that same error if I did.

---

### Post by Ric_NYC on 2010-02-11
> **jackrock said:**
> for some strange reason, this worked for me.  I've been trying all day to do this, and been using those commands...but  just copied and pasted right now, and it worked.  Maybe i was mistyping...but i don't think i would have gotten that same error if i did.

+1

---

### Post by lindsay7 on 2010-02-11
Worked great, thanks for your hard work putting this together.

---

### Post by aaronchall on 2010-02-11
Would it be better/more secure/more efficient to wait for it in the repositories?  Is there a way to automate the upgrade when that becomes available?

I use Zotero, the Firefox plug-in, to handle bibliographies, is there likely to be any issues?

---

### Post by Clark3934 on 2010-02-11
This worked great for me as well.  I've been waiting for this version and its improved font handing for ages.  Thanks for the post!

---

### Post by david.rahrer on 2010-02-11
Outstanding, thank you.  Worked perfectly as advertised.  I also noticed that 3.2 has fixed my dark theme problems ;)

---

### Post by tractor on 2010-02-11
Thank you for your marvelous, neat, terriffic, wonderful, outstanding way to upgrade to Open Office 3.2 in Ubuntu 9.10. It worked great, and everything works great!!!!!!! Thanks again!!!!!

---

### Post by ridgeland on 2010-02-11
Thank you scouser73

---

### Post by kaleem on 2010-02-11
[SIZE=4]please help me [/SIZE]


I made every thing well , but I don't find any thing in applications\office menu

---

### Post by lindsay7 on 2010-02-11
Did you copy the downloaded file to your Desktop before running the commands in the terminal?

---

### Post by BoredOutOfMyMind on 2010-02-12
> **kaleem said:**
> [SIZE=4]please help me [/SIZE]


I made every thing well , but I don't find any thing in applications\office menu

Did you do the last step? :D

```
sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9472_all.deb
```

---

### Post by Linuxforall on 2010-02-12
Best way to upgrade would be to add the official ppa at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

---

### Post by mikewhatever on 2010-02-12
> **aaronchall said:**
> Would it be better/more secure/more efficient to wait for it in the repositories?  Is there a way to automate the upgrade when that becomes available?

I use Zotero, the Firefox plug-in, to handle bibliographies, is there likely to be any issues?

Open Office 3.2 will only be available with Lucid. If you want to upgrade now, follow this howto.


> **Linuxforall said:**
> Best way to upgrade would be to add the official ppa at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

What exactly is 'the official ppa'? Who made it official? Besides, that ppa was last update nine weeks ago.

---

### Post by jcro001 on 2010-02-12
Thanks....works perfectly

---

### Post by drpjkurian on 2010-02-12
hi
Nice job

---

### Post by Linuxforall on 2010-02-12
> **mikewhatever said:**
> Open Office 3.2 will only be available with Lucid. If you want to upgrade now, follow this howto.




What exactly is 'the official ppa'? Who made it official? Besides, that ppa was last update nine weeks ago.

No one did but that ppa is used generally to upgrade OO packages, its the same team that makes OO packages for Ubuntu.

Also bear in mind that removing OO also removes the metapackage ubuntu-desktop and ordinarily that shouldn't be a problem till you try and upgrade your distro.

---

### Post by Milos_SD on 2010-02-12
Why I can't enable hardware acceleration and why it doesn't have option to enable quick start icon?

---

### Post by pmbuc on 2010-02-12
> **Linuxforall said:**
> Best way to upgrade would be to add the official ppa at [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

Launchpad PPA is empty for now. Either wait for it to be populated or use the DEBs.

---

### Post by cguy on 2010-02-12
Lovely. Thanks! :D

This release is so fast it's scary, haha.

---

### Post by garyyoung on 2010-02-12
I didn't remove 3.1 from my system and the command in step 4 failed with an error message that the .deb was incompatible with a component of the existing open office install.

---

### Post by plaxdan on 2010-02-12
Thanks very much ....worked beautifully.

---

### Post by alvarf on 2010-02-12
Works great :D

---

### Post by dayalsoap on 2010-02-12
This doesn't work. I have a 64 bit machine, and this gives me the crummy 32 bit install.  

Installing the DEB fails.

To get the 64bit .DEB, go here: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

then follow the OP's instructions.  They work well.

Thank you.

---

### Post by RobCandee on 2010-02-12
I also HAD to remove OOo 3.1 in order for the last command to  work - openoffice.org, openoffice.org-core and openoffice.org-common.

As for 64-bit vs. 32-bit - how can i tell which version I have? What I can see (via apt-cache) is 
openoffice.org3:
  Installed: 3.2.0-12
  Candidate: 3.2.0-12
  Version table:
 *** 3.2.0-12 0
        100 /var/lib/dpkg/status

Thanks!

---

### Post by robertcoulson on 2010-02-12
Thanks also from me...worked out great.
Bob

---

### Post by tjk on 2010-02-13
I think I'm misunderstanding something... when I download and uncompress the 64-bit deb file, I can't find the file named: "OOO320_m12_native_packed-1_en-US.9483"  So I'm unsure how you were able to install OO.

> **dayalsoap said:**
> This doesn't work. I have a 64 bit machine, and this gives me the crummy 32 bit install.  

Installing the DEB fails.

To get the 64bit .DEB, go here: [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html)

then follow the OP's instructions.  They work well.

Thank you.

---

### Post by mikewhatever on 2010-02-13
> **RobCandee said:**
> ...

As for 64-bit vs. 32-bit - how can i tell which version I have? What I can see (via apt-cache) is...

You have to run **uname -m**, if the output if i686, you have a 32bit system, if 86_64, then 64bit.


> **tjk said:**
> I think I'm misunderstanding something... when I download and uncompress the 64-bit deb file, I can't find the file named: "OOO320_m12_native_packed-1_en-US.9483"  So I'm unsure how you were able to install OO.

Well, substitute what you do find for the name, after all, it's just a folder.

---

### Post by tjk on 2010-02-13
> **mikewhatever said:**
> 
Well, substitute what you do find for the name, after all, it's just a folder.
Got it. Thanks.

---

### Post by meho_r on 2010-02-13
> **Milos_SD said:**
> ...and why it doesn't have option to enable quick start icon?

You don't need it anymore. Cold start is now ~7-8 sec, and after that, it takes about ~2 sec to start OOo.

---

### Post by frogotronic on 2010-02-13
> **aaronchall said:**
> Would it be better/more secure/more efficient to wait for it in the repositories?  Is there a way to automate the upgrade when that becomes available?

I use Zotero, the Firefox plug-in, to handle bibliographies, is there likely to be any issues?

It will probably end up in the PPA-Scribblers repository for Karmic before too much longer.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

It takes Chris a few days to do the builds, and then they should be updated via the synaptic.   ;)

- CH

---

### Post by calc on 2010-02-13
> **cement_head said:**
> It will probably end up in the PPA-Scribblers repository for Karmic before too much longer.

[https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)

It takes Chris a few days to do the builds, and then they should be updated via the synaptic.   ;)

- CH

Yes, I will try to get it in Lucid and into the ppa for Karmic once ooo-build and Debian have updated their build for the final release. That likely will be sometime mid next week.

---

### Post by dajare on 2010-02-13
Thanks for this! Worked like a treat on 9.04 with the en-GB install.

---

### Post by edward2536 on 2010-02-13
Thanks for the hard work. You have made this very simple . Well done

---

### Post by TocsDeTics on 2010-02-13
Great... Works fine for the CA (català) pakages. Thanks!

I have post i my blog [http://tocsdetics.blogspot.com](http://tocsdetics.blogspot.com)

PauC

---

### Post by Dano58 on 2010-02-14
Perfect.

---

### Post by mafaldaspeaks on 2010-02-14
> **scouser73 said:**
> Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the **Linux .deb** file.

**1** - Once you have done that, extract the .deb file, 



Then you'll see a file called OOO320_m12_native_packed-1_en-US.9483

**2** - You can remove the existing version of OpenOffice if you wish with this command: 



**3** - Copy and paste OOO320_m12_native_packed-1_en-US.9483 onto the desktop then open Terminal and paste this command: 



**4** - Then paste this command: 



Once you've done that you'll find OpenOffice 3.2 in Office.

I tried to follow all these steps. When I clicked Applications>Office, openoffice wasn't there. I'm now installing it through the synaptic package manager.

Update: I forgot to say I'm using the 64bit of ubuntu studio. Synaptic finished installing and it just installed back the 3.1 version.

---

### Post by carlb on 2010-02-14
Thanks.. Worked like a charm.  All I needed to do was substitute the name of the 64bit version in you instructions.

I did get a fail error though on removing the OO hyphen code during the removal of the old OO version.  But it doesn't seem to cause any issues so far

---

### Post by bswilson on 2010-02-14
I would also like to say thanks; this worked perfectly for me and I can't believe how fast OOo is now!  What a great product.

---

### Post by munkee on 2010-02-14
Smashing stuff.  Thanks for sorting that. :grin:

---

### Post by thecliff on 2010-02-15
Worked beautifully.  Thanks

---

### Post by aaronchall on 2010-02-15
Anyone have any issues with Zotero and this upgrade?

---

### Post by gwoodruff on 2010-02-15
I have tried twice now with the same results. I have Karmic 64bit. OO ver 3.1 works fine. I uninstall 3.1 and install 3.2 I get no errors during install but when I try to launch from the terminal I get "** (soffice:6469): WARNING **: unable to get gail version number". I tried to search for a solution but did not find one. Anyone have any tips?

Gary

A reboot made the apps launch. I still get the error when launching from the terminal but at least oo launches (and fast)!

---

### Post by frogotronic on 2010-02-15
> **aaronchall said:**
> Anyone have any issues with Zotero and this upgrade?

Hello,

  Just to be perfectly clear, the method posted in this forum thread **is _NOT_ an upgrade, it is a NEW install.**  This method does not replace the existing 3.1.1 Ubuntu version of OpenOffice.  It will install the Generic Linux non-distro specific version from SUN Microsystems *alongside* (at the same time) with the existing Ubuntu OO install.  The 3.1.1 that is included with Karmic Koala is a distro (Ubuntu) specific version that has MANY differences; among them are:

1) Ubuntu OO is installed to a different location than the SUN variant.
2) Ubuntu OO has 3D OpenGL acceleration.
3) Ubuntu OO has complete integration with the Ubuntu distro (desktop, etc).
4) Ubuntu OO has full functionality of animation and multimedia.

  I believe that the Ubuntu OO is a derivative of the [GO OpenOffice]("http://go-oo.org/").


******IF YOU WANT TO ACTUALLY UPGRADE******

You need to WAIT. Probably by the end of this week (Feb 15th, 2010) there will be an upgrade path available by adding this repository to your sources (SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this **[COLOR="Red"]ppa:openoffice-pkgs/ppa[/COLOR]** into the dialogue.)

Then run Update Manager and you should be able to UPGRADE.

---

### Post by sierrasdetandil on 2010-02-15
> **cement_head said:**
> Just to be perfectly clear, the method posted in this forum thread **is _NOT_ an upgrade, it is a NEW install.**
...
Probably by the end of this week (Feb 15th, 2010) there will be an upgrade path available by adding this repository to your sources (SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this **[COLOR=Red]ppa: openoffice-pkgs/ppa[/COLOR]** into the dialogue.)

Exactly. Right now, the PPA description says "Empty for now, will likely have OOo 3.2.0/3.2.1 debs for Karmic/Lucid  later in the cycle."

I'll just wait for the PPA to get updated (hopefully before Lucid).

---

### Post by frogotronic on 2010-02-15
> **sierrasdetandil said:**
> Exactly. Right now, the PPA description says "Empty for now, will likely have OOo 3.2.0/3.2.1 debs for Karmic/Lucid  later in the cycle."

I'll just wait for the PPA to get updated (hopefully before Lucid).

It will - Check post #33 in this thread.

- CH

---

### Post by j8a on 2010-02-15
Amazing guys, tks!

---

### Post by sleepee on 2010-02-15
hmmm...
weird that the last step gave me an error when i cd'd to the folder, but it worked perfectly when i just copy/pasted the command...

anyway... thanx for the how-to.  OOo is working like a charm..

---

### Post by aaronchall on 2010-02-16
> **cement_head said:**
> Hello,

  Just to be perfectly clear, the method posted in this forum thread **is _NOT_ an upgrade, it is a NEW install.**  This method does not replace the existing 3.1.1 Ubuntu version of OpenOffice.  It will install the Generic Linux non-distro specific version from SUN Microsystems *alongside* (at the same time) with the existing Ubuntu OO install.  The 3.1.1 that is included with Karmic Koala is a distro (Ubuntu) specific version that has MANY differences; among them are:

1) Ubuntu OO is installed to a different location than the SUN variant.
2) Ubuntu OO has 3D OpenGL acceleration.
3) Ubuntu OO has complete integration with the Ubuntu distro (desktop, etc).
4) Ubuntu OO has full functionality of animation and multimedia.

  I believe that the Ubuntu OO is a derivative of the [GO OpenOffice]("http://go-oo.org/").


******IF YOU WANT TO ACTUALLY UPGRADE******

You need to WAIT. Probably by the end of this week (Feb 15th, 2010) there will be an upgrade path available by adding this repository to your sources (SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this **[COLOR=Red]ppa:openoffice-pkgs/ppa[/COLOR]** into the dialogue.)

Then run Update Manager and you should be able to UPGRADE.

Are there any caveats with adding this ppa(?)?  (What is ppa?)  

If I choose to upgrade to Ubuntu 10.4, will there be any issues with openoffice resulting from this?  Is it possible this upgrade is meant to work with Lucid Lynx and may have problems with me on Karmic? 

Aaron

---

### Post by Linuxforall on 2010-02-16
> **cement_head said:**
> Hello,

  Just to be perfectly clear, the method posted in this forum thread **is _NOT_ an upgrade, it is a NEW install.**  This method does not replace the existing 3.1.1 Ubuntu version of OpenOffice.  It will install the Generic Linux non-distro specific version from SUN Microsystems *alongside* (at the same time) with the existing Ubuntu OO install.  The 3.1.1 that is included with Karmic Koala is a distro (Ubuntu) specific version that has MANY differences; among them are:

1) Ubuntu OO is installed to a different location than the SUN variant.
2) Ubuntu OO has 3D OpenGL acceleration.
3) Ubuntu OO has complete integration with the Ubuntu distro (desktop, etc).
4) Ubuntu OO has full functionality of animation and multimedia.

  I believe that the Ubuntu OO is a derivative of the [GO OpenOffice]("http://go-oo.org/").


******IF YOU WANT TO ACTUALLY UPGRADE******

You need to WAIT. Probably by the end of this week (Feb 15th, 2010) there will be an upgrade path available by adding this repository to your sources (SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this **[COLOR="Red"]ppa:openoffice-pkgs/ppa[/COLOR]** into the dialogue.)

Then run Update Manager and you should be able to UPGRADE.

Excellent advice and bear in mind, removing OO 3.1 from Ubuntu also removes metapackage Ubuntu desktop so when you chose a path to upgrade to Lynx rather than fresh install, you will run into issues.

---

### Post by cb951303 on 2010-02-16
BTW, will that PPA use go-oo or vanilla openoffice?

---

### Post by Linuxforall on 2010-02-16
> **cb951303 said:**
> BTW, will that PPA use go-oo or vanilla openoffice?

Go-OO.

---

### Post by zeroseven0183 on 2010-02-16
I recommend this thread. Thank you!
:KS:KS:KS:KS:KS

---

### Post by j8a on 2010-02-16
It works really fast on Xubuntu Karmic Koala, the insallation was succesfull.
Tks guys,

---

### Post by aaronchall on 2010-02-16
> **Linuxforall said:**
> Excellent advice and bear in mind, removing OO 3.1 from Ubuntu also removes metapackage Ubuntu desktop so when you chose a path to upgrade to Lynx rather than fresh install, you will run into issues.

So you're saying that going the PPA route will give me issues?  Or you weren't addressing my question, just reiterating a previously made point?  And what exactly does PPA mean?

Thanks!

---

### Post by dragoslav_ on 2010-02-17
The insallation was succesfull.:D

Thank you!

---

### Post by Smiff2 on 2010-02-18
doesn't look like the ppa [https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa") has been updated.

is there going to be an upgrade path for Jaunty or should I give up and install it manually from Sun? would prefer a proper update if possible.

or am i looking at the wrong ppa? that ppa only shows Hardy in the filter!

---

### Post by aaronchall on 2010-02-18
> **Smiff2 said:**
> doesn't look like the ppa [https://launchpad.net/~openoffice-pkgs/+archive/ppa]("https://launchpad.net/%7Eopenoffice-pkgs/+archive/ppa") has been updated.

is there going to be an upgrade path for Jaunty or should I give up and install it manually from Sun? would prefer a proper update if possible.

or am i looking at the wrong ppa? that ppa only shows Hardy in the filter!

Remember that "end of the week" phrase?  Well the 15th was only about 3 days ago...

I'm just being patient and waiting with bated breath.  I'd still like an answer to my earlier questions, especially these two: 

"Are there any caveats with adding this ppa?

If I choose to upgrade to Ubuntu 10.4, will there be any issues with openoffice resulting from this?"

Aaron

---

### Post by frogotronic on 2010-02-18
> **aaronchall said:**
> Remember that "end of the week" phrase?  Well the 15th was only about 3 days ago...

I'm just being patient and waiting with bated breath.  I'd still like an answer to my earlier questions, especially these two: 

"Are there any caveats with adding this ppa?Aaron

No, using the PPA is safe, because you can always use Synaptic to force a downgrade.

> **aaronchall said:**
> 
If I choose to upgrade to Ubuntu 10.4, will there be any issues with openoffice resulting from this?"
Aaron

No, the Lucid Lynx packages will have different numbering and upgrading should not be a problem.  Also non-standard (third-party) repositories are disabled during upgrade.

- CH

---

### Post by BobJam on 2010-02-19
I loaded that ppa you gave, cement_head, in post #45, and it went to downloading 58 of 60 and then stopped.  So I'm assuming the full upgrade hasn't been compiled yet . . . especially since, as one recent poster said, it's not "the end of the week" yet.

Is this correct, or is there something wrong?

Assuming my evaluation of the circumstance is correct, I'll just cool my heels and wait more.

---

### Post by frogotronic on 2010-02-19
> **BobJam said:**
> I loaded that ppa you gave, cement_head, in post #45, and it went to downloading 58 of 60 and then stopped.  So I'm assuming the full upgrade hasn't been compiled yet . . . especially since, as one recent poster said, it's not "the end of the week" yet.

Is this correct, or is there something wrong?

Assuming my evaluation of the circumstance is correct, I'll just cool my heels and wait more.

Hello,

   It takes a few days to build the packages assuming that they come from GO-OO on time and that they're non-buggy.

  The repository website is here ( [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)) and as you can see (Friday, Feb 19th, 2010) its still empty.   So yes, this is why you get an error on update.

  The packages have finally been updated in debian experimental, so it shouldn't be too much longer now.

- CH

---

### Post by Kirboosy on 2010-02-20
AWESOME!!! OOO 3.2 is amazing!! I got it to install the first try. THANKS ALL! ;)

---

### Post by Copernicus1234 on 2010-02-20
I
Want
It
Now

---

### Post by kemsiro on 2010-02-20
awwwwwwwww when will the ppa available for karmic @_@

---

### Post by bunburya on 2010-02-20
Thanks to OP for the handy instructions!

---

### Post by ftw on 2010-02-21
I extracted the tar file and get a folder not a file. I moved the folder to the desktop and followed the instructions. But I get this...

dpkg: error processing /home/jjubuntu/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/jjubuntu/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb


I'm not sure what that means. Help

---

### Post by dr.sehs on 2010-02-21
install it in easy way 

[LIST=1]
[*]Go to terminal and Type :> sudo add-apt-repository ppa:openoffice-pkgs/ppa
[*]now update your respository by type:  ** **[COLOR=#FF6600]**[B]**[/B][/COLOR]> sudo apt-get update && sudo apt-get upgrade ****[COLOR=#FF6600][COLOR=#000000]and enjoy the new features of openoffice org .[/COLOR][B][B][B][COLOR=#000000]
[/COLOR][/B][/B][/B][/COLOR] 
[/LIST]
 that's all

---

### Post by ftw on 2010-02-21
I had deleted 3.1 like the post had recommended so I guess your method should say to reinstall OO. But I did that and added the repository. Here's the error with the update....

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

So I guess this means there's no karmic package?



> **dr.sehs said:**
> install it in easy way 

[LIST=1]
[*]Go to terminal and Type :
[*]now update your respository by type:  ** **[COLOR=#FF6600]**[B]**[/B][/COLOR] ****[COLOR=#FF6600][COLOR=#000000]and enjoy the new features of openoffice org .[/COLOR][B][B][B][COLOR=#000000]
[/COLOR][/B][/B][/B][/COLOR] 
[/LIST]
 that's all

---

### Post by kemsiro on 2010-02-22
> **ftw said:**
> I had deleted 3.1 like the post had recommended so I guess your method should say to reinstall OO. But I did that and added the repository. Here's the error with the update....

W: Failed to fetch [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

So I guess this means there's no karmic package?

yep

u could see that ppa is empty for now. we gotta wait til it's available or you can do another way around.

convert Go-OO 3.2 .rpm package to .deb package using alien and install it .

---

### Post by Smiff2 on 2010-02-22
sorry, is there going to be an upgrade path for jaunty? 
this is the kind of thing that's very important for ordinary ubuntu users! please will someone official clarify. don't mean to sound annoyed and i do appreciate everyone's work but such a major part of the system must be properly maintained or it looks.. bad. unprofessional. again, no disrespect to anyone offering help here, these guides are appreciated.

i think if there is no technical reason why not then openoffice updates should be supported several ubuntu versions back, and in a timely fashion. it's not ok to say "upgrade to karmic/lucid". people have otherwise working systems and jobs to do, 9.04 isn't very old and we can't be risking a business by doing total system upgrades every 6 months. there are new features in OO.o 3.2 that are vital to some businesses like handling of passworded MS office files. i do feel this reflects on whether ubuntu want to be taken seriously as a business platform.  i hope i'm making sense and not missing a huge announcement somewhere.

---

### Post by frogotronic on 2010-02-22
Well,

  OO3.2rc4 is still in Lucid, and the final release is actually rc5, so the bleeding edge Ubuntu is still slightly behind.  My guess is that it might be another week or so before the 3.2.0rc5 (a.k.a 3.2.0 FINAL) makes it into Lucid and the PPA.

- CH

---

### Post by ftw on 2010-02-22
ok, I can wait but I hope I get some indication that 3.2 is available instead of looking for it but not a big deal either way. I reinstalled 3.1 and it opens up OO Writer in 2 seconds on the 2nd start. It takes 7 seconds the first time. I don't recall it being that snappy with the stock version (whatever that 3.1 OO version in a new Ubuntu install is called)

---

### Post by Xirev on 2010-02-22
Cheers for the 'How To' guide, works perfectly! I am using Linux Mint 7 (based on Ubuntu Jaunty).

---

### Post by frogotronic on 2010-02-22
> **ftw said:**
> ok, I can wait but I hope I get some indication that 3.2 is available instead of looking for it but not a big deal either way. I reinstalled 3.1 and it opens up OO Writer in 2 seconds on the 2nd start. It takes 7 seconds the first time. I don't recall it being that snappy with the stock version (whatever that 3.1 OO version in a new Ubuntu install is called)

Probably because its less integrated into the Ubuntu installation?  :confused:

---

### Post by RastaCalavera on 2010-02-22
after I extracted the tar.gz file and copied it to the desktop, I went into terminal and pasted 
			 				**sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb** 			 		

it then asked for my password and i entered it and then it said this

kylemchugh@Tuesday:~$ cd Desktop
kylemchugh@Tuesday:~/Desktop$ sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb  
dpkg: error processing /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb
kylemchugh@Tuesday:~/Desktop$

This is after I changed to the Desktop folder from root. I get similar errors when I just put in the code with out going to desktop. 

Help?

---

### Post by leandromartinez98 on 2010-02-22
The installation worked for me but many features are missing. For instance, I cannot insert mpeg and mov movies in presentations. I uninstalled it an installed 3.1 again to get back.

---

### Post by timjohn7 on 2010-02-22
> **RastaCalavera said:**
> after I extracted the tar.gz file and copied it to the desktop, I went into terminal and pasted 
			 				**sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb** 			 		

it then asked for my password and i entered it and then it said this

kylemchugh@Tuesday:~$ cd Desktop
kylemchugh@Tuesday:~/Desktop$ sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb  
dpkg: error processing /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb
kylemchugh@Tuesday:~/Desktop$

This is after I changed to the Desktop folder from root. I get similar errors when I just put in the code with out going to desktop. 

Help?

Did you perhaps download a different language version of OpenOffice?  The quoted command is for the US language version so you have to change the US part in the command to the language version you downloaded.  In other words, check that the part after /OOO320-m12_native_packed-i_en is exactly the same as the filename you downloaded.

Do the same for the last command in the original post.

---

### Post by aviedw on 2010-02-22
Worked like a charm. Thanks a lot

---

### Post by Xirev on 2010-02-23
> **Xirev said:**
> Cheers for the 'How To' guide, works perfectly! I am using Linux Mint 7 (based on Ubuntu Jaunty).

Actually I take it back. It screwed up language support for me. When I reinstalled language support, that screwed up OpenOffice, and I can't have them together. I got back to OpenOffice 3.0.

---

### Post by bob brazie on 2010-02-23
Which version is it? 3.2.5?

---

### Post by frogotronic on 2010-02-23
> **leandromartinez98 said:**
> The installation worked for me but many features are missing. For instance, I cannot insert mpeg and mov movies in presentations. I uninstalled it an installed 3.1 again to get back.

Yep, that's why the GO-OO version (or the Ubuntu variant of the GO-OO is more useful).  See Post [#45]("http://ubuntuforums.org/showpost.php?p=8830655&postcount=45")

- CH

---

### Post by Tim_Olaguna on 2010-02-24
> **cement_head said:**
> 

******IF YOU WANT TO ACTUALLY UPGRADE******

You need to WAIT. Probably by the end of this week (Feb 15th, 2010) there will be an upgrade path available by adding this repository to your sources (SYSTEM>ADMINISTRATION>SOFTWARE SOURCES, click the "Other Software" Tab, click the ADD button and copy & paste this **[COLOR="Red"]ppa:openoffice-pkgs/ppa[/COLOR]** into the dialogue.)

Then run Update Manager and you should be able to UPGRADE.

No, this does not work any more (if it ever truly did).  When trying to add the recommended software source I get an error message which says the directory is not available and may have been moved or deleted.

This is one of the frustrating things about Ubuntu and Linux in general.  One of those things which have me keep Windows as my primary operating system.  I too often find myself trying to work from posted messages which encourage readers to solve a problem or issue by relying on information which is no longer valid.  In this case the original message partially quoted above was reportedly posted only a week ago.  And now it is wrong and not reliable already.

---

### Post by aaronchall on 2010-02-24
> **Tim_Olaguna said:**
> No, this does not work any more (if it ever truly did).  When trying to add the recommended software source I get an error message which says the directory is not available and may have been moved or deleted.

This is one of the frustrating things about Ubuntu and Linux in general.  One of those things which have me keep Windows as my primary operating system.  I too often find myself trying to work from posted messages which encourage readers to solve a problem or issue by relying on information which is no longer valid.  In this case the original message partially quoted above was reportedly posted only a week ago.  And now it is wrong and not reliable already.

Regarding the PPA, to my knowledge it is just not available yet.  No one promised it would be available now.  One person said may be available by the end of the week.  The notes on it say "this cycle" if I recall correctly.  You could always install it the other way. This is the NICE thing about linux: multiple ways of doing things, in an open way.  I don't have to have the update, so I'm willing to wait for it to move to the PPA route.  If you need it immediately, do the other install, or learn to compile it yourself from the code.

Frustrating to wait, yes.  But don't say "it doesn't work" when you don't understand it or don't read the posts.  If someone here knows for a fact the PPA won't ever be available, please say so, but no guessing, ok?

---

### Post by leonardo_neo on 2010-02-24
> **RastaCalavera said:**
> after I extracted the tar.gz file and copied it to the desktop, I went into terminal and pasted 
			 				**sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb** 			 		

it then asked for my password and i entered it and then it said this

kylemchugh@Tuesday:~$ cd Desktop
kylemchugh@Tuesday:~/Desktop$ sudo dpkg -i ~/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb  
dpkg: error processing /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /home/kylemchugh/Desktop/OOO320_m12_native_packed-1_en-US.9483/DEBS/*.deb
kylemchugh@Tuesday:~/Desktop$

This is after I changed to the Desktop folder from root. I get similar errors when I just put in the code with out going to desktop. 

Help?

I think you have downloaded the OOo_3.2.0_LinuxIntel_install**_wJRE_en-US**.tar.gz package, which is sometimes given by OpenOffice website as default download option. Check the package which you have downloaded?

The tutorial mentioned here works on the .deb package.

If you can't download the .deb package, then you can manually download it from this page.
> [http://mirrors.ibiblio.org/pub/mirrors/openoffice/stable/3.2.0/](http://mirrors.ibiblio.org/pub/mirrors/openoffice/stable/3.2.0/)
 Select the exact package which is mentioned in the tutorial.

---

### Post by binary10 on 2010-02-26
[FONT=Arial][SIZE=3]On 9.04, I also had problems with spelling dictionaries with other applications after the installation of the en_GB version of OO 3.2.0 as instructed in the first post, the installation had removed the gnome-spell, myspell-en-gb, aspell packages.

A quick re-install of those packages then the other apps (pidgeon, evolution email) all seem to be back to normal. I think :)

[/SIZE][/FONT]

---

### Post by Jayakrishnan.Nair on 2010-02-27
thnx very much .i've been wondering how to launch openoffice 3.2 after installation

---

### Post by frogotronic on 2010-02-27
Hello,

  Well, it looks as though we might not get an upgrade path (via the PPA) for OpenOffice 3.2.0; might have to wait for 3.2.1?

  CC; any comment?

- CH   :popcorn:

---

### Post by Norm24 on 2010-02-27
Worked great.

Thanks for doing the footwork.

---

### Post by RastaCalavera on 2010-02-28
> **timjohn7 said:**
> Did you perhaps download a different language version of OpenOffice?  The quoted command is for the US language version so you have to change the US part in the command to the language version you downloaded.  In other words, check that the part after /OOO320-m12_native_packed-i_en is exactly the same as the filename you downloaded.

Do the same for the last command in the original post.

Thanks for chin checking me! I was making a stupid mistake hahahah got it working smooth now :)

---

### Post by Objekt on 2010-03-03
I got OpenOffice 3.2 installed, thanks to instructions found here: [http://www.unixmen.com/news-today/716-openofficeorg-32-rc2-is-out-]("http://www.unixmen.com/news-today/716-openofficeorg-32-rc2-is-out-")

The 3.2 apps are definitely installed.  For instance, I can right-click on a text file, choose "Open with other application..." and all the OpenOffice 3.2 apps are in the list.

[s]However, none of the OpenOffice apps appear in the Applications->Office menu.  Is there an easy way to make the shortcuts appear there?  I suppose I could put them there manually, but that's tedious.  Also, I have no idea what the executables for Writer, etc. are called, or where their icons are stored, so I couldn't do it that way if I wanted to.[/s]

All the icons appeared in the Applications->Office menu after a reboot.  I'm so used to NOT having to reboot for stuff to work, that I assumed I would see the icons appear right away.  

There is apparently some process that runs at startup, to update the panel menus with any newly-installed applications.  Is there some way to invoke that process manually?  I am a huge fan of Ubuntu's general lack of need to restart.

---

### Post by flyingsliverfin on 2010-03-09
i followed this guide without reading all of the posts afterward...

if i did install 3.2, will it be updated through the normal package manager?
also, if i want to undo it, is there a way to go back the old OO i had (i mean the one the go-oo develops and that ubuntu uses by default)?

---

### Post by Peeved Chemist on 2010-03-12
> **flyingsliverfin said:**
> i followed this guide without reading all of the posts afterward...

if i did install 3.2, will it be updated through the normal package manager?

No.  When the next OpenOffice release comes out, you'll need to install the new packages yourself, in much the same way as the first post in the thread instructs.

> **flyingsliverfin said:**
> 
also, if i want to undo it, is there a way to go back the old OO i had (i mean the one the go-oo develops and that ubuntu uses by default)?

Use synaptic to uninstall the OpenOffice 3.2 packages (they'll all be listed under "Installed (local or obsolete)", then re-install the old OpenOffice. 

I've been using openoffice.org's builds for some time now, due to this bug: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/510474](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/510474) - which makes the ubuntu-supplied OpenOffice packages completely unusable for my work.

---

### Post by KegHead on 2010-03-12
works perfectly!

KegHead

---

### Post by whosgotyou on 2010-03-14
Thank you so much for this. I'm a complete newbie to Ubuntu and this tutorial made upgrading my version of OpenOffice really simple.

---

### Post by aniruddha on 2010-03-15
Works great! Many thanks for starting this thread.

---

### Post by flyingsliverfin on 2010-03-15
is the new OO supposed to have  a new layout? i hardly notice a difference from the old one... maybe something went wrong with the install?

---

### Post by kut77less on 2010-03-18
I get the following error when opening Open office 3.2 afther the install 
> 
/opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/libuno_sal.so.3: version `UDK_3.10' not found (required by /opt/openoffice.org3/program/../basis-link/program/libsfxlx.so)
/opt/openoffice.org3/program/soffice.bin: /opt/openoffice.org3/program/../basis-link/program/../ure-link/lib/libxml2.so.2: no version information available (required by /opt/openoffice.org3/program/libjvmfwk.so.3)

Do you know of any solutions?

---

### Post by ridgeland on 2010-03-21
kut77less,
You're not opening 3.2 are you?
On my PC it's
openoffice.org3 -writer %U
not
soffice.bin
The old panel icon or menu item is just not updated.

Since your post is 3 days old, I'll guess you solved it.

---

### Post by frogotronic on 2010-03-23
Hello All,

  The PPA has been updated with the 3.2.0 debs for Karmic.

- CH    :popcorn:

---

### Post by Linuxforall on 2010-03-23
> **cement_head said:**
> Hello All,

  The PPA has been updated with the 3.2.0 debs for Karmic.

- CH    :popcorn:


Thanks for the info, time to upgrade.

Worked like a charm........thanks again. :D

---

### Post by aaronchall on 2010-03-23
> **cement_head said:**
> Hello All,

  The PPA has been updated with the 3.2.0 debs for Karmic.

- CH    :popcorn:
Thank you so much for the news!  Who do I have to thank when I try this and curse if it doesn't work!? :)  I've had the PPA thing set up for a while now, just waiting on this.  I'm going to go ahead and attempt a normal update, and we'll see what happens!

Thanks again.

Aaron

---

### Post by aaronchall on 2010-03-23
So I updated, and I got this (error?) message:

```
You are upgrading from a version which might have corrupted service/component registry files (*.rdb), especially /var/lib/openoffice/basis3.1/program/services.rdb and the rdb files in /var/spool/openoffice/uno_packages/cache for installed extensions.

If you experience problems with the component manager or segmentation faults involving libstore in either unopkg or OpenOffice.org, please check these files. Try cleanly reinstalling the packages and/or using a clean user profile.
```

I clicked "forward" and it unpackaged everything, should I have clicked cancel?  The dialogue seemed to have a lot of errors in it that I didn't understand, is this normal?

Now that it's all done, I seem to have openoffice 3.2 and I'm not getting any errors when I open it.

What do I do?  Is it possible to roll this PPA update back if I have problems with it?

Thanks,

Aaron

---

### Post by Linuxforall on 2010-03-23
> **aaronchall said:**
> So I updated, and I got this (error?) message:

```
You are upgrading from a version which might have corrupted service/component registry files (*.rdb), especially /var/lib/openoffice/basis3.1/program/services.rdb and the rdb files in /var/spool/openoffice/uno_packages/cache for installed extensions.

If you experience problems with the component manager or segmentation faults involving libstore in either unopkg or OpenOffice.org, please check these files. Try cleanly reinstalling the packages and/or using a clean user profile.
```

I clicked "forward" and it unpackaged everything, should I have clicked cancel?  The dialogue seemed to have a lot of errors in it that I didn't understand, is this normal?

Now that it's all done, I seem to have openoffice 3.2 and I'm not getting any errors when I open it.

What do I do?  Is it possible to roll this PPA update back if I have problems with it?

Thanks,

Aaron

I got the same warning, I ignored and let it install and so far, everything in OO 3.2 is working fine, from Impress to Draw to Writer so I guess, nothing went wrong.

---

### Post by motorcity909 on 2010-03-23
I had that same warning and all seems fine too.

V.happy to have upgraded at last. :p

---

### Post by aaronchall on 2010-03-23
Confirmation bias!  How do we KNOW nothing's wrong?

---

### Post by Linuxforall on 2010-03-23
> **aaronchall said:**
> Confirmation bias!  How do we KNOW nothing's wrong?

If there was, OO would have many issues including not starting and also dkpg would indicate installation errors.

---

### Post by claracc on 2010-03-26
Hallo, Yesterday i upgraded to openoffice 3.2 from 3.1 using the scribbler's ppa and following the method propossed in [http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html).

I had the problem indicated here> 
Code:

You are upgrading from a version which might have corrupted service/component registry files (*.rdb), especially /var/lib/openoffice/basis3.1/program/services.rdb and the rdb files in /var/spool/openoffice/uno_packages/cache for installed extensions.

If you experience problems with the component manager or segmentation faults involving libstore in either unopkg or OpenOffice.org, please check these files. Try cleanly reinstalling the packages and/or using a clean user profile.



I continued installation but when i tried to run openoffice 3.2 it failed.

I removed the ppa repository from sources, updated sources and through synaptic  tried to force the release openoffice 3.1 but something went wrong (or i did something bad) and i obtain the error "component manager cannot run openoffice". I deleted openoffice.org and install it again but the problem persisted.

So i uninstalled with synaptic openoffice.org and openoffice.org-core packages, I add the new ppa repository for openoffice 3.2 and updated it.

This time installation worked and now i have openoffice 3.2 running.

My question is if I want to have the original openoffice 3.1, what I have to do?, what packages i have to uninstall and what to install (please, step by step method).

Thankyou very much in advance.

Regards

---

### Post by wkulecz on 2010-03-26
This is good info, but it also illustrates why Ubuntu will never be a factor on the desktop.  Normal people who are only users want the applications updatable and could care less about the underlying system. 

Unless the major apps, things like Open Office, Gimp, Mozilla, Evolution, are back-ported to current LTS versions you will have no end of ill will for every system update that goes wrong, and they will likely be correct in thinking that Windows 7 And MS Office are cheap at twice the price.

These instructions seemed to work fine for getting OO-3.2 on Ubuntu 8.04, but I don't use OO enough to notice issues with minor features.  Fonts and spell checking seem fine.

---

### Post by Linuxforall on 2010-03-26
If Ubuntu is trying to make sure about stability of the system by not going for latest greatest cutting edge may I ask where is the harm in that? Also to add the PPA, its just matter of copy paste in terminal or go GUI via synaptic route.  Every six months, Ubuntu comes with new distros which has latest updated software as well so users have a choice of latest and best. LTS is for stability so updates are only on basis of need, there is always the PPA or enabling backports route.

---

### Post by SwimDude0614 on 2010-03-27
> **claracc said:**
> Hallo, Yesterday i upgraded to openoffice 3.2 from 3.1 using the scribbler's ppa and following the method propossed in [http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html).

I had the problem indicated here

I continued installation but when i tried to run openoffice 3.2 it failed.

I removed the ppa repository from sources, updated sources and through synaptic  tried to force the release openoffice 3.1 but something went wrong (or i did something bad) and i obtain the error "component manager cannot run openoffice". I deleted openoffice.org and install it again but the problem persisted.

So i uninstalled with synaptic openoffice.org and openoffice.org-core packages, I add the new ppa repository for openoffice 3.2 and updated it.

This time installation worked and now i have openoffice 3.2 running.

My question is if I want to have the original openoffice 3.1, what I have to do?, what packages i have to uninstall and what to install (please, step by step method).

Thankyou very much in advance.

Regards

I had this same problem. I added the PPA, apt-get update then upgrade, and OOo no longer runs. All I had to do was go into package manager, right click openoffice and choose "mark upgrade" and it works beautifully. nothing complicated at all.

---

### Post by Linuxforall on 2010-03-27
> **SwimDude0614 said:**
> I had this same problem. I added the PPA, apt-get update then upgrade, and OOo no longer runs. All I had to do was go into package manager, right click openoffice and choose "mark upgrade" and it works beautifully. nothing complicated at all.

If you wish to revert back to OO 3.1, just remove the ppa entry and reload synaptic, install OO 3.1, as simple as that. My upgrade to OO 3.2 via PPA went quite smooth, no issues on four machines I have upgraded so far.

---

### Post by Andy Wilkins on 2010-04-07
Spot on!

Cheers for these instructions - installing 3.2 was giving me grief for some reason, but your help was invaluable.

---

### Post by nomnex on 2010-06-07
Remember what you remove and re-install the missing dictionaries

For me:

```
       The following packages will be REMOVED:
  aspell aspell-en aspell-fr dictionaries-common hunspell-en-us hunspell-fr
  language-support-en language-support-writing-en language-support-writing-fr
  myspell-en-au myspell-en-gb myspell-en-za openoffice.org-base-core
  openoffice.org-calc openoffice.org-common openoffice.org-core
  openoffice.org-draw openoffice.org-emailmerge openoffice.org-gnome
  openoffice.org-gtk openoffice.org-help-en-gb openoffice.org-help-en-us
  openoffice.org-hyphenation openoffice.org-hyphenation-en-us
  openoffice.org-impress openoffice.org-l10n-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-au openoffice.org-thesaurus-en-us
  openoffice.org-writer python-uno wbritish wfrench
  
```i.e. aspell & hunspell to re-install on my system.

---

### Post by SydneyGB on 2010-07-11
> **mikewhatever said:**
> Open Office 3.2 will only be available with Lucid. If you want to upgrade now, follow this howto.

Is it possible to get OO 3.1 or 3.2 in Jaunty?  I'm considering moving to Karmic or Lucid, but it won't be for a bit.  Mostly I want the ability to colour-code tabs, which is possible in my print server's Karmic (OO v 3.1) but not in Jaunty's (3.0).

---

### Post by birkopf on 2010-08-12
Since few days there is update available. Open Office is automatically downloading version 3.2.1 to desktop. Once that is downloaded, things are easier than before. 

1) Unpack it

In Terminal cd to main directory and:

2) sudo sh ./update

After that you will be seen a lot of:

Preparing to replace ooobasis ...
Unpacking replacement ooobasis ...

Once done - 3.2.1 version will be fully installed and integrated!

---

### Post by Subito Piano on 2011-01-11
Anybody had success with these directions using Ubuntu 9.04 (or Mint 7)??

---

### Post by nomnex on 2011-01-18
> **Subito Piano said:**
> Anybody had success with these directions using Ubuntu 9.04 (or Mint 7)??

yes. here is a ping-point to this thread [http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#more-4011](http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html#more-4011)

---

### Post by Subito Piano on 2011-01-18
Thanks,nomnex!

Anyone still trying to do this with the lastest version (OpenOffice 3.2.1) -- it's not rocket science to change a few numbers, but here's the tweaked directions if you need them: 

Firstly, go to the OpenOffice website: [http://download.openoffice.org/](http://download.openoffice.org/) and download the Linux .deb file.

1 - Once you have done that, extract the .deb file (i just click on it and let the GUI program do the work)

Then you'll see a file called OOO320_m18_native_packed-1_en-US.9502

2 - You can remove the existing version of OpenOffice if you wish with this command:

sudo apt-get remove openoffice*.*

3 - Copy and paste OOO320_m18_native_packed-1_en-US.9502 onto the desktop then open Terminal and paste this command:

sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/*.deb

4 - Then paste this command:

sudo dpkg -i ~/Desktop/OOO320_m18_native_packed-1_en-US.9502/DEBS/desktop-integration/openoffice.org3.2-debian-menus_3.2-9502_all.deb

Once you've done that you'll find OpenOffice 3.2 under "Office" in the menu.  

When they upgrade to the next version of OpenOffice, use the same commands, changing to reflect the new file name of the packed file you download and the unpacked file you create.

Rationale for this:  I've had a couple older computers that simply DON'T like Mint 9/Ubuntu 10.04....but Mint 7/Ubuntu 9.04 works just fine.  :-)

---

### Post by RegUB on 2011-02-07
> **Linuxforall said:**
> 

Also bear in mind that removing OO also removes the metapackage ubuntu-desktop and ordinarily that shouldn't be a problem till you try and upgrade your distro.

Anyone know if there is any way round this? I would like to upgrade to OO 3.2 (or even 3.3 now that it is available) but I don't want to lose the option of upgrading my distro at a later date. I am currently on Ubuntu 8.04.

---

### Post by nomnex on 2011-02-07
u want to upgrade from 8.04 to what? 11.04. That's a good recipe for trouble.

Anyway, go for it, install OOo. It is a simple matter or removing it and re-installing the Ubuntu OOo version before the upgrade.

---

