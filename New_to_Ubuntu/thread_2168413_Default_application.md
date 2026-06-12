---
title: "Default application"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-08-17
When i try to change the default application for any kind of file (here i tried with mp3) it gives the following error 

**Error while setting "setting VLC media player" as default application : Failed to create file '/home/may/.local/share/applications/mimeapps.list.PU9W1W' : Permission denied**

(kindly see the attachment).

When i try to do the same from settings (default application), it crashes. The problem occurs for any application.

---

### Post by Crusty Old Fart on 2013-08-17
Maybe you need to be logged in as root in order to change that default setting.
Have you tried that?

Just a wild guess on my part.

Good luck,

Crusty

---

### Post by steamer360 on 2013-08-18
It might be a problem with VLC, does VLC work without being set to default? If not try uninstalling it and then installing it again.

---

### Post by Crusty Old Fart on 2013-08-18
> **steamer360 said:**
> It might be a problem with VLC, does VLC work without being set to default? If not try uninstalling it and then installing it again.

Maybe, but the OP wrote:
> **3dmatrix said:**
> ...When i try to do the same from settings (default application), it crashes. The problem occurs for any application.

It seems as though he doesn't have permission to set default applications from the GUI for anything.
If he can do it as root, then it may be that his user permissions are a bit hosed. If he can't do it as root, maybe his installation is hosed.

It might be helpful if he could attach a similar image with his Permissions tab active.

---

### Post by 3dmatrix on 2013-08-18
What i earlier considered, as a simple permission error, now seems even more complicated.

[B](1) I can not change default application of ANY file type. i have tried with mp3 and jpg.
(2) from root, i can change it but it is applicable only for the root user. when i am back to the user level it remains unchanged.
(3) If i try to change through system settings, system settings window crashes.
(4) The system is not able to copy / paste files to any usb drive. It gives error that the usb drive is read only.
(5) If i 'send to' that usb drive then it is possible to transfer file.
(6) When i use the same usb drive on other system, it works perfectly well.
(7) VLC is working normaly when i play the same file using 'open with' VLC.
[/B]
This is newly installed system which i had done on a friend's computer to introduce her to linux but i am facing so many strange errors.
I am supposed to return the comp today but it seems to still have many imperfections.
I am attaching some snapshots.

---

### Post by Crusty Old Fart on 2013-08-18
If you have set this system up with more than one user, there may have been be a problem with the correct permission levels being properly inherited when you added users. You could try adding another user and taking special care to pay close attention to how his/her permission levels are set up during the process. If everything goes well for him, you could remove the user/users whose permission levels are causing problems.

~~~ HOWEVER ~~~

If I was having as many problems with a new installation as you are, I wouldn't waste anymore time on it. I would start over and reinstall from scratch with a new installation.
You could spend several more days trying to fix all these problems, and possibly discover several more problems that you don't know about yet, and finally find yourself having to reinstall anyway.

---

### Post by 3dmatrix on 2013-08-18
> **Crusty Old Fart said:**
> If you have set this system up with more than one user, there may have been be a problem with the correct permission levels being properly inherited when you added users. You could try adding another user and taking special care to pay close attention to how his/her permission levels are set up during the process. If everything goes well for him, you could remove the user/users whose permission levels are causing problems.

Multiple user has not been created. It is a default system install.

> If I was having as many problems with a new installation as you are, I wouldn't waste anymore time on it. I would start over and reinstall from scratch with a new installation.
You could spend several more days trying to fix all these problems, and possibly discover several more problems that you don't know about yet, and finally find yourself having to reinstall anyway.

Well your advise makes sense. But if i have to reinstall the system then why not dump this version of Ubuntu. It is Ubuntu Kylin an official version of Ubuntu especially made for Chinese users. As my friend is a Chinese i wanted her to use it. But if i am facing so much trouble with it then she (who is new to linux) will get crazy. May be a normal Ubuntu with Chinese language support might be better. UbuntuKylin, it seems, is still carrying a lot of bugs.

---

### Post by Crusty Old Fart on 2013-08-18
> **3dmatrix said:**
> ...Well your advise makes sense. But if i have to reinstall the system then why not dump this version of Ubuntu. It is Ubuntu Kylin an official version of Ubuntu especially made for Chinese users. As my friend is a Chinese i wanted her to use it. But if i am facing so much trouble with it then she (who is new to linux) will get crazy. May be a normal Ubuntu with Chinese language support might be better. UbuntuKylin, it seems, is still carrying a lot of bugs.

I agree. Installing a version of Ubuntu, especially one with which you are already familiar, that has Chinese language support would seem to be a much better idea. It would be easier for you to help her with problems in the future, and she is less likely to perceive you as a someone who really doesn't know what the hell they are doing.

Best of luck to both of you,

Crusty

---

### Post by 3dmatrix on 2013-08-19
Thanks Crusty. Well, I would have certainly installed the normal Ubuntu for her but the problem is, Chinese people are used to some very different kinds of softwares. In fact i again installed the Ubuntu Kylin OS and gave it to her and this time i did not have all those problems but she was still not very satisfied as she was not able to use many XYZ softwares. And perhaps she felt life will be useless without that :) More over she found it so strange that windows softwares will not work in Ubuntu (i purposely did not tell her about wine else she will forever depend on wine and windows softwares and that will beat the very purpose of migrating to linux). It was funny to see her trying to click on every possible exe in her windows partition and say "Why is it not working ?". But the main problem that most chinese people face is online shoping. Here banks ask their customers to download some exe etc and use it on their windows comp for authorisation (i think it just installs a browser plugin). But i do not know how to help her with that.

---

### Post by Crusty Old Fart on 2013-08-19
I'm not surprised to read any of what you wrote. In fact, I expected it  to happen. I came to the conclusion many years ago that Linux is _for_ geeks, _by_ geeks, and _of_  geeks. It's also, in my opinion, the best operating system available.  But it isn't for everyone. The best  thing about Linux is that, if you're  enough of a geek, you can get under its hood, make it stand up and  dance, and it will rock your world. The worst thing about Linux is that  you _have_ to get under its hood just to get it on its feet, and if  you're not enough of a geek to do that, it will leave you frustrated  and disappointed. Now, instead of "giving" Linux to people who know  nothing about it, I tell them to read every single word in [***[COLOR=red]_[COLOR=blue]Linux is Not Windows[/COLOR]_[/COLOR]***]("http://linux.oneandoneis2.org/LNW.htm") and if  they're still interested enough in Linux to put in the time and effort  it requires to learn how to make it work for them, then I'll be happy to answer their  questions. Life is too short to spend days on end customizing an  installation for someone who will never be happy with it because they'll  never learn how to make it dance by themselves. Please understand that even though some of what I've written is stated as fact, all of it is just my crusty old opinion.

---

### Post by 3dmatrix on 2013-08-20
What you wrote is not wrong but with every passing day Linux is becoming more and more 'easy' to use and one does not needs to be a geek (at least i am not). To use it one only needs to have a flexible and open mind to 'accept' new things / new ways of doing things etc. In my last 10 years of 'using' linux i have seen linux becoming far less knowledge oriented (you do not need to know things to use it) and so the learning cure is not steep any more but the problem is, in most cases people do not wish to change. In a lot of cases people do not even use their mind before judging any thing, for example, that lady was astonished when i told her the name of softwares in windows and linux are rarely same. She asked me "Why ?" In China most people have two names (one chinese and one english). She is ready to accept one person having two different names but she is not ready to accept two very different softwares (made for very different environment)  having two different names. I feel my mistake in her case was, I should have kept the windows partitions invisible. Because she could easily click on the windows partition icons and enter and as she saw those windows stuff 'in linux' it made her think, it is the 'same thing'. May be sometimes making things less user-friendly helps  :)

---

### Post by Crusty Old Fart on 2013-08-20
[FONT=Verdana]I agree that the newer Linux distros are a lot  easier to use than those we had in the past. That pretty much goes for  all the technology that folks are hooked to these days. But, comparatively speaking, I still am of the opinion that Linux is for geeks. Perhaps the term "geek" means something a little different where you live than it does where I live.  I'm a geek. There's no question about it. My first lines of code were  written several years before we had text lighting up the phosphorescent coatings on the inside of cathode ray tubes. Back then, people actually used telephones to talk with each other. Can you imagine that? Computers  were actually used for computing (gasp!) and nothing else. Input was  little rectangular holes punched through stiff paper cards. Output was  typewriter ribbon ink stamped onto Z-folded, 11" x 14", [/FONT][FONT=Verdana][FONT=Verdana]pretty, green striped[/FONT]  paper with tractor feed holes running along both edges. Disks were the  size of garbage can lids and the drives were the size of large washing  machines...and on and on and on. A lot has changed in the last forty  years. Personally, I'm not so sure all of it has really been all that  good for society. But, that's a subject that could launch me into a  philosophical tirade that few people would appreciate, so I'll leave it  at that. As a matter of fact, as I write this, my crusty old brain is  being flooded with so much to express regarding the whole Linux vs.  Windows contrast that I could spend the next several hours pounding this  silly keyboard. If I did that, the moderators would probably close my  account, justifiably, and I wouldn't blame them. So, at this point, I  think the best things for me to do are to wish you the best, say good  night, crawl back into my pod and plug myself back into my probes before  the effect of the blue pill I ate wears off completely.
  
All the best wishes to you.
  
Good night,
  
Crusty[/FONT]

---

### Post by 3dmatrix on 2013-08-20
:-)

---

### Post by Jonathan Precise on 2013-08-24
Hello 3dmatrix!

For an easier transition to Linux, I would recommend [Zorin OS]("http://www.zorin-os.com/free7.html"), as it is made to look and feel like windows:) (you can uninstall WINE later if you want).

Unfortunately, do NOT use Software Updater to upgrade to the next ubuntu release (yes, Zorin is based on ubuntu), as this has caused problems in the past:-x. To upgrade to a new Zorin OS version, follow the instructions [here]("http://zorin-os.com/upgradeguide.html").

Also it is very important to use [Firefox]("https://www.mozilla.org/en-US/firefox/new/") to download Zorin OS.

---

