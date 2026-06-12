---
title: "[SOLVED] Several Questions please"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Evil79 on 2008-10-26
Greetings Ladies & Gents,

First of all I would like to apologies because I know those questions might have been asked before, but I couldn't find any on the topics.

Since the day i understood what a computer meant, i have never seen an OS system that i liked except for Windows. till now of course, i like Ubuntu a lot and would like to know and learn as much as possible about it. so I am sorry for the million questions.

1. I know that there are no Viruses on Unix but i am superstitious so Is there a Virus Protection program for Ubuntu ? - *on Windows i was using Kaspersky. i don't think it is available for Ubuntu.*

2. Is there a "Windows Live Messenger" for Ubuntu ?

3. From reading on Ubuntu, I understand that not all programs and games will run on Ubuntu, however there are alternatives for those programs. but what about games, does Ubuntu run games ?

Example - _World in Conflict, Crysis, Call of Duty, Warcraft, Company of Heroes_.

4. If the answer to {3} is YES - Windows has Direct X to show the ability of graphics, specially the difference from Direct X 9 & Direct X 10. so is there such a thing for Ubuntu, or does all games run on standard graphics.

5. Under { System => Preferences => Appearance } under the "Visual Effect" tab, i finally was able to click on Extra. but i was wondering if there was a more visual effects on ubuntu ? *- Like for example i saw on a video on ubuntu that once you click on a menu and jump to a sub menu. the main menu will disappear but in a cool visual effect. like fire or such.*

6. Is it possible to use another Explorer other than "Fire Fox" ? like for example "Chrome" the Google explorer.

7. When i installed Ubuntu the first time it was 7.10, but back then almost nothing was running specially my graphic card. so i uninstalled it. now that its 8.04, so my question is. is the New Updated Ubuntu stable and can actually "Exchange" Windows Vista ? -* because to be honest i would love to think so.*

8. Is there like a "Defrag" option on Ubuntu or like Disk Scan ?

9. This might not be an Easy one. but i tried installing another language and i think it worked successfully. however when i tried opening the Microsoft Word file with "Open Office Word Processor" the file was opened but the letters were backwards. so is that because i didn't install the second language correctly or is it because Open Office can not run Microsoft files.

10. Are there like special Video Codecs for Ubuntu, like DivX, Real Player, Quick Time. or does the Video player on Ubuntu runs all kind of videos regardless of the type ?


I apologies for all the questions, and would like to thank you for reading my post.

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by dracayr on 2008-10-26
1. there are firewalls and rootkit finders.. google them
2. pidgin (Applications&#8594;Internet&#8594;pidgin)
3. Warcraft yes, Crysis and CoD no, and the other two I don't know (there are ego-shooters for linux, though)
4. OpenGL
5. execute this in a command line: ```
sudo apt-get install compizconfig-settings-manager
``` Then, enter: ```
ccsm
```. You should now be able to configure the effects you would like to have
6. yes, opera works, chrome maybe (with wine), but I wouldn't use chrome. Google collects data about you and your browsing and as you can imagine, google can collect as much data as it wants, if you use google's browser.
7. It is stable, and any linux with compiz can exchange vista (except maybe the gaming) in my opinion, since vista only consists of fancy Eye candy (and support for high-end games)...
8. you don't have to defrag ext3, which is the filesystem ubuntu uses.
9. Open Office can open microsofts files. the support is even better with the new beta version (rc). I can't help you with your specific problem though
10. there are codecs available for all mayor video types. Totem searches for the codecs, and installs them for you when you first try to open a video using the specific codec. The reason they aren't installed by default is that the codecs aren't under the GPL license, and Ubuntu is.

dracayr

---

### Post by Helios1276 on 2008-10-26
2. If you are only looking for an a Windows Live Messenger replacement try Amsn.

I'd also recommend VLC player for movies and the like.

---

### Post by m_duck on 2008-10-26
Hey there

1. There are a few virus scanners for ubuntu. ClamAV and avast come to mind, but I don't know about them having never used them.
2. There is not an official "Windows Live Messenger" for linux but there are many clients to connect to the msn network for chat. I use "pidgin". There are loads though: amsn, emesene, kopete, kmess to name a few.
3. I am not sure about gaming much in linux but I have managed to run half life 2 and counter strike under wine - [wine]("http://www.winehq.org/") - see the "appdb" for games and how well they will run. There are also games that are native to linux. In ubuntu you can click Applications -> Add/Remove Programs and click games to see some of them (I think).
4. Not sure.
5. Once your graphics drivers are installed and extra is enabled, from synaptic, install the package "compizconfig-settings-manager". This will add an entry to System -> Preferences I believe where you can configure all the cool craziness that compiz has to offer.
6. Firefox is the browser I use, but there is always opera and loads more that I can't remember the names of. I believe google are currently developing a version of its chrome browser for linux.
7. I think so. I use linux most of the time except for the odd game (I'm not really a gamer), and for that I've kept my windows xp partition around.
8. I think due to the ext3 filesystem that ubuntu uses by default, files do not get fragmented as they do in windows so this is unneccessary.
9. Not sure.
10. There are a few packages of codecs to download to make everything work. A couple of useful resources are: [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") and [Multimedia howto]("http://ubuntuforums.org/showthread.php?t=766683&highlight=comprehensive+media")

Hope this helps!

---

### Post by Evil79 on 2008-10-26
Thank you so much "[COLOR="Red"]dracayr[/COLOR]", "[COLOR="Red"]Helios1276[/COLOR]", "[COLOR="Red"]m_duck[/COLOR]" I really appreciate it allot.

Kind regards,
Evil.

---

### Post by SunnyRabbiera on 2008-10-26
my take:

> 1. I know that there are no Viruses on Unix but i am superstitious so Is there a Virus Protection program for Ubuntu ? - *on Windows i was using Kaspersky. i don't think it is available for Ubuntu.*
As others have mentioned there is ClamAV, but its mainly for windows viruses.
Clam comes in handy when you are sharing files with your windows using friends, Clam is very useful to ensure you dont pass on infected files on by mistake.
But warning clam is not a GUI app by default, there are frontends for it though, my favorite is klamAV

> 2. Is there a "Windows Live Messenger" for Ubuntu ?
aMSN is the closest you can get here, Microsoft hates linux as it competes with windows directly (heaven forbid! ;)) but there are many alternatives to it.

> 3. From reading on Ubuntu, I understand that not all programs and games will run on Ubuntu, however there are alternatives for those programs. but what about games, does Ubuntu run games ?

Example - _World in Conflict, Crysis, Call of Duty, Warcraft, Company of Heroes_

Games are win some, loose some.
Wine is very good at its job, though not all games will work, for gaming dual boot.

> 4. If the answer to {3} is YES - Windows has Direct X to show the ability of graphics, specially the difference from Direct X 9 & Direct X 10. so is there such a thing for Ubuntu, or does all games run on standard graphics.
As others have mentioned openGL is our answer to directX, actually opengl is better then directx as for one its cross platform and two its open source :D

> 5. Under { System => Preferences => Appearance } under the "Visual Effect" tab, i finally was able to click on Extra. but i was wondering if there was a more visual effects on ubuntu ? *- Like for example i saw on a video on ubuntu that once you click on a menu and jump to a sub menu. the main menu will disappear but in a cool visual effect. like fire or such.*

There are many hidden effects for ubuntu, but fair warning it depends on your video card on how far you can go.
There is an application you can install via the repositories called compiz-fusion-plugins-extra
also you can install the advanced compiz config tools via the repositories too like Compiz configuration settings manager

> 
6. Is it possible to use another Explorer other than "Fire Fox" ? like for example "Chrome" the Google explorer.
We dont usually use internet explorer here, IE is controlled by microsoft so its not a standard here as it is on windows.
Firefox should get you by for the most part and if you bump into a page that demands MSIE you can install ies4linux:
[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

There is also Opera and countless other browsers you can use on linux.

> 7. When i installed Ubuntu the first time it was 7.10, but back then almost nothing was running specially my graphic card. so i uninstalled it. now that its 8.04, so my question is. is the New Updated Ubuntu stable and can actually "Exchange" Windows Vista ? -* because to be honest i would love to think so.*

What?

> 8. Is there like a "Defrag" option on Ubuntu or like Disk Scan ?
No, its not needed, though every 25 boots or so the system will check itself for errors.

> 
9. This might not be an Easy one. but i tried installing another language and i think it worked successfully. however when i tried opening the Microsoft Word file with "Open Office Word Processor" the file was opened but the letters were backwards. so is that because i didn't install the second language correctly or is it because Open Office can not run Microsoft files.
Open office can open up MS files, but sometimes you may need to tweak it for more then one language.
I am unsure how to do this, but I know there are a number of language packs for open office in the repositories.

> 10. Are there like special Video Codecs for Ubuntu, like DivX, Real Player, Quick Time. or does the Video player on Ubuntu runs all kind of videos regardless of the type ?
You will probably need codecs yes, the best way to start is by using the medibuntu repositories:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
By defult Ubuntu doesnt come with a lot of multimedia stuff as most of that stuff cannot be distributed in some nations, so you will have to get codecs on your own.
But no worries if you need instructions we can show you how to get most media working under ubuntu :D

> 
I apologies for all the questions, and would like to thank you for reading my post.

Many thanks and appreciation in advance.

Asking questions is th best way to learn, so dont worry about asking so much

---

### Post by Evil79 on 2008-10-27
Thank you so much " [COLOR="Red"]SunnyRabbiera[/COLOR] " I really appreciate it allot. and will try all of that once iam back from work. I didn't know about Compiz Extra!! now iam super excited.

Again thanks alot for your time. Much appreciated.

Kind regards,
Evil.

---

### Post by Sef on 2008-10-27
>  	Quote:
 	 	 		 			 				2. Is there a "Windows Live Messenger" for Ubuntu ? 			 		 	 	 
aMSN is the closest you can get here, Microsoft hates linux as it competes with windows directly (heaven forbid! :wink:) but there are many alternatives to it.

Also there is emesene.  It is available in the universe repositoiry.

---

### Post by ad_267 on 2008-10-27
The only thing I have to add is that Emesene is another possible alternative to MSN Messenger. I've had issues with Pidgin and MSN but no problems with emesene.

Edit: Damn, beaten to it.

---

### Post by prismpirate on 2008-10-27
> **Evil79 said:**
> Greetings Ladies & Gents,

First of all I would like to apologies because I know those questions might have been asked before, but I couldn't find any on the topics.

Since the day i understood what a computer meant, i have never seen an OS system that i liked except for Windows. till now of course, i like Ubuntu a lot and would like to know and learn as much as possible about it. so I am sorry for the million questions.

1. I know that there are no Viruses on Unix but i am superstitious so Is there a Virus Protection program for Ubuntu ? - *on Windows i was using Kaspersky. i don't think it is available for Ubuntu.*

2. Is there a "Windows Live Messenger" for Ubuntu ?

3. From reading on Ubuntu, I understand that not all programs and games will run on Ubuntu, however there are alternatives for those programs. but what about games, does Ubuntu run games ?

Example - _World in Conflict, Crysis, Call of Duty, Warcraft, Company of Heroes_.

4. If the answer to {3} is YES - Windows has Direct X to show the ability of graphics, specially the difference from Direct X 9 & Direct X 10. so is there such a thing for Ubuntu, or does all games run on standard graphics.

5. Under { System => Preferences => Appearance } under the "Visual Effect" tab, i finally was able to click on Extra. but i was wondering if there was a more visual effects on ubuntu ? *- Like for example i saw on a video on ubuntu that once you click on a menu and jump to a sub menu. the main menu will disappear but in a cool visual effect. like fire or such.*

6. Is it possible to use another Explorer other than "Fire Fox" ? like for example "Chrome" the Google explorer.

7. When i installed Ubuntu the first time it was 7.10, but back then almost nothing was running specially my graphic card. so i uninstalled it. now that its 8.04, so my question is. is the New Updated Ubuntu stable and can actually "Exchange" Windows Vista ? -* because to be honest i would love to think so.*

8. Is there like a "Defrag" option on Ubuntu or like Disk Scan ?

9. This might not be an Easy one. but i tried installing another language and i think it worked successfully. however when i tried opening the Microsoft Word file with "Open Office Word Processor" the file was opened but the letters were backwards. so is that because i didn't install the second language correctly or is it because Open Office can not run Microsoft files.

10. Are there like special Video Codecs for Ubuntu, like DivX, Real Player, Quick Time. or does the Video player on Ubuntu runs all kind of videos regardless of the type ?


I apologies for all the questions, and would like to thank you for reading my post.

Many thanks and appreciation in advance.

Kind regards,
Evil.

1. I do not think there is a need for Antivirus on Ubuntu. However, if having one makes you feel safe, then you could always use ClamAV.

2. Microsoft obviously does not make Windows Live Messenger for Ubuntu or any other linux distribution, as far as I know. However, I suggest using emesene, which supports offline messaging as well.

3. I can only vouch for Warcraft III running on Ubuntu through wine, although if you mean whether any other games run on Ubuntu, sure there is. Currently, we have [playdeb]("http://www.playdeb.net") which has a list of games which you could try out. Personally, I prefer Battle for Wesnoth and Tremulous, both of which can be found in Add/Remove programs in Ubuntu

4. Ubuntu has OpenGL, although I am not very sure myself on what it actually means or does.

5.Copy and paste this in the terminal (Applications > Accessories > Terminal ):

```

sudo apt-get install cssm

```

You should be prompted to type in your password, which allows you to install the program. After installation, go to System > Preferences > Compiz Settings Manager (Or something like that). The configuration manager should pop up. Navigate to Animations, and tweak it as you wish.

6.You can run [ephiphany]("http://www.gnome.org/projects/epiphany/") or [Google Chrome]("http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb"), or even Opera 9.5. There are plenty of web browsers available for Ubuntu.

7. I am positive that it is still not possible to replace Windows with Ubuntu as there are still many applications that we use that are not supported in Ubuntu (i.e AutoCad) Mark Shuttleworth has also mentioned that 
> "I'm very nervous of encouraging people to substitute Windows for Linux," Shuttleworth said during a recent interview. "It's great if you are able and willing to recraft the way you do things in your organisation," such as adopting thin-client computing. Where people just want to switch desktop operating systems, things get very difficult."

[Source]("http://www.theregister.co.uk/2008/09/03/shuttleworth_linux_desktop_fear/")

8. I have never needed to defrag my Ubuntu Partition, maybe this is because Ubuntu uses the ext3 filesystem?

9.What language are you using? (Displaying backwards...)

10. To resolve this, just navigate to Add/Remove Programs, search for Ubuntu Restricted Extras, check the checkbox and install.

---

### Post by em4r1z on 2008-10-27
1. There're viruses and other security threats that affect Unix-like OS's but they're way less common. Try Avast! or ClamAV, specially if you share your files with many Windows users for even if you're not infected you can spread the threat.

2. Pidgin or Empathy.

5. Install CompizConfig Settings Manager.

6. Opera, Konqueror, Flock, Epiphany. 

7. Use the Ubuntu 8.04 and 8.10 LiveCD to test the hardware compatibility on your machine.

8. Linux's filesystems use different tecniques to reduce fragmentation. Depending on your filesystem (ext3, JFS, XFS, ReiserFS, etc.) there might be a 'defrag' tool. This issue is not as important as it is in Windows, though. 

9. Which language?
Make sure you're not confusing interface translations with language support packages for applications.

10. You can play almost any media type if the proper codec's are installed.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Evil79 on 2008-10-27
> **Sef said:**
> Also there is emesene.  It is available in the universe repositoiry.

Thanks alot "[COLOR="Red"]Sef[/COLOR]", i will try downloading that once iam back from work.

Many thanks for the help and your time.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-27
> **ad_267 said:**
> The only thing I have to add is that Emesene is another possible alternative to MSN Messenger. I've had issues with Pidgin and MSN but no problems with emesene.

Edit: Damn, beaten to it.

Not a problem still thanks alot "[COLOR="Red"]ad_267[/COLOR]", i will try downloading that once iam back from work.

Many thanks for the help and your time.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-27
> **prismpirate said:**
> 1. I do not think there is a need for Antivirus on Ubuntu. However, if having one makes you feel safe, then you could always use ClamAV.

2. Microsoft obviously does not make Windows Live Messenger for Ubuntu or any other linux distribution, as far as I know. However, I suggest using emesene, which supports offline messaging as well.

3. I can only vouch for Warcraft III running on Ubuntu through wine, although if you mean whether any other games run on Ubuntu, sure there is. Currently, we have [playdeb]("http://www.playdeb.net") which has a list of games which you could try out. Personally, I prefer Battle for Wesnoth and Tremulous, both of which can be found in Add/Remove programs in Ubuntu

4. Ubuntu has OpenGL, although I am not very sure myself on what it actually means or does.

5.Copy and paste this in the terminal (Applications > Accessories > Terminal ):

```

sudo apt-get install cssm

```

You should be prompted to type in your password, which allows you to install the program. After installation, go to System > Preferences > Compiz Settings Manager (Or something like that). The configuration manager should pop up. Navigate to Animations, and tweak it as you wish.

6.You can run [ephiphany]("http://www.gnome.org/projects/epiphany/") or [Google Chrome]("http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb"), or even Opera 9.5. There are plenty of web browsers available for Ubuntu.

7. I am positive that it is still not possible to replace Windows with Ubuntu as there are still many applications that we use that are not supported in Ubuntu (i.e AutoCad) Mark Shuttleworth has also mentioned that 

[Source]("http://www.theregister.co.uk/2008/09/03/shuttleworth_linux_desktop_fear/")

8. I have never needed to defrag my Ubuntu Partition, maybe this is because Ubuntu uses the ext3 filesystem?

9.What language are you using? (Displaying backwards...)

10. To resolve this, just navigate to Add/Remove Programs, search for Ubuntu Restricted Extras, check the checkbox and install.

Thanks alot "[COLOR="Red"]prismpirate[/COLOR]", I will use that on the terminal. i hope that will be the magic touch needed to get all of the graphic effects on.

And regarding the Language, it is "Arabic". I do not care about the interface. because i want it to be in English. however what i was asking about is the Typing language to have a second language which is Arabic.

And apparently my old Arabic Microsoft word files. will open under Open Office. but the words will come in backwards.

Many thanks for the help and your time.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-27
> **em4r1z said:**
> 1. There're viruses and other security threats that affect Unix-like OS's but they're way less common. Try Avast! or ClamAV, specially if you share your files with many Windows users for even if you're not infected you can spread the threat.

2. Pidgin or Empathy.

5. Install CompizConfig Settings Manager.

6. Opera, Konqueror, Flock, Epiphany. 

7. Use the Ubuntu 8.04 and 8.10 LiveCD to test the hardware compatibility on your machine.

8. Linux's filesystems use different tecniques to reduce fragmentation. Depending on your filesystem (ext3, JFS, XFS, ReiserFS, etc.) there might be a 'defrag' tool. This issue is not as important as it is in Windows, though. 

9. Which language?
Make sure you're not confusing interface translations with language support packages for applications.

10. You can play almost any media type if the proper codec's are installed.
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Thanks alot "[COLOR="Red"]em4r1z[/COLOR]", Much appreciated.

And regarding the Language, it is "Arabic". I do not care about the interface. because i want it to be in English. however what i was asking about is the Typing language to have a second language which is Arabic.

Apparently my old Arabic Microsoft word files. will open under Open Office. but the words will come in backwards.

Many thanks for the help and your time.

Kind regards,
Evil.

---

### Post by hyper_ch on 2008-10-27
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Evil79 on 2008-10-27
> **hyper_ch said:**
> It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

Well problem is, as i understood from other forums it is not recomended to post several posts if they are all questions. thats why i posted all of my questions in one post to make it easier for those who check my post.

Also i admit iam **the GOD of all noobs, the LORD of all noobs, the Ultimate King of all noobs** when it comes to Ubuntu!, simply because iam new to it. since the day i have understood the meaning of a PC. i never thought that there are other Operating Systems. or even if we had a choice! thats why when i use Ubuntu i feel totaly lost. kind of like if you were using Windows 3.11 then jumped to Windows Vista kind of feeling.

That said, i agree i should have explained more on my topic title to give a clear topic to those with the knewledge to help me.

> **hyper_ch said:**
> 
And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Again you are talking to some one who used simple forums. like World of Warcraft forums or Sony Ericsson X1 Forums. i did not even know that there is an actuall option to mark each post as "Solved" to help otheres know that iam done.

For that i Apologies.

> **hyper_ch said:**
> 
Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

I do not need to remind you what level am i as a noob. i mean you are talking to some one who Installed "Ubuntu" just and i repeate just for the cool graphic effects because it is better than windows. i installed it because it has more eye candy than windows.

so do you think, or is it even logical that a person like me, would even understand what are those lines you just typed ? i mean till this day i have no idea what is the "Terminal" and why is it that everyone is sending me to it and asking me to type stuff in it.

i even call it "Command Prompt" so to me it is the DOS of unix

So Iam sorry that i do not have as much information as you kind sir, but iam just a noob who likes graphic effects and would love to learn more about Ubuntu so i can use it to the fullest.

Regardless, thank you so much "[COLOR="Red"]hyper_ch[/COLOR]" for reading my post. and for all of the help and tips. i really appreciate it.

Kind regards,
Evil.

---

### Post by Evil79 on 2008-10-27
> **prismpirate said:**
> 1. I do not think there is a need for Antivirus on Ubuntu. However, if having one makes you feel safe, then you could always use ClamAV.

2. Microsoft obviously does not make Windows Live Messenger for Ubuntu or any other linux distribution, as far as I know. However, I suggest using emesene, which supports offline messaging as well.

3. I can only vouch for Warcraft III running on Ubuntu through wine, although if you mean whether any other games run on Ubuntu, sure there is. Currently, we have [playdeb]("http://www.playdeb.net") which has a list of games which you could try out. Personally, I prefer Battle for Wesnoth and Tremulous, both of which can be found in Add/Remove programs in Ubuntu

4. Ubuntu has OpenGL, although I am not very sure myself on what it actually means or does.

5.Copy and paste this in the terminal (Applications > Accessories > Terminal ):

```

sudo apt-get install cssm

```

You should be prompted to type in your password, which allows you to install the program. After installation, go to System > Preferences > Compiz Settings Manager (Or something like that). The configuration manager should pop up. Navigate to Animations, and tweak it as you wish.

6.You can run [ephiphany]("http://www.gnome.org/projects/epiphany/") or [Google Chrome]("http://media.codeweavers.com/pub/crossover/chromium/cxchromium_0.9.0-1_i386.deb"), or even Opera 9.5. There are plenty of web browsers available for Ubuntu.

7. I am positive that it is still not possible to replace Windows with Ubuntu as there are still many applications that we use that are not supported in Ubuntu (i.e AutoCad) Mark Shuttleworth has also mentioned that 

[Source]("http://www.theregister.co.uk/2008/09/03/shuttleworth_linux_desktop_fear/")

8. I have never needed to defrag my Ubuntu Partition, maybe this is because Ubuntu uses the ext3 filesystem?

9.What language are you using? (Displaying backwards...)

10. To resolve this, just navigate to Add/Remove Programs, search for Ubuntu Restricted Extras, check the checkbox and install.

Ok when i tried typing "sudo apt-get install cssm" i got the following

[[img]http://xs432.xs.to/xs432/08441/screenshot971.png[/img]](http://xs.to)

Any idea what should i do so i can install Compiz please.

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by reg4c on 2008-10-27
> **Evil79 said:**
> Greetings Ladies & Gents,

First of all I would like to apologies because I know those questions might have been asked before, but I couldn't find any on the topics.

Since the day i understood what a computer meant, i have never seen an OS system that i liked ...

1. Linux does not use antiviruses it uses firewalls. Mostly people use ufw and Firestarter [look in the Add/Remove for it].

2. Ubuntu does not have WLM per se but does have some alternatives: Pidgin, Kopete [KDE so not really recommended for Ubuntu because of dependencies], aMSN, emesene.

3. ```
 sudo apt-get install wine 
```
This is the Windows set of libraries allowing you to run some Windows programmes on Linux. After some tinkering I have WoW, WC3, CoD2 and some other stuff running. 

4. Am not sure about this.

5. ```
sudo apt-get install compizconfig-settings-manager
```
This will give you a whole bunch of new customizations that you couldn't have even dreamt about in Vista.

6. You have a whole bunch of other browsers for Linux but Firefox is the best IMO. There is Chromium [?] that is actually a port of GChrome for Linux but an official release is not there yet.

7. As an ex-Vista user I can say that I have not gone back to Vista for a good 6 months now. I know that is not a long time but considering that have not even booted into Win even once its progress. It has really replaced Vista for me.

8. You do not need to defrag your disks in Linux.

9. OpenOffice.org can open MS Office files normally especially with the OpenOffice.org 3.0 out now. Perhaps you did not install the language pack but installed just the keyboard layout.

10. As for the codecs, when you install Ubuntu and try to play a file like .avi or .mp3 you will be asked to download the codec pack which you do once and then everything plays.
Also, I recommend installing VLC media player for video files that is really simple and plays everything perfectly'
```
sudo apt-get install vlc
```

Also, if it makes any difference, the Ubuntu community has fixed all my issues in record time which was very helpful when switching to Ubuntu.
Just make sure to search the forums first and if you do post to have a descriptive title.

Happy switching
Cheers

---

### Post by dracayr on 2008-10-27
it has to be compizconfig-settings-manager, not ccsm in the command

dracayr

---

### Post by ad_267 on 2008-10-27
You don't have to use the command line either, you can just go to System - Administration - Synaptic Package Manager and search for it.

---

### Post by Evil79 on 2008-10-27
Thank you "[COLOR="Red"]reg4c[/COLOR]" & "[COLOR="Red"]dracayr[/COLOR]" & "[COLOR="Red"]ad_267[/COLOR]" for replying and for your time.

The issue with Graphics is that i can't find the Compiz option or icon anywhere. and i can't install it simply because it is already installed just as in the attached screen shot.

[[img]http://xs432.xs.to/xs432/08441/snapshot3466.png[/img]](http://xs.to)

Any help you can advice me with Gents ? because iam lost.

Many thanks and appreciation in advance.

Kind regards,
Evil.

---

### Post by ad_267 on 2008-10-27
Looks like you don't have the extra repositories enabled. Go to system - administration - software sources and tick next to the universe, restricted and multiverse sources.

It seems like these are enabled by default for some people but not for others. Anyone know why? Does this depend on the country you are in?

---

### Post by Evil79 on 2008-10-28
> **ad_267 said:**
> Looks like you don't have the extra repositories enabled. Go to system - administration - software sources and tick next to the universe, restricted and multiverse sources.

It seems like these are enabled by default for some people but not for others. Anyone know why? Does this depend on the country you are in?

Indeed, finaly that was it. i found a whole new icons when i activated that and changed my server from the main server to the best server based on my location.

and now i got several glitter and cool graphical effects. iam lovin it.

Thanks alot "[COLOR="Red"]ad_267[/COLOR]" for the help and for your time.

Much appreciated.

Kind regards.
Evil

---

