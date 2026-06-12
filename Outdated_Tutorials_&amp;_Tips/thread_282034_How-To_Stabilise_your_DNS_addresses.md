---
title: "How-To Stabilise your DNS addresses"
date: 2006-10-22
forum: Outdated Tutorials &amp; Tips
---

### Post by handy on 2006-10-22
[CENTER][SIZE="3"][B]So if your problem is that your ISP's DNS addresses keep being lost after a reboot (sometimes it takes more than one reboot, sometimes it happens without a reboot!!) 

A *possible* symptom of this problem is not being able to use Synaptic Package Manager.

What follows *may* solve your problem.[/B][/SIZE][/CENTER]

**[SIZE="4"]*Also*[/SIZE]**, in this howto is a **[SIZE="3"]quick IPv6 fix for Firefox[/SIZE]** users, followed by a simple method that enables **[SIZE="3"]globally disabling IPv6[/SIZE]** *(added 22-Oct-07)*, which some may find they need to do to speed up their internet experience.  There is also basic instructions for using keyboard combinations for cutting, pasting & moving text in & out of the **Terminal** & elsewhere, intended for those unfamiliar with the **Terminal**.

**All sections are easy to find when scrolling.**

If you are new to the **Terminal**, scroll down the page to the **_Text & the Terminal_** section.

I have tested the following on Ubuntu's Dapper, Edgy, Feisty & Gusty, but not on the previous Breezy version of Ubuntu?

For **Breezy** see **Post 2**. [of this thread for Python's wonderful solution]("http://www.ubuntuforums.org/showthread.php?t=11544&highlight=d-link+adsl+router"), it does ***not*** work in Dapper & beyond, unfortunately.

[SIZE="4"]**_The Case of the Disappearing DNS's_**[/SIZE]

After a great deal of trying work-arounds, even being driven to invent one myself, someone called **Mips**, finally pointed me to the solution.

The following solution, pertaining to the dissapearing DNS's, is courtesy of **Stream303** I've just made it easier for new users to follow.

**____________________**

This is the way to **prepend** the **resolv.conf** file with your known good **ISP's Domain Name Servers (DNS)**.

**_[SIZE="3"]Editing the /etc/dhcp3/dhclient.conf[/SIZE]_**

(If you are unfamiliar with using the **Terminal** have a look down this page for the **_Text & the Terminal_** section.)

Enter the following line in the **Terminal**: 

**sudo gedit /etc/dhcp3/dhclient.conf**

and just before the **request** line in your **dhclient.conf** file that you are looking at in **gedit**, add the following line, or remove the comment **#** from the start of the line if it is allready exists):

**prepend domain-name-servers 208.67.222.222, 208.67.220.220;**

You will probably want to swap your ISP's DNS addresses for the ones in the above example. 

**(** [I]You may also choose to leave them, as they are the legitimate [**_OpenDNS_**]("http://www.opendns.com/")  IP's, & will work **_IF_** you edit your router's firmware via your browser & replace your ISP's DNS addresses with the OpenDNS ones. There are very simple & straight forward instructions for this on the [**_OpenDNS website_**]("http://www.opendns.com/start/"). If you don't know your ISP's DNS addresses, the [**_OpenDNS how-to_**]("http://www.opendns.com/start/") will show you how to get it from 95% of routers. If you still can't access your router you will have to google for the information.

***You can also allways check your ISP's web site or phone them if you don't have access to the addresses in documentation that your ISP supplied.***  

I have been using OpenDNS for some time & am very pleased with the faster browsing speed, highly recommended.[/I] **)**

For multiple addresses, separate with a comma and **don't forget the semicolon at the end**.

This will have the effect of prepending your ISP's nameservers and of having your routers DNS address automaticaly come up ***at the bottom*** of the list in **resolv.conf**. :KS 

Reboot or just bring your interface down and up again by entering the following in the **Terminal**:

**sudo /etc/init.d/networking restart**

Finished!

**____________________**


[SIZE="4"]**_IPv6 Quick (Firefox) Fix_**[/SIZE]

If you can't access the web through Firefox, though you know you have an internet connection via your modem/router,  ***OR***  you find it very slow to move between servers, after which browsing that server is as fast as it should be?  Try the following:

Enter **about:config** in Firefox's address field.

Enter **ipv6** in the new **Filter:** field.

Double click on the line left in the display window to change it's boolean value to **true**.

**Restart Firefox.**

& that should be that... :KS 

**____________________**


[SIZE="4"]**_Disable IPv6 Globally_**[/SIZE]

Unlike the method of editing */etc/modprobe.d/aliases*, the following method does not run the risk of being overwritten.  

**_Do the following to disable IPv6 globally:_**

**1.** To verify that the IPv6 module is loaded type the following from a terminal:

*handy@birdfish:~$* ***lsmod | grep ipv6***
ipv6 265856 10

**2.** Then from a terminal type:

*handy@birdfish:~$ **sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6***

**3.** **Restart**

**4.** To verify that the IPv6 module is not loaded type the following from a terminal:

[I]handy@birdfish:~$ **lsmod | grep ipv6**
handy@birdfish:~$[/I]

If for whatever reason the above method does not work, type either of the following alternatives ***a.*** or ***b.*** in the terminal:

a.  ***echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist***

b.  ***sudo nano -w /etc/modprobe.d/blacklist***  & enter the line ***blacklist-ipv6*** 

after both ***a.*** or ***b.*** do steps ***3.*** & ***4.*** as above.

**____________________**

[SIZE="2"]The reason for the first (DNS) problem which strikes lots of modem/routers is due to their windows centric design.

The reason for the second (IPv6) problem is due to the cheap quality of the router, which is also responsible for the first problem... :rolleyes:

***[Edit:]  After having used other Linux distro's & PC-BSD, I have had to modify my conclusions as I  have only experienced the above three problems when using *buntu, last verified on both (k)ubuntu 7.10.***[/SIZE]

**____________________**


[SIZE="4"]**_Text & the Terminal_**[/SIZE]

I know how it feels, having come from the windoze ***point & click for allmost everything*** environment, how intimidating it can feel, having to type arcane commands into the **Terminal**!

We can get used to the **Terminal** surprisingly quickly.

So often when we have found the help in the forums, wiki or other online reference we can just highlight with the mouse a command string & copy it into the **Terminal** on our own machine hit enter & move on... This method avoids typo's too!  

Very often, using commands in the **Terminal** is quicker by far than using a mouse.  

What follows are the few basic keyboard commands that make it all so easy.

These ***keyboard shortcuts*** are not only useful for the
**Terminal** they can be used for any other field that accepts text, the use of these keyboard shortcuts is only limited by your imagination. I use them all the time when writing in the forums. (All the 2 fingered ones are valid in windoze & DOS too!)

If you highlight text by left mouse button dragging over the desired text you can use keyboard combo's to manipulate it.

The most used 2 finger Key Combo's follow:

**Copy** = < **ctrl** > + < **c** >

**Paste** = < **ctrl** > + < **v** >

**Cut** = < **ctrl** > + < **x** > Followed by the **Paste** combo' is **Move**.

***When manipulating text with [B]Key Combo's**, in the **Terminal**, (which is **[I]_extremely_*** useful) you are required to use the same combinations as above, with the addition of the < **shift** > key, making _Terminal combo's 3 fingered_.[/B][/I]

The **Terminal** is your friend...

You will find both the **Terminal** & **Text Editor** in the ***Menu:* Applications / Accessories**

The **Text Editor** (**gedit** is it's name if you call it from the **Terminal**) is both simple & powerful.

For anyone wanting an online reference to the **Terminal** & beyond the 2 following links should keep you going for a long time:

[http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+tutorial](http://www.ubuntuforums.org/showthread.php?t=73885&highlight=terminal+tutorial)

[http://tldp.org/guides.html](http://tldp.org/guides.html)

---

### Post by mssever on 2006-10-24
Thanks. I'm subscribing to this thread so I can find it easily when I want to point people to it.

---

### Post by handy on 2006-10-25
> **mssever said:**
> Thanks. I'm subscribing to this thread so I can find it easily when I want to point people to it.

Thanks for your positive feedback :D  I thought I could take up less space on the forum's drives by putting a few oft needed solution in the same place. :cool:

---

### Post by torakiki on 2006-11-01
I've a NETGEAR DG834G and this worked perfectly. Thanks ;)

---

### Post by bayvista on 2006-11-07
I've tried this by plugging my DNS server address into dhclient.conf, but I still can't get Synaptic to work.

I have a D-Link DI524 Router connected to a D-Link DSL502T ADSL Modem using DHCP.

I can access the web via Firefox. I can even get to the Ubuntu repositories via Firefox, but not via Synaptic.


Any help appreciated.

David

---

### Post by bayvista on 2006-11-08
Thanks, Handy

I chose the second option - OpenDNS. Plugged in the addresses and all is working now. Much faster, too.

I don't think that the router quality is an issue. I don't consider $85 cheap considering what it does. No, it is just that Windows manage their networks better than Linux, which still has a long way to go to catch up. Nevertheless, I am dedicated to replacing my Windows with Linux eventually. 6 months work so far and still going!

David :eek:

---

### Post by dmizer on 2006-11-08
> **bayvista said:**
> I don't think that the router quality is an issue. I don't consider $85 cheap considering what it does. No, it is just that Windows manage their networks better than Linux, which still has a long way to go to catch up.

that's laughable.  $85 is retail level equipment (read: cheap).  when you're talking about the level of equipment able to handle ipv6 correctly and with no issues, this: [http://www.icpsales.com/cisco3800.html](http://www.icpsales.com/cisco3800.html) is the level of equipment and price range you're looking at.

sure, windows xp is suppose to be able to handle it (after a patch), but windows 2000 can't.  and linux has been able to handle ipv6 almost (if not as long) as ipv6 has been around.  remember, linux is a server first and a desktop second.  there's a reason most giants rely on linux for their servers (google for one), and i can assure you, it's not because linux's networking ability is behind windows.

---

### Post by bayvista on 2006-11-11
I thought it was too good....

Well, my Internet access is fine from all 3 PCs BUT...
I have lost the connection to my LAN?? 

Windows says:"Network Name cannot be found." in My Network Places when I try to access my Workgroup

Ubuntu says: "User/Password" when I try and access Windows Network, Anything I enter is rejected.

Any ideas?

David

---

### Post by Mishal on 2006-11-11
I am having problems browsing and for that matter doing anything else on the net EXCEPT that I have access to ubuntu servers using Synaptic.

I am guessing its a problem with my DNS but I don't know where to change the DNS in my router settings.
[[IMG]http://img152.imageshack.us/img152/7234/routerqt3.jpg[/IMG]](http://imageshack.us)

I don't even know what my ISP's DNS is. Please help:)

---

### Post by berserker on 2006-11-11
> **bayvista said:**
> I thought it was too good....

Well, my Internet access is fine from all 3 PCs BUT...
I have lost the connection to my LAN?? 

Windows says:"Network Name cannot be found." in My Network Places when I try to access my Workgroup

Ubuntu says: "User/Password" when I try and access Windows Network, Anything I enter is rejected.

Any ideas?

David

The same thing happens to me when I use the Opendns servers.  I read a post yesterday that mentioned Opendns has received several reports from Ubuntu users who lose access to their internal network when using their servers.  Nobody seems to have figured out a solution yet.

---

### Post by bayvista on 2006-11-11
To Mischal

Have a look at [www.opendns.com](www.opendns.com). This solved some of my problems.

David

---

### Post by StanMeis on 2006-11-12
This is my first day using Linux and the first issue I ran into was my DNS changing back to system defaults.  I followed your well written tutorial and managed to locate the file.  When I attempted to change dhclient.conf it wouldn't allow me to as it's a "read only" file.  I manged to find the file properties but it would not allow me to uncheck read only saying something to the effect that I didn't create the original file.  Next I attempted to replace it doing a "save as" and was blocked in that attempt as well.  Any suggestions?  This PC is going to be for my wife and she isn't going to want to change the DNS everytime she goes online.  

Changing the DNS in most OS's should be a two minute job, not two hours of research and frustration.  Please tell me that it gets easier.  Any fixes to revise the read only file would be greatly appreciated.  The answer I need is posted here but I'm unable to make the changes.

---

### Post by mssever on 2006-11-12
> **StanMeis said:**
> This is my first day using Linux and the first issue I ran into was my DNS changing back to system defaults.  I followed your well written tutorial and managed to locate the file.  When I attempted to change dhclient.conf it wouldn't allow me to as it's a "read only" file.  I manged to find the file properties but it would not allow me to uncheck read only saying something to the effect that I didn't create the original file.  Next I attempted to replace it doing a "save as" and was blocked in that attempt as well.  Any suggestions?  This PC is going to be for my wife and she isn't going to want to change the DNS everytime she goes online.  

Changing the DNS in most OS's should be a two minute job, not two hours of research and frustration.  Please tell me that it gets easier.  Any fixes to revise the read only file would be greatly appreciated.  The answer I need is posted here but I'm unable to make the changes.
Sounds like you've run afoul of Linux permissions. You have have superuser (root) priviledges to edit system files. This can be frustrating at first, but it Linux's permissions system is a great security feeature. The simplest fix is to hit Alt+F2 and type ```
gksudo nautilus
``` and use that window to navigate and open files.

A better practice IMHO is to only use superuser privileges when you need them and to type ```
sudo nano filename
``` into a terminal window.

BTW: sudo is the program that gives you superuser priviledges for a particular program. Use gksudo for graphical apps and sudo for command line or terminal-based apps.

---

### Post by StanMeis on 2006-11-13
Thanks.  This is the same thing my son-in-law and the tech guy at work told me today.

---

### Post by Mishal on 2006-11-13
> **bayvista said:**
> To Mischal

Have a look at [www.opendns.com](www.opendns.com). This solved some of my problems.

David

Thanks David but I already went through that site before posting here. That site does not provide instructions for my particular router - Siemens Speedstream 6520 and hence I can't seem to find WHERE I need to change my DNS settings.

Someone please help.

---

### Post by bayvista on 2006-11-14
You usually don't need to change anything in the Router. The DNS addresses are usually set to zero so that the operating system can set them.

To get my Ubuntu 6.06 working properly, I followed the Linux/Unix instructions on this website and added the DNS address of my ISP. If you don't know this, add the Open DNS addresses to dhclient.conf.

What happened to me was my D-Link ADSL router packed up and I replaced it with a router and separate ADSL modem. This did not bother Windows, but Ubuntu would not access the Internet. After much struggling, I eventually worked out the above solution which works for me.

David

---

### Post by Andos on 2006-11-14
handy - i just thought i'd say thank you very much.... your tip worked great for me.  I can finally use Ubuntu properly now :d

---

### Post by StanMeis on 2006-11-15
A quick PS to let everyone know what happened when I tried the suggestions noted in this thread.  It did not work for me and I got an answer to the problem that I wanted to share with everyone on this group from an unlikely place.  One of the riders on my vanpool runs a home network with Ubuntu and had this same problem.  His internet access is via a DSL modem and he's got a router with four ports that his home computers are connected to.

This is what he told me.  Go into your router (via your browser with the user and password you assigned when you set it up) and change the DNS numbers.  The next time Ubuntu boots up it will see the DNS numbers entered in your router at startup.  I did this and when I booted up and went into System/Administration/Networking the DNS problem was corrected.

This fix should work for anybody who is running a DSL modem connected to a router.  Hope this helps those of you who are using this type of configuration.

---

### Post by ilcarlos on 2006-11-19
It works,
I couldn't browse before but this really help me, and was so simple

> **handy said:**
> 
If you can't access the web through Firefox, though you know you have an internet connection via your modem/router try the following:

Enter **about:config** in Firefox's address field.

Enter **ipv6** in the new **Filter:** field.

Double click on the line left in the display window to change it's boolean value to **true**.

**Restart Firefox.**

& that should be that... :KS 

Thank you

---

### Post by handy on 2006-12-10
I haven't been very active on the forum's lately & have neglected this thread, sorry about that.

I'm glad that it has been of some help to some users. :)  Thanks for any & all feedback... :KS 

I have made some minor changes re the DNS stuff in the how-to, due to your informative feedback.

The Siemens Speedstream 4200 modem/router that Telstra Bigpond in Australia supplies doesn't come supplied with access info', I don't know if Optus Aust' is more helpful when they distribute it or not?

Following is the current access data for Australian subscribers to Bigpond & Optus, who were supplied with the Speedstream 4200 when they opened their account. The standard access info' is listed too for those that may need it:

**IP Address:**

**10.0.0.138** (Bigpond-supplied) 

**10.1.1.1** (OptusNet-supplied) 

**192.168.254.254** (Standard Firmware)

**Username & Password:**

Default username:  =  **admin**

*Bigpond-supplied* **password**:  =  **admin** 

*OptusNet-supplied* **password**: =   (no password is used)

So if you are not a bigpond user try without a password, if that fails then try **admin**, if that fails? :-(

Also, those supplied with these modem/routers by Telstra's Bigpond ISP, you have had the VoIP Port 5060 blocked! You can remedy this by using non-customised firmware :-) the details are comprehensively layed out here:

[http://whirlpool.net.au/forum-replies.cfm?t=570249](http://whirlpool.net.au/forum-replies.cfm?t=570249)

---

### Post by Mishal on 2007-01-10
I still can't browse but I can download anything using Synaptic. I am now using openDNS but still it doesn't work (though its working on Windows).

I have modified the dhclient.conf and resolv.conf files accordingly. One thing that may be of ntoe is that my router uses only one DNS rather than two. Nevertheless I have tried using one and I have tried using two in the resolv.conf file but in both cases Synpatic works but Firefox doesn't.

I used to be a full-time Ubuntu user for a long time but now I haven't used Ubuntu in 5 months. I am stuck with Windows because I can't connect to the internet on Ubuntu. Someone PLEASE help.

Thanks.

---

### Post by bayvista on 2007-01-10
In Ubuntu, check your Network Settings:

System/ Administration/ Network Settings/ DNS

Make sure that you have included your ISPs DNS in this list. If you don't know it, phone or email them. I found that OpenDNS only worked with some Ubuntu programs. Once I added my ISPs DNS, Bingo!

Dave

---

### Post by Nevermore on 2007-01-18
i am using my laptop with edgy and ethernet connection
i have the problem that every time i reboot my dns are lost, but i am using a fix ip address.
i tried the workaround u said, with no luck..
my pc takes good 5 mins to bootup because cant find the dns, i tried also to save the location
and i couldnt go around this problem..
what else can i do..

---

### Post by zzzname on 2007-01-18
Wouldn't it be easier to just write your DNS's in /etc/resolv.conf and then type chattr +a /etc/resolv.conf?

---

### Post by zzzname on 2007-01-18
Wouldn't it be easier to just write your DNS's in /etc/resolv.conf and then type chattr +a /etc/resolv.conf?

---

### Post by handy on 2007-01-18
resolv.conf is a temporary file that is created atleast every time you reboot your machine.

I tried making resolv.conf immutable, (it was probably the closest fix working in combination with some other editing of the dhclient.conf to the problem after trying quite a few,) but it was still a pain,  because my ISP changes DNS addressed often.  This situation would cause me to have to change permission on resolv.conf edit it & then make it immutable again.

The prepend in the dhclient.conf worked consitantly & was easier to edit.  The OpenDNS addresses mean I don't have to edit anymore, & they work equally well at least, to my ISP's DNS.  & I live in australia!

[Edit:] Since I'm using OpenDNS I don't have to edit my prepend line or resolv.conf if I was using the other method, though after trying nearly half a dozen different ways I to stabilise my DNS addresses, the prepend method is my choice. /

For some of the history on this issue:

[http://ubuntuforums.org/showthread.php?t=188551](http://ubuntuforums.org/showthread.php?t=188551)

The bottom line is that different solutions suit different hardware/software situations, & user's... :)

---

### Post by 454redhawk on 2007-01-18
> **handy said:**
> resolv.conf is a temporary file that is created atleast every time you reboot your machine.

I tried making resolv.conf immutable, (it was probably the closest fix working in combination with some other editing of the dhclient.conf) to the problem after trying quite a few, but it was still a pain,  because my ISP changes DNS addressed often.  This situation would cause me to have to change permission on resolv.conf edit it & then make it immutable again.

The prepend in the dhclient.conf worked consitantly & was easier to edit.  The OpenDNS addresses mean I don't have to edit anymore, & they work equally well at least, to my ISP's DNS.  & I live in australia!

For some of the history on this issue:

[http://ubuntuforums.org/showthread.php?t=188551](http://ubuntuforums.org/showthread.php?t=188551)

The bottom line is that different solutions suit different hardware/software situations, & user's... :)

By editing and locking down /etc/resolv.conf with **sudo chattr +i /etc/resolv.conf** the file will REMAIN at all times it is no longer a temporary file. This is the only sure fire way to secure the resolv.conf file from changing and KEEPING your prefered DNS. It ONLY has to be done one time.

---

### Post by handy on 2007-01-18
> **454redhawk said:**
> By editing and locking down /etc/resolv.conf with **sudo chattr +i /etc/resolv.conf** the file will REMAIN at all times it is no longer a temporary file. This is the only sure fire way to secure the resolv.conf file from changing and KEEPING your prefered DNS. It ONLY has to be done one time.

***It only has to be done one time it your ISP doesn't change their DNS addresses, & I'm sure that mine is not the only one in the world that does change their addresses, often.***  Also, I believe that if it was meant to **not** be a temporary (flag) file then it wouldn't be one to start with?  The immutable anwer always seems like a work around cludge to me albeit a reasonably good one.

This is only my opinion, If you don't like it, sorry, if my how-to has helped someone, great, if not, they move on, easy... :KS

---

### Post by 454redhawk on 2007-01-18
> **handy said:**
> It only has to be done one time it your ISP doesn't change their DNS addresses, & I'm sure that mine is not the only one in the world that does change their addresses, often.  Also, I beleive that if it was meant to **not** be a temporary (flag) file then it wouldn't be one to start with?  The immutable anwer always seems like a work around cludge to me albeit a reasonably good one.

This is only my opinion, If you don't like it, sorry, if my how-to has helped someone, great, if not, they move on, easy... :KS


You specifically mentioned using openDNS (as do I). No need for an ISP DNS. The ISP can change DNS all they want. This solution eliminates them from the loop.

---

### Post by zzzname on 2007-01-19
> **handy said:**
> resolv.conf is a temporary file that is created atleast every time you reboot your machine.

I tried making resolv.conf immutable, (it was probably the closest fix working in combination with some other editing of the dhclient.conf) to the problem after trying quite a few, but it was still a pain,  because my ISP changes DNS addressed often.  This situation would cause me to have to change permission on resolv.conf edit it & then make it immutable again.


Well, that's why I suggested using chattr +a, it makes the file imposible to delete and imposible to change anything what has already been written in it but at the same time it allows you and other programs to add other lines later.

---

### Post by handy on 2007-01-19
@454redhawk & zzzname,

**Two seperate topics are being mixed up here:**

**1.** Using the prepend line in dhclient.conf causes resolv.conf to have your prefered DNS addresses, in your prefered  order & put your router/gateway's address last.  Which I like better than making resolv.conf immutable, due to my preference of allowing the OS to write the correct information where & when it wants, rather than me having to take care of it.

**2.** The reason I offer OpenDNS's addresses in the how-to are manifold, they must also be considered ***bonus information*** to point 1. above:

*****  I link to [the OpenDNS Start page]("http://www.opendns.com/start/") - a clearly written & simple how-to configure many common routers which many people could find helpful at the least.

***** Some may not know their ISP's DNS's so they can use OpenDNS's how-to & addresses until they contact their ISP.  

***** OpenDNS does provide a faster cleaner service than ***most*** of our ISP's, so linking to it in the how-to may open a door to better service, it atleast opens the door of opportunity.

***** One can use OpenDNS via prepend as per the first post in this thread & not have to edit because their ISP has changed it's DNS addresses yet ***again***, or because you have changed your ISP for that matter.

The very nature of computing & the super configurable Linux based OS's means that not everything works for everybody, if it did this forum would be miniscule in size by comparison with what it is now...

If OpenDNS doesn't work as well as your ISP's DNS, don't use it.

If prepend doesn't work for you, that's unfortunate, try making resolv.conf immutable.

Follow your preferences where you can... :KS

The how-to has been written to help user's who do & don't, can & can't use OpenDNS, most specifically it demonstrates IMHO the cleanest solution for stabilising your chosen DNS addresses as I mentioned in point **1.** of this post. (Circles)

---

### Post by 454redhawk on 2007-01-19
> **handy said:**
> @454redhawk & zzzname,

**Two seperate topics are being mixed up here:**



If prepend doesn't work for you, that's unfortunate, try making resolv.conf immutable.

Follow your preferences where you can... :KS

The how-to has been written to help user's who do & don't, can & can't use OpenDNS, most specifically it demonstrates IMHO the cleanest solution for stabilising your chosen DNS addresses as I mentioned in point **1.** of this post. (Circles)


Thats the point I was making . The prepend option is NOT a sure fire way to do it . Sometimes for whatever reason it does not work (I imagine thats why you say"If prepend doesn't work for you, that's unfortunate") . Locking down the resolv.conf file would be just as "clean" as you like to put it AND it works without a doubt.

These ARE NOT 2 seperate issues

Locking down resolv.conf and using openDNS is the solution to the problem you describe. NOT the only solution but its the one that WILL work EVERY time without question.

Anyway. Sorry to jump in your thread. Take it for what its worth.:wink:

---

### Post by handy on 2007-01-19
> **454redhawk said:**
> 

These ARE NOT 2 seperate issues

Locking down resolv.conf and using openDNS is the solution to the problem you describe. NOT the only solution but its the one that WILL work EVERY time without question.

Anyway. Sorry to jump in your thread. Take it for what its worth.:wink:

Apparently OpenDNS doesn't work for everyone, I have no clue why?

Your input has caused more info' to be put in this thread, which is bound to useful to be someone...

So, thanks... :D

---

### Post by mawdryn on 2007-02-23
I was having a problem with disappearing DNS's as well, but the regular options being bantered about regarding the dhcpclient.conf file didn't work. presumably as I have a static IP. 

I found this blog entry from [ttp://www.shallowsky.com/blog/linux/resolvconf.html](ttp://www.shallowsky.com/blog/linux/resolvconf.html) which suggested adding 'dns-nameservers=x.x.x.x' into the /etc/network/interfaces file. 

This resolved the disappearing DNS issue for me.

---

### Post by Selig5 on 2007-03-31
Thanks, I just installed Ubuntu 6.10 for the first time and your 'ipv6 quick fix' made it possible for me to get Firefox on the internet. Great.

---

### Post by johnaaronrose on 2007-04-23
Using Feisty (last week's release) on a Dell Inspiron laptop, I previously altered the prepend statement (on the /etc/dhcp3/dhclient.conf file) for the wired ethernet (eth0) connection to show the open OpenDNS IPs (i.e. 208.67.222 & 208.67.220.220) by handy in November 2005 and that worked fine using Swiftfox (I'd previously used the same technique successfully on an older Acer laptop using Edgy with Firefox).

However, as soon as I'd got the wireless connection working, I disabled the wireless connection (using System/Administration/Network and the Connections tab) and I tried to run Swiftfox. I couldn't browse to any web site and so I checked the DNS tab on System/Administration/Network. And there were no entries other than 0.0.0.0. By the way, the router I'm using doesn't have the DNS IPs storable in it. When I put the appropriate entries in and saved, web sites could be browsed. So Feisty appears to clear DNS IPs when there is a wireless connection. Any work around to save me reloading these IPs at every logon?

---

### Post by ounas on 2008-02-03
Thanks Hanks, it helped
:)

---

### Post by Arthur Archnix on 2008-02-26
> If for whatever reason the above method does not work, type sudo nano -w /etc/modprobe.d/blacklist & enter the line **blacklist-ipv6**, then do steps 3. & 4. as above.

That looks like a typo to me. No?

---

### Post by handy on 2008-03-08
> **Arthur Archnix said:**
> That looks like a typo to me. No?

That is ***not*** a typo.

---

### Post by Arthur Archnix on 2008-03-08
Right, well I was just point out that there was a difference between the line I quoted, and the line in step two. One said "blacklist-ipv6" and one said "blacklist ipv6"

But I see you've gone and changed the one in step two as of three hours ago without pointing out why or what was changed. The least you could of done is said, that one isn't the typo, the one in step two was.

It must not matter either way, because blacklist ipv6 seems to work too. Guides available alternate between blacklist ipv6 and blacklist-ipv6.

---

### Post by handy on 2008-03-08
> **Arthur Archnix said:**
> Right, well I was just point out that there was a difference between the line I quoted, and the line in step two. One said "blacklist-ipv6" and one said "blacklist ipv6"

But I see you've gone and changed the one in step two as of three hours ago without pointing out why or what was changed. The least you could of done is said, that one isn't the typo, the one in step two was.

It must not matter either way, because blacklist ipv6 seems to work too. Guides available alternate between blacklist ipv6 and blacklist-ipv6.

Sorry, you are misunderstanding my actions.  I needed to point someone at this How-To, & for someone in a separate thread I also cut & paste a piece out, the whole section titled ***IPv6 Quick (Firefox) Fix***  I saw that I could improve the first  line in that section & added some text to it.  [***_See here?_***]("http://ubuntuforums.org/showpost.php?p=4474560&postcount=4")

I did not edit the any other section.

Perhaps you got confused because the line:

*handy@birdfish:~$ **sudo echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6***

Actually has the ***blacklist-ipv6*** both with & without the hyphen?

Anyway, storm in a tea cup... ;-)

---

### Post by Arthur Archnix on 2008-03-08
It was my misunderstanding. Please accept my apologies.

---

### Post by slopshid on 2008-03-08
Instead of using ***sudo nano -w /etc/modprobe.d/blacklist***, use ***echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist***

---

### Post by handy on 2008-03-08
> **Arthur Archnix said:**
> It was my misunderstanding. Please accept my apologies.

No worries mate! :-)

> **slopshid said:**
> Instead of using ***sudo nano -w /etc/modprobe.d/blacklist***, use ***echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist***

Thanks I'll check it out.

---

### Post by handy on 2008-03-08
> **slopshid said:**
> Instead of using ***sudo nano -w /etc/modprobe.d/blacklist***, use ***echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist***

Thanks slopshid, I tested it out & it works perfectly, I have added it to the How-To.

I left the previous line there as well, because when all else fails manually editing a script is all that's left. ;-)

---

### Post by spadron on 2008-06-04
Thanks for the post, worked for me!

---

### Post by schumifer on 2008-10-14
Damnnnn , you just became my hero. Have been fighting with unstable internet routing for the past couple of weeks. I new it was a dns issue, since i could ping the router but not any further.
Thanks a gazillion

---

### Post by SteveHillier on 2008-10-17
A big thank you to Handy for indentifying this problem and a solution.
If saved hours........
Steve
ps.  I have forgotten how to do a 'thanks' response

---

### Post by handy on 2008-10-17
> **schumifer said:**
> Damnnnn , you just became my hero. Have been fighting with unstable internet routing for the past couple of weeks. I new it was a dns issue, since i could ping the router but not any further.
Thanks a gazillion

> **SteveHillier said:**
> A big thank you to Handy for indentifying this problem and a solution.
If saved hours........
Steve
ps.  I have forgotten how to do a 'thanks' response

Glad it helped you both.

I spent months battling with this problem before finally finding the solution.

I don't use Ubuntu anymore & don't have the problem! :lolflag:

---

### Post by mssever on 2008-10-17
> **handy said:**
> I don't use Ubuntu anymore & don't have the problem!
So, what do you use now?

---

### Post by handy on 2008-10-18
> **mssever said:**
> So, what do you use now?

Leopard & Arch on one machine, though Leopard is my least favoured, Arch & Sabayon 3.4f on my 2nd machine, though that machine has drive drawers, so its not a dual boot routine.  2nd machine actually gets to try different distro's when the mood takes me.  Though I have found none that compare to Arch so far, though there is no accounting for personal taste eh!? :-)

---

### Post by Bruce M. on 2009-01-04
@ Handy

May you and your family throughout time immortal have peace, happiness and health.

I have been plagued with net problems since Sept 08 when my ISP was bought out by another. And then came the changes where certain net functions were built into the kernel along with Network Manager not performing up to par!

Then comes **handy** with his handy HowTo (pardon that, but it is very appropriate here)

For the first time in MONTHS I have an /etc/resolv.conf with just three entries, not 4!

**Old:** /etc/resolv.conf
```
nameserver 200.49.130.20
nameserver 200.49.130.21
nameserver 200.49.130.32
nameserver 172.20.2.12
```
**New:** /etc/resolv.conf - after a reboot too (just to see)
```
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 200.49.130.20
```
However I see something that concerns me.
As seen above

**nameserver 172.20.2.12** was replace with what was originally the first entry.

 and below:
```
  option routers 201.235.217.1;
  option dhcp-server-identifier 172.20.2.12;
```
I don't have a router??

Also why is it that when I issue this command: "*cat /var/lib/dhcp3/dhclient.eth0.leases*" I see two instances of the file?

```
bruloo@bruloo:~$ cat /var/lib/dhcp3/dhclient.eth0.leases
lease {
  interface "eth0";
  fixed-address 201.235.217.15;
  option subnet-mask 255.255.255.0;
  option routers 201.235.217.1;
  option dhcp-lease-time 21600;
  option dhcp-message-type 5;
  option domain-name-servers 208.67.222.222,208.67.220.220,200.49.130.20,200.49.130.21,200.49.130.32,172.20.2.12;
  option dhcp-server-identifier 172.20.2.12;
  option interface-mtu 576;
  option dhcp-renewal-time 18000;
  option broadcast-address 255.255.255.255;
  option dhcp-rebinding-time 19800;
  option host-name "bruloo";
  renew 0 2009/01/04 14:35:11;
  rebind 0 2009/01/04 14:35:11;
  expire 0 2009/01/04 14:35:11;
}
lease {
  interface "eth0";
  fixed-address 201.235.217.15;
  option subnet-mask 255.255.255.0;
  option routers 201.235.217.1;
  option dhcp-lease-time 20638;
  option dhcp-message-type 5;
  option domain-name-servers 208.67.222.222,208.67.220.220,200.49.130.20,200.49.130.21,200.49.130.32,172.20.2.12;
  option dhcp-server-identifier 172.20.2.12;
  option interface-mtu 576;
  option dhcp-renewal-time 10319;
  option broadcast-address 255.255.255.255;
  option dhcp-rebinding-time 18058;
  option host-name "bruloo";
  renew 0 2009/01/04 17:26:53;
  rebind 0 2009/01/04 19:36:56;
  expire 0 2009/01/04 20:19:56;
}
bruloo@bruloo:~$
```

Thanks, Have a nice day.
Bruce

---

### Post by handy on 2009-01-04
> **Bruce M. said:**
> @ Handy

May you and your family throughout time immortal have peace, happiness and health. 

:lolflag:

Please accept the gratitude of my family & I, for your immense kindness. :-D
______________

I'm sorry I can't help you with your questions as I have been using Arch Linux for much of the last year, & Arch does things quite differently, being based on the KISS approach, which certainly suits me ;-) ; in Arch there is a file */etc/resolve.conf.head* where you can place your dns addresses like so:

*nameserver xxx.xxx.xxx.xxx*

So that every time you start your network on that machine it writes what you have put in the resolve.conf.head into the start of resolve.conf.

Which is nice & simple for those that need to do such a thing.

It would be helpful if Ubuntu incorporated this system I think.


As far as your router is concerned; most ADSL modems incorporate a router, this may be what is being referred to.

---

### Post by mssever on 2009-01-05
@Bruce M.:

Are you running Intrepid? If so, have you explored all the new functionality in NetworkManager? With the release of Intrepid, I've been able to dump all my manual network configuration, and simply use NetworkManager for everything. Of course, my situation might not mirror yours exactly.

Failing that, you might be able to configure your router to set up your DNS for you (depending on your router brand/model). That was the method I used immediately prior to my current method.

---

### Post by Bruce M. on 2009-01-05
> **handy said:**
> :lolflag:

Please accept the gratitude of my family & I, for your immense kindness. :-D
______________

Accepted. ):P

I'm headed in the right direction because of this HowTo.

> **handy said:**
> I'm sorry I can't help you with your questions as I have been using Arch Linux for much of the last year, & Arch does things quite differently, being based on the KISS approach, which certainly suits me ;-) ; in Arch there is a file */etc/resolve.conf.head* where you can place your dns addresses like so:

*nameserver xxx.xxx.xxx.xxx*

So that every time you start your network on that machine it writes what you have put in the resolve.conf.head into the start of resolve.conf.

Which is nice & simple for those that need to do such a thing.

It would be helpful if Ubuntu incorporated this system I think.


As far as your router is concerned; most ADSL modems incorporate a router, this may be what is being referred to.

Yea, it would be nice.

BTW, not a ADSL modem ... I have a cable modem, and according to what is below, it probably has a router built in.

> Some cable modem devices may incorporate a router along with the cable modem functionality, to provide the LAN with its own IP network addressing. From a data forwarding and network topology perspective, this router functionality is typically kept distinct from the cable modem functionality (at least logically) even though the two may share a single enclosure and appear as one unit. So, the cable modem function will have its own IP address and MAC address as will the router.

And this page, which I just found, shows **my modem**: [How Cable Modems Work]("http://www.howstuffworks.com/cable-modem.htm"). It's now bookmarked and on a Pri 1 list to read, right after sending this post.

Have a GREAT Day
Bruce

---

### Post by Bruce M. on 2009-01-05
> **mssever said:**
> @Bruce M.:

Are you running Intrepid? If so, have you explored all the new functionality in NetworkManager? With the release of Intrepid, I've been able to dump all my manual network configuration, and simply use NetworkManager for everything. Of course, my situation might not mirror yours exactly.

Failing that, you might be able to configure your router to set up your DNS for you (depending on your router brand/model). That was the method I used immediately prior to my current method.

Yes, 8.10-64bit. I don't use a router! I have a Cable Modem, on a single home computer, connected to eth0.
 
I've dumped NetworkManager, the little applet that appears on the panel doesn't allow me to configure enough.  My ISP is sending 4 nameservers to my resolv.conf when the file only uses (reads) 3, and the fourth one is the DHCP  server, being ignored.

Have a nice day
Bruce

---

### Post by handy on 2009-01-05
***@BruceMM:*** Cable is an unknown to me as I live out in the sticks, & in this country, at least, it is only parts of major cities that have cable available to them, thus I have never had a need to learn about the cable technology.

Sorry I could not have been of more help.

---

### Post by mssever on 2009-01-05
> **Bruce M. said:**
> BTW, not a ADSL modem ... I have a cable modem, and according to what is below, it probably has a router built in.
There's an easy way to find out for sure. Type ifconfig and see what your IP address is as your computer sees it (not as reported by external websites). If your IP begins with 192.168, then you have a built-in router. Otherwise, you don't. If your setup is exotic, there's a possibility that this test might not be accurate, but most of the time it is.

Oh, on further reflection, here's a slightly different test: Compare your computer's IP address as reported by ifconfig with your IP as reported by some remote site, such as whatismyip.com . If the two are different, then someone's doing NAT or some other transformation between you and the remote site. Usually, that means you're using a router, although it's remotely possible that your ISP is doing some shenanigans.

At the last place I lived, I had cable Internet. My modem didn't have a built-in router (so I bought a separate unit). But if your modem has a built-in router, then it almost certainly has a configuration website built in, where you might be able to make the desired settings. Check your documentation.

---

### Post by Bruce M. on 2009-01-05
> **handy said:**
> ***@BruceMM:*** Cable is an unknown to me as I live out in the sticks, & in this country, at least, it is only parts of major cities that have cable available to them, thus I have never had a need to learn about the cable technology.

Sorry I could not have been of more help.

No problem handy, you got me here.  :) ... talk about sticks: Argentina, here, try that one on for size.

Stopped into a computer store downtown today and asked if they had any DVD-RAM disks.

Salesman: "DVD-RAM? No such thing, +R/W -R/W but no RAM."
Me: "Really, google it", at the same time a saleslady said, "Yes, I know about DVD-RAM disks, but we don't have any."

Looked every where, I have an LG-DVD-RAM drive, no disks.  :(

Have a great day.
Bruce

---

### Post by Bruce M. on 2009-01-05
> **mssever said:**
> There's an easy way to find out for sure. Type ifconfig and see what your IP address is as your computer sees it (not as reported by external websites). If your IP begins with 192.168, then you have a built-in router. Otherwise, you don't. If your setup is exotic, there's a possibility that this test might not be accurate, but most of the time it is.

First off, thanks for your input. I had no idea about that 192.168.

ifconfig does not show an IP starting with that number. That's a plus. :)

> **mssever said:**
> Oh, on further reflection, here's a slightly different test: Compare your computer's IP address as reported by ifconfig with your IP as reported by some remote site, such as whatismyip.com . If the two are different, then someone's doing NAT or some other transformation between you and the remote site. Usually, that means you're using a router, although it's remotely possible that your ISP is doing some shenanigans.

Checked out whatsmyip.com and it reports the same IP as ifconfig.

> **mssever said:**
> At the last place I lived, I had cable Internet. My modem didn't have a built-in router (so I bought a separate unit). But if your modem has a built-in router, then it almost certainly has a configuration website built in, where you might be able to make the desired settings. Check your documentation.

Guess it doesn't but it does have a site, but not a single IP address shows on that site.  :(

And my /etc/resolv.conf still has 4 nameservers (just did a fresh install).

Have a nice day.
Bruce

---

### Post by handy on 2009-01-06
***@Bruce M.:*** If your internet is working ok, & you don't have to do anything to maintain the working all right situation, then I would forget about it.  

It may very well be that this is how it works with your cable company & Linux (Ubuntu at least).  Cable is a bit different.

Your not having a router brings the question to my mind though, of what security does your ISP provide, if any?  (My ignorance of cable is talking here.) When we have an ADSL modem/router, the router usually incorporates NAT or SPI which are effective firewall systems. 

So I wonder if your not having a router means that the cable company is providing this (or some other) form of protection at its end?  

Is your IP the same if you have a look at it from this site:

*_[http://whatismyipaddress.com/](http://whatismyipaddress.com/)_*

& you can also use this site to test if your computer is protected somehow:

*_[http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)_*

It will also show your computers IP address which is good for verification. :-)

If you find that your computer is unprotected then I suggest that you investigate setting up a firewall ([*_firestarter_*]("https://help.ubuntu.com/community/Firestarter")) on your machine, if you have more than one machine you may enjoy setting up [*_IPCop_*]("http://www.ipcop.org/") on a cheap (near enough to free these days) PII headless box.  IPCop is really quite easy to set up & works like a dream.

---

### Post by mssever on 2009-01-06
> **Bruce M. said:**
> Checked out whatsmyip.com and it reports the same IP as ifconfig.
Based on that, it's almost certain that your modem is just a modem, with no router built in.
> **handy said:**
> Your not having a router brings the question to my mind though, of what security does your ISP provide, if any?  (My ignorance of cable is talking here.) When we have an ADSL modem/router, the router usually incorporates NAT or SPI which are effective firewall systems.

So I wonder if your not having a router means that the cable company is providing this (or some other) form of protection at its end? 
Based on my understanding of cable (which is probably somewhat outdated), the biggest security risk is data traveling between you and the ISP. I had a co-worker once who was a bit of a black hat, and he claimed that it was relatively easy to sniff your neighbor's cable internet traffic. A router wouldn't protect against this. The only defense is adequate encryption. But that situation might have been remedied. There was a time when it was quite simple to intercept wireless traffic, but these days many wireless networks have made that much more difficult, so I imagine the same might be true with cable. At any rate, back when I had cable, I never was able to see anyone else's traffic (I wasn't trying to snoop; I was just trying to see if I was vulnerable to snoops). If you run etherape as root and see anyone else's traffic, beware.

As far as NAT goes, NAT doesn't necessarily increase your security. For example, a default Ubuntu installation has no external ports open; therefore, NAT won't help it security-wise. Of course, most people install additional software, some of which might open up ports. There are a number of web-based port-scanning tools. It would be smart to run one of them, and make sure that any open ports are ports you expect to be open (such as port 80 for a web server or port 22 for an SSH server), and make sure that you follow adequate security procedures with the programs that are responsible for those ports. Where NAT can be a help is if you want to do something in a trusted environment (such as file-sharing) but don't want to expose those ports to the public. With only one computer, though, running such software in the first place would be foolish. So if you only have one computer, you don't really need a router as long as you're smart security-wise.

---

### Post by handy on 2009-01-06
Thanks for the info' mssever. :-) 

I use IPCop/Copfilter on an old PIII with my ADSL modem/router in bridge mode;
 it gives great security & better speed, plus a few other enhancements/services, like being able to run Privoxy & ClamAV (not that I need a virus checker :-)) without slowing down my internet throughput at all.

The computer cost me $5- at the tip, & it uses little electricity, the HDD rarely ever needs to spin up, the CPU rarely does more than idle & this box has a low power PSU, so as far as PIII's go it is about as good as it gets I think.  Though PII's are better, when one turns up at the tip I'll grab it. :-)

---

### Post by guberone on 2009-03-19
I disabled ipv6 in terminal using

echo "blacklist ipv6" | sudo tee -a /etc/modprobe.d/blacklist

but it didn't help my slow speeds.  Other laptops here are getting normal wireless and the slow machine has fast speed when booted into vista, but not in ubunti 8.10.  i want to re-enable ipv6 since disabling did not help and wifi was working well on other routers previously...

Can some one tell me how to re enable ipv6.... cant find how to anywhere though searching?  I've tried editing via 
gksudo gedit /exc/modprobe.d/blacklist 
but the list seems to be blank

Thanks

---

### Post by unutbu on 2009-03-19
> **guberone said:**
> 
gksudo gedit /**exc**/modprobe.d/blacklist 


Have you tried 
```

gksudo gedit /**etc**/modprobe.d/blacklist 
```
?

---

### Post by guberone on 2009-03-19
Thank you.  I was able to remove the black list line and ipv6 is back on.

Thanks for helping a noob find his way.

I'm going to try messing with this again another day, but if you can think of any reason as to why wifi is slow in comparison to to other laptops let me know.  I'm on a Belkin wirless router, don't know the model # as I'm in my office and the router is located in my landlords unit, but I'd guess its and older piece of crap.  

He ran a wire from the router into my office and ubuntu won't connect to that at all, but LAN works at home.  Maybe that's a clue to the wifi problem.

---

