---
title: "[SOLVED] I need to re-install firefox but I dont know how?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by gumpontheweb on 2008-05-05
I just got an update for foxyproxy in firefox. Now I get an error message when I open firefox. here is the shot...[IMG]http://ubuntuforums.org/attachment.php?attachmentid=68920&stc=1&d=1210015403[/IMG]

My other account is working fine so I wanted to do the simplest thing which I figured would be to re-install firefox. synaptic doesn't give me the option. when i went to uninstall, I got tons of other stuff going on.
What should I do?
Can I just make firefox in 1 account like the other account?

---

### Post by nowshining on 2008-05-05
no need to re-install

to get a new profile per say

in terminal run 

firefox --profilemanager


you can create a new profile if u'd like and even make it ask on startup which profile to use that way u don't have to do it everyting in the terminal. :)

---

### Post by nowshining on 2008-05-05
as for your problem, it's likely an add-on - ie: that foxy-proxy add-on causing the error. :)

---

### Post by akiratheoni on 2008-05-05
If you do want to uninstall Firefox, I believe the command would be:

```
sudo apt-get remove --purge firefox
```

---

### Post by gumpontheweb on 2008-05-05
I ended up upgrading to firefox 3 beta. at first, just to get rid of the add-on. I haven't  switched it back and I might not. Is there any downside to using a beta besides the obvious?
Very useful help though. Much appreciated!


Flash player plug-in doesn't install? whats up?

---

### Post by gumpontheweb on 2008-05-05
> **nowshining said:**
> no need to re-install

to get a new profile per say

in terminal run 

firefox --profilemanager


you can create a new profile if u'd like and even make it ask on startup which profile to use that way u don't have to do it everyting in the terminal. :)
the new firefox just stars up when I put it in...?
good idea though

---

### Post by nowshining on 2008-05-06
the downside to using a BETA is that a lot of add-one won't work with a BETA or work well or even @ all @ esp. an add-on that's really old. Altho.

Just to let u know an' XPI is actually a zip file in disguise :) and if u want to manually update an add-on to work with a newerr ver. of firefox - just edit the .rdf file changing the MAX version to a higher number - ie: 5.0 or something and re-insert or create a new .xpi with the updated rdf file and then go to open in firefox and browse to where u have it and open it up and install it however u'll have to rename the ext. .xpi before doing so.

Same thing with the add-ons that are .jar files or so - they to are just a zip file in disquise.

---

