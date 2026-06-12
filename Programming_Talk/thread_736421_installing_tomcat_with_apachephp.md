---
title: "installing tomcat with apache/php"
date: 2008-03-26
forum: Programming Talk
---

### Post by shendric on 2008-03-26
Hey all,

I'm currently running Apache and php with mysql on my 7.10 machine.  It's looking like I may need to learn to use JSP for some web application development for work, and so I'm looking to install tomcat.

Are there any particular pitfalls I should be aware of when installing tomcat onto such a system?

---

### Post by nitro_n2o on 2008-03-26
apt is great and should do everything right you just sudo apt-get install tomcat unless you have installed apache and php from source. In this case you either install tomcat from source, or look up apt documentation on how to make packages compiled from source visible to apt

---

### Post by shendric on 2008-03-26
Sounds good.  I was probably going to just use Synaptic, which is more or less the same thing, as I understand it.  Having never run tomcat, I wanted to make sure I wasn't about to do a "bad thing".

---

### Post by Kadrus on 2008-03-26
Read this Ubuntu documentation..just in case..
[https://help.ubuntu.com/community/ApacheTomcat5](https://help.ubuntu.com/community/ApacheTomcat5)
Everything should be alright from there..

---

### Post by shendric on 2008-04-02
I've been able to install tomcat 5.5 and it works just fine, but when I try to install struts 2 applications, I can't seem to get it to work.

I downloaded struts 2.0.11.1 and in the Tomcat Manager, I've selected the struts blank WAR file.  When I deploy it, the Manager says ok, but when I try to view the page or start it in the Manager, I get the following message:

FAIL: application at context path /struts2-blank-2.0.11.1 could not be started

Any help would be appreciated.

---

### Post by pmasiar on 2008-04-02
Struts is a bear. The most ridiculous web app framework I know. I treid to learn it for couple months, then gave up, paid $50 for MyEclipse plugin which knows how to handle Struts, borrowed some code tricks (LazyDynaBean) to fetch query parameters - and I am up and running without understanding how Strut's wizard in MyEclipse does it. Yes, I was embarrased, but I just gave up.

Compared to that, I installed TurboGears and within hour I was hacking on my code, and it was obvious what to change and where (even if you need to learn, but at least it is more obvious what is going on).

Avoid Java/Struts for web apps if you can. Even crap like PHP is better that that.

Struts is for web app with 10K pages, complicated validation, and stuff. Chances are, your app is much smaller - but Struts does not scale down, you have to set it up like you will have 10K pages.

</rant>

---

### Post by LaRoza on 2008-04-02
> **pmasiar said:**
> 
Struts is for web app with 10K pages, complicated validation, and stuff. Chances are, your app is much smaller - but Struts does not scale down, you have to set it up like you will have 10K pages.


It is for work, so it may be not an option.

---

### Post by CptPicard on 2008-04-02
And once again I must chime in that Struts is about the worst example of a Java web framework there is. Spring is much more modern in approach, and helps you a lot with your integration needs. That said, Java on the web still is too cumbersome, but Spring at least tries to take most of the pain away.

---

### Post by shendric on 2008-04-02
While I can appreciate the difficulties with Struts, it is the framework that I will be using because of work constraints, so I have little choice in the matter.  I suppose I'll just have to work on Windows for this, unless I can get Struts2 working on my Ubuntu box.  I was able to get Struts 1.3.8 to work just fine, but Struts 2 refuses to function.

---

### Post by pmasiar on 2008-04-02
> **shendric said:**
> Struts, it is the framework that I will be using because of work constraints, so I have little choice in the matter.

Sucks to be you (and me). At least get the MyEclipse plugin, is well worth $50 - and work may even pay for it. Even if not, it will save you more than 2 hours of work.

---

