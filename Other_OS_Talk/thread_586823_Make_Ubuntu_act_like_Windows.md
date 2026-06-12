---
title: "Make Ubuntu act like Windows"
date: 2007-10-22
forum: Other OS Talk
---

### Post by siege911 on 2007-10-22
Alright, I decided to write this little article before delving too deep into Ubuntu.

I've used Feisty for a web server and just got Gutsy. Since I've had little experience with Ubuntu (and Linux in general), I wanted to try and give my first opinions on it before I fall in love with it and start hating Windows. So I'm just going to give some first impressions which may help some people understand why most users still use Windows (aside from Microsoft's monopolistic attitude) and what Ubuntu should learn from that.

##########

My first negative impression was the color scheme. I just don't like it. The orange isn't very friendly. I think you need more welcoming colors like yellows, blues and greens. The Windows XP grassy hills is a great example of a good default background and the blue taskbar on the bottom is great. I briefly installed the Kubuntu Desktop and found that KDE was a much more friendly looking desktop. Beyond that I despised KDE and removed it...don't want to start a discussion about that... but the point is that people are first going to want it to look welcoming. I think you need to put a huge importance on graphic design when designing the OS. Ubuntu seems to place some importance but not a huge amount.

Now I know a lot of people are going to want to quickly comment how you can change the theme and all of that, but I'm trying to go about this from a computer illiterate perspective. A computer illiterate person will never change much more than their background wallpaper. Since Ubuntu is Linux for Humans, I'm assuming they mean ALL humans, rather than just tech savvy humans.

#########

My first positive impression was the eye-candy. I installed Ubuntu 7.10 on a 3 year old computer and was still able to get all of the Eye Candy out of it with no lag or skip. It was a lot more pretty than Vista especially after I turned the Appearance Settings up to Extra. The only suggestions I would make in this area is to include the Compiz Advanced Settings Manager (or whatever it's called) on install for some of the slightly more advanced users. I couldn't understand why I couldn't get the cube to work until I searched around the forums a bit. If you have to search these forums for help on your OS, then you can assume the average basic user will never know such information.

##########

My second positive impression was the Add/Remove Programs feature. There is no better feature than that. This was so much better than the traditional way of putting a CD in the drive, going through a whole new install process for each program, and hoping it worked. The only suggestion on this area is you may want to add a "Repository on the fly feature" or something like that. This way if you want to download something that's not in the default repositories, you could copy and paste the address provided by the program company into a box and only the packages from that repo would show up. Then when you are finished downloading, and you close it, that Repo goes away. I do know you can go through preferences and add 3rd party repos but that's just not as user-friendly. Remember that we are dealing with computer illiterate people.

Another suggestion would be a "Purchase Repository" which would have non-Open Source software that people could buy. You could put in your credit card information and receive an unlock key for the software as well as download it. I know that might be heresy on these boards but not everyone is die-hard about Open Source. Remember: ALL humans.

###########


My next negative impression was a lack of gaming support. I hear this is probably the primary complaint about Linux. While I haven't actually used such programs, I've heard there are several programs that can mimic Windows enough to allow for certain Windows based programs or games to function properly. Personally, I would include such programs as stock until Ubuntu (and/or other Linux distro) gains enough market share for companies to want to make Linux versions of the game/app. I know these may be complicated to run, but I see that necessary in order to convince people to change over.

I was recently trying to get my dad to switch over to Ubuntu. He said he was cool with it but he asked if it played his games (he's really into RTS games). My answer was "no". I'm sure I could get his games to play on his machine with enough mods and hacks, but he's not computer literate and if he ever got a new game, I'd have to fly from Arizona to Seattle to configure it for him. And I'm just not going to do that. So more Windows based support would be a HUGE factor in getting market share.

##########

My next complaint is the pure number of Distros out there. We have choices between RHE, Fedora, CentOS, Ubuntu, Mandriva, PCLinuxOS, OpenSUSE, etc. Those are just the few I could name off the top of my head without searching and I'm brand new to Linux. Everybody seems to be fighting each other for the .8% or so of the market share that's currently for Linux. I know Open Source tends to have a tendency towards that, but it confuses people. It's hard to explain to a computer illiterate person what the differences are. It's difficult to learn that I need a .deb package for Ubuntu and not a .rpm package even though they are both for Linux. And on top of that, Ubuntu is not really it's own distro, it's a Debian based distro. Even more confusing.

"So Ubuntu is Linux"
"Yes"
"So why can't I install this program?"
"Because that's based off of RPM and doesn't work with Ubuntu"
"What's the difference"
"They are just different types of Linux"
"Oh so I need something that's based off of Ubuntu Linux?"
"No, you need something that's based off of Debian"
"What's Debian?"
"It's what Ubuntu is"
"I thought Ubuntu is Linux"
"It is"
"???"

Get the picture? It's not very friendly towards computer illiterate people.

Not sure there is a solution, I just wish people would combine their efforts rather than divide them. But I think that's more just a dream of mine than anything. However, this whole thought may be something to look at regarding marketing Ubuntu. Trying to eliminate some of that confusion.


############

My next complaint is the Terminal and Config files. These seem to be popular among Linux users. I tried Red Hat linux several years ago and all I could find was information about config files and terminal codes. I ended up not touching Linux till now. If you are going to be user friendly, you have to get rid of those for all practical purposes. Ubuntu has done a pretty decent job of doing that but it still has some work ahead. Replace all config files and terminal entries with visual interfaces to do your configs and people will be happy. In Windows XP, in order to get to the "terminal", you have to go to Run -> "cmd". In Linux you have to run a Terminal command at some point while using it.

Now I don't think the Terminal and Config files should disappear all-together, but there should be viable alternatives for the basic user.


###########


My last complaint is file security. Not lack there-of, but too much that it's hindering. Personally I think Windows can be a little lax in it's security but it's getting better. Windows automatically assumes full control of it's file system to the Administrator account. Linux assumes no control of it's file system to it's Administrator account and so you have to use the Terminal (see my previous complaint) using "sudo" or "chown" or the like to do anything using the root account. There has to be some sort of middle ground or at least options. I do like that Gutsy includes a Home, Documents, Music, etc folder similar to Windows which allows full control. What I would like to see is at least two options for security.

1. Full security. This would basically be exactly as it is now.

2. Basic security. This would be for the average user. It would default most files to Read Only, but allow the right click -> Properties of the file or folder to allow writable (or even a once writable option for a single editing session). Then you could use more of the system with more ease. It would allow the moderately technical (like myself) people to edit the config files if they want but not allowing people to easily delete system files or edit important documents without a little intervention by the user.

I know a lot of the Linux fanatics here would hate this, but the other 99% of the world would probably appreciate it. I know I would. I recently tried my first try at a webserver. All I wanted to do was go to the Apache config files via the file browser and change some settings. I was forced to use "sudo gedit" or "chown" in order to edit. It was more frustrating than I wanted.






So that's my little article. I personally am growing to like Ubuntu more and more (to the point where I'm only going to have only 1 Windows box left for gaming), and I think Ubuntu is fast becoming a viable replacement for Windows, however there is still some work to go.

Hopefully this doesn't start a flame war or anything like that. It's just my thoughts.

---

### Post by fr££ on 2007-10-22
> **siege911 said:**
> 
2. Basic security. This would be for the average user. It would default most files to Read Only, but allow the right click -> Properties of the file or folder to allow writable 

You did try to right-click, yes? The permissions  menu doesn't give you the functionality you speak of? You can do pretty much what chmod and chown can do through the gui; only of course you lack some options (not a concern to "average users") and the ability to script the commands (again, not a concern to "average users").

TBH I haven't checked that this is available through the gnome window manager, as I'm running KDE, or perhaps I have misunderstood altogether what you mean. You may want to give the KDE look and feel a try if you haven't; many ex-windows users seem to prefer it (myself included).

---

### Post by TKR101010 on 2007-10-22
> TBH I haven't checked that this is available through the gnome window manager, as I'm running KDE, or perhaps I have misunderstood altogether what you mean.

If you're talking about being able to change the permissions via the "Permissions" tab in a files properties, then yes, it does work the same in gnome.

>  My first negative impression was the color scheme. I just don't like it. The orange isn't very friendly. I think you need more welcoming colors like yellows, blues and greens. but the point is that people are first going to want it to look welcoming.

I guess it's a matter of opinion. I liked the orange/brown "Human" theme of Ubuntu when I first installed it. I have since installed the UbuntuStudio-desktop theme, and although I really like the glossy black taskbars and such, I wish the progress bars, scroll bars and such had stayed orange instead of turning blue. If I knew how to easily change that (without uninstalling the UbuntuStudio theme as I like the rest of it) I would change it back to the orange, or maybe even a nice red.

>  Remember that we are dealing with computer illiterate people.

If someone is computer illiterate, they're still probably going to have a hard time as linux itself requires more user interaction with the os than windows. When it comes to windows I consider myself to be at least average in my knowledge, if not a bit above. Sure I may not be a programer and writing my own applications, but I can tweak things to my liking and get down nearly all the things I need to. I had been a windows user for at least 10 years, and just switched to linux in the last couple of months. Although Ubuntu is great and makes things easier than other linux distros I tried (I tried switching to linux a couple times before, but found it too difficult), I'm still very much a newbie, trying to learn the new os, and get lost often. I think linux is just something that requires more learning than windows. But even if I'm getting lost sometimes, linux (in general) doesn't need to dumb itself down for me, I need to use the opportunity to learn and therefore be more educated and better able to handle such things myself.

>  My next complaint is the pure number of Distros out there. We have choices between RHE, Fedora, CentOS, Ubuntu, Mandriva, PCLinuxOS, OpenSUSE, etc. I know Open Source tends to have a tendency towards that, but it confuses people. It's hard to explain to a computer illiterate person what the differences are.

What? You're complaining because you have too many choices? I'd rather have 1000 choices and find the one I want/need (even if it took me a while) than to have only 2 or 3 choices and find that none of them are what I want/need.

You keep mentioning these 'computer illiterate' people. Like I said before, I'm no programmer, and I'm definitely no network systems administrator or anything like that, and I even have difficulties installing some programs if I can't find instructions, but I am a human being and human beings are capable of learning. Instead of dumbing everything down for those who haven't caught on yet, why not encourage these 'computer illiterates' to educate themselves? Personally I like the learning process. When I figure something out, I get a little feeling of accomplishment about it :)

> It's difficult to learn that I need a .deb package for Ubuntu and not a .rpm package even though they are both for Linux.

Is it really that hard? That was one of the first things I learned about Ubuntu when I started looking for software to use. How can if be all that difficult to learn if you've just pretty much summed it up in one sentence and with a very minimum of computer jargon? 

Also, who's going to combine all these distros so that there are fewer of them? Nobody. They exist because different people have different needs, wants, and expectations. Even Ubuntu has at least 5 distributions (Ubuntu, Kubuntu, Xubuntu, Gobuntu, and Edubuntu) each of which is geared towards meeting the needs of different groups. Lets say that they consolidated all of them into one disto, UbuntuGeneric. That would completely invalidate the purpose of Xubuntu which is designed for people with older systems that don't have as much RAM as newer systems. So by combining just the Ubuntu distros, you're eliminating people who might otherwise be using the os.

l8rz,

TKR101010

---

### Post by LowSky on 2007-10-22
I think it would be nice to have one DVD Live CD that lets oyu try all the *buntu flavors, give people a choice of what they might like.

An ubuntu can be for computer morons (they can read so they are not illiterate in my book).

I set up my firend (who barely know windows) with a Ubuntu 7.04 machine, I turned on beryl/with the cube function, showed him how to change the wallpaper, gave him access to flash, java, mp3, encoded DVDs, and he is happy and content. All he needs it for is the internet and music and dvds. To him Ubuntu is perfect, and he's even making our other firends want linux if it can do all that stuff, without having to buy windows.

So in my opinion anyone can use ubuntu, you just have to want to change. Thats it, I don't want to hear excuses about the need for pretty GUIs and no need for terminal, because windows still needs terminal commands every once and a while (it was the only way to set up my wifi card to work was terminal commands to get into a registry file).

Look at Apple, it thinks customers can live with a terminal command every once in a while. And if I recall dosen't Apple build the "world's easiest to use computers"

The one thing I do like is your purchase repository idea, but your not the first to come up with the idea. The company Valve created Steam to sell games over the internet. Sooner or later they might make a linux version of their program and linux users will have games. Time will tell.

---

### Post by siege911 on 2007-10-22
> **fr££ said:**
> You did try to right-click, yes? The permissions  menu doesn't give you the functionality you speak of? You can do pretty much what chmod and chown can do through the gui; only of course you lack some options (not a concern to "average users") and the ability to script the commands (again, not a concern to "average users").
Yes I was talking about right-click. I went to "Random File X", right clicked on a file, and went to permissions. The file said the owner was root and I couldn't change any permissions. One the bottom it said "You are not the owner so you cannot change the permissions".

That's what I'm talking about. I have to "chown" it to myself in order to play with it. Unless I completely missed something.

---

### Post by igknighted on 2007-10-22
Much of what you wrote points to one rather in-escapable conclusion: Linux is not for you.  Keep in mind that the #1 person the linux developer is writing the programs for is, well, themselves.  They want an application that fits their needs.  I HIGHLY recommend you read this article ([http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")).  It will not convince you that linux is better, it will not convince you that we are right and windows is wrong... but it will help you to learn why we really just don't care about 90% of what you posted.  It has been posted by new users a million times before.  So while you think you have the brilliant points (and your points are well thought out and insightful, I'm not mocking them), they are hardly anything we haven't heard before.  And there are some points that we are in fact working on (like for example a universal packaging system).  But by and large, your points are relevant to a windows user.  We don't feel like we should try to reverse engineer the windows API to get windows binaries to run... and why should we?  We would rather make those games have linux installers as well.  And since there is only so much volunteer manpower available, we have to make a choice.

My recommendation to you is this.  Hang around, keep using linux, and really start to understand it and how it works.  Only then will you understand why posts like this fall on deaf ears (or since its online, i guess blind eyes would be more accurate).  I don't mean to be rude, but quite simply, your post wont change anything, so it comes off as whining.  Put in your time, and if you still feel strongly about any of this, then get involved and make it a reality.

---

### Post by siege911 on 2007-10-22
> Much of what you wrote points to one rather in-escapable conclusion: Linux is not for you.

Actually, my point was not to bash Linux if that is what you think I was doing. I'm currently in the process of all but switching over to Ubuntu. I convinced my cousin to switch his home laptop over to Ubuntu instead of getting a new laptop (he was complaining about the Blue Screen of Death so he was going to buy a whole new computer). I've almost convinced a friend at work to change over to Ubuntu since he was asking me whether he should go Mac or PC. I want to convince my dad to switch over but he's running some specialized boating navigation software that may only run on Windows on one of his machines and plays games on another (which obviously doesn't work well with Linux).

I like Ubuntu. But I'm not afraid to use the terminal or to play with some config files. I don't mind doing a little tweaking to get something to work right. It's just hard to convince others to do the same. I always get asked the same questions: "Will it work with Windows App X?" Sometimes I can say yes (or a semi yes... like OpenOffice when I get the Microsoft Word question). Most of the time it's a no.

That's the point of saying all of this. And I understand some things won't happen, like making all Windows apps run on Ubuntu (though including software like WINE would be helpful), but some of the things shouldn't be too far out there. Getting rid of config files and the terminal as much as possible would be a top priority IMO. But I do understand that Open Source developers are primarily developing for themselves rather than others so it is understandable. It was just a few thoughts anyways.

---

### Post by wheredidrealitygo on 2007-10-22
How about we don't make Ubuntu act like Windows, and keep making it act like.. Ubuntu.

> "It's hard to explain to a computer illiterate person what the differences are."

Most people that are using Ubuntu will not be computer illiterate, and if they are, they will have had someone that is computer literate show them how to do basic things, just like computer illiterate people on Windows. Computer illiterate Ubuntu users won't need to know these things because just like Windows users, they won't care enough to understand these differences.

> "My next complaint is the Terminal and Config files."

The terminal is very, very powerful for those of us who wish to use it on a regular basis, and we have no wish to get rid of it. Config files are much easier to manipulate than an interminably large registry, with assorted .dll files spread out along the C: for good measure.

> 
"Another suggestion would be a "Purchase Repository" which would have non-Open Source software that people could buy."

Linspire is exactly this, Ubuntu based, but available to be purchased. Ubuntu itself is not, nor will ever be (I hope) "purchasable", nor anything in it's repositories. That defeats the entire purpose of a Free Operating System.

I'm getting frustrated reading these types of post, and am going to refrain from posting anything inflammatory.

---

### Post by edd07 on 2007-10-22
> **wheredidrealitygo said:**
> Linspire is exactly this, Ubuntu based, but available to be purchased. Ubuntu itself is not, nor will ever be (I hope) "purchasable", nor anything in it's repositories. That defeats the entire purpose of a Free Operating System.
That's not true. Paying for software doesn't mean its not free (in the 'libre' sense). Large programs, especially games, take a lot of work and time to make, so I wouldn't object to pay for a really good Linux game. It will be Free as long as the source code is provided and you have the right to use it as you please.

---

### Post by wheredidrealitygo on 2007-10-22
> "That's not true. Paying for software doesn't mean its not free (in the 'libre' sense). Large programs, especially games, take a lot of work and time to make, so I wouldn't object to pay for a really good Linux game. It will be Free as long as the source code is provided and you have the right to use it as you please."

That sounds more like donating to an exemplary product, which is wonderful, I have no problems with that, but  what the OP was referencing was not open source: 

> Another suggestion would be a "Purchase Repository" which would have non-Open Source software that people could buy. You could put in your credit card information and receive an unlock key for the software as well as download it. I know that might be heresy on these boards but not everyone is die-hard about Open Source. Remember: ALL humans.

In this case, source code would not be provided, and we would be under restrictive licenses.

---

### Post by buddhacub1120 on 2007-10-22
ok so i'm sorry but i really want to switch back to windows vista. it just worked better with my machine. i love unbuntu but it's not worht all the hassles. for me at least. can anyone help me or point in the right direction on how to go about this smoothly? i also can't find my vista disk so imtrying to find a live disk to burn or something. thanks everyone.

---

### Post by wheredidrealitygo on 2007-10-22
Call your OEM (Original Equipment Manufacturer) and get them to send you a new dvd.

[This]("http://support.microsoft.com/default.aspx?scid=fh%3Ben-us%3Boemphone&LN=EN-US&x=8&y=14") is a list of USA-based phone numbers for all OEMs.

Have fun with Windows.

---

### Post by pelle.k on 2007-10-22
> My first negative impression was the color scheme. I just don't like it. The orange isn't very friendly. I think you need more welcoming colors like yellows, blues and greens
I can agree on that. Personally i like the standard "clearlooks" in gnome 2.20.

> Then when you are finished downloading, and you close it, that Repo goes away.
This is no better than installing debs with gdebi. You get no security updates, and you will probably not get this package updated when you move to a new version of ubuntu, causing conflicts in apt-get.

> It's difficult to learn that I need a .deb package for Ubuntu and not a .rpm package even though they are both for Linux. And on top of that, Ubuntu is not really it's own distro, it's a Debian based distro. Even more confusing.
We need a better standard of how packages are distributed and installed, yes. I agree :)

> My next complaint is the Terminal and Config files. These seem to be popular among Linux users.
Nothing wrong with that. I miss a common format though. The diversity in which config files are set up is just confusing.
Also, with a "standard", gui:s would be far more easier to create than now.

> you have to use the Terminal (see my previous complaint) using "sudo" or "chown" or the like to do anything using the root account
Well, there's nautilus-gksu (open as administrator) and nautilus-open-terminal if you would prefer that instead.

[B]
I wouldn't be too worried, linux is making progress. In it's own pace and direction. I have a feeling this is going to be a great ride. Don't worry :)[/B]

---

### Post by karellen on 2007-10-23
> **siege911 said:**
> Alright, I decided to write this little article before delving too deep into Ubuntu.

I've used Feisty for a web server and just got Gutsy. Since I've had little experience with Ubuntu (and Linux in general), I wanted to try and give my first opinions on it before I fall in love with it and start hating Windows. So I'm just going to give some first impressions which may help some people understand why most users still use Windows (aside from Microsoft's monopolistic attitude) and what Ubuntu should learn from that.

##########

My first negative impression was the color scheme. I just don't like it. The orange isn't very friendly. I think you need more welcoming colors like yellows, blues and greens. The Windows XP grassy hills is a great example of a good default background and the blue taskbar on the bottom is great. I briefly installed the Kubuntu Desktop and found that KDE was a much more friendly looking desktop. Beyond that I despised KDE and removed it...don't want to start a discussion about that... but the point is that people are first going to want it to look welcoming. I think you need to put a huge importance on graphic design when designing the OS. Ubuntu seems to place some importance but not a huge amount.

Now I know a lot of people are going to want to quickly comment how you can change the theme and all of that, but I'm trying to go about this from a computer illiterate perspective. A computer illiterate person will never change much more than their background wallpaper. Since Ubuntu is Linux for Humans, I'm assuming they mean ALL humans, rather than just tech savvy humans.

#########

My first positive impression was the eye-candy. I installed Ubuntu 7.10 on a 3 year old computer and was still able to get all of the Eye Candy out of it with no lag or skip. It was a lot more pretty than Vista especially after I turned the Appearance Settings up to Extra. The only suggestions I would make in this area is to include the Compiz Advanced Settings Manager (or whatever it's called) on install for some of the slightly more advanced users. I couldn't understand why I couldn't get the cube to work until I searched around the forums a bit. If you have to search these forums for help on your OS, then you can assume the average basic user will never know such information.

##########

My second positive impression was the Add/Remove Programs feature. There is no better feature than that. This was so much better than the traditional way of putting a CD in the drive, going through a whole new install process for each program, and hoping it worked. The only suggestion on this area is you may want to add a "Repository on the fly feature" or something like that. This way if you want to download something that's not in the default repositories, you could copy and paste the address provided by the program company into a box and only the packages from that repo would show up. Then when you are finished downloading, and you close it, that Repo goes away. I do know you can go through preferences and add 3rd party repos but that's just not as user-friendly. Remember that we are dealing with computer illiterate people.

Another suggestion would be a "Purchase Repository" which would have non-Open Source software that people could buy. You could put in your credit card information and receive an unlock key for the software as well as download it. I know that might be heresy on these boards but not everyone is die-hard about Open Source. Remember: ALL humans.

###########


My next negative impression was a lack of gaming support. I hear this is probably the primary complaint about Linux. While I haven't actually used such programs, I've heard there are several programs that can mimic Windows enough to allow for certain Windows based programs or games to function properly. Personally, I would include such programs as stock until Ubuntu (and/or other Linux distro) gains enough market share for companies to want to make Linux versions of the game/app. I know these may be complicated to run, but I see that necessary in order to convince people to change over.

I was recently trying to get my dad to switch over to Ubuntu. He said he was cool with it but he asked if it played his games (he's really into RTS games). My answer was "no". I'm sure I could get his games to play on his machine with enough mods and hacks, but he's not computer literate and if he ever got a new game, I'd have to fly from Arizona to Seattle to configure it for him. And I'm just not going to do that. So more Windows based support would be a HUGE factor in getting market share.

##########

My next complaint is the pure number of Distros out there. We have choices between RHE, Fedora, CentOS, Ubuntu, Mandriva, PCLinuxOS, OpenSUSE, etc. Those are just the few I could name off the top of my head without searching and I'm brand new to Linux. Everybody seems to be fighting each other for the .8% or so of the market share that's currently for Linux. I know Open Source tends to have a tendency towards that, but it confuses people. It's hard to explain to a computer illiterate person what the differences are. It's difficult to learn that I need a .deb package for Ubuntu and not a .rpm package even though they are both for Linux. And on top of that, Ubuntu is not really it's own distro, it's a Debian based distro. Even more confusing.

"So Ubuntu is Linux"
"Yes"
"So why can't I install this program?"
"Because that's based off of RPM and doesn't work with Ubuntu"
"What's the difference"
"They are just different types of Linux"
"Oh so I need something that's based off of Ubuntu Linux?"
"No, you need something that's based off of Debian"
"What's Debian?"
"It's what Ubuntu is"
"I thought Ubuntu is Linux"
"It is"
"???"

Get the picture? It's not very friendly towards computer illiterate people.

Not sure there is a solution, I just wish people would combine their efforts rather than divide them. But I think that's more just a dream of mine than anything. However, this whole thought may be something to look at regarding marketing Ubuntu. Trying to eliminate some of that confusion.


############

My next complaint is the Terminal and Config files. These seem to be popular among Linux users. I tried Red Hat linux several years ago and all I could find was information about config files and terminal codes. I ended up not touching Linux till now. If you are going to be user friendly, you have to get rid of those for all practical purposes. Ubuntu has done a pretty decent job of doing that but it still has some work ahead. Replace all config files and terminal entries with visual interfaces to do your configs and people will be happy. In Windows XP, in order to get to the "terminal", you have to go to Run -> "cmd". In Linux you have to run a Terminal command at some point while using it.

Now I don't think the Terminal and Config files should disappear all-together, but there should be viable alternatives for the basic user.


###########


My last complaint is file security. Not lack there-of, but too much that it's hindering. Personally I think Windows can be a little lax in it's security but it's getting better. Windows automatically assumes full control of it's file system to the Administrator account. Linux assumes no control of it's file system to it's Administrator account and so you have to use the Terminal (see my previous complaint) using "sudo" or "chown" or the like to do anything using the root account. There has to be some sort of middle ground or at least options. I do like that Gutsy includes a Home, Documents, Music, etc folder similar to Windows which allows full control. What I would like to see is at least two options for security.

1. Full security. This would basically be exactly as it is now.

2. Basic security. This would be for the average user. It would default most files to Read Only, but allow the right click -> Properties of the file or folder to allow writable (or even a once writable option for a single editing session). Then you could use more of the system with more ease. It would allow the moderately technical (like myself) people to edit the config files if they want but not allowing people to easily delete system files or edit important documents without a little intervention by the user.

I know a lot of the Linux fanatics here would hate this, but the other 99% of the world would probably appreciate it. I know I would. I recently tried my first try at a webserver. All I wanted to do was go to the Apache config files via the file browser and change some settings. I was forced to use "sudo gedit" or "chown" in order to edit. It was more frustrating than I wanted.






So that's my little article. I personally am growing to like Ubuntu more and more (to the point where I'm only going to have only 1 Windows box left for gaming), and I think Ubuntu is fast becoming a viable replacement for Windows, however there is still some work to go.

Hopefully this doesn't start a flame war or anything like that. It's just my thoughts.

yes, stiil some work to do. with the default theme :lolflag:
your post is hilarious in many parts. why don't you just windows and abandon these "well-intended" thoughts of making ubuntu like windows?

---

### Post by Tux Aubrey on 2007-10-26
I would take issue with your idea of what a "computer illiterate" person would and would not find difficult.

IMO, someone who had never used a computer before (and wanted to learn) would be better off with Ubuntu than Windows if they were starting with a preloaded and fully functional desktop. More experienced  Windows users come to Linux with so many bad habits and ingrained thought process that they can really struggle (I know I did!)

After a while the "Linux way", especially when polished and, yes, dumbed-down a bit, with some ubuntu magic will seem very straight forward.  

If you are not starting to enjoy it after a few weeks, go back to Windows.  Nobody, least of all the people on this forum, want to force Ubuntu onto people.  And most of us would rather move to another distro if anyone tries to force it to mimic Windows.  (You could try one of the distros that has gone down that road - I think there's one called LinuxXP that even has a "Start" button - you know, the one you click on to turn off your computer. :)

---

### Post by Afoot on 2007-10-26
> **siege911 said:**
> 
"So Ubuntu is Linux"
"Yes"
"So why can't I install this program?"
"Because that's based off of RPM and doesn't work with Ubuntu"
"What's the difference"
"They are just different types of Linux"
"Oh so I need something that's based off of Ubuntu Linux?"
"No, you need something that's based off of Debian"
"What's Debian?"
"It's what Ubuntu is"
"I thought Ubuntu is Linux"
"It is"
"???"

"So XP is Windows"
"Yes"
"So why can't I install this program?"
"Because that's a 64-bit installation file and only works with Vista"
"What's the difference"
"They are made for different types of Windows"
"Oh so I need something that's based off of Windows XP?"
"No, you need something that's 32-bit"
"What's 32-bit?"
"It's what XP is"
"I thought XP was Windows"
"It is"
"???"

-_-

---

### Post by wheredidrealitygo on 2007-10-26
> **Afoot said:**
> "So XP is Windows"
"Yes"
"So why can't I install this program?"
"Because that's a 64-bit installation file and only works with Vista"
"What's the difference"
"They are made for different types of Windows"
"Oh so I need something that's based off of Windows XP?"
"No, you need something that's 32-bit"
"What's 32-bit?"
"It's what XP is"
"I thought XP was Windows"
"It is"
"???"

-_-

I salute you.

---

### Post by Tatty on 2007-10-26
Hi siege91.  Congratulations on trying your first Ubuntu desktop system.  Its a big step in an exciting direction!

Much of what you say in your post is almost exactly what I (and im sure pretty much every new Ubuntu user) thought when i first started with Ubuntu.

I think it comes from a mix of excitement and frustration.  Excitement because of new things to play with and new ways of working, but frustration at certain things you previously took for granted which no longer work.

Its easy to blame Ubuntu for not delivering what you want, but when you sit down and look at what you are demanding, you start to realise that you are saying you want Ubuntu to be Windows.  Ubuntu is not windows, and nor should it be.  It is not developing to try to emulate windows. it is developing in its own way as an independant operating system to meet the needs of its users and its future users.  Lol, dont forget that GNU/ Linux existed as an operating system long before windows had that status!

Many of the points you raise are genuine issues which many people cite as the negative points for Ubuntu.  And unfortunately there are no quick fixes for them.  The issue with lack of gaming support, for example, is only really going to be solved when gaming companies start supporting linux, and that comes down to consumer pressure.

You seem like a smart guy who will soon get to grips with the ways of Ubuntu.  Just stick at it and be prepared to learn new things, over time all the things that seem fiddly now will become second nature.  Lol i tend to struggle slightly on windows systems now.  I often have to sit for a moment to think how to do certain things, then i grumble for a bit about why it works in such a stupid way.

Anyway, stick at it, cos once youre over that learning curve, youre gonna love it! :)

---

### Post by igknighted on 2007-10-26
Well said, tatty.

---

### Post by SunnyRabbiera on 2007-10-27
alright lets get over the flaws in your posts

> **siege911 said:**
> 

My first negative impression was the color scheme. I just don't like it. The orange isn't very friendly. I think you need more welcoming colors like yellows, blues and greens. The Windows XP grassy hills is a great example of a good default background and the blue taskbar on the bottom is great. I briefly installed the Kubuntu Desktop and found that KDE was a much more friendly looking desktop. Beyond that I despised KDE and removed it...don't want to start a discussion about that... but the point is that people are first going to want it to look welcoming. I think you need to put a huge importance on graphic design when designing the OS. Ubuntu seems to place some importance but not a huge amount.

Now I know a lot of people are going to want to quickly comment how you can change the theme and all of that, but I'm trying to go about this from a computer illiterate perspective. A computer illiterate person will never change much more than their background wallpaper. Since Ubuntu is Linux for Humans, I'm assuming they mean ALL humans, rather than just tech savvy humans.
[

so you prefer the preschool theme of XP?
that is really sad, I find XP's default blue scheme pathetic, it looks like something from preschool!
Personally i would more favor XP's silver theme or its media edition theme, now those I can see as semi decent eye candy... but its default blue theme is rather... ugh, I would take ubuntu's gentile orange and brown anyday.
> 
My first positive impression was the eye-candy. I installed Ubuntu 7.10 on a 3 year old computer and was still able to get all of the Eye Candy out of it with no lag or skip. It was a lot more pretty than Vista especially after I turned the Appearance Settings up to Extra. The only suggestions I would make in this area is to include the Compiz Advanced Settings Manager (or whatever it's called) on install for some of the slightly more advanced users. I couldn't understand why I couldn't get the cube to work until I searched around the forums a bit. If you have to search these forums for help on your OS, then you can assume the average basic user will never know such information.

this is something more up kubuntu's sleeve, kde tacked onto ubuntu normally doesnt look so good.

> 
My second positive impression was the Add/Remove Programs feature. There is no better feature than that. This was so much better than the traditional way of putting a CD in the drive, going through a whole new install process for each program, and hoping it worked. The only suggestion on this area is you may want to add a "Repository on the fly feature" or something like that. This way if you want to download something that's not in the default repositories, you could copy and paste the address provided by the program company into a box and only the packages from that repo would show up. Then when you are finished downloading, and you close it, that Repo goes away. I do know you can go through preferences and add 3rd party repos but that's just not as user-friendly. Remember that we are dealing with computer illiterate people.

well sometimes repo's have issues, but it is easy to fix...
the thing is that the add/remove app is not meant to be the main package manager, synaptic is.
Its pretty easy for anyone to use it, though maybe it should be more featured... perhaps a synaptic link on the default desktop could help.

> Another suggestion would be a "Purchase Repository" which would have non-Open Source software that people could buy. You could put in your credit card information and receive an unlock key for the software as well as download it. I know that might be heresy on these boards but not everyone is die-hard about Open Source. Remember: ALL humans.

too many legal issues with this one, sorry it wont work.
luckily CNR is allegedly heading our way so maybe in the future this is more plausible...
but if its not free dont use it, thats my philosophy...

> 
My next negative impression was a lack of gaming support. I hear this is probably the primary complaint about Linux. While I haven't actually used such programs, I've heard there are several programs that can mimic Windows enough to allow for certain Windows based programs or games to function properly. Personally, I would include such programs as stock until Ubuntu (and/or other Linux distro) gains enough market share for companies to want to make Linux versions of the game/app. I know these may be complicated to run, but I see that necessary in order to convince people to change over.

I was recently trying to get my dad to switch over to Ubuntu. He said he was cool with it but he asked if it played his games (he's really into RTS games). My answer was "no". I'm sure I could get his games to play on his machine with enough mods and hacks, but he's not computer literate and if he ever got a new game, I'd have to fly from Arizona to Seattle to configure it for him. And I'm just not going to do that. So more Windows based support would be a HUGE factor in getting market share.

alright this is the most annoying one, its not our friggin fault that games are not supported...
game makers TARGET WINDOWS, there I said it... its not our fault that the games dont work by default, BLAME THE FRIGGIN GAME COMPANIES!!!!!!!!
Look this kind of crap is ignornt of our current situation, now maybe something like this might happen but as long as MS holds dominance we will get little to none game support.
> 
My next complaint is the pure number of Distros out there. We have choices between RHE, Fedora, CentOS, Ubuntu, Mandriva, PCLinuxOS, OpenSUSE, etc. Those are just the few I could name off the top of my head without searching and I'm brand new to Linux. Everybody seems to be fighting each other for the .8% or so of the market share that's currently for Linux. I know Open Source tends to have a tendency towards that, but it confuses people. It's hard to explain to a computer illiterate person what the differences are. It's difficult to learn that I need a .deb package for Ubuntu and not a .rpm package even though they are both for Linux. And on top of that, Ubuntu is not really it's own distro, it's a Debian based distro. Even more confusing.

again, THIS IS NOT OUR FAULT.
Dont blame ubuntu because its a linux distrobution, blame linux itself and the GPL.
I KNOW its confusing but really there is little to be done about it except make linux as closed as windows is and THAT IS NEVER GOING TO HAPPEN.
Look the reason for so many distros is that linux is open source, meaning anyone can do what they wish... if you are going to complain then complain not just about ubuntu but give this to other distrobution and they will all say the same...
LINUX IS OPEN SOUCE, if you dont like that go back to windows!

> "So Ubuntu is Linux"
"Yes"
"So why can't I install this program?"
"Because that's based off of RPM and doesn't work with Ubuntu"
"What's the difference"
"They are just different types of Linux"
"Oh so I need something that's based off of Ubuntu Linux?"
"No, you need something that's based off of Debian"
"What's Debian?"
"It's what Ubuntu is"
"I thought Ubuntu is Linux"
"It is"
"???"

and i will reiterate one of the other posts made here:

"So XP is Windows"
"Yes"
"So why can't I install this program?"
"Because that's a 64-bit installation file and only works with Vista"
"What's the difference"
"They are made for different types of Windows"
"Oh so I need something that's based off of Windows XP?"
"No, you need something that's 32-bit"
"What's 32-bit?"
"It's what XP is"
"I thought XP was Windows"
"It is"
"???"

> Not sure there is a solution, I just wish people would combine their efforts rather than divide them. But I think that's more just a dream of mine than anything. However, this whole thought may be something to look at regarding marketing Ubuntu. Trying to eliminate some of that confusion.
so you WANT linux to be as closed off as windows? to hell with you on this one bud, to unify linux would only close off the open mindedness of it.

> 
My next complaint is the Terminal and Config files. These seem to be popular among Linux users. I tried Red Hat linux several years ago and all I could find was information about config files and terminal codes. I ended up not touching Linux till now. If you are going to be user friendly, you have to get rid of those for all practical purposes. Ubuntu has done a pretty decent job of doing that but it still has some work ahead. Replace all config files and terminal entries with visual interfaces to do your configs and people will be happy. In Windows XP, in order to get to the "terminal", you have to go to Run -> "cmd". In Linux you have to run a Terminal command at some point while using it.

Now I don't think the Terminal and Config files should disappear all-together, but there should be viable alternatives for the basic user.
this one i sort of agree with, for every terminal app I think there should be a gui one... but the terminal in ubuntu and a few others I have used I have barely touched, yes linux itself is still terminal oriented but we are getting close on this one.

> My last complaint is file security. Not lack there-of, but too much that it's hindering. Personally I think Windows can be a little lax in it's security but it's getting better. Windows automatically assumes full control of it's file system to the Administrator account. Linux assumes no control of it's file system to it's Administrator account and so you have to use the Terminal (see my previous complaint) using "sudo" or "chown" or the like to do anything using the root account. There has to be some sort of middle ground or at least options. I do like that Gutsy includes a Home, Documents, Music, etc folder similar to Windows which allows full control. What I would like to see is at least two options for security.

1. Full security. This would basically be exactly as it is now.

2. Basic security. This would be for the average user. It would default most files to Read Only, but allow the right click -> Properties of the file or folder to allow writable (or even a once writable option for a single editing session). Then you could use more of the system with more ease. It would allow the moderately technical (like myself) people to edit the config files if they want but not allowing people to easily delete system files or edit important documents without a little intervention by the user.

well for you you might want to look into a root based system, as that takes more or less a windows way of things.
there is the root administration account and the others are secondary.
this kind of system might be more up your alley.
the thing about sudo though that is both a flaw and a benifit is that the defualt user is pretty much the administrator.
this way also works like windows, but the biggest issue with windows is that it does pretty much aloow anybody to be the root and that is very bad for the system.
at least there is a margin for error in both a root and sudo based system but frag something up in windows and the whole system is done for.
I am thankful for the root/sudo systems in linux as that makes recovery a lot easier.

perhaps there should be an easier way to tell the different files though, between administration and regular files but this might need a rehaul of how most DE's run...
it would be a pain to do but its plausible.

---

### Post by machoo02 on 2007-10-27
> **Tatty said:**
>  Lol, dont forget that GNU/ Linux existed as an operating system long before windows had that status!IANAWFB*, but this is not true:

[The first independent version of Microsoft Windows, version 1.0, released in November 1985....]("http://en.wikipedia.org/wiki/Windows#History")
[The Linux kernel was first released to the public on 17 September 1991, for the Intel x86 PC architecture...]("http://en.wikipedia.org/wiki/Linux")

* - I am not a Windows fan boy

---

### Post by DuneSoldier on 2007-10-27
> **machoo02 said:**
> IANAWFB*, but this is not true:

[The first independent version of Microsoft Windows, version 1.0, released in November 1985....]("http://en.wikipedia.org/wiki/Windows#History")
[The Linux kernel was first released to the public on 17 September 1991, for the Intel x86 PC architecture...]("http://en.wikipedia.org/wiki/Linux")

* - I am not a Windows fan boy

I don't think Windows 1.0 qualifies as it's own OS, since it still required DOS to be present to launch it. Kind of like X11 and Linux, X11 is an application that runs on Linux.

---

