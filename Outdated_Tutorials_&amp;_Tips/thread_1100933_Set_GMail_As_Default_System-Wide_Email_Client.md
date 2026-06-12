---
title: "Set GMail As Default System-Wide Email Client"
date: 2009-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by SketchyClown on 2009-03-19
If you are like myself who no longer uses POP-3 email and a seperate client and prefers to use web-based GMail, then I have the simple solution for you to enable having GMail as the default system-wide email client in Ubuntu.

There is a tutorial which is quite old and dated now @ **HowToGeek** which requires using scripts and the command line to get this to work in Ubuntu with Firefox, but possibly due to improvements in Firefox since that article was written, I have found how to set this up in two(2) simple steps!

**First:**

Open Firefox and navigate to ***Edit > Preferences > Applications*** and scroll down to the ***'mailto' ***option and in the pull-down menu select ***'GMail'***.

[B]Second:

[/B]In the ***System*** menu on the panel, navigate to ***Preferences > Preferred Applications ***and in the section for ***'Mail Reader' ***, select ***'Custom'*** and in the ***'command' ***box, enter ***'firefox %s' ***(without the quotes, of course).

Thats it. You are now done. No scripts, no command line. Test it out by clicking any link to send an email either in a web page or for example in Emesene/Pidgin Messenger for sending an email to someone and you should find that Firefox opens a compose email window with the recipient's email address there for you.

Enjoy.:D

---

### Post by pvfjr on 2009-03-29
Seems to have changed something, thanks.  I'm having an issue right clicking on an image in firefox, hitting "send image".  I get a server error from gmail.  Says its a temporary 404 error and that my account is unavailable.  If I hit "try again" it just goes to my inbox and forgets that I was trying to send an image.  Any ideas?  Actually, I just checked and it does that with mailto: links too.

---

### Post by sambita on 2009-03-29
Thanks a lot for this!

---

### Post by SketchyClown on 2009-03-31
> **pvfjr said:**
> Seems to have changed something, thanks.  I'm having an issue right clicking on an image in firefox, hitting "send image".  I get a server error from gmail.  Says its a temporary 404 error and that my account is unavailable.  If I hit "try again" it just goes to my inbox and forgets that I was trying to send an image.  Any ideas?  Actually, I just checked and it does that with mailto: links too.

I do not get this error. I select an image in Firefox (v.3.0.8 currently) and select ***Send Image ***and it opens the GMail compose message window with the image details already inserted into the body of the message.

Not sure what it is that you are doing differently.

Server errors are a GMail issue or an issue with your ISP or network setup.

---

### Post by pvfjr on 2009-04-04
Well I had a rather odd development.  I just tried it on a separate windows machine on a separate dial-up ISP, using IE and G-mail Notifier with the mailto: feature enabled, which used to work.  I'm getting the same message any time I click on a mailto: link.  So it looks like your command is fine, it must be my account.

---

### Post by pvfjr on 2009-04-09
Well I figured it out, just in case anyone else runs into this.  The problem was due to the fact that my g-mail was in "basic html mode" rather than "standard mode", which happened because it wasn't loading properly on the dialup machine.  I didn't know that it would make all the other computers default to that mode as well, and disabled a lot of features, including this nice little mailto: fix.

---

### Post by SketchyClown on 2009-04-10
Glad to hear you got it sorted out, pvfjr.

---

### Post by bug67 on 2009-04-10
Well, this is cool!  Never even looked that far under the hood of FF before...always skipped over those "applications."

I wonder if this same procedure would work for setting up Apple's MobileMe as the default/system wide email client?  I see a "Use Yahoo" and a "Use Other."  Hmmm...must investigate further.

Thanks for the tip!:D

---

### Post by jpyanowski on 2009-04-12
Thanks for this info. Makes sending things very easy.

---

### Post by MGStreak on 2009-06-15
Is there any way to have the gmail compose window open in a new tab automatically? 

Yes, I know one could CTRL-click or middle-click or scroll-click, but I'm asking about getting FireFox to automagically take a single click on a mailto: link, open a new tab and load the gmail compose window.

Any ideas?

The closest I have found to this implementation is in this article:
[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

Sadly, it did not work for me!

---

### Post by simonbanyard on 2009-09-06
This feature is missing from my version of FF (3.0.13). Any ideas?

Sorry; solution found here [http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+default+firefox](http://ubuntuforums.org/showthread.php?t=1037693&highlight=gmail+default+firefox)

---

