---
title: "How  to use Gaim with Google Talk servers"
date: 2005-08-25
forum: Outdated Tutorials &amp; Tips
---

### Post by celticmonkey on 2005-08-25
Prerequisites: You need to install Gaim and you need a gmail account.

Add an account in Gaim with these settings:

Protocol: Jabber
Screenname: your_gmail_name
Server: gmail.com
Password: your_gmail_password
Alias: you_can_leave_this_blank

under Show more options:
Use TLS if available: check
Force old SSl: uncheck
Allow plaintext auth over unencrypted streams: uncheck
Port: 5222
Connect server: talk.google.com

Note: for screenname, you don't need to enter @gmail.com after you login name.

This will allow you to IM other gmail users. You won't be able to use the VOIP feature of google talk.

---

### Post by cutOff on 2005-08-25
Works like a charm. Many thanks.

---

### Post by Paulus on 2005-08-25
worked here too!  ty!

---

### Post by LaSSarD on 2005-08-25
[QUOTE=celticmonkey]Prerequisites: You need to install Gaim and you need a gmail account.

Add an account in Gaim with these settings:

Protocol: Jabber
Screenname: your_gmail_name
Server: gmail.com
Password: your_gmail_password
Alias: you_can_leave_this_blank

under Show more options:
Use TLS if available: check
Force old SSl: uncheck
Allow plaintext auth over unencrypted streams: uncheck
Port: 5222
Connect server: talk.google.com

Note: for screenname, you don't need to enter @gmail.com after you login name.

This will allow you to IM other gmail users. You won't be able to use the VOIP feature of google talk.[/QUOTE]
 Perfect, I was looking for it :)

---

### Post by arnieboy on 2005-08-25
[QUOTE=LaSSarD]Perfect, I was looking for it :)[/QUOTE]
off topic but if u cant use the VoIP feature, then whats the big deal anyway? there are a zillion chat protocols already BUT the only chat engine that lets us use VoIP is skype. linux desperately needs a few more alternatives.

---

### Post by mike998 on 2005-08-25
Google is going to open the specs on the VoIP part and allow third party developers to create VoIP usage.

As mentioned [here](http://www.google.com/talk/developer.html#protocols)

---

### Post by arnieboy on 2005-08-25
[QUOTE=mike998]Google is going to open the specs on the VoIP part and allow third party developers to create VoIP usage.

As mentioned [here](http://www.google.com/talk/developer.html#protocols)[/QUOTE]
sounds exciting to me. lets wait and watch :)

---

### Post by zlogic on 2005-08-25
Does it download the contactlist from Gmail? My Gaim doesn't do that, is this my misconfiguration fault or is it something avaliable only in Google Talk for Windows?

---

### Post by celticmonkey on 2005-08-26
When I first logged on using Gaim I didn't have any contacts and it didn't import any. However, I've since noticed that everytime I email someone from Gmail, they pop up on my contacts in Gaim. I tried removing a contact in Gaim and found the name had also disappeared from my address book when I logged into Gmail. How one blocks unwanted users or keeps users in the address book but not the Gaim contact list I don't know.

As to the lack of VOIP, it looks like Google's service is open standards and will someday be interoperable with Linphone or Gizmo ([http://www.gizmoproject.com)](http://www.gizmoproject.com)) which is very similar to Skype but uses open standards. By the way, Gizmo has just released a linux beta with debian packages.

---

### Post by intangible on 2005-08-26
Google themselves have a nice howto for GAIM here, with screenies :-) !: [http://www.google.com/support/talk/bin/answer.py?answer=24073](http://www.google.com/support/talk/bin/answer.py?answer=24073)

---

### Post by macgyver2 on 2005-08-26
Cool, I was using the wrong server.  Works now.  Thanks!

---

### Post by njean on 2005-08-27
it works fine, thanks!

---

### Post by wiggie on 2006-10-15
If you still have problems connecting try replacing gmail.com with googlemail.com for the server. It worked for me.

Cheers

---

