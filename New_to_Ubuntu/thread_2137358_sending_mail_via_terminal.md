---
title: "sending mail via terminal"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by sniper8752 on 2013-04-20
I am trying to send mail via the terminal following [this tutorial]("http://www.webupd8.org/2009/11/use-gmail-to-send-emails-from-terminal.html").  I get the error saying "send-mail: Authorization failed....").  I double checked my username/password, and it was fine.  What else could I be missing?

---

### Post by HeroOfCanton on 2013-04-20
Are you able to receive mail okay? If so, try changing the port you're using for outgoing mail. I always have issues with my ISP blocking SMTP ports because apparently they think every person in the world uses webmail exclusively. :rolleyes: Quick change of the port number and it works fine.

---

### Post by sniper8752 on 2013-04-20
I use the web interface in gmail, and it seems to work ok, if that's what you mean.  what port should I try?  i am uinsg 465, and made sure that UseTLS is set to yes.

here is my configuration file:

```
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=postmaster

# The place where the mail goes. The actual machine name is required no
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=mail

# Where will the mail seem to come from?
#rewriteDomain=

# The full hostname
# hostname=raspberrypi

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
#FromLineOverride=YES

root=username@gmail.com
mailhub=smtp.gmail.com:465
rewriteDomain=gmail.com
AuthUser=username
AuthPass=password
FromLineOverride=YES
UseTLS=YES
```

---

### Post by HeroOfCanton on 2013-04-20
You can give any port number a shot. Really depends on how gmail's servers are setup. Not sure what they allow personally. Looking at your config, I'm kind of doubting that's your issue now... Normally it's the standard SMTP port 25 that ISP's block, not 465.

Here's something interesting though:
I see on my personal gmail settings that the outgoing server is *smtp.googlemail.com* not smtp.gmail.com.

Might want to give that a shot for your mailhub setting.

---

### Post by prodigy_ on 2013-04-20
Try mailx instead: [http://www.bogh.us/doc/mailx_gmail/](http://www.bogh.us/doc/mailx_gmail/)

---

### Post by sniper8752 on 2013-04-20
> **HeroOfCanton said:**
> You can give any port number a shot. Really depends on how gmail's servers are setup. Not sure what they allow personally. Looking at your config, I'm kind of doubting that's your issue now... Normally it's the standard SMTP port 25 that ISP's block, not 465.

Here's something interesting though:
I see on my personal gmail settings that the outgoing server is *smtp.googlemail.com* not smtp.gmail.com.

Might want to give that a shot for your mailhub setting.

When I use a port, such as 25, it says that it cannot open that address.  Changing to googlemail didn't seem to help.

---

### Post by sniper8752 on 2013-04-20
> **prodigy_ said:**
> Try mailx instead: [http://www.bogh.us/doc/mailx_gmail/](http://www.bogh.us/doc/mailx_gmail/)

how do I install it?

EDIT:  Nevermind; It looks like I have it installed already.

---

### Post by sniper8752 on 2013-04-20
For some reason, it still has the send-mail: authorization failed.  what should I do about that?

---

### Post by prodigy_ on 2013-04-20
Not sure. I tested mailx with my Gmail account just recently and it worked fine.

---

### Post by sanderj on 2013-04-20
What is your goal? Use a one-liner to send a mail via a smart-host? If so, I advice to use [https://code.google.com/p/mailsend/](https://code.google.com/p/mailsend/) ... works for me.

Usage:

```
echo "Hello, this is a test" | mailsend -smtp  gmail-smtp-in.l.google.com -f [email]blabla@telfort.nl[/email] -t [email]evaq@gmail.com[/email] -sub Testing -v
```

HTH

---

### Post by sniper8752 on 2013-04-20
> **sanderj said:**
> What is your goal? Use a one-liner to send a mail via a smart-host? If so, I advice to use [https://code.google.com/p/mailsend/](https://code.google.com/p/mailsend/) ... works for me.

Usage:

```
echo "Hello, this is a test" | mailsend -smtp  gmail-smtp-in.l.google.com -f [EMAIL="blabla@telfort.nl"]blabla@telfort.nl[/EMAIL] -t [EMAIL="evaq@gmail.com"]evaq@gmail.com[/EMAIL] -sub Testing -v
```

HTH

I can use attachments?  does it use any type of security?

how does it compare to sendmail?

---

