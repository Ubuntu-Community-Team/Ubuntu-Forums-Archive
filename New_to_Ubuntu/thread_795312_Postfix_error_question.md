---
title: "Postfix error question"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by mrhinman on 2008-05-15
It seems of late my mail is not going out:

This is the Postfix program at host ***myubuntuserver***.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to <postmaster>

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

			The Postfix program

<recipient@otherhost.com>: host otherhost.com[***.205.3.131] said: 554
    <recipient@otherhost.com>: Relay access denied (in reply to RCPT TO command)

Can anyone assist with this?  I'm clueless here.

---

### Post by Monicker on 2008-05-15
The remote server rejected the email message because the sender was not authorized to send it to that machine for delivery.

---

### Post by mrhinman on 2008-05-15
> **Monicker said:**
> The remote server rejected the email message because the sender was not authorized to send it to that machine for delivery.

I'm confused.  I own both the sending and receiving servers, although the receiving server is remotely hosted.  It was working before, now I'm totally lost.

The originating server is on a static IP and uses a dyndns.org address also.  I'm running Postfix but now I'm wondering if I should revert to Sendmail since it's not working anymore.

A solution would be helpful here, or point in the right direction.  I know virtually nothing about mail servers, so this is new ground for me.

---

### Post by Monicker on 2008-05-15
In my opinion, Postfix is much easier to use than Sendmail, but that is your choice.  :)

You will need to check the log files on the remote server to see exactly why it would not relay the message to its final destination.  The postfix config file also has a section for "trusted networks" for which it will deliver email; these can be individual ip address, or network ranges.

See this documentation for more details:  [http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from]("http://www.postfix.org/BASIC_CONFIGURATION_README.html#relay_from")

If it worked before, I would look into what has changed recently.

---

