---
title: "I really screwed up and all I want to do is play poker"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Southsidepoker on 2008-08-09
Ok I really screwed myself and accidentally deleted vista completely and installed ubuntu. 

All I want to do Is play some cards on ultimate bet and I can't figure out how to install it.

The whole reason I got in this stupid mess in the first place was vista kept freezing up on me completely and the only way I could get it to work was to run it in safe mode. So I decided to install ubuntu on a partition and try it out. Well instead I accidentally deleted vista and now I don't know how to do anything. I read the tutorials and none of them are working for me. 

I dl'ed the app from ultimatebet.com and it put an icon in my desktop called ubsetup.exe I double click it then the mouse pointer turns into a circle for a few seconds and then goes back to normal and nothing happens.

I am so frustrated right now and all I want to do is relax and use my computer . Instead I feel like breaking it in half over my knee.

---

### Post by Diabolis on 2008-08-09
The file **ubsetup.exe** has the .exe extension, which means that is a windows executable. You can't run windows executables directly in linux, but you can run them using other programs like cedega and wine or inside a virtual installation of windows.

The easiest for you would be to get either cedega or wine. Since wine is free and you can get it from the repositories, probably thats the path that you want to follow.

To install wine, just:
```
sudo apt-get install wine
```

After that, you can right click on **ubsetup.exe**, and you'll see an option that says something like "run with wine".

---

### Post by Southsidepoker on 2008-08-09
> **Diabolis said:**
> The file **ubsetup.exe** has the .exe extension, which means that is a windows executable. You can't run windows executables directly in linux, but you can run them using other programs like cedega and wine or inside a virtual installation of windows.

The easiest for you would be to get either cedega or wine. Since wine is free and you can get it from the repositories, probably thats the path that you want to follow.

To install wine, just:
```
sudo apt-get install wine
```

After that, you can right click on **ubsetup.exe**, and you'll see an option that says something like "run with wine".

Thank you so much for the quick response. I am a total nub with ubuntu and linux and I don't know where to enter that code.

---

### Post by perlluver on 2008-08-09
Go to Applications>Accessories>Terminal and enter that code.

---

### Post by ad_267 on 2008-08-09
You can enter it in Applications - Accessories - Terminal.

You can also install software from Add/Remove or System - Administration - Synaptic Package Manager but it's usually easier to give people commands to enter rather than describe lots of steps.

---

### Post by Diabolis on 2008-08-09
In a terminal. In the menu: **Accesories / Terminal**

---

### Post by ad_267 on 2008-08-09
According to this: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273), the software should run with wine but you have to install Internet Explorer in wine to get it to work first.

After you have run that code to install wine run:
```
winecfg
``` to configure wine.

Then:
```
wine iexplore http://winehq.org
```
which will install internet explorer.

This might seem like a lot of hassle to go through but just remember you're running a windows program in Linux. :)

---

### Post by Southsidepoker on 2008-08-09
OK I got ultimate bet installed with wine. I just found it in the synap-whatever. Thanks for the terminal info though, Now that I have it installed it says I need flash player 8 to play but the link to DL it does nothing, So I just went to the flash player site and now I got a flashplayer link on the desktop but this one has an orange lock on it and when I click on it I get prompted asking if I really want to run it (the flash installer) click yes then it seems like something is going to happen but nothing does and it still says I need it. 

Why do computers have to be such a pain in the ***. All I want to do is play a little poker and browse the internet a little, I hardly even download music or anything and my computers still always screw up. Why can't they just do what they are supposed to do. It is just a 700 dollar headache. I had planned on just chilling out playing cards tonight and instead I have to be all stressed and ready to kill something.

---

### Post by ad_267 on 2008-08-09
Installing programs in Ubuntu is different to windows. Instead of downloading the flash player from the website you install it from the package manager. You can go to system - administration - synaptic package manager and search for flashplugin or enter in a terminal:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by starcannon on 2008-08-09
I'd recommend winedoors, its a nice little gui for wine.
Directions and Information on it are here:

[https://help.ubuntu.com/community/WineDoors](https://help.ubuntu.com/community/WineDoors)

That should let you install all of your windows dependencies with a nice easy to understand gui.

GL

---

### Post by Diabolis on 2008-08-09
Yeah, thats why I avoid as much as I can using anything related to windows. Even when I could have a problem in linux, I know there will be always a solution here in the forums.

You can also try ies4linux: [easy how to]("http://www.psychocats.net/ubuntu/ies4linux")

Probably this is a lot of information and installation instructions, so you might just want to play for now: [http://ubuntuforums.org/showthread.php?t=573947](http://ubuntuforums.org/showthread.php?t=573947)

---

### Post by Southsidepoker on 2008-08-09
Thanks alot for all the info guys. I am super new and ended up way over my head by deleting vista before I learned how to use ubuntu, This is one of the best communities I have ever seen and I really look forward to learning and erasing my windows dependencies.

---

### Post by tinker312 on 2008-08-09
Hey Southsidepoker, 

I've been trying to run some windows applications in Ubuntu as well, just as a hobby mostly, and I've found that crossover office is a very polished application that uses wine to help with installing and using windows apps.  There is a 30 day trial and then it's 30 bucks or so. It may be worth looking into if you are transitioning to Ubuntu and have not found alternatives to window based apps.

---

### Post by ad_267 on 2008-08-09
> **tinker312 said:**
> Hey Southsidepoker, 

I've been trying to run some windows applications in Ubuntu as well, just as a hobby mostly, and I've found that crossover office is a very polished application that uses wine to help with installing and using windows apps.  There is a 30 day trial and then it's 30 bucks or so. It may be worth looking into if you are transitioning to Ubuntu and have not found alternatives to window based apps.

Crossover office isn't really needed unless you have some reason why you absolutely must use Microsoft Office. OpenOffice is very similar and easy to use, it also supports .doc, .xls formats etc and OpenOffice 3 will have better support for .docx and .xlsx

This site has alternative open source software for programs used in windows: [http://www.osalt.com/](http://www.osalt.com/)

---

### Post by Southsidepoker on 2008-08-09
> **tinker312 said:**
> Hey Southsidepoker, 

I've been trying to run some windows applications in Ubuntu as well, just as a hobby mostly, and I've found that crossover office is a very polished application that uses wine to help with installing and using windows apps.  There is a 30 day trial and then it's 30 bucks or so. It may be worth looking into if you are transitioning to Ubuntu and have not found alternatives to window based apps.

Thanks for the suggestion man I will definitely keep it in mind.

---

### Post by Southsidepoker on 2008-08-09
> **ad_267 said:**
> Installing programs in Ubuntu is different to windows. Instead of downloading the flash player from the website you install it from the package manager. You can go to system - administration - synaptic package manager and search for flashplugin or enter in a terminal:
```
sudo apt-get install flashplugin-nonfree
```

Well I did this and still says I need flash player 8. Kind of confusing I guess I will just keep trying to figure something out, soo sad want to play the poker.

---

### Post by ad_267 on 2008-08-09
Ok I guess that the internet explorer in wine can't use the normal flash player then. According to the page on the wine appdb ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273)) people got it working after installing internet explorer using winetools ([http://von-thadden.de/Joachim/WineTools/index.html](http://von-thadden.de/Joachim/WineTools/index.html)) so maybe that's what you need to do.

Does it have to be this particular poker game? That link Diabolis posted before ([http://ubuntuforums.org/showthread.php?t=573947](http://ubuntuforums.org/showthread.php?t=573947)) had a few poker games that would run on Ubuntu without any hassle.

---

### Post by suprfish on 2008-08-09
> **Southsidepoker said:**
> Well I did this and still says I need flash player 8. Kind of confusing I guess I will just keep trying to figure something out, soo sad want to play the poker.

Hang in there! :KS

Do the following:

1. Open up a terminal (**Applications > Accessories > Terminal**).
2. Enter "**cd ~/Desktop**"
3. Then, enter "**wine [name of the install file]**", replace brackets with the filename (e.g."**wine UltimateBet_Installer.exe**"). Run it.
4. Copy and paste whatever the output is in the terminal into a new post.

---

### Post by bpowell2005 on 2008-08-09
FYI: Here's a link to instructions from somebody who got ultimate bet running under wine...looks like what I've seen here already; install IE6, install UB. I didn't look too deep. [http://www.theunspecialized.com/content/view/140/52/](http://www.theunspecialized.com/content/view/140/52/)

---

### Post by Southsidepoker on 2008-08-10
> **ad_267 said:**
> Ok I guess that the internet explorer in wine can't use the normal flash player then. According to the page on the wine appdb ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3691&iTestingId=273)) people got it working after installing internet explorer using winetools ([http://von-thadden.de/Joachim/WineTools/index.html](http://von-thadden.de/Joachim/WineTools/index.html)) so maybe that's what you need to do.

Does it have to be this particular poker game? That link Diabolis posted before ([http://ubuntuforums.org/showthread.php?t=573947](http://ubuntuforums.org/showthread.php?t=573947)) had a few poker games that would run on Ubuntu without any hassle.

Yeah it pretty much has to be ultimate bet, I play for money and that is the site I have money on. Is everything this difficult to install on linux or does it get easier as you get used to it? 

I am trying to use this guys instructions [http://www.theunspecialized.com/content/view/140/52/](http://www.theunspecialized.com/content/view/140/52/) but now wine-doors froze while I was using it to install ie and flash player 9. It is so frustrating because the ultimate bet software is installed and I can login just can't play without flash 8.

Why the **** are computers such a ******* pain in the *** all I want to do is ******* play cards that is the only reason I bought a ******* computer and got the internet. I guess I am just gonna have to call HP and send it in and get a refund and just get a different computer. I cant even do one simple ******* task on it. The only reason I even have the thing and it won't do it. How ******* hard does it have to be to ******* install flash player. It shouldn't be brain surgery.

---

### Post by SlalomMan on 2008-08-10
Maybe try installing flash player 8 and not 9? I know sometimes emulatio--ahem, "compatibility layers" like wine get buggy with newer versions of software.

---

### Post by Diabolis on 2008-08-10
> **Southsidepoker said:**
> Yeah it pretty much has to be ultimate bet, I play for money and that is the site I have money on. Is everything this difficult to install on linux or does it get easier as you get used to it? 

I am trying to use this guys instructions [http://www.theunspecialized.com/content/view/140/52/](http://www.theunspecialized.com/content/view/140/52/) but now wine-doors froze while I was using it to install ie and flash player 9. It is so frustrating because the ultimate bet software is installed and I can login just can't play without flash 8.

Is not this difficult usually. Plus, as time passes, things get better. I've seen how it has been improving, thanks to all the open source developers.

If you really get stuck with the guide that you are using. You might want to check out [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page"), because the flash player plug in is installed automatically when you install them.

[how to install ies4linux in ubuntu]("http://www.psychocats.net/ubuntu/ies4linux")

---

### Post by ad_267 on 2008-08-10
> **Southsidepoker said:**
> Yeah it pretty much has to be ultimate bet, I play for money and that is the site I have money on. Is everything this difficult to install on linux or does it get easier as you get used to it? 

I am trying to use this guys instructions [http://www.theunspecialized.com/content/view/140/52/](http://www.theunspecialized.com/content/view/140/52/) but now wine-doors froze while I was using it to install ie and flash player 9. It is so frustrating because the ultimate bet software is installed and I can login just can't play without flash 8.

No it's nowhere near this difficult to install most things. It's only difficult because this is a windows application and isn't supposed to run in Linux. Most things can be installed easily through Add/Remove programs or the Synaptic Package Manager. If you do get this sorted and keep Ubuntu around this explains how to install all kinds of programs: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I guess installing through wine doors is your best shot. Maybe reinstall wine and delete the .wine folder in your home directory to get a fresh slate then try again. (That folder is hidden, you can press Ctrl+H to show hidden files)

---

### Post by cgkades on 2008-08-10
yes, oh yes. it gets easier. just remember that all this is free. and even free comes at a price, and in linux that price is patience. I only use windows at work now, and as soon as i can figure out how to make my computer apart of the domain so i can get access to email and such, i'll just boot into a live ubuntu session and reconfigure every morning and be rid of the garbage for good

---

### Post by Southsidepoker on 2008-08-10
> **SlalomMan said:**
> Maybe try installing flash player 8 and not 9? I know sometimes emulatio--ahem, "compatibility layers" like wine get buggy with newer versions of software.

Maybe that would work but I can't even install the one I downloaded so I doubt I will be able to get one I cant find installed. I have been trying to install flash player for 3 hours now. I am pretty much beyond trying now. I am just going to get another computer , this is way to much stress to deal with just to install 1 little program.None of this **** even makes sense . Why can't I even click the link for flash 8 on ultimate bet that it says u need. Everything pretty much uses flash so why would it even be an issue should just be there. Like I said the only reason I bought this thing was to play poker and I have never went longer than 2 months without having to return my computer. Why the **** do they have to be such a pain in the *** . I barely even use mine for anything outside of playing poker and still nothing but problems nonstop.

---

### Post by suprfish on 2008-08-10
You have Wine Doors installed, correct? (**Applications > Wine > Wine Doors**). You should be able to install Flash 8 really easily with it.

---

### Post by tinker312 on 2008-08-10
Perhaps you can try this [http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/](http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/) it's a detailed tutorial of installing all the major poker clients on linux.  

Linux is not for everyone, it does take patience as other have said.  Yet, the reward of configuring your system, of making it your own is worth it. When I first started out I would spend hours pecking out commands at the terminal trying to get my system to do what I wanted. I broke my installation most of the time, but sometimes I actually got things to work and it was very satisfying. I still am a novice but I love to tinker and learn and explore things that are unfamiliar to me and so far, ubuntu with the community, support and overall usability of the OS has me really stoked.

Windows has it's advantages as well and for most people, generally speaking, it's the OS of choice.  It's the reason why so many people try to port window apps to linux, such as ultimate bet. If you give it a year window binary execution will become as seamless as the archive manager is now in Ubuntu.  Winehq, Crossover Office and Cedega may even check binary dependencies against a database and automagically download and install them for users.  The trick is that these pieces of the puzzle that make ultimate bet or other windows apps work are not free, they are proprietary and so we have brilliant developers who I'm assuming reverse engineer these windows balls of money and create gpl versions available for me, you and some kid in Africa who can use a computer and surf the web and not have to spend a years worth of his parents salary to license windows.  (Although, Gates may give away millions of copies of windows in Africa, I don't really know :)

---

### Post by Southsidepoker on 2008-08-10
Ok so I downloaded ies4linux got it installed which supposedly intalled flash player and guess what. It still doesn't work. I even reinstalled the UB software thru there site with ies4linux or w/e thinking that might help and nothing changes. Why won't it just ******* work. I just want to do one simple thing. It got installed with ies4linux so why the hell isnt it working . Is ultimate bet reffering to a different flash 8? That is exactly what they call it flash 8. And that is the one thing I haven't seen mentioned in any of the ub tutorials. It is like I am the only one who didn't already have it before they downloaded ultimate bet.

---

### Post by tinker312 on 2008-08-10
I actually think his problem is that he needs a flash distribution that works with web applications and not just a flash plugin. 

and/or 

We need to find a way to configure ultimate bet to link to the non-free plugin he installed with synaptic, assuming he did install the flash plugin available through the package manager.

I wonder if there is a configuration file for ultimate bet that you can edit and point to the libflash.so plugin.  Isn't the game basically a flash web page that links to the their server? I should install and check . . .

---

### Post by suprfish on 2008-08-10
> **Southsidepoker said:**
> Ok so I downloaded ies4linux got it installed which supposedly intalled flash player and guess what. It still doesn't work. I even reinstalled the UB software thru there site with ies4linux or w/e thinking that might help and nothing changes. Why won't it just ******* work. I just want to do one simple thing. It got installed with ies4linux so why the hell isnt it working . Is ultimate bet reffering to a different flash 8? That is exactly what they call it flash 8. And that is the one thing I haven't seen mentioned in any of the ub tutorials. It is like I am the only one who didn't already have it before they downloaded ultimate bet.

[http://ubuntuforums.org/showpost.php?p=5560542&postcount=8](http://ubuntuforums.org/showpost.php?p=5560542&postcount=8)

---

### Post by Diabolis on 2008-08-10
Just to see why it was so hard to get this working, I went to their site and downloaded the application.

When I tried to install it, it asked me to install [Gecko]("http://wiki.winehq.org/Gecko"), so I did.

The program does show a link that says that you need to install flash 8, however everything seems to be working. See the screenshot that I attached.

This is my wine version:
```
wine --version
wine-1.0

```

Running in hardy heron.

I guess that actually Gecko is the problem. I do have installed ies4linux, but I don't know how to open the program with ies4linux instead of Gecko.

---

