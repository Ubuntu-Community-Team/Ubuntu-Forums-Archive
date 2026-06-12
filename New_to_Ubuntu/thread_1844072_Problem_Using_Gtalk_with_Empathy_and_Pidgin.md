---
title: "Problem Using Gtalk with Empathy and Pidgin"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by sakibmoon on 2011-09-14
I used Pidgin for google talk. After using it a few days, it wouldn't log in. After I checked account, I saw that my account type was selected as XMPP and I couldn't select it as Gtalk. Every time I select it to Gtalk, it would automatically be back to XMPP. I uninstalled it and started using Empathy. Now in my empathy account, I can't see my contacts. When I start empathy it goes to the message icon on the upper panel ( I don't know it's name). If somone sends me a message, I can see it. But I can't see my contacts or chat with them.
In advanced option, no encryption is used, priority is selected 0, server is selected to "talk.google.com" and port is selected "5222". I haven't changed any of these.
I am using Ubuntu 10.04.
After seeing performance of pidgin and empathy, I even wrote a article on hubpage-
[http://sakibmoon.hubpages.com/hub/How-to-use-Gtalk-Yahoo-Messenger-Skype-and-other-Chat-Account-in-Ubuntu](http://sakibmoon.hubpages.com/hub/How-to-use-Gtalk-Yahoo-Messenger-Skype-and-other-Chat-Account-in-Ubuntu) ( I thought there are people like me who don't know ABC of Ubuntu, but want to use it )
and now I am the one who don't know what to do.:confused: I feel a lttle ashamed of myself. :(  I always use Gtalk for communication. Quick help would be great.

Thanks to all.

---

### Post by el_koraco on 2011-09-14
select port 5223

---

### Post by sakibmoon on 2011-09-14
> **el_koraco said:**
> select port 5223

After I select 5223, I get a network error. Any other option?

---

### Post by Rex Bouwense on 2011-09-14
I believe that the protocol for Gtalk is XMPP.  At least that what I am using in Pidgin (in Lucid)

---

### Post by sakibmoon on 2011-09-14
> **Rex Bouwense said:**
> I believe that the protocol for Gtalk is XMPP.  At least that what I am using in Pidgin (in Lucid)

I also think that XMPP is connected to Gtalk somehow, but the problem is when I select Gtalk as my account, add details and save it, I get network error. If i go again to see my account setting, I see that XMPP is selected as my account type, not Gtalk. I don't understand what the problem is. Now empathy is not showing the contacts. I don't know what to do.

---

### Post by Rex Bouwense on 2011-09-14
Not sure about Empathy because I never used it.  I have been a Pidgin guy since I converted to Linux.  However, when using Pidgin, if I cannot connect to Gtalk or chat whatever it is called, it will not show any contacts.  It will only show contacts if I am connected.  When it doesn't connect, I have to re-enable it.  Once again I am not sure if it is the same in Empathy.

---

### Post by sakibmoon on 2011-09-14
> **Rex Bouwense said:**
> Not sure about Empathy because I never used it.  I have been a Pidgin guy since I converted to Linux.  However, when using Pidgin, if I cannot connect to Gtalk or chat whatever it is called, it will not show any contacts.  It will only show contacts if I am connected.  When it doesn't connect, I have to re-enable it.  Once again I am not sure if it is the same in Empathy.

I also preferred Pidgin, but started using Empathy after facing problem with it. I know that it won't show contact if I am not connected, but I get error while connecting. When I start Pidgin, it gets stuck for a while. (See attachment 1) and then it says "unable to connect"(see attachment 2)

---

### Post by Rex Bouwense on 2011-09-14
Hey that happens to me all the time when I don't have a good solid connection.  Just choose reconnect.

---

### Post by sakibmoon on 2011-09-14
> **Rex Bouwense said:**
> Hey that happens to me all the time when I don't have a good solid connection.  Just choose reconnect.

Thanks Rex, maybe this is not a bug or problem then. But I cannot connect even if I try reconnecting ten times. Once it has been shown it won't connect again. My internet speed 32 kBps, but this was not a problem when I started it using at first. It would connect in a second.

---

### Post by LowSky on 2011-09-14
In pidgin go to modify account, Gtalk uses XMPP, so does facebook in case you use that too, its a very popular protocol. 

Basic should look like this:
Username: your username (easy)
Domain: gmail.com
Resoource: pidgin
Password: your password 9if you have issues log into your gmail account, just once and then retry pidgin, sometimes that clears the error

Advanced:

Connection Security: Require encryption
uncheck Allow plain text
Connect port is 5222
connect server is blank
file transfer proxy: proxy.eu.jabber.org
BOSH is blank

 Proxy Tab:
should be: Use Gnome Proxy settings, unless you have to set this by hand leave it there.


hope this helps

---

### Post by sakibmoon on 2011-09-15
My settings are already set that way. I reinstalled both empathy and pidgin several times and tried all your suggestion, but I still get the error. Maybe Using Wine will solve the problem.

---

### Post by lpwaqas on 2011-09-15
I am using pidgin on ubuntu Meerkat just fine, the notifications are awsome, to me it seems that you have gmail account setup on both empathy and pidgin all you need to do is to quit empathy (or kill the process) and run pidgin using simple gmail configuration.

---

### Post by sakibmoon on 2011-09-16
At first I thought so. I uninstalled Empathy and only tried Pidgin. Didn't work. Then uninstalled Pidgina and installed Empathy. Didn't work that too. Maybe the problem is with my connection or something. I am using Prism now.

---

