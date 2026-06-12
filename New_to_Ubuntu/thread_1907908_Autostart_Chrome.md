---
title: "Autostart Chrome"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by nick roto on 2012-01-12
I have set up an old laptop with Lubuntu which now runs fast enough to be useful again (it was starting to struggle under Windows). I would like to leave it in a holiday property so that visitors can find useful information about the property and the area, or check their email, etc.
The system boots directly into Lubuntu without requiring a password but I want it to open with the property's website homepage displayed in Chrome. I have tried a couple of things I found in the forum, involving scripts (which I don't really understand yet, being new to Linux) but they haven't worked. Could somebody please show me what to do explicitly (i.e. assuming very little knowledge)? Thanks.

---

### Post by kc1di on 2012-01-12
hi nick roto,

this is one way you can do it I'm sure there are others. 

open up Chrome and make the page you want the home page.

Next go to pacman and navigate to the following file
/usr/share/applications

Find the Chrome file there and right click and copy.
now navigate to your home folder click on the tab that says view
select show hidden files (or something similar) you will find a folder labeled .config (it may be .conf) open that in that folder will be a folder labeled autostart open that and past the file you copied from applications.
close the file manager and restart chrome should start upon login.
Hope this helps,
Dave

---

### Post by nick roto on 2012-01-12
Thanks. Unfortunately it's not clear to me what "go to" pacman means. Even Googling pacman + Ubuntu didn't help: is it a game or a system tool? According to Synaptic it's a game.

---

### Post by kellemes on 2012-01-12
> **nick roto said:**
> Thanks. Unfortunately it's not clear to me what "go to" pacman means. Even Googling pacman + Ubuntu didn't help: is it a game or a system tool? According to Synaptic it's a game.

He surely means "pcmanfm", the default filemanager shipped with Lubuntu.

---

### Post by Lupajz on 2012-01-12
> **nick roto said:**
> 

You mean like starting up Lubuntu and auto open chrome with lets say homepage of your web site ? 
System -> Preferences -> Startup apps ? and make new google-chrome

Or am I getting this wrong ? My english isn't that good :P

---

### Post by kc1di on 2012-01-12
> **nick roto said:**
> Thanks. Unfortunately it's not clear to me what "go to" pacman means. Even Googling pacman + Ubuntu didn't help: is it a game or a system tool? According to Synaptic it's a game.

Sorry pacman is the filemanager.

---

### Post by nick roto on 2012-01-12
OK Kellemes, how do I "go to" pcmanfm please? I can copy instructions  but don't yet understand what I'm doing in script language (I've only  just loaded Lubuntu).

Yes Lupajz, that's what I mean. However, the closest I can find to your suggestion is System -> Preferences -> Desktop Session Settings. This shows a tab, "Applications automatically started after entering desktop", with a list of applications, some enabled (ticked). The list doesn't include Chrome (if could add it, that would be great). If I open the Advanced tab it presents me with Window Manager: openbox-lxde and the "WARNING: Do NOT touch this unless you know exactly what you are doing." - which, of course, I don't.

---

### Post by nick roto on 2012-01-12
Thanks kc1di. I may be VERY stupid and I'm certainly very new to LUBUNTU (or any version of Unix) but the only "pacman" I can see listed anywhere on my system is a game. And I don't know the instruction to "go to" it either.
I'm sure this is EASY, but it's very frustrating.

I did find Start -> Accessories ->  File Manager -> Applications ->Preferences -> Openbox  -- no dire warnings this time but no Autostart option either.

---

### Post by kc1di on 2012-01-12
ok the Pacmanfm can be accessed by clicking on the folder icon with the pointer next to the start icon in the panel.  or you can go to start >accessories >filemanager when you get to the .config file you will have to create a new folder name autostart (didn't know it was not there by default.) 
You can do that by going to the file tab scroll down  to Create new then folder name it autostart then follow the rest of the instructions in my first post.
good luck

---

### Post by nick roto on 2012-01-12
Thanks. I did eventually discover what you meant in your first post and  using the folder icon was able to navigate around the folders and files  as you said. However right-click in Applications didn't offer Copy (only  Open and Properties) so I used Edit|Copy from the File Manager menu.  When I tried to Edit|Paste into Autostart (which did exist) I got a  message saying "The file operation is finished, but there are some  errors.", "Copying files: chromium-browser.desktop", "To:/home/nick/.config/autostart", "Some errors occurred: The specified location is not supported".

---

### Post by kc1di on 2012-01-12
> **nick roto said:**
>  However right-click in Applications didn't offer Copy (only  Open and Properties) so I used Edit|Copy from the File Manager menu.  When I tried to Edit|Paste into Autostart (which did exist) I got a  message saying "The file operation is finished, but there are some  errors.", "Copying files: chromium-browser.desktop", "To:/home/nick/.config/autostart", "Some errors occurred: The specified location is not supported".

Now I'm stumped because the right click works fine in my installation.  Maybe someone else will have a suggestions.
Sorry,
Dave

---

### Post by nick roto on 2012-01-12
> **kc1di said:**
> Now I'm stumped because the right click works fine in my installation.  Maybe someone else will have a suggestions.
Sorry,
Dave
"nick" is the main user but is there a problem with authority. The account type is Custom, should I change it Administrator? I would need to change it back later so that visitors don't have too much privilege.

---

### Post by kc1di on 2012-01-12
Yes change it to Admin and see if that will work for you, Don't for get to change it back though.

---

### Post by Catharsis on 2012-01-12
Are you trying to autostart Chromium or Google Chrome? Chromium is the open-source version that comes with Lubuntu and has a blue icon; Google Chrome is the one you have to download from Google and has a red, green, and yellow icon.

Open up a terminal: Main Menu -> Accessories -> LXTerminal

For Chromium, run:
```
cp /usr/share/applications/chromium-browser.desktop ~/.config/autostart
```
For Google Chrome, run:
```
cp /usr/share/applications/google-chrome.desktop ~/.config/autostart
```
Copy & Paste the commands to avoid mistakes.

---

### Post by nick roto on 2012-01-12
Yippee, done it! Thanks Catharsis (yes, I wanted Chromium).
Dave, I think we might have been there. In principle I prefer your method since I don't (yet?) speak "script" so have to take all instructions totally on trust. But the instructions were explicit and simple enough to copy.
Thanks for the help (both). I hope to become a more fluent systems user before too long. We seem to need Script more often than a Windows user needs DOS/Command lines but maybe that stops Lubuntu (and Ubuntu?) becoming too bloated.
Nick

---

### Post by dcsoldschool53 on 2012-01-12
I really do not have any knowledge to past on to you about Lubuntu, but I do have a list of websites that may help you in the long run with your Operating System.

Lubuntu documentation FAQ workaround:
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Workarounds)

Lubuntu documentation FAQ guide
[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides)

Lubuntu one stop thread
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by kc1di on 2012-01-12
> **nick roto said:**
>  I hope to become a more fluent systems user before too long. We seem to need Script more often than a Windows user needs DOS/Command lines but maybe that stops Lubuntu (and Ubuntu?) becoming too bloated.
Nick

Just keep at it it will come to you quickly. and Linux is a very good system once you grasp the in's and out's of it. Enjoy,
Dave :)

---

### Post by Catharsis on 2012-01-13
Aye, credit to Dave for the fix. I just figured it was a bug in PCManFM that was causing the error.

And Lubuntu doesn't really need command line skills; it's just usually simpler and easier to do things through the terminal (i.e. in this case all you had to do was enter one command).

---

### Post by nick roto on 2012-01-13
My immediate requirement to set up an old laptop as an electronic guide for visitors to my holiday property, using Lubuntu, is now complete.
I had a quick skim through the helpful links you provided dcsoldschool, they look a useful bunch. I have a few more problems to crack with Ubuntu which I've installed alongside Windows on my main desktop PC (getting extra video codecs and also Truecrypt to install properly) and will try to follow the seemingly arcane instructions that didn't work for me.
 Thanks again everyone.

---

