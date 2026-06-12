---
title: "web-development: an alternate to email-based verification"
date: 2008-08-22
forum: Programming Talk
---

### Post by dexter.deepak on 2008-08-22
i have a sign up module in my jsp project. email-based verification of signups has been there for quite some time now ;so i was just hoping to get something newer to implement. 
PS : i have to use something which CAN be implemented through jsp/java.

---

### Post by dexter.deepak on 2008-08-23
bump ?? am i asking this question in a wrong place ??

---

### Post by NovaAesa on 2008-08-23
Firstly, are you talking about JavaServer Pages, or Java Stored Procedures? The acronym JSP is a bit ambiguous.

---

### Post by dexter.deepak on 2008-08-23
it is meant to be java server pages; i didnt know about java stored procedures yet, thanks for that second thought..its a nice thing i would like to use.

---

### Post by tinny on 2008-08-24
> **dexter.deepak said:**
> i have a sign up module in my jsp project. email-based verification of signups has been there for quite some time now ;so i was just hoping to get something newer to implement. 
PS : i have to use something which CAN be implemented through jsp/java.

How about a text message challenge response?

E.g. The user registers their details, one of the details is a mobile phone number. 

Then instead of your system sending an email it sends a SMS message with a token number. Then the first time the user wants to login they must supply this token code (E.g. "1234")

This approach is called two factory authentication.

Post back if you are interested and I can point you in the right direction. :)

---

### Post by dexter.deepak on 2008-08-24
thanks tinny, i had actually been thinking of that alternative, but never dared to read the java sms api(s), if you could please back-support me, i can dare to touch that thing.

---

### Post by codeking on 2008-08-24
To send text messages you have to use SMPP, and you have to buy the text messages in bulk.  A easier (and free) way is to send an email to a certain email address from the service provider.  Like this: [http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/](http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/)

---

### Post by tinny on 2008-08-24
> **dexter.deepak said:**
> thanks tinny, i had actually been thinking of that alternative, but never dared to read the java sms api(s), if you could please back-support me, i can dare to touch that thing.

No SMS APIs required.

Ive used Clickatell before [http://www.clickatell.com/](http://www.clickatell.com/) (it was easy :) )

All you need to do is build a URL post. 

```

http://api.clickatell.com/http/sendmsg?user=xxxxx&password=xxxxx&api_id=xxxxx&to=448311234567
&text=Meet+me+at+home
```

> **codeking said:**
> To send text messages you have to use SMPP, and you have to buy the text messages in bulk.  A easier (and free) way is to send an email to a certain email address from the service provider.  Like this: [http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/](http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/)

SMPP is over kill. (All that PDU etc... :shock: )

Have a read of this [http://www.clickatell.com/developers/api_http.php](http://www.clickatell.com/developers/api_http.php)

BTW: When I last calculated it out it cost NZD00.07 per txt message

---

### Post by dexter.deepak on 2008-08-24
thanks for those links, but this would involve a dependency on other websites which i dont want at all. 
plus, i am not making a website for any professional use, so i cant afford to spend a penny over it..i want a free service.
thanks for all your ideas.

---

### Post by tinny on 2008-08-24
> **dexter.deepak said:**
> thanks for those links, but this would involve a dependency on other websites which i dont want at all. 
plus, i am not making a website for any professional use, so i cant afford to spend a penny over it..i want a free service.
thanks for all your ideas.

I understand why you want something that is free. But whats the problem with interfacing with another service? This is the reality of web development. :)

> **codeking said:**
> To send text messages you have to use SMPP, and you have to buy the text messages in bulk.  A easier (and free) way is to send an email to a certain email address from the service provider.  Like this: [http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/](http://www.allthingsmarked.com/2006/09/04/howto-send-free-text-messages-through-email/)

Have a look at this email approach, if it works it could be quite good.

---

