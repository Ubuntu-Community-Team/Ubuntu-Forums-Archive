---
title: "Email web forms?"
date: 2011-02-18
forum: Programming Talk
---

### Post by billdotson on 2011-02-18
So, I've always wondered, couldn't you just send an email from any address through a web form? Many of the ones I've seen only require a name, the sender email and the recipient email. What stops someone from putting in some bogus name (or even the right name that goes with the email if they know it) and sending an email? I haven't done really any web programming so I am unsure.

Thanks.

---

### Post by Grenage on 2011-02-18
Are you talking about the sort of forms that are used for customer feedback?  Most of these forms are coded to send mail to a particular destination, and the sender address is really only used so that the recipient can reply to you.

---

### Post by billdotson on 2011-02-18
I guess. What made me think of it is an add-on I have for Firefox that takes the main text on the page (just the article part of an article for instance) and formats it in an easier to read way. Then, there is an icon you can press to "Share". You put in your name, email address and the recipient email, along with an optional comment.

---

### Post by hakermania on 2011-02-19
These mails are sent with PHP usually....

---

### Post by sneakyimp on 2011-02-19
If it's an add-on for firefox, it's probably using your local machine to send the mail.

Most PHP forms *should* be engineered to avoid spam practices.  If they're not, spammers quickly locate them and use them to send spam mail.  The anti-spam hardening in practice is a pretty thoughtful exercise.  You either have to limit the message content to something very specific or you have to limit the recipient using captcha or something.

---

### Post by billdotson on 2011-02-19
So would a spam message from a poorly designed PHP form have a forged header (I don't know a lot about hacking, etc.)

I don't think the Firefox add on connects to Thunderbird or anything actually.

---

