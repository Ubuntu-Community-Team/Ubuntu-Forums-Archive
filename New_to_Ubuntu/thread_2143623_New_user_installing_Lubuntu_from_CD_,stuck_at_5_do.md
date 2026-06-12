---
title: "New user installing Lubuntu from CD ,stuck at 5 dots moving."
date: 2013-05-09
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-09
Hey everyone here. Im new to linux and i have a question. I decided to install lubuntu 13.04 to my laptop and i chose the install from cd thingy. But now the 5 dots are moving but it has been like that for over 20 minutes? Is that normal?

---

### Post by Impavidus on 2013-05-09
No, that's not normal. We'll need some more information to help you. Which version of Lubuntu is this? And can you give some details on your hardware? Make and model of the laptop, video card, amount of RAM. There may be some incompatibility, but usually these can be solved.

Have you already installed or are you just booting from the cd now? Is there a different operating system present on the laptop, like Windows 7 or 8?

---

### Post by DragonGirl123 on 2013-05-09
I have windows 7 on my laptop as well. I have an acer aspire aspire 5742G. Intel Core i3-380m ,nvidia geforce gt 630m 1gb. 6GB DDR3 Ram. I downloaded the 64 bit torrent from here for the pc [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu). No i havent installed it already ,and yes im just booting from the cd. Sorry for grammar mistakes because english isnt my first language.

---

### Post by Impavidus on 2013-05-09
Try the nomodeset boot option. It has to do with the kernel not working with your video card natively. It can be solved after installation. This is common with nvidia cards.

See [http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb](http://askubuntu.com/questions/152847/how-to-access-boot-options-12-04-live-usb) Read the first answer.

And english isn't my first language either.

---

### Post by DragonGirl123 on 2013-05-09
should i shut down my computer or how do i get back to the boot option screen? sorry for nooby question.
I got it working ,now the dots look diffrent ,how long should i wait?
YaY the install welcome thing came up, i hope i wasent too much of an hassile just im noob at linux.

---

### Post by newb85 on 2013-05-09
Good to hear it's working. Please mark the thread as solved (click on"thread tools"...).  Also, you'll want to make sure to install the nvidia drivers.  I'm not sure how that's done in Lubuntu, but I'm sure it's straight-forward these days.

---

### Post by ikt on 2013-05-09
> **DragonGirl123 said:**
> i hope i wasent too much of an hassile just im noob at linux.

Hey don't think like that! We were all noobs once, my first time using linux it was so hard I couldn't install it, I tried like 10 different distro's and couldn't get any of them to install, so I gave up on it until Ubuntu came along and it was the only linux OS that would install on my computer easily.

Ask as many questions as you like, because you can be sure that if you're asking the question, at least 10 other people also want to know the answer, we even have a site dedicated to asking questions:

[http://askubuntu.com/](http://askubuntu.com/)

So don't ever feel ashamed or 'a hassle' because for every super elite linux who's above "the noobs", there are hundreds of thousands of people looking for answers to questions and looking to help others out. Hope your experience gets better from here on in :)

---

### Post by DragonGirl123 on 2013-05-09
> **ikt said:**
> Hey don't think like that! We were all noobs once, my first time using linux it was so hard I couldn't install it, I tried like 10 different distro's and couldn't get any of them to install, so I gave up on it until Ubuntu came along and it was the only linux OS that would install on my computer easily.

Ask as many questions as you like, because you can be sure that if you're asking the question, at least 10 other people also want to know the answer, we even have a site dedicated to asking questions:

[http://askubuntu.com/](http://askubuntu.com/)

So don't ever feel ashamed or 'a hassle' because for every super elite linux who's above "the noobs", there are hundreds of thousands of people looking for answers to questions and looking to help others out. Hope your experience gets better from here on in :)
Thanks for the warm welcome , im only a 14 year old girl. Im glad that it is soon finished installing ,thanks for the help.

---

### Post by Impavidus on 2013-05-09
I was just checking a different subforum.

As you have now booted into a live session you can have a look around. You can check whether wifi is working (if you need it), it is the second most common cause of hardware problems (after graphics). After installation you'll have to install nvidia drivers. I'm not the specialist in that matter, but there are some people around here who know a lot about that. We'll help you through.

---

### Post by DragonGirl123 on 2013-05-09
it installed and runs ,now how do i get my wifi to work?

---

### Post by Impavidus on 2013-05-09
I don't how what the menu looks like in Lubuntu, but somewhere in "settings" there must be something for network connections. There you should be able to set the name and password for the network. These settings won't persist after rebooting until you have installed, but it's mostly for testing. It's good to know in advance whether your wifi will work or whether you'll need to download additional drivers for it.

---

### Post by grahammechanical on 2013-05-09
> **DragonGirl123 said:**
> it installed and runs ,now how do i get my wifi to work?

That depends upon your meaning. It could be that you need a driver or that you are not sure of the method to make a WiFi connection. I could explain it to you if you was using standard Ubuntu but I am not using Lubuntu. So the best that I can do is give you this link. I am sure that it will be helpful.

[https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

Apparently under the Networking heading you are advised to look in the "tray" for Network Manager. I am guessing that in Lubuntu the tray is at the bottom of the screen. Clicking on the Network Manager icon will pull up a menu. Do you see any WiFi access points listed? Is your network there? If the answer is Yes, then you do not need a wireless driver.

See how you go for now

Regards and welcome to the community.

---

### Post by DragonGirl123 on 2013-05-09
it only shows my wired connection not my wireless.

---

### Post by grahammechanical on 2013-05-09
Then you need a driver. Look for System Settings. I cannot tell you where it is in Lubuntu but once you have opened System Settings look for Software & Updates and open that. Then go to the Additional Drivers tab. It is there that you can change video drivers but you should also find an option to install a wireless driver.

Regards.

---

### Post by DragonGirl123 on 2013-05-09
when i click software updater it said software is up to date.

---

### Post by grahammechanical on 2013-05-09
You need to find a utility called Software & Updates (that is its name in 13.04). It used to be called Software Sources. It is a place where we can change settings for receiving notification of updates. It is also now (in 13.04) where we install additional drivers. There used to be a separate utility to do this but it is now part of Software & Updates. It is a different utility to Update Manager/Software Updater.

---

### Post by DragonGirl123 on 2013-05-09
found it, doing it right now. Yay got my wifi working :D .Now how do i get steam working so i can talk to my friends there?

---

### Post by Impavidus on 2013-05-09
I don't know.

Did everything else go fine? Setting up your partitions et cetera?

---

### Post by DragonGirl123 on 2013-05-09
yeah the partion thingy got fine, just i need to get stem working? anyone?

---

### Post by grahammechanical on 2013-05-09
Steam? I am so old that I remember steam trains and that is about all I know about steam. You might find this interesting:

[http://www.webupd8.org/2013/03/how-to-chat-with-your-steam-friends.html](http://www.webupd8.org/2013/03/how-to-chat-with-your-steam-friends.html)

[http://www.omgubuntu.co.uk/2013/05/valve-release-portal-beta-for-linux](http://www.omgubuntu.co.uk/2013/05/valve-release-portal-beta-for-linux)

I find both of those sites useful for keeping up to date with Linux and Ubuntu.

Regards.

---

### Post by DragonGirl123 on 2013-05-09
how do you do @ symbol at linux? it dosent seem to work the way it does in windows

---

### Post by Impavidus on 2013-05-09
It depends on your keyboard. On mine (US keyboard) it's shift-2. Maybe Ubuntu thinks you have a different kind of keyboard than you really have. Check the keyboard settings.

---

### Post by DragonGirl123 on 2013-05-09
*i had estonian keyboard selected because i have one ,but when i selected estonian keyboard with us letters now it works ,thanks for the help.*

---

### Post by DragonGirl123 on 2013-05-09
also i have another question , i got steam installed but trough ubuntu software center but it gives me error ,32 bit librairies are missing. What to do

---

### Post by Impavidus on 2013-05-10
You may need 32 bit versions of libraries. Installing ia32-libs seems the way to go, but read this: [http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

I haven't done things like this myself, as I don't have enough RAM to fully utilise 64 bit, so I'm still with 32 bit.

---

### Post by DragonGirl123 on 2013-05-10
Got steam working. :D

---

