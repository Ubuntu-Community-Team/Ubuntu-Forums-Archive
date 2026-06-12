---
title: "Configuring Startup (Xubuntu 12.04)"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by manikinxvx on 2013-08-29
As an absolute beginner, I have had many successes with my migration to Linux (Xubuntu 12.04) after years of Mac and Windows familiarity. There are, however, items which are giving me difficulty with configuration of the startup process/procedures of my system. I guess I'll take them in order, of sorts.

1) Is there a way to configure auto-login for a specific user? I know I don't have to enter my pw for every login, but how might I bypass the login screen entirely, unless I choose "Log Out" [to change user] instead of "Shut Down"?

2) I have two external drives, but they don't auto-mount at startup. This, despite having the options selected in Removable Drives and Media to "Mount removable drives when hot-plugged" as well as to "Mount removable media when inserted".

3) I have attempted adding Mozilla Thunderbird to the Application Autostart tab of Session and Startup, with addition of the command "thunderbird start", but I have an inkling that I am simply missing something from this command to make it work. Dropbox uses "dropbox start -i"; is this what should be entered for Thunderbird, or something else? I have considered attempting this... but I don't want to break anything. I'd rather learn the proper information rather than *just* going with trial-and-error.

4) Wine... is there a thread or preferred-tutorial for configuring Wine? I have no problems running simple, seemingly single-file applications (eg: Notepad), but installation of apps which require further configuration fail seemingly ever time. Photoscape, is one notable example. [I know Notepad is un-necessary and I commonly use Leafpad, I was just noting that some work and some do not.]

If there are existing thread covering or relating to these topic, I apologize for these inquiries and would request direction to them. 


Thanks to all, in advance, who take the time to read this post.
--M

---

### Post by JKyleOKC on 2013-08-29
I don't have answers to all your questions, but can help with a few.

Autologin is easy; open a terminal and type the command "gksudo thunar" which will ask for your password. Type it in; you won't see any indication that it's being accepted, but when you finish and hit Enter, a copy of the file manager should show up together with a warning that you are in dangerous territory. Navigate to the /etc/lightdm directory and open it. You should see several files, including "lightdm.conf" among them. Double-click that one to open it for editing, and add a line "autologin-user=manikinxvx" (if manikinxvx is the name of the user you want to log in automatically). Then save the file, and that user will automatically log in at the next reboot. Close Thunar as soon as you are done, since it's in a risky condition.

As for automatically mounting the external drives, be absolutely sure you want to set it up because if you do, and then unplug either of them, you'll get error messages at boot time. The way to set it up is to add them to the /etc/fstab file; I can't give you detailed instructions until you describe the drives in a bit more detail. Specifically, are they formatted for Windows or for OSX, and do you want to be able to write to them? If for Windows, is it FAT, FAT32, or NTFS? Also do you want them to be accessible to all users, or only to one? All of this can be configured in the fstab file, and some of it is absolutely necessary.

EDIT: Those options for automounting that you've checked are triggered when you connect the drives after the system is up and running, only. Thus they have no effect at boot time. You could pull the plug on each, then put it back in, and they should then mount automatically. For mounting at boot time, the /etc/fstab file entries are needed.

I've not tried to autostart Thunderbird, but there's no guarantee at all that the method dropbox uses will work with any other application -- and usually, such application-specific modifiers don't work with much of anything else. There may be something in the Tbird help files on line to show their recommended way to do it, if it has one at all. If it does not, you could put together a simple shell script (think Windows batch file, but shell scripts are much more powerful) to launch it, and then add the script to the Autostart list via Applications->Settings->Settings Manager->Session and Startup->Application Autostart.

And I can't help at all with WINE.

Hope this helps a bit!

---

### Post by Elfy on 2013-08-29
Thunderbird will start without appending anything

Applications->Settings->Settings Manager->Session and Startup->Application Autostart

click add - fill in the boxes - command for thunderbird is thunderbird

---

### Post by manikinxvx on 2013-08-29
JKyleOKC,
lightdm.conf already did contain the line "autologin-user=..." Oh well, that's not that big of a deal if I just have to click "Login" one time. Maybe I'm just being too finicky.

The external drives are: /dev/sdb (FAT) and /dev/sdc (FAT)


Elfy,
Thanks for that tip with just having "thunderbird" for the command. That worked perfectly.

---

### Post by Toz on 2013-08-29
With respect to wine, have a look at [this wiki entry]("https://help.ubuntu.com/community/Wine"). You also might want to have a look at [PlayOnLinux]("http://www.playonlinux.com") as it is a nice graphical front-end to wine that you might find useful. Unfortunately, I don't believe its in the official Ubuntu repositories for 12.04, but installation instructions are available on their website.

---

### Post by JKyleOKC on 2013-08-29
I forgot to ask one more essential question: What directories are in your /media directory? you can use the command "ls -l /media >mmm.txt" from a terminal to get the list copied into a text file in your home directory named "mmm.txt" and then copy and paste the content of that file into a reply here. After you paste it into the reply, before sending it, highlight the whole content of the file and click on the "quote" icon of the toolbar. If you're using the "quick reply" capability it will be the one at the far right of the toolbar. If not, it will be the one that looks like a comic strip's "speech balloon." We need to know what's there, and if it's empty I'll include instructions for creating mount points for both drives; tell me what you want them named, or I can just call them "sdb" and "sdc" if you like...

---

### Post by Jonathan Precise on 2013-08-29
> **manikinxvx said:**
> As an absolute beginner, I have had many successes with my migration to Linux (Xubuntu 12.04) after years of Mac and Windows familiarity. There are, however, items which are giving me difficulty with configuration of the startup process/procedures of my system. I guess I'll take them in order, of sorts.

1) Is there a way to configure auto-login for a specific user? I know I don't have to enter my pw for every login, but how might I bypass the login screen entirely, unless I choose "Log Out" [to change user] instead of "Shut Down"?

2) I have two external drives, but they don't auto-mount at startup. This, despite having the options selected in Removable Drives and Media to "Mount removable drives when hot-plugged" as well as to "Mount removable media when inserted".

3) I have attempted adding Mozilla Thunderbird to the Application Autostart tab of Session and Startup, with addition of the command "thunderbird start", but I have an inkling that I am simply missing something from this command to make it work. Dropbox uses "dropbox start -i"; is this what should be entered for Thunderbird, or something else? I have considered attempting this... but I don't want to break anything. I'd rather learn the proper information rather than *just* going with trial-and-error.

4) Wine... is there a thread or preferred-tutorial for configuring Wine? I have no problems running simple, seemingly single-file applications (eg: Notepad), but installation of apps which require further configuration fail seemingly ever time. Photoscape, is one notable example. [I know Notepad is un-necessary and I commonly use Leafpad, I was just noting that some work and some do not.]

If there are existing thread covering or relating to these topic, I apologize for these inquiries and would request direction to them. 


Thanks to all, in advance, who take the time to read this post.
--M

I'm not too familiar with Xubuntu. However, If you can go to user accounts, The section that says "Login Automatically", set it to ON.:)

As for auto-mount, the options you checked just reflect:

"Mount all external hard-drives and USB's when plugged in **_AFTER_** Xubuntu starts:( (this was generally when the side of the computer would heat-up, thus having the name hot-plugging)"

To do that, add a line to fstab. Note that if they are not connected at start-up, you may get error messages (it happened to me once).

For wine, post them [here]("http://ubuntuforums.org/forumdisplay.php?f=313").

---

### Post by manikinxvx on 2013-08-31
JKyleOKC,
I will perform the "ls -l /media >mmm.txt" later today and reply with the resulting output.

Jonathan Precise,
If only going into "Accounts" were as simple in Xubuntu as with other operating systems: [http://www.urbanpeasant.net/photodump/Screenshot.png](http://www.urbanpeasant.net/photodump/Screenshot.png) I *did* go into Sessions and Startup and reviewed that tab; no luck: [http://www.urbanpeasant.net/photodump/ScreenshotII.png](http://www.urbanpeasant.net/photodump/ScreenshotII.png)

---

### Post by JKyleOKC on 2013-08-31
> **manikinxvx said:**
> If only going into "Accounts" were as simple in Xubuntu as with other operating systems: [http://www.urbanpeasant.net/photodump/Screenshot.png](http://www.urbanpeasant.net/photodump/Screenshot.png) I *did* go into Sessions and Startup and reviewed that tab; no luck: [http://www.urbanpeasant.net/photodump/ScreenshotII.png](http://www.urbanpeasant.net/photodump/ScreenshotII.png)You got halfway there, just stopped too soon. On the "Sessions and Startup" page, click the tab at the top labelled "Application Autostart" and you'll get a new dialog that lists all the applications currently set up for autostarting. Right-click anywhere in that list and a pop-up menu will appear, with an "Add" entry. Click that entry and you'll get the add dialog...

I agree that it could be made a bit simpler, but since the *buntu systems are far more customizable than most others, it'll never be as simple as systems that don't offer so many choices.

---

### Post by Jonathan Precise on 2013-08-31
> **JKyleOKC said:**
> You got halfway there, just stopped too soon. On the "Sessions and Startup" page, click the tab at the top labelled "Application Autostart" and you'll get a new dialog that lists all the applications currently set up for autostarting. Right-click anywhere in that list and a pop-up menu will appear, with an "Add" entry. Click that entry and you'll get the add dialog...

I agree that it could be made a bit simpler, but since the *buntu systems are far more customizable than most others, it'll never be as simple as systems that don't offer so many choices.

I was referring to the auto-login.

---

### Post by Jonathan Precise on 2013-08-31
> **manikinxvx said:**
> JKyleOKC,
I will perform the "ls -l /media >mmm.txt" later today and reply with the resulting output.

Jonathan Precise,
If only going into "Accounts" were as simple in Xubuntu as with other operating systems: [http://www.urbanpeasant.net/photodump/Screenshot.png](http://www.urbanpeasant.net/photodump/Screenshot.png) I *did* go into Sessions and Startup and reviewed that tab; no luck: [http://www.urbanpeasant.net/photodump/ScreenshotII.png](http://www.urbanpeasant.net/photodump/ScreenshotII.png)

Once again, I'm not too familiar with Xubuntu. However, try this next solution:

Go to the [FONT=courier new]Session[/FONT] tab. There should be something about auto-login. If not, go to the [FONT=courier new]advanced[/FONT] tab, and try again.

---

### Post by manikinxvx on 2013-09-01
I resolved the issue of Thunderbird starting with the tip from Elfy. Auto-login is the only remaining issue from that inquiry.

Today (well, as of yesterday) only one of my external drives is working properly. Anyway... the one that is working is listed in terminal as: drwx------ 8 manikinxvx manikinxvx 16384 Sep  1 07:13 sdb

---

### Post by Jonathan Precise on 2013-09-01
Please read my last post (for auto-login).

---

### Post by JKyleOKC on 2013-09-01
Back at post #4 you said "*lightdm.conf already did contain the line "autologin-user=..." Oh well, that's not that big of a deal if I just have to click "Login" one time. Maybe I'm just being too finicky.*"

Post the output from "cat /etc/lightdm/lightdm.conf" here so that we can see it; if you want to hide your user name, replace it with "xxx" but **don't** change anything else. If there's nothing after the "autologin-user=" on that line, it's **cancelling** autologin rather than enabling it, and if the line begins with "#" then it has been tagged as just a comment and will have no effect. That's **all** that I have had to do here to enable autologin on two different Xubuntu 12.04 systems.

The autostart items listed on the "Session" tab of "Sessions and Startup" in the Settings Manager aren't executed until **after** you have logged in, so nothing you do there can have any effect on autologin.

EDIT: I agree with you that it would be much easier if it were added to the individual user settings; as I recall, it WAS there in some older versions. However the display manager, lightdm, handles login and is a completely different package from the one that contains user settings, so this is an example of the price we have to pay for having so many options.

You might try changing from lightdm to gdm, which is what the older versions used. It's fairly easy to do. I tried it because of other issues I had with lightdm, but changed back almost immediately...

---

### Post by manikinxvx on 2013-09-02
The output from lightdm.conf is as follows:

[SeatDefaults]
autologin-guest=false
autologin-user=manikinxvx
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=xubuntu

---

### Post by JKyleOKC on 2013-09-03
Here's mine, which works.> [SeatDefaults]
autologin-user=jk
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
allow-guest=false
 I'm don't know if those additional lines in yours are what's keeping it from doing the same, but you might try putting the "#" at the front of each to make it look like this (adding the allow-guest line, too), saving it, then re-booting, to see.> [SeatDefaults]
#autologin-guest=false
autologin-user=manikinxvx
#autologin-user-timeout=0
#autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
allow-guest=false 

---

### Post by manikinxvx on 2013-09-03
> **JKyleOKC said:**
> Here's mine, which works. I don't know if those additional lines in yours are what's keeping it from doing the same, but you might try putting the "#" at the front of each to make it look like this (adding the allow-guest line, too), saving it, then re-booting, to see.

... well... I won't be trying that again in the future.

---

### Post by SpazCool on 2013-09-06
Ah thank God, just the thread I needed.

---

### Post by manikinxvx on 2013-09-09
I marked this as [Solved] even though... well, it's only "kinda" solved. I'll skip some of these things until I increase my own knowledge. Thank you to those who offered advise and assistance.

---

