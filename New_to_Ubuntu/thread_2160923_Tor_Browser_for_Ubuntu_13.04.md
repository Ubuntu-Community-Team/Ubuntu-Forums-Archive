---
title: "Tor Browser for Ubuntu 13.04"
date: 2013-07-08
forum: New to Ubuntu
---

### Post by Traxster on 2013-07-08
Hi folks,

installed tor browser bundle from ppa, everything  worked find except for last step. where you have to change ownership of the .tor-browser folder. 

Here is the command listed    **sudo chown $USER -Rv ~/.tor-browser/     **however when I enter it in terminal I receiveerror message below.


chown: missing operand after '/home/fmb/.tor-browser/'
  

Can anyone tell me what I may doing wrong? 

thanks in advance

traxster

---

### Post by Curtis6767 on 2013-07-08
From Tor's wikipedia page:

"As of 2012, 80% of the Tor Project's $2M annual budget comes from the [United States government]("https://en.wikipedia.org/wiki/United_States_government"), with the [Swedish government]("https://en.wikipedia.org/wiki/Swedish_government") and other organizations providing the rest."

No idea how to install it. Not interested. There is no anonymity on the internets.

GL

---

### Post by dannyboy79 on 2013-07-08
i believe you have an extra slash on there. try sudo chown $USER -Rv ~/.tor-browser

---

### Post by Traxster on 2013-07-08
> **Curtis6767 said:**
> From Tor's wikipedia page:

"As of 2012, 80% of the Tor Project's $2M annual budget comes from the [United States government]("https://en.wikipedia.org/wiki/United_States_government"), with the [Swedish government]("https://en.wikipedia.org/wiki/Swedish_government") and other organizations providing the rest."

No idea how to install it. Not interested. There is no anonymity on the internets.

GL, 

I do believe that there are some vulnerabilities in using the tor browser, depending on what you are doing with it, however that is not what I asked, and furthermore, I disagree with your comment 'There is no anonymity on the internets'. There are ways to anonymize all of your web traffic. 


Solved: by using this command     sudo chown -R USER ~/.tor-browser

---

### Post by dannyboy79 on 2013-07-08
> **Traxster said:**
> , 

I do believe that there are some vulnerabilities in using the tor browser, depending on what you are doing with it, however that is not what I asked, and furthermore, I disagree with your comment 'There is no anonymity on the internets'. There are ways to anonymize all of your web traffic. 


Solved: by using this command     sudo chown -R USER ~/.tor-browserthat command couldn't have worked UNLESS you specifically have a user named USER. lol

---

### Post by Traxster on 2013-07-08
> **dannyboy79 said:**
> that command couldn't have worked UNLESS you specifically have a user named USER. lol


I assumed everyone would know to replace 'USER' with their username, lol

---

### Post by dannyboy79 on 2013-07-09
> **Traxster said:**
> I assumed everyone would know to replace 'USER' with their username, lol
that's why there was a $ in there, the command is ```
sudo chown $USER -Rv ~/.tor-browser
```

---

### Post by Traxster on 2013-07-14
> **dannyboy79 said:**
>  ```
sudo chown $USER -Rv ~/.tor-browser
```


That command produced an error(with my real username in place of "$USER"):lolflag: when I started the tor-browser. Point taken about the "$" though.


Traxster

---

### Post by hirumabiff14 on 2013-11-28
[FONT=Ubuntu Mono]sudo chown $USER -Rv ~/.tor-browser
[/FONT] command produced no such file or directory

---

