---
title: "Setting up Evolution for my College Email"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by AdrianStrays on 2008-05-07
I'm trying to set up Evolution for my school email account, but I can't for the life of me get it to work.  There are some configuration settings that I can't seem to find in Evolution (Changing port, the LDAP Server...)

Below is a guide for setting it up in Thunderbird
[http://www.uss.pdx.edu/bin/article.php?article=343737](http://www.uss.pdx.edu/bin/article.php?article=343737)

If you could help me, that'd be great.

---

### Post by OMRebel on 2008-05-08
Looks to be pretty straight forward.  Open up Evolution and go to Edit - Preferences.  Highlight the account you've been trying to setup and and click on Edit.  

Click on the Receiving Email tab, select IMAP for Server Type.  
For "server" put in psumail.pdx.edu:993.
For "authentification" select password.
For "username" enter in your user name. 
For "Use secure connection" select SSL.

Click on the Sending Email tab, and select SMTP for Server Type.
For "server" put in mailhost.pdx.edu:587.
For "authentification" select login.
For "username" enter in your user name.
For "Use secure connection", select TLS.

For the Directory Server, I'm not real sure, but you should be able to Google how to do that if it's possible.

Edit - Okay, I figured out how to setup LDAP.  In Evolution, beside the New button, click on the downward arrow and select Address Book.  Then for Type select LDAP.  
For name, enter in "PSU Directory".
For server, put in ldap.oit.pdx.edu.
Put in 389 for your port.
For "Login method" select distinguished name (DN).
For "Login" enter in dc=pdx,dc=edu.
Click on the Details tab, and the click on Fine Possible Search Bases, and something should come up.  

That's really all I can figure out about setting up your DS through LDAP.

---

### Post by AdrianStrays on 2008-05-08
It works now, but there are two seperate trees "On this Computer" and "School" how do I merge those two?

---

### Post by OMRebel on 2008-05-08
I'm not sure how to resolve that problem to be honest.  Try doing a google search on it.  More than likely someone has had that problem before.  If you do figure it out, be sure to post it here.

---

