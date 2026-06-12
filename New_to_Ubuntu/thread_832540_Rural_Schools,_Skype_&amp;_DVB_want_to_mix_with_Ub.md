---
title: "Rural Schools, Skype &amp; DVB want to mix with Ubuntu"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by martindoom on 2008-06-17
Hello from the new guy.

I've just installed Ubuntu 8.04 on my daughters Acer aspire 5500Z in minutes and with total success but she doesn't use skype nor have a TV card. I didn't download the prog but got the disk sent out from Canonical/Ubuntu in France and everything works great.

I'm running a Compal HEL80C with XP home edition pre installed and really wanted Ubuntu for my work and not the daughter. I run 'Rural  School's Resource Support', an NGO out here in Estonia, and clearly Ubuntu, and or similar, is ideal for these cash strapped institutions. All the schools i work with have the same rig as mine as i managed to get a job lot from a kind hearted philanthropist. Clearly i need to now know this Ubuntu system inside out before i start installing to these rigs (it's up to the IT teachers after that)but i am having second thoughts about using Ubuntu for the following reasons:

1. Communication is paramount and all schools/students use 'Skype' (It is afterall an Estonian creation) and i noticed Ekriga (i think that's what linux Voip support software is called)does not support 'Skype' due to it using proprietary content.

2. All laptops go home with the students and it can be the only access they have to TV using the LifeView MVP/DVB-T 1.04 (build 1336) analogue/digital tv cards. They do need this for education.

All info i've found so far originated from here ===> [http://wiki.ubuntu.org.cn/UbuntuWiki:LaptopTestingTeam/CompalHEL80](http://wiki.ubuntu.org.cn/UbuntuWiki:LaptopTestingTeam/CompalHEL80)

Don't get me wrong. Estonia's a well advanced country but there is still poverty and educational 'black holes' geographically speaking.

Any help is well appreciated.

---

### Post by Sinkingships7 on 2008-06-17
Skype has a native Linux version: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

And you can use MythTV for your other problem.

EDIT: I should say, I've never used either software mentioned above. But I've heard great things about MythTV.

---

### Post by martindoom on 2008-06-17
> **Sinkingships7 said:**
> Skype has a native Linux version: [http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

And you can use MythTV for your other problem.

EDIT: I should say, I've never used either software mentioned above. But I've heard great things about MythTV.

Damn, that was quick lol. The skype link is just what i was looking for. I thought i must be making a mistake while searching. Re MythTV. I know you haven't used it but would i need to have the hardware altered or will the software (at least i think that's what mythtv is) work with the mini laptop tv cards that we already have. I know it's a specific question but i've been searching all night. If You don't know, any idea where i could start looking?

Many thanks Sinkingships7

---

### Post by Sinkingships7 on 2008-06-17
Here's a link that seems to list supported MythTV/Linux tuner cards. You can have a look at that and see if your card's supported. Remember, if there are several cards made by the same company as your card, then just because it's not listed, it doesn't mean it won't work.

[http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card)

EDIT: Yes, MythTV is software.

---

### Post by steve101101 on 2008-06-17
you can install skype the the symnaptic package manager .. the guide is here ... [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by steve101101 on 2008-06-17
it is always a better practice to install software through the package manager so that it is easier to update and uninstall if necessary.

---

### Post by ad_267 on 2008-06-17
This might help determine whether that device is supported: [http://www.linuxtv.org/wiki/index.php/Supported_Hardware](http://www.linuxtv.org/wiki/index.php/Supported_Hardware)

Do you have a lap top that you can install Ubuntu on and see if the tuner will work with MythTV?

This explains what MythTV is and how to set it up: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by martindoom on 2008-06-17
> **ad_267 said:**
> This might help determine whether that device is supported: [http://www.linuxtv.org/wiki/index.php/Supported_Hardware](http://www.linuxtv.org/wiki/index.php/Supported_Hardware)

Do you have a lap top that you can install Ubuntu on and see if the tuner will work with MythTV?

This explains what MythTV is and how to set it up: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

Spot on!

Card is there by name and pic and is supported. now i've just got to Format 162 laptops with ubuntu and get the them working with skype and TV....OH my God! What have i begun lol

[Edit] Forgot mine so that's 163 OMG!!!

---

### Post by ad_267 on 2008-06-17
I recommend just doing one first to make sure everything works properly, I'm sure it will but just to be sure.

If you're downloading and installing packages (eg skype and mythtv, and you might want to see what other educational software is available) you may want to set up one correctly with all the software you need and then use aptoncd (it's available from the repositories) to put all the packages you've downloaded onto a cd so you don't have to download them for each laptop.

Oh yeah and you may want to check out Edubuntu. It's ubuntu but specifically for schools. [http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by scotcella on 2008-06-17
Fantastic Thread...  

Im bookmarking this thread!!

Will refer this when the time comes to do this!!!

---

### Post by martindoom on 2008-06-18
> **ad_267 said:**
> I recommend just doing one first to make sure everything works properly, I'm sure it will but just to be sure.

If you're downloading and installing packages (eg skype and mythtv, and you might want to see what other educational software is available) you may want to set up one correctly with all the software you need and then use aptoncd (it's available from the repositories) to put all the packages you've downloaded onto a cd so you don't have to download them for each laptop.

Oh yeah and you may want to check out Edubuntu. It's ubuntu but specifically for schools. [http://www.edubuntu.org/](http://www.edubuntu.org/)

Thanks for all your help. Makes sense to do one first so i'll do my own with Ubuntu then (since i've had a look at edubuntu) it makes sense to follow your advice with edubuntu. A few brownie points in my cap from the board of directors courtesy of your shrewd thinking. I'll check back and let you all know how i get on:)

---

### Post by martindoom on 2008-06-18
Hello again!

Well so far it\s a big success story! Ubuntu 8.04 installed and working sweet. Skype also installed and working. About to attempt the mythtv step now so watch this space! Only small prob is my keyboard is all over the shot as i can\t seem to get any keyboard options that allow Ctrl+alt keys working which i need for @ (i copied and pasted the one you see here) and i can\t find an apostrophe for love nor money nor a question mark...ok, i guess that\s more than a small problem lol

---

### Post by ad_267 on 2008-06-18
You will need to go to System - Preferences - Keyboard. Then to the layout tab and to Layout Options and have a play around with some of those options to see if you can get your alt key doing what you want.

I think you need to go to "third level choosers" and select the key you want to use there.

---

### Post by martindoom on 2008-06-19
> **ad_267 said:**
> You will need to go to System - Preferences - Keyboard. Then to the layout tab and to Layout Options and have a play around with some of those options to see if you can get your alt key doing what you want.

I think you need to go to "third level choosers" and select the key you want to use there.

Yip1 you did it again:) I followed the instructions above and got the keyboard configured (more or less) with ctr/alt functioning fine and i have apostrophes,question marks and @ all working.So thanks again!!! 

I've not actually attempted the MythTv part yet as i'm stuck trying to get the integrated webcam working. I've found out the driver (possibly) that's needed is here ===>  [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/) but none there will load for me. I get "Error:Dependency is not satisfiable:Linux image generic." I then found this link but it's baffling for someone like me, in the early stages of learning Ubuntu ===>  [http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/](http://www.indragunawan.com/2008/04/microdia-webcam-ubuntu-710-gutsy/)

Any help on the webcan issue would be greatly appreciated as skype is a bit pointless without a webcam!

**[Edit]**Could aso use some help with installing moblock or is there something better? Also is transmission P2P anygood? I was thinking about using firestarter firewall and clamav too but i have, and the school's network will have a server based version of F-secure internet security. will this work with ubuntu? I know there are wide ranging and varied questions here so if i've overloaded this post i apologise and just ignore everything past the webcam request and i'll take it step-by-step in the furure. All the best!

---

### Post by JoshuaRL on 2008-06-19
Don't worry, this is all one related problem.  Ubuntu comes with a wonderful firewall, called iptables.  Firestarted is merely a GUI way to change firewall settings.  As far as clamav, it really isn't necessary.  It will only search for Windows viruses anyway, since there is no active Linux malware currently.

I would also suggest you use remastersys to make installing on the 163 computers easier.  It takes an image of the hard disk, and saves it on a DVD.  That way, you can make your own personal restore DVD.  You can also use it to install on identical computers extremely easy.

---

### Post by martindoom on 2008-06-19
> **JoshuaRL said:**
> Don't worry, this is all one related problem.  Ubuntu comes with a wonderful firewall, called iptables.  Firestarted is merely a GUI way to change firewall settings.  As far as clamav, it really isn't necessary.  It will only search for Windows viruses anyway, since there is no active Linux malware currently.

I would also suggest you use remastersys to make installing on the 163 computers easier.  It takes an image of the hard disk, and saves it on a DVD.  That way, you can make your own personal restore DVD.  You can also use it to install on identical computers extremely easy.

Ok. So i'm using Ubuntu 8.04 so is iptables all ready up and running by default or is there some activation required? Can you help with moblock installation or is that covered by iptables too. I'd really rather use uTorrent as opposed to transmission. I followed all the instructions to get it working on ubuntu and installed it but i don't get the option to use it when the download window pops up. I can see the utorrent icon in the toolbar and it's working fine (although i can't do the speed test as it requires shockwave and flash player which, although installed, don't seem to be working). Oh yeah and what do i do about the integrated webcam issue? All comps are Compal HEL80C notebooks. There's a link in one of my earlier posts in this thread showing a test done on this model with ubuntu and it says the webcam should work. I know i'm asking a lot of questions but it's a one man team here to get all this set up by September the 1st. Sometimes i think i'm on top of things and everythings going swimmingly, othertimes.....well that's just now when it's 2am and it seems like all i did today was find problems and solve nothing and praying for help on the ether lol[-o<

**[Edit]**Great time saving and catastrophe avoidance in your remastersys suggestion. Idea adopted and taken on board. Thanks for that!

---

### Post by Delever on 2008-06-19
Deluge bittorrent client is closer to uTorrent and can be installed from repositories.

---

### Post by ChompTheMan on 2008-06-19
> **martindoom said:**
> Sometimes i think i'm on top of things and everythings going swimmingly, othertimes.....well that's just now when it's 2am and it seems like all i did today was find problems and solve nothing and praying for help on the ether lol[-o<

I have days like this as well.  It gets easier the longer you persevere and the day comes when you start finding the solutions to your problems.  On days like that I feel on top of the world.  You are taking on a big project by yourself but you sound determined, keep it up!  You've got a big community willing to help you solve your problems :)

On the torrent client note, you may wish to check out Ktorrent.  I don't know if it's like Utorrent(I've never used it), but it's a sleek, fully featured bittorrent client and can automatically set up Peerguardian(but not Moblock).

---

### Post by martindoom on 2008-06-19
> **ChompTheMan said:**
> I have days like this as well.  It gets easier the longer you persevere and the day comes when you start finding the solutions to your problems.  On days like that I feel on top of the world.  You are taking on a big project by yourself but you sound determined, keep it up!  You've got a big community willing to help you solve your problems :)

On the torrent client note, you may wish to check out Ktorrent.  I don't know if it's like Utorrent(I've never used it), but it's a sleek, fully featured bittorrent client and can automatically set up Peerguardian(but not Moblock).

Lol...people out there do care. Aw shucks & thanks for the well needed confidence booster. I'm just dedicated to the kids really (kids i say? well, some are but IT classes are grades 4 through 12 and S/s can take home laptops from grade 9). I've been out here doing similar rural infrastruture work since '95 (By out here i mean Estonia, Belarus, Ukraine, Lithuania with 2 years helping the "hill tribes" in Chiangmai, Thailand). Quite some journey i can tell you! Brains too buzzing to continue trying to solve the webcam prob (19hrs searching and experimenting and still no further forward ](*,)) i'm going to take a break and check out your ktorrent idea. How do i delete uTorrent now though. Can't find it's nesting place in the system anywhere and does it matter that i activated 'wine' to get it working?

This is a dreamland of a forum. Helpful, friendly and supportive peeps that don't razz the mr. green newbie :mrgreen:

---

### Post by Delever on 2008-06-19
To uninstall wine program (uTorrent is windows program, installed with wine, so it is wine program now), Use Applications->Wine->Uninstall wine software.

And hello from Lithuania :)

---

### Post by martindoom on 2008-06-19
> **Delever said:**
> To uninstall wine program (uTorrent is windows program, installed with wine, so it is wine program now), Use Applications->Wine->Uninstall wine software.

And hello from Lithuania :)

Wow! Small world Happy Jannin'ios naktos i think? Do you remeber the Eurovision song contest entry for Lithuania (or Leedu as you're called up here) 'Cool guy with long hair' ? The band was 'Alien Run Amok' or something like that. Anyway, the lead singer (i call him Caesar but his real name is Romaldus or Romus) is coming up here for that special day...Janni Päev to spend it with me and my wonderful family! What a nutter lol

Thanks for the wine uninstall info. I found that, in my present mental state, i couldn't follow the instructions for Ktorrent successfully enough so i'll leave your teachings till i've cleared my mind of 'Penguins' lol Too much for 1 guy today:confused:

---

### Post by jre on 2008-06-20
You can find a MoBlock wiki on [https://help.ubuntu.com/community/MoBlock](https://help.ubuntu.com/community/MoBlock) if you want to install it. I don't know ktorrent and its IP-blocking plugin.

---

### Post by martindoom on 2008-06-22
Well hi again. I've hit a major problem that needs a remedy yesterday. I can't get on our internal website that we use for many things least of which is conferencing with the board of directors/trustees. We have no choice but to go with Ubuntu and Edubuntu due to cost restrictions (from what i've discovered so far about it's power and far reaching possibilities i'm more than satisfied with that decision). I've have been told to revert to Xp until i can prove that i know what i'm doing while using Ubuntu (i've clearly shown i don't by not being able to use our main comms/vid conferencing channel to update them on current goings on). 

I have no choice (other than losing my job), but to do what they have instructed ie the temporary reinstallation of XP. However, after installing the genuine XP disc amd selecting setup.exe i get a screen that has several options, the 2 most relevant are 'install windows xp' and 'check system compatability. the first option just stays on 'gathering info' and does nothing and the second gives me an error window. 

I' and my organisation are staying with ubuntu but i must keep them updated in the interim before full installation on all computers so, anyone pleeeaase help me to reinstal XP while i get this problem resolved.[-o<

**[Edit]**I have no doubt that there is a fix for this problem but i need to communicate with the trustees as and when they want and i fear i have damaged their trust in Ubuntu and me, not to mention a decision has been made for me to (as i said, temporarily) revert to XP until i can assure them i can get all the functionality of the computers and our communication working.

---

### Post by ad_267 on 2008-06-22
That's probably because the ext3 file system isn't recognised by windows. You can boot into the Ubuntu Live CD and select System - Administration - Partition Editor and delete the partitions set up for Ubuntu (should be an ext3 partition and a swap partition) so that the whole drive is unallocated space. I don't think you will need to reformat as ntfs as the Widows install should be able to do this once the other partitions are deleted.

It is also possible to set up a dual boot so that you can choose between Windows and Ubuntu when turning on your computer. Usually this is easiest by installing Windows first then Ubuntu second.

---

### Post by martindoom on 2008-06-22
Hiya ad_267. Thank god you and others are walking me through this and thanks for your patience and advice.

I can't seem to boot into live cd!!!? I've tried everything including F12 on startup but i just get my usual log-in screen up. I don't know why i didn't think to tell the trustees that i could load dual OS's but that is clearly the right path at this stage.

So...any advice on how to get live cd booted?

---

### Post by ad_267 on 2008-06-22
Did you install from the live cd initially? Usually there's a message saying press delete or F12 or something similar to enter the BIOS setup. Then you can change the BIOS boot order setting to make the CD drive a higher priority than the hard drive so that you can boot from the cd.

Edit: Most likely to be Escape, F1, F2, F12, Delete to enter BIOS setup.

---

### Post by martindoom on 2008-06-22
Yip. I installed ffrom a genuine (not downloaded) CD posted from Canonical,France. I hit F12 to enter BIOS and chose the cd/dvd boot option but still only arrive at my usual log-in screnn!!?? Clueles atm :-(

---

### Post by ad_267 on 2008-06-22
When you hit F12 do you get a boot menu or the BIOS setup? Some computers have F12 as a boot menu and another key such as F2 or delete to enter the BIOS where you can change the actual boot order.

This might help:[http://pcsupport.about.com/od/tipstricks/ht/bootcddvd.htm](http://pcsupport.about.com/od/tipstricks/ht/bootcddvd.htm)
[http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/](http://techpaul.wordpress.com/2007/08/03/how-to-boot-from-a-cd/)

---

### Post by doorknob60 on 2008-06-22
> **martindoom said:**
> 
I have no choice (other than losing my job), but to do what they have instructed ie the temporary reinstallation of XP. However, after installing the genuine XP disc amd selecting setup.exe i get a screen that has several options, the 2 most relevant are 'install windows xp' and 'check system compatability. the first option just stays on 'gathering info' and does nothing and the second gives me an error window. 


Did you double click those .exe's from inside Ubuntu?

---

### Post by martindoom on 2008-06-22
I ve got a phoenix systems screen that comes up with the options of F2 for bios and F12 for startup order and i\ve tried both to no avail. Im now back to my limited usage keyboard *having hit the install ubuntu option on reboot from the live cd *guess this won\t change mu system as it claims( but still can\t see partition editor from the system menu.
**Edit.** Oops! My bad. Was looking at pref menu not admin. Main partition deleted but /dev/sda - GParted using 5.79 GiB is locked so can\t delete it. Is this ok *question mark goes here)

---

### Post by ad_267 on 2008-06-22
The partition editor is on the live cd but not installed in Ubuntu by default. You could install it but it wouldn't be any use if you want to remove the partition Ubuntu is installed on.

---

### Post by martindoom on 2008-06-22
> **doorknob60 said:**
> Did you double click those .exe's from inside Ubuntu?

Yes i did. Is that yet another thing i\ve done wrong today?

---

### Post by martindoom on 2008-06-22
> **ad_267 said:**
> The partition editor is on the live cd but not installed in Ubuntu by default. You could install it but it wouldn't be any use if you want to remove the partition Ubuntu is installed on.

Did you see my edit? The one where i\ve got into the live CD screen and found the partition editor? I\ve deleted the main partition but still left with the dev sda gparted one. what should i do now?

---

### Post by ad_267 on 2008-06-22
OK I'm not quite sure what's going on. If you want to reinstall windows you need to boot from the Windows CD to reinstall. You can't run the windows installer from inside Ubuntu.

If you did do that and you got an error trying to install windows when booting from the cd then you should try booting from the ubuntu cd and select "try ubuntu without changing your computer" and then run the partition editor to delete the ubuntu partitions.

---

### Post by ad_267 on 2008-06-22
If there's a partition you can't delete it's probably because it's been mounted. Open up the file manager and go to computer and right click on the drives and select unmount volume if it is an option.

---

### Post by martindoom on 2008-06-22
> **ad_267 said:**
> OK I'm not quite sure what's going on. If you want to reinstall windows you need to boot from the Windows CD to reinstall. You can't run the windows installer from inside Ubuntu.

If you did do that and you got an error trying to install windows when booting from the cd then you should try booting from the ubuntu cd and select "try ubuntu without changing your computer" and then run the partition editor to delete the ubuntu partitions.


I\m panicking. Sorry.Gotta talk the the trustees this morning so have to have this solved by then. I\ll try the re boot from XP now. Hang on and wait for me to come back bro and cheers.

---

### Post by doorknob60 on 2008-06-23
> **martindoom said:**
> Yes i did. Is that yet another thing i\ve done wrong today?

That just tries to install Windows inside of Wine. That would be really sweet if it worked, but it doesn't. The proper way to install XP is to put the CD in the drive and boot from it (like the same way you booted from your Ubuntu CD). Unless you want to keep Ubuntu, the Windows installation should wipe your Ubuntu partition for you. If you wanna keep Ubuntu and dual boot, it's more complicated though. EDIT: Sorry if my reply is a little late...

---

### Post by martindoom on 2008-06-23
Big sigh! 

Couldn't get XP to connect to my speedtouch once i finally got it reinstalled so reverted back to Ubuntu and installed XP on one of the other laptops.

I think i just need to sit down for a while with something like an Ubuntu 8.04 manual/guidebook/tutorial and absorb the basics as i'm just too new to all of this. Can anyone recommend something downloadable?

**[Edit]** Here's a list of things i have left to understand and achieve:

1. Get my webcam working (integrated on a Compal HEL80c) I found this, [http://www.linux-projects.org/modules/news/](http://www.linux-projects.org/modules/news/) but none of the downloads seem to work (i get an error messeage mentioned in one of my posts in this thread), so i must need the kernel listed at the same link, i guess, but don't know where to put it once i've downloaded it as it tells me i need to choose an association/program to open it with (i have the same prob with Realplayer 11 for Linux.

2. Get the TV card working. MythTV says i need gxine but again this is getting too technical for my current ability, what with the additional instructions found here [http://www.mythtv.org/wiki/index.php/Video_capture_card](http://www.mythtv.org/wiki/index.php/Video_capture_card) for my lifeview flyTV hardware. Really need to immerse myself in the basics of the 'terminal' etc.

3. Get Skype working with video. I think Skype 2.0 for linux will do this but it's no use unless the webcam works first.

4. Hopefully get the Omnipass, fingerprint reader (integrated) working although this is hardly essential.

5. Hopefully get the media card reader (integrated) working but as above, this is hardly essential.

I really appreciate the support you've all given so far but untill i find somthing to read about all this, i fear i'm too green to handle this on my own and am out of my depth.

---

### Post by mrpeenut24 on 2008-07-23
I've also got a Compal HEL80 (velocity-micro l80x).  I got the fingerprint reader working by installing fprint-demo.  Also, you can use it to log in with libpam-fprint.  Here's the webpage for it: [http://www.reactivated.net/fprint/wiki/Main_Page](http://www.reactivated.net/fprint/wiki/Main_Page)

All of the packages should be in the repositories, although you may need to enable some extra ones.


I'm also trying to figure out how to get the webcam working.  Did you ever find out how?

---

