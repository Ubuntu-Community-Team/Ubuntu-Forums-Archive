---
title: "Using msn with a gmail adress on pidgin"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by tokamak on 2008-05-09
Hi, 

Ik just switched from windows and im trying to use msn. I used a gmail account to msn with. Is this still possible with pidgin because I am not able to connect with this account to the msn server.

---

### Post by scragar on 2008-05-09
I use pidgin with MSN all the time and my email is @gmail.com so that's not the problem.

Enter your full email in the username box, and check your advanced settings:
server: **messenger.hotmail.com**
Port: **1863**

---

### Post by KIAaze on 2008-05-09
I use MSN with a Yahoo address, so I don't think Gmail should be a problem.

However, I had a similar problem: I could use MSN with aMSN, but not with Pidgin.
The reason: My password was too long. ^^

Here's a description of the problem:
[http://developer.pidgin.im/ticket/3460](http://developer.pidgin.im/ticket/3460)

If you type in only the first 16 characters, it should work. :)

Alternatives to Pidgin to test such problems:
aMSN
Kopete

---

### Post by The Pinny Parlour on 2008-09-27
I'm using a fresh install of Ubuntu.  I have Pidgin fired up using MSN with a gmail account and I get the following:

<email address> disabled
Unable to authenticate: The e-mail address or password is incorrect.

They're not incorrect, they're correct.

Any help is great.

Thanks

---

### Post by PocketDog on 2008-09-27
You have to associate your gmail (or any non-MSN/Hotmail) account with a .NET passport. You can do that at [http://www.passport.net](http://www.passport.net) It's free to do.

---

### Post by dbbolton on 2008-10-09
> **PocketDog said:**
> You have to associate your gmail (or any non-MSN/Hotmail) account with a .NET passport. You can do that at [http://www.passport.net](http://www.passport.net) It's free to do.
I have done this and I'm still having this same problem. I also checked the advanced settings as mentioned earlier, and they matched up.

Any help?

---

### Post by PocketDog on 2008-10-09
I don't know, sorry. I've got an old Gmail account I've never used on MSN - I just set up access via [www.passport.net](http://www.passport.net) for my Gmail account, clicked enable in Pidgin while signed in, and it works for me

---

### Post by iscah on 2008-10-09
[SIZE="1"]Hi there - I'm having the same problem as dbbolton, tokamak, and The Pinny Palour. It seems to be a common issue.

Normally I use my **gmail** address as my **Windows Live ID** (to sign into Windows Live/MSN Messenger). But I can't get Pidgin to work - it keeps saying "Unable to authenticate: Authentication Failure".

My settings are as follows:


[SIZE="2"]**BASIC TAB**[/SIZE]
**Login options**
Protocol: MSN
Username: [email]myusername@gmail.com[/email]
Password: mypassword
Remember password: Checked

**User options**
Local alias: myalias
New mail notifications: Unchecked
Use this buddy icon for this account: image selected

[SIZE="2"]**ADVANCED TAB**[/SIZE]
**MSN options**
Server: messenger.hotmail.com
Port: 1863
Use HTTP Method: Unchecked
HTTP Method Server: gateway.messenger.hotmail.com
Show custom smileys: Checked

**Proxy options**
Proxy type: Use global proxy settings


My password is not long, so the problem doesn't lie there.

I have also tried checking the option "Use HTTP Method", but I haven't changed much more than that.

Does anyone know what I'm missing? A few people (like Scragar) say that it works for them. Are you able to list your configuration settings?[/SIZE]

---

### Post by PocketDog on 2008-10-09
[img]http://img235.imageshack.us/img235/9426/screenshotmodifyaccountmv1.png[/img][img]http://img46.imageshack.us/img46/385/screenshotmodifyaccountrt1.png[/img]

My proxy settings in System > Preferences > Network Proxy is set to 'Direct Internet Connection'. (Laptop > Wireless Router > Internet)

---

### Post by iscah on 2008-10-09
Hm... perhaps the problem is that I am using Win XP? I haven't tried this on my Ubuntu computer. I have to wait a while before I can do that.

But it should still work for Windows, right? The only difference between what I have and what you have is the proxy type. You have "Use GNOME proxy settings", I have "Use global proxy settings". (My other options are: No proxy, HTTP, Socks 4, Socks 5, Use environmental settings)

I have been able to set up my GTalk account and another MSN account (@hotmail.com)... just no success with an MSN account with @gmail.com. 

Thank you very much for posting that, though. I suppose I will just have to keep fiddling.

---

### Post by jesuisbenjamin on 2008-11-17
> **PocketDog said:**
> I don't know, sorry. I've got an old Gmail account I've never used on MSN - I just set up access via [www.passport.net](http://www.passport.net) for my Gmail account, clicked enable in Pidgin while signed in, and it works for me

Does this mean your gmail address works both for Google Chat and MSN messenger?
So you actually don't need to use any hotmail address to use MSN messenger?

---

### Post by PocketDog on 2008-11-17
Correct. I've never actually had a Hotmail account

---

### Post by Mkve on 2009-03-20
*edit* solved! :)

---

### Post by bushtangu on 2010-03-15
i have the same problem, can you help please!

---

### Post by KIAaze on 2010-03-15
Can you log in on [https://login.live.com](https://login.live.com) with your non-hotmail address?
If you can do that, you should be able to log in with pidgin/kopete/aMSN.

Only problem might be if the password is too long.
cf [http://developer.pidgin.im/ticket/3320](http://developer.pidgin.im/ticket/3320) (bug appears to be fixed in latest version)

---

