---
title: "Web Hosting on nown website - mail server service like Gmail"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by makandale on 2014-06-21
Hi guys, well I'm in a situation that requires guidance and advice. I have two websites hosted on a share hosting plan with a service provider, now I want to accomplish two things:  
 **1** host my websites on my own server.
 **2** Provide a mailing web service like Gmail, Yahoo and Hotmail
 so the first question is this: can I accomplish both task on one machine? (I plan on using an AMD FX 6-Core Black Edition FX-6100 &#8211; or maybe I'll use 2 FX-6100 on server motherboard) if I can't do both with one machine then i'll do the obvious decision I'll choose one. My next question is do I need Apache? I've done a few research on Google and this is what I think i'm gonna need to accomplish my tasks.

 Orporating System          Ubuntu server 12.04 LTS (precise), 14.04 LTS (trusty)   
 Mail server software          iRedMail  or hMailServer 
 Web control panel           zPanel  and Zantastico

 which takes us to my third question do I need Apache? While i'm waitting on my AMD  FX-6100 I have an old HP 500 (OS server not yet installed) I want to do some test run with some subdomains. Now can you help me with my questions?
 **1 &#8211;** can I host my websites on my own server and Provide a mailing web service like Gmail, Yahoo and          Hotmail on the same server.
 **2 &#8211; **Do I need Apache to accomplish these tasks or can I do without?

 Anticipating thanks
*necessity is the mother of all inventions  *

---

### Post by sandyd on 2014-06-21
> **makandale said:**
> Hi guys, well I'm in a situation that requires guidance and advice. I have two websites hosted on a share hosting plan with a service provider, now I want to accomplish two things:  
 **1** host my websites on my own server.
 **2** Provide a mailing web service like Gmail, Yahoo and Hotmail
 so the first question is this: can I accomplish both task on one machine? (I plan on using an AMD FX 6-Core Black Edition FX-6100 &#8211; or maybe I'll use 2 FX-6100 on server motherboard) if I can't do both with one machine then i'll do the obvious decision I'll choose one. My next question is do I need Apache? I've done a few research on Google and this is what I think i'm gonna need to accomplish my tasks.

 Orporating System          Ubuntu server 12.04 LTS (precise), 14.04 LTS (trusty)   
 Mail server software          iRedMail  or hMailServer 
 Web control panel           zPanel  and Zantastico

 which takes us to my third question do I need Apache? While i'm waitting on my AMD  FX-6100 I have an old HP 500 (OS server not yet installed) I want to do some test run with some subdomains. Now can you help me with my questions?
 **1 &#8211;** can I host my websites on my own server and Provide a mailing web service like Gmail, Yahoo and          Hotmail on the same server.
 **2 &#8211; **Do I need Apache to accomplish these tasks or can I do without?

 Anticipating thanks
*necessity is the mother of all inventions  *
Yes,it should be possible to have both on the same machine. Just make sure that your web control panels are secure. There have been lots of issues caused by control panels being hacked and the servers being compromised. One of the recent examples is Kloxo, which was compromised and the servers used to send DDOS attacks. As a result, I prefer to setup a web server without a control panel and configure using the configuration files instead.

As for Apache, you will need some kind of webserver to serve your webmail pages. All of the control panels youve listed come with some kind of webserver.

Heres a expanded list of software in addition to the above:

Web Control Panels:
VestaCP
ISPConfig
Ajenti

Mailing Software:
Axigen (Free for 100 accounts)
iRedmail
Zimbra (which is a bit heavy and requires 2G+ RAM imo)

To be honest, you would be better off letting an email provider handle your mail offsite due to the complexity of email systems - there are a few that will allow you to use your own domain such as Yandex. There are some others that are cheap such as MXRoute.

---

### Post by makandale on 2014-06-26
hi **[[COLOR=#c61919][B]sandyd**[/COLOR]]("http://ubuntuforums.org/member.php?u=717412")[/B] as I'm about to install my OS, something else run in my mind how would I transfer my web content ove to Zpanel? can I use my Cpanel backup files or something? For example a popular script like wordpress i can install a fresh one then just do a back up but what about the rest of my content and data base? how would I do that? If anyone else can assist feel free to reply.
thank you

---

