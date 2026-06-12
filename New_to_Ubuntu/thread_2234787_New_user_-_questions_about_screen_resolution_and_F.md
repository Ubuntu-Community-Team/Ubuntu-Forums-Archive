---
title: "New user - questions about screen resolution and Flash"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by Michael_Bernard on 2014-07-16
Hello everyone, this is my first day in this new and exciting world of Ubuntu. I had Windows 7 before, didn't know much nor was I interested in learning, but that's what I had before. I've never been much of a tech person at all, but I definitely have an interest nowadays and I am ready, willing and able! Originally I first wanted to start to explore this interest with the iPhone 4. Then I upgraded to the 4S, the 5 and finally made the switch to the Nexus 4 and now Nexus 5. Pretty good being on Android and it has made me have more of an interest in the technical aspects of everything. My sister works for IBM and built me a computer which I planned on using to learn and also play some games. Games don't seem to be much of a hobby for me anymore but I do enjoy having a quality graphics card at my disposal. Alright that's enough of a background, now let's get into the nitty gritty. Much of the material will seem quite ridiculous to some, but keep in mind I will be reading as much as I can everyday and I will get better. Having this little place to get all my little questions answered will help keep me confident and feeling in control. Thanks for your help in advance and I hope to be an educated member soon! I am the lowest of the low as of now though!

Alright, some questions I have. 

1) I have my computer hooked up to my tv. Previously I was using 1920 x 1080, which stretched the screen out way too wide and made the websites too small. I've toggled with adjusting icons and the like, but it never feels quite right. So I've switched to 1280 x 720. Am I going to be loosing precious resolution? I'd love to have the best resolution possible for my tv, but I am still not quite comfortable in the answers I've found. I've fixed the overscan issue that was a problem previously so at least I'm getting somewhere. I have a 58 inch Panasonic tv, it's an LED version, which Panasonic has been notoriously bad with, but this one seems to be decent. Also while I had Windows I read that for computers hooked up to tvs, it was best to use ycbrc (?) instead of rgb for the color settings? These seemed to look a bit better to my eye personally. Unfortunately I haven't been able to come across that option as of yet in Ubuntu, but that maybe because of the graphic card driver I have? Which brings me to my next question...

2) Ok, so I have a Nvidia GEFORCE 760 video card which definitely seems to be pretty good. I have the standard open source driver right now but from what I'm reading I should definitely get the proprietary driver. Which one? The one that's recommended for Ubuntu or the graphics card or what? I went to the Nvidia website and they went to check based on my OS and card but then it required Java and I didn't have it which brings me to my next question.

3) All the codecs, synaptics, and third party stuff. I have no idea what this stuff is. I kind of get it. Ubuntu is free and open source so they are not going to auto install proprietary drivers that you actually need. Problem is, I have no idea about any of this stuff and I'm a pretty critical person. I like to keep everything as clean as possible and I want to enjoy downloading every little thing needed, if it is fact needed. What do I really need to make this computer work well? I know there are some big packages of restricted access things or something? Meh... I'm a bit lost here.

4) So I tried Firefox for the first time and it looked great, but then crashed Youtube everytime. Also had to download Flash for it. So I read Chrome has it's own video player installed in it, but only could get chromium, ended up finding Chrome and things are good. Or are they? Do I need to install that pepperflash plug in to get the highest quality? My videos seem a bit off and when I scroll on a website it kind of glitches. I'm a bit too nervous to download anything without 100% knowing about it, hopefully someone can help me along here.

Alright, thanks for your time, I will be searching and reading as much as I can. Thanks for your help.

---

### Post by yancek on 2014-07-16
For the nvidia driver, click the System Settings icon (the gear/wrench icon in the left panel) and you will see an Additional Drivers icon.  Click on that and you will get a recommended option for your graphics.

Synaptic is a package manager.  Ubuntu generally uses now the Software Center which you can use to select, download and install software.  There is also a search option to search to see if some particular software is available.  You can also use 'apt-get' from a terminal to install software.  You would need to know the name of the software.

sudo apt-get install nameofprogram would do it if it available, replace nameofprogram with the actual software name.

You usually need to install codecs for multimedia.  You are also better off downloading from the Ubuntu repositories so using apt-get will do that or the software center.  You can also add repositories.  Best to post about a specific software or problem and someone should be able to tell you if you need another repository and what it is.

---

### Post by Michael_Bernard on 2014-07-16
Ok half of that was over my head. I'd like to stay away from terminal for now if I can. Do I need to get Synaptic? On Nvidia they told me I needed Java, but now I'm having trouble downloading Java. Yikes. I did the Open SDK 7 or something. Still hasn't registered with Nvidia though.

Ok I'm downloading some drivers, did terminal for the synaptic package manager, restricted access, flash plugin, vlc media player. Anything else that you would consider

---

### Post by mastablasta on 2014-07-17
you dont' need to go to nVidia site to install driver. it was mentioned how the best way to do it is. click additional drivers, click recomended and install and that's it.

codecs and such can be installed upon system install (one box needs to be ticked). they are restricted, not because of access but because of the licenses. for example while in somre ocuntries they are completelly free to use others have restrictions (e.g only for home use not for commercial and similar). anyway - open ubuntu software cneter, type "ubuntu restricted extras" in the search box and when it find it click on it to install.

java - java should be part of ubuntu system. it's the open version of java. and Works fine for most things. if it's not installed - again software center, trype java and then install.

some things though need Oracles version of java. for that the install is more complicated but can be done by copying 5 lines into temrinal and pressing enter after they get copied. more ifno on that here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

aside frm terminal th eother option is to add the PPA (personal repository) into ubuntu center as software source, update the center and then again search oracle java and then click install.


since you say you are familiar with Apple and Android. - 

- software center is like App store or Google play (in fact the "stole" this idea from Linux/BSD/UNIX...) - it offers a nice view of selected repositories and applicaitons within them
- PPA is personal repository packaged and maintained by helpful individuals - think of it as personal app store with only one app. 

so if you know those phones you should feel at home in Linux.

edit: also read "[how to get a quick and good answer]("http://ubuntuforums.org/showthread.php?t=1422475")"
> 
**Make the title of your thread meaningful and concise.** For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you.

---

### Post by buzzingrobot on 2014-07-17
Michael, here's my take:

1. Open the "Software Center" application. (Tap the Windows/Super key and entering "Software Center".  The icon for the app will appear in the top left corner.)  Search for "ubuntu-restricted-extras".  Click on it to highlight it and then click install. (If you see 386 versions listed, they are for 32-bit machines.) This installs a batch of multimedia codecs, Adode Flash, some Microsoft fonts, etc. This is the standard way they are installed on Ubuntu.

2. As suggested, using the "Additional Drivers" app is the most reliable way to install an Nvidia driver.  Tap Windows/Super and start entering "Additional Drivers", etc. It should indicate that the open source Nouveau driver is installed. Select one of the proprietary Nvidia drivers (usually best to pick the one that's recommended) and proceed. The installation is not instantaneous and can take several minutes.  Once complete, you need to reboot to activate the new driver.  (This should take care of the YouTube issue.  Meanwhile, just ignore Firefox when it offers to install Flash or some such thing by itself.  That's a Windows-ism that Mozilla hasn't removed from Firefox for Linux.)

3. A 58-inch TV display is pretty wide. I don't know the maximum resolution the Nvidia 760 will support, but, in the end, the TV won't display any more pixels than it is capable of displaying.  When you spread 1920 pixels across a 58-inch screen, the individual pixels will be much larger than when spread across, for example, a 15-inch laptop screen.

---

### Post by Gordonbp531 on 2014-07-17
> **yancek said:**
> For the nvidia driver, click the System Settings icon (the gear/wrench icon in the left panel) and you will see an Additional Drivers icon.  Click on that and you will get a recommended option for your graphics.

Actually that's not quite right - it's Settings>Software and Updates>Additional Drivers tab

---

### Post by Michael_Bernard on 2014-07-19
Hey guys after following this, I seemed to have everything up and working for my minimalist needs.

[http://www.unixmen.com/top-things-installing-ubuntu-14-0413-1013-0412-1012-04/](http://www.unixmen.com/top-things-installing-ubuntu-14-0413-1013-0412-1012-04/)

What is your opinion on what the author of the link is saying? He seemed to know what he was talking about and I felt comfortable in following majority of that stuff step by step. I read around a lot of what should be added and it seemed pretty legit. What do you think?

---

### Post by Mark Phelps on 2014-07-19
Personally, if I wanted the Cinnamon desktop, I'd go with Mint rather than adding it to Ubuntu.

Also, I would not just install everything he listed -- especially stuff like Torrent SW and Wine. I don't use the first and have personally found the second to be largely a waste of time, since nearly every Windows app I tried with it either didn't work, or worked so poorly as to be useless.  But, that's your call.

Also, Ubuntu Tweak is now not nearly as useful as it was years ago, since fewer things can be tweaked now.  So, I personally wouldn't bother with it.

My own approach would be to only install the apps you feel you really need.  Don't need to load your PC up with lots of stuff you're not going to use.

---

### Post by yancek on 2014-07-19
I would suggest you read through and understand what each of the applications suggested do and whether it something you need.  If you can't think of a use for it, don't use it.  Many users won't need or use most of it.

---

### Post by Impavidus on 2014-07-20
There is no such thing as essential software, other what is needed to boot your system and login. Just add what you think you'll need, everything else is just bloat. There is nothing that you *should* add. Keep in mind that adding a lot of PPAs may make the system less stable.

---

### Post by Rob Sayer on 2014-07-20
Personally I've not been impressed by what I've seen on unixmen.  For example all I've ever done in a number of ubuntu installs as far as codecs go is to install ubuntu-restricted-extras.  Never had a problem.

Also, I wouldn't touch a lot of the other stuff they mention.  Why install utorrent?  it's not that well supported in linux and it's no better than transmission or ktorrent.

There are a lot of crappy linux blogs out there.  Just because someone has a linux blog doesn't mean they're actually knowedgeable.  And like many blogs they can be more marketing than information.

As mentioned in post 10, don't use 3rd party external ppa's to install unless you seriously can't do what you want to do otherwise AND you know what you're doing.  Common noob mistake.

As far as using it on a large screen goes I'd be tempted to make the fonts and icons bigger than lower the resolution.  You're losing video performance.  I'd *always* use the monitor's native resolution.

I'd definitely recommend installing and using synaptic.  I always either use it or the terminal.  It's been ages since I use the software centre.  IMO the only good thing about it is that it has user recommendations.  The problem with that is that many said users are not knowledgeable enough for me to care how many stars they give something.

---

### Post by buzzingrobot on 2014-07-20
> **Rob Sayer said:**
> 
As mentioned in post 10, don't use 3rd party external ppa's to install unless you seriously can't do what you want to do otherwise AND you know what you're doing.  


And always read a PPA's page on launchpad.net to check for restrictions, qualifications, etc., and even just to see if the project is still alive. Blindly copying and pasting install commands from a random website isn't the way.

---

### Post by Michael_Bernard on 2014-07-22
Hmm. I see. Thanks for the help guys. I have much to learn. I definitely am a minimalist, so I'm going to try that approach. I really have no clue what the hell Cinnamon, PPA's, Repositories, etc are. Guess I need to get on Google. Essentially all I need is to be able to web browse and watch torrents. That's probably not even the right way to say that. Yikes. I feel totally clueless here, it is overwhelming.

How about to make this a little more fun for you guys, tell me what you guys do when you first install Ubuntu?

Do you check the third party box even if you are a minimalist? What's next? What web browser do you prefer? What do you spend most of your time on Ubuntu doing? 

I'd like to be a plain Jane, super minimalist who only has things he actually uses. I pretty much live my life like that so why not on my computer? I'll try to do it without the third party ( codecs? lol ) and see what happens. I do want to finish this seasons of my shows, but after that I'll do it. 

I'm sure I'll need some sort of video player to be able to do that. And hopefully some more responses will come in and steer me where I need to go.

Where should I go to get a basic understanding of Ubuntu? I went to Android Central and have been able to get more comfortable with the tech world, although it never really gets all that technical there. But something like that, where would you recommend?


I must say that I absolutely love Ubuntu. It feels so much faster and clean and efficient than Windows. I'll never look back again. It is just so much better for someone who has the limited needs I do. It reminds me a lot like iOS or OS X, just very simple and clean. I don't know how else to explain it. 

I do hope more games come to Linux from Steam though, that would definitely help out a lot. I don't game much, but I didn't spend 250 on a video card for nothing. I read that they only had 30 games Feb 2013 and now are up to 300 or so, so that seems like improvement for sure, but not many major games. Oh well, like I said, not much of a gamer, but when I do want to game, I'd like to have it all ready to go.

I agree with the poster above as well. I do want to keep the best resolution possible, I need to play around with the settings to make it look right. Everything is way too small. But hopefully I'll figure that out.

---

### Post by yancek on 2014-07-22
Cinnamon is a Desktop environment.  There are quite a few available and the most common are KDE, Gnome, Unity, Mate, XFCE, LXDE, the list goes on.  Other operating systems don't give you a choice.  PPA, see the link below: 

[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

Repositories are on the servers used by the specific distribution and are monitored regularly so are checked for problems regularly and are safer than downloading willy/nilly from various locations on the internet from untrusted and unknown sources which may or may not be what they claim to be.

A lot of third party codecs deal with multimedia so if you watch a lot of video, you probably will want that.

---

### Post by Bucky Ball on 2014-07-23
Install ubuntu-restricted-extras. That will take care of a lot of things, including Flash crashing probably.

Also, you will have much better luck asking one support question per thread, with each thread in the appropriate sub-forum. Gets confusing otherwise. (Descriptive thread titles help your cause as well.)

* I have changed the title of this thread from the generic one to something that might help your chances. Good luck.

---

### Post by mastablasta on 2014-07-23
desktop environments comparison: [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

video player is present by default. I do however suggest to install VLC (in software center). it is so powerful and yet easy to use.

repository - archive maintained by Canonical & community (makers of Ubuntu) - think of it as google play in android or apples app store (which are just renamed repositories).
PPA - personal repository usually made and maintained by one person or a small team. often used to easily add things to software center and then install them.

third party box is always a yes for me on desktop. it provides plenty od good things which can't be included in install image due to licensing.

to look for Ubuntu related things the Ubuntu wiki is the place to go for specifics and Ubuntu manual is very good for some general overview of the OS (see my signature).

you say no major games in linux? I would count civilization as major game. Not sure where Europa Universalis IV come in but also on Linux, Half life ported many of their game s(a bit old though) to Linux. 

yeah for the strong GPU maybe not much yet, but if you follow the Gaming on Linux website for example or some other new site you will see that many new games will have Linux port. Some are in production, some are rumours while some are confirmed.

you may also want to look here a bit: [https://appdb.winehq.org/](https://appdb.winehq.org/)

wine can play some windows games quite well. ofcourse again the limit is proprietary locked down MS DirectX.

---

### Post by Michael_Bernard on 2014-07-23
Alright thanks a lot everyone. If I have specific questions I will make a different thread. Thank you.

---

### Post by Bucky Ball on 2014-07-24
Okay. Please mark the thread a solved to help others by following the second link in my signature. Cheers and good luck. ;)

---

