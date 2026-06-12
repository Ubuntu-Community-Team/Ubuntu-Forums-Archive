---
title: "Need help for installing Linux and picking right software"
date: 2020-01-24
forum: New to Ubuntu
---

### Post by alihshawon on 2020-01-24
[FONT=Roboto]I am a heavy wi[/FONT][FONT=Roboto]ndows and mac user and same time Linux lover. But you guys and me have same mindsets. that is we love to share and contribute. This is why I love Linux a lot. From long ago, I am thinking to migrate to Linux but I couldn't. Its because I am so used  to with few programs  on windows that in order to transform, I have to ensure that I will be able to use these programs or similar programs on Linux. Also I want a unique looking desktop environment which will require less resource.  So can you please suggest me any desktop environment where I can start my journey? I am using following programs-[/FONT]
[FONT=Roboto]
1. Adobe Photoshop ***
2. Adobe After Effects ***
3. Adobe Audition *
4. Adobe Premiere Pro **
5. Adobe Illustrator ***
6. FL Studio ***
7. Autodesk Maya *
8. Camtasia Studio ***
9. Android Studio ***
10. Nox Player *
[/FONT]
[FONT=Roboto]These star marks indicates how frequently I use them. So you know transforming to another OS is quite challenging for me without your help. So if you could suggest me a desktop environment where I could be comfortable like windows (actually I am kind of bored because of their unnecessary updates, ads and resource greedy systems but I don't have any other option) and I could run most of these programs, that would be very helpful for me. Or even you could suggest me alternatives of these programs. Or if you want more detailed discussion, please feel free to ask me anything.I have installed ubuntu, linux mint, zorin os before. But never used them even for one week. But now I really want to migrate from windows and get softwares that will be good for me also I will get good support. Today I downloaded Ubuntu latest LTS distro for amd64 machine and made live usb using rufus using gpt partition. But unfortunately I couldn't install it because it shows me "Out of range" message on display. What I thinking that there is something wrong with my hardware. So here is the details of the machine where I want to install Ubuntu.[/FONT]

[FONT=Roboto]Mainboard: Gigabyte B250m DS3H[/FONT]
[FONT=Roboto]CPU: Intel Core i5 7500 3.40 GHz[/FONT]
[FONT=Roboto]RAM: 32 GB DDR4[/FONT]
[FONT=Roboto]HDD: 240 GB SSD for OS[/FONT]
[FONT=Roboto]          2TB SATA for storage.[/FONT]
[FONT=Roboto]GPU: Zotac nVidia Geforce GT 430 4GB[/FONT]

[FONT=Roboto]Monitor is square monitor and I always use 1280x1024 on windows 10. I never cared for refresh rate but I think it was either 50 or 60 hz[/FONT]


[FONT=Roboto]It makes me very sad that I have convinced about 50+ people to transform from windows to Linux (Most of them chosen Linux mint or Zorin OS because of similar look to windows as they were not so expert. But I am happy with that because they are using Linux) but I couldn't migrate myself till today. I really want to migrate and this is why I need support.[/FONT]

[FONT=Roboto]I hope you all will help me with installation and picking the softwares.[/FONT]

---

### Post by crip720 on 2020-01-24
First question would be if you want to relearn what you do with your  programs with other replacements.  Don't know enough, but think the  first five will not work or not work well in Linux.  Some might work  with wine, but you will have to check on he wine website.  There should  be Linux alternatives to all those programs, but they will not be the  same.  Gimp would be a good replacement for photoshop, but there are  others also.  Desktops are usually a person's opinion as to the best,  some use lighter resources, some look nice.  I would use google with  each of your programs and check if they work on linux or alternatives.

---

### Post by Impavidus on 2020-01-25
Adobe isn't known for being Linux-friendly. They make applications for Windows and Mac, not Linux. There are some alternatives. The obvious alternative for Photoshop is Gimp. 90% of the users use such a small fraction of the functionality of Photoshop and Gimp that they won't notice any difference, but you may belong to the other 10%. There are alternatives for most other software too, but with such highly specialised stuff as you use, it's difficult to say whether you'll consider them adequate. In any case it will take time and effort to get used to them. Have a look at [https://alternativeto.net/](https://alternativeto.net/) and try some options. But if you can't live without the applications you mention, you won't be able to live without Windows or Mac either.

The desktop environment doesn't affect the applications you can run, although some combinations allow you to use somewhat less memory as application and desktop environment can share libraries. But OS, desktop environment etc. won't use much more than a GB, so that's no consideration on your computer. You could consider Ubuntu Studio. It's an official Ubuntu flavour and comes with a light and easily configurable desktop environment and a load of image, video and audio software installed.

Your "Out of range" message comes as the OS fails to set the correct mode for your monitor. Try booting with the nomodeset option. It's often needed on nvidia systems before you've installed the proprietary drivers. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I don't have nvidia graphics so I never tried this myself, but here is some more information: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Don't try to find a driver on a website and install it manually. The additional drivers tool does it all automatically and makes sure it keeps working after upgrades.

---

### Post by therealdps on 2020-01-25
Hey there, I thought that I would just give a little input as to some of the programs that you are looking for. I do not think that you can natively get any of those Adobe products on Ubuntu, but you can always try Wine. There are however, so very nice alternatives (some of which i use myself), but I cannot vouch for how they compare to the Adobe counterparts, but I haven't ever had any issue with getting work done with these programs:

[LIST]
[*]Krita (very nice art suite) 
[*]Blender (also and art suite, but imo a focus on 3D modeling) 
[*]Drawing (a VERY simple "Paint" like program) 
[*]LMMS (an alternative to Fruity Loops) 
[*]Anbox (alternative to the Nox android emu) 
[*]OBS (Fully featured and very functional Open Broadcaster Software, alternative to Camtasia) 
[*]Android Studio has a native program, in several forms (Snap, Deb, RPM i think too, etc). 
[/LIST]

These are the programs that I can personally vouch for, that work and work very well. Now, you may have your own opinion about them after trying them, but try to keep an open mind and understand that when you first tried to use Adobe products, you had to learn them as well :D.

Now, on your issue with getting Ubuntu installed because of an error of "out of range", someone else has already touched on what could be causing it, and I completely agree with their input... so no need for me to repeat it. If you happen to be confused on how to implement the fix, and what to do afterwards, do not hesitate to contact me or quote me with a reply here. 

I think that it would be a fairly good choice to start with Ubuntu (regular, vanilla Ubuntu), mainly because of the lack of headaches and the GREAT hardware and community support. The desktop is also very stable and easily managed, as long as you don't get caught up in the whole "elitist, i have to make everything look like a have a degree in CS" customization things. Then you may be in trouble, but that wouldn't be the fault of Ubuntu, but the extra stuff that gets done to it lol.

Let me know your thoughts, and get back to us!

Cheers!

---

### Post by mastablasta on 2020-01-26
also i would try the alternative software first in windows. see if they are offering what you need. if not and if you really need specific professional software that only has windows version, then just install windows. use what works for you and what does that you need to do. after all OS should be get out of the way, it's the applications that matter. if you can't use applications you need to use, then the OS is meaningless.

---

### Post by alihshawon on 2020-02-04
Hello, sorry for late response. I am always willing to learn.

---

### Post by alihshawon on 2020-02-04
> **crip720 said:**
> First question would be if you want to relearn what you do with your  programs with other replacements.  Don't know enough, but think the  first five will not work or not work well in Linux.  Some might work  with wine, but you will have to check on he wine website.  There should  be Linux alternatives to all those programs, but they will not be the  same.  Gimp would be a good replacement for photoshop, but there are  others also.  Desktops are usually a person's opinion as to the best,  some use lighter resources, some look nice.  I would use google with  each of your programs and check if they work on linux or alternatives.

Hello, sorry for late response. I am always willing to learn. Also I would prefer native linux programs instead of depending on windows programs through wine or any emulator.

---

### Post by alihshawon on 2020-02-04
> **Impavidus said:**
> Adobe isn't known for being Linux-friendly. They make applications for Windows and Mac, not Linux. There are some alternatives. The obvious alternative for Photoshop is Gimp. 90% of the users use such a small fraction of the functionality of Photoshop and Gimp that they won't notice any difference, but you may belong to the other 10%. There are alternatives for most other software too, but with such highly specialised stuff as you use, it's difficult to say whether you'll consider them adequate. In any case it will take time and effort to get used to them. Have a look at [https://alternativeto.net/](https://alternativeto.net/) and try some options. But if you can't live without the applications you mention, you won't be able to live without Windows or Mac either.

The desktop environment doesn't affect the applications you can run, although some combinations allow you to use somewhat less memory as application and desktop environment can share libraries. But OS, desktop environment etc. won't use much more than a GB, so that's no consideration on your computer. You could consider Ubuntu Studio. It's an official Ubuntu flavour and comes with a light and easily configurable desktop environment and a load of image, video and audio software installed.

Your "Out of range" message comes as the OS fails to set the correct mode for your monitor. Try booting with the nomodeset option. It's often needed on nvidia systems before you've installed the proprietary drivers. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I don't have nvidia graphics so I never tried this myself, but here is some more information: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

Don't try to find a driver on a website and install it manually. The additional drivers tool does it all automatically and makes sure it keeps working after upgrades.

I am very open to try different softwares. I use adobe programs a lot but that doesn't mean I won't be live without them. I know gimp is better option for me. But I don't know for other programs. So your advice to see on alternative.to will be very helpful for me.

And for desktop environment, I am currently trying with kde and gnome. I could chose these two from other environments. I will be able to pick one as permanent very soon.
And I have fixed the nvidia driver issue by installing ubuntu 16. version 16 isn't making any problem at all. Also it runs very smoothly. performance is so much good.

---

### Post by alihshawon on 2020-02-04
> **therealdps said:**
> Hey there, I thought that I would just give a little input as to some of the programs that you are looking for. I do not think that you can natively get any of those Adobe products on Ubuntu, but you can always try Wine. There are however, so very nice alternatives (some of which i use myself), but I cannot vouch for how they compare to the Adobe counterparts, but I haven't ever had any issue with getting work done with these programs:

[LIST]
[*]Krita (very nice art suite)
[*]Blender (also and art suite, but imo a focus on 3D modeling)
[*]Drawing (a VERY simple "Paint" like program)
[*]LMMS (an alternative to Fruity Loops)
[*]Anbox (alternative to the Nox android emu)
[*]OBS (Fully featured and very functional Open Broadcaster Software, alternative to Camtasia)
[*]Android Studio has a native program, in several forms (Snap, Deb, RPM i think too, etc).
[/LIST]

These are the programs that I can personally vouch for, that work and work very well. Now, you may have your own opinion about them after trying them, but try to keep an open mind and understand that when you first tried to use Adobe products, you had to learn them as well :D.

Now, on your issue with getting Ubuntu installed because of an error of "out of range", someone else has already touched on what could be causing it, and I completely agree with their input... so no need for me to repeat it. If you happen to be confused on how to implement the fix, and what to do afterwards, do not hesitate to contact me or quote me with a reply here. 

I think that it would be a fairly good choice to start with Ubuntu (regular, vanilla Ubuntu), mainly because of the lack of headaches and the GREAT hardware and community support. The desktop is also very stable and easily managed, as long as you don't get caught up in the whole "elitist, i have to make everything look like a have a degree in CS" customization things. Then you may be in trouble, but that wouldn't be the fault of Ubuntu, but the extra stuff that gets done to it lol.

Let me know your thoughts, and get back to us!

Cheers!


Thanks so much for your help. I am familiar with Blender and Android Studio on Linux. And I already started with Ubuntu 16. I didn't faced any problem with installing it. I have also fixed the driver issue too. Now its time to explore. I believe with you all, I won't face any problem and I will learn more day by day. If you would allow, I would contact you personally for tips for these programs.

---

### Post by Impavidus on 2020-02-04
It's OK to use Ubuntu 16.04, but it's a bit old and has only a little over one year of support left. After that there are no more security upgrades and no more repositories to install software from, so you should have stopped using Ubuntu 16.04 by April next year. Some of the applications you may install only have three years of support, meaning they are end of life already. And a bit old in Ubuntu also means older versions of most applications. I'm quite sure there is a way to fix your graphics driver issue in Ubuntu 18.04 or 19.10.

---

### Post by vidtek on 2020-02-04
You are going about this in the right way.  Gnome desktop is probably better supported than many others, personally I use Kubuntu as the personalisation options are myriad, like peeling an onion, there are layers of customisations available.  

With Kubuntu or KDE and the plasma desktop the ease of switching from one desktop or activities to another with various applications running isolated from each other enhances my productivity enormously.  On the odd occasion I have to fire up Windows (usually to support another user) I find it frustrating that I cannot have multiple switchable desktops and it really cramps my style now. 

Basic gnome now incorporates multiple desktops too.

Kubuntu has the Kdenlive video editor which is usually adequate for my needs, and as others have said, Gimp has more options than you can poke a stick at........

Audacity is a great audio editor, and openoffice is just about as good as Office in Windows.  All free, you must accept that with no cost there is a steep learning curve and there are the occasional glitches.  But you cannot compare commercial products such as MS Office and the full range of Adobe products costing thousands of pounds with an open-source offering.

The other issue is of course time.  Every minute spent learning a new application enough to become proficient is a minute you will never get back again.  Are you prepared to use your precious time in this way?  Only you can answer that.  But I would add that if you are a young person with a new family, this may not be the best way to spend your precious time.

All the best to you Tony.

---

