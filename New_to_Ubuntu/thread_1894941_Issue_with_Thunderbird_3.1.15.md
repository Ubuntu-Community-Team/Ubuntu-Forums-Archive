---
title: "Issue with Thunderbird 3.1.15"
date: 2011-12-13
forum: New to Ubuntu
---

### Post by ClientAlive on 2011-12-13
I have this issue with Thunderbird where one of my email accounts will receive but not send. It's my student email account so it's an account that I have to have and use on a regular basis. I've contacted the help desk at my campus several times throughout the semester and they have been as helpful as they can over the phone but the situation is still unresolved. Their position is that they do not support any email client so any help they do give is on their grace to do so. They want me to bring the computer to the campus which is 45 miles away from me and I don't have the ability to do that right now. Even if I did they would keep my computer for some indeterminate period of time and get to it if/ when they could. I would be without a computer and it in a town 45 miles away. I really need help with this if someone can walk me through it.

Some information that may be of use follows:

/*When attempting to send mail throught this account I get the following error message:*/

Sending of message failed.
The Kerberos/GSSAPI ticket was not accepted by the SMTP server pluto.dsu.edu. Please check that you are logged in to the Kerberos/GSSAPI realm.

/*Upon opening the app this morning:*/

mail server at "myusername@pluto.dsu.edu is not an IMAP4 mail server" //Quoted part is exact. Not quoted is best could remember.

/*Links*/

[http://help.dsu.edu/examples/smtp.htm](http://help.dsu.edu/examples/smtp.htm)
[http://support.dsu.edu/email/popimap.htm](http://support.dsu.edu/email/popimap.htm)

---

### Post by jtarin on 2011-12-13
Is your mail server IMAP or POP?

---

### Post by alphacrucis2 on 2011-12-13
> **ClientAlive said:**
> I have this issue with Thunderbird where one of my email accounts will receive but not send. It's my student email account so it's an account that I have to have and use on a regular basis. I've contacted the help desk at my campus several times throughout the semester and they have been as helpful as they can over the phone but the situation is still unresolved. Their position is that they do not support any email client so any help they do give is on their grace to do so. They want me to bring the computer to the campus which is 45 miles away from me and I don't have the ability to do that right now. Even if I did they would keep my computer for some indeterminate period of time and get to it if/ when they could. I would be without a computer and it in a town 45 miles away. I really need help with this if someone can walk me through it.

Some information that may be of use follows:

/*When attempting to send mail throught this account I get the following error message:*/

Sending of message failed.
The Kerberos/GSSAPI ticket was not accepted by the SMTP server pluto.dsu.edu. Please check that you are logged in to the Kerberos/GSSAPI realm.

/*Upon opening the app this morning:*/

mail server at "myusername@pluto.dsu.edu is not an IMAP4 mail server" //Quoted part is exact. Not quoted is best could remember.

/*Links*/

[http://help.dsu.edu/examples/smtp.htm](http://help.dsu.edu/examples/smtp.htm)
[http://support.dsu.edu/email/popimap.htm](http://support.dsu.edu/email/popimap.htm)

So what client do they support. They should have a doc for configuring the supported client from which it should be easy to figure out how to configure thunderbird. Your initial error message sound like a problem with the authentication of the connection to the smtp server (smtp is used for sending mail). If you didn't get the second error originally then something has changed either at your end or theirs.

---

### Post by ClientAlive on 2011-12-13
> **jtarin said:**
> Is your mail server IMAP or POP?

The only info I have is what's contained about it in those two links in my op. The one: [http://support.dsu.edu/email/popimap.htm](http://support.dsu.edu/email/popimap.htm)  gives information for either but the other link says at the top or it they only support imap. Interstingly, the error message I get when I start Mozilla says

> 
mail server at "myusername@pluto.dsu.edu is not an IMAP4 mail server" //Quoted part is exact. Part not quoted is best could remember.


It's interesting to me that the guys down at the help desk didn't know what the settings are supposed to be or where to find the information. They had to search for it and emailed it to me later.

> **alphacrucis2 said:**
> So what client do they support. They should have a doc for configuring the supported client from which it should be easy to figure out how to configure thunderbird. Your initial error message sound like a problem with the authentication of the connection to the smtp server (smtp is used for sending mail). If you didn't get the second error originally then something has changed either at your end or theirs.

Apparently they only support logging in over the internet. I have 5 other email accounts I manage though. It would be horribly inconvenient if I had to do that. One solution they wanted me to do was have it forward through some other, free account (like hotmail or something). I don't like that idea because I'm trying to keep this email free from garbage, spam and the like. It's my school email, so it's kinda sacred.

I haven't had a chance to try what's at that guide (one of the links in my op) or to verify a certain suspicion I have but I'm going to do that now and will report back. It appeared to me that Mozilla had changed settings back to default after we had configured that details yesterday afternoon. Don't quote me on that though, I'll know more certain in a about 15 min here.

---

### Post by ClientAlive on 2011-12-13
Interesting new development. Never got as far as trying to make sure the settings are right. I logged on over the internet and noticed something in my drafts folder that I did want to go out. When I opened it and clicked the send button I get the following error message:

> 
You don't have the permissions required to send messages from this mailbox.


That's not from Mozilla, it's from the web client (over the internet). They must have something wrong with my account or settings down there on my school's server. I'm gonna call them tomorrow and tell them about it.

---

