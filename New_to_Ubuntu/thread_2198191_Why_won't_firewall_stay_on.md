---
title: "Why won't firewall stay on?"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by hebdave on 2014-01-07
Hi there I am new to linux ubuntu and am reading through the desktop help menus. My question since I am a only used to microsoft windows and moved to linux ubuntu recently is why won't the firewall stay on ? Every time I reboot I have to click on the lock in the firewall and then enter a password and finally then have switch it on AGAIN each time too. 3 odd things to go through every time I boot ? Why like windows once it is SET will in not 'stay' set on on re-booting ? I am not complaining just wanting to find a fix. Also this may be a similar problem - in Knotes I put what it claims will be a 'permanent sticky' on the desktop and it disappears on reboot too. I was going to ask if the antivirus remains on also but I think clamtk does not have the real time feature since it is unneeded due to linuxs less penetrable security system. 

So I am here to ask about the firewall first. i installed the Gufw firewall which I found through the ubuntu software center I think. I am literately 2 days old in linux and have no experience and don't have any idea about code at all. However if you sensibly guide me I will then understand you most likely since I have read things here and there before installing linux. I no sudo is often a start term and managed to find where the terminal was but thats it ! I do ctrl + alt + T. I am very simplistic when it comes to computing but hope I can force my self to learn linux coding if I really have too. I'm here to learn in regards to the firewall. I no work networks and public wifi places require the firewall ideally and so am asking why it doesnt stay on on reboot and you need to unlock , password and reset to on each new session.

I looked at hiberating my computer which is a separate thing and could not understand coding at all for that. I could add the first command then I got confused as it seemed to say I needed an editor and to save a file and add to the file too with this command added or something. That was in the help menu for new desktop beginners and needs a re-think for getting it across to people who are new. That was the only confusing part in the help menus about the desktop and other basic operations however.

Many thanks ! :)

---

### Post by deadflowr on 2014-01-07
Run
```
sudo ufw status
```
in a terminal. (password required, and will not be visible when you type it)
The out put should show as active, if you turned on the firewall.
Don't know why the gui's like gufw always show as not on.
But gufw is just a graphical frontend for ufw, which in turn is a frontend for iptables.

sudo is a function that allows a user to become root-level on the system, for a moment.
Long enough to make changes to the system, per a given task.(install software, edit a system file, etc,etc)
sudo functions affect the system, system-wide.
If you need to do something within your own user folders, then sudo is not needed.
More on sudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Sorry, I know nothing about hibernate options.

---

### Post by grahammechanical on 2014-01-07
The actual firewall is UFW (Uncomplicated Firewall) it is installed at the same time that Ubuntu is installed but it is not enabled. Gufw is a graphical user interface for UFW. We can manage UFW using terminal commands or by using Gufw (once installed).

> [COLOR=#333333][FONT=Ubuntu]To enable the firewall, simply check the [/FONT][/COLOR]**Enabled**[COLOR=#333333][FONT=Ubuntu] box[/FONT][/COLOR]

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

Ticking the enabled box should set UFW up to run at boot time. To see if this is happening you can run this command in the terminal

```
sudo ufw status verbose
```

You should see something like this

> Status: active
Logging on: low
Default; deny (incoming), allow (outgoing)
New profiles: skip

What do you see? Is UFW active?

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Regards.

Edit: As a test I have just installed Gufw. We need to authenticate every time we open the Gufw utility and that is a sensible security precaution. Otherwise anyone who gained access to our computer could disable the firewall without our knowledge and so make the machine vulnerable.

The Gufw utility has an opening page with a slider that we can set from Off to On and we get a message at the bottom of the page saying that the firewall is enabled. And it is still enabled after a reboot as proved by running the above command. I get "Status: active."

So, I do not understand why you say that the firewall does not stay on. Perhaps you mean that the Gufw utility does not open without the need to authenticate the user as the administrator?

One of the reasons why Linux is more secure than Windows is that it does not work in the same way as Windows. Ubuntu adds an additional layer of security by removing the need to login as Administrator. The term sudo allows us to work as administrator for a limited time and then we revert back to being a standard user. And it is as a standard user that we work most of the time. In this way our machine is secure from anyone who gains access to it and tries to make changes to the OS without our approval. Dialog boxes that ask for authentication are a graphical way of entering the term "sudo."

---

### Post by hebdave on 2014-01-08
Hi yes it does say it is active with the command I put into the terminal. All I meant was is I was new to linux so when I look at the graphical interface it shows unlocked and says its 'off' on the interface itself. So as a new user of linux its fairly baffling as you then believe that each time you switch it on at booting it turns off. Personally I'd change it somehow so that because it would attract more people to 'stay with' linux. However I think its probably possible that it happens with may other pieces of software for security perhaps in a similar way to the firewall perhaps. Again being a bit harsh with my view and would say that would also be confusing too if it is the case. I think while I will get used to 'change' since it is not m.windows anymore that it will still remain odd to new users. If there is really no other computing way to get round things thats a shame. I fear new users may go back to windows (thats the only reason I am still talking really). Having said that is is great to no it is still active but for some reason when I look at the GUI it does leave me in 'some doubt' as to what is 'really' happening. I guess its testable in some way to prove its okay though. Hope you don't mind me sharing my new user perception I really want to see linux flourish as windows is just so unsafe these days. If people don't normally complain about linux for the reason I stated it this is potentially still what they'd think. What I do like it that linux is so secure because of it being built like it is. But is there a way of getting the best of both worlds? Will linux ubuntu be like this is 10 years time with the graphical interface still looking switched off ?... hmm hard to say ? Could not the interface say its 'on' but not really be on to outsiders instead on reboot ? Is there some way round it- I bet there must be !?  This would bring user reassurance and more folk would stop with linux I think. I'm sure I am missing the point perhaps but just a thought anyway. 

Thanks for your help glad to no its functioning much appreciated.

Edit- However I do have the 13.04 as I thought it might be more stable than new releases , some issues with new releases for some things was my reasoning. So things may be different there.

---

### Post by mastablasta on 2014-01-08
what do you mena? you mean it is not enabled on reboot?

or oyu mean that the status is displayed strange (slider)? i think slider is strange.

interafce in linux is constantly changing and user's input is welcomed. but it doesn't get far on this forum. as this is a help forum and developers are rarely here. there are other addresse where one can recomend and give ideas to improve it.

otherwise unlike widnows ubuntu doeasn't have any ports opened by default. so usually the router/modem firewall is enough which is why many do not tinker with the ufw. but some users might still want to do it. but sane defaults are already incorporated in the OS.

i think ubuntu manual (check link in my signature) should be part of the Ubuntu help files.

---

### Post by hebdave on 2014-01-08
The GUI is not enabled on re-boot thats what I am saying Yes. However as explained it does show in the teminal command prompt as 'active' since I typed that in. On re-boot the GUI always turns off pretending it is disabled when its not. This is the way things seem to be. I have ubuntu 13.04 was my other point which may be an issue but shouldn&#8217;t be. is it worth telling the developer since a large percentage of people will have a firewall. As I understand it you do need a firewall for public places and perhaps other senarios. Can you explain that futher maybe to me ? 

Many thanks you guys are very helpful here. Much appreciated !

---

### Post by Impavidus on 2014-01-08
I don't know what Ubuntu will look like in six months, let alone in ten years. It's now completely different from the interface on Ubuntu 6.06, when I first installed Ubuntu. Your problem now sounds like a small bug in the GUI frontend of the firewall. Small problems like that sometimes creep up. This happens on systems developing much faster than Windows.

Something else though, Ubuntu 13.04 only had 9 months of support, of which only a few weeks are left. The problem may already be solved on 13.10. 13.10 is stable enough for daily usage. If you want something rock-solid, use LTS releases, not the latest-but-one release.

---

### Post by deadflowr on 2014-01-08
> [COLOR=#000000]As I understand it you do need a firewall for public places and perhaps other senarios.[/COLOR]

I would think that a secure connection would be a higher priority than a firewall.
Firewalls can help stutter efforts by unknown entities from gaining access to the system, but won't stop someone who has high-jacked your existing connection.

---

### Post by 3rdalbum on 2014-01-08
Some here disagree with me, but a personal firewall is completely unnecessary on a normal install of Ubuntu.

A firewall was necessary on Windows because the operating system itself would respond to incoming connection requests from anybody on the internet. The firewall hides the connection request from the operating syatem. Ubuntu does not respond to connection requests , unless you install some server software. End result: Exactly the same as if you had a firewall installed.

The toggle switch moving back to "off" is not normal. The switch reads the state of the firewall and displays it, but for some reason in your case it isn't. Must be a bug. Either way, even if you turn off the firewall, you'll have the same amount of protection.

---

### Post by hebdave on 2014-01-08
Can I use ubootin to get the older release as I have to do it from a memory key or at least a none cd method. I seem to remember ubootin did not allow me to get it when I had looked before but I am not sure. I think ubuntu has to be put on a machine via some external source ie cd , key etc . Am I about right ? 

Just to say i will be asking how to install the server onto the desktop or need a server edition as they seem to call it. I will be trying to put wordpress onto a server edition. I take it that you get a desktop too with a sever edition - of not I need a desktop first then the server which according to the blogs online is done through lamp as just one method.  It also means I may now need a firewall given what I read above if I have a website server.

Thanks very much.

---

### Post by deadflowr on 2014-01-08
> [COLOR=#000000] I take it that you get a desktop too with a sever edition [/COLOR]

No

If you install the server version, you would have to install the desktop yourself.
It's a command line interface.

---

### Post by 3rdalbum on 2014-01-08
You don't get a desktop with the Server edition. Just install WordPress, PHP, Apache etc onto your Desktop edition.

If you want the WordPress site visible from the internet, then you at least need Port 80 (web server port) allowed in the firewall, or to not use a firewall. If your modem has a firewall too, you will need to configure that to allow port 80. If you have a firewall in your modem you can probably get by without one running on your computer.

---

### Post by mastablasta on 2014-01-08
and i would add here that if you dont' plan to actually run a webserver on your computer and you need wordpress just to develop, try it out, test... then a better way is to simply use an image from turnkeylinux preloaded with wordpress and then just run that oen in virtual box. it needs only about 250-300RAM to run.

ofcourse if you want a server then this is not usually done on a desktop mashcine. ofcourse internet server has to allow outside access in some way otherwise the only one reading the website will be you :-D

instead of downgrading why not just upgrade to 13.10 and then to 14.04 LZS (Long Term Support) when it comes out.

---

### Post by hebdave on 2014-01-09
[QUOTE=

instead of downgrading why not just upgrade to 13.10 and then to 14.04 LZS (Long Term Support) when it comes out.[/QUOTE]

You guys are really helpful thank you very much :-k  So how does it tend to happen with support Mastablasta or anyone ? I am not sure we are on the money here quite as I read a few blogs etc.-

This seemed the best summary below.

 [http://askubuntu.com/questions/16366/whats-the-difference-between-a-long-term-support-release-and-a-normal-release](http://askubuntu.com/questions/16366/whats-the-difference-between-a-long-term-support-release-and-a-normal-release)

Is it trying to say that eventually all versions become an LTS. i.e. 13.10 after its 16 months of support thats left has a approx. 2 year GAP where it is UNSUPPORTED. Then after say 2 years it might becomes an LTS instead with its ubuntu distro. If so they are effectively will have it very stable in all respects by then for commercial purposes. Since I am just needing a website and will be buying hosting it is different as I will not be the host server 'they will'. Although it would still be self hosting using wordpress that I am doing rather than say using blogger blogs which is hosted already. Any self-hosting does bring complications to a diagree especially when I'm new to it. I don't know if Linux with wordpress has a better reputation than say windows op with wordpress. I gather windows is a one click install but linux is not but hopefully thats not going to cause to many difficulties initially for me. 

It might be you would advise me to read up on linux itself first to find out what its truly about as a desktop distro operating system before me using words like 'LAMP' to install wordpress I think with linux. Although I am not 100 % sure on that yet as I only read about LAMP yesterday. It all new folks - I'm moving to linux due to better security with online websites hopefully. Its often as you'd be aware cheaper than paying people to make things water tight with windows easy to exploit set up. 

A MESSAGE TO THE MODERATOR - DOES THIS THREAD NOW NEED MOVING ELSEWHERE DUE TO SUBJECT CHANGE - ONLY THIS POST NEEDS MOVING NOT THE THREAD AS THE REST WAS ABOUT FIREWALL. I DON'T MIND IT STAYING HERE IF PEOPLE ARE JUST AS EQUIPPED TO ANSWER.

Thanks everyone for your really helpful advice !

---

### Post by deadflowr on 2014-01-09
> [COLOR=#000000]A MESSAGE TO THE MODERATOR - DOES THIS THREAD NOW NEED MOVING ELSEWHERE DUE TO SUBJECT CHANGE - ONLY THIS POST NEEDS MOVING NOT THE THREAD AS THE REST WAS ABOUT FIREWALL. I DON'T MIND IT STAYING HERE IF PEOPLE ARE JUST AS EQUIPPED TO ANSWER.[/COLOR]

Use the report post button at the bottom of the post, and post what you wrote there.
A mod will review it and decide if intervention is needed.

As far as how the release cycles will go, it's still somewhat up in the air.
What we do know is that the LTS release cycles will remain like they are.
The interim, well, who knows.
Like Ubuntu itself, those things are a moving target and a work in progress.

---

