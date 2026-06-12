---
title: "Lubuntu 11.10 - Shutdown button missing from panel"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by Big Lizard on 2011-10-14
I did two installs of Lubuntu 11.10. One computer has the Shutdow button on the panel. On the other computer it's missing and I can't find out how to restore it. (I tried a bunch of the panel applets, but it's not there...or did I miss it.)  How do I get that back?
---BTW, there is no "Shutdown" in the applet list.---

Thanks in advance for any help.
--------------------------------------------------------------
Edit
I guess nobody knows. So much for Lubuntu 11.10.

---

### Post by Ammok on 2011-10-15
Mines is missing too, not found it yet. I have to Switch USer to get the loggon screen and the shutdown button is there on that screen. Unfortunately it does not always shutdown the pc. So have to hard off the pc. Not very good so far really.

---

### Post by verymadpip on 2011-10-15
I deleted my shutdown button by accident on an 11.10 beta & couldn't find it in panel applets.

I used the logout option in the main menu as it brings up the same options list as the shutdown button usually at the other end of the panel.

Checking my shiny new 11.10 final, the logout button at the bottom of the main menu still provides the list...or has it disappeared from there too?

---

### Post by amjjawad on 2011-10-16
> **Big Lizard said:**
> I guess nobody knows. So much for Lubuntu 11.10.

You need to learn how to be patient ;)
Things are going crazily fast and I do have tons of personal issues here. I'm trying to help as much as possible but it's getting worse here, mate. Just give me some time and I'll get back to you.

Thanks for understanding.

FEEL FREE to PM with a link of your thread next time you do have a new problem whether here or on LXDE Forum, ok? ;)

That goes to ANYONE. YES, PM me your thread link [COLOR=Red]**if it's related to Lubuntu ONLY. **[/COLOR]Thanks!

---

### Post by mcconkeyb on 2011-10-17
I will just add that I have seen this problem too. So I will wait like all the others for a solution.

---

### Post by Mzee nyuki mpya on 2011-10-17
I have the same problem with Ubuntu 11.10 as you are having with Lubuntu. I'm sure it will be fixed before long, but meanwhile I'll describe how I got round it:

**[COLOR="Red"]Click on Dash home. Type "Shutdown" (without the quotation marks) in the search panel. The Shutdown App appears in a File icon. Click on this and a nice friendly program starts with the choice of Restart or Cancel or Shutdown.[/COLOR]**

This will be my method of choice until the problem is fixed.:P

Typing "sudo shutdown now" in the terminal also worked for me, but it was slower. 
Ctrl/Alt/Delete just restarts the computer, with no shutdown option.

---

### Post by amjjawad on 2011-10-17
Ok, finally got some time so there you go:

1- Open LXTerminal

2- Type this command (just copy and paste it there):


```
sudo leafpad /usr/share/applications/lubuntu-logout.desktop

```

3- Now, copy the content below and paste it in that file, double check, save and exit.

```
[Desktop Entry]
Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Type=Application
Comment=Shutdown or Reboot
Icon=system-shutdown-panel
Exec=lubuntu-logout
#NoDisplay=true
Categories=Settings;DesktopSettings
```

4- Right Click on LXPanel > Add/Remove Panel Items > Add > Application Launch Bar > Double Click on Application Launch Bar > Preferences > Select Shutdown from the list and Click "Add" > Close > Close

5- DONE.

---

### Post by amjjawad on 2011-10-17
> **Mzee nyuki mpya said:**
> I have the same problem with Ubuntu 11.10 as you are having with Lubuntu. I'm sure it will be fixed before long, but meanwhile I'll describe how I got round it:

**[COLOR="Red"]Click on Dash home. Type "Shutdown" (without the quotation marks) in the search panel. The Shutdown App appears in a File icon. Click on this and a nice friendly program starts with the choice of Restart or Cancel or Shutdown.[/COLOR]**

This will be my method of choice until the problem is fixed.:P

Typing "sudo shutdown now" in the terminal also worked for me, but it was slower. 
Ctrl/Alt/Delete just restarts the computer, with no shutdown option.

Hi,

Lubuntu/LXDE doesn't have "Dash" and "Unity" ;)

The command for shutdown is:

```
sudo shutdown -P now

```

---

### Post by amjjawad on 2011-10-17
I have updated the wiki page. Now, everyone can see that and no need to more threads :)

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

---

### Post by kalehrl on 2011-10-17
It is quite easy to restore your default panel with all the buttons.
Just type as normal user, not sudo:

```
 mv ~/.config/lxpanel/Lubuntu/panels/panel ~/
```

then restart panel:

```
lxpanelctl restart
```

---

### Post by amjjawad on 2011-10-17
> **kalehrl said:**
> It is quite easy to restore your default panel with all the buttons.
Just type as normal user, not sudo:

```
 mv ~/.config/lxpanel/Lubuntu/panels/panel ~/
```

then restart panel:

```
lxpanelctl restart
```

I have two LXPanels on my desktop, one on the top, one on the left. When I followed your way, I got this problem:

```
mv: cannot stat `/home/xxx/.config/lxpanel/Lubuntu/panels/panel': No such file or directory
```

and ... I don't have my main LXPanel now :)
Just the one on the left which is NOT the main LXPanel.

Any idea how to fix that?

---

### Post by kalehrl on 2011-10-17
I know for sure that it worked on 11.04.
I had the same problem as the poster with buttons missing after my fiddling with them and I restored the default panel with these commands.
Were you logged as root when you issued those commands?
You need to be just user because it doesn't work with root.
Maybe something changed in 11.10 but I don't think so.

---

### Post by amjjawad on 2011-10-17
> **kalehrl said:**
> I know for sure that it worked on 11.04.
I had the same problem as the poster with buttons missing after my fiddling with them and I restored the default panel with these commands.
Were you logged as root when you issued those commands?
You need to be just user because it doesn't work with root.
Maybe something changed in 11.10 but I don't think so.

Definitely I didn't run that command as root :)

When I checked: 

/home/xxx/.config/lxpanel/Lubuntu/panels

the old file is gone, obviously, and it's on my /home folder. I opened PCManFM as a root, copied the file and return it back to it's original place. Issued:
```
lxpanelctl restart

```

But that did NOT fix the issue.

IMHO, this method isn't safe for someone with two panels. Now, I have to waste some time to get back my panel back :D

---

### Post by kalehrl on 2011-10-17
I had just one panel and after all this, I got the default one which came with the lubuntu installation.
I'm sorry if I caused you problems.
I found these commands somewhere on this forum and they worked perfectly for me on 2 occasions.

---

### Post by amjjawad on 2011-10-17
> **kalehrl said:**
> I had just one panel and after all this, I got the default one which came with the lubuntu installation.
I'm sorry if I caused you problems.
I found these commands somewhere on this forum and they worked perfectly for me on 2 occasions.

Oh well, I had to remove the panel on the left and delete its config file, move the config file back to its original place, logged off didn't fix it so had to reboot, didn't fix it, had to type the previous two commands again and it's ok now but without my left panel that I wasted 30mins the other day to customize it.

I don't recommend that way at all :)

From Fresh NEW Test.

As an advice from a fellow Ubuntu Member, being here for almost two years now taught me that short and simple paths are not always recommended. Sometimes, you need to do it the long way to get a better result.

Please, don't be sorry at all. I do love making tests. This is how I learned more about Linux.

By the way, you are new here so Welcome to Ubutnu Forum :)

---

### Post by kalehrl on 2011-10-17
Thank you for your welcome :)
I thought you knew any user panel configurations will be lost after these commands.
That's why I wrote that it restores default panel.
I love lubuntu. I've been using it for a half year now, since 11.04 release.
It breathed a new life into my dell latitude d505 laptop with originally 256MB of ram.
Later I added additional 256 so now I have a whopping 512MBs :D
Much more than lubuntu needs. :)

---

### Post by amjjawad on 2011-10-17
> **kalehrl said:**
> Thank you for your welcome :)

Anytime :)

> I thought you knew any user panel configurations will be lost after these commands.
That's why I wrote that it restores default panel.

That is exactly why I don't recommend that way :D
If you know, don't assume others will ;)

But again, it's ok, as I mentioned, I do need to do these tests to learn more and help others to follow the right and easy way.

> I love lubuntu. I've been using it for a half year now, since 11.04 release.

Well, then guess I found a new friend who loves Lubuntu like me so Welcome to the club!

I'm Lubuntu addicted and loving it.

> It breathed a new life into my dell latitude d505 laptop with originally 256MB of ram.
Later I added additional 256 so now I have a whopping 512MBs :D
Much more than lubuntu needs. :)

Mint LXDE 9 breathed a new life into my very antique laptop. I know it wasn't Lubuntu but still LXDE :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2136&pictureid=7114[/IMG]

Oh, that laptop has only 64MB RAM and 366MHz P2.

---

### Post by musahossein on 2011-10-17
> **Big Lizard said:**
> I did two installs of Lubuntu 11.10. One computer has the Shutdow button on the panel. On the other computer it's missing and I can't find out how to restore it. (I tried a bunch of the panel applets, but it's not there...or did I miss it.)  How do I get that back?
---BTW, there is no "Shutdown" in the applet list.---

Thanks in advance for any help.
--------------------------------------------------------------
Edit
I guess nobody knows. So much for Lubuntu 11.10.

I installed ubuntu 11.10 by accident. Now, no shut down button, no systems button that lets me open a terminal. How can I get the shutdown button?

---

### Post by amjjawad on 2011-10-17
> **musahossein said:**
> I installed ubuntu 11.10 by accident. Now, no shut down button, no systems button that lets me open a terminal. How can I get the shutdown button?

So you don't have LXPanel? or it's just the Shutdown button?

---

### Post by Mzee nyuki mpya on 2011-10-24
> **amjjawad said:**
> Hi,

Lubuntu/LXDE doesn't have "Dash" and "Unity" ;)

The command for shutdown is:

```
sudo shutdown -P now

```
Thanks for your help, amjjawad, to an Ubuntu user in a lubuntu thread! I like LXDE and used Moon OS on an old laptop for a while. After reading your post, I came close to moving to Lubuntu. However, I waited another day - (after all, I've been using Ubuntu since 04.10!) I was puzzled because I seemed to be the only Ubuntu user with this particular problem. When I next re-booted, Ubuntu decided to do its periodic file system check, which is scheduled every 30 boots. After it had finished, the panel appeared, with the stop button - Ubuntu appeared to have automatically repaired itself! I suppose some system files had got themselves scrambled after this major upgrade (I'd opted to keep Gnome on 11.04). So I'll keep Ubuntu with Unity, which I'm getting used to now it's working properly. However, I'll watch Lubuntu with interest!
 BTW, is Lubuntu easy to customise - can it be installed with a bit of "eye candy"? After all, MoonOS with LXDE was beautiful, so it must be possible...
Best wishes to all Lubuntu users and thank you again.

---

### Post by amjjawad on 2011-10-24
> **Mzee nyuki mpya said:**
> Thanks for your help, amjjawad, to an Ubuntu user in a lubuntu thread! I like LXDE and used Moon OS on an old laptop for a while. After reading your post, I came close to moving to Lubuntu. However, I waited another day - (after all, I've been using Ubuntu since 04.10!) I was puzzled because I seemed to be the only Ubuntu user with this particular problem. When I next re-booted, Ubuntu decided to do its periodic file system check, which is scheduled every 30 boots. After it had finished, the panel appeared, with the stop button - Ubuntu appeared to have automatically repaired itself! I suppose some system files had got themselves scrambled after this major upgrade (I'd opted to keep Gnome on 11.04). So I'll keep Ubuntu with Unity, which I'm getting used to now it's working properly. However, I'll watch Lubuntu with interest!
 BTW, is Lubuntu easy to customise - can it be installed with a bit of "eye candy"? After all, MoonOS with LXDE was beautiful, so it must be possible...
Best wishes to all Lubuntu users and thank you again.

My story with Lubuntu and how I fell in love with it is a bit long so I think I'll skip that part for now but just for the record, Ubuntu 9.10 was my very first Linux OS that I ever used. I still consider myself new to the Linux World. I'm glad I have finally found what I need and looking for ... well, maybe not 100% because my ambition has no limits but so far so good. LXDE/Lubuntu simply meets most of my needs if not all. I'm kind of old fashion type of guy who can't offered the latest hardware and not even interested in that. I'm more into old machines. It's another story back in Oct and Nov 2010. Since that time, I started to love Lightweight Distributions. I was about to join SliTaz's Team but didn't. Was so much interested about antiX but didn't join as well. For some reason, I loved Lubuntu and started to be addicted to it and I finally joined a team.

Lubuntu, just like Ubuntu, in most cases, whatever works there will work on Lubuntu as well but sometimes, you need to edit or add some config stuff. Both share the same core but the DE is different of course.

While Lubuntu 11.10 was still under development, I had to test it. I installed Cairo-Dock and it worked without any issues. I read it some where that Docky needs some extra work-around to get it up and running. Even Compiz works on LXDE with some work-around.

My advice is: if you are happy with Ubuntu, stick with it but don't let that prevent you from having a look at Lubuntu. If you have an old machine, better to breath new life using Lubuntu than throw it away.

Thank you for your nice word and hope you'll try Lubuntu, even from Live-USB :)

---

### Post by Rex Bouwense on 2011-10-24
+1 Way to go amjjawad.

---

### Post by amjjawad on 2011-10-24
> **Rex Bouwense said:**
> +1 Way to go amjjawad.

You know me my friend, I couldn't resist :)

Love is a beautiful thing that you shouldn't keep for yourself only, you need to share it with everyone you may come across and the more time I use Lubuntu, the more I love it and the more I'll keep talking and sharing that love :)

Why am I so addicted to it? one way to find out: USE IT :)

---

### Post by volsurf on 2011-12-22
Changing the appearance theme from 'high contrast' to 'Ambiance' did the trick for me!

---

### Post by amjjawad on 2011-12-22
> **volsurf said:**
> Changing the appearance theme from 'high contrast' to 'Ambiance' did the trick for me!

Hello and Welcome to Ubuntu Forum and thanks for using Lubuntu :)

---

### Post by Stanwilliamsmusic on 2012-06-01
> **amjjawad said:**
> My story with Lubuntu and how I fell in love with it is a bit long so I think I'll skip that part for now but just for the record, Ubuntu 9.10 was my very first Linux OS that I ever used. I still consider myself new to the Linux World. I'm glad I have finally found what I need and looking for ... well, maybe not 100% because my ambition has no limits but so far so good. LXDE/Lubuntu simply meets most of my needs if not all. I'm kind of old fashion type of guy who can't offered the latest hardware and not even interested in that. I'm more into old machines. It's another story back in Oct and Nov 2010. Since that time, I started to love Lightweight Distributions. I was about to join SliTaz's Team but didn't. Was so much interested about antiX but didn't join as well. For some reason, I loved Lubuntu and started to be addicted to it and I finally joined a team.

Lubuntu, just like Ubuntu, in most cases, whatever works there will work on Lubuntu as well but sometimes, you need to edit or add some config stuff. Both share the same core but the DE is different of course.

While Lubuntu 11.10 was still under development, I had to test it. I installed Cairo-Dock and it worked without any issues. I read it some where that Docky needs some extra work-around to get it up and running. Even Compiz works on LXDE with some work-around.

My advice is: if you are happy with Ubuntu, stick with it but don't let that prevent you from having a look at Lubuntu. If you have an old machine, better to breath new life using Lubuntu than throw it away.

Thank you for your nice word and hope you'll try Lubuntu, even from Live-USB :)
I just wanted to say thanks for all the helpful posts [amjjawad]("http://ubuntuforums.org/member.php?u=941822") .

I have been using Ubuntu since 6.06 LTS and still have a couple of those original disks   from Canonical.
I have been using Lubuntu since 10.10 and Love it,  though still used regular Ubuntu till 11.10 on another box, but switched it over to Lubuntu recently. 
I have a Lot of fun customizing  the LXDE desktop , just seeing what all is possible and playing mostly, that is fun for me, I suppose I am odd that way.

I have 2 GB of RAM but Ubuntu 12.04 would not even run or just barely on  another amd64 box, so it flies with Lubuntu!
 This computer seems to have some stability issues, whereas the panel (bottom) will completely disappear at times and the shutdown button as well, but  I put a shutdown  link on the desktop, still other times the entire desktop will turn blue, wallpaper disappear, and all the icons on the desktop all but one that is,  and just today I realized that the one link to a file on the desktop that is on the desktop when that happens,  is on the root desktop!  I am actually seeing the root account desktop, (which I hardly ever log into so it took me a few times to really notice the one link I had on it was on the root desktop which has no wallpaper but isn't blue)
 but when it does that, though I am still my normal user account when that happens, (Not root , but it shows root desktop).
I am baffled, that is the strangest thing I have seen in all my years of using Ubuntu haha..
It only seems to do that when I am using nautilus (I  installed it) with root priviledges, I also have SpaceFM, and kept PCManFM, and also have  Krusader file managers installed , but it started happening   after I installed nautilus. 
I will fix that aforementioned problem,  I reckon, but at any rate I Love Lubuntu, especially compared to the latest Ubuntu's .
 I tried Precise, and  almost immediately formated over that partition , well after a couple days any way.
I have 5 or 6 other Linux distros on other boxes and partitions (Fedora 16, SuSe 12.1, Mint , Debian ,Puppy,  DSL, to name a few),  but I  seem end up using Lubuntu almost all the time.
All in all  Lubuntu is a Great distro!  - in my humble opinion anyway.
P.S. the forum will not let me edit my profile in any way, the User CP  I get

 "vBulletin Message :
**Stanwilliamsmusic**, you do not have permission to access this page. This could be due to one of several reasons:
  
[LIST=1]
[*]Your user account has less than 50 posts.
[*]Your user account may not have sufficient privileges to  access this page. Are you trying to edit someone else's post, access  administrative features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation
[*]
And  a lot of times I get that when I try to view someone else's posts on the forum when I am seeking answers.
It will not let me view them, I get that same messsage or similar, it says I have less than 50 post and do not have permission to view that post .I should have close to 50 posts by now, maybe not, but it shows like 6?  I know I should have more than that, surely, although I didn't join the forum for a few years after I started using Ubuntu. 
I still consider myself a Linux newbie, as there is a Lot to learn :)
[/LIST]

---

### Post by oldos2er on 2012-06-01
> **Stanwilliamsmusic said:**
>  you do not have permission to access this page. This could be due to one of several reasons: 

[http://ubuntuforums.org/showthread.php?t=1836816](http://ubuntuforums.org/showthread.php?t=1836816)

Questions about the forum should be posted to Forum Feedback & Help.

---

### Post by x3qt0r on 2012-09-08
plus 1 to amjjawad.
=)

---

### Post by inearlygaveup on 2012-10-15
Thanks amjjawad - I have been looking to solve this problem on my lubuntu 12.4 after accidentially deleting the icon.

Thanks a lot.

---

