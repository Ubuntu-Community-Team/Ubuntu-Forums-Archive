---
title: "My current Hardware Enablement Stack (HWE) going out of support ?"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by hebdave on 2014-07-16
Hi my current Hardware Enablement Stack (HWE) is going out of support
on 07/08/14.  After this date security updates for critical parts (kernel
and graphics stack) of your system will no longer be available. THIS IS WHAT MY UPDATE SAID THIS MORNING.


For more information, please see:
[http://wiki.ubuntu.com/1204_HWE_EOL](http://wiki.ubuntu.com/1204_HWE_EOL)  (it then says !)

So I went to the above address and it said I should run this in the terminal - [COLOR=#333333]hwe-support-status --verbose

**This then says if you do not want to upgrade to do this command and reboot your system - **[/COLOR]**sudo apt-get install linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty linux-image-generic-lts-trusty**
The problem then is I get this error -

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgl1-mesa-glx-lts-trusty : Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but it is not going to be installed
                              Recommends: libgl1-mesa-dri-lts-trusty (>= 7.2) but it is not going to be installed
 xserver-xorg-lts-trusty : Recommends: libgl1-mesa-dri-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-input-all-lts-trusty but it is not going to be installed
                           Recommends: xserver-xorg-video-all-lts-trusty but it is not going to be installed
                           Recommends: x11-xserver-utils-lts-trusty but it is not going to be installed
                           Conflicts: libglapi-mesa:i386 (>= 0~)
E: Unable to correct problems, you have held broken packages.

The packages 'directly above' seem to be the very ones which it recommends I am meant to install 'further above' i put in bold. Only it seems to talk about them not being allowed to be installed upon 'trying to install' or something ?

[COLOR=#333333]
Any way to try and fix the broken packages I did a sudo apt-get update and [/COLOR]sudo apt-get -f install. This is because I don't understand the explanations of the apt-get 'how to page' (in ubuntu documentation) well enough **each time** I read them. The help pages leave me more questions about which packages belong to which programs for instance ? Do I even need to know that ?... etc. And is there an overall package restore command so I don't need to work out what dependencies I am missing ? The questions I ask I am not sure what they mean either in asking them so it all rather confusing really. :?

Thanks.

---

### Post by kansasnoob on 2014-07-16
Are you running with proposed updates enabled?

Typically that's a bad idea.

---

### Post by grahammechanical on 2014-07-16
The wiki link points out that Ubuntu 12.04.4 now has the same hardware and graphic stack as Ubuntu 14.04. But in August 14.04 will move to being 14.04.1 with the latest Linux hardware and graphic stack. Ubuntu 12.04 will not and cannot get those updates. That is the situation. Notice these two FAQ

> 
[LIST]
[*]**I am running 12.04.2 HWE. From August 8, 2014 onwards my system will no longer receive package updates?**
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]Not true. Such a system will only stop receiving updates for the kernel and the graphics stack. The rest of the software will continue to get updates.[/FONT][/COLOR]

[LIST]
[*]**So if I am running 12.04.3 (as seen from *lsb_release -d*) then starting from August 8, 2014 my kernel and graphics stack will no longer receive package updates?**
[/LIST]
[COLOR=#333333][FONT=Ubuntu Beta]Not true. 12.04.3 is not 12.04.3 HWE. And since HWE (and thus a new kernel series) cannot be introduced through regular package updates it is possible to update a non-HWE system to arrive at a later point release, such as 12.04.3, and still preserve the EOL date of April 2017.[/FONT][/COLOR]


A Long Term Support release only gets hardware updates for the first two years and it gets that by means of what are called point releases (12.04 > 12.04.1 > 12.04.2 > 12.04.3 > 12.04.4)

But an LTS release will continue to get maintenance updates for the full length of its supported life = 5 years.

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

What is the benefit of having the latest Hardware Enablement Stack? It means that Ubuntu will run on newer hardware. But my hardware is about 6 years old. The latest HWE does not benefit me using this machine. But if I was to buy a new machine with the latest hardware then It would better if I installed Ubuntu 14.04.1 rather than 12.04.0 which has an HWE that is two years old. That is the point of Point Releases. It is not about no longer getting security fixes. But about keeping Ubuntu up to date with the latest hardware.

Do you need a newer HWE? 

Regards.

---

### Post by kansasnoob on 2014-07-16
> Ubuntu 12.04.4 now has the same hardware and graphic stack as Ubuntu 14.04

No, if a user installed using the 12.04.4 image they'd have the Saucy HWE stack.

It's also possible that a user may have manually installed a later HWE stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I raised an issue here:

[http://ubuntuforums.org/showthread.php?t=2234478](http://ubuntuforums.org/showthread.php?t=2234478)

But based on current test results no one should be seeing this warning unless they have the proposed repos enabled. If that's the case they just need to be patient because the Trusty HWE stack is not quite complete and won't be fully tested in Precise until August 17th :)

---

### Post by hebdave on 2014-07-16
Are okay well i understand enough to release I'm probably okay as i am then. My computer is about 2 to 3 years old now with the i3 core processor as an example of hardware to give you an age idea. I was worried when I read the page 'that you also mentioned' when I read this -
[COLOR=#333333][FONT=Ubuntu Beta][I]
Such a system will only stop receiving updates for the kernel and the graphics stack 

[/I][SIZE=3]I then thought that I may not get the full security I needed for my system. I don't no enough about kernels and there purpose , its seems above when you said -[/SIZE][/FONT][/COLOR][COLOR=#000000]'this is the point of Point Releases it is not about no longer getting security fixes' that I am now thinking that there just for hardware. I still get all the security updates required to keep everything secure hopefully therefore.
[/COLOR]
[SIZE=3][FONT=Ubuntu Beta][COLOR=#333333]My feeling was that a older long term release may be more stable and alot of the updates that come through are also given to the newer LTS version anyway. I may use ubuntu for website related activities soon so wondered if a more tried and tested Ubuntu was better was my reasoning. Please excuse any technical misunderstanding of Ubuntu I rarely get time to look into it all to be honest. The danger of picking up things gradually is you then forget the other Ubuntu bits you learned a few months ago - or I tend to find myself forgetting things where others seem to remember - if only my grey matter did not leak - frustrating !![/COLOR][/FONT][/SIZE]

---

### Post by 3rdalbum on 2014-07-16
It is your choice, but Ubuntu 14.04 has had a good shake-down period and I don't see a reason for you not to use it. It's very good, very few complaints even on the release day.

---

### Post by kansasnoob on 2014-07-17
> **hebdave said:**
> Are okay well i understand enough to release I'm probably okay as i am then. My computer is about 2 to 3 years old now with the i3 core processor as an example of hardware to give you an age idea. I was worried when I read the page 'that you also mentioned' when I read this -
[COLOR=#333333][FONT=Ubuntu Beta][I]
Such a system will only stop receiving updates for the kernel and the graphics stack 

[/I][SIZE=3]I then thought that I may not get the full security I needed for my system. I don't no enough about kernels and there purpose , its seems above when you said -[/SIZE][/FONT][/COLOR][COLOR=#000000]'this is the point of Point Releases it is not about no longer getting security fixes' that I am now thinking that there just for hardware. I still get all the security updates required to keep everything secure hopefully therefore.
[/COLOR]
[SIZE=3][FONT=Ubuntu Beta][COLOR=#333333]My feeling was that a older long term release may be more stable and alot of the updates that come through are also given to the newer LTS version anyway. I may use ubuntu for website related activities soon so wondered if a more tried and tested Ubuntu was better was my reasoning. Please excuse any technical misunderstanding of Ubuntu I rarely get time to look into it all to be honest. The danger of picking up things gradually is you then forget the other Ubuntu bits you learned a few months ago - or I tend to find myself forgetting things where others seem to remember - if only my grey matter did not leak - frustrating !![/COLOR][/FONT][/SIZE]

You never did answer my question. Are you running with proposed updates enabled?

Kernel updates quite frequently are security related updates so if you're running a kernel in the 3.5, 3.8, or 3.11 series then you will not receive kernel related security updates after August 8th, but the Trusty HWE stack is not yet complete so you should not be receiving that message yet.

Please read again:

[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by hebdave on 2014-07-17
Are okay well when I looked in the software sources section in the settings the proposed part was NOT ticked. So no it is not enabled. Whether at one point it was enabled by me I am not certain. Also in the past when I have added software or packages from the internet ( trustworthy websites). They occasionally advised to update my whole system with updates which were not yet released officially. So this may of possibly caused something at some point perhaps which triggered the warning [SIZE=1][[COLOR=#000000]kansasnoob[/COLOR]]("http://ubuntuforums.org/member.php?u=554595")[/SIZE]. The websites I used always gave all the commands layed out for us to copy and paste into the terminal. If it was to hard to do and I didnot understand it I would not do it though. This is why on the whole my ubuntu 12.04.3 works pretty well. I mainly try to stick to the main repositories as well. 

Regarding the Kernel are you saying that there are protection issues that surround this if I do not upgrade in my particular situation ?

Also I should say that I added a 32 bit terminal command for applications that just ran on 32 bit computers- My computer being 64 bit. I assumed that I could then run 32 or 64 bit applications and my computer has remained a 64 bit.

Actually after re-reading the docs I have way to many questions which  will confuse me in terms of which I should ask you ( I tend to not really quite understand what the docs mean due to all the technicalities)- in other words it would confuse you as to why I asked a question that made little sense to you.  I can understand perhaps 50 % of whats said but am not certain how much of that 50 % I truly understand. Plus I would have about 20 questions at least.  

**I have now tried to upgrade and it won't let me. It says Package dependencies cannot be resolved. This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time. The following packages have unmet dependencies:**
**libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed**
**                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed**
**                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed**
**xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed**


Please note you already have answered it with saying upgrade but I just wanted to make sure. I read in the past applications stay with you that you had prior when upgrading. I did add things that were not in the main repository perhaps for one or two things and they seemed to still get updated by tick boxes I enabled through software sources 3rd party repository. I don't think that will affect my upgrade. Will upgrading solve my problems with the kernels and KWE stack since my computer is only 2 years or 3 years old ? I read on ask ubuntu - **[SIZE=3][COLOR=#333333][FONT=UbuntuRegular]The point release essentially contains the bug fixes the version has got since it was released to the public, which includes security fixes, package updates, translation packs updates, etc.[/FONT][/COLOR].[/SIZE]** So with this in mind I assume the HWE is not critical and that is the part of the kernel they are updating. And also I am likely to receive it eventually anyway ?

Please feel free to just concentrate on getting me updated if there ar too many questions at present.

---

### Post by hebdave on 2014-07-17
High I googled the specific issue about the HWE stack [h=1][Hardware Enablement Stack (HWE) out of support]("http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support")[/h]and it gave me this for the computer I am running [http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support](http://askubuntu.com/questions/493541/hardware-enablement-stack-hwe-out-of-support) . I used the AMD 64 terminal command at the bottom of that askubuntu thread. It seemed say you can get a bug in updating. So I used this and it just updated the HWE - 

sudo apt-get install -V libglapi-mesa-lts-trusty libgl1-mesa-glx-lts-trusty xserver-xorg-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty libgl1-mesa-dri-lts-trusty x11-xserver-utils-lts-trusty libglapi-mesa-lts-trusty:i386 libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386 libgles2-mesa-lts-trusty libglapi-mesa-lts-trusty mesa-vdpau-drivers-lts-trusty
To be honest I dont know how much help I am being putting this hear. The command added and removed depencies accordingly so it seemed. this then allowed the update to be installed as well all in the same command. 

I do hope I have not caused a problem further down the line for myself by using the command. Perhaps if someone can look at the above command and tell me if it was not just an inadequate fix I'd know it was legitimately good.

Thanks.

---

### Post by dschaller on 2014-07-17
I had the same problem as the OP. I was prompted both by Update Manager and by running hwe-support-status to upgrade HWE. When I tried, Update Manager kept crashing and the command line apt-get install said there were too many dependency problems to install the updates. Does post #9 work then? That looks a little different than what hwe-support-status said to do.

---

### Post by MrSteve on 2014-07-17
had that update message a few days ago and updated 
my 12.04.4 had to be reinstalled but i do have separate partitions for /, /swap, /home 
so no data lost

after the update on a clean 12.04.4 install all went well
running kernel 3.13.0-32-generic on ubuntu 12.04.4

my wife's system (fully updated) is still on 3.2.0-67-generic ...

---

### Post by hebdave on 2014-07-18
> **dschaller said:**
> I had the same problem as the OP. I was prompted both by Update Manager and by running hwe-support-status to upgrade HWE. When I tried, Update Manager kept crashing and the command line apt-get install said there were too many dependency problems to install the updates. Does post #9 work then? That looks a little different than what hwe-support-status said to do.

I did have problems with the first time I used the ask ubuntu information. Alot of applications stopped working. I am unsure but I think it was perhaps virtualbox that was not updated so it perhaps tries to update that to or something obscure like that. Anyway I had to reload an image I had from clonezilla. After that I started with the link I gave you and proceeded one at a time to try each command. This time I seemed to have few if any problems and the update manager no longer showed the HWE stack error. It seems like things are fixed but I had a problem with chrome syncing tonight and cannot get the sign in to chrome working at all well with my password manager. Oddly the password manager works fine with all other pages including gmail. So it may be an unrelated problem. 

When using bleech bit I get an error related to google autofill tables or something. So this might be related to the above syncing issues or the password filling.

It would be nice to know that the commands askubuntu posted were safe commands. So perhaps some one could still confirm this for myself and you too ? If I get loads of errors I will let you know. And if you use the askubuntu recommendation particularly the 2nd to last command for 'amd 64 processors' be sure to backup everything before trying what I did.

Please note the pages that have been put up in the docs (links recommended to me) may not be correct for some people for HWE enablement stacks. This is why askubuntu showed the amd processor alternative to which I added to this forum above. As to whether it completely reliable it would be nice to see what others thought of the command.

---

### Post by dschaller on 2014-07-21
Thanks for the update, hebdave. I appreciate it. As I've researched the bugs and problems with upgrading the HWE stack, I'm coming to the conclusion that maybe I just shouldn't do it for awhile. I find multiple command suggestions for upgrading to the 3.13 HWE kernel on 12.04 and none of them are really confirmed to work 100% that I can tell. I just can't afford to have my production machine go down if this goes wrong. I'd be interesting is someone posting something like: "Here's the official way to do this ..." or if someone could confirm that a particular upgrade path has really worked seamlessly for them with no apparent problems afterward. It's a little disappointing that the update manager throws a warning at you but then can't do the upgrade it asks for and doesn't even seem to give the correct instructions for doing it. I am running AMD64 12.04.4 with the 3.5 (12.10) kernel.

---

### Post by MrSteve on 2014-07-27
just an update ...

3 times this Ubuntu HWE update blow my stystem out of the water (3 re-installs)
changed to Kubuntu 12.04.4 with no problems ../

---

### Post by mc4man on 2014-07-27
The advice given on how to upgrade mesa/xorg to the lts-trusty packages is not going to work, at least not currently.
(- they should have created a meta package that can do it properly

It can be done thru synaptic but it's not straightforward & not easily described 
(- I just did 12.04 on lts-quantal to lts-trusty. 
As it stands now with mesa/xorg one needs to first remove the lts-quantal packages which will be replaced with the release versions. (or lts-whatever you have

Then install the lts-trusty packages, making sure to get all that are needed. (the 2 xorg meta packages are useful here - input-all & video-all.
It's one of these deals that requires one to get it right & complete before logging out or restarting or game over. Searching lts-'whatever you have' & lts-trusty in synaptic is also useful to the process

---

### Post by kc1di on 2014-07-27
the recommendation [in this]("http://ubuntuforums.org/showthread.php?t=2235731&highlight=hwe") thread worked on my Wife's laptop.

---

