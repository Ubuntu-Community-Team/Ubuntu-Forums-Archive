---
title: "Ubuntu &amp; Outlook"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by kegelb on 2008-07-08
I'm trying to make the switch between m$ and linux for my travel latop.  I need to know how I can connect to my companies exchange system using Ubumtu.  I currently use Outlook and connect via HTTP.  Can I do this?  IF I can how?

Thanks in advance

BK

---

### Post by st33med on 2008-07-08
That depends on what email client you would like to try.
By default, Ubuntu uses Evolution, which has an easy way to setup. But, in my opinion, it is best to use Thunderbird.

```
sudo apt-get install thunderbird
```

I am sad to say, Wine doesn't seem to run Outlook well.

---

### Post by kegelb on 2008-07-08
Thanks...i'll check out Thunderbird.  do you know if I will be able to connect to the exchange server via HTTP?

---

### Post by st33med on 2008-07-08
[http://www.downloadsquad.com/2007/03/30/howto-thunderbird-and-ms-exchange-server/]("http://www.downloadsquad.com/2007/03/30/howto-thunderbird-and-ms-exchange-server/")
Yeah, do that after installing.

---

### Post by eriqjaffe on 2008-07-08
Those instructions will only work if the mail server you are accessing allows IMAP connections (our company, for example, does not allow IMAP connections).  Check with your System Administrator to make sure your company does.

You can use Evolution, which connects via Outlook Web Access, but it's a bit flaky.

---

