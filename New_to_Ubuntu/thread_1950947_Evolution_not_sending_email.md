---
title: "Evolution not sending email"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by arnoversfeld on 2012-04-01
I'm running Ubuntu 10.04 LTS version and use Evolution 2.28.3 as email client. For months, ever since a started using  Ubuntu 10.04, Evolution has worked perfectly. For a few days now Evolution has stopped sending email; I get an error :
 

 Error while Sending message.
 DATA command failed: Connection timed out: mail not sent.
 

 Where must I look, what must I do to find out what is causing the problem. When I use Outlook express in Windows XP there's no problem sending email to the same SMTP server.
 

 Many thanks for anyone who is going to help.

---

### Post by Tamlynmac on 2012-04-01
Just a quick thought, are you receiving e-mail? If not, then have you checked to see if your online? On the bottom left corner of Evolution there's an icon showing if your online. If it's offline simply left click on the icon and it will go online. That option is also located in the menu: file/work online or work offline.

If your offline and send or receive, the time out error is the one I've always seen generated. I experienced this after an update, finding that I was offline after said update.

Good Luck & Hope this helps.

---

### Post by arnoversfeld on 2012-04-02
Hi Tamlynmac.
Thank you so much for your response.

Evolution was online, I clicked on the icon to go offline, then I clicked on it again to go online and hit send/receive.
I receive email without a problem but still get:

Error while Sending message.
DATA command failed: Connection timed out: mail not sent

My messages still sit in my Outbox.
Somewhere I should be able to enable logging and a log level. Any idea where I may find that.
Thanks again for your response !

---

### Post by arnoversfeld on 2012-04-02
Hi Tamlynmac.
Thank you so much for your response.

Evolution was online, I clicked on the icon to go offline, then I clicked on it again to go online and hit send/receive.
I receive email without a problem but still get:

Error while Sending message.
DATA command failed: Connection timed out: mail not sent

My messages still sit in my Outbox.
Somewhere I should be able to enable logging and a log level. Any idea where I may find that.
Thanks again for your response !

---

### Post by Tamlynmac on 2012-04-02
You might wish to check you sending preferences.
edit/preferences

Select the account (left click on account) on the main window when it open and then select the edit button on the right side of the window. Go to the sending e-mail tab. It's possible that your authentication is incorrect. Try left clicking on the "Check for supported types" button and see what's available. Also check and make sure your server information is correct (including type = SMPT) and that your user name is accurate. If your receiving mail, check the receiving mail tab and you may be able to use it to help identify the correct setup for your sending e-mail.

Good Luck

---

### Post by arnoversfeld on 2012-04-03
Hi Tamlynmac.
Thank you so much for your response. I called my service provider today to check the SMTP server address. It was correct so we replaced it with the server's IP address. Which still didn't make a difference. The agent then asked me to delete the message in the ourbox and then hit send/receive. I did that and it seemed to work correctly, so I created a test message and hit send. It work perfectly. It seems that the message somehow got corrupted and couldn't be sent.
I normally use HTML format so I tested by sending a message with (plain text) and one with HTML format. The plain text was sent almost instantly while the HTML could be sent.
It seems clear there is problem using HTML format so I'll just steer clear of it for a while.
Thank you once  again for responding.

---

### Post by Tamlynmac on 2012-04-03
> arnoversfeld

Glad you figured it out. I use HTML all the time in Evolution and have never had a problem, wonder if it has something to do with your server? Perhaps, something to do with your character encoding. I use Unicode (UTF-8) for both composing & general.

Anyway, it sounds like your at least able to send/receive e-mail, be it plain text. Have your tried sending any attachments? This might be interesting as your e-mail server may have restrictions on both HTML & attachments.

I noticed your still using 10.04. My family & I will continue using 10.04 until support runs out in 2013 at which time we'll switch to Xubuntu on all of our systems. I've been Ubuntu only since 7.04 and on our systems the new releases seem to be memory hogs and slow. Neither do I like the basic Unity format. We tried both MATE and Cinnamon only to find them even slower. I actually enjoy being able to configure each of our systems separately and the family enjoys being creative with their desktops. None of them have indicated they like the new releases.

We have installed Xubuntu on one of our desktops and have been extremely pleased with it's stability & functionality. It's not quite as configurable as 10.04, but close enough. Are you going to switch to 12.04 when support runs out for 10.04? Or, have you decided on a different path? If you haven't decided yet, you might try downloading the .iso for Xubuntu, Kubuntu and/or Lubuntu and test the live CD/stick before making any decision.

Good Luck

---

