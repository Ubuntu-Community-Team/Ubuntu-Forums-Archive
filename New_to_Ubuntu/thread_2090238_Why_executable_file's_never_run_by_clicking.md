---
title: "Why executable file's never run by clicking?"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by starstreams on 2012-12-01
Hello. I'm working out of a book called *Quick start guide Unix/Linux 4th edition Deborah S Ray*. So far all the commands demonstrated in the book seem to be working great, but I've run into an issue more than once when I double click on a setup-x86 installer. All the read-me sources imply that you can execute the file. but it never does anything. The option titled: (*Make the file executable) "*is" checked. What ends up happening is, I see a dialog box with three options:

[LIST]
[*]Execute
[*]Execute in Terminal
[*]Open
[/LIST]

Nothing happens when I choose any of them. However, if I point the terminal to the location of the file and run it, the installer runs and installs the application. 
What is my operating system missing that I can't run the file as the documentation says I should? 

Advanced Thanks

---

### Post by Enigmapond on 2012-12-01
If you open the preferences in nautilus/behavior you can set it there to execute or just ask you each time what to do. Hope this helps!

Cheers!

PS Welcome to the forum!..:)

---

### Post by squakie on 2012-12-01
A lot of those are also probably shell scripts - which normally you would be asked if you want to execute or display, at least that's been my experience.

---

### Post by monkeybrain2012 on 2012-12-01
It may or may not describe your problem but in general if you double click something in lubuntu (say a music file, which is supposed to be open by the default music player) it appears not to work and you have to click many times to get it to open.  This is the most frustrating thing for me about lubuntu. 

After searching the lxde forum it turns out that double click does work in lubuntu but the default is that it takes a long time so people end up clicking many times in order to get the file to open by the application.

Here is the fix.

create a hidden file called .gtkrc-2.0 in your home if it doesn't already exist.

```
leafpad .gtkrc-2.0
```then enter the following

```
gtk-double-click-time=1000
```Then save and there should be a huge improvement.

---

### Post by starstreams on 2012-12-01
**[COLOR=Blue]@ Enigmapond[/COLOR]**,  
But the problem is not whether or not it "asks" me what to do each time. The issue is that it doesn't execute.
If clicking on execute doesn't execute, why would setting it to automatically execute make any difference? Or I guess that is the question. 
Why is the diolog box not executing when I click execute?


**EDIT**, @Enigmapond: you must have edited your post. 

I had originaly responded to your suggestion about changing nautilus's preferences.. and I said..
> How did you know I had nautilus installed? 
 Nautilus is a file manager I recently installed because Truecrypt needed it to mount drives.  Are you saying that my issue could be related to a file manager's preferences? The reason was the base of my original question. I'm trying to learn what this issue relates to? So would it be safe for me to assume that no matter what file manger I install  this issue is usually related to the preferences in (any) given file manger? By the way, I searched the nautilus man page, I  don't see where about changing preferences in Nautilus. PCManFM is my default file manager, and I also have nautilus installed on the same system, but nautilus _only loads_ when I mount a Truecrypt volume.  I wonder if it's bad to have two FM's installed.
 [COLOR=Blue]**@squakie**[/COLOR]

 It is an executable script, that came with no instructions. And like I mentioned when I double click it, it "does" prompt me if I want to execute the file. 
But it does nothing when I select an option, *execute* or *execute in terminal*. I was able to install Truecrypt by pointing the terminal to the executable path. My question is why? Why do I have to manually run it from the terminal when the file is setup as an executable?
 

 [COLOR=Blue]**@monkeybrain2012**[/COLOR]
 I don't have any issues starting files. I haven't tried music files yet. but text files open fine.
 It's interesting you mentioned LXDE forum. I didn't know they had their own forum. I know LXDE is a desktop environment. But when I was looking for a linux forum today, I went to Lubuntu's site, but their defult forum links to Ubuntu forums. By the way, I appreciate the recommendation on what you said about creating a hidden file with gtkrc-2.0.
However, I'm currently in learning mode, and I don't understand what that does at this stage. Can you please explain in more detail? I don't want to just start entering commands and changing the system without knowing something about them. But I do appreciate you taking the time to make the suggestion.

---

### Post by monkeybrain2012 on 2012-12-01
So you install Nautilus in lubuntu, this may be the root of your problem as pcfman is the default file manager. When mix and match like that something strange may happen. I remember when I did that last time cd and usb stopped mounting and it may be other problems depending on your versions and set up.  it would appear that depending on where a file is sometimes it is controlled by nautilus sometimes by pcfman so the options in the file managers don't always work.

  **EDITED: **you can mount drives in pcfman just not on the Desktop. You open any folder and see the drives mounted on the side panel. If you don't see the drives there is a tab on top of the side panel called "Places", click the small arrow and choose "Directory Tree" instead and you will see all your mounted drives.

---

### Post by starstreams on 2012-12-01
> **monkeybrain2012 said:**
> So you install Nautilus in lubuntu, this may be the root of your problem as pcfman is the default file manager. When mix and match like that something strange may happen. I remember when I did that last time cd and usb stopped mounting and it may be other problems depending on your versions and set up.  it would appear that depending on where a file is sometimes it is controlled by nautilus sometimes by pcfman so the options in the file managers don't always work.

  **EDITED: **you can mount drives in pcfman just not on the Desktop. You open any folder and see the drives mounted on the side panel. If you don't see the drives there is a tab on top of the side panel called "Places", click the small arrow and choose "Directory Tree" instead and you will see all your mounted drives.

I was getting an error in Truecrypt. It would not mount with PCman. The file was located in my home directory/Downloads. I think there are some instructions in nautilus that TC seems to prefer because the developers set it as the FM on choice. I know some people have mounted Truecrypt drives with custom scripts. 
So monkey, are you saying that the location of your files can sometimes dictate what file manager loads?
I've been told by a few people that it's ok to have more than one FM on the system, but it does seem like it could cause some confusion. I don't know how to write script at this stage in order to get Truecrypt to load in my default PCman manager. Do you think uninstalling PCman and just keeping Nautilus as the default instead might fix all this?

---

### Post by monkeybrain2012 on 2012-12-01
> **starstreams said:**
> I was getting an error in Truecrypt. It would not mount with PCman. The file was located in my home directory/Downloads. I think there are some instructions in nautilus that TC seems to prefer because the developers set it as the FM on choice. I know some people have mounted Truecrypt drives with custom scripts. 
So monkey, are you saying that the location of your files can sometimes dictate what file manager loads?
I've been told by a few people that it's ok to have more than one FM on the system, but it does seem like it could cause some confusion. I don't know how to write script at this stage in order to get Truecrypt to load in my default PCman manager. Do you think uninstalling PCman and just keeping Nautilus as the default instead might fix all this?

I tried this in 11.04, I don't remember clearly now, but maybe Pcman controlled files in the Desktop or the other way around, but some functions that originally worked in Pcman would stop working and they don't work in Nautilus either (though no problem in Ubuntu 11.04 )  I have tried fooling around with configuration files  but never succeeded in fixing the problems. In the end I just reinstalled. 

Yeah, I am aware of people saying it is ok (why do you think I did that? :))but my guess is that they are not the developers of either Gnome or LXDE and haven't tested all the possible scenarios, it may work fine for them because it happens that they don't use the functions where problems occur.

I never use trucrypt so afraid can't help you there.

---

### Post by squakie on 2012-12-01
Some scripts, when executed by a mouse click, run very fast and have no indication they ever did run - normally I don't see a terminal open for them.  If it runs it terminal via ./<scriptname>, then I would suspect it is actually running when you click it or select execute.  One way to tell:  edit the script and add:

echo ***** the script ran ***** > ~/mytest.txt

then save the script and double click it (or click execute).  Wait a few seconds (perhaps 30 or so) and then check to see if a file called "mytest.txt" now exists in your home folder and if its contents say:

***** the script ran *****

If so, you know the script is executing even if you don't see it.  If not, post back and we'll go from there.

---

### Post by starstreams on 2012-12-01
Thanks again guys.


> **squakie said:**
> Some scripts, when executed by a mouse click, run very fast...

If so, you know the script is executing even if you don't see it.  If not, post back and we'll go from there.
Well, I uninstalled Nautilus, and Truecrypt won't mount as expected. There is something in Nautilus that Truecrypt needs to mount drives. 
Anyway, I also uninstalled Truecrypt so I could test to see if the file would execute now that nautilus is removed. It didn't though, same thing. Nothing happens when I click it.
As far as adding the [COLOR=Gray]*echo ***** the script ran ***** > ~/mytest.txt*[/COLOR], where do you put these lines in the file? at the very end of the file after the exit 0? there's all kinds of code in the setup file but don't have experience with scripts. I'm using Leafpad to look at it.

Either way, I don't think it ran when I selected execute from the dialog box. The reason I say that is, in my last attempt to run it by pointing the terminal to the file (which installed it finally) there was a bunch of conformation messages that I had to click _yes_ to allow the program to proceed through the installation. But simply clicking the executable never gave me any prompts. 
Maybe the reason I can't run it from the file is because it needs sudo permissions which the terminal gives the option for.

---

### Post by monkeybrain2012 on 2012-12-01
In my experience installing nautilus somehow changes some configurations, functions that were lost didn't restore even after removing nautilus (in my case mounting usb drives, I couldn't figured out what has been changed because the lxde configuration files seemed ok, what makes it more difficult is that lubuntu modifies vanilla lxde architecture so I might even have been looking at the wrong configuration files)

---

### Post by starstreams on 2012-12-01
I think you could be right monkey
I thought maybe I could run a reinstall on PCman to see if it reset itself, bit nothing changed.
One of my friends says, PCman is buggy, and I've also noticed some file manager crashes with it. He says, There is an fork of it called SpaceFM that much more stable.

But in the case of Truecrypt, he explained that Certain apps still rely on nautilus library's for certain things. Lots of these apps are written for &#8220;mainstream&#8221; Linux GUIs in mind and aren&#8217;t always platform independent. What happens with Truecrypt if you don't have nautilus installed is, when you go to mount a drive or file container, it says, [COLOR=Red]*Invalid Argument *[COLOR=Black]and it won't mount. I don't even know if SpaceFM would work with Truecrypt.[/COLOR][/COLOR]

---

### Post by squakie on 2012-12-02
> **starstreams said:**
> Thanks again guys.



Well, I uninstalled Nautilus, and Truecrypt won't mount as expected. There is something in Nautilus that Truecrypt needs to mount drives. 
Anyway, I also uninstalled Truecrypt so I could test to see if the file would execute now that nautilus is removed. It didn't though, same thing. Nothing happens when I click it.
As far as adding the [COLOR=Gray]*echo ***** the script ran ***** > ~/mytest.txt*[/COLOR], where do you put these lines in the file? at the very end of the file after the exit 0? there's all kinds of code in the setup file but don't have experience with scripts. I'm using Leafpad to look at it.

Either way, I don't think it ran when I selected execute from the dialog box. The reason I say that is, in my last attempt to run it by pointing the terminal to the file (which installed it finally) there was a bunch of conformation messages that I had to click _yes_ to allow the program to proceed through the installation. But simply clicking the executable never gave me any prompts. 
Maybe the reason I can't run it from the file is because it needs sudo permissions which the terminal gives the option for.

If it's asking questions and wanting replies, then it will need to run in a terminal.  Normally nobody is going to go to the trouble to provide a "windowed" question/answer environment just for an install.  When you just click on it, besides it not having super user permissions, it also can't ask the questions (probably just going to stdout).

---

### Post by starstreams on 2012-12-02
interesting, that makes perfect sense squakie.
I didn't think of that, but  coding all the windows would be a lot more work. Either way, the terminal works great.
By the way, thank you for that point of view, that makes total sense now.

I'm a little uncertain about my file manager situation. Is there anything wrong with installing something like nautilus (which I think is made for Gnome) on Lubuntu which uses the light weight PCmanFM by default?
I removed PCmanFM, because I think it got broke after I installed nautilus. And also because I can't use PCmanFM with Truecrypt unless I use scripts which is beyond me at this stage.

Although I'm trying to force myself to do things via the terminal, I'm curious about something. 
I'm seeing nautilus in the Synaptic Package Manager as an option to install rather than using the terminal command, so I'm guessing because it's there, could this indicate that it's compatible with my version of Lubuntu? I mean how does the terminal know how to find the correct version for my system?

---

