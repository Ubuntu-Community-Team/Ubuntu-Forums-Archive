---
title: "how do i get new mail notification on my desktop using Evolution Mail"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by kevinstrudwick on 2008-04-26
how do i get an indicator/icon on my desktop to inform me i have new mail. i can manually retrieve new mail by going into Evolution, but it's not what i want, as i have to remember to check my mail!
any help would be appreciated

kevin

---

### Post by swegner on 2008-04-26
Hi Kevin,

In Evolution there is a plugin called "Mail Notification" that will do exactly what you are looking for.  I believe it is distributed in the "evolution-plugins" package.  To make sure it is installed, go to System > Administration > Synaptic Package Manager.  Do a search for "evolution-plugins" and make sure it has a green box next to it.  If not, click the box to install, and press apply.

In Evolution, go to Edit > Plugins.  Scroll down and look for "Mail Notification", and check it to enable it.  In the right pane, you can go to "Configuration" to make sure it'll show a message in the notification area.  Once you've got that setup, that should do it!  Note that Evolution needs to be open and running to receive notifications. 

Hope this helps!

---

### Post by kevinstrudwick on 2008-04-26
Thanks Scott,

i tried your suggestion but i am not getting new mail notification unless i specifically request them from within Evolution, or I am logging into Evolution. I am probably being incredibly dense here but this is what i expect from a mail service

1. when i log onto the internet, i want to be able to see if new message(s) have been left for me (and how many preferably).

2. whilst i am using the internet i want a new mail notification to pop-up on my screen regardless of whether i am signed into email at the time.

I don't care who i use for email, but surely my old ISP (aol) were not doing something unique by keeping their customers informed about new mail.

mr genuinely puzzled

---

### Post by swegner on 2008-04-26
Hi Kevin,

Perhaps I misunderstood your question, or else I'm not sure where you are stuck.  Here's some more suggestions I have for you:

First of all, I'm not quite clear-- do you already have your email account setup within Evolution?  That is, can you send and receive your AOL emails from within Evolution?  If not, this is the first thing you need to setup.  There are numerous guides elsewhere, let me know if you need one.

If your email is already setup, then perhaps it isn't being fetched automatically.  There in an option to check mail automatically every so often.  In Evolution, go to Edit > Preferences.  In the left pane, make sure "Mail Accounts" is selected.  In the main pane, select your mail account, and click "Edit".  In the pop-up window, select the "Receiving Options" tab.  Check the first box that says "Check for new messages every ** minutes".  Then you can fill in a value here-- either 5 or 10 minutes is usually ok.

If both of these are already setup, then perhaps it is just that Evolution isn't running.  As far as I'm aware, Evolution needs be running, even minimized, to get notifications working.  You can launch it manually from the main menu, or you could have it automatically start when you login.  To set it up to auto-start, go to Settings > Preferences > Sessions.  Click on "Add".  In the "Name" field, enter "Evolution mail".  For command, enter
```
evolution --component=mail
```
And for comment, enter "Email client".  Click OK, and Evolution will start automatically next time you login.

If none of these solve your problem, then perhaps I still don't understand your situation.  Let me know.

---

### Post by natrixgli on 2008-04-26
Hey,

Rather than have evolution always run at startup, there is a separate mail notification program, oddly enough called 'mail-notification'.

I've used mail-notification which works well, and will run when evolution is closed. It will show number of messages, and pop up a little summary of the messages as they arrive. 

If you go to Add/Remove you can search for mail-notification and there you have it. 

When you set it up, you can have it run at startup. I also recommend checking the "always show" option so you can see that it is running.

Cheerio,

-n8

---

### Post by end-user on 2008-04-27
> **natrixgli said:**
> Hey,

Rather than have evolution always run at startup, there is a separate mail notification program, oddly enough called 'mail-notification'.

I've used mail-notification which works well, and will run when evolution is closed. It will show number of messages, and pop up a little summary of the messages as they arrive. 

If you go to Add/Remove you can search for mail-notification and there you have it. 

When you set it up, you can have it run at startup. I also recommend checking the "always show" option so you can see that it is running.

Cheerio,

-n8

I get an error message about it being unable to communicate with Evolution if Evolution is closed.

---

### Post by rosswmcgee on 2008-04-27
The last answer is the correct and easy way. I use mail notification all the time it is great. If you hihglight the notification icon you will see the mail that is in your box before you down load it. This offers you the opportunity to see if there is any junk type or possible danger lurking. If you see that there is then go to your isp provider and delete that mail before it arrives in evolution. Ross

---

### Post by kevinstrudwick on 2008-04-27
thanks for the help. 'mail-notification' was not present in my add/remove programs, but i was able to get it using sudo apt-get install mail-notification.
i just need to work out how to set it up (am struggling with depression right now) so i may have to leave it for now.
on the positive side i have managed to dual boot Windows98se and ubuntu 7.10 and can continue to use my ms-money programme.:)

---

### Post by end-user on 2008-04-27
There is an additional package you will need to use mail-notification with Evolution, you will have to use Synaptic Package Manager, and also grab mail-notification-evolution.

But, and anyone can feel free to correct me, I believe there is no way to have Evolution running in the background with mail-notification giving you updates on new mail. Since Evolution is the program that actually downloads the mail from the pop server, it is almost useless to use mail-notification and mail-notification-evolution. All you'll really get is some more customization for how the notifications look.

Alltray would be a better (still half-***) solution. That can be gotten in Add/Remove. It lets you put evolution in the tray, and Evolution already has some notification options in the Mail Notification plugin (you can go to the configure tab, for example, to change the beep to something more pleasant). I suppose one could use Alltray + mail=notification + mail-notification-evolution if they wanted to really customize how it works.

I think someone was suggesting perhaps that you could use mail-notification to check for new mail directly on the server, and then open Evolution on a need be basis, at which point it would download the mail. 

See, there is some dogma in the GNOME bible somewhere that is morally and ethically [wrong]("http://www.go-evolution.org/FAQ#Can_I_minimize_the_Evolution_window_to_the_system_tray.3F") to use the System Tray in any manner that resembles functionality. Apparently Pidgin and Liferea are quite the rabble-rousing rebels for allowing the masses their guilty pleasure of tray functionality, and the unfortunate side effect is it leaves sane users who are ignorant of the pure path of the GNOME confused as to whether or not they can actually get their desktop to behave the way they want it to. It is more important that users conform to the program than the other way around. And the Notification Area is very sensitive. Now, personally, I think there is just some dev somewhere who had a really bad incident with GatorWare and hasn't recovered.

---

### Post by QUEEN HIPPOLYTA on 2008-04-27
> **natrixgli said:**
> Hey,

Rather than have evolution always run at startup, there is a separate mail notification program, oddly enough called 'mail-notification'.

I've used mail-notification which works well, and will run when evolution is closed. It will show number of messages, and pop up a little summary of the messages as they arrive. 

If you go to Add/Remove you can search for mail-notification and there you have it. 

When you set it up, you can have it run at startup. I also recommend checking the "always show" option so you can see that it is running.

Cheerio,

-n8


For those who don't know mail notification works really well with thunderbird so that you don't have to keep it open all the time.

---

### Post by Miroku on 2008-06-13
wow thanks for the mail-notification proggy -- works like a charm!

the forums are awesome, if it were a woman, i would make love to it :popcorn:

---

### Post by gandaran on 2008-06-13
the best way to get evolution to notify you of incoming mail is to keep evolution running in the system tray, to do that you use the **alltray** utility to put the evolution mail icon in the system tray.

---

### Post by crjackson on 2008-06-13
> **QUEEN HIPPOLYTA said:**
> For those who don't know mail notification works really well with thunderbird so that you don't have to keep it open all the time.

Thanks - I didn't know that.  I use thunderbird myself.  I'll be installing this little toy over the weekend.

---

