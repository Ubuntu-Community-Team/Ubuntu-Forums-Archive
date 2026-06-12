---
title: "Tips N Tricks: GyachI-Sidetrack (yahoo messenger , webcam , voice chat)"
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by loell on 2007-05-02
update to a **newer thread** [http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")


[gyachi 1.1.31 for hardy heron]("http://www.mediafire.com/download.php?nlrmdlub4tv") now share your photos and view the photos of your friends and love ones :)

[gyachi 1.1.31 for gutsy]("http://www.mediafire.com/download.php?izgy1gktmxf")





Howto for V4l2 webcams by [kung fu ubuntu]("http://ubuntuforums.org/member.php?u=294691")

> **kung fu buntu said:**
> **UVC V4L2 webcam working!**
My original post is at [https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966](https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966)



I was able to get my Logitech Quickcam Fusion working with Gyachi 1.1.27 on my amd64 system. 
NOTE: for amd64 you need vloopback-1.1.2. 
I am yet to webcam chat with someone, but I can configure the webcam with no problems. The image quality is superb. 
 
I have built GyachI, on a chroot'ed system, using this config: 
./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --enable-plugin_photosharing --disable-plugin_xmms 
 
 
HOW TO: 
- Get vloopback and flashcam from [http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html](http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html) 
Build it and have it working on your system.
NOTE: it's mandatory to have the kernel module; not the flash application.
 
- build the application in the tarball at [http://ubuntuforums.org/attachment.php?attachmentid=64218&d=1206784138]("http://ubuntuforums.org/attachment.php?attachmentid=64218&d=1206784138")
 
- check the "embedded readme" in the source file

---

### Post by loell on 2007-05-04
:popcorn:  feedback is always welcome

---

### Post by kaede on 2007-05-05
can u manage to work out with file transfer to yahoo with gyachi ?

---

### Post by loell on 2007-05-05
do you mean when it freezes during the transfer?

---

### Post by mrgnash on 2007-05-05
:popcorn: Nicely done. Definitely some welcome improvements over 1.05 -- thanks!!

---

### Post by Soarer on 2007-05-05
I'd like to try it, but so far I have not been able to see the download files on the wiki.

---

### Post by loell on 2007-05-05
i'm glad you've come to apreciate it, :) thank you :)

---

### Post by loell on 2007-05-05
> **Soarer said:**
> I'd like to try it, but so far I have not been able to see the download files on the wiki.

i've added another link :) you can download from the first link its from yourfilelink.com

---

### Post by kaede on 2007-05-05
> **loell said:**
> do you mean when it freezes during the transfer?
not freezing. i mean. i even can't work it out transfering file with my friend who using yahoo messsenger. :D

---

### Post by loell on 2007-05-05
> **kaede said:**
> not freezing. i mean. i even can't work it out transfering file with my friend who using yahoo messsenger. :D

really? hmm, nobody reported that issue to gyachi's site and forum , kinda strange...

is it both recieving and sending files, or which one?

---

### Post by Soarer on 2007-05-05
Thanks - I've downloaded & installed.

Now, how do I launch it please? I only have GyachE on my menu, and gyachi-sidetrack in a terminal does nothing.

Thanks

---

### Post by loell on 2007-05-05
> **Soarer said:**
> Thanks - I've downloaded & installed.

Now, how do I launch it please? I only have GyachE on my menu, and gyachi-sidetrack in a terminal does nothing.

Thanks

just type

```
gyachi
```

---

### Post by Soarer on 2007-05-05
I was looking for something more complicated :)

Now that I have quit the GyachE that was also running (and therefore causing disconnections) it seems to run fine. I'll try it out - thanks.

---

### Post by gebeleizis on 2007-05-06
The file transfer has some quirks. 
If it doesn't work you could choose another File Server in Options tab. And change this everytime it doesn't work.
Stuff from YM that I want to see here.
-possibility to send multiple files.
-possibility to send file >250 kB.
-drag'n'drop.
- italic font for "permanently offline" option.

This is a nice piece of software. Thank u for it.

---

### Post by loell on 2007-05-06
thanks for the pointers on file transfer :)
i've reported the filetransfer problem already, and other uesrs confirm it too. its just unfortunate that the official devs 
were only notified lately.

i'll review review these suggestions, whenever i'll resume improving the gyachi again.
and perhaps implement the easier ones :)

---

### Post by taladan on 2007-05-18
Any chance for a 64 bit version of this?

I'm finding that I'm coming to regret installing the 64 bit version because every 32 bit version of a program I want to run, the system won't, no matter what workaround I try.

---

### Post by loell on 2007-05-18
there was a user who compiled  and package gyachi in 64 bit by striping out the voice chat function, i don't know if he still an ubuntu user.

i haven't seen his handle in the forum for quite a while now. :(

---

### Post by mrojas73 on 2007-05-21
I will testing it tomorrow, I am very excited about the new version.

Thank you.

---

### Post by jello_hosaka on 2007-05-27
hey loell! kabayan! i installed sidetrack on ubuntu feisty, there weren't any problems while installing but i can't seem to find the link to launch it... forgive me for i am a newbie...

---

### Post by loell on 2007-05-27
yeah, kabayan :) , try restarting, it will then appear in the applications menu  --> Internet --> gyache improved.

you can launch it in the command line by invoking ```
gyachi
```

---

### Post by paguilera on 2007-06-07
Hi.

Any chance of a version for Edgy users?

---

### Post by loell on 2007-06-07
hello, i could not make a deb package for edgy , as i have already migrated to fiesty , but if you already know how to compile and willing to hunt the development files in order to compile, i'd post the link for the source code.

---

### Post by imon9 on 2007-06-07
hello...

it seems like gYachi-sidetrack is really full of good features, but funnily, once i successfully log-into it. I get a system message, and the next thing i know, i am log-out again.

i am sure my log-in is successful because all my friendlist is visible.

i wonder if the problem is due to me having some contacts from WLM8 (windows live messngeer)

please advice

---

### Post by loell on 2007-06-07
are there any other clients , like (gaim/pdgin , kopete) thats currently running?

---

### Post by imon9 on 2007-06-07
no, there is not other client running, except for emesene, which is a MSN clone (can be found a [www.emesene.org](www.emesene.org))..

of course, at the moment i have pidgin install, but not running, does that matters?

and i got this funny message from systemadmin:

>   * Logging PM to file : '/home/user/.yahoorc/gyach/log//2007-06-07.141405.txt' *
SystemAdmin:   [System Message]

---

### Post by imon9 on 2007-06-07
also, i dont really understand gyachi interface... why cant it be like the normal IM GUI? why we need to log into a chatroom? i hardly use the chat room in yahoo... of course i'm not against the chat room feature, but isn't chatroom something we use only when we initiate group chat?

futher more, such gui made gyachi takes up at least 2/3 or my screen area, isnt it a bit too much for a IM program?

no offence though, i just don't get it...

please advice on the log-in error.

---

### Post by loell on 2007-06-07
> **imon9 said:**
> no, there is not other client running, except for emesene, which is a MSN clone (can be found a [www.emesene.org](www.emesene.org))..

of course, at the moment i have pidgin install, but not running, does that matters?

and i got this funny message from systemadmin:

yes, it matters at times, when you log in to gyachi , then you run pidgin with the same yahoo account, it will log you out in gyachi to log in to pidgin.

i haven't  encounter a systemadmin message yet to this day , kinda strange, just taking a wild guess, did you define any other user account in your system?

---

### Post by loell on 2007-06-07
> **imon9 said:**
> also, i dont really understand gyachi interface... why cant it be like the normal IM GUI? why we need to log into a chatroom? i hardly use the chat room in yahoo... of course i'm not against the chat room feature, but isn't chatroom something we use only when we initiate group chat?

futher more, such gui made gyachi takes up at least 2/3 or my screen area, isnt it a bit too much for a IM program?

no offence though, i just don't get it...

please advice on the log-in error.

you can check the no chat room check box in the login window, and it won't automatically join you into chat room,   

about the gui layout, well, its been like that for like half a decade now, over the years the userbase has come to accept it , you can compare  gyachi's gui from [http://gyachi.sourceforge.net](http://gyachi.sourceforge.net) and the gui of gyachi-sidetrack.

heheh, actually, it took me months to update the icons and a bit of layout change in the PM window.  ;)

---

### Post by imon9 on 2007-06-07
ok... first of all..just to clear things up a bit. I consider myself a above average computer user... and i already rull out things like "double sign-in" in different client...

btw, i not only experience this in Gyachi-sidetrack, same thing happen with gyache-improved...

so my only deduction is that my yahoo account having "MSN" contacts... perhaps that is the cause.. have u added MSN contacts to your yahoo user-list ever?

this is because yahoo 8 support cross-contacts with Windows Live Messenger (which is not supported by GAIM, Pidgin, kopete).. while Pidgin will still give an error everytime i run it, but it kept me log-in, but gyachi bounce me out... kopete on the other hand did not give error nor bounce me out.

if you dual boot your PC, perhaps u can fire-up your updated, original yahoo client and add a MSN contacts and try log-in again in gyachi... maybe the same problem will occur to u.. 

though, i'm not sure if you can removed the contacts or not, so experiment at your own risk for experimenting sake ;D

cheer anyway for replying my on very short notice... about the GUI, i kindda understand it has always been like this... i just though maybe someone with the skill will do some rewritting :D obviously, i'm thinking too much again

---

### Post by imon9 on 2007-06-07
PROBLEM SOLVED

i removed a contact named "sysmtemadmin" which appear to be a spam which i added when i first used Gyachi when i logged into a public chatroom... 

i am glad the problem is solve and the icons of gyachi is now much more nicer :) thanks for the effort

---

### Post by djchandler on 2007-06-07
> **taladan said:**
> Any chance for a 64 bit version of this?

I'm finding that I'm coming to regret installing the 64 bit version because every 32 bit version of a program I want to run, the system won't, no matter what workaround I try.

If there's any unused space on your hard disk, even though it is allocated for the 64-bit, I think the 32-bit installer will ask if you want to use part of it for the 32-bit version. Grub will give another option at boot of what OS to run if you don't want to wipe out the 64-bit install. BTW, as long as the disk is populated in any way, the 32-bit installer balks even when you tell it to use the whole device. I had to wipe a hdd first with dban when I wanted to install over something else. The Ubuntu installer respects any and all files systems already on the hdd.

---

### Post by loell on 2007-06-07
> **imon9 said:**
> PROBLEM SOLVED

i removed a contact named "sysmtemadmin" which appear to be a spam which i added when i first used Gyachi when i logged into a public chatroom... 

i am glad the problem is solve and the icons of gyachi is now much more nicer :) thanks for the effort

oh thanks for shedding light to this problem, others might experience this too ,
 you can also go to setup --> protection tab --> check the "Do not allow any to add me .." check box , to avoid other from adding automatically.

---

### Post by S-99 on 2007-06-07
Hmm, wow, i downloaded this and gave it a go. It downloaded fine, installed fine, and works fine. Great cleanup and improvement over gyachi1.05. Though, along with gyachi 1.05, the new version won't show my webcam while amsn does. I heard that this had to do with some compression settings and v4l. But, i can't find much help on the net with it, as i use gspca drivers and not ucvideo drivers.

So in other words i was one of the few people who did get my quickcam messenger working under feisty and works in all of my programs except for gyachi. What do i do for my cam to make it display a picture there, because it has the right video device in there.

---

### Post by loell on 2007-06-08
gyachi uses v4l1 by default , at times when a webcam is v4l2 compatible only, gyachi could not detect it. :(
but during configure/compile time, you can specify a parameter to use v4l2. perhaps i can make a deb package later tommorow with that option enabled,and maybe you can test it, i'll just PM you when i have it ;)

---

### Post by impala on 2007-06-08
ok I have tried to download gyachi.sidetrack several times and it bombs off before the download finishes , is there a problem with the link, I really want to try this as I have had so many problems trying to get voice to work in gyachi, can you post gyachi.sidetrack at sourceforge or somewhere else make it more accessible. thanks for all the work you guys put into these projects.

---

### Post by S-99 on 2007-06-08
Well, that sounds like an idea. And i'm willing to try it so i can get rid of crappy kopete for downloading crappy kde core files for one small program as temporary measure for yahoo webcam. But yeah, my cam uses v4l1 as far as i could find out about it in gstreamer-properties where i was testing it.

---

### Post by impala on 2007-06-08
Ok because the links appear to be broken for gyachi.sidetrack when I tried to download it in Fiesty Fawn I logged into windows and thought lets be clever, and download the deb file to my flash stick and transfer it over. Well guess what, it bombs of at 1,560,770 bytes every time,, then starts to download again and again, I went to your googlepages, [http://gyachi.sidetrack.googlepages.com/](http://gyachi.sidetrack.googlepages.com/) and saw the source code as well as the deb package, guess what , it also bombs off before the download can complete. Is there
some thing flakey about these links, maybe it works fine for others but hell if windows and fiesty are having problems. Who knows. 
[http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz](http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz)
[http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5-1_i386.deb](http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5-1_i386.deb)

LOELL The problem I have with gyachi is that the sound isnt constant and the mic does not work thats why I want to try your version, We cant get a lot of people off Windows because so many want yahoo with voice, if it is such a chore to install gyachi then how can a novice to linux be expected to switch over, yahoo with voice is to me the most important Project I can think of, you can build all the versions of linux you like but if people cant get such a common progran like yahoo to work right up they will never cross over.

PS. I just installed Fiesty, had Dapper and loved it, so crisp and clean, the judges are still out on Fiesty.

---

### Post by loell on 2007-06-08
> **impala said:**
> Ok because the links appear to be broken for gyachi.sidetrack when I tried to download it in Fiesty Fawn I logged into windows and thought lets be clever, and download the deb file to my flash stick and transfer it over. Well guess what, it bombs of at 1,560,770 bytes every time,, then starts to download again and again, I went to your googlepages, [http://gyachi.sidetrack.googlepages.com/](http://gyachi.sidetrack.googlepages.com/) and saw the source code as well as the deb package, guess what , it also bombs off before the download can complete. Is there
some thing flakey about these links, maybe it works fine for others but hell if windows and fiesty are having problems. Who knows. 
[http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz](http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz)
[http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5-1_i386.deb](http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5-1_i386.deb)

LOELL The problem I have with gyachi is that the sound isnt constant and the mic does not work thats why I want to try your version, We cant get a lot of people off Windows because so many want yahoo with voice, if it is such a chore to install gyachi then how can a novice to linux be expected to switch over, yahoo with voice is to me the most important Project I can think of, you can build all the versions of linux you like but if people cant get such a common progran like yahoo to work right up they will never cross over.

PS. I just installed Fiesty, had Dapper and loved it, so crisp and clean, the judges are still out on Fiesty.

sorry, i have no idea, why it bombs at you.  this could be a problem related to your internet connection. i tested it again today, but i could not replicate the symptomps you mentioned above.

you might have a misconception, that i have changed or improve gyachi's voice chat in this version, if you can refer to my first post, those are the only changes that i have made. also, gyachi voice chat is room voice chat , but if you would just like yahoo voice call funtionality, you could try this instruction.

[URL="http://ubuntuforums.org/showthread.php?t=414121"]
HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service.[/URL]

you can also look around, but to this date, there is no FOSS project that has decoded yahoo sip voice protocol.  this task is quite difficult ;) and for years third party yahoo clients have always play a cat and mouse game with yahoo.

---

### Post by Carbon Tiger on 2007-06-09
Hello, bit of a newbie question here. (I've only been using ubuntu for about three days so I'm learning as I go) Anyway, everything is working fine with this program but the voice chat, in my terminal I get this error message:

(gyachi:7812): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_WIDGET (child)' failed

(gyachi:7812): Gtk-CRITICAL **: gtk_box_pack_start: assertion `child->parent == NULL' failed
Could not open /tmp/pyvoice_chat_start_username

Any idea what the problem is and how I can fix it ?

Thanks.

---

### Post by Carbon Tiger on 2007-06-10
I dunno I can't seem to get the voice chat working. It connects and it opens the talk window but the talk button is greyed out no matter what I do. I'm on a HP  Pavilion dv6000 if that helps. Sorry if I'm being a pest its just this is the last thing left on my list of things to do since moving to ubuntu full time.

---

### Post by loell on 2007-06-11
hi, you need to be in a chat room , before you start the voice chat.

---

### Post by S-99 on 2007-06-12
Ok, with the camera thing. I tried the v4l2 build for shits and giggles because i could mainly because you offered so kindly. Anyway, blank screen with my quickcam messenger in the v4l2 build. So i tried switching back to the qc-usb driver instead of the gspca. Gspca and qc-usb for my cam are v4l. This sounds like it's a problem with feisty. Gyachi worked perfectly when i installed the qc-usb driver for my cam in edgy. Then i got my cam working in feisty with gspca, so i uninstalled that got going with good old qc-usb installed. And everything works with the webcam now except for gyachi pretty much. I have v4l1 enabled and driver loaded, but gyachi wont show a picture, perhaps this is due to feisty?

Also gyachi-sidestep seemed to have slowdown when chatting to my contacts on my friends list. I could type 5 seconds later i couldnt do anything, and then i could go back to typing. Idk what was with it.

---

### Post by loell on 2007-06-12
> **S-99 said:**
> 
Also gyachi-sidestep seemed to have slowdown when chatting to my contacts on my friends list. I could type 5 seconds later i couldnt do anything, and then i could go back to typing. Idk what was with it.

hmm , you can monitor what application is consuming your cpu, through system monitor.

there could another process or application that could be using the cpu by that time you type.

---

### Post by impala on 2007-06-12
Hi Loell .
I finally got gyachi-sidekick but only after a sqillion attempts and installing d4x download manager, funny that , Well it looks nice and fancy, better than all the others, good job, but one problem still remains , as with all the other versions of Gyach I have tried it logs in fine, start voice chat and sounds great at first then the blipping starts, like it is segmenting, as long as one person stays on mic its fine, when the users change in it segments, and sound is only in one speaker, also people see me key up the mic but nothing comes out, I tried to test the mic in sound recorder and got fold back when I pushed the volume up too high so it seems the mic is functional but alas did not record anything, using fiesty, any help welcome. :D:D:D

---

### Post by loell on 2007-06-12
:lolflag:

 i guess name mixup is a good thing :))  , theres gyachi-sidestep , gyachi-sidekick. maybe there will also be, 
side-lines , side-ways or side by side, heheh , this is what one get for picking a name from out of the blue :popcorn:


can you upload a an image of your gnome-alsamixer , preferably on imageshack.com , and post the link here
so that i can see your mixer settings, and we will see what we can do.. install gnome-alsamixer first if you don't have it.

---

### Post by Carbon Tiger on 2007-06-13
> **loell said:**
> hi, you need to be in a chat room , before you start the voice chat.

I dunno its weird I go into a conference room click voice chat enable and then open the voice chat box, click on and the talk icon is still grayed out. Something with my sound codecs ? Or m I doing something wrong here ?

---

### Post by loell on 2007-06-13
is this a private conference? or a public chat room? if its a chat room , may i know what room is this?

---

### Post by Carbon Tiger on 2007-06-14
> **loell said:**
> is this a private conference? or a public chat room? if its a chat room , may i know what room is this?

It was a private conference. I really don't use yahoos public chat rooms....oh and when I try to make a private room (not a conference but a room) for me just to use with my buddies I get the can't create room error in yahoo (but I think this may be a general yahoo error). Thanks for taking time to answer my questions. I hope I'm not being too much of a pest.

---

### Post by loell on 2007-06-14
i see , i haven't gone to this path yet. but there was a similar question posted in yahoo answers, about voice chat in private conferences, a couple of answers said that there should have (10+) participants in a private conference for voice chat to be enabled. though i could not confirm this .

---

### Post by rockyec78 on 2007-06-22
hey thanks for this hack of gyachi, somewhat more resembling to an IM program =D>
i have a problem in putting my display pc in IM window, whenever i try to use "Share my photo" option in "My Display Image" dialog box, after selecting the pic it says "the image could not be converted to a 96x96 .PNG image".
when i try to use "Share my avatar" it says "The image could not be loaded".
I had this problem with Gyachi too.:(
how to solve this problem??????????

---

### Post by loell on 2007-06-22
yeah :)

 that is because "convert" command is not installed in fiesty by deafult , this command is used in gyachi for avatar resizing.
 the **convert** command is part of ```
imagemagick
``` package, 

try installing
```
 imagemagick
``` 


hth ;)

---

### Post by M_N_M74 on 2007-06-26
I would like to try the gyachi-sidetrack, but clicking on the link you provided in the first post doesn't allow me to download.  The dialog box comes up but the only allowable button is cancel.  how else can I get this program...and what do I have to do to install it when I do have it?  Will this version work on a 64bit machine?

Thanks

---

### Post by loell on 2007-06-26
hi, i've added another link for others that have difficulty downloading from google pages.

but this particular deb package is not meant for 64 bit, still waiting for anyone volutneering to pacakge it as 64 bit.

---

### Post by odiseo77 on 2007-06-27
Hi loell, I'm lzrs_morell from the official gyachi forum; remember me? ;) Just installed gyachi_sidetrack on Feisty and it looks great; there's a nice improvement in the look & feel. I'm only having one issue, that I also have with the official gyachi package, either on Debian, or Ubuntu: I can't enter any chatrooms :( does anyone else is having the same issue? (not sure if it's because I'm behind a router on a wireless connection; I don't use yahoo too often and I have been 'unplugged' from yahoo and gyachi for a while so I think I'm gonna ask on the official gyachi forum).

P.S.: btw, I think the package from the first link you posted is somehow corrupted; when I tried to install it I got some errors (in spanish); something like: "(...)dpkg-deb: the 'paste' subprocess returned the error output code 2. dpkg: error when processing gyachi_sidetrack_1.0.5-1_i386.deb (--install): insufficient reading on buffer_copy (error in dpkg-deb during  `./usr/local/share/gyachi/audibles/base.us.goodbyes.split.gif') (...)" So I tried the one on the 2nd link and it installed fine. (just to let you know).

Greetings! :)

---

### Post by loell on 2007-06-27
hello lzrs_morrell :)

 ofcourse i remember you, how could i forget, we were both packagers and you're the one who taught me how to package gyachi the working but unusual way. ;)

the room problem is related yahoo servers problem. even the official client is having difficulty entering rooms.

hhmm :-k , file corrupted?  it seems i will have re-uppload it. i might have to remove the new link for now.

---

### Post by odiseo77 on 2007-06-27
Hi again! Well, too bad yahoo is having problems with its chat servers... lets hope for this issue to get solved :)

(and lets hope for gyachi 1.0.6 to be released soon!! :D )

Greetings!

---

### Post by Matthyis on 2007-06-27
the voice dont work I dont understand sometimes I see people talking but cant here them I'm able to loggin yahoo fine and browse roooms but the voice dont work I'm useing version
gyachi1.0.5-1edgyi386 and the side kick say's dependency not satisfiable libasound2
any idea's? thank you

---

### Post by loell on 2007-06-27
> **odiseo77 said:**
> Hi again! Well, too bad yahoo is having problems with its chat servers... lets hope for this issue to get solved :)

(and lets hope for gyachi 1.0.6 to be released soon!! :D )

Greetings!

yeah lets hope for a new release , and if stefan and greg can finally look into my code changes for corrections and what not, then maybe they can implement some it if not all of it.:biggrin:

---

### Post by loell on 2007-06-27
> **Matthyis said:**
> the voice dont work I dont understand sometimes I see people talking but cant here them I'm able to loggin yahoo fine and browse roooms but the voice dont work I'm useing version
gyachi1.0.5-1edgyi386 and the side kick say's dependency not satisfiable libasound2
any idea's? thank you

the deb package is only compatible for fiesty not for edgy :( , sorry , i could not build an edgy package for this hack/mod. as i have already upgraded my pc from edgy to fiesty, after it was released.

---

### Post by justin_c18 on 2007-06-29
"corrupt filesystem tarfile - corrupted pachage archive
dpkg-deb: subprocess paste killed by signal (broken pip)"

That's what I get when I ry to install gyachi-sidekick.
Can I install on xubuntu? What has changed, is it still bulky?

---

### Post by girard on 2007-07-01
tsong! i didn't read through all six pages anymore so pardon if i missed this. 

would there be a slight possiblity that a pc to pc call between a linux and windows yahoo user, be established already? this also goes for video calls. never got this to run on 6.10. although i like it when gaim shows those who are invisible, so i use my linux desktop from time to time. problem is, i need to communicate with my wife abroad, so i have to use my MS pc for the pc-to-pc and video call of yahoo messenger, which we can't establish when i'm on ubuntu.

also, i might be missing something. by voice chat, do techie guys mean pc-to-pc calls or is it different?

---

### Post by loell on 2007-07-02
pare! ;)

voice chat is only available in public rooms , theres no native yahoo voice call (pc to pc call) yet  for any third party yahoo client in linux and even in windows.


Maybe you'd like to try this setup

[URL="http://ubuntuforums.org/showthread.php?t=431290"]   	
HOWTO: Voice call Yahoo Messenger using Ekiga and gtalk2voip service.[/URL]

let me know if it works for you :)

---

### Post by girard on 2007-07-02
salamat! i'll keep you posted if it works!

---

### Post by medya on 2007-07-03
i wish you make gyachi looks just like y! .  i dont think it is a hard work I may do that this summer for you . if u dont mind.

---

### Post by loell on 2007-07-03
> **medya said:**
> i wish you make gyachi looks just like y! .  i dont think it is a hard work I may do that this summer for you . if u dont mind.

first off, you don't need to ask permission from me, so i won't mind, its open source, anyone can change/code it. ;) 
plus i'm not part of the official gyachi development team.

if you think it is easy to implement the default  Y! layout in gyachi, **then, code it. by all means...**
_*put your money where your mouth is*_ as they say these days.

no offense, but i just hope you don't end up like this

[**gyachoo-messenger**]("http://sindos.wordpress.com/2007/03/02/gyachoo-messenger/")

a possible poser.



till then...

---

### Post by currahee30577 on 2007-07-03
I get this error when trying to install   dpkg : error processing  /tmp/gyachi_sidetrack_1.0.5-1_i386-1.deb

---

### Post by loell on 2007-07-03
maybe download it again, to another folder/directory other than the /tmp directory , let me know how it goes..

---

### Post by currahee30577 on 2007-07-03
when I retry I get a message List of files could not be read, please report this as a bug.... this maybe or may not be a bug

---

### Post by neoflight on 2007-07-03
i am running debian etch and i cant seem to install the deb. Is there a way to get an etch deb for this one? i am curious to see how it works. Yahoo messenger with webcam and sound is the one thats keeping the XP in my laptop. Once this can be fixed i can remove XP forever. 

Thanks

---

### Post by citadin86 on 2007-07-03
Nice. but what about 64bit users?!?!?!?!?!?!?!?!?!. We want voice chat and webcam as well.

---

### Post by tonytux on 2007-07-03
Loell- installed gyachi through automatix, found this post while searching for my problem and tried to install your version thinking it might have been fixed through your mods, turns out your version was the one I installed from automatix.

I enjoy this messenger over gaim immensely, have yet to attempt any of the previous problems, voice, video, file trasfer, I really have no need for them at the moment.  But I am getting a problem with using anything off of the "My Yahoo" tab, any of the dropdown list selections: weather, email, news, etc. give me a 'this document has moved [here]("http://e.my.yahoo.com/config/set_cssplash?.done=http%3a%2f%2fmy.yahoo.com%2fpreview%2fpirymail.html")' which sends me to a page on my Firefox about getting my yahoo web-page set-up, nothing close to what I was originally trying to get to. I was curious if this is a Yahoo server thing, a port forwarding thing or if it is a small catch in the program, I'm hoping it's something I overlooked or setup incorrectly.

I appreciate all that people of your stature and abilities does for the end-users, keep it up!

---

### Post by loell on 2007-07-03
hi, tonytux :)

thanks for the heads up, i didn't know  that arnieboy already incorporated this mod/hack in automatix. :D

so you're using the "My yahoo" function? yeah, its mostly an old URL , it just needs a bit of updating. correcting the url, i think for most part this is doable, i'll add it in my to-do list :)

EDIT.. 

 i'm also using the y! mail preview, but it doesn't direct me to that page, I think you need to  configure your "MY yahoo" page
just click the **get it now** button , the direction should be relatively easy from there , post back if you encounter any problems in configuring

---

### Post by loell on 2007-07-03
> **currahee30577 said:**
> when I retry I get a message List of files could not be read, please report this as a bug.... this maybe or may not be a bug

can you install other deb packages of other programs?

---

### Post by loell on 2007-07-03
> **neoflight said:**
> i am running debian etch and i cant seem to install the deb. Is there a way to get an etch deb for this one? i am curious to see how it works. Yahoo messenger with webcam and sound is the one thats keeping the XP in my laptop. Once this can be fixed i can remove XP forever. 

Thanks

if there is someone , who have an etch box.. :D

@lzrs_morell , do you still have your etch?

---

### Post by loell on 2007-07-03
> **citadin86 said:**
> Nice. but what about 64bit users?!?!?!?!?!?!?!?!?!. We want voice chat and webcam as well.

the voice chat won't work on 64 bit :(, it uses an old  version of wine component..
but its possible to package this by stripping out the  voice chat, and the webcam and other functions will stil; work, 

 though i'll have yet to find a volunteer that has 64 bit machine for 64 bit packaging :)

---

### Post by currahee30577 on 2007-07-03
> **loell said:**
> can you install other deb packages of other programs?

loell yes I can install other apps

---

### Post by currahee30577 on 2007-07-03
its says corrupt tarfile - corrupt package archive

---

### Post by odiseo77 on 2007-07-03
> **loell said:**
> if there is someone , who have an etch box.. :D

@lzrs_morell , do you still have your etch?

Hi loell, didn't see your post til now, yes, I have my debian box, only it's not etch anymore but lenny/sid :D Haven't tested the debian etch package after I dist-upgraded to Lenny, but I guess it should work. If you give me the sources of  gyachi_sidetrack I can make a Debian one of it :biggrin: but I think it won't work on Etch since I'm on Lenny, as I said before :(

---

### Post by currahee30577 on 2007-07-04
loell, I got it up and running. A very nice program. Thanks for all your help

---

### Post by loell on 2007-07-04
> **odiseo77 said:**
> Hi loell, didn't see your post til now, yes, I have my debian box, only it's not etch anymore but lenny/sid :D Haven't tested the debian etch package after I dist-upgraded to Lenny, but I guess it should work. If you give me the sources of  gyachi_sidetrack I can make a Debian one of it :biggrin: but I think it won't work on Etch since I'm on Lenny, as I said before :(

heheh :D , that's just fine.

---

### Post by neoflight on 2007-07-05
> **odiseo77 said:**
> Hi loell, didn't see your post til now, yes, I have my debian box, only it's not etch anymore but lenny/sid :D Haven't tested the debian etch package after I dist-upgraded to Lenny, but I guess it should work. If you give me the sources of  gyachi_sidetrack I can make a Debian one of it :biggrin: but I think it won't work on Etch since I'm on Lenny, as I said before :(

seems like we are both...!!!
it does not matter...i am ready to upgrade to lenny if  I get this one...i dont want to boot again to xp....please...thanks

---

### Post by odiseo77 on 2007-07-05
> **neoflight said:**
> seems like we are both...!!!
it does not matter...i am ready to upgrade to lenny if  I get this one...i dont want to boot again to xp....please...thanks

Well, I don't have the sources of gyachi_sidetrack, so I can't build a debian package with it, but you still can use the [official gyachi package for etch]("http://prdownloads.sourceforge.net/gyachi/gyachi_1.0.5-1_i386.deb?download") ;)  I'm using it right now on Lenny and works ok (except, of course, for the chatroom problem I mentioned before)... anyway, as soon as gyachi 1.0.6 is released (hopefully with the changes loell made to it), I'll build a package for debian lenny ;)

---

### Post by loell on 2007-07-05
> Well, I don't have the sources of gyachi_sidetrack, so I can't build a debian package with it, but you still can use the official gyachi package for etch I'm using it right now on Lenny and works ok (except, of course, for the chatroom problem I mentioned before)... anyway, as soon as gyachi 1.0.6 is released (hopefully with the changes loell made to it), I'll build a package for debian lenny 

here is the source [http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz]("http://gyachi.sidetrack.googlepages.com/gyachi_sidetrack_1.0.5.tar.gz") ;)

afaik, the code hasn't been  evaluated yet by gyachi devs , though i already presented this  to them.. 
i've been talking to (hoshy - project lead) but mostly to greg the current active coder for gyachi, he also busy with his fixes and enhancements to the UI , it may take a while to see this on gyachi main.

---

### Post by odiseo77 on 2007-07-05
Thanks loell! As soon as I have some time I'll build a .deb package for lenny for others to enjoy it ;)

Greetings.

---

### Post by girard on 2007-07-08
hi. just downloaded the deb file. double-clicked it. and i believe it installed itself. but i can't see it in the internet tab, nor does it run when i type in gyachi in the terminal. i'll also try to figure it out while i wait for replies. but any help would be welcome.   i'm on fiesty. have gaim and skype installed (if that really adds anything)

---

### Post by loell on 2007-07-08
if it does not show up, when you type ```
 gyachi 
``` in the terminal, and prompted with the error
```
command not found
``` or something similar, then i think  its not installed.  can you download the deb file again? the file might have been corrupted, i also added another link, perhaps you can try the first one.

---

### Post by tonytux on 2007-07-09
loell
   Yup! you were right I overlooked the obvious, works like a charm now. Thanx! :lol:

---

### Post by neoflight on 2007-07-12
any updates for lenny package yet? ...

sound and webcam are the only things keeping me away from ditching windows....

---

### Post by odiseo77 on 2007-07-12
Hi, neoflight, loell sent me the sources, but I've been a bit busy lately. I think I'll build it this weekend and post the link here ;)

Greetings!

---

### Post by odiseo77 on 2007-07-14
Hi loell, I'm trying to compile gyachi-sidetrack on Debian Lenny/sid in order to build the .deb package; I ran the autogen.sh script, then './configure --enable-maintainer-mode' (all the dependencies were successfully met), but when I run 'make' I get this:

```
(...)
In file included from win32.c:29:
wine/winbase.h:544: warning: ‘packed’ attribute ignored for field of type ‘CHAR[8]’
In file included from wine/module.h:11,
                 from win32.c:34:
wine/pe_image.h:60: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:62: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:64: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:66: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:67: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
wine/pe_image.h:69: warning: ‘packed’ attribute ignored for field of type ‘BYTE’
win32.c:71: error: static declaration of ‘vsscanf’ follows non-static declaration
win32.c: In function ‘expGetSystemInfo’:
win32.c:1015: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c:1042: warning: format ‘%ld’ expects type ‘long int’, but argument 3 has type ‘DWORD’
win32.c: In function ‘expGetFullPathNameA’:
win32.c:3528: warning: assignment discards qualifiers from pointer target type
win32.c: In function ‘expExitProcess’:
win32.c:4402: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘DWORD’
make[2]: *** [win32.o] Error 1
make[2]: se sale del directorio `/home/vicente/gyachi-1.0.5/gyvoice'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/vicente/gyachi-1.0.5'
make: *** [all] Error 2
vicente@debian-box:~/gyachi-1.0.5$
```

Do you know how to solve this issue? 

Thanks in advance.

P.S.: Though this doesn't seem to be the problem, I already have wine, libwine and libwine-dev packages installed.

Regards.

---

### Post by loell on 2007-07-14
yeah, this is an error produce by newer GCC

in configure.in find this line

AC_CHECK_FUNCS([dup2 gethostbyname gettimeofday memmove memset mkdir regcomp rmdir select setlocale socket strcasecmp strchr strcspn strdup strncasecmp strrchr strstr strtol strtoul uname])

and add ```
vsscanf
``` after uname, and then do the usual.


this is also the case of gyachi main, though its been fixed in the cvs

---

### Post by odiseo77 on 2007-07-15
@loell: thanks, that worked! :)

@neoflight : here it is, finally: [gyachi_sidetrack for Debian lenny/sid]("http://rapidshare.com/files/43057897/gyachi_1.0.5-1_i386.deb.html") :biggrin:

Note that you must dist-upgrade to lenny before installing the package, otherwise, you'll probably get dependencies issues :)

Greetings.

---

### Post by loell on 2007-07-15
i'll also put this in the first post :)

---

### Post by odiseo77 on 2007-07-15
Great!! Thank you loell :D

---

### Post by leech on 2007-07-15
How awesome is it that I discovered this program a few hours ago (knew about gYachE but not gYachI) and was looking for a sid package since the one on the site doesn't work anymore (due to the libjasper version)  Very nice.

And for once it's stayed on for a few hours without crashing, which was the reason I never used gYachE.

Leech

---

### Post by drytear on 2007-07-17
and .. how do you solve the freezing while transfering file from windows to gyachi problem? (using yahoo account)

---

### Post by loell on 2007-07-17
> **drytear said:**
> and .. how do you solve the freezing while transfering file from windows to gyachi problem? (using yahoo account)

well, programatically speaking, you need the file transfer to be done on a separate process, so the main application won't freeze.

---

### Post by drytear on 2007-07-18
so then .. it's a design bug ?

---

### Post by loell on 2007-07-18
> **drytear said:**
> so then .. it's a design bug ?

most likely, one of the current devs, is indicating to fix this soon, perhaps in time for  version 1.0.6

---

### Post by wersdaluv on 2007-07-24
This one looks so much better compared to the other Gyache Improved!

I'm just wondering, how come Gyachi devs manage to add webcam support (and partial voice support) while Pidgin and Kopete can't manage to do it? What's with Pidgin and Kopete?

---

### Post by loell on 2007-07-25
> **wersdaluv said:**
> This one looks so much better compared to the other Gyache Improved!

I'm just wondering, how come Gyachi devs manage to add webcam support (and partial voice support) while Pidgin and Kopete can't manage to do it? What's with Pidgin and Kopete?

:lolflag: multi-protocol and code abstraction can be a pain in the *ss , though i should say thier method could be very rewarding compared to a single client- single protocol approach like gyachi and amsn.

yahoo webcam support didn't come easily  in gyachi , it was incorporated by chris pinkham way back in 2000 in 
gyach -- the mother of all gyach fork series :)

and kopete does webcam too. ;)

---

### Post by Carlo1973 on 2007-08-01
Something I would like to see in Gyachie is this. Webcam support for V4l2 camera's lol.

I believe it was enabled or compiled into the latest gyachi build you posted here, but I can't seem to get it to work for the life of me. When I try it out I get these weird errors "Gyachi (Webcam Broadcaster): Error While querying mmap-buffers."

I've used the multimedia selector in Ubuntu, and it does detect my webcam properly, does turn it on and show me a fairly decent image of my self on it.  So I know the kernel compilations for my cam are installed and same with V4l2. I just wish I could get it to work with a chat program - not just the multimedia selector/test program. 


Carlo

---

### Post by loell on 2007-08-01
a month ago, i've had the chance to chat with the project lead via :arrow: ICQ :mrgreen:

i reported this incidednt where some v4l2 webcams could not be detected,  it was then that i learned that the v4l2 cam code for gyachi is still at an experimental stage,

anyhow, have you considered kopete?

---

### Post by cyke on 2007-08-02
hi, i could not get my webcam to work. im running feisty on a sony vaio laptop VGN-SZ series.  webcam is ricoh R5U870 built-in cam.  it works on  ekiga softphone app.

i get a "Gyachi (Webcam Broadcaster):  Error whie capturing initial image." error when starting my webcam.

has any vaio users got success in running cam on gyachi?

---

### Post by wersdaluv on 2007-08-04
My webcam has been working with Gyachi for quite some time until last week, when I tried to start my webcam, there was an error message that said ```
Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.
```

I decided to reformat after all the problems that I had with my Feisty install.

Now, after having a fresh new Feisty install in a new partition, the error message was there again.

I ran xawtv in the terminal while my webcam was connected and what came out was 
```
xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory

```

How do I make my webcam working again?

---

### Post by wersdaluv on 2007-08-04
> **wersdaluv said:**
> My webcam has been working with Gyachi for quite some time until last week, when I tried to start my webcam, there was an error message that said ```
Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.
```

I decided to reformat after all the problems that I had with my Feisty install.

Now, after having a fresh new Feisty install in a new partition, the error message was there again.

I ran xawtv in the terminal while my webcam was connected and what came out was 
```
xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.20-16-generic)
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory

```

How do I make my webcam working again?

Ooops! I just had to tighten my webcam's usb connection to make it work!

It's working now! :)

:lolflag:

---

### Post by loell on 2007-08-04
> **wersdaluv said:**
> Ooops! I just had to tighten my webcam's usb connection to make it work!

It's working now! :)

:lolflag:

LoL indeed :)

---

### Post by chocbar31 on 2007-08-10
Dayumm...Excellent Improvements, as I am a Gyachi fool. Haven't seen a better app for chat other than Gyachi. Gyach(E,I) Rocks!

With your improvement it also now Rolls. Great job loell!

Thank Ya!

:guitar:

---

### Post by loell on 2007-08-10
your'e welcome  :)

---

### Post by flowbot on 2007-08-12
wow, looks like really cool app!

unfortunately, using Gutsy Gibbon i also get the error:

```

Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.

```

I've got an integrated laptop webcam that uses the uvc usb video driver. it works with ekiga, amsn and luvcview. unfortunately i can't tighten the usb cable, as the webcam is built  into the laptop :D

any idea if there's a fix for this?

---

### Post by JNik on 2007-08-12
This looks much better than GyachI/E. Thanks for the fork :)

What I would like to see in any/every fork is buddy icons next to the nicks in the "Buddies" list.

By the way, I have to hold the right button clicked, and select an item from the pop-up menu by releasing it, in order to select it. Another way is to press the "properties" button on the keyboard. If I just right click, the pop-up appears and disappears in no time. Is that a bug or a future? :)

I get the following messages on the console
```

(gyachi:6450): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_WIDGET (child)' failed

(gyachi:6450): Gtk-CRITICAL **: gtk_box_pack_start: assertion `child->parent == NULL' failed

(gyachi:6450): Gtk-CRITICAL **: gtk_menu_attach_to_widget: assertion `GTK_IS_MENU (menu)' failed

(gyachi:6450): Gtk-CRITICAL **: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed

(gyachi:6450): Gtk-CRITICAL **: gtk_widget_set_events: assertion `!GTK_WIDGET_REALIZED (widget)' failed

(gyachi:6450): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(gyachi:6450): GLib-GObject-CRITICAL **: g_signal_handlers_destroy: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gyachi:6450): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```
so the right click problem might have to do something with them?

---

### Post by loell on 2007-08-12
that's a gtk thingy i believe, i have been finding solution through documentation to no avail :( , i guess that's how a gtk right click pop-up can only work.

those critical messages in the console were already fixed in the CVS of gyachi,

there is an exciting development going on in gyachi main, the dev(s) had numerous bug fixes, and made the file transfer more usable by unlimiting the file size, though the old interface is all the same ;)

i guess i'll have to redo the facelift whenever the new version is coming out :popcorn:

---

### Post by lazyron on 2007-08-22
I too am seeing the following error message:

```
Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.
```

Shell output is:

```
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/LegacyHuman/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
```

Relevant lsusb output:

```
Bus 005 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger

```

I configured with the default settings, so I'm not sure if I selected the correct webcam support option for use with Gyachi.

Ekiga picks up the webcam fine and I'd be happy using that but I'd like to be able to continue using my Yahoo account as it's already set up with Friend Lists, etc...

Any ideas?

---

### Post by yousufinternet on 2007-08-22
hi
i am using gyachI and i realy like the features in this program 
althought the user interface is a bit complicated but it's ok 

i have another problem with the program 
i can't read the arabic text i type using gyachI although the other users (yahoo messenger or pidgin ) can read the text i send to them :)
waiting to hear a solution
and sorry for my english 
(a screenshot is attached)

---

### Post by odiseo77 on 2007-08-22
Yeah, I have a similar problem with UTF8 encoding; for example, if I type accented characters (áéíóú) or the 'ñ' sign it sometimes displays the right characters and other times displays weird ones ...it happens both, with the official gyachi client and with gyachi-sidetrack. I posted about this bug at the official gyachi forum, but it seems to me the developers haven't figured how to fix it yet...

---

### Post by loell on 2007-08-23
:-k odd, in chat rooms, i can see Arabic text just fine.

---

### Post by diver62 on 2007-08-24
I am a newbie to linux. I was wondering if someone could help me figure out what I have done wrong in the install of 'sidetrack. I am getting this message when I start gyachi: (gyachi:17178): Gtk-CRITICAL **: gtk_box_pack_start: assertion `GTK_IS_WIDGET (child)' failed

(gyachi:17178): Gtk-CRITICAL **: gtk_box_pack_start: assertion `child->parent == NULL' failed
I have read on this thread about needing to be in a chat room but I can't even get logged on to yahoo. I would really appreciate any help on this problem. Thanks in advance. :confused:

---

### Post by loell on 2007-08-24
in the log in window, where you provide your yahoo user name and password,
you also need to choose a server in the list just below it, check the no chat room check box.

---

### Post by diver62 on 2007-08-25
Thank you loell very much. I wasn't paying very close attenion to what I was doing. lol

---

### Post by Nicole on 2007-08-28
Loell, thanks very much for this. 

I was just wondering if other yahoo chat users were having trouble logging into chat rooms at the moment (more so than normal, I mean!) and if this is a problem with yahoo, or my computer, or if gyachi/other 3rd party software needs to update something? I suspect it's Yahoo, it usually is, but thought I'd see if it was something I had broken...

N

---

### Post by loell on 2007-08-28
yeah, yahoo rooms are badly messed up at the moment.

---

### Post by fortAlamo on 2007-08-29
With gyachi I get this msg as i *TRY* to change chat's room:

'To help prevent spam and bots from disrupting your Yahoo! chat experience, please click here to verify your account (this link wil'"

the msg is interrupted, NO link to be clicked :(

using ymessanger ( on win ) i can read the link, click on it and change the room


any hints?

tnx

---

### Post by loell on 2007-08-29
yeah this a new implementation by yahoo, just a couple of hours ago, i guess.

in the terminal you can see the url, for the captcha, you can just copy and paste the captcha to firefox, then enter the turing number, and then you can enter the room.

i know this is an inconvinience for us all, just bear with this for a little while.

---

### Post by fortAlamo on 2007-08-29
tnx for the reply :)


I can't see the link on the main "gyachi" chat screen cos is interrupted,
what you mean with "in the terminal you can see the url" ?

---

### Post by loell on 2007-08-29
sorry, i haven't explain clearly ;)

in order to see the url captcha for rooms, you need to run gyachi through the terminal or the command line console, when you enter a room and you can't see the captcha, in gyachi's main window, just swith to the console where executed gyachi, you'll see the url there.

---

### Post by fortAlamo on 2007-08-29
> **loell said:**
> sorry, i haven't explain clearly ;)


 actually you were clear ....  :lolflag:

I've already tried running gyach from the terminal konsole as well, 
BUT , even from there  I can't see the link anyware :confused:

---

### Post by fortAlamo on 2007-08-29
... maybe I just miss smthing :popcorn:

---

### Post by loell on 2007-08-29
can't you see this in the terminal? also enable packet debugging in connection menu

---

### Post by fortAlamo on 2007-08-29
> **loell said:**
>  enable packet debugging in connection menu

THAT did the trick :guitar:

now i can see the link on konsole

many thanks :)

---

### Post by loell on 2007-08-29
np :)

---

### Post by @vijay@ on 2007-09-02
loell
i just install gyachi-sidetrack in my feisty ; but i was unable to connect to the yahoo server
im behind a proxy server ....... i enable to connect through proxy in setup

but getting errors like unable to connect through socket 4 or something like that

---

### Post by abish on 2007-09-07
and how do i run gyache from terminal?.
m sorry.. i am new to linux!

---

### Post by loell on 2007-09-07
just type **gyachi** in the terminal

---

### Post by abish on 2007-09-07
thanks man.:)
i typed gyache.. hehe. dumb!!

---

### Post by loell on 2007-09-07
np :)

---

### Post by Severa on 2007-09-07
Maybe you guys and gals can help me.
I'm running the CVS version from page 1 of this thread on Feisty.
Trying to tweak my webcam, it's an Omnivision with the ov51x-jpeg driver from rastageeks.org.
Thing is the webcam looks just fine when I check it on xawtv but does this weird bouncing
split screen thing, I'll include part of a screenshot I took.
(Yes my nails are painted an interesting shade of blue, the color's not my concern so much as the split screen)
Any help would be greatly appreciated. Thanks!

---

### Post by loell on 2007-09-07
my wild guess is that, the image is converted twice , once in the ov51 driver and the second is in gyachi hence the split. 

i could provide an experimental package without the format conversion, if you are willing to test this :)

---

### Post by Severa on 2007-09-07
> **loell said:**
> my wild guess is that, the image is converted twice , once in the ov51 driver and the second is in gyachi hence the split. 

i could provide an experimental package without the format conversion, if you are willing to test this :)

Sure, I'll try it. *s*  Thanks.

---

### Post by topedgemonk on 2007-09-08
when i try to install, it says.. 'dependency is not satisfiable: libasound2'. Could you please tell me what to do? but I run dapper drake 6.06... is that the problem?

---

### Post by loell on 2007-09-08
yeah, its the problem , since the deb package is for ubuntu fiesty, sorry :(

---

### Post by loell on 2007-09-08
> **Severa said:**
> Sure, I'll try it. *s*  Thanks.

[try this pacakge]("http://www.mediafire.com/?6mx9tp0y8df")

and see if theres any luck for your webcam.

---

### Post by Severa on 2007-09-08
> **loell said:**
> [try this pacakge]("http://www.mediafire.com/?6mx9tp0y8df")

and see if theres any luck for your webcam.

No luck. it's still doing the split screen bounce thing like before. Thanks for the try. *s*

Would compiling it from source make a difference? I tried that before but could never get it to compile for me.

---

### Post by HarshReality on 2007-09-10
OK, how do we get recording going.... I selected ffmpeg and got a desktop full of jpgs lol

---

### Post by loell on 2007-09-10
you can encode the images by

```
mencoder -ovc lavc -mf fps=3:type=jpg 'mf://*.jpg' -o movie.avi
```

---

### Post by ralyon on 2007-09-14
I haven't seen any other comments on this so I thought I would chime in. But first I want to say what a great product. I had to use yahoo yesterday in my virtual windows and I realized just how much better gyachi is than yahoo. Thanks for all the hard work.

Now the problem, there appeared to be an update on the chat rooms yesterday and now I get an invalid id when I try and connect to the chat rooms. I am using the 1.0.5 linked to earlier in this thread. It was working the day before with only a connection hiccups which reset the other users in the room, but I liked thatt as it hid everyone that wasn't talking.

Is someone aware of this and working on a fix and if so, how can I help. I had voice and video working before as well, so I can test that as well.

ralyon

---

### Post by loell on 2007-09-14
its a yahoo server problem, i too is waiting for it to be restored


--edit

my bad, it seem yahoo changed the captcha packet again :(

---

### Post by luvz_mocha on 2007-09-14
> **loell said:**
> [try this pacakge]("http://www.mediafire.com/?6mx9tp0y8df")

and see if theres any luck for your webcam.

 I tried to install this package and get:

root@Home8:/home/george# dpkg -i '/home/george/Desktop/gyachi_1.0.5-1_cvs_i386.deb' 
(Reading database ... 173596 files and directories currently installed.)
Unpacking gyachi (from .../gyachi_1.0.5-1_cvs_i386.deb) ...
dpkg: error processing /home/george/Desktop/gyachi_1.0.5-1_cvs_i386.deb (--install):
 trying to overwrite `/usr/lib/win32/tsd32.dll', which is also in package w32codecs
Errors were encountered while processing:
 /home/george/Desktop/gyachi_1.0.5-1_cvs_i386.deb

Please help a total newb

---

### Post by loell on 2007-09-14
you could install the one from the frist post of the first page of this thread :)

---

### Post by luvz_mocha on 2007-09-15
> **loell said:**
> you could install the one from the frist post of the first page of this thread :)

The sidetrack build will install, but does not fix the cap chat problem when entering yahoo rooms.

---

### Post by loell on 2007-09-15
there is a cvs build at top of the first post , which fixed the captcha problem, however , yahoo changed again the protocol specs of the captcha the other day, still waiting for developer to commit the latest changes of the latest fix.

---

### Post by luvz_mocha on 2007-09-15
Getting back to my original question about installing the CVS build. Is it a permissions problem that the install can not overwrite:

`/usr/lib/win32/tsd32.dll

---

### Post by loell on 2007-09-15
nope, thats because you have win32codecs installed in your system , which gyachi have some of those codecs too.

anyhow, if you could wait within this week, i'll release another cvs build deb, with the second captcha fix , and as the developer said with out having to launch a browser , just to enter the captcha ;)

---

### Post by sabitha on 2007-09-28
> **loell said:**
> nope, thats because you have win32codecs installed in your system , which gyachi have some of those codecs too.

anyhow, if you could wait within this week, i'll release another cvs build deb, with the second captcha fix , and as the developer said with out having to launch a browser , just to enter the captcha ;)

have you finished the another cvs build deb loel. :) sorry i just can wait to see the fix because i already try the last one you build but still got trouble to join the room to long wait the captcha code not like YM (windows vers.), because sometimes i can join the room but too much failed join even i enter the captcha code.:KS

---

### Post by loell on 2007-09-29
> **sabitha said:**
> have you finished the another cvs build deb loel. :) sorry i just can wait to see the fix because i already try the last one you build but still got trouble to join the room to long wait the captcha code not like YM (windows vers.), because sometimes i can join the room but too much failed join even i enter the captcha code.:KS

here it is :) .. [http://www.mediafire.com/?52oh9ejx07d]("http://www.mediafire.com/?52oh9ejx07d")

---

### Post by loell on 2007-09-29
hi, as the porject is brewing for a new release , it needs further testing.

and so to those gyachi ubuntu fiesty users , please test the latest CVS deb package found in the first post of this thread.

any feedbacks regarding the latest CVS is appreciated.



some notable improvements.

**1. improved  filetransfer , theoretically you can now transfer 1 gig files **


**2. room captcha,provided by yahoo rooms, without having the need for a browser to input the captcha**


**3. settings on the buddy tab, to expand or not to expand offline buddies, and vice versa**

**4. chat tab ui is cleaner, when you are not in a room**

---

### Post by EvZ on 2007-09-29
hello im new to this but i love the program only problem is it only worked for me once right after i installed it and after that i get an error message that says i have been disconnected because of a broken pipe, error sending to socket 32 or somthing like that any help? i really appreciate it

---

### Post by loell on 2007-09-29
are you behind router

---

### Post by luvz_mocha on 2007-09-29
> **luvz_mocha said:**
> Getting back to my original question about installing the CVS build. Is it a permissions problem that the install can not overwrite:

`/usr/lib/win32/tsd32.dll

I am still getting this error with the latset build. The sidetrack build will install fine.
Any ideas as what is needed?

---

### Post by loell on 2007-09-29
> **luvz_mocha said:**
> I am still getting this error with the latset build. The sidetrack build will install fine.
Any ideas as what is needed?

thanks for the heads up , this only happens if you have win32 codecs, anyway.

here it is [http://www.mediafire.com/?0edr0enrodg](http://www.mediafire.com/?0edr0enrodg)

---

### Post by EvZ on 2007-09-30
nope no router straight cable connection

---

### Post by luvz_mocha on 2007-09-30
> **loell said:**
> thanks for the heads up , this only happens if you have win32 codecs, anyway.

here it is [http://www.mediafire.com/?0edr0enrodg](http://www.mediafire.com/?0edr0enrodg)

Thanks!!! Works great.

---

### Post by click2down on 2007-10-03
> **loell said:**
> :popcorn:  feedback is always welcome
I down it, but i can't install.
Please help me!:popcorn:

---

### Post by loell on 2007-10-04
what are the steps that you took exactly in installing it?

---

### Post by s_spiff on 2007-10-04
anyone care to put up some screenshots. Also is there a deb for x64?

---

### Post by loell on 2007-10-04
> **s_spiff said:**
> anyone care to put up some screenshots. Also is there a deb for x64?

it has a wine component which make it difficult to port to x64, i don't have x64 machine too.

---

### Post by manubalasree on 2007-10-06
I have same problem

---

### Post by GoneWithTheWind on 2007-10-14
> **loell said:**
> room captcha,provided by yahoo rooms, without having the need for a browser to input the captcha]

Is this working now, and does it work with 6.06?

Thanks.

---

### Post by odiseo77 on 2007-10-14
The captcha thingie should work on every OS as long as you manage to compile it and install properly (which is not too hard on debian-based distros), unless, of course, that you have a .deb package for Dapper.

---

### Post by chocbar31 on 2007-10-19
YAY....finally installed on Gutsy, after final release! I'm baaaack! Course, I never really left as I had to use 7.04 until it would run on Gutsy. 

Time to move files!!!

Can't thank loell enough. Haven't used Yahoo's messenger in over a year now. No plans to go back either!

7.10 has come a long way. Love it when everything works outta-the-box; even when it doesn't! Eventually, getting the fix feels so grand.

:)

---

### Post by loell on 2007-10-19
nice to hear from you :)

i haven't yet build a gutsy deb though. i hope that i could convince gyachi developer to make the release cut tommorow, then i could finally build a new release :)

---

### Post by dmneoblade on 2007-10-19
I get this error when trying to install under Gutsy. Anyone have links to the .deb files for these libraries so I can get it set up? (quite the impatient one here, and finding .deb files online is annoyingly hard. )

```

Selecting previously deselected package gyachi.
(Reading database ... 108604 files and directories currently installed.)
Unpacking gyachi (from gyachi_1.0.5-1_i386.deb) ...
dpkg: dependency problems prevent configuration of gyachi:
 gyachi depends on libgail17 (>= 1.6.6); however:
  Package libgail17 is not installed.
 gyachi depends on libjasper-1.701-1 (>= 1.701.0); however:
  Package libjasper-1.701-1 is not installed.
dpkg: error processing gyachi (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gyachi
jippen@black

```

---

### Post by Samhain13 on 2007-10-19
^I get the same dependency problem trying to install the same 1.0.5-1_i386.deb.

---

### Post by loell on 2007-10-19
if i could not convince the developer to have a release tommorow , then i'll build a gutsy CVS deb package sometime later tommorow.

---

### Post by dmneoblade on 2007-10-19
Found libgail18 in the repo, worked just fine.
As far as libjasper... that took some hunting
For impatient people like me, you can install this deb. For more patient ones, wait till tomorrow for the maintainer to deal with it. ~.^

[http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.06_i386.deb)

---

### Post by sabitha on 2007-10-19
> **dmneoblade said:**
> Found libgail18 in the repo, worked just fine.
As far as libjasper... that took some hunting
For impatient people like me, you can install this deb. For more patient ones, wait till tomorrow for the maintainer to deal with it. ~.^

[http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.06_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/j/jasper/libjasper-1.701-1_1.701.0-2ubuntu0.6.06_i386.deb)

thanks....!!! i'm impatient people like you too :)

---

### Post by Samhain13 on 2007-10-20
> **loell said:**
> if i could not convince the developer to have a release tommorow , then i'll build a gutsy CVS deb package sometime later tommorow.

Yey! Thanks dude! :D

---

### Post by loell on 2007-10-22
sorry for the long delay,

 but here it is [gyachi 1.1.0 release candidate deb package for gutsy]("http://www.mediafire.com/?avyn4kzjxmy")

I also have fiesty package in the first post of the thread.

---

### Post by Samhain13 on 2007-10-22
Thanks man! Downloading it now. :D

Ok, as per our chat conversation, here's what I can confirm:
1. Webcam utility works.
2. Personal images and avatars work.
3. Smiley theme animations work also.

Will be trying out file transfers later.
Cheers! :D

[edit]
File transfers are working too.

---

### Post by arethz on 2007-10-22
Amazing! What a rapid production! I will try it now.. Thanks dude! :popcorn:

---

### Post by loell on 2007-10-22
thanks for the feedbacks :)

---

### Post by andoty_jazz on 2007-10-22
Loelle dude. Idol. Thank you for the update.

Your rock!!! :guitar:

---

### Post by loell on 2007-10-22
np :)

---

### Post by nswint on 2007-10-27
The video feature isn't working in the gutsy release. 

File transfer is working.  I sent a 160 mb file over it.  Voice chat appears to be working  I got a couple of seqfaults.  

gyachivoice[22906]: segfault at 0000000000000000 rip 00000000f75da3f0 rsp 00000000ffda0524 error 4


I'll have to test more.  On 1.0.5 the video feature worked with my logitech quickam using the  gspca drivers

---

### Post by nswint on 2007-10-28
> **nswint said:**
> The video feature isn't working in the gutsy release. 

File transfer is working.  I sent a 160 mb file over it.  Voice chat appears to be working  I got a couple of seqfaults.  

gyachivoice[22906]: segfault at 0000000000000000 rip 00000000f75da3f0 rsp 00000000ffda0524 error 4


I'll have to test more.  On 1.0.5 the video feature worked with my logitech quickam using the  gspca drivers

There was a problem with gyachi-upload  I had to run getlibs.. I"m running on an amd64 processor

/usr/local/share/gyachi/gyachi-upload: error while loading shared libraries: libjasper.so.1: cannot open shared object file: No such file or directory


That portion is resolved but it appears that gyachi-upload is making weird calls to v4l2

[67085.119065] ioctl32(gyachi-upload:23948): Unknown cmd fd(15) cmd(803c7601){t:'v';sz:60} arg(080591e0) on /dev/video1
[67085.189222] ioctl32(gyachi-upload:23948): Unknown cmd fd(15) cmd(400e7607){t:'v';sz:14} arg(0805922c) on /dev/video1


It works fine with my v4l bttv card on /dev/video0

---

### Post by nswint on 2007-10-28
Also in the buddy list window there when you select the friends xx / online xx button the dropdown reads: show all ofline buddies, show only offline buddies in the online group, don't show offline buddies.

The first two do the exact same thing.  Possibly it should be for the second option only show online buddies in the online group. 

Currently there is no offline group.  All buddies are listed in the online group and only go away when you select the don't show offline buddies option.

---

### Post by loell on 2007-10-28
> **nswint said:**
> The video feature isn't working in the gutsy release. 

File transfer is working.  I sent a 160 mb file over it.  Voice chat appears to be working  I got a couple of seqfaults.  

gyachivoice[22906]: segfault at 0000000000000000 rip 00000000f75da3f0 rsp 00000000ffda0524 error 4


I'll have to test more.  On 1.0.5 the video feature worked with my logitech quickam using the  gspca drivers

no worries, the voice chat bug has already been resolved yesterday in the CVS.

---

### Post by loell on 2007-10-28
> **nswint said:**
> There was a problem with gyachi-upload  I had to run getlibs.. I"m running on an amd64 processor

/usr/local/share/gyachi/gyachi-upload: error while loading shared libraries: libjasper.so.1: cannot open shared object file: No such file or directory


That portion is resolved but it appears that gyachi-upload is making weird calls to v4l2

[67085.119065] ioctl32(gyachi-upload:23948): Unknown cmd fd(15) cmd(803c7601){t:'v';sz:60} arg(080591e0) on /dev/video1
[67085.189222] ioctl32(gyachi-upload:23948): Unknown cmd fd(15) cmd(400e7607){t:'v';sz:14} arg(0805922c) on /dev/video1


It works fine with my v4l bttv card on /dev/video0

hmm this is interesting, are you running ubuntu 64 bit?

since your webcam is using an spca dirver, can you confirm that it works on camorama or xawtv in gutsy?

this might be an architecture issue.

---

### Post by AndyLovesLinux on 2007-10-28
are there no xmms plugins?

---

### Post by Inxsible on 2007-10-28
> **loell said:**
> hmm this is interesting, are you running ubuntu 64 bit?

since your webcam is using an spca dirver, can you confirm that it works on camorama or xawtv in gutsy?

this might be an architecture issue.So are you saying gyachi does not work on 64 bit architecture ?

I would really like to use this, but it should work on 64 bit Gutsy :(

---

### Post by loell on 2007-10-28
> **Inxsible said:**
> So are you saying gyachi does not work on 64 bit architecture ?

I would really like to use this, but it should work on 64 bit Gutsy :(

it does, if the voice chat with wine is stripped out.

and of course it should be compiled for 64 bit.

---

### Post by Inxsible on 2007-10-28
> **loell said:**
> it does, if the voice chat with wine is stripped out.

and of course it should be compiled for 64 bit.
i wanted to use the voice chat feature. But i don't get 'voice chat with wine'. Do you need wine to be able to voice chat?

I am sorry, I am a bit confused here.

In other words, i want to use gyachi to connect to yahoo users and be able to voice chat (pc-to-pc calls) and use webcam. Can I do this without wine?

I don't mind compiling from source, if I have to.

---

### Post by loell on 2007-10-28
> **Inxsible said:**
> i wanted to use the voice chat feature. But i don't get 'voice chat with wine'. Do you need wine to be able to voice chat?

I am sorry, I am a bit confused here.

In other words, i want to use gyachi to connect to yahoo users and be able to voice chat (pc-to-pc calls) and use webcam. Can I do this without wine?

I don't mind compiling from source, if I have to.

ah i see now what you'd like to do , the "voice chat" is the capability to  
talk in public chat room which has wine component inside it, this is one blocking feature  that prevents it from compiling in 64 bit, not unless it is remove before compile time. the webcam feature is native so it not a problem in 64 bit.

the pc to pc call, or VOIP capability, is not available yet, you can achive this by using a sip softphone ie (ekiga , gizmo) then call through gtalk2voip service to a yahoo user, more info at gtkalk2voip.com

---

### Post by Inxsible on 2007-10-29
> **loell said:**
> ah i see now what you'd like to do , the "voice chat" is the capability to  
talk in public chat room which has wine component inside it, this is one blocking feature  that prevents it from compiling in 64 bit, not unless it is remove before compile time. the webcam feature is native so it not a problem in 64 bit.

the pc to pc call, or VOIP capability, is not available yet, you can achive this by using a sip softphone ie (ekiga , gizmo) then call through gtalk2voip service to a yahoo user, more info at gtkalk2voip.com
Thanks for the info loell. 

and keep up the good work !! :D

---

### Post by nswint on 2007-10-31
Yup  2.6.22-14-generic x86_64

The camera worked in the last release 1.05 I think without issue.. here's a horrible color unbalanced image

camorama -d /dev/video1

---

### Post by loell on 2007-10-31
i see, 

since you are in x86_64?

in the last 1.0.5 release, did you actually install the 32 bit package? 
 i think you cannot install it, not unless you installed a 64bit package of gyachi, as i know there was one in dapper to edgy.

---

### Post by nswint on 2007-11-01
I used getlibs on the 32 bit package

---

### Post by loell on 2007-11-01
i am not familiar with the workings of getlibs :(

but in any case, if it did work for you in 1.0.5 version, typicaly it should still work, as the webcam code of gyachi hasn't change since then. perhaps this is ubuntu 64 dirvers? or getlibs way of getting the 32 bit dependencies?

---

### Post by nswint on 2007-11-01
It could very well be the gspca drivers.

---

### Post by nswint on 2007-11-01
does gyachi-upload call upon v4l or v4l2?

---

### Post by loell on 2007-11-02
> **nswint said:**
> does gyachi-upload call upon v4l or v4l2?

yeah, it does.

---

### Post by jinx31 on 2007-11-04
Hi - I'm trying to download the 1.1.0 deb package for gutsy, but the link in the first message in this thread comes back saying "No servers available with specified file".

Is there somewhere else I can get this file?  Thanks!

** - I tried again tonight and it worked.

---

### Post by Felson on 2007-11-06
I have tried installing the 32bit version on my 64bit OS, and I got that to work just fine. But I haven't been able to test the video/voice yet. Heres a quick how-to. 

```

cd ~
mkdir lib_extract
cd lib_extract
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-3_i386.deb
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/libg/libgtkhtml2/libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb
sudo dpkg -x libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb .
sudo dpkg -x libjasper1_1.900.1-3_i386.deb .
cd usr/lib
sudo cp * /usr/lib32/
cd ~
sudo rm -rf lib_extract

mkdir gyachi_extract
cd gyachi_extract
wget http://download209.mediafire.com/zt4moceomglg/avyn4kzjxmy/gyachi_1.1.0-1_i386_gutsy.deb
sudo dpkg -x gyachi_1.1.0-1_i386_gutsy.deb .
cp -rp usr /
cd ~
sudo rm -rf gyachi_extract

```

Posting this so others can play to. I may be running 64bit OS, but I am more interested in my apps working then I am in them working as 64bit... If this works for you, please post your trials here. I am interested in if this get voice to work, as I can't test it ATM.

---

### Post by loell on 2007-11-07
Hi all, i've updated the first post and link to reflect the official release,

you can download this gutsy deb, directly

at [http://downloads.sourceforge.net/gyachi/gyachi_1.1.0-1_i386_gutsy.deb?modtime=1194233326&big_mirror=0]("http://downloads.sourceforge.net/gyachi/gyachi_1.1.0-1_i386_gutsy.deb?modtime=1194233326&big_mirror=0")

now the codecs are already separated for some good reasons, if you would like to have voice chat in rooms

install this codecs  [http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0]("http://downloads.sourceforge.net/gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0")

---

### Post by Nicole on 2007-11-08
Does this new release support webcams that use v4l2? My laptop comes with an inbuilt cam that does use v4l2, you see, and so far the only thing I've been able to get to work with it is Ekiga; yahoo is where I'd want to use it most though, so it would be fabulous if gyachi did work with it!

Thanks for all your help,

N

---

### Post by loell on 2007-11-08
sadly not yet :( , though this has already landed on the developers todo list by using gstreamer to get most of the compatible webcams in the linux land.

---

### Post by nswint on 2007-11-08
> **Nicole said:**
> Does this new release support webcams that use v4l2? My laptop comes with an inbuilt cam that does use v4l2, you see, and so far the only thing I've been able to get to work with it is Ekiga; yahoo is where I'd want to use it most though, so it would be fabulous if gyachi did work with it!

Thanks for all your help,

N

No luck with  v4l2 with gyachi for me.. anyone else care to chime in?

---

### Post by nswint on 2007-11-08
This method does not work and will only lead to more problems on the 64-bit kernel


BTW I've made a post to the gyachi forum on SF.  More problems trying to run the 64-bit version.  You get no text .. just blocks


(gyachi:3299): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(gyachi:3299): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(gyachi:3299): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: Failed to load Pango module '/usr/lib/pango/1.6.0/modules/pango-basic-fc.so' for id 'BasicScriptEngineFc'

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: /usr/lib/pango/1.6.0/modules/pango-basic-fc.so: wrong ELF class: ELFCLASS64

(gyachi:3299): Pango-WARNING **: pango_shape called with bad font, expect ugly output

(gyachi:3299): Pango-WARNING **: pango_font_get_glyph_extents called with null font argument, expect ugly output


> **Felson said:**
> I have tried installing the 32bit version on my 64bit OS, and I got that to work just fine. But I haven't been able to test the video/voice yet. Heres a quick how-to. 

```

cd ~
mkdir lib_extract
cd lib_extract
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-3_i386.deb
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/libg/libgtkhtml2/libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb
sudo dpkg -x libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb .
sudo dpkg -x libjasper1_1.900.1-3_i386.deb .
cd usr/lib
sudo cp * /usr/lib32/
cd ~
sudo rm -rf lib_extract

mkdir gyachi_extract
cd gyachi_extract
wget http://download209.mediafire.com/zt4moceomglg/avyn4kzjxmy/gyachi_1.1.0-1_i386_gutsy.deb
sudo dpkg -x gyachi_1.1.0-1_i386_gutsy.deb .
cp -rp usr /
cd ~
sudo rm -rf gyachi_extract

```

Posting this so others can play to. I may be running 64bit OS, but I am more interested in my apps working then I am in them working as 64bit... If this works for you, please post your trials here. I am interested in if this get voice to work, as I can't test it ATM.

---

### Post by Inxsible on 2007-11-08
> **Nicole said:**
> Does this new release support webcams that use v4l2? My laptop comes with an inbuilt cam that does use v4l2, you see, and so far the only thing I've been able to get to work with it is Ekiga; yahoo is where I'd want to use it most though, so it would be fabulous if gyachi did work with it!

Thanks for all your help,

NI know this is a gyachi thread, but I can use my built in webcam in Kopete and connect to yahoo.

you might wanna try that out.

---

### Post by loell on 2007-11-08
yep, when it comes to yahoo/webcam/v4l2 kopete is a contender

---

### Post by rold50 on 2007-11-12
I have a logitech Quick cam that uses QC-usb driver. My webcam is v4l1

The webcam works when I test it using camorama but with gyachi, I only see a black screen.

How do I fix this problem?

---

### Post by wersdaluv on 2007-11-19
I can't broadcast my webcam. Whenever I try to, an error message comes out. Sometimes, I can view my webcam image when I start my webcam then the error message comes out when I press "Broadcast." Sometimes, when I start my webcam, the error message comes out immediately. 

I attached the snapshot of the error message. :D

---

### Post by Samhain13 on 2007-11-25
Hi. I'd also want to report an error when trying to start my webcam:

```

GThread-ERROR **: GThread system may only be initialized once.
aborting...

```

---

### Post by loell on 2007-11-25
does this happen every time you activate your webcam?

---

### Post by Samhain13 on 2007-11-26
No. Only when trying to activate it using Gyachi.
I can use my webcam with Camorama and VLC.

---

### Post by loell on 2007-11-26
can you reinstall the app? gthread error is  a threading error which is a bit strange. let me know if the problem still persist after reinstallation.

---

### Post by rold50 on 2007-11-26
Hi Loell,

do you know how i can fix my webcam?
All I see is a black screen when I start my webcam in gyachi.
I can see other's webcam but they also only see a black screen when they try to view my webcam.
My webcam uses Vl41 and it works with camorama.

---

### Post by loell on 2007-11-26
> **rold50 said:**
> Hi Loell,

do you know how i can fix my webcam?
All I see is a black screen when I start my webcam in gyachi.
I can see other's webcam but they also only see a black screen when they try to view my webcam.
My webcam uses Vl41 and it works with camorama.

I probably can't be much of help , this is probably a uvc base webcam driver?

---

### Post by rold50 on 2007-11-26
I have the QCM-USB driver for my webcam.

I'm using a logitech quick cam.

---

### Post by Samhain13 on 2007-11-27
Loell: Yup I tried reinstalling, still got the same error.
I downloaded the package again, reinstalled, still the same.

Oh, and like rold50, I can receive webcam streams from friends. But I am unable to start mine.
I tried with Kopete and I was successful in sending and receiving webcam streams but for some reason, Kopete takes up too much CPU power (maybe because I'm running it in Gnome, I don't know). I would prefer to still use GyachI though.

:)

---

### Post by stanz on 2007-12-20
Hi All,
I'm running Gutsy 7.10, and I tried to install gyachi-codecs with gdebi and it errors out with conflicts to the already installed w32codecs. Breezing thru this thread--I didn't notice any one else with this error.
I already posted on sourceforge, typing here for others.
Any work around?
Will it always be a conflict?
Thanks in advance !

---

### Post by stanz on 2007-12-20
Well, I got some interesting info on [SourceforgeGyachi]("https://sourceforge.net/forum/forum.php?thread_id=1896937&forum_id=533967")
Now just to run it and see how it all works.

---

### Post by wersdaluv on 2007-12-20
What can we do to fix uvc webcams? :)

---

### Post by loell on 2007-12-20
> **wersdaluv said:**
> What can we do to fix uvc webcams? :)

gstreamer is the way.

---

### Post by wersdaluv on 2007-12-20
> **loell said:**
> gstreamer is the way.

Uhum. What exactly can I do? :D

---

### Post by loell on 2007-12-20
from a users point, none :(

gstreamer is a multimedia framework , so coders would have to code it.

in any case gstreamer for gyachi will be a pain on the neck during the integration phase.

---

### Post by jrusso2 on 2007-12-20
Every time I try to post a message into yahoo chat with Gyachi it just crashes>
does anyone have a fix for this?

---

### Post by loell on 2007-12-20
when did this started?

---

### Post by wersdaluv on 2007-12-21
I found out that the version of my Logitech Quickcam Orbit/Sphere is pwc. I'm wondering why it worked in Feisty while the webcam is choppy in Gutsy. You think, it's a kernel issue?

---

### Post by loell on 2007-12-21
> **wersdaluv said:**
> I found out that the version of my Logitech Quickcam Orbit/Sphere is pwc. I'm wondering why it worked in Feisty while the webcam is choppy in Gutsy. You think, it's a kernel issue?

maybe its just a driver / module issue, you can try  recompiling/reinstalling the pwc driver, and see if there any difference with the webcam images.

```


apt-get source pwc-source

cd pwc-10.0.12-rc1+final/

make

sudo make install


```

---

### Post by wersdaluv on 2007-12-22
> **loell said:**
> maybe its just a driver / module issue, you can try  recompiling/reinstalling the pwc driver, and see if there any difference with the webcam images.

```


apt-get source pwc-source

cd pwc-10.0.12-rc1+final/

make

sudo make install


```

Still choppy but less choppy! yeyyy!!!

Mmmm...

What else can I do? :D

:guitar:

:KS

---

### Post by loell on 2007-12-22
uhmm, you could clean the lense? ;) j/k.

heheh, i'm out of idea.

---

### Post by neaghi on 2008-01-04
hi all
i'm from Romania pls escuse my english...I want to know what is the latest version of gyachi-sidetrack, and if somebody know if in Sindos Pesta distribution the gyachoo settings is unlocked..10x.:)

---

### Post by loell on 2008-01-04
the official gyachi version is already v1.1.10 , a lot had happened during the holiday season, themes are now supported so anyone can make a yahoo messenger like theme if they like.

most of gyachi-sidetrack's feature is also now availble in the official gyachi version.

---

### Post by _sluimers_ on 2008-01-11
Hi there!
I have webcam troubles with Gyachi. I use a Hercules Deluxe camera and it works fine in kopete and xawtv, but not well in camorama or Gyachi. 

Gyachi shows the webcam like a movie that doesn't have the right framerate.
Part of the top goes to the bottom and it's continiously moving up and down.

---

### Post by shadowtroopers on 2008-01-17
hi, 
i'm using gyachi 1.1.10, under xubuntu gutsy machine. My gyachi was installed by using gdebi package installer. Just want to know, how to compile gyachi from cvs?. I just like to test any new release version of gyachi. I prefer step by step.

Thanks.

---

### Post by BatsotO on 2008-02-01
hi loell, can u recommend me some good compatible ( and most importand is cheap) webcams that i can use with gyache? I have z-star cams but no go.  And since we are geographicly not far, i think the models wont be that much different. Thank you in advance.
And one more thing, I still cant see my friends buddy image in the buddy list, it was shown in pidgin but pidgin is bad for public pc. 
Thank you again, Best Regard

---

### Post by loell on 2008-02-01
i find logitech webcams to be the most compatible webcam for gyachi,  even the devs use the brand, and mine is the old logitech quickcam express II. ;)

---

### Post by sabitha on 2008-02-03
> **loell said:**
> the official gyachi version is already v1.1.10 , a lot had happened during the holiday season, themes are now supported so anyone can make a yahoo messenger like theme if they like.

most of gyachi-sidetrack's feature is also now availble in the official gyachi version.
i can't find gyachi v1.1.10 still v1.1.0 on there:confused:. where i can download for v1.1.10

---

### Post by loell on 2008-02-03
its in the CVS yet, and it is still considered a minor version which is now 1.1.25 as of this writing, i may build a deb package whenever** yahoo photos** is ready for testing.

---

### Post by technomagik on 2008-02-04
The webcam works when I use kopete, but I can't stand kopete. It also works with a stand alone webcam application called cheese. It does not work with egika or VLC. 

When I use it with Cheese it uses "v4l2src" and works great. The webcam is reported to work with uvc (c'moooon gstreamer coding :))

When I try to use it in gyache 1.10 I get the error:

An error occured at ioctl 'VIDIOSCIPT'
Could not set camera properties.

I also get a simultaneous error window that says
Error while querying mmap-buffers.

I tried running the webcam with GyachE 1.07 with webcam utilities and pyvoicechat (came with the rpm, which i converted to deb with alien) and received a different error, but it was simpler and basicly said this (i dont remember the exact words):

Could not receive webcam image.

Gyache 1.07 showed that it was using the v4l1 driver, but I believe this camera is supposed to use the v4l2 driver, is there a way I can make gyache 1.10 use the v4l2 driver? (assuming it is also attempting to use v4l1, like 1.07)

The light on the webcam blinks twice after i click OK on the error messages from either 1.07 or 1.10, so the proper device (/dev/video0) is selected.



The webcam is a built in webcam in the LCD of my laptop. It is a VGA 640x480 webcam. It is in a xps m1330 laptop.


Any help would be GREATLY appreciated.

---

### Post by loell on 2008-02-04
yes, unfortunately this is a rising issue for some time now, currently gyachi only supports v4l1 , you could compile it as v4l2 but this doesn't seem to work either.

the solution is to use gstreamer as one of its component, this may be implemented after the project is done with yahoo photos.

---

### Post by ComputerHermit on 2008-02-07
I can't seem to get the voice to work.
I downloaded gyachi_1.1.0-1_i386_gutsy.deb gyachi-codecs.deb
Am I not doing something right?

---

### Post by shadowtroopers on 2008-02-12
> **ComputerHermit said:**
> I can't seem to get the voice to work.
I downloaded gyachi_1.1.0-1_i386_gutsy.deb gyachi-codecs.deb
Am I not doing something right?

In some cases, gyachE had a problem with wine codecs. Have you tried to reinstall the codecs?

---

### Post by ComputerHermit on 2008-02-13
> **shadowtroopers said:**
> In some cases, gyachE had a problem with wine codecs. Have you tried to reinstall the codecs?
I got it I dident have the port open

---

### Post by ComputerHermit on 2008-02-13
Gyachi rocks thanks

---

### Post by _sluimers_ on 2008-02-14
> yes, unfortunately this is a rising issue for some time now, currently gyachi only supports v4l1 , you could compile it as v4l2 but this doesn't seem to work either.

the solution is to use gstreamer as one of its component, this may be implemented after the project is done with yahoo photos.

I sure hope it will. I have the same problem, I think.

---

### Post by amrith on 2008-02-17
How to start voice chat?
whenever I click voice chat .It says enabled 
cant ppl who have yahoo msngr use it?

---

### Post by hanzj on 2008-02-20
Hello,
Is it possible to make  computer -to- regular phone line calls, ([http://voice.yahoo.com/](http://voice.yahoo.com/), also known as "Phone Out")?

I still have some money on my yahoo voice account.
Thank you.

---

### Post by loell on 2008-02-20
not possible at the moment.

you may want to look at 

1.Ekiga
2. Gizmo
3. Skype for linux

---

### Post by pburn on 2008-03-07
I am using GyachE Improved 1.1.0 ...but I am being booted by a nut in one of the chat rooms...how can I prevent someone from booting me ??

The following are the messages displayed in GyahE before being disconnected from yahoo.

  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0011' ( k_ss0011 ) **
  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0012' ( k_ss0012 ) **
  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0013' ( k_ss0013 ) **
  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0014' ( k_ss0014 ) **

  ** WARNING: TOO MANY SOUND EVENTS HAVE BEEN PLAYED TOO QUICKLY (Possible Flood or Boot Attack from a malicious Yahoo user?) -  Sound Events will be temporarily disabled for 2.5 minutes to help protect your system.
  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0015' ( k_ss0015 ) **
  ** [GyachE-I] Ignored PM from User NOT in the Room ( "" )  : 'k_ss0016' ( k_ss0016 ) **
    ** You have been disconnected from Yahoo! [Probably booted...reconnecting] **
  Disconnected from Yahoo!    See Ya!  Online for  0 : 00 : 22

    ** You have been disconnected from Yahoo! [ Error receiving from socket: 0 ] **

---

### Post by technomagik on 2008-03-13
I have two questions.

1. I am having way too much trouble trying to compile gyachE, I really want to try using it with --enable-v4l2. Could you please post a .deb file to install it? 

2. I noticed theres a photoshare RPM package. I tried converting it with alien. It would not install. Could you please post a .deb file for this? 

It would be very helpful. I'd like to test the photoshare plugin, and I'd be happy to report my experiences in detail for development help.

I'm running Mint Linux daryna 4. Any ubuntu packages will work fine, since it is based off of Ubuntu Gutsy.

---

### Post by loell on 2008-03-15
updated deb package for newer version. see first post/page :)

---

### Post by kung fu buntu on 2008-03-21
I installed your deb package on my chroot'ed ia32 Debian.
Let us hope it works with my Logitech QuickCam Fusion.

I don't know if this matters or not, but it worried me a bit when I tried to install it:
dpkg: warning - unable to delete old directory `/usr/local/share': Directory not empty
dpkg: warning - unable to delete old directory `/usr/local': Directory not empty
dpkg: dependency problems prevent configuration of gyachi:

It tries to delete those dirs??? Very weird...

BTW, was this built with V4L2?

thank you

---

### Post by loell on 2008-03-21
i don't know if it would work with chrooted debian, perhaps try the debian sid pacakge in gyachi's download page, this build did not enabled v4l2, but did gyachi v4l2 work for you anyway?

---

### Post by kung fu buntu on 2008-03-21
@loell 
when using your .deb I had no sucess, as when I try to start my webcam I get an error message:
[B]GyachI (webcam broadcaster)
Error while querying mmap-buffers.[/B]

I don't think the chroot will be a problem since hardware devices work in a transparent way IIRC.
Besides, Gyachi detected my tvcard with no problems (off course there was no TV in gyachi :p).

About the other .deb packages: as far as I can see, you made the other deb packages as well... so no point in there :p

> but did gyachi v4l2 work for you anyway?
I don't have that build :p
I will try building it again (I tried before but was doing it on my amd64 systems instead of the chroot).
But nonetheless, would it be possible for you to make a deb package with V4L2 enabled?

---

### Post by kung fu buntu on 2008-03-21
NOOOOOOOOOOOOOOOOOoooooooooooooooooooooooo :'(
It doesn't work!
After sooooo many hours around this....

./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --enable-plugin_photosharing --disable-plugin_xmms

I still get the same error message :(
That means V4L2 is broken :(


And Gyachi is broken in respect to xmms, because there is no longer a xmms package in Debian, only xmms2. I was able to build and run because I had old packages installed.
During configure this is the error message:
[B]checking for /usr/include/xmms/xmmsctrl.h... no
configure: error: cannot find include file xmms/xmmsctrl.h. Perhaps you need to install the xmms development package?[/B]

ahhhhhhhh.... this is so demoralizing...



EDIT:
[UVC V4L2 support]("https://sourceforge.net/forum/forum.php?thread_id=1955929&forum_id=533967")
when gyachi uses gstreamer for accessing video devices then most likely this won't be a problem. probably this will be implemented at next --> next milestone release ( around 1.3 ) hopefully.

lol.... just noticed, it was you who said this loell

When will that be? 1 month? 6 months?
Is there any way to help in the coding process?
aMSN supports V4L2 UVC webcams (although it's in tcl/tk... not sure if anything can be re-used at the concept level)



EDIT2:
[V4L2 status]("https://sourceforge.net/forum/forum.php?thread_id=1982023&forum_id=533966"): "This is probably one of the things I'll be looking at sometime later this year. No fixed time-frame (I happen to have a day job that doesn't include developing gyachi :( ) "

That means no webcam support for some of us.... including me :(

---

### Post by kung fu buntu on 2008-03-23
There may be some good news... I haven't tested this yet but...

In [this blog]("http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html") the author explains how to get Flash to work with V4L2 devices, whereas Flash only supports V4L (one).

Maybe this can be used to get webcams working with Gyachi as well...


If anyone tries, please let me know.

---

### Post by loell on 2008-03-23
good find, that might just work :)

---

### Post by kung fu buntu on 2008-03-24
:(

I tried using it but no luck... this is the error message I got in Gyachi:
"An error occured at 'ioctl VIDIOCGCAP'. 
Wrong device." 
And another one for VIDIOCSPICT. 
 
Any insights on this? 

Thank you

---

### Post by loell on 2008-03-24
i don't have any idea actually, as I don't have a v4l2 webcam :(

but this might contribute something,A while back, I  tried [avld]("http://allonlinux.free.fr/Projets/AVLD/") to stream some video file to a webcam device and it works in gyachi.

---

### Post by ComputerHermit on 2008-03-24
I dont have a cam but my mane problem was the voice I did not have the ports open in  firewall script
 I think GyachI is great

---

### Post by kung fu buntu on 2008-03-24
> **loell said:**
> i don't have any idea actually, as I don't have a v4l2 webcam :(

but this might contribute something,A while back, I  tried [avld]("http://allonlinux.free.fr/Projets/AVLD/") to stream some video file to a webcam device and it works in gyachi.

:mad:
I hate this :(

AVLD works fine by itself. I was able to stream a video and open it with mplayer.
But Gyachi still gives the same error messages. And flash doesn't work as well.

ahhhh linux.... you drive me crazy...

---

### Post by loell on 2008-03-24
I was thinking more of using the avld and pipe a mencoder with v4l2, ie

```
mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video0 -o /dev/Video1
``` 

ofcourse you would have to set gyachi to use Video1, I just don't know if this could work

---

### Post by kung fu buntu on 2008-03-24
I don't quite understand it... nor was able to get it to work.

Using AVLD by itself works fine. This is what I executed:
[B]echo "width=320 height=240 fps=14" > /dev/video1
mencoder video.avi -nosound -ovc raw -vf format=bgr24 -of rawvideo -o /dev/video1
mplayer tv:// -tv "driver=v4l:device=/dev/video1:noaudio:outfmt=rgb24:width=320:height=240"[/B]

Note that I'm using /dev/video1 because /dev/video0 is my tv card, and there are no more devices because the cam is unplugged.

I then tested Gyachi by using /dev/video1 and it gives me those errors. I can open /dev/video0 (my tv card) in Gyachi without problems.
This should have worked this way... The video should appear in Gyachi... but it didn't :(



Now, trying what you said:
**mencoder tv:// -tv driver=v4l2:width=320:height=240:device=/dev/video2 -o /dev/video1**
Where video1 is avld and video2 is my webcam, I get this output:
```
success: format: 9  data: 0x0 - 0x0
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (046d:08ca)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: MJPEG
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument
Error: Cannot set norm!
Selected input hasn't got a tuner!
Audio block size too low, setting to 16384!
Floating point exception 
```

---

### Post by loell on 2008-03-24
sigh :(

I gues it doesn't work. 

was looking into this too, [http://forum.skype.com/index.php?showtopic=108225]("http://forum.skype.com/index.php?showtopic=108225") .
again, my lack of a v4l2 webcam prevents me from doing any v4l2 related  test.     :(

did you ever consider kopete?

---

### Post by kung fu buntu on 2008-03-24
I'm surprised... kopete worked.
I had tried it before but the image was a complete mess...
I tried it now, the image was a complete mess (although in a different way) but I was able to fix it in the config tabs.
It is nice I can have it working.

I never used kopete (for msn I use aMSN) so I'll have to see how it works for a real webcam chat session... bidirectional synchronized audio and video.

Still, Gyachi seems to be a lot better than Kopete... and another reason for solving this problem would be that I would also be able to use my webcam on flash websites... and this would be *really* usefull for me.

So, if anyone knows how to solve this, please go ahead... I appreciate it.

---

### Post by kung fu buntu on 2008-03-24
**I [COLOR="Red"]almost[/COLOR] have Gyachi working!**

In the [linux flash webcam headache site]("http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html") I mention previously there is the solution to the V4L1-V4L2 issue.
It wasn't working with me because my system is an amd64 and the flash plugin is 32 bits. But this is now solved thanks to the author. I now have webcam support in flash :D


As for Gyachi, I tried changing the [http://www.swift-tools.net/Blog/flashcam.c]("http://www.swift-tools.net/Blog/flashcam.c") code to open the V4L2 device using a RGB24 palette and write to V4L1 using the same palette (simple copy). As well as the resolution to 320*240.

This has to be done because the capture prog is prepared for flash.

Unfortunately I get a black screen in Gyachi webcam. I can set the camera parameters but it always stays black.

Do you have any idea on what might be wrong here?
I checked gyachiupload-v4l.c and it expects RGB24 (even though it iterates through other palettes but that didn't seem to work).

Thanks.

---

### Post by loell on 2008-03-24
in gyachiupload-v4l.c there's this **set_v4l2control ** and **get_v4l2control**

these methods will only be available if gyachi is compiled with --enable-v4l2

try recompiling gyachi with v4l2 enable, if this could not control your webcam properties, its probably because gyachi could not control the loop back device.

---

### Post by kung fu buntu on 2008-03-24
I don't understand what you mean.

All this trouble is because my webcam doesn't work with Gyachi. Because the UVC driver only supports V4L2.
AFAIK Gyachi V4L2 support isn't perfect, that is why not all webcams work.

When I initially tried using Gyachi before, Gyachi sent errors messages, I never got to the webcam properties.
And yes... at that time I had recompiled Gyachi with v4l2 support. BTW, it's the built I am using.


I guess you're right on the loopback not allowing to set webcam properties. However the image doesn't get black in Flash apps.... So you should also see something in Gyachi... and not pure black... I mean RGB=000

---

### Post by loell on 2008-03-24
> **kung fu buntu said:**
> 
I guess you're right on the loopback not allowing to set webcam properties. However the image doesn't get black in Flash apps.... So you should also see something in Gyachi... and not pure black... I mean RGB=000

yeah, it should show something other than black, but somehow gyachi is setting its own default rgb, i'm not even sure if its the rgb or just gyachi doesn't understand the format that's been streamed from the loopback device. 

I  think the right person with this knowledge in gyachi is **Stefan Sikora** -- (gyachi founder), as he did the v4l2 coding while greg --(current dev)  hasn't venture in this part of the  code yet. might be worth if asking stefan.

---

### Post by ComputerHermit on 2008-03-26
yahooo yahoooo

 GyachI is great I enjoy it alot ty anyway I got booted today it took them like 6 times :lolflag: of a flood some bot thing pakiebot something was the screen name 
like that but the voice was still going that was great and I was able to rejoin the chat I was thinking of is their some way I can filter the flood or maybe use a different server or some input off of this community might help
 I do have the  Flooder/Booter List but I'm unable to add any name's?

---

### Post by loell on 2008-03-26
yeah, gyachi is really vulnerable at flooding and boot codes, but i haven't found anyone who had some level of expertise in boot codes, the flood protection in gyachi is rather old and buggy it would be nice though to have some filter or protection from these kind of things,

---

### Post by shadowtroopers on 2008-03-27
Yup, agreed with you loell, the boot protection wasn't good enough. Nowadays it' more and more complex than before. Sometimes it's too slow to respond when there's a flood by someone in the room. I'm wondering whether is there any suggestion on the firewall part that we can improve. As for pburn question for being booted, here is my setting. This may won't work on you but for me, it helps a lil bit. On setup option.
1. Protection: ( enable below)
-do not allow anyone who's not friend to add me to their friend list
-do not accept any file
-automatically reject all invitation
-enable basic boot protection
-Accept private message, invite and files only from friends
-enable spam protection
-never auto ignore friends
-suppress multiple consecutive post

2.option tab (enable below)
-Ping every 1 min

Hope that can improved a lil bit. Actually, i didn't enable pre-emptive boot option because it may slow down gyachi respond time when someone booting you. My intention is just to minimize the process time so that gyachi can respond fast when being boot.

---

### Post by kung fu buntu on 2008-03-28
**UVC V4L2 webcam working!**
My original post is at [https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966](https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966)



I was able to get my Logitech Quickcam Fusion working with Gyachi 1.1.27 on my amd64 system. 
NOTE: for amd64 you need vloopback-1.1.2. 
I am yet to webcam chat with someone, but I can configure the webcam with no problems. The image quality is superb. 
 
I have built GyachI, on a chroot'ed system, using this config: 
./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --enable-plugin_photosharing --disable-plugin_xmms 
 
 
HOW TO: 
- Get vloopback and flashcam from [http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html](http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html) 
Build it and have it working on your system.
NOTE: it's mandatory to have the kernel module; not the flash application.
 
- build the application in the tarball at [http://rapidshare.com/files/103163006/gyachicam-0.2.tar.gz.html](http://rapidshare.com/files/103163006/gyachicam-0.2.tar.gz.html) 
 
- check the "embedded readme" in the source file

---

### Post by loell on 2008-03-28
nice :) could you just attach the last link from rapidshare here?   rapidshare just quickly expires.  and I would also like to add this in the first post with  your consent and credit of course :)

---

### Post by kung fu buntu on 2008-03-29
Done.

Yes, please add it in to first post, otherwise this would just end up lost here. :)

---

### Post by szandor on 2008-04-09
> **kung fu buntu said:**
> :(

I tried using it but no luck... this is the error message I got in Gyachi:
"An error occured at 'ioctl VIDIOCGCAP'. 
Wrong device." 
And another one for VIDIOCSPICT. 
 
Any insights on this? 

Thank you

after i got to page 25 i knew i should have gone with kopete when i was only invested up to page 6... 

anyway, after reading all this, as well as some of the newer posts at the sourceforge forum, i'm still not sure what all has been integrated with gyachi and which packages i need for chat, video, and voice. or even if any of the v4l2 stuff has been sorted out.

i think i read that someone was not able to get the vloopback driver to work with flash or gyachi. i was able to build the frame forwarder and driver on my m1330. 

05a9:7670 OmniVision Technologies, Inc.

i was finally able to get the webcam and microphone working in stickam. then i tried looking for ymessenger, ran across gyachi, had enough time to install the package on the first page, and come up here to work. i'm hoping all this reading wasn't in vain. by the way, once you get the v4l module to work with v4l2, don't forget to kill the frame forwarder if you use an application that needs to use the v4l2 driver.

---

### Post by palwpra on 2008-04-12
Hi,
I am trying to install gyachi on fesity. The link on the first page is only for gutsy and I couldn't find the link for the feisty package and when I tried installing using the gutsy .deb file. I am getting the error Dependency  is not satisfiable: libasound2. so is there a  version for feisty?
Any help is really appreciated.

Thanks,
palwpra

---

### Post by loell on 2008-04-12
there is an old package for ubuntu edgy in gyachi's download area that could be installed for fiesty. i couldn't make a newer package for fiesty, as i only have gutsy and  hardy on my machine.

---

### Post by oldHat on 2008-04-17
> **Samhain13 said:**
> Hi. I'd also want to report an error when trying to start my webcam:

```

GThread-ERROR **: GThread system may only be initialized once.
aborting...

```

I started having the same problem after I enabled Assistive Technology support.  After I disabled it (System/Preferences/Universal Access/Assistive Technology preferences), my cam worked fine.

While troubleshooting, I upgraded from 1.1.0 to 1.1.26.  The problem continues into 1.1.26 but disappeared when I made the change I described.

---

### Post by Oddvar on 2008-04-18
> **Felson said:**
> I have tried installing the 32bit version on my 64bit OS, and I got that to work just fine. But I haven't been able to test the video/voice yet. Heres a quick how-to. 

```

cd ~
mkdir lib_extract
cd lib_extract
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/j/jasper/libjasper1_1.900.1-3_i386.deb
wget http://ubuntu.cs.utah.edu/ubuntu/pool/main/libg/libgtkhtml2/libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb
sudo dpkg -x libgtkhtml2-0_2.11.1-0ubuntu1_i386.deb .
sudo dpkg -x libjasper1_1.900.1-3_i386.deb .
cd usr/lib
sudo cp * /usr/lib32/
cd ~
sudo rm -rf lib_extract

mkdir gyachi_extract
cd gyachi_extract
wget http://download209.mediafire.com/zt4moceomglg/avyn4kzjxmy/gyachi_1.1.0-1_i386_gutsy.deb
sudo dpkg -x gyachi_1.1.0-1_i386_gutsy.deb .
cp -rp usr /
cd ~
sudo rm -rf gyachi_extract

```

Posting this so others can play to. I may be running 64bit OS, but I am more interested in my apps working then I am in them working as 64bit... If this works for you, please post your trials here. I am interested in if this get voice to work, as I can't test it ATM.

>>I tried this. It stop at cd /usr/lib32 (dont exist).
Also I wonder about the periods(.) at the far end of some commands.
This did not work for me.

---

### Post by szandor on 2008-04-23
> **Oddvar said:**
> >>I tried this. It stop at cd /usr/lib32 (dont exist).
Also I wonder about the periods(.) at the far end of some commands.
This did not work for me.

the '-x' is for extract and the '.' is for current directory. if you are user1 and run this in a directory other than user1, say, root, the command will fail.

---

### Post by hhpeter on 2008-04-26
I've been trying to instal gyachi for a couple of days now on ubuntu 8.04
Can somebody please explain what do I do wrong
I download gyachi.tar.gz file
Extract it 
when I enter ./configure it says to check the install file 
there is a long sentence after ./configure I tried to enter that but it still tells me to check install file ???
Please help me

---

### Post by Carlo1973 on 2008-05-01
Hey it's been a LOOOONG time since I've been in here and it seems like Lloel has made some major improvements to Gyachi! Awesome man! Actually the whole Gyachi team needs a pat on the back for keeping this going. It's far superior to Pidgin and Koepete if you ask me. 

I was just wondering where I could actually find the source to Gyachi 1.1.27 that I've seen references to. Honestly what is the official current version available for download (alpha, beta, pre-release, and official release). I'd love to get in on that action. I hear that people have made some headway on figuring out the V4L2 problems with some of the logitech cams (for example: The Orb MP)

If I can find the source so I can just build it that would be cool. either that or having a fully functioning deb with all the needed stuff I need to install with it, ready for Ubuntu Hardy 8.04 LTS (which is what I'm running right now). Think maybe I better just stick to the source and build it fresh with the instructions I've read on here :cool:

Keep me posted!

Carlo

---

### Post by loell on 2008-05-01
hi, i forgot to update this thread, i actually built a hardy package and its in a new thread, as this thread is  already very long.

[http://ubuntuforums.org/showthread.php?t=773802]("http://ubuntuforums.org/showthread.php?t=773802")

---

### Post by ShelJ on 2008-05-13
I too am having problems using webcam.  Here is my cam info:```
Bus 001 Device 002: ID 046d:08b5 Logitech, Inc. QuickCam Sphere
```

and when i try to use webcam in Gyachi this is the error that I get:```
/usr/lib/gyachi/gyachi-upload: error while loading shared libraries: libjasper.so.1: cannot open shared object file: No such file or directory

```

I tried to download libjasper but got an error that it was not found.

P.S.
Ok I found libjasper, i do have it installed with the file listed earlier, so I don't know why I am getting this msg.

---

### Post by loell on 2008-05-14
what ubuntu version are you at?

---

### Post by Script Warlock on 2008-05-22
well this is a -one step at a time- cguro request ko kung may extra time pa pwede sali na natin ang voice chat sa gyachi..

---

### Post by loell on 2008-05-22
> **boyet said:**
> well this is a -one step at a time- cguro request ko kung may extra time pa pwede sali na natin ang voice chat sa gyachi..

eek, your on a thread outside the loco :popcorn:

---

### Post by Script Warlock on 2008-05-22
nyaaaaah......sory nakalimutan ko....cge na nga ot na: bro sali mo na lang sa plano mo ang voice chat ha...:lolflag:

---

### Post by shrinathk87 on 2008-06-24
Hello Sir,

I couldnt find a HOMEPAGE for gyachi... is it NOT under development ? Is there any official site for Gyachi...??

and also, are Gyach, GyachI and GyachE all the same...?

Thank you.

---

### Post by loell on 2008-06-24
yes, google will even find it easily for you. ;)

[http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by shrinathk87 on 2008-06-25
i am sorry to bother you again...

but i dont get one thing...the homepage u sent says the current version is 1.1.0 but at the starting of this thread, u gave a Mediafire file sharing link that says its gyachi 1.1.31 ?

is 1.1.31 a beta version ? or is it that the homepage is not updated ? 
( highly unlikely that homepage is not updated i guess )

Thanks again..

---

### Post by loell on 2008-06-25
close to it, v1.1.31 is a CVS version only, currently the latest CVS version is 1.1.35, you could either choose to install the deb package of this thread which is as you know is 1.1.31 or you compile and install the latest.

---

### Post by linuxfce on 2008-08-22
I used the flashcam method and it works. The problem now is that the image is in 160 x 120 resolution. I have looked all over google, tried the camera properties window (no resolution setting found), and looked in the source files for vloopback and flashcam and found nothing. I am not a developer though, so its very possible I missed something in the source files.

Please help me find a solution to get the cam running at a higher resolution.

If you are going to suggest compiling gyachi with v4l2-enable I have tried desperately, and I mean desperately. 

The error is:
Possibly undefined macro: AM_PATH_GLIB_2_0

I would be so appreciative if you could create a .deb for a v4l2 enabled gyachi-sidetrack. If v4l2-enable puts a resolution setting in the gyachi Camera properties window it may work. The Brightness, Contrast, Hue, all work (though vloopback must be restarted to see changes).

Thanks for your time

---

### Post by loell on 2008-08-22
hi here's the current thread

[http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi")

the deb is compiled with v4l2.

---

### Post by linuxfce on 2008-08-23
Thanks loell I had no idea that it was compiled already with v4l2. I did try it and it didn't give me any options to change the resolution of the cam image.

Any suggestions? :???:

---

### Post by loell on 2008-08-23
> **linuxfce said:**
> Thanks loell I had no idea that it was compiled already with v4l2. I did try it and it didn't give me any options to change the resolution of the cam image.

Any suggestions? :???:

 v4l2 as your webcam is. Is a hit or miss with gyachi and flashcam :(

for what its worth, i just thought that you should know, that the project is waiting for another project(libv4l) to stabilize and go mainstream before it can address this issue.

---

### Post by linuxfce on 2008-08-23
Thanks loell I really appreciate the feedback. I'll keep poking around and if I find something I'll post it here.

---

### Post by ninjamonkey26 on 2008-10-13
> **kung fu buntu said:**
> **UVC V4L2 webcam working!**
My original post is at [https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966](https://sourceforge.net/forum/forum.php?thread_id=1989288&forum_id=533966)



I was able to get my Logitech Quickcam Fusion working with Gyachi 1.1.27 on my amd64 system. 
NOTE: for amd64 you need vloopback-1.1.2. 
I am yet to webcam chat with someone, but I can configure the webcam with no problems. The image quality is superb. 
 
I have built GyachI, on a chroot'ed system, using this config: 
./configure --enable-v4l2 --enable-soundevents --enable-statuspixmaps --enable-wine --enable-plugin_photosharing --disable-plugin_xmms 
 
 
HOW TO: 
- Get vloopback and flashcam from [http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html](http://swifthumors.blogspot.com/2008/03/linux-flash-webcam-headache.html) 
Build it and have it working on your system.
NOTE: it's mandatory to have the kernel module; not the flash application.
 
- build the application in the tarball at [http://rapidshare.com/files/103163006/gyachicam-0.2.tar.gz.html](http://rapidshare.com/files/103163006/gyachicam-0.2.tar.gz.html) 
 
- check the "embedded readme" in the source file

So do I drag and drop the files from that tarball into the webcam directory of the unzipped gyachi? and modify the makefile too?

---

### Post by loell on 2008-10-13
> **ninjamonkey26 said:**
> So do I drag and drop the files from that tarball into the webcam directory of the unzipped gyachi? and modify the makefile too?

you just install it, no unzipping of gyachi's source.

---

### Post by esafwan on 2008-10-30
I'm using Ubuntu Hardy Heron! I cant find a suitable download for mine. Can any body tell me how i can get it for this architecture!

This is the only app. that i have not got in Linux!:(

---

### Post by loell on 2008-10-30
> **esafwan said:**
> I'm using Ubuntu Hardy Heron! I cant find a suitable download for mine. Can any body tell me how i can get it for this architecture!

This is the only app. that i have not got in Linux!:(

what architecture are you running? 32? or 64?

---

### Post by esafwan on 2008-10-31
64 bit

---

### Post by loell on 2008-10-31
> **esafwan said:**
> 64 bit

[https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.48-1~ubuntu11_amd64.deb]("https://launchpad.net/%7Eloell/+archive/+files/gyachi_1.1.48-1~ubuntu11_amd64.deb")

---

### Post by dsdeiz on 2008-12-03
I get this error after trying to start webcam:
```
Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.
```

It was working yesterday when I was using cheese to test my webcam.. Any ideas? :(

---

### Post by loell on 2008-12-03
> **dsdeiz said:**
> I get this error after trying to start webcam:
```
Gyachi (Webcam Broadcaster)
An error occured at 'ioctl VIDIOCSPICT.'
Could not set camera properties.
```

It was working yesterday when I was using cheese to test my webcam.. Any ideas? :(

if you're in intrepid ibex , you won't have any webcam detection problem. i'm guessing this is hardy or earlier.

---

### Post by dsdeiz on 2008-12-03
Yeah, I'm currently using hardy. I've used the deb package that you provided in the Howto: Gyachi.

---

### Post by loell on 2008-12-03
in intrepid, gyachi tapped a new webcam layer, to make it more compatible with recent linux supported webcam, this layer is not available hardy, since your webcam is detected by cheese in hardy, i'm almost sure that intrepid gyachi can detect that webcam.

---

### Post by dsdeiz on 2008-12-03
> **loell said:**
> in intrepid, gyachi tapped a new webcam layer, to make it more compatible with recent linux supported webcam, this layer is not available hardy, since your webcam is detected by cheese in hardy, i'm almost sure that intrepid gyachi can detect that webcam.
I see so I guess I'll just upgrade to intrepid. Thanks :)

***Edit:** I got my webcam working with Kopete although the color was "pinkish" and I haven't "actually" tried it (i.e. invite a friend of mine to view my webcam). I'll probably stick to this until I can upgrade to Intrepid and try gyach. Many thanks again. :)*

---

### Post by uschxc on 2008-12-30
i'm able to get my webcam to work, sort of.  i get two small images in the top quarter of the webcam screen instead of one full image.  running intrepid 32bit

---

### Post by loell on 2008-12-30
> **uschxc said:**
> i'm able to get my webcam to work, sort of.  i get two small images in the top quarter of the webcam screen instead of one full image.  running intrepid 32bit

hmm, this is more of  driver issue (not gyachi's), integrated laptop webcam can in times, difficult to troubleshoot, would you know by chance the name of the integrated webcam?

---

### Post by n2dabloo on 2009-01-01
> **loell said:**
> hmm, this is more of  driver issue (not gyachi's), integrated laptop webcam can in times, difficult to troubleshoot, would you know by chance the name of the integrated webcam?

I have the exact same problem.  My integrated webcam is a Chicony 2.0  I'm using Intrepid Ibex on a Toshiba laptop.  Any help would be greatly appreciated as this is my primary means of staying in touch with family overseas.

---

### Post by loell on 2009-01-01
> **n2dabloo said:**
> I have the exact same problem.  My integrated webcam is a Chicony 2.0  I'm using Intrepid Ibex on a Toshiba laptop.  Any help would be greatly appreciated as this is my primary means of staying in touch with family overseas.

chicony uses the uvc driver, try asking on their mailing list

[https://lists.berlios.de/mailman/listinfo/linux-uvc-devel]("https://lists.berlios.de/mailman/listinfo/linux-uvc-devel")

---

### Post by n2dabloo on 2009-01-01
> **loell said:**
> chicony uses the uvc driver, try asking on their mailing list

[https://lists.berlios.de/mailman/listinfo/linux-uvc-devel]("https://lists.berlios.de/mailman/listinfo/linux-uvc-devel")

I got this when I tried that link:
[IMG]http://e.imagehost.org/0901/Screenshot-Add_Security_Exception.png[/IMG]
thanks anyway.

---

### Post by loell on 2009-01-01
> **n2dabloo said:**
> I got this when I tried that link:
thanks anyway.

its just a certificate. you can acquire it, to get through.

---

### Post by uschxc on 2009-01-02
> **loell said:**
> hmm, this is more of  driver issue (not gyachi's), integrated laptop webcam can in times, difficult to troubleshoot, would you know by chance the name of the integrated webcam?

sure Loell, from what i can tell its OmniVision Technologies something or other.  lshw doesn't tell me much and lsusb tells me just the manufacturer.

xawtv pulls up a perfect image, if i use yahoo via vmware workstation the webcam works appropriately (although mucho resource hogging, as to be expected) so if it is a driver issue it seems to me it would be gyachi's implementation of the driver...unless xawtv and vmware use a different access method.  subscribing to this so let me know asap what i can do to help with this problem.

---

### Post by loell on 2009-01-03
> **uschxc said:**
> 
xawtv pulls up a perfect image, if i use yahoo via vmware workstation the webcam works appropriately (although mucho resource hogging, as to be expected) so if it is a driver issue it seems to me it would be gyachi's implementation of the driver...unless xawtv and vmware use a different access method.  subscribing to this so let me know asap what i can do to help with this problem.

xawtv uses a raw old layer to access webcam devices, VMWare is well,.. virtual. while gyachi uses the new  standard layer in accessing webcams. the project is **libv4l**

[more info]("http://hansdegoede.livejournal.com/3636.html") probably contact libv4l's developer as to why the split image.

---

### Post by uschxc on 2009-01-03
> **loell said:**
> xawtv uses a raw old layer to access webcam devices, VMWare is well,.. virtual. while gyachi uses the new  standard layer in accessing webcams. the project is **libv4l**

[more info]("http://hansdegoede.livejournal.com/3636.html") probably contact libv4l's developer as to why the split image.

well i do know my camera doesn't work with v4l, only v4l2

---

### Post by Tosa on 2009-01-03
> **loell said:**
> hmm, this is more of  driver issue (not gyachi's), integrated laptop webcam can in times, difficult to troubleshoot, would you know by chance the name of the integrated webcam?

I have the same problem with two small images.

But I don't have an integrated camera and a laptop. It's a MSI StarCam on my desktop.
I'm running Interpid 64. In Kopete the same camera has a perfect image.
:confused:

---

### Post by uschxc on 2009-01-03
mine also works just fine through Ekiga, for what its worth.

---

### Post by loell on 2009-01-03
like i said this is a driver issue (image decoding), its between **uvc** and **libv4l**,  not much gyachi can do about it. 

if you are doubtful.

you can contact these projects for further responses,

[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

[http://hansdegoede.livejournal.com/3636.html](http://hansdegoede.livejournal.com/3636.html)

and

[http://gyachi.sourceforge.net]("http://gyachi.sourceforge.net")

---

### Post by DougieFresh4U on 2009-01-10
First i would like to say thanks for all the work and time spent with this thread and gyachi, thanks 'loell'. 
Now for my dilema, I am using 'Jaunty' and I do not know where I got download from but it was a .deb (I am horrible with .tar and compiling) I am using 'GYachE Improved 1.1.58'. I can get my logitec , cheapo cam working but I am having problem with chat/voice. Always tells me I am missing some files which are .dll and 32 some thing or other. I would be glad for a tips or suggestions on maybe getting voice/chat working. Also when I start webcam I get black picture but I just go into properties and move sliders over and picture comes in but rather 'orangish' but other then can see me and I also see there cam
Thanks

---

### Post by loell on 2009-01-10
> **DougieFresh4U said:**
> First i would like to say thanks for all the work and time spent with this thread and gyachi, thanks 'loell'. 
Now for my dilema, I am using 'Jaunty' and I do not know where I got download from but it was a .deb (I am horrible with .tar and compiling) I am using 'GYachE Improved 1.1.58'. I can get my logitec , cheapo cam working but I am having problem with chat/voice. Always tells me I am missing some files which are .dll and 32 some thing or other. I would be glad for a tips or suggestions on maybe getting voice/chat working. Also when I start webcam I get black picture but I just go into properties and move sliders over and picture comes in but rather 'orangish' but other then can see me and I also see there cam
Thanks

you need [gyachi codecs]("http://downloads.sourceforge.net/ gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0")

also try [1.1.59]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi") maybe the webcam could improve.

---

### Post by DougieFresh4U on 2009-01-11
> **loell said:**
> you need [gyachi codecs]("http://downloads.sourceforge.net/ gyachi/gyachi-codecs.deb?modtime=1194233368&big_mirror=0")

also try [1.1.59]("http://ubuntuforums.org/showthread.php?t=773802&highlight=gyachi") maybe the webcam could improve.
Thanks so much.
After reading all through thread, I understand that I can not do voice chat with friends via gyachi. So what would I use for voice chat for yahoo?

---

### Post by loell on 2009-01-12
> **DougieFresh4U said:**
>  So what would I use for voice chat for yahoo?

i use gizmo5 to call yahoo contacts.

---

### Post by n2dabloo on 2009-01-14
I see that Gyachi 1.1.61 is out.  I downloaded it but I'm clueless as how to install it.  Any help would be greatly appreciated.  I'm hoping that the webcam issues have been resolved in this latest release.

---

### Post by loell on 2009-01-14
> **n2dabloo said:**
>   I'm hoping that the webcam issues have been resolved in this latest release.

there were no changes that pertains to webcam in .60 and .61 . any webcam changes  will be unlikely in succeeding releases.

---

### Post by n2dabloo on 2009-01-14
> **loell said:**
> there were no changes that pertains to webcam in .60 and .61 . any webcam changes  will be unlikely in succeeding releases.

Thanks for your tireless efforts with this messenger, salamat po.

---

### Post by loell on 2009-01-14
> **n2dabloo said:**
> Thanks for your tireless efforts with this messenger, salamat po.

np, if you ever want to talk to the developer of the project, feature request / bug report [http://gyachi.sourceforge.net/forums.shtml]("http://gyachi.sourceforge.net/forums") :)

---

### Post by Medox on 2009-02-17
How do I install Gyachi 1.1.61 on Ubuntu 8.10?

I had no luck/idea :|

**p.s.** A .deb package would be great. Btw, @loell, I've used your previous packages, thanks! Can you make one for .61 too?

---

### Post by loell on 2009-02-17
there's really no significant change from .59 to .61 ,  though if time allows i may build .61 some time this week.

---

### Post by andyshedd on 2009-02-19
any eta on jaunty packages?

---

### Post by bsnider on 2009-02-20
Dear Loell, 

  I am trying to learn how to use Gyachi.  I find it somewhat difficult.  1)  First of all, I really want to be able to do voice chat.  You were saying in a message a couple of years ago that you have to be in a "room"  Being in a conversation with one user does not make you in a room, does it?  I dunno, could you explain that a little?  Is there a detailed tutorial about how to use Gyachi somewhere? 

2)  I guess to do voice chat,  you need to be have a microphone and speakers hooked up to the plugs on the computer, isn't that right?  Our webcam has a microphone built in, but it is not working yet.  

2)  I really want to get the web cam working.  When trying to start the webcam, the error message came up "an error occurred in ioctl vidiocspict.  could not set driver properties."  I am using a Logitech V-AUX16 web cam.  

 Thank You in advance very much for your help!!

Bruce

---

### Post by loell on 2009-02-21
> I guess to do voice chat, you need to be have a microphone and speakers hooked up to the plugs on the computer, isn't that right? Our webcam has a microphone built in, but it is not working yet.

yes, unless there is a way to make webcam with mic device work on linux, you need to have the usual audio peripherals.

> ) I really want to get the web cam working. When trying to start the webcam, the error message came up "an error occurred in ioctl vidiocspict. could not set driver properties." I am using a Logitech V-AUX16 web cam.

is this working on other apps?

---

### Post by bsnider on 2009-02-24
Thank you Mr Loell for your reply!  

I used headphones and a big microphone. 

I was able to get the webcam to work on Cheese.  

I spent alot of time searching the Ubuntu forums and web for more suggestions.  One thing I learned about Gyachi is that you need to go to Setup-Options - Sound Device and select some option.  The only one that came up is Pulse Audio plugin 9.10.  I dunno if that worked, but at least I heard some audio through the headphones at one point.  

I tried the following procedure trying to get Gyachi to work.  I was unsuccessful:  
Have other user fix their profile on windows YIM.  Maybe make it available for all to see, etc.  
I think other user using Windows should not click invite or anything else.  
I GO To rooms, Favorites, or Room List.  If using room list, it will expand if you click the triangle on the left  Select a suitable room, like Christian Chat
I enter scrambled code
I Invite Other User 
Other User needs to click on website agreeing to enter Christian Chat room
I click on voice chat icon
I select name of other user from menu that appears.  (IF possible)   

After all this effort, I think I will quuit trying to use Gyachi.  I could not get it to work at all, after spending many hours trying.  Also, my wireless router shut down, and I think maybe Gyachi caused that. 

My main goal is to get VOIP to work somehow.  I will next try Ekiga.  

When Gyachi is improved so that it works really well, it would be great to add it as a supported Ubuntu application available through the Add/Remove menu. 

Still, thank you very much for your help!  

Bruce

---

### Post by uschxc on 2009-08-28
so if i send you a v4l2 webcam loell, you can get to work on supporting the library? :)

---

### Post by loell on 2009-08-28
> **uschxc said:**
> so if i send you a v4l2 webcam loell, you can get to work on supporting the library? :)

oh no. not to me.. ;)

but if you send to the guy(s) who develops webcam drivers like spca5xx,uvc and other webcam development teams then you can have results.

---

### Post by Night-Horse on 2009-09-24
Hello All,

Am having a problem with voice. When I try to use it I get this error on console: "sh: gyachivoice: not found"

I did not found any relevance errors on my searching and I read somewhere that gyachivoice is installed with the package. So what's wrong on my comp? :P

I am using jaunty x64 and installed gyachi from your repo loell. Thanks in Advance. :)

---

### Post by YannBuntu on 2009-11-08
> **loell said:**
> i use gizmo5 to call yahoo contacts.

Hi Loell, 
thank you for helping so much on this thread.
I would like to summarize the situation for YahooMessenger (to update our [ubuntu-fr wiki]("http://doc.ubuntu-fr.org/visioconference")). 
I understood from the past discussion that:
- Gyachi is good for audio+video on Yahoo Messenger , but video is not working for everyone 
- the best soft for audio on Y!messenger is Gizmo 

Please can you confirm/correct ?

thank you in advance!

---

### Post by loell on 2009-11-08
> **YannBuntu said:**
> Hi Loell, 
thank you for helping so much on this thread.
I would like to summarize the situation for YahooMessenger (to update our [ubuntu-fr wiki]("http://doc.ubuntu-fr.org/visioconference")). 
I understood from the past discussion that:
- Gyachi is good for audio+video on Yahoo Messenger , but video is not working for everyone 
- the best soft for audio on Y!messenger is Gizmo 

Please can you confirm/correct ?

thank you in advance!

Hello,

- Gyachi is good for Yahoo Video, it works mostly if the webcam is detected by libv4l

- any SIP based soft phone will do, that can contact gtalk2voip service, it's just gizmo does this automatically.

---

### Post by YannBuntu on 2009-11-08
thank you for your quick answer!

so if we want to use audio+video with Yahoo Messenger, you recommend to use 2 sofwares ? (Gyachi for video + Gizmo for audio) ? 

Is this solution as functional/reliable as Skype ? (considering any type of router/internet box, and any type of correspondant's OS)

For YahooMessenger, what other SIP+[automatic Gtalk2voip] softphone can we use ? Pidgin and Empathy are ok ?

What other software could be used for the Y!M webcam ?


Sorry for the amount of questions, but I try to be exhaustive for the French wiki. 
By the way, I think the English wiki is lacking information about videoconference possibilities on Ubuntu: the only data I found is [https://help.ubuntu.com/community/InternetApplications](https://help.ubuntu.com/community/InternetApplications) and it is out-dated ! Do you know a better page? (if not I will tell this problem to the doc team, and try to create an English page).

---

### Post by loell on 2009-11-10
> **YannBuntu said:**
> 
so if we want to use audio+video with Yahoo Messenger, you recommend to use 2 sofwares ? (Gyachi for video + Gizmo for audio) ? 

yes, but it's not really limited to that, we could also do kopete for yahoo video and ekiga or empathy for Yahoo voice, did a howto way way back [http://ubuntuforums.org/showthread.php?t=414121](http://ubuntuforums.org/showthread.php?t=414121)

> **YannBuntu said:**
> 
Is this solution as functional/reliable as Skype ? (considering any type of router/internet box, and any type of correspondant's OS) 

sadly, No, it isn't reliable. I mean as far Yahoo voice is concerned, since it uses gtalk2voip.com service to contact yahoo, it's delayed oftentimes, full of echoes, and gtlak2voip will spam your contact at the other end. :(

in free software nobody really bothered to try to decipher yahoo voice,  this is really a loosing battle.  who knows perhaps wine might be able to fully run yahoo messenger someday. ;)

if you're still optimistic about Full Yahoo audio/video in Linux,  you could ask the empathy guys if they are doing something about it.

or   maybe you could  also follow up [gyachi]("gyachi.sourceforge.net/forums.shtml") of any plans for the feature.

:)

---

### Post by YannBuntu on 2009-11-11
Thanks for your precious advices. 

> **loell said:**
> - any SIP based soft phone will do, that can contact gtalk2voip service, it's just gizmo does this automatically.

With Ekiga for example: 
1) I send a gtalk2voip invitation to the correspondant via the gtalk2voip website.
2) The correspondant has to accept the invitation
3) I can call the correspondant by entering mycorrespondantlogin%yahoo.com@yahoo.gtalk2voip.com in the sip bar.

What is the procedure with Gizmo ? (No need to send gtalk2voip invitation?)

---

### Post by loell on 2009-11-11
> **YannBuntu said:**
> 
What is the procedure with Gizmo ? (No need to send gtalk2voip invitation?)

yep, no need, and the user can just add the contact in gizmo with @yahoo prefix. and then they can call away.

---

### Post by fishfillet on 2009-11-11
Hey Loell, this is very much OT but I just want you to know that you are doing a great job with GYACHI.

I've used the original Gyach then and you and so as the others have really improved it a lot.

Keep it up kabayan!

---

### Post by YannBuntu on 2009-11-12
yep, thanks a lot Loell !

---

### Post by iya_dech2000 on 2010-11-06
voice error on gyach 1.1.48

     tsd32.dll
      tssoft.acm

Not in the following directories:
      /
      /usr/lib/win32/
      /usr/lib/win32/
      /usr/local/lib/win32/
      /usr/lib/codecs/

i use ubuntu 8.04

i extremely newbie...
help me...

---

### Post by mahmoodkamal on 2011-01-17
Hi guys,

I am a new user of gyachi. Can someone guide me how to initiate voice chat with someone. I can do text chatting, but don't know how to start voice chat.

Can someone please help ???

---

