---
title: "[SOLVED] Replying to mailing lists"
date: 2008-07-24
forum: Programming Talk
---

### Post by jamesdcarroll on 2008-07-24
I know that mailing lists are a major way that open source programmers communicate, that's why I am asking this here instead General Help.

When I read a message and hit 'Reply' Evolution naturally assumes that I want to reply to the <FROM> field, when in fact I need to reply to the <TO> field.  Is there some place I can set a flag or something to change the behavior?

Thanks,

---

### Post by mssever on 2008-07-24
> **jamesdcarroll said:**
> I know that mailing lists are a major way that open source programmers communicate, that's why I am asking this here instead General Help.
 
 When I read a message and hit 'Reply' Evolution naturally assumes that I want to reply to the <FROM> field, when in fact I need to reply to the <TO> field.  Is there some place I can set a flag or something to change the behavior?
 
 Thanks,
 Just use the reply to all button. I don't know exactly what it's called since I don't use Evolution, but every decent e-mail client has such a feature.


<off-topic>I hate mailing lists. 'Twould be nice if more open source projects would switch to forums.</off-topic>

---

### Post by jamesdcarroll on 2008-07-25
Thanks, I was hoping there'd be something a little more graceful.

<off topic> Totally agree. Even NNTP would be better. But they refuse to change </off topic>

---

### Post by mssever on 2008-07-25
> **jamesdcarroll said:**
> Thanks, I was hoping there'd be something a little more graceful.
  It seems there's a debate about this subject. I think that the mailing list should set the reply-to header to the list reply address, instead of the sender. When I complained once on a mailing list that didn't mangle the reply-to header, someone sent me a link to a site explaining why mangling the header is a bad idea. They had some good points, but that doesn't change the way it should be, IMHO. So, better to use forums where there's no confusion.

Also, people on mailing lists sometimes get annoyed when you send HTML-formatted mail--even though any mail reader that can't cope with HTML mail is seriously broken. Forums avoid such issues.

---

### Post by jamesdcarroll on 2008-07-26
I found the problem: GMail.  It doesn't forward emails from yourself which posts to mailing lists appear as.

[http://groups.google.com/group/Gmail-Help-Message-Delivery-en/browse_thread/thread/7cd5c9969c1b35f8/d98ec4e21cf80bdc?lnk=raot](http://groups.google.com/group/Gmail-Help-Message-Delivery-en/browse_thread/thread/7cd5c9969c1b35f8/d98ec4e21cf80bdc?lnk=raot)

I created a sub account on my ISP and its fine.

---

### Post by lisati on 2008-07-26
There's an option in Evolution which might be helpful. The process is something along the lines of the following: Highlight the message to which you wish to respond, then click on message->mailing list. If the email has the proper headers (which depends on the mailing list) there will be an option "Post message to list" available.

---

