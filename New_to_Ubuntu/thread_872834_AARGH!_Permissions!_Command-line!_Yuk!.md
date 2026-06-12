---
title: "AARGH! Permissions! Command-line! Yuk!"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by hellopaul on 2008-07-28
Hello.

I am new to Ubuntu, but am a very experienced computer user, but quite inexperienced when it comes to old-fashioned Ubuntu-style command-line interfaces. I have two questions:

1. I have installed Ubuntu on my wife's laptop, hoping it might be better/faster/leaner than Windows Vista. She is less computer literate than me, and has never typed a command since she threw out her MS-DOS machine many many years ago. In practice, once I've managed to set up (if I manage to set up!) her machine, will she be able to use it for normal day-to-day office/internet/email tasks without ever having to go near the terminal? It looks like installing even the smallest program requires way, way more than the 'double-click the installer' that Windows/Mac users enjoy.

2. How can I log in as 'root' or whatever I have to do, so that while I'm setting up the machine, I can just drag & drop files and not have to revert to the 1970s style terminal / sudo cp... just to copy or move files? I hate being told 'permission denied' - surely the USER tells the computer what to do, not the other way round?! I know it's possible to screw up the whole OS by deleting the wrong file, but I'm more than happy to take this risk. I can't even open a file using Text Edit without the silly permission denied thing!:confused:

I appreciate that Ubuntu is free and under constant development, but I was unaware that it really is not a finished GUI/OS and, as much as I hate to say it,  in no way can replace Windows for an average user. I use MacOSX on a day-to-day basis, and using Vista and Ubuntu make me realise just how good it is! (As it *should* be for the MASSIVE premium that Apple forces people to pay for its machines!)

Here's hoping my Ubuntu relationship can improve - I love the Ubuntu/Linux philosophy:)

Paul

---

### Post by Dr Small on 2008-07-28
First off, please do not regard the terminal as old-fashioned. In fact, it is the most powerful thing on your system. I use it daily. But, if you are using Ubuntu and set it up for your wife, she can use Synaptic to install applications.

As for using root to drag and drop files, please use:
```
gksudo nautilus
```

This can be made a launcher, typed in the Run Dialog or executed in the terminal.

---

### Post by eightmillion on 2008-07-28
You can start graphical apps as root with the command, "gksudo appname". To run nautilus as root you would use the command, "gksudo nautilus".

---

### Post by newbuntuxx on 2008-07-28
hey hellopaul,

I understand your furstaration as I was in the same boat not too long ago. However, once I learned that everything that I litereally need as a basic user is found in my home directory /home/username, then, I really didn't need to login as root to copy/paste etc.

But, to answer your question, open terminal and type: 

```
sudo nautilus
```

that is equivlent to your windows explorer, with full permissions. Just dont delete the wrong files.

---

### Post by gjoellee on 2008-07-28
command to log in as root (in terminal) is ```
su -
``` but you might not know the password...so go to System->Administration->Users and Groups, click on root and unlock. Then then click on root again and go to properties. Click set password by hand and make up something you remember. Now you can do su - and enter the root password you have set up

---

### Post by snowpine on 2008-07-28
You can install many applications by going to the applications menu and choosing add/remove programs. It is a very easy-to-use graphical installer, no command line necessary.

When giving/receiving instructions on these forums, most of us prefer to use terminal commands because they are impossible to misunderstand. Very often, there is a GUI alternative. However, when typing up tutorials on the forums, GUI instructions can be misinterpreted ("click the red button halfway down the page"--what if my screen is a different size or I use a different color theme?) so we use command line instructions to eliminate the ambiguity. :)

---

### Post by markjensen on 2008-07-28
Your #2 seems to be well-answered, so let me just post my observations and opinions on your other points.> **hellopaul said:**
> I am new to Ubuntu, but am a very experienced computer user, but quite inexperienced when it comes to old-fashioned Ubuntu-style command-line interfaces. I have two questions:

1. I have installed Ubuntu on my wife's laptop, hoping it might be better/faster/leaner than Windows Vista. She is less computer literate than me, and has never typed a command since she threw out her MS-DOS machine many many years ago. In practice, once I've managed to set up (if I manage to set up!) her machine, will she be able to use it for normal day-to-day office/internet/email tasks without ever having to go near the terminal? It looks like installing even the smallest program requires way, way more than the 'double-click the installer' that Windows/Mac users enjoy.The command line is actually quite advanced, not backwards.   Some items may be easier or more descriptive in that mode, like getting your partition information from a **fdisk -l**.   A graphical image for that would take up more space and generally be much less informative for it, to boot.   You can also copy/paste commands from other sites.  I have found it nearly impossible to copy/paste images to get my mouse to click where I need it to. ;)

That said, my wife actually asked me to install Linux on her new Dell laptop, after she used Linux on her Sony desktop that recently had a motherboard capacitor failure.   She doesn't use the command line.  Just just uses the computer.   So, yes, it can be done. :)

> **hellopaul said:**
> I appreciate that Ubuntu is free and under constant development, but I was unaware that it really is not a finished GUI/OS and, as much as I hate to say it,  in no way can replace Windows for an average user.I would disagree with that.  As would my wife.  And my kids (although they have 2 XP machines, 1 Vista, and one Linux PC they use interchangeably, so are a mixed bag).

---

### Post by hellopaul on 2008-07-28
Wow! Thanks everyone for your unbelievably quick replies! I will give your suggestions a go right now...

Thanks!

Paul

---

### Post by Shazaam on 2008-07-28
Two things to remember...
1. When using the "sudo command there is a fifteen minute time limit before it (the cli) will re-ask you for your password.
2. When you log in as root (using the su command) there is NO time limit. This can lead to mistakes like surfing the net as root, permanently changing/editing critical system files causing damage to your Ubuntu installation, etc. That is why there is a sticky about this here.....
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by billgoldberg on 2008-07-28
> **hellopaul said:**
> Hello.

I am new to Ubuntu, but am a very experienced computer user, but quite inexperienced when it comes to old-fashioned Ubuntu-style command-line interfaces. I have two questions:

1. I have installed Ubuntu on my wife's laptop, hoping it might be better/faster/leaner than Windows Vista. She is less computer literate than me, and has never typed a command since she threw out her MS-DOS machine many many years ago. In practice, once I've managed to set up (if I manage to set up!) her machine, will she be able to use it for normal day-to-day office/internet/email tasks without ever having to go near the terminal? It looks like installing even the smallest program requires way, way more than the 'double-click the installer' that Windows/Mac users enjoy.

2. How can I log in as 'root' or whatever I have to do, so that while I'm setting up the machine, I can just drag & drop files and not have to revert to the 1970s style terminal / sudo cp... just to copy or move files? I hate being told 'permission denied' - surely the USER tells the computer what to do, not the other way round?! I know it's possible to screw up the whole OS by deleting the wrong file, but I'm more than happy to take this risk. I can't even open a file using Text Edit without the silly permission denied thing!:confused:

I appreciate that Ubuntu is free and under constant development, but I was unaware that it really is not a finished GUI/OS and, as much as I hate to say it,  in no way can replace Windows for an average user. I use MacOSX on a day-to-day basis, and using Vista and Ubuntu make me realise just how good it is! (As it *should* be for the MASSIVE premium that Apple forces people to pay for its machines!)

Here's hoping my Ubuntu relationship can improve - I love the Ubuntu/Linux philosophy:)

Paul

So you are asking help, while bashing ubuntu and it's userbase at the same time?

You may think you are a very advanced user on other Os's, but your new to linux. You just don't know how to do things.

Did you even look around the menu's?  I guess you didn't see "add/remove" or "synaptic package manager".

2. Telling users how to log in as root isn't allow by the guidelines. And you obviously shouldn't do so.

Learn to use sudo (or gksudo).

As for the file managing, you could use 

```
gksudo nautilus --no-desktop
```

Just don't remove or rename, move, ... files you don't know while being in there.

--

Also, if I have to use windows I feel lost because there is no (real) command line interface. 

The CLI is the most power part of Ubuntu.

---

### Post by Atomic Dog on 2008-07-28
Billgoldberg, I don't think he was bashing as much as venting from frustration.  As you know, linux can be daunting for new users at first.

Bill's advice is right about being careful about doing file manipulation while running nautilus as root.  You can cause some problems for yourself as I learned myself the hard way.

Now is it really against the rules to tell somebody how to become root in a shell?  That seems preposterous.

---

### Post by ilrudie on 2008-07-28
> **newbuntuxx said:**
> 
```
sudo nautilus
```

Don't do this.  Use gksudo as mentioned above.

Also there is no need to set a root password in Ubuntu.  If you want to become the root user from the terminal use
```
sudo su -
```or
```
sudo bash
```Installing applications in Ubuntu is the easiest of any OS I have experienced.  aptitude, synaptic and add/remove all find all the files you need and get them for you.  Of course its different from windows where you find the application online, download it (hopefully from a trusted site), click it, break a dependency, and then get to go on a treasure hunt for dlls only to find out its a trial version with limited functionality.  Different isn't worse.  Its just different.  Give it a try.  Afterall its impossible to be better than something without being different.  Ubuntu strives to be better for its users than any other OS so it will be different in many ways.

Regarding your opinion that Ubuntu is not finished I would have to agree.  It is constantly evolving and getting better nearly every day.  No OS is truly finished.    OSX is nicely polished but not finished.  They release updates and redo applications regularly.  Every release tweaks the interface a bit.  Windows releases updates all the time as well.  Show me an OS thats "finished" and I'll show you an OS thats no longer supported.  I too have a mac and although I was in love with it when I had only windows to compare it to I have found Ubuntu to be in many ways supperior.  The interface is not as pretty but the OS works better IMO (plus I don't like dropping my hard earned dollars just to get the new interface tweaks and apps when they release a new OS).

Good luck with your Ubuntu experiments and try to remember that different doesn't mean worse.

P.S.
> **Atomic Dog said:**
> 
Now is it really against the rules to tell somebody how to become root in a shell?  That seems preposterous.
I believe the restriction is against tutorials on how to enable graphical root logins/autologin.  I don't think there are rules against telling someone how to get a root shell or how to su to root.

---

### Post by snowpine on 2008-07-28
> **ilrudie said:**
> Regarding your opinion that Ubuntu is not finished I would have to agree.  It is constantly evolving and getting better nearly every day.  No OS is truly finished.    OSX is nicely polished but not finished.  They release updates and redo applications regularly.  Every release tweaks the interface a bit.  Windows releases updates all the time as well.  Show me an OS thats "finished" and I'll show you an OS thats no longer supported.  

This is a great point, and I will add my frustration with Windows when I go to shut down the computer and it says "Please wait... installing important updates." What updates are you installing and when exactly did I ask you to do that? Whereas with Ubuntu, I can see exactly what the updates are and install (or not) when I want to.

---

### Post by decoherence on 2008-07-28
i'm a mac admin. so as long as we're venting frustrations...

1. why don't all my users show up in Workgroup Manager?
2. why doesn't removing the writable bit from a preference cause that preference to be... uh... not writable?
3. why does iMovie 08 insist on putting crap in the root level of the drive?

and most importantly

4. WHY CAN'T I CHANGE ANY OF THESE THINGS???

Yeah, Macs are good. But they're only *better* if you're doing video editing or need Adobe CS3. Beyond that is just a matter of experience.

That said, I would like it as well if Nautilus prompted you for a password when you tried to drag something in to a folder you don't have permissions for. The infrastructure for doing this is already in place (Policykit and GIO) so we will hopefully see features soon and it will make Ubuntu much friendlier for folks like the OP.

---

### Post by nothingspecial on 2008-07-28
My wife uses our Ubuntu pc everyday for email, ipod, facebook ect ect ect;  and wouldn`t even know how to open a terminal. She`s a much more experienced computer user than me (or was when we got this damned thing)!

---

### Post by a0u on 2008-07-28
> **hellopaul said:**
> 
How can I log in as 'root' or whatever I have to do
Does Mac OS X let you do that?   With Ubuntu (as with all other responsible Unix-like systems), it is [never recommended that you log in as root]("https://help.ubuntu.com/community/RootSudo") - in fact, the root account is disabled by default in Ubuntu.

> **hellopaul said:**
> 
I am new to Ubuntu, but am a very experienced computer user, but quite inexperienced when it comes to old-fashioned Ubuntu-style command-line interfaces


And while we are on the subject of the command line, might I respectfully direct your attention to one interesting blog post: [10 Reasons Why the Command Line is More User-Friendly than the Desktop]("http://penguinpetes.com/b2evo/index.php?title=10_reasons_why_the_command_line_is_more"). :)

---

### Post by steveneddy on 2008-07-28
You just need to learn the Linux way.

Most can be done in GUI, but if you need to use CLI, then just copy and paste.

In Linux, just highlight or select the word or phrase you would like to paste and go to the application tat you want to paste into, then middle mouse click (the scroll wheel). Easy.

Look at the first two links in my sig. Those will help you more than you could imagine.

---

### Post by Brightbelt on 2008-07-28
I'm not new to Ubuntu, but I understand some people don't want to have to deal with the command line. 

Do all computer users design webs?:no - Write Code?:no - Use Photoshop?:no.

So let's be realistic and understand there are many levels of use involved - this is the scenario now whether we like or not. Linux benefits from understanding this and they obviously do understand it to a great degree already or there wouldn't be things like Add/Remove and Synaptic. And saying stuff like "well, my sister/mother/grandmother uses the command line blah blah blah" doesn't really do anything very constructive. Just my opinion there. 

So here are my tips as a GUI-sympathetic user:

1) When following a HOWTO or tutorial, always read it to the very end. Why? Because after telling you all the command line procedures, and all the stuff you'll have to do in the terminal, at the very bottom, they will often give you the EASY alternative there at the very end. Look carefully, since it's often a half of a sentence like ...

> ...or if you prefer you can download the Deb file here and double-click to install it.

2) From time to time, you will encounter complex instructions about a program you don't have. About where to download it, how to compile it or install it at the command line. ALWAYS  CHECK THE SYNAPTIC PACKAGE MANAGER, EVEN IF YOUR HELPER OR ONLINE HOWTO OR TUTORIAL DOES NOT MENTION IT. I have found more answers (and more programs available) that way than I ever thought I would.

3) The Synaptic Package Manager offers more graphics alternatives than you may realize. Doing a search for 'GTK themes' and 'Xfce-gtk' will bring up a lot of graphics choices. 

4) Things in Linux often require a second push. If something doesn't install or gets quirky right away, ALWAYS try again. Linux is more flexible in this way than we think.

Well that's it for starters.

Frank B.

---

