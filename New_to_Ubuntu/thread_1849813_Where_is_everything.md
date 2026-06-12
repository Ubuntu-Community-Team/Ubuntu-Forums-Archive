---
title: "Where is everything?"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by flitter on 2011-09-25
At my job I have received a PC from state Job Service office. We are becoming a satellite station. The computer has Ubuntu installed. There is pretty wallpaper and 1 icon for the software job service uses. There is a thin white line up top that shows the time. The computer is not online yet so I have not poked around much.
 
First and foremost, how do I shut it down properly? Then, where is everything else. I don't know what version of Ubuntu I have, or anything about the computer.
 
Help!! How do I find anything about this box?
 
I have done some reading on these forums and I do not understand any of the jargon. I know Windows, period.
 
Thanks.

---

### Post by arochester on 2011-09-25
On the dektop,try a **RIGHT** click and see if you get a menu.

---

### Post by Manyette on 2011-09-25
Shutdown: Top right corner of the screen, left click for shutdown options.
Programs: Top left corner of the screen, programs and options.

---

### Post by Paqman on 2011-09-25
> **flitter said:**
> 
First and foremost, how do I shut it down properly?

ON most machines you can just hit the power button and it'll pop up a menu asking what you want to do (shut down, suspend, etc)

> 
Then, where is everything else. I don't know what version of Ubuntu I have, or anything about the computer.


It's a bit hard to know what version you've got, and it can make quite a big difference. Next to where it shows the time it probably also has icons that show whether you're connected and so on. If it has wifi you can click on the network icon to pick a wifi network to connect to.

If the machine has a Windows key, try hitting that and see if you get a dash pop up. If so you can search for and browse applications and folder through that. Alternatively, try moving your cursor to the top and/or left and see if anything pops up.

Above all, don't sweat it. Linux is no more difficult to use than Windows, it's just different. There's plenty of people here who can help you with anything you need.

---

### Post by haqking on 2011-09-25
> **flitter said:**
> At my job I have received a PC from state Job Service office. We are becoming a satellite station. The computer has Ubuntu installed. There is pretty wallpaper and 1 icon for the software job service uses. There is a thin white line up top that shows the time. The computer is not online yet so I have not poked around much.
 
First and foremost, how do I shut it down properly? Then, where is everything else. I don't know what version of Ubuntu I have, or anything about the computer.
 
Help!! How do I find anything about this box?
 
I have done some reading on these forums and I do not understand any of the jargon. I know Windows, period.
 
Thanks.

It maybe kiosked, i expect if it has been given to you by your employer then they will train you on it, or there is a manual for your installation somewhere.

---

### Post by Paddy Landau on 2011-09-25
The latest versions of Ubuntu are a bit different from the previous ones. It would help to know which version.

Do this:

[LIST=1]
[*]Press *Ctrl-Alt-T*. You should get a new window with a flashing cursor.
[*]Type the following and press Enter:```
lsb_release -cidr
```
[*]Let us know what you see. It will look something like this:```
Distributor ID: Ubuntu
Description:    Ubuntu 10.04.3 LTS
Release:        10.04
Codename:       lucid
```
[*](You can close the window afterwards.)
[/LIST]

---

### Post by flitter on 2011-09-26
I got a menu. Create folder, create launcher, create document>No templates installed, empty file, organize desktop by name, keep aligned (checked), paste (grayed out), change desktop background.
 
I clicked on Create Launcher and got:
Type: application, application in terminal, location
Name: empty box
Command: empty box>Browse>bin, boot, cdrom, dev, etc, home, lib. lost & found, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var, initrad.img, vm linuz
Comment: empty box
 
Ctrl-Alt-T did nothing. There is nothing in either upper corner to click on.  There are no icons except the job service software package which I cannot access until we are online with it.
 
There will be no training.  We are a low budget church based charity and this is one of our community outreach programs. Our job service office has closed.  This computer will allow people to search job listings, apply for unemployment, find job training, etc. from our computer lab.
 
I am lost and there is no one to ask.

---

### Post by 3rdalbum on 2011-09-27
From your description it sounds like the machine has been customised to only work as a "kiosk" - basically, to access ONLY your job search program.

However, the right-click menu will allow you to do pretty much anything you want, if you know how to use it properly. Whoever "kiosked" the computer didn't do a good enough job.

If you create a launcher and set the 'command' as "gksudo halt" you will be able to shut down the computer from the launcher you created. Set the name to "Shut Down" or something like that.

If you want a web browser you *might* be able to create a launcher with the command "firefox".

If you want to access the terminal, you can try either of these:

```
gnome-terminal
```

or

```
xterm
```

From this you can do pretty much anything, possibly even install new software once you've got that internet connection running.

---

### Post by dFlyer on 2011-09-27
I would go to your employer and ask him for linux training. To shut down the computer depend on what version of ubuntu your using. If you have a more current version you should find an icon all the way to the right of the top line your referring to that has a button symbol. Just press it and it should give you a shut down option along with several other options.

---

### Post by flitter on 2011-09-27
I am asking here, how do I find out what version I have.  There are NO icons on the desktop except the software for job service.
 
My employer has nothing to do with this.  It is a charity and I am a volunteer.  The job service office is 50 miles away and no one there seems concerned about the OS. The people with whom I have met so far don't even know what Ubuntu is.  
 
All of this may be unnecessary if this computer behaves itself. I will be the only one available to troubleshoot when problems occur.  I am clueless.

---

### Post by flitter on 2011-09-27
Can you translate "terminal" into windows-speak. I don't understand the term.
 
Please forgive my ignorance.  This is all greek to me.

---

### Post by haqking on 2011-09-27
> **flitter said:**
> Can you translate "terminal" into windows-speak. I don't understand the term.
 
Please forgive my ignorance.  This is all greek to me.

there is no windows speak, it is not windows ;-)

to access terminal, press ctrl+alt+t or drop to console with ctrl+alt+f1 and ctrl+alt+f7 to get back to gui

or there should be a link to it in the applications menu

---

### Post by stmiller on 2011-09-27
Terminal is like the Windows Command Prompt. A 'DOS'-like box where you can type text commands.


[[IMG]http://i.imgur.com/iXi5C.png[/IMG]](http://imgur.com/iXi5C)

---

### Post by flitter on 2011-09-27
Oh, I give up. Uncle uncle.  
 
I do not understand anything you just said.
 
nevermind.

---

### Post by flitter on 2011-09-27
I see! thanks.  Ctrl Alt t did not work.  I will try the others before I give up.

---

### Post by Basher101 on 2011-09-27
you should not give up on ubuntu, it is a great os! can you make a screenshot of your desktop with the print button? just save it to the desktop and upload it in your next post. By the looks of the desktop environment (e.g. your interface) we get alot of information and could determine by it what version you might have.

---

### Post by Phateless on 2011-09-27
I'm so glad I stumbled on this thread so I don't have to post it myself. I'm an android fanatic so gnome already feels like home to me. I should have checked this out years ago.  :D

---

### Post by The Cog on 2011-09-27
You say there is a thin white line at the top. I wonder if it does anything if you hold the mouse over it. Maybe it's a taskbar configured for auto-hide?

---

### Post by matt_symes on 2011-09-27
Hi

Can you take a screen shot with a camera or a mobile phone and upload it here on the forum as an attachment.

We can help you and if we can see what is on your screen then that would be a start.

Kind regards

---

### Post by flitter on 2011-09-27
There is nothing on the screen. That's the problem. At the top just right of center is a very thin white line. I click on it and it shows the time and will show appointments or calendar entries.  I am not at work now so am trying to remember. There is the icon for the "kiosked" software. I can right click anywhere and get the abovementioned menu.  
 
Probably I could get a screen shot but there is nowhere to go with it after I get it.
 
Will try again tomorrow afternoon.

---

### Post by haqking on 2011-09-27
> **flitter said:**
> There is nothing on the screen. That's the problem. At the top just right of center is a very thin white line. I click on it and it shows the time and will show appointments or calendar entries.  I am not at work now so am trying to remember. There is the icon for the "**kiosked**" software. I can right click anywhere and get the abovementioned menu.  
 
Probably I could get a screen shot but there is nowhere to go with it after I get it.
 
Will try again tomorrow afternoon.

so it is kiosked then, which is what as mentioned a few times.

That means someone somewhere has set it up so that you have limited access to the system.

You need to speak to whoever gave you the machine, who set it up etc.

---

### Post by flitter on 2011-09-28
The lightbulb has gone on, guys.  This is a public computer. It is not meant to be fiddled with! Anyone could do anything to it.  Problem solved. I will not be responsible for problem solving on this one.
 
Thank you all for the input.

---

