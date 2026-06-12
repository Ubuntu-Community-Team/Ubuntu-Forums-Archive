---
title: "Waterfox, how to get it?"
date: 2020-02-27
forum: New to Ubuntu
---

### Post by alfero on 2020-02-27
Hi,            
                        
The last thing that i need to get now in Xubuntu is a second navigator: Waterfox, but is not in the repos, and i have been reading different posts here and there on internet, tried a cup of things, but i’m not able to get it, the “solutions” if there is any, is it out of my understanding ... why is Waterfox not friendly with Ubuntu?.            
                        
I did not find anything here in this forum about it, searching ... n[COLOR=#000000]**othing is coming up.**[/COLOR]            
                        [COLOR=#000000][B]
Is it impossible to get Waterfox installed in Ubuntu in an easy way?.[/B][/COLOR]            
                        [COLOR=#000000][B]
Please, any tutorial or information for a newbie to help with this subject will be grateful.[/B][/COLOR]            
                        [COLOR=#000000][B]
Thank you very much.[/B][/COLOR]

---

### Post by Holger_Gehrke on 2020-02-27
You've got two options:


[LIST=1]
[*]According to 'snap find waterfox' there's a snap package of waterfox 2020.01 (version from last month). If you can live with the restrictions snap puts on applications then that's fine, I generally prefer not to use snaps.
[*]Install the binary from waterfox.com/download. Not as difficult as it sounds. Download the Archive then double-click waterfox-current-2020.02.en-US.linux-x86_64.tar.bz2 in the file manager. This should open an archive manager - probably file-roller. Switch back to the file manager and go to your home directory. Now switch to the archive manager and drag'n'drop the directory 'waterfox' from the archive manager into the file manager to unpack into the home directory. In an ideal world that would be it, but when has the world ever been close to ideal ... There's one library waterfox needs which is neither included in the archive nor part of the default install. Open a terminal and enter 'sudo apt install libc++1'. After asking for your password (which you will have to enter without any feedback by the computer) it will install the lib. Now you can enter '~/waterfox/waterfox' and waterfox will run. If you want an icon in the menu or on the desktop then the easiest way is to copy the .desktop-file for firefox from /usr/share/applications to ~/.local/share/applications, rename the copy to waterfox.desktop and change it with a text editor replacing Firefox in the Name-lines with Waterfox and firefox in the Exec-lines with the full path and name for waterfox.
[/LIST]
 
Holger

---

### Post by Impavidus on 2020-02-27
Best option is to try an appimage, snap or a ppa. My preference would be a ppa. Have a look here:
[https://github.com/hawkeye116477/waterfox-deb-rpm-arch-AppImage](https://github.com/hawkeye116477/waterfox-deb-rpm-arch-AppImage)
It's an unofficial source. You have to decide whether you trust it.

---

### Post by alfero on 2020-02-27
This is exactly the information i had already seen searching the internet. No, i can't follow it, things don't come out, i've tried several times, nothing, i don't understand well. I have lost more time in this since yesterday than in installing the system.


If there is nothing else ... anyway, thank you very much.

---

### Post by CelticWarrior on 2020-02-27
What can't you follow? What steps you don't understand? And, very important, which method have you tried and the results?

Better to choose a method and stick to it, only try a different approach if it doesn't work. And when asking for help you should always describe what you tried already and the results.

I could install it in a matter of minutes using Holger's info. Basically all we have to do prior to run the installer is to install the dependency, in terminal:
```
sudo apt install libc++1
```

---

### Post by alfero on 2020-02-27
After the instalation of this package, now i can get it, two installers are coming gdebi and the roller, thanks.

The only problem is that i have to install privative software, for now i just want to see how the system work without it (it was a recommendation for another place).

Any way i will considered solved.

---

### Post by yetimon_64 on 2020-02-27
> **alfero said:**
> ...
Any way i will considered solved.
Could you please mark the thread as [SOLVED] by using the thread tools drop down menu at the top of your browser window?
The blue link in my signature below is to a guide for how to do so if needed. Regards, yeti.

---

### Post by alfero on 2020-02-27
I did't it do it before because nobody is doing this elemental requirement here, when i came yesterday and start to search it was looking to me like no thread were solved at this forum. :o

---

### Post by yetimon_64 on 2020-02-28
> **alfero said:**
> ... it was looking to me like no thread were solved at this forum. :o
Sorry if my request surprised you but asking an OP to mark a thread as solved is common practice here.

It helps the people supplying the answers to know which threads to focus there efforts on and saves them time from having to wade through a thread only to find it no longer needs help. Marking the thread solved also helps users searching the forum to find information/solutions for their problems as well.

You are right in that not enough users, particularly new users unfamiliar with the forum, do not do so. I only ask people to mark their thread when it is clearly apparent it is concluded like with the part of your post I quoted above in my first post here.

It is not mandatory but it does help out other users and even the helpers who help you as well.

Regards, yeti. :)

---

### Post by alfero on 2020-02-28
No, it is my English, what surprised me is, or it was, not to see any post marked as solved. 

All the contrary i think that this should be a kind of mandatory requirement.
It is shameful to come to a place where you can resolve a problem and to receive the help you need and not even to give thanks or to indicate others that the problem was solved. 

&#65279;Kindness is something that every day is scarcer.

---

### Post by yetimon_64 on 2020-02-28
> **alfero said:**
> No, it is my English, what surprised me is, or it was, not to see any post marked as solved. Ah OK, I understand what you mean quite a bit better now.

> **alfero said:**
> All the contrary i think that this should be a kind of mandatory requirement.
It is shameful to come to a place where you can resolve a problem and to receive the help you need and not even to give thanks or to indicate others that the problem was solved. Yes that would be ideal if everyone was good enough to do so. I think the age and size of the forum, with over 2 million members and over 2 million threads, might make this too difficult to enforce though. Despite my current profile age, I have actually been a member here since 2010, I remember times here when this forum was incredibly active and busy. It would have been an absolute nightmare back then for staff to even consider trying to enforce marking threads. The forum nowadays is by far less active than it used to be, but with the old habit of requesting marking threads still used like back in the busier days.

&#65279;> **alfero said:**
> Kindness is something that every day is scarcer.
+1, Sad but true in my opinion.

All the best to you. I better "sign off" now lest this thread runs too far off topic ;). Cheers, yeti.):P

---

### Post by alfero on 2020-03-02
Just in case somebody need it, i found today an easy way to get waterfox for Ubuntu:


[https://askubuntu.com/questions/935466/how-do-i-install-waterfox](https://askubuntu.com/questions/935466/how-do-i-install-waterfox)

---

### Post by hk42 on 2020-03-03
Thanks for this topic
I just tried waterfox as appimage it is OK in both 19.04 and 19.10.
On the contrary firefox keeps destroying my profile when I switch from 04 to 10.
Netflix is OK with waterfox.

---

### Post by Impavidus on 2020-03-03
There's no reason to switch back and forth between 19.04 and 19.10. 19.04 reached end of life over a month ago. But I can understand why some people switch back and forth between 18.04 and 19.10.

---

### Post by hk42 on 2020-04-09
> **Impavidus said:**
> There's no reason to switch back and forth between 19.04 and 19.10. 19.04 reached end of life over a month ago. But I can understand why some people switch back and forth between 18.04 and 19.10.

There is no reason for firefox and others to loose all preference ,bookmarks,and passwords when upgrading OS.
With Windows I'm still waiting for drivers updates (creative labs ,iomega,cinergy,asus) so I still use XP.
Linux seems to be a bit better at least as far as hardware is concerned.

---

