---
title: "Remove these icons? (PIC)"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by d4m1r on 2011-10-14
[IMG]http://i.imgur.com/h5jyY.png[/IMG]

First off, what is this top bar called? Secondly, I'd like to remove those 2 icons as I never use  a program based email (don't even have evolution configured) or the built in IM feature.

Is there even a way to remove/hide them? If I remove the Evolution email client, will it remove the email icon? :|

---

### Post by d4m1r on 2011-10-14
Any ideas?:confused:

---

### Post by dFlyer on 2011-10-14
before you bump please wait at least 24 hours. I can't answer your question.

---

### Post by wildmanne39 on 2011-10-14
Hi, I believe the only way to remove the mail icon is to uninstall evolution but that uninstalls things you probably want to keep so I do not recommend it.

I am not sure about the date.
Thank you

---

### Post by d4m1r on 2011-10-15
> **wildmanne39 said:**
> Hi, I believe the only way to remove the mail icon is to uninstall evolution but that uninstalls things you probably want to keep so I do not recommend it.

I am not sure about the date.
Thank you

Uninstalled Evolution email and Empathy IM but there are still there..I'll check after restarting. I am not trying to remove the date but the IM thing. I am surprised this is not a common question.

What is that top bar called anyway?

@dflyer, only bumped because it was on the 3rd page already because of all the 11.10 topics and I thought it was an easy fix :(

---

### Post by wildmanne39 on 2011-10-15
Hi, I am afraid you will find it uninstalled other things as well, I do not remember in 11.04 what all it uninstalled but when you uninstall from synaptic you can click to see what is going to be removed.

I believe the top bar is just called a panel but that may have changed since 11.04 came out.
Thank you

---

### Post by Calerid on 2011-10-15
Umm Hi, Guys?

Right click, select remove? All I had to do? Have you tried this?

---

### Post by d4m1r on 2011-10-15
> **Calerid said:**
> Umm Hi, Guys?

Right click, select remove? All I had to do? Have you tried this?

What version are you running?! This is not an option for any of those icons for me...Even after a restart (after uninstalled Evolution Mail and Empathy IM) they are still there...

Has anyone used the "dconf" app? I head it is able to modify that panel which is called the "user menu" apparently :-?

---

### Post by Lisiano on 2011-10-15
Are you running 11.10 or 11.04? In 11.10 the E-Mail, IM and status is inside a single app-indicator called [Indicator Messages](apt://indicator-messages)(Click name to start USC). Removing it will remove the envelope icon.
As for the Status one, I don't remember the Natty package for it, in Oneiric it's integrated into the Envelope icon so the Status is just the user with a user list now.

---

### Post by Calerid on 2011-10-15
Well, hmm there hasssss to be a way. I will keep looking the webs. I am not sure what this article is saying, it does sound like you can make it disappear.

 [http://www.omgubuntu.co.uk/2011/07/ubuntu-11-10-menu-goodbye/](http://www.omgubuntu.co.uk/2011/07/ubuntu-11-10-menu-goodbye/)

I do not know if I misread the article. Well I will look over my sources some more and ask around. Hope we can find a solution. good luck in the mean time :P

---

### Post by d4m1r on 2011-10-15
> **Lisiano said:**
> Are you running 11.10 or 11.04? In 11.10 the E-Mail, IM and status is inside a single app-indicator called [Indicator Messages]("apt://indicator-messages")(Click name to start USC). Removing it will remove the envelope icon.
As for the Status one, I don't remember the Natty package for it, in Oneiric it's integrated into the Envelope icon so the Status is just the user with a user list now.

I am running 11.04, isn't it evident from the picture? ;)

@Calerid, ok please update this if you find anything and I will too!

---

### Post by dave01945 on 2011-10-15
have you tried removing or have you alredy removed

evolution-indicator

and

indicator-me


```
sudo apt-get remove evolution-indicator indicator-me
```

---

### Post by Lisiano on 2011-10-15
Judging from the article, removing [Indicator Messages](apt://indicator-messages) and [Indicator Me](apt://indicator-me) should do the trick. Note the names are links to Ubuntu Software Center.

---

### Post by d4m1r on 2011-10-15
[This guide  ]("http://shortrecipes.blogspot.com/2011/04/ubuntu-1104-natty-narwhal-how-to-remove.html")worked like a charm :mrgreen:

---

