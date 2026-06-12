---
title: "No such file or directory"
date: 2017-03-16
forum: New to Ubuntu
---

### Post by poisonfor3 on 2017-03-16
Trying to download Tor Browser and keep getting this:

```
No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

```

I did a lot of research and found a bunch of stuff that is not helping me because it is over my head.
I know nothing about line commands so when people say things like "do a cd" I have no clue what they are talking about.
Albeit I tried to do a cd~ and cd/ and a bunch of others but nothing helped.

Here are a bunch of sites that I looked into but are talking over my head and/or not being able to solve my problem:
[https://www.drupal.org/node/1849174](https://www.drupal.org/node/1849174)

[http://askubuntu.com/questions/13338...he-file-exists]("http://askubuntu.com/questions/133389/no-such-file-or-directory-but-the-file-exists")

[http://askubuntu.com/questions/55139...ubuntu-14-04-1]("http://askubuntu.com/questions/551395/no-such-file-or-directory-ubuntu-14-04-1")

[https://ubuntuforums.org/showthread.php?t=1131954](https://ubuntuforums.org/showthread.php?t=1131954)

[https://ubuntuforums.org/showthread.php?t=1090228](https://ubuntuforums.org/showthread.php?t=1090228)

[https://ubuntuforums.org/showthread.php?t=1692556](https://ubuntuforums.org/showthread.php?t=1692556)

[http://askubuntu.com/questions/48626...ing-a-tar-file]("http://askubuntu.com/questions/486264/cannot-open-no-such-file-or-directory-when-extracting-a-tar-file")

[https://superuser.com/questions/6911...e-or-directory]("https://superuser.com/questions/691131/tar-cannot-open-no-such-file-or-directory")

[http://www.linfo.org/cd.html](http://www.linfo.org/cd.html)

[https://en.wikipedia.org/wiki/Cd_(command)]("https://en.wikipedia.org/wiki/Cd_%28command%29")

I can unpack it myself I do not need a line command for that. 

then I try cd~ i guess that is my home directory
then cd to the name of it but nothing

Changing over to Xubuntu last, everything back into my computer now but Tor. I did what I call a "flush and fill". With new installs and just transferring over needed information like bookmarks.

Also tried to use the software manager to install it and it works to a point. It puts a nice little button (icon) in my main menu for me but when I click it the tor installer tried to download it and install it but I keep getting the same message after it downloads it:
```

SIGNATURE VERIFICATION FAILED!
You might be under attack, or there might just be a network problem. Click Start try the download again.
```

Any one know whats going on or help?

Thanks for reading and any help you can give,
-Annie

---

### Post by oldos2er on 2017-03-16
It would help to know the exact command you ran that resulted in "no such file or directory. " If the tar file is in your home folder you should be able to right-click on it to extract it.

---

### Post by poisonfor3 on 2017-03-16
Yes I can  extract it no problem. Yet I can not get it to install

I tried ...

```
tar -xvJf tor-browser-linux64-6.5.1_en-US.tar.xz

cd tor-browser_en-US
```

and many many other things. That I can not remember. 

if the cd command can not find it (in my home folder) then I do not see how any other commands will find it but I did try a bunch.

Been at this for 5 hours before I just gave up and came here. I do try very hard to do things without help not because I am bull headed but so many people ask silly questions that a simple goolgle search could fix. Albeit a lot of people seem to have the same problem no one seemed to have an "easy to understand" answer.

I am following the "Linux Instructions" directions listed here;

[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

here is a copy of it in full:
```
hot@hot-fsutb:~$ tar -xvJf tor-browser-linux64-6.5.1_en-US.tar.xz
tar (child): tor-browser-linux64-6.5.1_en-US.tar.xz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
hot@hot-fsutb:~$ 
```



so many many hours ago I did just like you said. I extracted the file and tried the next step:
```
hot@hot-fsutb:~$ tar -xvJf tor-browser-linux64-6.5.1_en-US.tar.xz
tar (child): tor-browser-linux64-6.5.1_en-US.tar.xz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
hot@hot-fsutb:~$ cd tor-browser_en-US
bash: cd: tor-browser_en-US: No such file or directory
hot@hot-fsutb:~$ 

```


After that I tried a bunch of other non-working stuff.

- thanks again for any help.

---

### Post by oldrocker99 on 2017-03-16
> **poisonfor3 said:**
> 
[HTML]SIGNATURE VERIFICATION FAILED!
You might be under attack, or there might just be a network problem. Click Start try the download again.[/HTML]


I installed it from a PPA, using the Ubuntu MATE Welcome Software tool. I got the same verification problem. After reading your post, I tried it again, and voila! it worked. It's up now. I had gotten the verification error every time before. You **might** try again.

---

### Post by #&amp;thj^% on 2017-03-16
It dose not install per-say but it is a Bundled Appliction..that launchs from inside the extracted .tar.xz. (**Hint>>right click and Extract Here**)
You should see A folder now named "tor-browser_en-US" inside there...you will see "TorBrowser Setup" (Screenshot inculded)
Make sure permissions are set to "Allow executing file as program".
Now your set..just double click the "TorBrowser Setup" and it should begin the connection.

---

### Post by lisati on 2017-03-16
@poisonfor3: Please use [noparse]```
 and 
```[/NOPARSE] tags to enclose quotes from terminal output, it helps preserve the formatting better than some of the other options available.

---

### Post by poisonfor3 on 2017-03-16
@[**[COLOR=#C61919][B]oldrocker99**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=565288")

I did try it again after a good nights sleep; just before I posted this and got the same message. I was using MATE but I am (as in only just last night) using xUbuntu.*   As such I do not have "Ubuntu MATE Welcome Software" I have "Gnome Software" (gnome-software %U). But I did (before all this Tor thing) download "Ubuntu Software Center", "App Grid" (kinda like this one best), "Software Boutique" (this may be the same as the "Ubuntu MATE Welcome Software" uses) and "Lubuntu Software Center". They all have stuff on them that the others do not. So I was about to go looking for, and install. "Ubuntu MATE Welcome Software" but was going to try the installers i have one last time. This time trying all of them. I did try the "Gnome Software" and "Ubuntu Software Center" but was going to try all of them this time. I started with "Lubuntu Software Center" it did not even have it, then tried "Software Boutique" and as you put it "voila! it worked." 

Albeit a work around that got my Tor Browser, it never did answer the reason I kept getting the errors when I follow the directions from the Tor website. 

I now have the folder in my home folder called ".tor-browser-en" with the program in it. I wanted this setup so I can copy my old folder from my backups from my old MATE profile (before the flush and fill) to the new ".tor-browser-en" folder in the new (Xfce Ubuntu) profile. After that I was able to open my Tor from my menu and it has all my old bookmarks and stuff as I liked it ( not to worry I did not change anything bad/wrong ) . I could have (and next time will) just export all my bookmarkers and reload them. Yet I like the idea of just having to save my home folder and I have everything I need is in there. I could not do this in Windows after Windows XP came out but that is a different topic. (Another off topic thing, does not seem to work with KDE stuff. I lost all my kMyMoney data, but that is a different topic too).

@[**[COLOR=#000000]1fallen[/COLOR]**]("https://ubuntuforums.org/member.php?u=2040855")                            

Yes I was able to get it to work by doing just as you say, long ago but I was wanting to get it installed like I had it before for the reason I talk about above (to transfer Tor folder information), if I knew how; I could have somehow just transferred the information by hand to the new "portable'' Tor Browser and made a link to it and put the link into my menu but I am not able to do that in Linux (yet) like I could with Windows. I also have Trails so I have a "portable'' Tor Browser in there if I needed a potable Tor Browser. 

One funny thing about what you said to do however. When I click on the link you show in the picture it worked but then the icon changed and the NAME of it changed too. It then would not work after that. Strange. If I deleted it and re-extracted it; it would work one more time and the icon and name would change again and not work . . . again. But if I went into the folder next to the icon and inside the folder I found "Tor Browser Setup" and clicked that then THAT would work. Kinda buggy. The NSA needs to fix their spy-bot it has in my computer so it works without affecting my performance. I know this because it is in the new wiki leaks that they mandate that all their spy-bots are not to effect performance of the OS. 

Or may just be a Xubuntu glitch. The world may never know because I got my Tor Broswer working (NSA spy-bot included) and that is all I wanted. 

Thanks all for your help.


A pic of before and after I clicked the Tor Browser icon thing.

---

### Post by #&amp;thj^% on 2017-03-18
Sorry for the delay in my reply...but the changing of the icon is the normal behavior, using the bundled .tar.gz package.
Just mentioning here... I usually grab the Icon from that folder>>after it has changed, and drop it to the launcher (Unity) or panel (Mate) or if you use a Dock manager, you could pin it on the Dock.
Hope this useful.
Kind regards

---

