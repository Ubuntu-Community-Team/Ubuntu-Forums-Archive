---
title: "help accessing a website"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by n0chi on 2008-05-20
hello all,
I am new to ubuntu and I am trying to access the following BU site from Firefox 2 in ubuntu 8.04

[http://vista42.bu.edu/](http://vista42.bu.edu/)

Initially it turns out my JRE was not installed properly and after LOTS of research :) I learned how to install a symbolic link and got that problem sorted out (as you can see from my attached screenshot)

so What happens is... I go to the above site and click the "Login" (or any of the 10 links on the right) and they go nowhere... I am just left on that page forever... I never get to the next site which asks for my ID and pass.

Also I noticed this error in Firefox... might be useful... not sure:
something about "nsextensionmanager.js" not installed

(I am suspecting that the javascript of that site is getting messed up?)

not sure...

Thanks!

---

### Post by Thirtysixway on 2008-05-20
Hm... I see a box that says Login and
```

Access to Vista requires your BU login name and Kerberos password. Your username is your BU email address without "@bu.edu".

```

It's not asking me about java, and it doesn't look to me that there's any java on the login screens.

---

### Post by n0chi on 2008-05-20
> **Thirtysixway said:**
> Hm... I see a box that says Login and
```

Access to Vista requires your BU login name and Kerberos password. Your username is your BU email address without "@bu.edu".

```

It's not asking me about java, and it doesn't look to me that there's any java on the login screens.

cool, so its that second screen that I cant see... any thoughts on what might be stalling my browser?

i guess what I am asking is... what are those sites using... and how do I get that functionality to work in my environment?

---

### Post by Thirtysixway on 2008-05-20
It may be a Javascript problem.  Looking at the source..
```

<button class="submit" name="login" type="button" onclick="window.location = 'http://www.bu.edu/phpbin/vista/cluster41/index.php'">

```
It's using Javascript to redirect you to the login page.

Try going to [http://www.bu.edu/phpbin/vista/cluster41/index.php](http://www.bu.edu/phpbin/vista/cluster41/index.php) and see if that loads for you.

---

### Post by n0chi on 2008-05-20
> **Thirtysixway said:**
> It may be a Javascript problem.  Looking at the source..
```

<button class="submit" name="login" type="button" onclick="window.location = 'http://www.bu.edu/phpbin/vista/cluster41/index.php'">

```
It's using Javascript to redirect you to the login page.

Try going to [http://www.bu.edu/phpbin/vista/cluster41/index.php](http://www.bu.edu/phpbin/vista/cluster41/index.php) and see if that loads for you.

Doesn't load :(

also, how did you get a screenshot of just the browser?

---

### Post by Thirtysixway on 2008-05-20
What does the page display when you say it doesn't work?

::Hold down ALT and press the PRINTSCREEN button [above the num lock key] and it should bring up the screenshot but only for the current active window.  Print Screen button alone does the entire screen ;)

---

### Post by n0chi on 2008-05-20
> **Thirtysixway said:**
> What does the page display when you say it doesn't work?

::Hold down ALT and press the PRINTSCREEN button [above the num lock key] and it should bring up the screenshot but only for the current active window.  Print Screen button alone does the entire screen ;)

this link:
[http://www.bu.edu/phpbin/vista/cluster41/index.php](http://www.bu.edu/phpbin/vista/cluster41/index.php) 

looks like the attached picture...

---

### Post by Thirtysixway on 2008-05-20
At the bottom of your screenshot it looks like it's not finding the server, so perhaps it's a DNS issue.  Are you currently at school or somewhere else?  I'm not quite sure how to fix this other than maybe switching DNS servers.


Last resort, try
[https://weblogin.bu.edu//web@login3?jsv=1.5p&br=un&fl=6](https://weblogin.bu.edu//web@login3?jsv=1.5p&br=un&fl=6)

That's what it should be turning into.

---

### Post by n0chi on 2008-05-20
hmm now that you mention it.... I cant even get to [www.bu.edu](www.bu.edu) lol...

im off campus.

---

### Post by Thirtysixway on 2008-05-20
Yeah so it must be some dns issue.  It may fix later, or you could try different dns servers

OpenDNS
```

1. Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

```
[https://www.opendns.com/start?device=ubuntu#step1](https://www.opendns.com/start?device=ubuntu#step1)

Sorry I can't really give any more information :\

---

### Post by n0chi on 2008-05-20
tired those dns numbers, still the same problem :(

thanks for your help!

---

### Post by n0chi on 2008-05-22
> **n0chi said:**
> tired those dns numbers, still the same problem :(

thanks for your help!

what does this error mean?

Error: installLocation has no properties
Source File: file:///usr/lib/firefox/components/nsExtensionManager.js
Line: 3938

---

### Post by n0chi on 2008-05-31
also its bizzare that only [http://www.bu.edu](http://www.bu.edu) seems to not work... all other sites that i need seem to be going through ok!

Any idea why that could be?

---

### Post by james_vanb on 2008-05-31
Your first screen shot seems to indicate that Java not being detected.  I've been able to open all links in this post with no problems using Firefox 3 Beta 5 from Hardy.  At the risk of asking the painfully obvious, have you checked to make sure Java is updated?

```
sudo apt-get install sun-java6-fonts sun-java6-plugin
```

May be worth a shot checking.

Or upgrade Firefox if you're using Hardy?

---

### Post by n0chi on 2008-06-03
I just dont have the latest (version 6) of java, as the site I need works best on version 5, but I do have version 5 installed properly (as you can see in my frist post)

EDIT... also I have tried other borwsers as well and they seem to be having the same issue... so its something to do with the settings of ubuntu... I think!

---

