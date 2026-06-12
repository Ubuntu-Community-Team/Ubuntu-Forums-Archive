---
title: "Ubuntu not ready for prime time?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by jbspear on 2008-06-01
I just downloaded Ubuntu 8.04 and am running it on my Vista-based laptop, an ACER Aspire which is an AMD 64 machine.  I really like what I see on my home screen so far and the software options are very appealing because of the simplicity and the price.  Unfortunately, the first problem I hit is that I can't get my wireless modem to work (it is an Atheros AR5007), which is sort of a show-stopper.  To find a solution, I've searched these forums and Google and I've found two different answers -- one is that Atheros is not yet supported by Ubuntu.  The other is a fix someone posted that I've pasted in below.  As a beginner, I found this solution to be incomprehensible but I recognize more sophisticated users may read this post and think I'm just plain stupid.  So I've pasted the fix below and put in [brackets] why someone without computer training would find it impossible to follow these directions.  Hence my comment that Ubuntu is not ready for prime time -- on the theory that if I can't fix this problem with due diligence, there will be others who are likewise be similarly challenged.  If anyone wants to try to translate these instructions, it would be very much appreciated by lots of newbies like me, since I have seen quite a few posts about the Atheros wireless.   Thanks!

For AMD64 Users
If you are using 64 bit version following this procedure
Blacklist the default driver
echo &#8220;blacklist ath_pci&#8221; | sudo tee -a /etc/modprobe.d/blacklist [WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]
Download the 64 bit driver [SINCE THE MODEM IS NOT WORKING, HOW DO YOU DOWNLOAD ANYTHING?  AND IF YOU CAN DOWNLOAD IT, WHERE DOES IT GO?]
wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
Extract driver using the following command [WHERE ARE YOU SUPPOSED TO TYPE THIS? ]
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
Ensure you have your kernel headers and the build essential package. [WHAT&#8217;S A KERNEL? WHAT&#8217;S AN ESSENTIAL PACKAGE? HOW DO YOU ENSURE YOU HAVE THESE? AND ALL THE STUFF THAT FOLLOWS, IS THIS ONE COMMAND OR A BUNCH OF DIFFERENT COMMANDS? AND WHERE DO YOU GO TO TYPE THESE IN?]
sudo aptitude update
sudo aptitude install linux-headers-$(uname -r) build-essential
Install ndisgtk
sudo apt-get install ndisgtk
Either use ndisgtk to install the driver or
sudo ndiswrapper -i net5211.inf
Load up ndiswrapper every time Linux is loaded
sudo modprobe ndiswrapper
echo &#8220;ndiswrapper&#8221; | sudo tee -a /etc/modules
Restart your system using the following command [HOW DO YOU DO RESTART YOUR SYSTEM USING A COMMAND SINCE THE YOUR CHOICES ARE USUALLY ICONS LIKE LOG OFF, RESTART, ETC?]
sudo reboot
Your card should have been detected and it should show available networks but if it does not, try
sudo iwlist scan [AND WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]

---

### Post by philinux on 2008-06-01
You need to be patient first.

You need to connect your laptop to the internet wired if you can. Then you can do the stuff mentioned.

---

### Post by shifty_powers on 2008-06-01
> **jbspear said:**
> 

For AMD64 Users
If you are using 64 bit version following this procedure
Blacklist the default driver
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist [WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]
Download the 64 bit driver [SINCE THE MODEM IS NOT WORKING, HOW DO YOU DOWNLOAD ANYTHING?  AND IF YOU CAN DOWNLOAD IT, WHERE DOES IT GO?]
wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
Extract driver using the following command [WHERE ARE YOU SUPPOSED TO TYPE THIS? ]
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
Ensure you have your kernel headers and the build essential package. [WHAT’S A KERNEL? WHAT’S AN ESSENTIAL PACKAGE? HOW DO YOU ENSURE YOU HAVE THESE? AND ALL THE STUFF THAT FOLLOWS, IS THIS ONE COMMAND OR A BUNCH OF DIFFERENT COMMANDS? AND WHERE DO YOU GO TO TYPE THESE IN?]
sudo aptitude update
sudo aptitude install linux-headers-$(uname -r) build-essential
Install ndisgtk
sudo apt-get install ndisgtk
Either use ndisgtk to install the driver or
sudo ndiswrapper -i net5211.inf
Load up ndiswrapper every time Linux is loaded
sudo modprobe ndiswrapper
echo “ndiswrapper” | sudo tee -a /etc/modules
Restart your system using the following command [HOW DO YOU DO RESTART YOUR SYSTEM USING A COMMAND SINCE THE YOUR CHOICES ARE USUALLY ICONS LIKE LOG OFF, RESTART, ETC?]
sudo reboot
Your card should have been detected and it should show available networks but if it does not, try
sudo iwlist scan [AND WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]

basically, all of those commands are entered, one by one, into a terminal, and press enter.

applications>accessories>terminal

---

### Post by spiderbatdad on 2008-06-01
All of those are terminal commands. Open a terminal: Applications>>Accessories>>Terminal

If you have no wired connnection, and hence no means of getting the wireless driver from within the OS, you need to use some other means via a working internet connection ie, flash-drive.

Ubuntu has been providing wonderful functionality, out-of-the-box, for several years now. Your pc manufacturer chose to use hardware that didn't provide opensource drivers. That is no fault of this OS. Even some factory installed linux computers still have the atheros wireless card...go figure.
My thinkpad wireless card worked from the first boot up. 

Ubuntu doesn't have to be ready for the prime-time, nor perfect for all users. It only has to satisfy the people who choose to use it. If that is you, then it will take some leg work to get that wireless card working...if it will work at all.

---

### Post by steveneddy on 2008-06-01
copy and paste the commands, don't type them in by hand.

---

### Post by bobnutfield on 2008-06-01
As a first time user of Linux or Ubuntu, it is very easy to be totally intimidated and confused by what you have posted.  But, you must first try to clear your mind of any thoughts that you will approach Linux like you do Windows.  Linux is not Windows and Windows is not Linux.

The details you have posted are actually quite easy, but it would certainly be confusing for a new user.  It would not take you long to sort out the things that look so difficult for you, but as a previous poster has pointed out, you will need some patience as you learn.  These instructions are for an INSTALLED Ubuntu and will not work with a temporary Live CD running (even if they did work, all would be lost the next time you reboot.)  

If you want you install and use Linux and Ubuntu, you can get all you want from it, but there is a learning curve.

Bob

---

### Post by stchman on 2008-06-01
> **jbspear said:**
> I just downloaded Ubuntu 8.04 and am running it on my Vista-based laptop, an ACER Aspire which is an AMD 64 machine.  I really like what I see on my home screen so far and the software options are very appealing because of the simplicity and the price.  Unfortunately, the first problem I hit is that I can't get my wireless modem to work (it is an Atheros AR5007), which is sort of a show-stopper.  To find a solution, I've searched these forums and Google and I've found two different answers -- one is that Atheros is not yet supported by Ubuntu.  The other is a fix someone posted that I've pasted in below.  As a beginner, I found this solution to be incomprehensible but I recognize more sophisticated users may read this post and think I'm just plain stupid.  So I've pasted the fix below and put in [brackets] why someone without computer training would find it impossible to follow these directions.  Hence my comment that Ubuntu is not ready for prime time -- on the theory that if I can't fix this problem with due diligence, there will be others who are likewise be similarly challenged.  If anyone wants to try to translate these instructions, it would be very much appreciated by lots of newbies like me, since I have seen quite a few posts about the Atheros wireless.   Thanks!

For AMD64 Users
If you are using 64 bit version following this procedure
Blacklist the default driver
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist [WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]
Download the 64 bit driver [SINCE THE MODEM IS NOT WORKING, HOW DO YOU DOWNLOAD ANYTHING?  AND IF YOU CAN DOWNLOAD IT, WHERE DOES IT GO?]
wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)
Extract driver using the following command [WHERE ARE YOU SUPPOSED TO TYPE THIS? ]
tar xvf ar5007eg-*.tar.gz
tar xvf ndiswrapper-newest.tar.gz
Ensure you have your kernel headers and the build essential package. [WHAT’S A KERNEL? WHAT’S AN ESSENTIAL PACKAGE? HOW DO YOU ENSURE YOU HAVE THESE? AND ALL THE STUFF THAT FOLLOWS, IS THIS ONE COMMAND OR A BUNCH OF DIFFERENT COMMANDS? AND WHERE DO YOU GO TO TYPE THESE IN?]
sudo aptitude update
sudo aptitude install linux-headers-$(uname -r) build-essential
Install ndisgtk
sudo apt-get install ndisgtk
Either use ndisgtk to install the driver or
sudo ndiswrapper -i net5211.inf
Load up ndiswrapper every time Linux is loaded
sudo modprobe ndiswrapper
echo “ndiswrapper” | sudo tee -a /etc/modules
Restart your system using the following command [HOW DO YOU DO RESTART YOUR SYSTEM USING A COMMAND SINCE THE YOUR CHOICES ARE USUALLY ICONS LIKE LOG OFF, RESTART, ETC?]
sudo reboot
Your card should have been detected and it should show available networks but if it does not, try
sudo iwlist scan [AND WHERE ARE YOU SUPPOSED TO ENTER THIS COMMAND?]

You can buy a 4965AGN for about $20 off ebay.  They work OOB  with Hardy.  I just bought a laptop and I did a bit of research to see if all the hardware worked.

Also have you tried madwifi to get that Atheros card working?

---

### Post by y6FgBn)~v on 2008-06-01
And a time saving tip is the middle mouse button is a shortcut to paste :)

---

### Post by SunnyRabbiera on 2008-06-01
Just remember ubuntu is a community driven OS, its not our fault that microsofts owns the market and has a say in all devices...
we can only do so much

---

### Post by stchman on 2008-06-01
Here is a forum entry for that card.

[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by john.richardson on 2008-06-01
I have been using ubuntu for nearly 3 weeks now solidly, I had merely flirted with it in the past on a live cd. I installed it and luckily for me everything worked.
It is completely different from windows but then I don't think Ubuntu wants to be windows.

For me to use ubuntu, it has taken time. I have used windows along time and even Hackintosh OS X on a dell. 

It took me over a week to get ubuntu to perform the same operations I took for grant on windows and I still find it annoying that there is no form of adobe CS3 but then thats really adobe's fault and the fact that because I prefer to use a wysiwyg editor for websites and not strict html and css code, linux users look down on me.

---

### Post by KevinD_Atl on 2008-06-01
Not sure what kind of Acer you had, but I have the Aspire 5315 and it took some work to get the wifi ready.  I followed these instructions -- [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=610603")

However, I am running versin 7.10
I use the wrapper but now I want to change it to madwifi so I can inject

---

### Post by archer6 on 2008-06-01
> **jbspear said:**
> As a beginner, I found this solution to be incomprehensible why someone without computer training would find it impossible to follow these directions.  Hence my comment that Ubuntu is not ready for prime time -- on the theory that if I can't fix this problem with due diligence, there will be others who are likewise be similarly challenged. 


Just a few thoughts to share. I too am a total beginner with Ubuntu Linux. I knew that going in, and still chose to proceed. I did the initial research to see what I was getting into and, and read about the challenges of various hardware components not working, or presenting problems. However my viewpoint  is that it presents me with an opportunity to learn and grow in an area that I'm very interested in. Therefore I was prepared for whatever came my way in the process of starting from ground zero. I expected to apply patience, due diligence, and a commitment to do my part to learn the operating system that I choose to embrace as a terrific alternative to Windows & OS X.  So for me it all about using my positive attitude, enthusiasm and taking the stance that this would be fun, challenging and rewarding as I learned the system. While I can certainly appreciate your frustration, please understand that I'm not being critical or judgemental, I'm simply sharing how I view Linux as a beginner and how much I'm enjoying this adventure. 

Finally one must remember that the people here are all volunteering their very valuable time to help new people such as myself. In my mind that is a blessing and a gift to those of us who need help. I happen to be a moderator, and (with all due modesty) an expert on two other forums where the roles are reversed. I'm the one with the knowledge and I'm very eager and happy to share it with everyone, especially the new people. I give generously of my time, posting  frequently and find it very satisfying and rewarding to give back. 

Have patience, do your part, and I'm confident that you will find Ubuntu is indeed ready for prime time and more. ....:)

Cheers!

---

### Post by starcannon on 2008-06-01
First I'd note that installing operating systems is not something endusers are usually equipped to do. Thats why most buy computers with an OS already installed by the OEM; that said, operating system installing is not ready for prime time, regardless of OS (mac has a bit of an edge here but even they have had their bumps). OEM installed Ubuntu is available here:
[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)
here:
[http://www.zareason.com/shop/home.php](http://www.zareason.com/shop/home.php)
and here:
[http://www.system76.com/](http://www.system76.com/)
and likely other places as well, I just put up my favorite 3 places to shop.

Second 64bit is still very much a work in progress, mac is the only one that can claim success here; yes I realize you can make everything work on 64bit, so no I don't want to get flamed. I'm just saying that for the moment 32bit is much easier to install, and unless your doing something specific like a server or video editing etc... your not going to see a big performance gain, though 32 bit will limit you to about 3.5gb of ram.

And finally I'd also keep in mind that if your coming in from another OS, do consider how long it took you to acquire the knowledge that makes you an expert in what ever OS your coming in from. Linux does not do things the Windows way, Windows does not do things the Mac way, etc... etc... So be patient with yourself and give it time, once you get the hang of it I think you'll wonder why anyone would do things any other way.

Hang in there, and don't be too quick to decide whether all s is p, here at my own home its all we use. My kids have been using Linux in one form or another since they were 5 and 6 years old. We have been using linux exclusively for 5 years now. We use it for Work, College, Home finances, Leisure, and for our children's educational needs. So I guess what I'm saying is, that linux is ready for primetime, it just requires one to be ready to learn linux in the same way one learned windows, or one learned osx.

GL and fair well however you decide to go.

---

### Post by stchman on 2008-06-02
As far as 64 bit is concerned, I have 64 bit Ubuntu running on an Athlon 64 machine very well.  They only sticking points for mer were Java and gDesklets.  I have fixed the Java problem using Icedtea and have not yet tackled the gDesklets problem.

I have talked to some Vista users and they have had MANY problems with Vista 64 so I feel that Linux does have a leg up on Vista in this area.  Having the hardware drivers in the kernel does have its advantages.

---

