---
title: "NVIDIA fx5500 installation in ubuntu which ruined my system"
date: 2009-05-11
forum: Philippine Team
---

### Post by vivatsemiramis on 2009-05-11
i had my old pentium 4 2.0ghz desktop upgraded recently: changed the motherboard and power supply because according to the technicians the old motherboard would almost blackout; then added another 160gb ide drive, 1gb memory ddr266, and replaced my ati radeon with nvidia geforce fx5500. the old xp2 system that was working was corrupted, so i tried having the old hard drive reformatted and had ubuntu installed.

everything worked fine, the way i expected it until i downloaded the nvidia driver and installed the 173 driver (which according to the system was the recommended choice, instead of 96). after the installation finished, i rebooted the computer as instructed, and got a BLANK SCREEN after the ubuntu login bar finished.

i panicked. i ran the safe mode, but i failed to do my research. so i just restarted that pc. i thought maybe i could put on the 9.04 live cd again and repair it, or have a clean install again. it hanged after the "loading hardware drivers" with an init:rc-default main process error.

it was 1 am, and my brain was slowing down. instead of stopping and resuming tomorrow, i proceeded to fix it. stupid mistake perhaps, i thought of reformatting the old hard drive (where the ubuntu was installed) with XP setup. i deleted it and made a new ntfs partition. i thought my problems were solved.

it's 3am already, and i tried both the intrepid and jaunty live cd. after i chose any option among the menu, the screen would flash 'loading' then it hanged at the 'loading hardware drivers' again and the rc-default thing; been trying for like 3 hours now. it was so frustrating.

is this a hopeless case scenario? what can i do? does this mean i would never be able to use ubuntu in this system ever again? my sisters would be so much disappointed. if not for the nvidia, and the consequent stupidities, it would have been running perfectly. please. thanks

---

### Post by vivatsemiramis on 2009-05-11
after doing some research and learning about where the problem possibly lies, i tinkered something and was able to install from the live cd. i rebooted and turned the on-board graphics card off, then i turned the apci something at the other options (or pressing f6 at the live cd menu).

things went well, i didn't know whether because i turned the on-board graphics card off (which was turned on the whole time), or because of turning off the apci something at the f6 option. whew, i can finally go to sleep after this finishes. i had almost given up on ubuntu in this old desktop of mine.

regards

---

### Post by dodimar on 2009-05-11
> **vivatsemiramis said:**
> after doing some research and learning about where the problem possibly lies, i tinkered something and was able to install from the live cd. i rebooted and turned the on-board graphics card off, then i turned the apci something at the other options (or pressing f6 at the live cd menu).

things went well, i didn't know whether because i turned the on-board graphics card off (which was turned on the whole time), or because of turning off the apci something at the f6 option. whew, i can finally go to sleep after this finishes. i had almost given up on ubuntu in this old desktop of mine.

regards

I believe its the acpi that might cause the issue.

like someone said to me. Linux mostly works out of the box, but when you want to set it up, it'll be hard....

had the same issue with an ATI card.. I already forgot the steps I made to make it work,,

---

### Post by kingkalag on 2009-05-11
> **vivatsemiramis said:**
> i had my old pentium 4 2.0ghz desktop upgraded recently: changed the motherboard and power supply because according to the technicians the old motherboard would almost blackout; then added another 160gb ide drive, 1gb memory ddr266, and replaced my ati radeon with nvidia geforce fx5500. the old xp2 system that was working was corrupted, so i tried having the old hard drive reformatted and had ubuntu installed.

everything worked fine, the way i expected it until i downloaded the nvidia driver and installed the 173 driver (which according to the system was the recommended choice, instead of 96). after the installation finished, i rebooted the computer as instructed, and got a BLANK SCREEN after the ubuntu login bar finished.

i panicked. i ran the safe mode, but i failed to do my research. so i just restarted that pc. i thought maybe i could put on the 9.04 live cd again and repair it, or have a clean install again. it hanged after the "loading hardware drivers" with an init:rc-default main process error.

it was 1 am, and my brain was slowing down. instead of stopping and resuming tomorrow, i proceeded to fix it. stupid mistake perhaps, i thought of reformatting the old hard drive (where the ubuntu was installed) with XP setup. i deleted it and made a new ntfs partition. i thought my problems were solved.

it's 3am already, and i tried both the intrepid and jaunty live cd. after i chose any option among the menu, the screen would flash 'loading' then it hanged at the 'loading hardware drivers' again and the rc-default thing; been trying for like 3 hours now. it was so frustrating.

is this a hopeless case scenario? what can i do? does this mean i would never be able to use ubuntu in this system ever again? my sisters would be so much disappointed. if not for the nvidia, and the consequent stupidities, it would have been running perfectly. please. thanks

restart mo and system hit ESC to enter to GRUB select mo ang line na may ( recovery mode ) pagkatapos mag load scroll down hanapin mo ang line that says root terminal. 
hit enter
type: login
enter your username:
password:

$ sudo apt-get remove compiz compiz-core

$ sudo reboot

good luck

---

### Post by kingkalag on 2009-05-11
restart mo ang system
tapos HIT ESC to enter GRUB
then select: kernel Recovery Mode
and then select :root drop to root shell prompt
type: login
enter your username:
and your password:

sudo apt-get remove compiz compiz-core 

sudo reboot

good luck once again... .. ..

---

### Post by vivatsemiramis on 2009-05-11
> **dodimar said:**
> I believe its the acpi that might cause the issue.

like someone said to me. Linux mostly works out of the box, but when you want to set it up, it'll be hard....

had the same issue with an ATI card.. I already forgot the steps I made to make it work,,

this is a different question, but partly related. what am i supposed to do now with the graphics driver with my nvidia fx5500? should i choose the 96 driver to enable compiz? i'm afraid i would have to go through the same process again if ever it fails me again. regards :)

---

### Post by kingkalag on 2009-05-11
> **vivatsemiramis said:**
> this is a different question, but partly related. what am i supposed to do now with the graphics driver with my nvidia fx5500? should i choose the 96 driver to enable compiz? i'm afraid i would have to go through the same process again if ever it fails me again. regards :)


run into the same problem before when I installed intrepid to my friends system, follow my instruction to remove compiz for now and install it later after you do all the updates and upgrades.

---

### Post by vivatsemiramis on 2009-05-11
> **kingkalag said:**
> run into the same problem before when I installed intrepid to my friends system, follow my instruction to remove compiz for now and install it later after you do all the updates and upgrades.

thanks for that. by the way, when i enabled the on-board graphics card the loading hardware drivers hanging problem occurred again, so my conclusion is that it must be with the acpi in the live cd menu (have to turn it off) and that the on-board graphics card should be disabled. additional info for those who are having the same problem. i did it for more than 5 times, both thru the live cd and the login--those two are the culprits.

---

### Post by guitar_man on 2009-05-11
ang agang threads nito....good morning muna sa inyo.hehe
nasubukan mo na ba gamitin yung driver 173????
minsan kasi yun ang gagana...parehas sila pwede para sa fx5500
naexperience ko na tong situation na to..pero 5200 nga lang yung sa akin

---

### Post by loell on 2009-05-11
if the 96 driver series works well and with compiz then i think you should stay with it.

---

### Post by vivatsemiramis on 2009-05-12
> **guitar_man said:**
> ang agang threads nito....good morning muna sa inyo.hehe
nasubukan mo na ba gamitin yung driver 173????
minsan kasi yun ang gagana...parehas sila pwede para sa fx5500
naexperience ko na tong situation na to..pero 5200 nga lang yung sa akin

hi! oo, nasubukan ko yung driver 173 kaya nga naghang yung screen ko after nung splash screen eh. may isa pang pagpipilian sa hardware software menu, 96 driver pero natatakot na akong maginstall kasi baka maulit uli yung nangyari. kung 96 kaya hindi kaya magkaproblema ulit? salamat :)

---

### Post by vivatsemiramis on 2009-05-12
> **loell said:**
> if the 96 driver series works well and with compiz then i think you should stay with it.

hi! actually i haven't tried it yet; haha i'm so frightened that it would give me the same experience as the 173 driver. any advise? should i proceed with the 96 driver? my gosh, why is it so hard to make the nvidia cards working in ubuntu :) thanks

---

### Post by _duncan_ on 2009-05-12
Anong monitor ang gamit mo?

May kaibigan kasi akong nvidia geforce 5500 din ang card. Luma na ang monitor niya. Nag-blank din ang screen pag-install ng restricted driver (173).

Sinubukan kong i-swap ang mas bagong monitor, gumana na. Tapos, binago ko ang /etc/X11/xorg.conf niya para i-set sa mas mababang resolution na kaya ng lumang monitor. Pagbalik ng lumang monitor, ayos na.

----------

Pahabol: Hindi lang pala nag-blank ang screen. Automatic na nag-off pag-boot ng Ubuntu. Senyales na hindi nakayanan ng lumang monitor ang default resolution na dulot ng restricted nvidia driver. Kaya ko naisipan ang solusyon na nabanggit ko sa taas.

---

### Post by ragadanga63 on 2009-05-12
Have you tried using Envy?

---

### Post by badrra on 2009-05-12
Unfortunately the 96 and the 176 drivers wont work on the FX5500 series. The best driver to use for that is the 100 series to run compiz and all that stuff. And unfortunately as well the 100 series did not work on ubuntu 8.10 as well. So I had to switch to Hardy. I am not sure if it will work on 9.04. I havent tried it yet. Ubuntu as well as Nvidia has discontinued support for the 100 series, hence not much can be read about it. But I am 100% sure that that is the driver you need. 

Depending on the monitor, you may have to configure the xorg.conf for a lower resolution like this:

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
	Modes	   "1024x768" "800x600" "640x480"	
    EndSubSection
EndSection

How to install 100 driver series:

1) Download 100 series drivers (from the NVIDIA website)
2) go to term window cntrl-alt-f2
3) turn off x Windows sudo /etx/init.d/gdm stop
4) chmod x+a NVIDIA-Linux-...100.....run
5) then run mo yung NVIDIA-Linux....
6) it will recompile the kernel for you 
7) When done it will ask you if you want to reconfigure xorg.conf
8) yes
9) sudo vi /etc/X11/xorg.conf
10) apply the above settings (hanapin mo na lang doon), save
11) start x windows sudo /etx/init.d/gdm start
12) Then the NVIDIA Splash screen starts. 

To test run glxgears on term. That sould work. Then you can install and run compiz fusion on it. 

Good luck

Edit: Forgot to tell you backup mo muna yung xorg.conf before you do this so kung merong mangyari restore mo lang yun.

---

### Post by loell on 2009-05-12
I'm leaning more on duncan's assessment , since I've also expirienced that same thing.

---

### Post by vivatsemiramis on 2009-05-12
hi thanks for all your reply. i'm using samsung syncmaster bh59-00362s. will try your suggestions. i tried using the 96 driver but it also produced the same results. i hope it will finally work. :) thanks all

---

### Post by vivatsemiramis on 2009-05-13
hi! i tried duncan's suggestion, i downloaded the 173 driver again but edited the xorg.conf file so that the resolution would be lower, 1064x768, although i think my monitor can support up to 1600x1200 resolution. however, it still failed. after the splash screen, it was a blank screen but i was able to revert back using the xfix in the recovery mode. i haven't tried badrra's suggestion though.

---

### Post by badrra on 2009-05-13
> **vivatsemiramis said:**
> hi! i tried duncan's suggestion, i downloaded the 173 driver again but edited the xorg.conf file so that the resolution would be lower, 1064x768, although i think my monitor can support up to 1600x1200 resolution. however, it still failed. after the splash screen, it was a blank screen but i was able to revert back using the xfix in the recovery mode. i haven't tried badrra's suggestion though.

I wish you the best of luck. And just to let you know, I am also using FX5500 series. It worked for me it might just work for you.

---

### Post by loell on 2009-05-13
> **vivatsemiramis said:**
> but i was able to revert back using the xfix in the recovery mode. i haven't tried badrra's suggestion though.

what was the resolution  that you are able to revert back?

---

### Post by vivatsemiramis on 2009-05-13
> **loell said:**
> what was the resolution  that you are able to revert back?

1064x768.

@badrra, are you using jaunty as well? i haven't tried your solution because you said in your post you had to go back to hardy to make fx5500 work. it's because i have 9.04 installed in my old desktop. regards

---

### Post by vivatsemiramis on 2009-05-13
> **badrra said:**
> I wish you the best of luck. And just to let you know, I am also using FX5500 series. It worked for me it might just work for you.

will try your solution this time (gosh i hate that making this graphic card work had consumed virtually my whole day today). this is my last option at least for now. if it still does not work, i'll leave it just like that for now. whew. thanks a lot by the way :)

---

### Post by vivatsemiramis on 2009-05-13
badrra, i tried your solution, but after i ran the NVIDIA file, upon installation i was prompted that the 100 series driver (is it the 180 driver, which i got by choosing the driver for nvidia 100 series in their website), did not support any installed gpu in my old desktop. it also said that the card installed in my system was supported by the 173 driver. i didn't know if it was only the wrong driver (i looked at all the drivers for the 100 series) but the 180 driver was the only driver that was available for download. you have any insights? could it be the wrong driver? thanks a lot.

---

### Post by loell on 2009-05-13
> **vivatsemiramis said:**
> 1064x768.



I think you should install **nvidia-settings** (sudo apt-get install nvidia-settings ) via synaptic or apt, from the working resolution which is 10624x768 , execute it (sudo nvidia-settings), then from there increase the resolution and lower down the refresh rate, you will [COLOR="Blue"]know [/COLOR] if the particular settings [COLOR="Blue"]will[/COLOR] work if you click "apply".  Then save it.

---

### Post by badrra on 2009-05-13
> **vivatsemiramis said:**
> badrra, i tried your solution, but after i ran the NVIDIA file, upon installation i was prompted that the 100 series driver (is it the 180 driver, which i got by choosing the driver for nvidia 100 series in their website), did not support any installed gpu in my old desktop. it also said that the card installed in my system was supported by the 173 driver. i didn't know if it was only the wrong driver (i looked at all the drivers for the 100 series) but the 180 driver was the only driver that was available for download. you have any insights? could it be the wrong driver? thanks a lot.


Sori naka tulog ako hehehe. Nope not the 180 series driver. 100 talaga sya. Ito yung link. I am not too sure if it is going to work on jaunty but it **did not** work on 8.10 so I had to revert back to hardy. 

Download: [http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

Then use the instrucitons above. It will also uninstall previously installed drivers.

---

### Post by badrra on 2009-05-13
Teka nga let me switch over to jaunty and i'll tell you what happened after that. 

OT: ang bilis ng Opera 10 acid3 test 100%. you  might want to try it out. :p

---

### Post by badrra on 2009-05-13
Nope, sorry it didnt work. the 100 driver is no longer supported. Let me try something else. Ill let you know later.

---

### Post by badrra on 2009-05-13
Ginamit ko yung 173 but before restarting the PC, inedit ko yung xorg.conf to look like this. 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 [COLOR="Sienna"] 	SubSection "Display"
    		Depth      24
    		Modes      "1024x768" "1280x600" "1024x600"  
  	EndSubSection[/COLOR]
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection

Yung naka red dinagdag ko after installing the recommended. Bagal lang sakin jaunty kasi legacy PC gamit ko e hehehh.

Gumana sya. Enabled ung glx. Nakapag glxgears ako

Suggestion ko babaan mo yung resoultion gamitin mo yun red na nilagay ko.

---

### Post by vivatsemiramis on 2009-05-13
> **badrra said:**
> Ginamit ko yung 173 but before restarting the PC, inedit ko yung xorg.conf to look like this. 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 [COLOR="Sienna"] 	SubSection "Display"
    		Depth      24
    		Modes      "1024x768" "1280x600" "1024x600"  
  	EndSubSection[/COLOR]
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection

Yung naka red dinagdag ko after installing the recommended. Bagal lang sakin jaunty kasi legacy PC gamit ko e hehehh.

Gumana sya. Enabled ung glx. Nakapag glxgears ako

Suggestion ko babaan mo yung resoultion gamitin mo yun red na nilagay ko.

alright. will try it later. thanks talaga. re: opera, haha i might try it out later as well.

@loell, should i try your suggestion after badrra's suggestion or before it?

regards. thanks all! :)

---

### Post by loell on 2009-05-13
> **vivatsemiramis said:**
> 
@loell, should i try your suggestion after badrra's suggestion or before it?


any of the two methods that will work for you is good. :)

---

### Post by vivatsemiramis on 2009-05-14
> **badrra said:**
> Ginamit ko yung 173 but before restarting the PC, inedit ko yung xorg.conf to look like this. 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
 [COLOR="Sienna"] 	SubSection "Display"
    		Depth      24
    		Modes      "1024x768" "1280x600" "1024x600"  
  	EndSubSection[/COLOR]
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"False"
EndSection

Yung naka red dinagdag ko after installing the recommended. Bagal lang sakin jaunty kasi legacy PC gamit ko e hehehh.

Gumana sya. Enabled ung glx. Nakapag glxgears ako

Suggestion ko babaan mo yung resoultion gamitin mo yun red na nilagay ko.

hi! oh my gosh, i don't know. i tried your suggestion but it still failed; same blank screen results. haha it's really funny, this fx5500 is causing so much trouble. anyway, maybe i'll just leave it like that for now. i don't know what's wrong with this system that i couldn't make it work. anyway thanks for everything :) regards

---

### Post by guitar_man on 2009-05-14
kakabalik ko lang sa bahay...hmm
nagsubok ka na ba ng ibang monitor???try using old monitor na support ang 800x600 or 1024x768...fx5500 medyo matanda na yung card...at mukhang maganda monitor...try lang naman..

---

### Post by badrra on 2009-05-14
> **vivatsemiramis said:**
> hi! oh my gosh, i don't know. i tried your suggestion but it still failed; same blank screen results. haha it's really funny, this fx5500 is causing so much trouble. anyway, maybe i'll just leave it like that for now. i don't know what's wrong with this system that i couldn't make it work. anyway thanks for everything :) regards

Hmmm nakaka intriga bakit kaya. Pwede mo ipost dito yun xorg.conf mo?

---

### Post by leipogs23 on 2009-05-15
Tried to search the net but all I've seen so far are people having problems with their NVIDIA. Ganun ba talaga to or sa lahat naman ng brands? Well I'll keep you posted when I find a new solution. Muka kasi di gumagana sayo ang mga standard solution...

---

### Post by guitar_man on 2009-05-15
ok naman sa akin....fx5500 sakin.

---

### Post by vivatsemiramis on 2009-05-15
> **badrra said:**
> Hmmm nakaka intriga bakit kaya. Pwede mo ipost dito yun xorg.conf mo?

yung xorg.conf ko kapareho lang ng ni-post mo, kaya in-add ko lang yung red, except dun sa last section na nvidia logo, true yung sa akin. pareho lahat, in-add ko yung sinabi mo, pero ayun hehe hindi sya gumana,..

---

### Post by vivatsemiramis on 2009-05-15
> **leipogs23 said:**
> Tried to search the net but all I've seen so far are people having problems with their NVIDIA. Ganun ba talaga to or sa lahat naman ng brands? Well I'll keep you posted when I find a new solution. Muka kasi di gumagana sayo ang mga standard solution...

thanks for that hehe, i am starting to think my nvidia card may just have to go to the waste bin as it is so useless, and my board has an on-board card.. tsk, what a waste of money hehe

---

### Post by badrra on 2009-05-15
> **vivatsemiramis said:**
> thanks for that hehe, i am starting to think my nvidia card may just have to go to the waste bin as it is so useless, and my board has an on-board card.. tsk, what a waste of money hehe


Nagkaron ba ng error message like "....revert to low resolution mode..." something like that? And is it asking you to re-configure?

---

### Post by vivatsemiramis on 2009-05-15
> **badrra said:**
> Nagkaron ba ng error message like "....revert to low resolution mode..." something like that? And is it asking you to re-configure?

none. after editing the xorg.conf file i saved it then rebooted. upon reboot, after splash screen, the usual blank screen welcomed me. then i got no choice but to restart the pc and switch to recovery mode, then xfix again. i tried not to uninstall the driver and reboot it again, but the same blank screen. so after switching to recovery mode yet again, i tried to remove the 173 driver. after that, everything went back to normal. to answer your question, no error or any message, just the blank screen. i think when i installed the 96 driver before i had that revert to low resolution mode thing, but not in 173 driver.

---

### Post by loell on 2009-05-15
when you have nvidia card and during installation, the default driver that it will be using is NV ( the opensource driver for nvidia cards )

so during the first install, does the resolution look ok?

---

### Post by vivatsemiramis on 2009-05-15
> **loell said:**
> when you have nvidia card and during installation, the default driver that it will be using is NV ( the opensource driver for nvidia cards )

so during the first install, does the resolution look ok?

resolution was at 1064x768; it was ok, but when i enabled the visual effects, it required the nvidia driver to be installed, so i had to use jockey after the first install.

---

### Post by loell on 2009-05-15
> **vivatsemiramis said:**
> resolution was at 1064x768; it was ok, but when i enabled the visual effects, it required the nvidia driver to be installed, so i had to use jockey after the first install.

i see, did you backup the xorg.conf? if not i think i still have one config lying around, probably i could give one.

what you might have done was, lower the resolution then, like 600x800 , so when the effects was enabled, i think the desktop would show. and  then would have done the nvidia-settings.

---

### Post by vivatsemiramis on 2009-05-15
> **loell said:**
> i see, did you backup the xorg.conf? if not i think i still have one config lying around, probably i could give one.

what you might have done was, lower the resolution then, like 600x800 , so when the effects was enabled, i think the desktop would show. and  then would have done the nvidia-settings.

yeah, i did backup the default xorg.conf. should i do that, lower the resolution? i tried changing the resolution according to badrra's suggestion, exactly how he did it and made it work in his pc. i'm still wondering why i couldn't make it work in mine... one suggestion was to change the monitor to an older model, but i'm still going to ask for some older model to do some experiments some time.

---

### Post by loell on 2009-05-15
> **vivatsemiramis said:**
> yeah, i did backup the default xorg.conf. should i do that, lower the resolution? 

yeah, it worth a shot. lower the resolution before enabling the restricted driver.

---

### Post by badrra on 2009-05-15
Check this one out it might resolve the issue: 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Samhain13 on 2009-05-17
Wouldn't it be easier to just use Hardy? Hehe. I have the same card, having no problems with the driver (whatever that was installed when I enabled Desktop Effects). Just saying. :)

---

### Post by dannybuntu on 2009-05-17
Word of advice. Just chill. Ganyan din ako dati. Pag may problem sugod agad. In the process I made many costly mistakes. Approach the problem well rested. Contemplate like a zen master. Assess the concern. Look at the solutions. Record your efforts. It will work out.

First off check launchpad for any related entries:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/115700](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/115700)
[https://answers.launchpad.net/ubuntu/+question/18636](https://answers.launchpad.net/ubuntu/+question/18636)

I have similar problems for FX5500 which I just bought 2 weeks ago for 900 pesos :)
The only difference is my screen isn't blank.

[http://dannybuntu.blogspot.com/2009/04/day-980-i-barely-survived-upgrade-to.html](http://dannybuntu.blogspot.com/2009/04/day-980-i-barely-survived-upgrade-to.html)

For now I am content without compiz - as long as I can play Tremulous. I am running my Pentium 3 650 mhz pc with 256 RAM on Ubuntu Jaunty triple boot with WinXp and Debian Lenny. 

Do not be pressured. Relax. It is what it is.

---

### Post by badrra on 2009-05-17
fx550 for 900? gosh where did you get it? I want to get one for my son's PC.

---

### Post by guitar_man on 2009-05-17
@dannybuntu 

oo nga boss dannybuntu san mo nabili yun???gusto ko bilan yung pentium II ko.:D

---

### Post by dannybuntu on 2009-05-22
Kung alam niyo po dito sa bandang sucat paranaque, yung dating rolls roy. Ngayon, ganun din ang pumalit na negosyo - second hand galing korea. sa sucat :)

---

