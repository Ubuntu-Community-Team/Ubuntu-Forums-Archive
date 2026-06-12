---
title: "Gmail integration with Ubuntu and Autostart"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-20
Hey,

I am pretty amazed with the Chat integration into the operating system. But even here, I have to start Chat on ubuntu start, or I wont be loged in. I wonder if I could auto connect upon restart.

Same goes with Email. Mozilla Thungerbird seems neat, but it should auto start as well.  

Also I am not sure if Thuderbird is the best choice for gmail.  Surely it recognizes it, but unlike web gmail, it doesn't show me the content of inbox.

Instead it shows everything, even though I have filters in place to move certain emails to other label/sub folders.

Thunderbird simply doesn't give me the same experience as in web.

What do you guys use for Gmail integration into Ubuntu?

Thanks,

---

### Post by Lynceus on 2012-05-20
I use Thunderbird too and i like it, i haven't tried out the chat function.
Auto start would be nice, i hope someone can help us with that.

---

### Post by pfindan on 2012-05-20
Just add Thuderbird to your startup programs. 

Go to unity dash type in "startup" and add thunderbird to the list. (command should be ' thunderbird ' if memory serves me right )

Good luck ! Welcome to Ubuntu!

---

### Post by Lynceus on 2012-05-20
> **pfindan said:**
> Just add Thuderbird to your startup programs. 

Go to unity dash type in "startup" and add thunderbird to the list. (command should be ' thunderbird ' if memory serves me right )

Good luck ! Welcome to Ubuntu!

I tried it out and it works, on startup Thunderbird opens (not in the background).
 But my wifi could not make a connection so i disabled it and did a reboot.

Still thanks for the help

---

### Post by joetait on 2012-05-20
> **Lynceus said:**
> I tried it out and it works, on startup Thunderbird opens (not in the background).
 But my wifi could not make a connection so i disabled it and did a reboot.

Still thanks for the help

I don't know about how to get it to start in background, but I used to have to thunderbird start in the background exactly like that and had no issues with wifi connection. Did you try it a couple of times?

---

### Post by Houmie on 2012-05-20
Thanks for your replies. I will try that.

Btw do you recommend using Pop3 or imap for connecting to Gmail with Thunderbird?

---

### Post by mastablasta on 2012-05-20
> **Houmie said:**
> 
Btw do you recommend using Pop3 or imap for connecting to Gmail with Thunderbird?

IMAP.

btw i do not have any issues you mentioned. using TB on Ubutnu linux, Debian Linux and WindowsXP with Gmail (among other servers...)

---

### Post by guimaster on 2012-05-24
Canonical is not going to succeed in obtaining mass adoption until they fix this Auto-Start problem. With every single release of Ubuntu, new users need to ask this same old question, and older users who expected this to be fixed by now can't figure out why it doesn't work the way it ought to. New users _do not know_ how to configure a program - period - much less how to configure a program to auto-start.

:confused:

When you install a program, it should auto-start by default, or a question should be asked upon installation if the program should auto-start. Also, Empathy and Thunderbird should auto-start minimized by default, without anyone having to configure anything. 

At the absolute minimum, Empathy and Thunderbird should auto-start because they are part of the panel and the panel should just "work" right after install. I can just imagine how annoyed a new user would be having to click "Available" every time they start the computer in order to get Empathy to log in.

---

### Post by mastablasta on 2012-05-24
> **guimaster said:**
>  
When you install a program, it should auto-start by default, or a question should be asked upon installation if the program should auto-start. Also, Empathy and Thunderbird should auto-start minimized by default, without anyone having to configure anything. 
 .
 no it shouldn't . it never does in any OS.
i don't need it always on and do not want it to autostrat. same goes for large majority of other progs.
 
they would clog up the ram for no good reason.

---

### Post by MadmanRB on 2012-05-24
Auto starting thunderbird by default sounds like a terrible idea to me, sorry.
As not everyone even knows what an Email application is in the first place as many still use email services such as AOL and hotmail in a browser as opposed to using an app.
Same with empathy too, sure it sounds nice for your convenience but not for those of us who dont use IM clients.
I avoid them personally
And really as pointed out above no OS does this by default even windows

---

### Post by NikTh on 2012-05-24
> **Houmie said:**
> 

What do you guys use for Gmail integration into Ubuntu?

Thanks,

I use UnityMail. You must add an external repository to install it. Search for **mytia57 ppa** in Launchpad
;)

---

### Post by xedi on 2012-05-24
> **guimaster said:**
> Canonical is not going to succeed in obtaining mass adoption until they fix this Auto-Start problem. With every single release of Ubuntu, new users need to ask this same old question, and older users who expected this to be fixed by now can't figure out why it doesn't work the way it ought to. New users _do not know_ how to configure a program - period - much less how to configure a program to auto-start.

:confused:

When you install a program, it should auto-start by default, or a question should be asked upon installation if the program should auto-start. Also, Empathy and Thunderbird should auto-start minimized by default, without anyone having to configure anything. 

At the absolute minimum, Empathy and Thunderbird should auto-start because they are part of the panel and the panel should just "work" right after install. I can just imagine how annoyed a new user would be having to click "Available" every time they start the computer in order to get Empathy to log in.

This is a terrible idea IMO, such kind of default configurations are making using Windows a horrible experience: "Every" program is so arrogant that it installs itself everywhere, puts a shortcut everywhere and autostarts so that after a while your windows system is just trash which needs hours to boot.

Besides that, it is so easy to set programs to autostart in Ubuntu, that it's not a huge hurdle to set it up yourself even as beginner.

> Also I am not sure if Thuderbird is the best choice for gmail. Surely it recognizes it, but unlike web gmail, it doesn't show me the content of inbox.

Instead it shows everything, even though I have filters in place to move certain emails to other label/sub folders.

In my case Thunderbird does that and you can find the subfolders in the profile section, so it's not in the "normal" inbox but under it where you have the gmail profile. E.g. I have sms backup on my phone which records sms and call logs in gmail but they don't appear in my standard inbox but in the subfolder under the gmail profile thingy.

---

### Post by Houmie on 2012-05-24
> **xedi said:**
> This is a terrible idea IMO, such kind of default configurations makes Windows a horrible experience to use: "Every" program is so arrogant that it installs itself everywhere, puts a shortcut everywhere and autostarts so that after a while your windows system is just trash which needs hours to boot.

Besides that, it is so easy to set programs to autostart in Ubuntu, that it's not a huge hurdle to set it up yourself even as beginner.



In my case Thunderbird does that and you can find the subfolders in the profile section, so it's not in the "normal" inbox but under it where you have the gmail profile. E.g. I have sms backup on my phone which records sms and call logs in gmail but they don't appear in my standard inbox but in the subfolder under the gmail profile thingy.

Too be honest I don't think its a terrible idea. It is great having a choice.  When I start the PC I want email & chat ready. Dont want to start everything myself.

It would have been nice having the option of auto start + minimized.

I just tried adding thunderbird to autostart, but don't find the program. I have to browse to it and have no idea where it is.  And I think minimized is not even supported right?

---

### Post by xedi on 2012-05-24
> **Houmie said:**
> 

It would have been nice having the option of auto start + minimized.

I just tried adding thunderbird to autostart, but don't find the program. I have to browse to it and have no idea where it is.  And I think minimized is not even supported right?

I actually agree that it is a good option to have but guimaster was talking about that every program should autostart by default or at least the panel programs, which I think would make Ubuntu so bloated that nobody would want it. Not everybody uses thunderbird or empathy, or not all the time, why should it be then the default that those programs start?

---

### Post by lile001 on 2012-05-24
To get back to the OP's idea, what would be the best way to use GMAIL integration:

Gmail with Thunderbird?

Gmail with Evolution?

Which is best, or is this just a matter of preference?

IMAP or POP?  ( I don't really even know what these are, I just know they are options)

Does Gmail's calendar integrate with the calendars on these programs?  Contacts?

---

### Post by mastablasta on 2012-05-25
as i mentioned already i use Thunderbird for gmail with lightning extension for calendar. i haven't checked if this calendar integrates with googles but email works prefectly with IMAP. i haven't tried pop with gmail.
 
imap and pop well basically for user the biggest difference is:
IMAP - e-mail stays on server and is not downloaded to your computer. which means you can access it from multiple maschines (portable thuderbid ;-) )  bacially a user sees an image of what is on server.
POP - e-mail is downladed to users computer on connection. so the emails are actually stored localy. in this case you couldn't access them later from another mashicne or via browser, since they are only on local mashicne. sometimes this can be handy (e.g. mail server has a limit of 100MB yet for example you get 150MB of mail a month...). since you always download it the limit would not be reached (well unless someone sends a file larger than 100MB)

---

### Post by stinkeye on 2012-05-25
I use gmail with POP.
I check my gmail using a perl script and send the results to notify-send ,play a sound and display on the desktop using conky.
The new mail notification stays on the desktop until I fetch the new mail using
opera's built in mail client.

---

### Post by guimaster on 2012-05-26
> **MadmanRB said:**
> Auto starting thunderbird by default sounds like a terrible idea to me, sorry.
As not everyone even knows what an Email application is in the first place as many still use email services such as AOL and hotmail in a browser as opposed to using an app.
Same with empathy too, sure it sounds nice for your convenience but not for those of us who dont use IM clients.
I avoid them personally
And really as pointed out above no OS does this by default even windows

If you install MSN Messenger in Windows, or any other Messenger program, it will auto start by default whether you like it or not.

> **xedi said:**
> I actually agree that it is a good option to have but guimaster was talking about that every program should autostart by default or at least the panel programs, which I think would make Ubuntu so bloated that nobody would want it. Not everybody uses thunderbird or empathy, or not all the time, why should it be then the default that those programs start?

I'm surprised by the responses I am getting. How many bug reports have been filled regarding this issue?

Empathy should definitely log in on startup. Or at least with the new Messaging Menu options it should default to the setting you used the last time. If you set the Messaging Menu to "Available" it should default to available on the next boot. That is a no-brainer, but it does not work that way in Ubuntu 12.04, at least not for me, and this hasn't worked in previous versions of Ubuntu either. It always defaults to "Offline" regardless of which way you set it the last time you used it.

And I disagree that it's easy for a new user to configure. How does a new user know which Startup Command to use?

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/322314](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/322314)
[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/549723](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/549723)

> **Houmie said:**
> Too be honest I don't think its a terrible idea. It is great having a choice.  When I start the PC I want email & chat ready. Dont want to start everything myself.

It would have been nice having the option of auto start + minimized.

I just tried adding thunderbird to autostart, but don't find the program. I have to browse to it and have no idea where it is.  And I think minimized is not even supported right?

Probably not, and there is no option for Evolution either. A program specifically designed for minimizing apps is likely needed.

One thing I will mention is just how easy it is in the Mint Menu on Linux Mint, and that ease of configuring a program to start on boot is desperately needed in Ubuntu. In the Gnome 2x Mint Menu you just right click and choose: "Load on Startup" or something like that, and it's done.

---

