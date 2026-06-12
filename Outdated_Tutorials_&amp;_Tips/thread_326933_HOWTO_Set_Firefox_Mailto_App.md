---
title: "HOWTO: Set Firefox Mailto App"
date: 2006-12-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Nick Rivers on 2006-12-28
I came across a very easy method for setting your desired mailto: application in Firefox and I thought I would share it since it seems to be a recurring question in the forum.

Open Firefox and in the address box, type
```
about:config
```
and hit Enter

Then in the browser window Right-click --> New --> String 

In the dialog box, type 
```
network.protocol-handler.app.mailto
```
and click OK.

In the next dialog box, type 
```
/path/to/your/preferred/mail/application
```
and click OK.

Yes, it's just that simple. :)  I hope this helps.

---

### Post by jis on 2007-09-12
In Xubuntu, you would type exo-open in "the next dialog box" to follow the Mail Reader setting set in the (Xfce menu) Application > Settings > Preferred Applications.

BTW. sylpheed-claws is faster to launch than thunderbird. I wish there were newer version available in ubuntu repositories. New versions of the mail client is called Claws Mail: [http://www.claws-mail.org/](http://www.claws-mail.org/). Anyway, you can install Claws Mail from [http://www.claws-mail.org/downloads.php?section=downloads](http://www.claws-mail.org/downloads.php?section=downloads)

---

### Post by djgrandmarquis on 2007-09-29
Thanks Nick.

For Gmail users, you can write a little script that opens Gmail as your default mail client.

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

---

### Post by MountainX on 2008-01-23
> **djgrandmarquis said:**
> Thanks Nick.

For Gmail users, you can write a little script that opens Gmail as your default mail client.

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

Thanks!

---

### Post by spadewarrior on 2008-06-04
I can't get this to work with Xubuntu and Claws-Mail.

Can anybody explain how to use exo-open?  I have specified that Claws is my preferred mail client but it doesn't load when I click on email addresses.

---

### Post by jis on 2008-06-06
In terminal you would use exo-open like
exo-open mailto:recipient@email.address
or 
exo-open [email]recipient@email.addr[/email]ess

exo-open binary is located at /usr/bin

Anyway, I have problems to get it work in Firefox, too. I am using FF 3.0b5 in Hurdy. Yahoo! mail is launched by clicking mailto-links, instead. Maybe it has something to do with gecko.handlerService.schemes.* fields in about:config?

---

### Post by jis on 2008-06-06
spadewarrior, do you get a dialog tittled Launch Application when you click a mailto link?

P.S. I suppose you are using Firefox 3 beta 5.

---

### Post by jis on 2008-06-06
There is a way to get Launch Application dialog back:
[http://groups.google.fi/group/mozilla.support.firefox/browse_thread/thread/ea9cf4bab675ec40?hl=fi#](http://groups.google.fi/group/mozilla.support.firefox/browse_thread/thread/ea9cf4bab675ec40?hl=fi#)

---

### Post by spadewarrior on 2008-06-06
Thanks, that's sorted it out.

---

### Post by SocratesTNR on 2008-11-22
> **djgrandmarquis said:**
> Thanks Nick.

For Gmail users, you can write a little script that opens Gmail as your default mail client.

[http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/](http://www.howtogeek.com/howto/ubuntu/set-gmail-as-default-mail-client-in-ubuntu/)

Thanks for that...

Got a little confused with

**Open terminal and type chmod u+x ~/open_mailto.sh**

This is what I had to type to get it to work:

root@TheNewRepublic:/home/harry# chmod u+x open_mailto.sh

Newbe, so don't understand quite what's going on.

---

