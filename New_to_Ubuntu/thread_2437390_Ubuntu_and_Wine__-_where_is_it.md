---
title: "Ubuntu and Wine  - where is it?"
date: 2020-02-23
forum: New to Ubuntu
---

### Post by mge23 on 2020-02-23
Hello all.  New to Ununtu (well, this version: 16.04 LTS updated from 14.04 LTS that I installed last night, which replaced a really old version I hadn't used in 4020 days!).

Have installed Wine, but where is it located?  How do I locate and open it and keep it visible on the side? It briefly appears as shown in the attached screenshot.  As soon as I close the window it disappears from the side.  Puzzled.

Tried to locate this issue elsewhere on the forum but couldn't find anything.

---

### Post by mörgæs on 2020-02-23
Hi, welcome to the fora.

The main problem for Wine is support for (new/advanced) Windows programs, and you will find many threads here dealing with this topic.

The Wine developers are constantly improving in this field. Therefore I think you should do a clean install (no upgrades) of 19.10 in stead of spending time on 16.04.

---

### Post by The Cog on 2020-02-23
You only see a wine window when it's running a windows application. 
You can launch windows apps with a command line like "wine notepad". I think you can probably right-click a windows program in a file manager and choose to open it with wine, but it's some years since I used wine so I don't remember for sure.

Oh, and your screenshot is of a wine configuration editor (wineconfig?) running. It's not wine itself. Wine doesn't have its own user interface as such.

---

### Post by mge23 on 2020-02-23
Thank you for your reply.

I'm using 16.04 LTS simply because this old PC won't accept the latest version of Ubuntu (rather than disposing of a perfectly good old machine I've upgraded with the most suitable OS I could).

---

### Post by Impavidus on 2020-02-23
That's not the way to go. If you have old hardware (like a computer that hadn't been used in 11 years), it's usually best to use a light flavour, not an old release. As the light flavours like Lubuntu only get 3 years of support, 16.04 is not the best option. I still have Xubuntu 18.04 running on a reasonably powerful 16 year old computer. There are cases where you indeed need an old kernel or a very light system. There are Linux distros specifically made for such old hardware.

But sometimes sending it to the recycling centre is the best thing to do with old stuff that still works. Using it for the sole reason of not leaving it unused doesn't make sense. A newer computer can do the same tasks at lower energy consumption.

---

### Post by monkeybrain20122 on 2020-02-23
> **Impavidus said:**
> That's not the way to go. If you have old hardware (like a computer that hadn't been used in 11 years), it's usually best to use a light flavour, not an old release. As the light flavours like Lubuntu only get 3 years of support, 16.04 is not the best option. I still have Xubuntu 18.04 running on a reasonably powerful 16 year old computer. There are cases where you indeed need an old kernel or a very light system. There are Linux distros specifically made for such old hardware.

But sometimes sending it to the recycling centre is the best thing to do with old stuff that still works. Using it for the sole reason of not leaving it unused doesn't make sense. A newer computer can do the same tasks at lower energy consumption.

Disagree. Ubuntu 16.04 is still a supported release and it is actually running exceptionally well here on a fairly new and powerful system76 laptop. This is my production system and I need it stable and rock solid. I know things well enough to selectively upgrade some packages and keep other as is, etc. So I am having the best of all worlds now, I have a stable system but also bleeding edge versions for software I use (newer than the version in 19.10 or even 20.04) 

Whereas there are things in 18.04 that are essentially broken, not a big deal but since we are on this thread. playonlinux is one of those things that work in 16.04 but completely broken in 18.04.

---

### Post by mörgæs on 2020-02-23
> **mge23 said:**
> ...this old PC won't accept the latest version of Ubuntu...

We need the hardware specifications to be able to give meaningful advice. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and post lshw.txt in CODE tags.

---

### Post by monkeybrain20122 on 2020-02-23
To answer op's question.

See this thread [https://ubuntuforums.org/showthread.php?t=2391933](https://ubuntuforums.org/showthread.php?t=2391933)
Upstream (Debian, not wine, since those files were created by Debian) has removed winecfg .desktop as well as a few other .desktop files.

---

### Post by webaake on 2020-02-23
For Wine I'd recommend Playonlix which is a very useful helpprogram for installing and configuring Windows programs under Wine. Yes, it says "Play" but it works equally well for production applications. Here: [https://www.playonlinux.com/en/](https://www.playonlinux.com/en/)

I use Playonlinux everyday on 18.04.

---

### Post by mge23 on 2020-02-23
Thank you for this.  

It's a long long time since I've done anything like  this (wasn't sure how to open the terminal window; know now!).  Ran  that command but all I see is the attached screenshot...

---

### Post by mörgæs on 2020-02-23
Quoting myself:

> **mörgæs said:**
> ...and post lshw.txt in CODE tags.

The text please and not as screenshot.

---

### Post by monkeybrain20122 on 2020-02-23
> **webaake said:**
> For Wine I'd recommend Playonlix which is a very useful helpprogram for installing and configuring Windows programs under Wine. Yes, it says "Play" but it works equally well for production applications. Here: [https://www.playonlinux.com/en/](https://www.playonlinux.com/en/)

I use Playonlinux everyday on 18.04.

How do you use pol on 18.04? It is broken here. [https://ubuntuforums.org/showthread.php?t=2398938](https://ubuntuforums.org/showthread.php?t=2398938)

---

### Post by EuclideanCoffee on 2020-02-23
I'm a bit frustrated that no one has yet told you where wine is.

With the terminal window you opened, there are a few commands that can help you determine where an application is. Type the following

which wine

You should see the following, typically (I don't have wine installed) /usr/bin/wine.

This is the path where the executable command is located. This command will be in your path, meaning you can run the command simply typing "wine" into your terminal.

Now try it now. Notice that it may error out because you did not provide an "argument." An argument is anything after a command that goes into it. Essentially there are two ways of doing this. You can write an argument like so [command] word. The command will use word to generate a result. Or you could do this. [command] < word. This is called redirection, which essentially does the same as using a command with an argument, instead this argument is said to be redirected to the command.

Now download any Windows software. This could be on a CDROM or any media. Please Google how to use media. It will take time, but once you figure it out, you won't forget.

now in your terminal, find the path of where your download is. If you downloaded the file from your browser, it's likely in your ~/Downloads folder. Simply type this in your terminal.

cd ~/Downloads

Now type:

pwd

Notice the output says /home/your-username/Downloads

This is the absolute path to your Download folder. Now using cd, find where your file was downloaded. You should know by looking for the path. If you're using the "file explorer" on your desktop, simply figure out the entire folder path to determine where your file is stored.

Once you know the path, you can run it with wine.

Let's pretend you are still inside Downloads. To determine if you are now, simply write pwd in the terminal. The last / should indicate which folder you are in. If it's Downloads, you are in the correct folder for this tutorial. To run the Windows program in wine, simply do the following.

wine name-of-program-here.exe

And the program should run.

Run time errors are common. So if you have a problem, don't be afraid to Google "wine program name" and then the error you see in the best way you can describe.

Good luck!

---

### Post by webaake on 2020-02-24
How I use POL? Either I start POL itself and configure the apps from within it, or I start my Windows apps directly from the Ubuntu (Xfce) desktop. The thread you're refering to is from august 2018. This is febrauri 2020. Just install and test POL and see for your self.

Installing and running Windoze apps on Linux is always a daunting task. Wine makes it possible but can be a tall order to use. POL makes it easier to use Wine  but is still not hazzle free.  As we say where I grew up: "Fold up your shirt sleeves and dig in!" :P

---

### Post by monkeybrain20122 on 2020-02-24
> **webaake said:**
> How I use POL? Either I start POL itself and configure the apps from within it, or I start my Windows apps directly from the Ubuntu (Xfce) desktop. The thread you're refering to is from august 2018. This is febrauri 2020. Just install and test POL and see for your self.

Installing and running Windoze apps on Linux is always a daunting task. Wine makes it possible but can be a tall order to use. POL makes it easier to use Wine  but is still not hazzle free.  As we say where I grew up: "Fold up your shirt sleeves and dig in!" :P

I just tried it. Still same issue.
What versions of wine do you use for setting up your wine-prefixes?

---

### Post by webaake on 2020-02-24
I don't do any wineprefixes, POL does it for me. Within POL I can chose amongst several different Wine versions - different for every app if need be. 

I'm sorry but I don't remember any issues with POL (and Wine therein) on my Xubuntu 18.04 install. My install is updated every day and I've used several different kernels - 4.15.x, 5.05, and now 5.3.18. I do have issues with some windows apps within POL, but that's to be expected. Some don't run at all. That's life. I stopped using Windows several years ago and no dual booting whatsoever.

---

### Post by monkeybrain20122 on 2020-02-24
> **webaake said:**
> I don't do any wineprefixes, POL does it for me. Within POL I can chose amongst several different Wine versions - different for every app if need be. 

I'm sorry but I don't remember any issues with POL (and Wine therein) on my Xubuntu 18.04 install. My install is updated every day and I've used several different kernels - 4.15.x, 5.05, and now 5.3.18. I do have issues with some windows apps within POL, but that's to be expected. Some don't run at all. That's life. I stopped using Windows several years ago and no dual booting whatsoever.

What I am asking is which versions of wine do you use in setting up your pol apps? My 18.04 is completely up to date.

---

### Post by The Cog on 2020-02-24
```
sudo lshw -sanitize > lshw.txt
``` creates a file called lshw.txt. You should be able to view that file, and paste the contents into a comment here. The "> lshw.txt" is the bit that redirects output to a file called lshw.txt instead of letting it go to the screen.

---

### Post by webaake on 2020-02-24
I have POL 4.2.12.

---

### Post by monkeybrain20122 on 2020-02-24
> **webaake said:**
> I have POL 4.2.12.

I mean wine versions, not POL version. In POL you install your apps in different wine prefixes and for each choose your wine version. This is the whole point of POL instead of plain wine because you can choose different versions of wine. What that old thread is saying is that setting up wine prefixes doesn't work for versions of wine other than the system one, which defeats the purpose of using POL, since you can just use wine (on their forum they say it would work of 'newer' versions of wine, but didn't say which is 'newer". I tried 2.xx and didn't work)

---

### Post by webaake on 2020-02-25
Ok. One app runs on Wine 3.17 the others at 3.20. I do have older versions available within POL.

---

### Post by monkeybrain20122 on 2020-02-25
> **webaake said:**
> Ok. One app runs on Wine 3.17 the others at 3.20. I do have older versions available within POL.

They are available but you can't set up virtual drives with them. See the thread.

---

### Post by mastablasta on 2020-02-25
i found a couple of work arrounds, but i can't confirm it work with older wine version since i didn't need them. and i am not convinced they are needed anyway, because newer version are often better in their support for windows apps.

first, i dumped the usage of scripts. it seems like they are not working, so instead i would read the wine appdb website and follow instructions there (e.g. if some additional setting up is needed). this additional setup can be done through GUI.

so here is what i found out:

1. i use the install a non-listed program or app (small link bottom left on install screen).
2. installing any additonal libraries works well in GUI
3. some installers crash in the end or don't exit but install the app regardless (could be that is not a PoL issue)
4. changing wine version after install works. however i only i changed from default to staging (to get the CoD4 graphical issues resolved).

PoL does work but quirky. not as it was designed and it seems some parts work as they are supposed to, other work but you get to them through some other path. so try strange things, like install first then change wine version. or install first then setup or add the libraries (use the update function).

games i installed via PoL so far are mostly with gold or platinum rating on wineappdb: Oblivion (needed original .dll copied), Arx Fatalis, Torchlight, Fear, Far cry 1 & 2 (2 works better than native), CoD2, CoD4:MW, UT2004 (along with some bots like balistic weapons), Unreal, Quake2, Voyager Elite force 2. CoD2 install hanged in the end, but it works. i created manually short cut. no issues in game so far and i am almost at the end of it. Hearts of Iron 2 install didn't work, however copying files from the windows XP install worked and the game plays with no issues at all. i played through it 2 times.

I had issues with jedi knight 2, however there is open source engine implementation available and both jedi knight (i give it gold, because some keys namely Ctrl act strangely) and jedi academy (i give it platinum) work well. played through both.

i didn't bother with Morrowind this time since OpenMW works really good.

finally i wish they would get PoL back ot where it was. scripts or not, it used to work well and it would be good to have something that is independent of STEAM to install games and other applications as well. i know there is Lutris, but they are a bit to much on the edge for my taste, besides i don't want to mess up the OS just to play old games.

---

