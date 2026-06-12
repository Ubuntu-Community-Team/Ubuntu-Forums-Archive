---
title: "evolution problems"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by wrknight on 2011-10-19
Yesterday, I made the mistake of permitting my intel core 2 duo to upgrade from 11.04 which was nice and stable to 11.10 where everything went to pot.  I have fixed most of the serious problems, but Evolution mail is completely out of control.  I lost almost all of my "Sent" folder messages, I lost one of my in-boxes, each time I send, I get an error message about putting the message into the sent folder and when I close the application it won't close, I have to forcibly kill the process.  What I think I would like to do is reinstall it, but I don't want to lose any more mail than I have already lost.  (Ideally, I would like to recover my lost mail.)  I suspect that many of the problems are related to the mail file format change, but I have yet to verify that.

So first, does anyone have a simple fix for Evolution?  If not, do I have to uninstall Evolution in order to reinstall it?  And if I have to uninstall it, will I lose any data?  And finally, what's the best approach to fixing this problem?

---

### Post by JazzPotato on 2011-10-19
My clean install of 11.10 has evolution installed, but uses thunderbird for mail by default. imo thunderbird is better, but if you want to keep evolution, i'd uninstall and reintsall. You shouldnt lose any data if you use webmail like google mail/hotmail and you ahve evolution set to pop3.

---

### Post by dniMretsaM on 2011-10-19
Your mail should be in ~/.evolution/mail/. As for getting Evolution to work right, I don't know. 11.10 uses Thunderbird as the default mail client, so you might want to switch. I saw a really nice guide to help with this, I'll see if I can find it.

---

### Post by wrknight on 2011-10-19
Now I am totally confused.  The default mail for 11.10 using Gnome is evolution.  There is no indication that Thunderbird is doing anything or is even present.  If Thunderbird is doing something behind the scenes, I have no idea what is happening or how to find out.  So how do I find out what, if anything, Thunderbird is doing.

---

### Post by haqking on 2011-10-19
> **wrknight said:**
> Now I am totally confused.  The default mail for 11.10 using Gnome is evolution.  There is no indication that Thunderbird is doing anything or is even present.  If Thunderbird is doing something behind the scenes, I have no idea what is happening or how to find out.  So how do I find out what, if anything, Thunderbird is doing.

There seems to be recurring theme with this evolution and upgrading to 11.10 thing where Thunderbird is default

Just so you know for the future, evolution allows you to export your settings and mail to mbox or tar.gz etc.

always have backups so in the event you mess up, or allow an unauthorised upgrade without testing then recovery is easy.

Also depending on your mail provider you can possibly change remote settings so you can pull them all down again locally.

but BACKUP ;-)

---

### Post by dniMretsaM on 2011-10-19
> **wrknight said:**
> Now I am totally confused.  The default mail for 11.10 using Gnome is evolution.  There is no indication that Thunderbird is doing anything or is even present.  If Thunderbird is doing something behind the scenes, I have no idea what is happening or how to find out.  So how do I find out what, if anything, Thunderbird is doing.

No, Evolution is not default in 11.10. Thunderbird is. Anyway, have a look at these links:
[http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html](http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html)
[http://ubuntuforums.org/showthread.php?t=1790177](http://ubuntuforums.org/showthread.php?t=1790177)
[https://help.ubuntu.com/community/MigrateEvolutionToThunderbird](https://help.ubuntu.com/community/MigrateEvolutionToThunderbird)

On a side note, reading about all these people having trouble moving from Evolution to Thunderbird makes me glad that I've always used TB and don't have to deal with all this crap.

> **haqking said:**
> but BACKUP :wink:

What does that mean?

---

### Post by haqking on 2011-10-19
> **dniMretsaM said:**
> 


What does that mean?

It means make BACKUPS.

---

### Post by dniMretsaM on 2011-10-19
> **haqking said:**
> It means make BACKUPS.

Either you missed my sarcasm, or you're being sarcastic too.

---

### Post by haqking on 2011-10-19
> **dniMretsaM said:**
> Either you missed my sarcasm, or you're being sarcastic too.

oh i did miss that actually, but you never know on here...LOL ;)

---

### Post by dniMretsaM on 2011-10-19
> **haqking said:**
> oh i did miss that actually, but you never know on here...LOL ;)

Yeah, it's hard to portray sarcasm on the Internet unless you use the [SARCASM][/SARCASM] tags.

---

### Post by wrknight on 2011-10-19
You guys are talking way past me. You say that Thunderbird is the default application, yet I can find no evidence anywhere on my system that Thunderbird is doing anything.  When I open the Applications menu and select Office, I find and open Evolution Mail and Calendar.  (This is what I am using.)  At this location, Thunderbird is not listed.  When I have Evolution open to the mail application and pull down the Help menu as select About, it says "Evolution 3.2.0 Groupware Suite, Evolution Website, Copyright © 1999 - 2008 Novell, Inc. and Others" - and there's no mention of Thunderbird anywhere.  So what am I missing?  Where is Thunderbird in all this?  Please tell me where to find what you say is Thunderbird.

---

### Post by dFlyer on 2011-10-19
> **wrknight said:**
> You guys are talking way past me. You say that Thunderbird is the default application, yet I can find no evidence anywhere on my system that Thunderbird is doing anything.  When I open the Applications menu and select Office, I find and open Evolution Mail and Calendar.  (This is what I am using.)  At this location, Thunderbird is not listed.  When I have Evolution open to the mail application and pull down the Help menu as select About, it says "Evolution 3.2.0 Groupware Suite, Evolution Website, Copyright © 1999 - 2008 Novell, Inc. and Others" - and there's no mention of Thunderbird anywhere.  So what am I missing?  Where is Thunderbird in all this?  Please tell me where to find what you say is Thunderbird.

If your using 11.10 thunderbird is the default application.

---

### Post by haqking on 2011-10-19
> **wrknight said:**
> You guys are talking way past me. You say that Thunderbird is the default application, yet I can find no evidence anywhere on my system that Thunderbird is doing anything.  When I open the Applications menu and select Office, I find and open Evolution Mail and Calendar.  (This is what I am using.)  At this location, Thunderbird is not listed.  When I have Evolution open to the mail application and pull down the Help menu as select About, it says "Evolution 3.2.0 Groupware Suite, Evolution Website, Copyright © 1999 - 2008 Novell, Inc. and Others" - and there's no mention of Thunderbird anywhere.  So what am I missing?  Where is Thunderbird in all this?  Please tell me where to find what you say is Thunderbird.

You said you were using 11.10, there is no Applications menu in 11.10.

Thunderbird is the default client in 11.10 though it can be removed and Evolution installed

can you show us a screen dump of your desktop and the output of

```
gnome-session --version
```

and

```
cat /etc/issue
```

or

```
lsb_release -a
```

---

### Post by wrknight on 2011-10-20
Here are the reports from the following commands.


wayne@K-1:~$ gnome-session --version
gnome-session 3.2.0

wayne@K-1:~$ cat /etc/issue
Ubuntu 11.10 \n \l

wayne@K-1:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

---

### Post by haqking on 2011-10-20
> **wrknight said:**
> Here are the reports from the following commands.


wayne@K-1:~$ gnome-session --version
gnome-session 3.2.0

wayne@K-1:~$ cat /etc/issue
Ubuntu 11.10 \n \l

wayne@K-1:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric

OK thats weird.  You say you have an applications menu ?

---

### Post by wrknight on 2011-10-20
Everyone on this thread (except me) says I'm using Thunderbird for my mail, but I can find no evidence that that is true.  Everything I do says I'm using Evolution.  Now I use Evolution because I like the integrated calendar and task functions.  The last time I used Thunderbird it didn't have those functions and I didn't like having to use two different applications that weren't integrated when I could accomplish what I wanted with one.  So, I returned to Evolution when I upgraded to 10.04 and have been using it since.  It was working fine up until I did the latest upgrade to 11.10 (from 11.04) yesterday and now it does weird stuff.  Like it won't save my outgoing messages.  Whenever I send a message, I get an error message about not being able to save it in the Sent folder.  Also, when I try to make configuration changes, it tells me I have to be online when, in fact, I am online.  And finally, when I try to close it, it refuses to close and I have to forcibly kill the process.  If I have to move to Thunderbird, I am going to be one unhappy camper.

---

### Post by haqking on 2011-10-20
> **wrknight said:**
> Everyone on this thread (except me) says I'm using Thunderbird for my mail, but I can find no evidence that that is true.  Everything I do says I'm using Evolution.  Now I use Evolution because I like the integrated calendar and task functions.  The last time I used Thunderbird it didn't have those functions and I didn't like having to use two different applications that weren't integrated when I could accomplish what I wanted with one.  So, I returned to Evolution when I upgraded to 10.04 and have been using it since.  It was working fine up until I did the latest upgrade to 11.10 (from 11.04) yesterday and now it does weird stuff.  Like it won't save my outgoing messages.  Whenever I send a message, I get an error message about not being able to save it in the Sent folder.  Also, when I try to make configuration changes, it tells me I have to be online when, in fact, I am online.  And finally, when I try to close it, it refuses to close and I have to forcibly kill the process.  If I have to move to Thunderbird, I am going to be one unhappy camper.

like i say above, 11.10 does not have an applications menu so i am confused.

Can you show us a screen dump of your desktop

cheers

---

### Post by dniMretsaM on 2011-10-20
> **haqking said:**
> OK thats weird.  You say you have an applications menu ?

+1

> **wrknight said:**
> Everyone on this thread (except me) says I'm using Thunderbird for my mail, but I can find no evidence that that is true.  Everything I do says I'm using Evolution.  Now I use Evolution because I like the integrated calendar and task functions.  The last time I used Thunderbird it didn't have those functions and I didn't like having to use two different applications that weren't integrated when I could accomplish what I wanted with one.  So, I returned to Evolution when I upgraded to 10.04 and have been using it since.  It was working fine up until I did the latest upgrade to 11.10 (from 11.04) yesterday and now it does weird stuff.  Like it won't save my outgoing messages.  Whenever I send a message, I get an error message about not being able to save it in the Sent folder.  Also, when I try to make configuration changes, it tells me I have to be online when, in fact, I am online.  And finally, when I try to close it, it refuses to close and I have to forcibly kill the process.  If I have to move to Thunderbird, I am going to be one unhappy camper.

Ok, hold on. We didn't say that you were USING Thunderbird, just that it is installed. The reason we say that is because Thunderbird is the default mail client in 11.10. We know this for a fact, so we can only assume it's installed unless you removed it or something weird went wrong with the upgrade. Note that the last time you used TB was before 10.04, so that was version 3.x or possible 2.x. It's up to version 7 now, so you might want to give it another try. As for an integrated calender, you would just install Lightning. And nobody is forcing you to switch to Thunderbird, I honestly doubt you'll have to. Anyway, please show us a screen shot of your desktop.

---

### Post by alexpotter on 2011-10-20
> **wrknight said:**
> Yesterday, I made the mistake of permitting my intel core 2 duo to upgrade from 11.04 which was nice and stable to 11.10 where everything went to pot.  I have fixed most of the serious problems, but Evolution mail is completely out of control.  I lost almost all of my "Sent" folder messages, I lost one of my in-boxes, each time I send, I get an error message about putting the message into the sent folder and when I close the application it won't close, I have to forcibly kill the process.  What I think I would like to do is reinstall it, but I don't want to lose any more mail than I have already lost.  (Ideally, I would like to recover my lost mail.)  I suspect that many of the problems are related to the mail file format change, but I have yet to verify that.

So first, does anyone have a simple fix for Evolution?  If not, do I have to uninstall Evolution in order to reinstall it?  And if I have to uninstall it, will I lose any data?  And finally, what's the best approach to fixing this problem?

I don't like Evolution. Never had done - too clunky, slow and not able to get to my Gmail account. I installed Thunderbird - much easier and better, and now that it is integrated into 11.10 is a great change! :)

---

### Post by haqking on 2011-10-20
> **alexpotter said:**
> I don't like Evolution. Never had done - too clunky, slow and not able to get to my Gmail account. I installed Thunderbird - much easier and better, and now that it is integrated into 11.10 is a great change! :)

I love evolution, not at all clunky, very fast and handles my multiple gmail, mail, gmx etc mail with no problems.

And in my 11.10 USB and VM i removed thunderbird default and installed evolution 3.2 and again works great.

---

### Post by philinux on 2011-10-20
With an upgrade Thunderbird is probably not even installed. Unless a user installed it before the upgrade. A clean install would install it.

---

### Post by haqking on 2011-10-20
> **philinux said:**
> With an upgrade Thunderbird is probably not even installed. Unless a user installed it before the upgrade. A clean install would install it.

indeed, though still doesnt explain the OP applications menu, still waiting to see a screen dump. PLus i have seen other threads with upgrades where thunderbird is the client and they have lost their mail ? (without backups of course ;-)

I am confused ;-)

---

### Post by philinux on 2011-10-20
> **haqking said:**
> indeed, though still doesnt explain the OP applications menu, still waiting to see a screen dump. PLus i have seen other threads with upgrades where thunderbird is the client and they have lost their mail ? (without backups of course ;-)

I am confused ;-)

Indeed. I did a clean install but backed up evolution to its tar file. I have home on its own partition and just deleted most of the .config files. Evolution restored fine and converted my mbox.
Awaiting screen dump too.

---

### Post by dniMretsaM on 2011-10-20
I always though upgrading installed all the default applications, even if someone hadn't originally installed them. I could be wrong, I am just guessing this from some things I read in other threads. Either way I'm still confused about the presence of an application menu. Is it possible he means the window that show up when you click on the "+" button in the launcher?

EDIT: 777th post :popcorn:

---

### Post by wrknight on 2011-10-20
I'm not sure exactly what you mean by a screen dump.  I have a jpeg image of my desktop, but I am not sure how to attach it or include the image in this message.  But I'll give it a try.


file:///home/wayne/Desktop/Desktop.jpeg


Unhh! I don't think that worked.  I don't see anything inviting me to attach an image file.  I honestly don't know how to do what you are asking.


PS  By the way, Thunderbird is installed, it just isn't launched.  Also it doesn't show up in the process table.

---

### Post by wrknight on 2011-10-20
did this work?



apparently not.

---

### Post by lyngvi on 2011-10-20
Here is a picture of a dog.

Advanced... Manage Attachments... Browse... Find the file... Hit the "Upload" button to the right... When it's uploaded, the Current Attachments view should indicate the filename, and allow you to remove the attachment. Just close that window, then finish your post and hit "Submit Reply.

---

### Post by wrknight on 2011-10-20
did it work this time?





Voila!  I guess it did.

---

### Post by dniMretsaM on 2011-10-20
Uhhh... That's not Unity that's for sure. Are you using Gnome-Shell/fallback (I don't know what either looks like actually)?

Anyway, what's the status of your mail? Does it exist in ~/.evolution/mail/?

---

