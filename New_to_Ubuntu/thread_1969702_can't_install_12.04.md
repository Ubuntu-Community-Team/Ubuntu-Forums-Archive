---
title: "can't install 12.04"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-04-30
I am finding it impossible to install 12.04 on a laptop. It has 1GB RAM. Here is what I have tried, most several attempts. 
It worked perfectly with 11.10.
   I burned both USBs and DVDs of Ubuntu,Xubuntu, Lubuntu.None would go beyond the splash screen. I tried upgrade and clean install. I reformatted all the partitions and tried all again. 
   I hit F6 at boot to disable all the nomodset etc options.
   I am able to install Knoppix,Puppy, and 11.10 gnome Shell Remix but can't find a way to upgrade that to 12.04. 
   I installed Ubuntu desktop and Lubuntu and Xubuntu from synaptic in Gnome Shell Remix 11.10 but still can't upgrade.
   I suspect it may be the wireless driver as I once saw an error about b43 missing-yet the wireless worked perfectly on previous 11.10 and the currently installed Gnome Shell Remix 11.10.I can try to install it from command line but I don't know how too access the command line from a live CD that freezes at the splash screen. 
   The only reason I installed Gnome Shell Remix 11.10 was of the tons of live CDs I have it was the only buntu flavor I could get to actually install.The error is always the same a total freeze at the Ubuntu splash screen with the dots underneath.And I have waited even hours just to be sure it wouldn't eventually go.  Again it worked great in 11.10. But I couldn't get upgrade from update manager, alt+f2, or command line. And it has all current updates.I just want to get the LTS on it. I even went and tried 10.04 in the hopes of upgrading from that to 12.04 but same freeze issue. The gnome shell remix simply asks if I want to set up wireless at install and I said no and then installed firmware from synaptic and wireless works fine. I have been at this all weekend and am pretty frustrated.

I tried it again and after checking option 6-nomodeset in the F6 at install I get this error about the firmware needed.  ":b43/ucods5.fw not found" go to [http://wirelesss.kernel.org/users/Drivers/b43](http://wirelesss.kernel.org/users/Drivers/b43) etc.The trouble is the firmware is installed but when a live CD is used how can I have it see the installed firmware? I didn't think I can get something installed before the live CD.Also when I go to that page it says page doesn't exist yet. But the wireless works fine on 11.10.I can try to install the firmware from a command prompt but I haven't found a way to access a command prompt since it freezes at the splash screen. I can access the F options but I don't see any that lead to a command prompt.The only other thing I can think of is some combination of options off for example aspci and nomodeset, etc. This is beyond me though.

---

### Post by xedi on 2012-04-30
Wow, you seem to have really tried "everything" so I'm probably not of much help, but I'm curious, why exactly does an upgrade from 11.10 to 12.04 not work?

Does the update manager never asks you to upgrade or does something go wrong during the actual upgrade process?

---

### Post by Rex Bouwense on 2012-04-30
I just installed Lubuntu 12.04 this morning on an old Dell Inspiron with only 512 RAM.  I too had the firmware missing problem, but I had it before so I know the answer.  See 
[http://ubuntuforums.org/showthread.php?t=1869293](http://ubuntuforums.org/showthread.php?t=1869293)
Not exactly the same problem but the solution should work for you as well (thanks to garvinrick4 who provided me with the answer)

---

### Post by audiomick on 2012-04-30
Any chance of connecting with a cable for the upgrade? I'd be a bit nervous about doing something  as fundamental as a system upgrade via wireless. It is not reliable enough for me, even when it is working.

A couple of things, though. I believe that you can install drivers when you boot into the live environment. If your wireless doesn't want to play in 12.04, though, then you wont be able to do that either. Back to a cable...

I think I have seen a number of posts recently referring to the b43 drivers. I don't really know, but I have a feeling that there might be a few issues with them at the moment. 

All in all, I would really try doing the upgrade with a cable, then address the wireless issue once the OS is on the machine.

---

### Post by hackerseraph on 2012-04-30
I would definitely try temporarily removing the wireless card, and using the ethernet to install (?) that way any blacklisted drivers do not impair you.

---

### Post by cmcanulty on 2012-04-30
I am connected with a cable and can easily get wireless working if I could install. As my post said. Every buntu flavor freezes at the splash screen I never get a chance to install. No one seems to get the main issue that I can't get into the live environment.I get the Ubuntu screen then select to install or live then the Ubuntu with the dots and never get any further.I know the wireless works fine on this laptop in 11.10 and just needs firmware butI can't install firmware if I can't get to a live environment. I think I have explained it as carefully as I can. I CANNOT get to a live environment it freezes at the splash screen.I have tried the upgrade option and the command line option. None will upgrade.Now I have 2 laptops this is occuring on. Is there a way to run a sudo command to install firmware (I know the command) or to get a terminaal prompt before I get into the live setup. The firmware was on the machine in 11.10 and worked fine.The link to the other thread is helpful but until I can get a prompt to install I can't do anything

---

### Post by anewguy on 2012-04-30
I wouldn't think that firmware missing for a wireless adapter would stop you from booting - it should just disable the wireless.  I would think it should be something else causing it not to boot, but not positive.  I believe I've read your posts correctly, but I just want to be sure:  using the LiveCD, you have added nomodeset but it still didn't boot the LiveCD?  I know there is another option, something like i915modeset=false or some such thing (it's been a while since I had to use that).  Again, maybe you already tried that as well, but I thought I'd ask.

Also, did you do your download while it was still beta (I did and I've had a TON of updates starting on the day it was released)?

Dave ;)

---

### Post by williejones on 2012-04-30
> **cmcanulty said:**
> I suspect it may be the wireless driver as I once saw an error about b43 missing-yet the wireless worked perfectly on previous 11.10 and the currently installed Gnome Shell Remix 11.10.I can try to install it from command line but I don't know how too access the command line from a live CD that freezes at the splash screen. 
  

This really has nothing to do with installing.  You really need to boot the live CD to "try Ubuntu".  It may have to take the F6, nomodset to boot.  If you can boot to a live CD desktop, you can select the install from the desktop.  Do not allow updates while installing.
You can then use a wired connection to load your wireless drivers and update.

---

### Post by arpanaut on 2012-04-30
Hey cmcanulty.

I can't find the bug right now but the jist of the work around was...

when the first splash screen shows with the keyboard and the man pops, hit any key > enter for english>

hit f6, don't select anything, then esc > at the end of the Boot options bla bla--

add (just start typing)  b43.blacklist =  yes  >then hit enter.

This should allow you to finish install and upon reboot you will be able to add the drivers you need.
I'm not sure if you have to add the same boot parameters on first boot or not but this should get you going.

---

### Post by anewguy on 2012-05-01
> **williejones said:**
> This really has nothing to do with installing.  You really need to boot the live CD to "try Ubuntu".  It may have to take the F6, nomodset to boot.  If you can boot to a live CD desktop, you can select the install from the desktop.  Do not allow updates while installing.
You can then use a wired connection to load your wireless drivers and update.

Read the last paragraph of his opening post - it sounds to me like he has already tried this option.  I asked in my post because I just wanted to verify that.

---

### Post by cmcanulty on 2012-05-01
yes I have tried all except the blacklist idea. Please stop recommending the try ubuntu if I could do that I would I CAN'T get to the try or install i got something installed last night using 
```
do-release-upgrade -d
``` 
but the other menu is missing so I can't access hardly any system tools or the main menu also synaptic doesn't show anywhere even though I installed it from the software center.I am in classic now but a sort of weird screwed up classic
No I didn't download the beta and I tried all the options please read post #1 as that explains. I can't seem to make it clear that it freezes BEFORE I can get to either a try or install. All I can get is the f options none of which help I tried them all but not all 7x7 combinations of two or more at once.

---

### Post by thatguruguy on 2012-05-01
> **cmcanulty said:**
> yes I have tried all except the blacklist idea. Please stop recommending the try ubuntu if I could do that I would I CAN'T get to the try or install i got something installed last night using 
```
do-release-upgrade -d
```but the other menu is missing so I can't access hardly any system tools or the main menu also synaptic doesn't show anywhere even though I installed it from the software center.I am in classic now but a sort of weird screwed up classic
No I didn't download the beta and I tried all the options please read post #1 as that explains. I can't seem to make it clear that it freezes BEFORE I can get to either a try or install. All I can get is the f options none of which help I tried them all but not all 7x7 combinations of two or more at once.

Out of curiosity, why are you using the "-d" flag?  Are you trying to install 12.10?  The correct command would be:
```
do-release-upgrade
```
... without the "-d".

---

### Post by cmcanulty on 2012-05-01
OK thanks I saw the -d part on several help forums

---

### Post by candtalan on 2012-05-01
I had a similar prob on an inspiron 1300 and the blacklist b43 whatever worked immediately. Once I had got it installed, re booting needed a blacklist again.....
 but once running it is easy to get b43 firmware  via cable  from the ubuntu software centre.

here is my old thread
[http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

When booting from live cd use F6 to get the boot string and add the blacklist string with a space at each end
good luck

---

### Post by cmcanulty on 2012-05-01
I got it to accept that typing you told me. Then it goes to the try ubuntu and actually opens the unity desktop but when I click the install option the hour thing goes for a few seconds then stops same if I right click it and try open. I am going to reboot and see if I can be fast enough to get the install option instead of try ubuntu. I am also trying to install the firmware from the software center as it will let me do that.But then to I have to unblacklist it? I don't know how to do that.Then I tried to install synaptic so I could install the other b43 file that laptop needs but it doesn't seem to let me install synaptic even though I enabled the universe source.I am working on it though and this is as further than I've gotten before. Another laptop I have has the same issue so I think this is definitely something Ubuntu needs to make easier.This is what turns people off to Linux not fancy doodads missing.
The last try I got led to a bud report-
ubiquity crashed with DebconfError in command (): (10,"console-setup/codeset doesn't exist")

---

### Post by cmcanulty on 2012-05-01
Well maybe semi success. I am currently installing Xubuntu after the blacklist deal. Can I backdoor into Ubuntu classic from Xubuntu? Unity seems to be the bugaboo which I don't want anyway. I had tried Xubuntu and Lubuntu earlier but without the blacklist typing in.Of course it isn't done yet but it sure looks promising.
I got it installed but won't boot. I tried  esc and f6 at boot but didn't do anything.

---

### Post by candtalan on 2012-05-01
> **cmcanulty said:**
> Well maybe semi success. I am currently installing Xubuntu after the blacklist deal. Can I backdoor into Ubuntu classic from Xubuntu? Unity seems to be the bugaboo which I don't want anyway. I had tried Xubuntu and Lubuntu earlier but without the blacklist typing in.Of course it isn't done yet but it sure looks promising.

Blacklist prevents b43 being found missing and stoppping the show. After (xubuntu, ubuntu  whatever) install, b43 is still missing so initially  blacklist is still needed, but once installed and running a desktop, early install the b43 firmware, when that is done, the temporaray blacklist will go when reboot, and a reboot will pick up the b43 firmware you just installed.

When xubu ntu is installed and running,  you can then instal the package, say, 
ubuntu-desktop
get this from ubuntu software centre or apt-get or synaptic. Then when installed all packages, choose which session, at login (submenu) also Lubuntu-desktop (my favourite).

the multiple choice of sessions will occasionally add extra items in menus, eg two calculators, whatever, bt will be convenient backdoor.

---

### Post by cmcanulty on 2012-05-01
Can you explain how to do the blacklist deal at first boot after install, thanks. I am afraid the Ubuntu desktop will still fail though as even when I got into a live session it wouldn't install.I think xubuntu is probably better anyway but I am used to classic and like it a lot.I have to keep real up on Ubuntu as I have it installed on 10 laptops at our library.
I found I could hit c at boot then typed the blacklist deal and then esc but it is still hanging at the splash screen. I really thought I had it solved this go around. ******
 I also tried this with no result

Blacklisting kernel modules

Sometimes it may be necessary to blacklist a module to prevent it from being loaded automatically by the kernel and udev. One reason could be that a particular module causes problems with your hardware. The kernel also sometimes lists two different drivers for the same device. This can cause the device to not work correctly if the drivers conflict or if the wrong driver is loaded first.

You can blacklist a module using the following syntax: module_name.blacklist=yes. This will cause the module to be blacklisted in /etc/modprobe.d/blacklist.local both during the installation and for the installed system.
I also tried this fix 
[http://ubuntuincident.wordpress.com/tag/boot-stops/](http://ubuntuincident.wordpress.com/tag/boot-stops/)
by booting into the gnome shell 11.10 that boots no problem, then mounted sda1 but then couldn't find how to navigate to the correct file to edit. Gparted showed sda1 as mounted but it didn't show up when I did gksudo nautilus
Now I am POed 4 days of this to no avail. LTS is supposed to mean something not new problems that didn't exist before

---

### Post by candtalan on 2012-05-02
> **cmcanulty said:**
> Can you explain how to do the blacklist deal at first boot after install, thanks. I am afraid the Ubuntu desktop will still fail though as even when I got into a live session it wouldn't install.I think xubuntu is probably better anyway but I am used to classic and like it a lot.I have to keep real up on Ubuntu as I have it installed on 10 laptops at our library.
I found I could hit c at boot then typed the blacklist deal 

sorry to hear you are still getting problems however - you need to hit e (not c) to put the blacklist string into the boot string, the e will allow you to 'edit' the existing string.

So, after install, and reboot, when you see the grub boot menu list of choices and a timer counting down  ready to start, then at that stage press 
e
this then gives a screen containing only about 10 lines of text. 
Near the bottom, the line beginning
linux /boot/vmlinuz-..............
and also containing 
ro quiet splash ......

this is the line to edit for the blacklist: something like
 ..... ro b43.blacklist=yes quiet splash ......
note there are no spaces either side of the = sign I believe.
hth

---

### Post by cmcanulty on 2012-05-02
I got Xubuntu to boot by using a slightly different command I found here
[http://ubuntuforums.org/showthread.php?t=1249157]("http://ubuntuforums.org/showthread.php?t=1249157")
so "b43.blacklist=true"
Now I am installing the Ubuntu desktop package. Then I hope to get back to classic. I also installed the b43 packages so should I delete the blacklist command? I don't want to risk getting it unbootable again. Thank you again

---

### Post by cmcanulty on 2012-05-02
I am in classic and have the wireless working. The key was using xubuntu USB then at splash screen entering
"b43.blacklist=true"
then from the try Xubuntu option.Then install firmware-b43-instasller and b43-fwcutter pkgs. Then install Xubuntu. Then I installed Nautilus (not in Xubuntu ) and mounted sda1 then did sudo nautilus and went to /etc/modbrobe.d/blacklist.conf of sda1 and deleted the blacklist b43 line.Then I installed gnome fallback. What a difficult and complicated way to get ubuntu! Most newbies would give up and go back to WIN. This,b43 is a real common wireless too. I hope they patch this soon. Now I have another 2 laptops to do and hope I can get them to work. Thanks everyone who helped!

---

### Post by candtalan on 2012-05-02
> **cmcanulty said:**
> I got Xubuntu to boot by using a slightly different command I found here
[http://ubuntuforums.org/showthread.php?t=1249157]("http://ubuntuforums.org/showthread.php?t=1249157")
so "b43.blacklist=true"
Now I am installing the Ubuntu desktop package. Then I hope to get back to classic. I also installed the b43 packages so should I delete the blacklist command? I don't want to risk getting it unbootable again. Thank you again

I found that after the  b43 firmware was installed, the machine booted normally after that. If you do somehow get  a further problem, just  do a temporary blacklist an dreinstal th eb43 firmware, but that is pretty unlikely I would think.
after installing the ubuntu-desktop pachage,  before reboot (but presumably in ubuntu after a simple re login to a ubuntu session) also install 'myunity' (good for a few tweaks) and I also installed AWN (avant window navigator) I found by chance that this seemed to also install ubuntu classic session :-) I did start awn but I dont think that was necessary for the classic session install. I am not sure though, that awn itself is very stable yet in unity.

---

### Post by cmcanulty on 2012-05-03
thanks, one other question. now that I have Ubuntu can I delete the original xubuntu I installed from or would that cause a potential boot problem?

---

### Post by candtalan on 2012-05-04
> **cmcanulty said:**
> thanks, one other question. now that I have Ubuntu can I delete the original xubuntu I installed from or would that cause a potential boot problem?

As I understamd it you installed Xubuntu, then ubuntu-desktop into it, giving you the choices to log in to either a xubuntu session or an ubuntu ordinary session (?)
If this is the situation then you can remove xubuntu-desktop and you will be left with  just ubuntu ok. The booting up process which seems to want to find b43 will not be affected anyway because it runs before the login or before the desktop starts to run - that is my guess anyway, so I would be ok with removing the xubuntu-desktop packages. And anyway, you have at this stage, already got the b43 firmware in place. One thing I found (because I use multiple -desktops like this on occasions) is that just removing say xubuntu-desktop package does not actually seem to remove all of the packages it installed!  I saw in a psychocats site (a while ago, something along these lines - [http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu) ) a list of items that can be removed to help 'clean up' in such situation, if it makes any difference.
Although you have had a lot of difficulty getting to this stage :-( it would be very easy to - if you wanted to (now you are an expert at this!)  
 - reinstall ubuntu from cold using the blacklist text at install time and then 
 - (you do not need the cd again) use the blacklist text at first boot, by catching the grub menu and editing it for blacklist
 - then immediately install b43 firmware from ubuntu software centre
 - then when you subsequently re boot, it will work normally

This would be (almost) a normal ubuntu install and you end up with a normal ubuntu. This is something I would tend to do for myself  because it would irritate me that I had extra packages even though they might be irrelavant! 
hth

---

### Post by cmcanulty on 2012-05-04
This seems like a major 12.04 bug. Of the 10 various laptops I have tried so far, 3 would not install any buntu flavor from DVD or USB. And 2 would not even with the blacklist tweak. Yet knoppix, bodhi, puppy, and gnome shell remix 11.10 install fine. I have one that I still have only got the remix on and nothing I try will upgrade it to 12.04 even though I have put both xubuntu and ubuntu desktops on it. I have tried the blacklist thing, command line, alt F2, and the live USB or DVD won't even open on it. I am about to give up on that one.Isn't b43 one of the most common wireless? Is there anything else I can do to get it to 12.04, remembering that the live try or ionstall option will not go past the splash screen even with blacklist.b43=yes or =true??

---

### Post by GreenWhite on 2012-05-04
I had to use the alternate-CD install. You can try that here.

  [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)



  Good luck.

---

### Post by candtalan on 2012-05-05
> **cmcanulty said:**
> This seems like a major 12.04 bug. Of the 10 various laptops I have tried so far, 3 would not install any buntu flavor from DVD or USB. And 2 would not even with the blacklist tweak. Yet knoppix, bodhi, puppy, and gnome shell remix 11.10 install fine. I have one that I still have only got the remix on and nothing I try will upgrade it to 12.04 even though I have put both xubuntu and ubuntu desktops on it. I have tried the blacklist thing, command line, alt F2, and the live USB or DVD won't even open on it. I am about to give up on that one.Isn't b43 one of the most common wireless? Is there anything else I can do to get it to 12.04, remembering that the live try or ionstall option will not go past the splash screen even with blacklist.b43=yes or =true??

Yes - without a doubt try the nomodeset thing!
From the cd boot menu use F6 either to choose nomodeset, or use a related command in the boot string. With an installed version (first reboot) it is (I think, needs to be confirmed) necesary to edit the /etc/default/grub file and then do sudo update-grub

good luck.

If you have any energy or strength left yet
( :-( ) do consier to file relavlent bugs because the devs do not usually read these  columns, it is bugs they see?
With the installer I *think* the command is 
ubuntu-bug ubiquity

---

### Post by cmcanulty on 2012-05-05
as I said in post #1 I did that and all the other options already nothing works

---

