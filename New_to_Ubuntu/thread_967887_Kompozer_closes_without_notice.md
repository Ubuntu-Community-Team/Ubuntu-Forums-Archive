---
title: "Kompozer closes without notice"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by FreewheelinFrank on 2008-11-02
I'm trying to use Kompozer but it closes without notice frequently. How can I a) track down what's wrong and b) report the bug?

---

### Post by goinglinux on 2008-11-02
FreewheelinFrank,

Where you report the problem depends on whether you think it's a Kompozer problem, an Ubuntu problem, a Gnome problem, etc. I'd start with the Kompozer site, [http://www.kompozer.net]("http://www.kompozer.net"). There's a link on that main page for reporting bugs.

But be as specific as you can about what the problem is. For example, I have a problem with Kompozer as well. (That's what got me to read your post.) My problem is this:

Kompozer version 0.7.10
It worked flawlessly under Ubuntu and Kubuntu 8.04 and earlier. Recently I switched to Ubunutu 8.10. (Gnome 2.24.1) Now I have this problem.

Kompozer closes (crashes) when I use the mouse to select "Recent Pages" from the "File" menu. As soon as the mouse touches the "Recent Pages" selection. None of the other menu selections cause this to occur. The program does not crash if I use the key combination Alt+F to select the "File" menu, then Alt+R to select the "Recent Pages" menu. 

I also installed the kubuntu-desktop packages from the package repositories and under KDE 4.1, Kompozer behaves the same way.

---

### Post by FreewheelinFrank on 2008-11-03
Thanks for your reply!

> Kompozer version 0.7.10
It worked flawlessly under Ubuntu and Kubuntu 8.04 and earlier. Recently I switched to Ubunutu 8.10. (Gnome 2.24.1) Now I have this problem.

Kompozer closes (crashes) when I use the mouse to select "Recent Pages" from the "File" menu. As soon as the mouse touches the "Recent Pages" selection. None of the other menu selections cause this to occur. The program does not crash if I use the key combination Alt+F to select the "File" menu, then Alt+R to select the "Recent Pages" menu.

That's exactly the problem I have! Recent Pages is guaranteed to see the program close without notice (although it's done so at other key/mouse strokes too.)

> Where you report the problem depends on whether you think it's a Kompozer problem, an Ubuntu problem, a Gnome problem, etc.

Indeed, but that's part of the problem: how do I know why it's closing? Is there some sort of log that might tell me?

I've filed a bug report at Kompozer. Perhaps you could add a comment saying that you have exactly the same problem?

[http://sourceforge.net/tracker/index.php?func=detail&aid=2216875&group_id=170132&atid=853122](http://sourceforge.net/tracker/index.php?func=detail&aid=2216875&group_id=170132&atid=853122)

---

### Post by Pisolo on 2008-11-03
HI all!
I've go the same problem here! No clue about a possible Ubuntu or Kompozer problem.
The Kompozer version is 0.7.10 (20080314) and crashes if I try to use either the app main menu bar or the context menu (the one invoked right clicking on the objects).

---

### Post by uarale on 2008-11-03
KompoZer shutdown immediately everytime I move the mouse over menus that have multiple choices from them.

When I open KompoZer from terminal, i see the error: "Segmentation fault"

Hope the bug fixed soon, cause KompoZer is the only WYSIWYG html editor I use in Ubuntu everyday.

---

### Post by quercusrobur on 2008-11-03
Its happening to me as well and I too rely on Kompozer for keeping various websites up to date...

---

### Post by AllanPoe on 2008-11-03
> **uarale said:**
> KompoZer shutdown immediately everytime I move the mouse over menus that have multiple choices from them.



Same here.

---

### Post by FreewheelinFrank on 2008-11-03
>  Re: Kompozer closes without notice
KompoZer shutdown immediately everytime I move the mouse over menus that have multiple choices from them.

When I open KompoZer from terminal, i see the error: "Segmentation fault"

Hope the bug fixed soon, cause KompoZer is the only WYSIWYG html editor I use in Ubuntu everyday

Nice one! I remember something about starting apps in a Terminal to see error reports now.

Perhaps you could post what you've noticed about menus with multiple choices- and the "Segmentation fault" error message in a comment at the bug report?

[http://sourceforge.net/tracker/index.php?func=detail&aid=2216875&group_id=170132&atid=853122](http://sourceforge.net/tracker/index.php?func=detail&aid=2216875&group_id=170132&atid=853122)

---

### Post by quercusrobur on 2008-11-03
It would be good if the bug with Kompozer could be fixed - in the meantime however I just installed Seamonkey Composer which at first glance looks very similar to Kompozer, so seems to be a good alternative for the time being.

Does Firefox have an equivalent wysiwyg html editor as an add-on? I had a look but couldn't find anything... 

I also tried Amaya, but couldn't really get along with it - it also caused my laptop to freeze!

---

### Post by goinglinux on 2008-11-03
> **quercusrobur said:**
> [I]n the meantime however I just installed Seamonkey Composer which at first glance looks very similar to Kompozer, so seems to be a good alternative for the time being.

Does Firefox have an equivalent wysiwyg html editor as an add-on? I had a look but couldn't find anything... 

I also tried Amaya, but couldn't really get along with it - it also caused my laptop to freeze!

I think there are many of us looking for alternatives at this point. Now, though, I'm thinking this is an Ubuntu issue since the version of Kompozer hasn't changed, just the version of Ubuntu. If so, it's too bad Kompozer is feeling the brunt of this issue. If not, I notice quite a few bugs and comments on the issue at their site.

For me, Seamonkey is missing critical CSS tools, so I can't use it. Firefox doesn't have anything of its own. Amaya crashes in similar ways to Kompozer on my machine. So far, the only work-around I have found is to use Kompozer under CrossOver, or to use my 7.10 machine that I (thankfully) haven't upgraded yet.

---

### Post by crjackson on 2008-11-10
The solution for me was dumping Intrepid and going back to Hardy. There were a couple of deal-breakers for me under Intrepid and this was one of them.

---

### Post by crjackson on 2008-11-10
As a test only you might try running kompozer from the terminal using sudo. I'm at work right now and can't test this or I would. If that works, it would seem to indicate POSSIBLY a permissions issue. If that is the case, you may be able to find the offending folder and change the permissions to fix this.

I'll check it out later this week and see if it works.

---

### Post by waffen on 2008-11-12
Not working with sudo kompozer command, crash with the same error

---

### Post by waffen on 2008-11-12
Workaround: I have installed Wine for another App then its not run in 64bits, Kompozer for Win.. run fine!

---

### Post by houstonbofh on 2008-11-13
It is bugged.  Any submenus using the mouse will crash it. [https://bugs.launchpad.net/bugs/263441](https://bugs.launchpad.net/bugs/263441)  You can work around by using the keyboard to navigate submenus.  Strangely enough I have to use the mouse for cut and paste, however. :(

---

### Post by crjackson on 2008-11-13
> **waffen said:**
> Not working with sudo kompozer command, crash with the same error

Was worth a try. I found another therad where someone said it worked.

I finally tested it when I got home and it didn't work for me either.

---

### Post by crjackson on 2008-11-13
> **waffen said:**
> Workaround: I have installed Wine for another App then its not run in 64bits, Kompozer for Win.. run fine!

It figures that the Win version is good and the Linux version is borked. I hate that! For now I'm sticking with Hardy on my main system so that I can use Kompozer. It's sad... I have to keep windows around for a couple of apps., now I have to keep older versions of linux around for the same reason.

---

### Post by waffen on 2008-11-13
> **crjackson said:**
> It figures that the Win version is good and the Linux version is borked. I hate that! For now I'm sticking with Hardy on my main system so that I can use Kompozer. It's sad... I have to keep windows around for a couple of apps., now I have to keep older versions of linux around for the same reason.

](*,) yes! I have Windoze inside VirtualBox only for testing my App... Intrepid is the worse Ubuntu then I installed from the beginning... before I never need to put a bug report, today I have 4! :confused:

---

### Post by germmare on 2008-11-14
Normal or in terminal as root or user kompozer and quanta crash with : segmentation fault. And all since -Intrepid-

---

### Post by crjackson on 2008-11-14
> **germmare said:**
> Normal or in terminal as root or user kompozer and quanta crash with : segmentation fault. And all since -Intrepid-

That's why my workhorse remains at Hardy 8.04.1

---

### Post by germmare on 2008-11-15
In terminal as root or as normal user:
Kompozer crash immediately when open in (X,K)- Ubuntu 8.10 for eg. a table
Fault: Segmentation fault.

---

### Post by philinux on 2008-11-16
This is a pain I was just going to have a beginners go at this.

Is there an alternative, easy app, in the repos or elsewhere till kompozer gets fixed.

---

### Post by waffen on 2008-11-16
> **philinux said:**
> This is a pain I was just going to have a beginners go at this.

Is there an alternative, easy app, in the repos or elsewhere till kompozer gets fixed.

I use Kompozer inside Wine... in other site I read then Quanta crahs in the same way....

---

### Post by Wolfhere on 2008-11-19
sigh....it does. I am recent to Ubuntu. I like it because I am not tied to Windows anymore (or so I thought). I have Vista with Dreamweaver (which I have paid plenty for), as Guest...I am trying to justify getting rid of Windows. From what I see of Kompozer, it would be a good replacement for Dreamweaver. Alas...I installed Intrepid. Neither Kompozer or Quanta Plus works in Ubuntu. 
If I have to use wine to use Kompozer, I might as well stay with Windows (Guest VM) until Kompozer...or rather in this case..Intrepid Ibex is fixed. Someone made a valid point. If the version of Kompozer has not changed, just the OS of Ubuntu..and both HTML editors worked before...we have another bug in Ibex.
And by the way, I cannot open a file on my USB drive from either HTML editor. I had to copy locally to even open the files.

---

### Post by PierreDeKat on 2008-11-19
Just an FYI, I'm using the Seamonkey suite, which includes Composer (with a C instead of a K, so not built around KDE), and it doesn't seem to have the same bug that the KDE version has. 

It's definitely not crashed on me, anyway. And I can open "Recent Pages" without a hitch.

I started off, back in the days, with the Netscape suite, and followed it through the Mozilla suite phase, and now I'm using the Seamonkey suite, the closest thing to a descendant of Netscape, by my reckoning.

Never understood why the folks at Mozilla wanted to break the thing up into Firefox, Thunderbird and all that mess, anyway.

So many people have Firefox and Thunderbird installed, and then they're still sitting around thinking: dang, if only I had a program like Frontpage or Dreamweaver to maintain a website...

Well, they can thank the good folks at Mozilla for that puzzlement.

And you know what the funny thing is?

The whole idea about splitting up Netscape/Mozilla was to make the different modules load faster. And then they quickly proceeded to bloat each module up to the point where they take twice as long to load as the suite.

Seriously.

---

### Post by PierreDeKat on 2008-11-20
For the uninitiated, just some quick miscellaneous info about Seamonkey.

Seamonkey
[http://www.seamonkey-project.org/](http://www.seamonkey-project.org/)
(You can download Seamonkey for various operating systems there, but the easiest way, in this context, is to get Seamonkey from the Ubuntu repos.)

Once you get the Seamonkey suite installed, you can launch each component individually with:

Seamonkey Browser:
```
seamonkey
```

Seamonkey Mail and News:
```
seamonkey -mail
```

Seamonkey Composer
```
seamonkey -edit
```

Note: each component generally uses comparable or less memory than its Firefox/Thunderbird equivalent.

There are a lot of other ways to launch the individual components, things like "seamonkey -profilemanager", "seamonkey -p yourusername" for launching specific profiles, etc., but I won't go into them all.

Seamonkey has several of the same plugins that Firefox/Thunderbird have, but you generally want to make sure that you're installing the Seamonkey version.

To play Flash in Seamonkey, flashplugin-nonfree out of the Ubuntu repos works great, though you might have to temporarily uninstall and reinstall flashplugin-nonfree, just to make sure that a plugin gets created in the appropriate profile folder.

But for Flashblock, I've been using version 1.3.9, available here:
[http://downloads.mozdev.org/flashblock/](http://downloads.mozdev.org/flashblock/)

Some of my favorite Seamonkey themes, like "iCandy Junior" and "Rain", are here:
[http://www.spuler.us/](http://www.spuler.us/)

But there are lots of others available, as well.

It might be possible to share profiles with Firefox/Thunderbird, but it's probably best to create new profiles. Maybe import an old profile, but name it something different in Seamonkey.

Let's see here, what else ... oh yeah, Seamonkey's "Preferences" are a lot like KDE-style preferences, in that you have options for everything but the kitchen sink. Whereas, like Firefox, the "Preferences" are like the Gnome version, where you only have a few of the most desired options available.

So you might have to spend a little extra time figuring out how you want to set things up. For Composer, everything's pretty straightforward, but if you want to adjust the size of your internet cache for Seamonkey Browser, it'll take you a little time to sort through the Preferences to find that particular setting.

What else ... oh yeah, one more thing, since we're focusing on Seamonkey Composer. Your HTML *will* validate. Even if you're coding manually and, like, you forget a closing tag, Composer will add it for you.

I don't think I've ever used Composer and had my HTML fail a validation test.

Anywho, that's just some miscellaneous stuff off the top of my head. But try it. And if you don't like it, uninstall it. No biggie.

---

### Post by alphacrucis2 on 2008-11-28
> **Wolfhere said:**
> sigh....it does. I am recent to Ubuntu. I like it because I am not tied to Windows anymore (or so I thought). I have Vista with Dreamweaver (which I have paid plenty for), as Guest...I am trying to justify getting rid of Windows. From what I see of Kompozer, it would be a good replacement for Dreamweaver. Alas...I installed Intrepid. Neither Kompozer or Quanta Plus works in Ubuntu. 
If I have to use wine to use Kompozer, I might as well stay with Windows (Guest VM) until Kompozer...or rather in this case..Intrepid Ibex is fixed. Someone made a valid point. If the version of Kompozer has not changed, just the OS of Ubuntu..and both HTML editors worked before...we have another bug in Ibex.
And by the way, I cannot open a file on my USB drive from either HTML editor. I had to copy locally to even open the files.

There is a 0.8 version of Kompozer due out soon but I gather that it will be the last as it appears that is will be superceded by a new project called BlueGriffon. Some info about Kompozer 0.8 has been posted on the Geckozone forums. It's all in French. If you can't read that then here is a google translate of the tread:

[Thread about Kompozer on Geckozone forum]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.geckozone.org%2Fforum%2Fviewtopic.php%3Ft%3D70879+&hl=en&ie=UTF-8&sl=fr&tl=en")


[BlueGriffon]("http://www.bluegriffon.org/")

---

### Post by houstonbofh on 2008-12-01
There is a very early port of Komposer with 1.8 geko available.  He posted a link in the bug on launchpad.

[QUOTE=kaze@kompozer.net]I've done ~50% of the job (i.e. porting KompoZer to Gecko 1.8.1).

You can grab pre-alpha builds in this directory: [http://kompozer.net/zip/](http://kompozer.net/zip/) (i.e. the 'kompozer-YYYYMMDD.tar.gz files).
Some features haven't been re-implemented yet (e.g. source tab, templates, spell checker).

Please don't report any bug on these snapshots yet, *except* if you find
a way to crash KompoZer with these snapshots. KompoZer's test team
couldn't crash these snapshots so far, so I believe the upcoming version
should be pretty stable.

I'm doing my best to release a public version before the end of this year.
Tony > is there a procedure to replace KompoZer 0.7.10 with KompoZer 0.8 in Intrepid?

-- kompozer crashes in intrepid when opening the recent files menu [https://bugs.launchpad.net/bugs/263441](https://bugs.launchpad.net/bugs/263441) You received this bug notification because you are a direct subscriber of the bug. [/QUOTE]

So all is not yet lost. :D

---

### Post by SteveDee on 2008-12-03
I found that Kompozer crashes under Intrepid when using the mouse for anything.

But amazingly I can edit pages without any problems if I don't touch the mouse, and do everything just using the keyboard! (you get used to it quite quickly)

---

### Post by sippligood on 2008-12-10
FIX: You just have not to use Synaptic to get KompoZer. Instead get the latest release from the kompozer-website
[http://kompozer.net/zip/](http://kompozer.net/zip/)
and download, unpack and start it. No install or compilation needed.
Check here:
[http://nyuviu.wordpress.com/2008/12/...der-usb-stick/](http://nyuviu.wordpress.com/2008/12/...der-usb-stick/) (in German only but with pics)

or follow Bruce:
[https://bugs.launchpad.net/ubuntu/+s...41/comments/40](https://bugs.launchpad.net/ubuntu/+s...41/comments/40)

No crashing anymore . You may even use it from usb-stick.

Regards Sippligood

---

### Post by philinux on 2008-12-10
It does work indeed. Nice one.

---

### Post by SteveDee on 2008-12-11
Yes, it seems to have solved my problems as well.

To point your menu link to the new Kompozer location:-
 - Select System > Preferences > Main Menu 
 - Applications > Internet > Kompozer > Properties > Browse

Now select the new file location, e.g. /home/steve/kompozer/kompozer in the Command field.

---

### Post by skywatcher on 2009-01-04
OOPS! PLEASE IGNORE! I just saw the fix -- it's late and I must be getting tired ... :(

Yes, the list of concerned Kompozer users is certainly growing.  As goinglinux pointed out, the version of Kompozer hasn't changed -- Ubuntu versions changed.

But having said that, I have some experience of Kompozer being quirky on Windows Vista, which I used until about two months ago when I installed Intrepid. On a few occasions Kompozer would close without warning on Vista, too, but not frequently enough to cause concern.

---

### Post by skywatcher on 2009-01-05
Uhh, well, back again.

The fix doesn't work for me.  I did as Sippligood suggested: download and unpack the tar.gz, then run kompozer directly. Now it doesn't close without warning anymore.  Instead, the program opens OK, but does nothing -- I cannot load files, cannot insert images, etc.  I also notice that the tips window is missing at start-up.

Any ideas, anyone?

---

### Post by SteveDee on 2009-01-05
> **skywatcher said:**
> Uhh, well, back again.

The fix doesn't work for me.  I did as Sippligood suggested: download and unpack the tar.gz, then run kompozer directly. Now it doesn't close without warning anymore.  Instead, the program opens OK, but does nothing -- I cannot load files, cannot insert images, etc.  I also notice that the tips window is missing at start-up.

Any ideas, anyone?

As the Kompozer files only need un-zipping, could it simply be a corrupted file?

I've just copied my Kompozer folder to my memory stick and still runs OK, so the location is none too critical.

The other possibility is that there is a problem with the latest files. The version I downloaded was the file dated 20081205, so maybe you should try that one.

---

### Post by skywatcher on 2009-01-06
Thanks, SteveDee

I downloaded 20081205 as you suggested, and now it does work, sort of.

I still have problems, though: when I insert images, they don't show, and the tab that allows me to view and edit the html code is missing.

Guess I'll have to resort to SeaMonkey, after all.

Thanks again, all, for your help.

---

### Post by jrusso2 on 2009-01-06
> **FreewheelinFrank said:**
> I'm trying to use Kompozer but it closes without notice frequently. How can I a) track down what's wrong and b) report the bug?

Strange that NVU used to do this too and Kompozer is built on NVU.

---

### Post by SteveDee on 2009-01-06
> **skywatcher said:**
> Thanks, SteveDee

I downloaded 20081205 as you suggested, and now it does work, sort of.

I still have problems, though: when I insert images, they don't show, and the tab that allows me to view and edit the html code is missing.

Guess I'll have to resort to SeaMonkey, after all.

Thanks again, all, for your help.

This very odd. I have now downloaded the 20081223 version and this also works fine. Selecting the un-zipped Kompozer folder I see it contains 445 items totalling 32.7MB (but yours will only match this if you have the same version).

If you've got a CD copy of Intrepid, it may be worth booting from that, then trying Kompozer.

---

### Post by skywatcher on 2009-01-08
> This very odd. I have now downloaded the 20081223 version and this also works fine. Selecting the un-zipped Kompozer folder I see it contains 445 items totalling 32.7MB (but yours will only match this if you have the same version).

Very odd, indeed. I downloaded the 20081223 version again, without luck. I cannot open files; the html code tab is missing; etc.

The un-zipped folder on my computer is also 32.7MB, it contains 423 files and 23 sub-folders.

Weird! I give up ... what's the term people use on these forums? :(

---

### Post by cozmicharlie on 2009-01-08
I'm a little late coming into this thread but I have been tracking it for some time now.  I have been trying to use Kompozer (really a wonderful app) and I have the same problem as everyone else - crashing when I try almost anything.  Searching around the bug reports, this is apparently due to incompatibility with the new Gecko 1.8 in Intrepid (it will work in 8.04).  The following was posted so if anyone can help please do so.

[http://sourceforge.net/tracker/index.php?func=detail&aid=2339056&group_id=170132&atid=853122](http://sourceforge.net/tracker/index.php?func=detail&aid=2339056&group_id=170132&atid=853122)
> [I]KompoZer crashes with GTK 2.14   	 Private: (?)
No
On recent GNU/Linux distros using GTK 2.14, KompoZer crashes whenever the
user selects a sub-menu with the mouse.
Everything is OK when accessing sub-menus with the keyboard. This might be
a workaround for the very short term.

I'm rebuilding KompoZer on a newer Gecko core. This will solve the
problem.
My first builds work fine (much more stable than KompoZer 0.7.10 on GTK
2.12), I'll put the new code on the SVN as soon as possible.
However, there are quite a lot of features that have to be re-implemented.

This bug is #1 on my list. I'm working on it.
If anybody can take the time see what has changed between Gecko 1.7 and 1.8
in the menu/popup widgets to submit a patch for recent Linux distros, that
would be very appreciated.[/I]

Going to the latest tarball did not help me in intrepid.  The only way I could get it to work was by running Kompozer in wine.  

Hope this helps.

---

### Post by oygle on 2009-01-13
I found out this problem only a few days ago. Searched around and although tht bug has not been fixed, I was able to try a few tips and use Kompozer, without it closing.

1. It can open files okay, as long as you use the menu with the keyboard.
2. You can use the mouse to 'position' in a cell, table, row, column, or any other part of the html document.
3. BUT, don't use the mouse on the menu, and don't left or right click the mouse.

So, how can one 'navigate' then ?  Just use the keyboard to navigate the menu. For example to add a row

Alt - B - I - R

use your keyboard left and right arrows to navigate some of those menu options.

HTH

Oygle

---

### Post by clw3388 on 2009-01-19
:popcorn:
A bit late on my comment as well but what the heck..
I use a handfull of html editors.
kompozer
amaya
bluefish
quanta..
They all (except bluefish) crash under 8.10. ubuntu broke em.. worked fine in 8.04.. broke in both 8.10 x64 and i386.... clean install and upgrade... BROKE I SAY, BROKE!!

---

### Post by jonpon on 2009-03-03
I've been having the same problem.It started last week. up until then NVU worked fine. Then suddenly it Crashed as I tried to edit in code.
I tried deleting the .nvu file in my HOME File as it my have been corrupted.That didn't work. so I deinstalled. I wanted to Reinstall but it doesn't seem to exist anymore as NVU but as Kompozer so I installed Kompozer.
Looks identical to NVU and I have the exact same problem.
I tried
```
cd ~
sudo rm -r .kompozer
```
But to no avail. 
Funny thing is it works fine if I log on as ROOT!!!

Could this an issue with an update I may have done recently?

---

### Post by doogiekd on 2009-03-28
Same problem here with Kompozer crashing. Not good - since I'm in the middle of building a community website for a church. There must be a simple solution to this since using without the mouse works, as well as using as root. (Terminal command use "gksudo kompozer")

Not really a good solution - the best web building program that has been in use for years is no longer working properly.

---

### Post by 6foot3 on 2009-04-29
Same problem here (version 0.7.10 (20090420) on ubuntu 9.04). Also tried running from terminal as root using sudo and got the "Segmentation fault". Running from the terminal as a normal user produces the same result. Invoking using gksudo causes the "Recent Pages" menu item to be greyed so, no crashes.

I had just done a weird thing after installing 9.04 on top of 8.10 (no  format). I also wanted to use a new user name so I launched nautilus using sudo and moved all the files from the old username's home folder to my new username's home folder. Somewhere in my manuevers I selected all the files in a folder and ended up opening all of them as root. Since this was the first time Openoffice 3.0 was running, it seems to have created a settings folders with root as the owner.

The result was that Openoffice could not access the settings file and crashed with the following message "The application cannot be started. The user interface language cannot be determined." I fixed it by using chown to change the ownwership of the hidden openoffice.org folder, it's subfolders and files from root to my new username. I get the feeling that similarly, this might have something to with ownership of a file or folder but that's just my WAG.

Alan

---

### Post by alphacrucis2 on 2009-04-30
> **doogiekd said:**
> Same problem here with Kompozer crashing. Not good - since I'm in the middle of building a community website for a church. There must be a simple solution to this since using without the mouse works, as well as using as root. (Terminal command use "gksudo kompozer")

Not really a good solution - the best web building program that has been in use for years is no longer working properly.

kompozer 0.7.10 is not compatible with gtk 2.14. It is dead in the water. The kompozer dev aka Kazé is aware of the problem and is in the process of working on a new version of kompozer 0.8. He has released an alpha2 version for testing which is available here:

[http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2]("http://kazhack.org/?post/2009/04/02/KompoZer-0.8a2")

I don't think a deb package is available yet so you would have to compile it.

---

### Post by mistypotato on 2009-05-10
What's worse....

They decided to remove the preview feature that was so terrific in the existing versions.  Improvement :confused:

---

### Post by mistypotato on 2009-05-11
Another...more serious issue.....

Kompozer 8 (available form the Kompozer site), has a nasty bug in it that will arbitrarily change the code in certain web pages rendering the entire page useless.  I can find no rhyme or reason to it.  But it destroys the page.

Without a backup, you can lose a great deal of work so if you're going to try the Beta 8 version, I STRONGLY advize backups before you even load the pages into Kompozer.

I had this happen before but I thought it was a fluke but I downloaded a fresh copy yesterday and 3 months later, it's doing it again.

It may happen only when you work on non-standard web pages such as .cfm pages etc.   Not certain on that.

I just wish we could have a working Kompozer like it was before.  No other changes necessary.

---

### Post by mschap on 2009-05-15
Same problem

I delayed moving to Linux for 3 years due to the lack of a half decent WYSIWYG html editor.  I did migrate 5 years ago and have been using NVU and Kompozer since then.  This is really frustrating as I do not want to go back to M$.

---

### Post by SteveDee on 2009-05-18
> **mistypotato said:**
> Another...more serious issue.....

Kompozer 8 (available form the Kompozer site), has a nasty bug in it that will arbitrarily change the code in certain web pages rendering the entire page useless.  I can find no rhyme or reason to it.  But it destroys the page.

Without a backup, you can lose a great deal of work so if you're going to try the Beta 8 version, I STRONGLY advize backups before you even load the pages into Kompozer.

I had this happen before but I thought it was a fluke but I downloaded a fresh copy yesterday and 3 months later, it's doing it again.

It may happen only when you work on non-standard web pages such as .cfm pages etc.   Not certain on that.

I just wish we could have a working Kompozer like it was before.  No other changes necessary.

Kompozer version 20081218 seemed to be working fine for me, but since Ubuntu upgrade to 9.04 I get a strange problem if I copy a string from one page to another (especially if the string contains a web link). I find that other chucks of text have been dumped in the (copy to) page as well. This could be anywhere in the page, so can be tricky to spot.

Anyone running a version of Kompozer on 9.04 that is problem free?

---

### Post by MasterNetra on 2009-06-13
> **SteveDee said:**
> Kompozer version 20081218 seemed to be working fine for me, but since Ubuntu upgrade to 9.04 I get a strange problem if I copy a string from one page to another (especially if the string contains a web link). I find that other chucks of text have been dumped in the (copy to) page as well. This could be anywhere in the page, so can be tricky to spot.

Anyone running a version of Kompozer on 9.04 that is problem free?

No its not problem free on 9.04, it crashes when you go to smart widgets, at least in Ubuntu version of Jaunty.

---

### Post by johnh10000 on 2009-06-17
> **MasterNetra said:**
> No its not problem free on 9.04, it crashes when you go to smart widgets, at least in Ubuntu version of Jaunty.

Iwas haveing similar probs.  I just got quanta +, so far so good

apt-get install -f quanta

---

### Post by Francewhoa on 2009-06-23
KompoZer 0.7.10 is unstable with Ubuntu. Try the latest version 0.8 alpha it's more stable. The new version has views/tabs built in and spit window like Dreamweaver. Find this post: [http://ubuntuforums.org/showpost.php?p=7501868&postcount=6](http://ubuntuforums.org/showpost.php?p=7501868&postcount=6)

---

### Post by jack_spratt on 2009-06-26
Woot - just lost three hours of work thanks to a bug thats been known about for more than 7 months and has been fixed for six!

Last time I ever use kompozer - devs allowing this app to be in use for so long when its so broken is totally unacceptable.

Still no viable WYSIWYG in GNU/Linux then... I'll wait another three years and try again. Fortunately I hardly ever use them.

My advice: DONT USE KOMPOZER.

---

### Post by ivanvajar on 2009-06-26
You can use Seamonkey suite. Works fine.

---

### Post by jack_spratt on 2009-06-26
> **ivanvajar said:**
> You can use Seamonkey suite. Works fine.

Good idea - I'll try it out

---

### Post by johnh10000 on 2009-06-27
gang I had the same problem get kompozer-0.7.10-i386.deb
from their site or my ftp site [ftp://tux.isa-geek.org/linux/webdesign/kompozer-0.7.10-i386.deb](ftp://tux.isa-geek.org/linux/webdesign/kompozer-0.7.10-i386.deb)

it works then

---

### Post by ubalderdash on 2009-07-05
> **jack_spratt said:**
> Woot - just lost three hours of work thanks to a bug thats been known about for more than 7 months and has been fixed for six!

Last time I ever use kompozer - devs allowing this app to be in use for so long when its so broken is totally unacceptable.

Still no viable WYSIWYG in GNU/Linux then... I'll wait another three years and try again. Fortunately I hardly ever use them.

My advice: DONT USE KOMPOZER.


Well said Jack Spratt ! Kompozer is about as useful as a bike with no wheels; it keeps your anger exercised but you never get anywhere. Windows is still the only place to be for serious web publishers !

---

### Post by ivanvajar on 2009-07-05
GOOD NEWS EVERYBODY! Dreamweaver is available on Wine Doors! I installed it two days ago. I have been using Seamonkey before.

---

### Post by ubalderdash on 2009-07-11
> **ivanvajar said:**
> GOOD NEWS EVERYBODY! Dreamweaver is available on Wine Doors! I installed it two days ago. I have been using Seamonkey before.

This sounded like really good news but it turns out that the Wine-Doors package repository is down and the website is dead. Wine-Doors still  installs well enough but cannot be used.

---

### Post by Cfossy2 on 2009-08-28
I also had the same problem with Kompozer, however I took a chance, downloaded Kompozer 0.8 Alpha, under Ubuntu 9.04, unzipped it and installed it into the old Kompozer directory and presto it worked and I am now able to edit files as well as right click to edit JPEGs.As a precaution I also downloaded SeaMonkey which doesn't seem to have a problem at the moment.

---

### Post by ktmom on 2009-09-11
Thanks for the pointer.  Sure enough [kompozer-0.8a4]("http://sourceforge.net/projects/kompozer/files/current/0.8a4/kompozer-0.8a4-gcc4.2-i686.tar.gz/download") works a treat.  It's not perfect, but at least it no longer crashes.  There is a discussion about the problems under GTK 2.14 and the progress of porting Kompozer to a newer Mozilla code base at [WYSIFA Forum]("http://wysifauthoring.informe.com/forum/kompozer-development-f11/kompozer-0-8-progress-t1940.html")

---

### Post by ArielEnter on 2009-10-14
There is a new versions of Kompozer in its alpha stage that doesn't have this issue. Some installation packages (.deb) for Ubuntu have been already submitted. You have to install both kompozer-data and kompozer packages.

---

