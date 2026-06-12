---
title: "New to Ubuntu. Having some light resistance."
date: 2019-01-13
forum: New to Ubuntu
---

### Post by okfinethen on 2019-01-13
Hello all,

I am new to linux/ubuntu. I recently bought a lenovo thinkpad 580 and I am hung up on a few things. 

The few things:

I had an encrypted dual boot WIN10/Ubuntu 18.04.1 LTS installed from a small computer shop. I want a chance to learn more about safer and private computing. Also, I want to show my kids there is something more out there the IOS/WIN10. I would always rather be coached then have things done for me,so I am posting this. I worked with very little DOS when I was 8yo on a 486/33, I had a bbs, 2800 & 14.4 modems, good times. I am not afraid of terminal at all and I am really interested in putting the effort in.

So here it goes.  The guys at the shop installed Ubuntu with my personal information, specifically home drive. I am trying to see how far I can get without throwing my name and details around. I did read about usermod and making a separate (temp user) which worked...kinda.

-I was able to change the device name in settings->details->about.Bonus I got my name off that.
-So my terminal reads myname@newdevicename (what are these terms called what??@what??).I got the home folder name changed in terminal (newname@newname) but the old name still shows up in the finder/explorer or whatever Ubuntu calls the file program. My concern about the change I made here is config file references and such. Really who knows what I have potentially done.

So back to the shop. I Asked for help and they were googling the forums to fix the home drive issue. Not very confidence inspiring. I was hoping they would have a bit more experience. So I kindly said I will live with it and ran out of the store laptop in hand.

This is becoming quite a story now but hopefully you will keep reading on.

So I work with the laptop and realise ubuntu is going to work for me and decide to just reinstall a fresh version of ubuntu and turf my dualboot and windows entirely. No problem. 


I Get a usb->download the 18.04.1 LTS iso. reboot with the usb and no love. Into the Bios I go and move USB up in priority, reboot and still no action. Straight to the dual boot OS selection screen everytime. So that is a problem, now I am going to my happy place and breathing it out. So I wipe the usb and make a USB through "startupdisk creator" and it hangs at 8%. Really?!?! 

Doing all this made me realise I don't have all the drivers for the laptop.What if I re-install and my camera, keyboard functions and who god know what might not work. So I go to lenovo's website and no linux drivers for the laptop only Win10. Also there are quite a few drivers. Which drivers should I install first? Should I omit any?But I am still working through it, I am committed to the change. This makes me realise I should look for a flow chart of the best way to setup a computer from scratch. 

So my plan based off my limited patience is to have the USB stick with Ubuntu OS install and drivers in a separate new folder. I mess with this and no love. Then I remember I had the shop encrypt the hard drive. I have a 250gb M2 for the OS and and ssdHD for extra storage. I then ask myself, is the encryption screwing me up or can I wipe everything now?

Also,I was excited to move to linux in whatever flavor to try to make my identity a little less easy to find. Teach my kids that some privacy is important and should be on their radar. To sign up to this forum I gave up my credentials, a little life sucking. Will I really have to create a whole new "fake identity" to be able to try and be a little more anonymous? I don't know if I want to teach my kids that they need to start creating fake identities to survive online. So I have been researching email accounts. Ideally something with aliases. I don't know, there was one under Switzerland I read about. Something not google and something where I don't have to send my mom a secret passcode to make plans for lunch. 

So I find myself here. As you can see I violated the "no long post rule" on my first post. I have found writing it therapeutic though. Also I have read and re-read the post for grammar and spelling, I tried.

Any help would be super appreciated. Likely I will have shitpot more question in the future.

Be well,

Okfinethen

---

### Post by The Cog on 2019-01-13
> So my terminal reads myname@newdevicename (what are these terms called what??@what??)
They are called username@hostname.

What are you asking for help for? Changing your username, making a USB installer perhaps?

---

### Post by oldfred on 2019-01-13
I only have desktop, so do not use encryption on entire system as it only is inside my home.
Ubuntu's encyption uses LVM which normally is full drive, or it erases Windows. You can use LVM on part of  a drive, but install is a lot more complicated and you lose some of the advantages of LVM which manages the entire drive with volumes, not partitions.
Using LVM & encryption is like jumping into the deep end of the pool to learn to swim. You may survive, but will require a lot of work.
Often better or easier to start with standard Ubuntu install in one partition which is now the default install. If UEFI, which all newer systems use, it will use or need an ESP - efi system partition. Some users that understand partitions like to separate operating system from user data and use another partition for /home.

Ubuntu is a multiple user system, so you can have multiple users in /home (folder if just / (root), or partition). But normally only one user has administrative rights to use sudo to temporarily be the admin and make system changes. Windows used to assume you always are an Admin, although now you have to click on an admin session, somewhat like using sudo. Other Linux have a user root that is the admin, but then too many new users stay in root and then do not have some of the protections that prevent a normal user from accessing system functions.

Your user name in Ubuntu is not really sent anywhere, but  often we ask for terminal output and it will show. Some users do use different names which may not be name they login to Ubuntu forums or other Internet sites.

---

### Post by Geoffrey_Arndt on 2019-01-14
Suggest you try "Etcher" for creating your bootable devices.   Works on all platforms.  Very simple too.   [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

---

### Post by mastablasta on 2019-01-14
for reinstall:

1. download the image
2. check the hash of the downloaded image : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
3. many usb creators currently do not work,use the one that works and create the USB or create a DVD (which will always work)

for full privacy - you would need to use something like TailsOS or similar and use it in live session only. the search engines have many means of tracking the users. you would also need a VPN and onion browser. with too much stuff loaded you might look suspicious, just as you would  if you went to a mall with a ski mask on and olive or black suit. it's plain and strange. :)

as i know Ubuntu offer the option of (temporary) guest account which would delete all the stuff after logging out. it is meant to be used if you want to borrow temporarily someone your laptop and you wouldn't want them to access your data or other things on the PC.

encryption adds a layer of complexity, however on a laptop that is moved around and can potentially be stole it is probably a must.

---

### Post by yancek on 2019-01-14
> [COLOR=#222222][FONT=Verdana] The guys at the shop installed Ubuntu with my personal information, specifically home drive.[/FONT][/COLOR]

I'm trying to understand what that means.  When you install Ubuntu (or any Linux) you need to create at least one user and have a password for that user.  When you say home drive do you mean you have home on a separate physical hard drive?  Windows usually uses the terms for physical hard drive, partition and volume interchangeably so it gets confusing.    

> [COLOR=#222222][FONT=Verdana].I got the home folder name changed in terminal (newname@newname) [/FONT][/COLOR]

Do you mean the user named directory under the /home directory?  You don't want to change the name of the /home directory itself.  Your subsequent statement would seem to indicate that you simply created another user.  Specifically, can you tell us what you did to try to make this change?

> [COLOR=#222222][FONT=Verdana] in the finder/explorer or whatever Ubuntu calls the file program[/FONT][/COLOR]

Linux system generally refer to it as a "File Manager" because it is used in a graphical environment to 'find' and 'explore' as well as manage directories and files.  The term "Finder" and "Explorer are specific to Apple and microsoft systems respectively.

Ubuntu has a site with a detailed explanation of installing it on a computer with a windows 10 system at the link below so read through that to get a basic understanding.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link below is to the official Ubuntu Manual which explains using the operating system.  Has several different versions so get the correct one.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by okfinethen on 2019-01-14
Ok I am going to work through these responses. Thanks so much for the great replies.

Okfinethen

---

### Post by okfinethen on 2019-01-14
Okiedokie I figured out multi-quote lol

> **The Cog said:**
> They are called username@hostname.

What are you asking for help for? Changing your username, making a USB installer perhaps?

Thanks I am just trying to get rid of my dual boot win10/ubuntu and run straight Ubuntu. I think the issues are possibly getting resolved.

> **Geoffrey_Arndt said:**
> Suggest you try "Etcher" for creating  your bootable devices.   Works on all platforms.  Very simple too.   [https://www.balena.io/etcher/](https://www.balena.io/etcher/)

Thanks I will give that a try! I was worried when the "startup disk app" from search stopped at 8%

> **mastablasta said:**
> for reinstall:

for full privacy - you would need to use something like TailsOS or  similar and use it in live session only. the search engines have many  means of tracking the users. you would also need a VPN and onion  browser. with too much stuff loaded you might look suspicious, just as  you would  if you went to a mall with a ski mask on and olive or black  suit. it's plain and strange. [IMG]https://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

Yes I agree very much about the ski mask comment. I have watched my share of documentaries about privacy. I really like [Nothing to Hide]("https://topdocumentaryfilms.com/nothing-hide/"),  and so many others. I could quote that movie all day. For me it just  seems that there should be an easier solution to protect identities.  It's a conversation that makes people glaze over. I would love to see a  day that the average person and their kids are protected, even with a  low computing IQ (in fact aren't those folks the ones who need it most?). I don't think it is reasonable to have End2End email encryption for my parents or my kids. It is very important though, in  Canada right now there are stories all the time of people falling for  scams. It's sad...real sad. So I ask, what the hell can I do about it? I  can learn it for myself, teach my kids and talk about it with my family  and friends. 

> **yancek said:**
> I'm trying to understand what that means.  When  you install Ubuntu (or any Linux) you need to create at least one user  and have a password for that user.  When you say home drive do you mean  you have home on a separate physical hard drive?  Windows usually uses  the terms for physical hard drive, partition and volume interchangeably  so it gets confusing.    

This is where I got stuck by having someone else doing my install/encryption for  the laptop. I wasn't involved in actually doing it. I asked for a dual  boot Win10 and Ubuntu. I had a 250gb HD split into 2 parts 130gb for  ubuntu and 86gb for win10. When I fire up the computer I get a DOS looking  screen giving me OS options. I did this because I wanted to explore  Ubuntu while the rest of the family can still log into WIN10. 

I also had them encrypt the drive. The whole thing I am assuming. I now realize I should have asked more questions...

[COLOR=#ff0000][/COLOR]> **yancek said:**
> Do  you mean the user named directory under the /home directory?  You don't  want to change the name of the /home directory itself.  Your subsequent  statement would seem to indicate that you simply created another user.   Specifically, can you tell us what you did to try to make this  change?

Ok so I used Usermod in terminal for this with all kinds of attributes. eg usermod -this -that (i cant remember exactly what I used or what the options are called in ubuntu speak). 

I tried to rename the /home/*this_is_what_i_renamed

I wasn't able to because I got an error that /home/*this_is_what_i_renamed was in use. 

So I read a solution that said to make a temp folder move everything over and delete the other folder. 

I stopped here because I was worried there would be potential broken links or some other problems.

***My  main concern about this as well is losing any drivers for the laptop  when I re-install Ubuntu clean. I am worried things like my camera, mic  and FunctionKeys may not work.
At the lenovo website there are so many  drivers and updates but all windows. No linux option. So I haven't wiped the drive  until I got some responses from the forums.
 
> **yancek said:**
> Linux system generally refer to it as a "File  Manager" because it is used in a graphical environment to 'find' and  'explore' as well as manage directories and files.  The term "Finder"  and "Explorer are specific to Apple and microsoft systems respectively.

Ubuntu has a site with a detailed explanation of installing it on a  computer with a windows 10 system at the link below so read through that  to get a basic understanding.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The link below is to the official Ubuntu Manual which explains using the  operating system.  Has several different versions so get the correct  one.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

Yep it is time to read the manuals : ) 

Thanks for the links!

You all take care and I really appreciate the responses

okfinethen




Okfinethen

---

