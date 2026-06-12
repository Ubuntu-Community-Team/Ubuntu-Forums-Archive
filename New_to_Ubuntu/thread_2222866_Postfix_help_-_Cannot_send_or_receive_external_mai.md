---
title: "Postfix help - Cannot send or receive external mail with Outlook."
date: 2014-05-08
forum: New to Ubuntu
---

### Post by Tim_Allen on 2014-05-08
As per the title.  We cannot currently send external mail from our Postfix server when we connect it to outlook.  

Outlook sends and receives mail internal to the server.  
Outlook receives mail that is sent from an external source.
Outlook fails to send to external sources and gives a relay error.

Any help would be most appreciated.

Thanks,

---

### Post by drink1297 on 2014-05-08
Can you post any errors in the logs?

Do you have the correct MX records in DNS to be able to send externally?

---

### Post by Tim_Allen on 2014-05-08
The only error that I get is from Outlook.

Your message did not reach some or all of the intended recipients.
 
      Subject:    Test
      Sent: 20/03/2014 16:21
 
The following recipient(s) cannot be reached:
 
      'XXXX@gmail.com' on 20/03/2014 16:21
            Server error: '554 5.7.1 <[EMAIL="legrimsqueaker@gmail.com"]XXXX@gmail.com[/EMAIL]>: Relay access denied'

In terms of grabbing them from the server, I'd need to get a how-2 on that.

---

### Post by drink1297 on 2014-05-08
I am not very experienced in mail, but try this, sounds like it could be an outlook issue/setting:

[http://www.zimbra.com/forums/administrators/32746-solved-cannot-send-mail-external-email-add-outlook-2007-relay-access-denied.html](http://www.zimbra.com/forums/administrators/32746-solved-cannot-send-mail-external-email-add-outlook-2007-relay-access-denied.html)

---

### Post by drink1297 on 2014-05-08
This is good to:

[http://www.virtualmin.com/node/11479](http://www.virtualmin.com/node/11479)

---

