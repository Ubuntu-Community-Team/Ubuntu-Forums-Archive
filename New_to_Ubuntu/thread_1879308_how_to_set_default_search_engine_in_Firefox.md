---
title: "how to set default search engine in Firefox"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by raymondvillain on 2011-11-11
Running Ubuntu 10.10, Mozilla Firefox used to use Google for my default search engine.  Then I replaced my router and now it uses some screwy thing called Dlinksearch (Dlink is the router brand I installed).

How does one go about setting the default search engine in Firefox?

Now, even if I type a specific address in the box, I get the "Dlinksearch.com" listings for this topic, and I am not connected to the address I typed in.

---

### Post by I2k4 on 2011-11-11
Try this:

[http://www.groovypost.com/howto/change-firefox-4-address-bar-search-engine-provider/](http://www.groovypost.com/howto/change-firefox-4-address-bar-search-engine-provider/)

---

### Post by pqwoerituytrueiwoq on 2011-11-11
that is being set by your dns server in your router
i normaly use google's dns server
[system->preferences-> network connections]("http://i.imgur.com/40Dbf.png")
click the one you are using eg "eth0" for wired and click edit or what ever you have for wireless
[IMG]http://imgur.com/Q0Swc.png[/IMG]
that would give you google instead of the dlink (you can set this in your router instead so it will affect all computers connected)


here is where i would change the setting in firefox (i have it using Google's "im feeling lucky" search)
[http://i.imgur.com/DiSjL.png](http://i.imgur.com/DiSjL.png)

---

### Post by raymondvillain on 2011-11-11
Thanks, pqwoerituytrueiwoq, but I'm still having problems.  If I go to System>Preferences>Network Connections, I can choose the connection I'm using, which is eth0, and edit it.  Where do I get rid of the current default search by using Network Connections?

I went through the steps to change the default browser in Firefox ([http://i.imgur.com/DiSjL.png](http://i.imgur.com/DiSjL.png)) but it didn't help.

You mentioned that the dns server in the router was "taking over".  If I log onto the router, can I somehow disable this function?

Thanks again,
Hank

---

### Post by raymondvillain on 2011-11-11
Got it!

It was a setting in the router.  I disabled the "Enable DNS relay" check box and now I'm back to normal.

Thanks for all the help, I will mark this solved.

Hank

---

