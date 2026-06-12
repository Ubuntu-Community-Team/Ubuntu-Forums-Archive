---
title: "LAMP Server + Static ip address + Wordpress test website + Contact Us form not workin"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by adamjedgar on 2014-02-10
Hi guys,
i have installed a VM Virtual box LAMP server (Unbuntu 13.10 desktop) on static ip address.
It is running a test wordpress website that once is finished i plan on sending up to another web server in a datacentre.

I have setup a contact US form on the wordpress website, however, when i attempt to test the contact us form...no email is sent to the default email address. I also did a check yesterday by clicking the "forgot password" button on admin logon screen in wordpress and that isnt working either. Someone told me that the problem is with the mail function on the ubuntu LAMP.

I installed Dovecot...but it doesn't seem to want to work...i get a time out error when i telnet.

Looking at the wiki, im not really sure what to do as it says the following...
[INDENT]**Choice of Protocols**
[COLOR=#333333][FONT=Ubuntu]Once you have chosen, amend the following line in the file [/FONT][/COLOR]**/etc/dovecot/dovecot.conf**[COLOR=#333333][FONT=Ubuntu]:
[/FONT][/COLOR]protocols = pop3 pop3s imap imaps1. [/INDENT]

There is no line with the following information on it in the dovecot.conf???
2. Also, should i be using the Dovecot or DovecotLDAP for a wordpress test site? 
3. What is the difference between the two?
4. As i am a newbie, should i use a different mail app?


kind regards,
adam
[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]

---

### Post by sandyd on 2014-02-10
Hi, what page in the wiki are you using

---

### Post by adamjedgar on 2014-02-10
> **sandyd said:**
> Hi, what page in the wiki are you using

I installed the ubuntu mail stack

went to the dovecot wiki
[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

1. Does my server actually need any of this in order for the Wordpress Contact Us form, and lost my password button, to work?

2. Also, after installing the Ubuntu mail stack i tried to 

telnet localhost pop3

"start dovecot" i get an error saying "unkown job: Dovecot"

"telnet localhost imap2" produces and error saying "unable to connect to remote host: connection refused"


3. Are the above errors related to the missing protocols line "[COLOR=#333333][FONT=UbuntuMono]protocols = pop3 pop3s imap imaps"[/FONT][/COLOR] in "/etc/dovecot/dovecot.conf" referred to in my first post?

---

