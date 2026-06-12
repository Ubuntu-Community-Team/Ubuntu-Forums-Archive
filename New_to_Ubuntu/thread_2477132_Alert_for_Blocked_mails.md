---
title: "Alert for Blocked mails"
date: 2022-07-15
forum: New to Ubuntu
---

### Post by mfaheem5697 on 2022-07-15
Need a kind of alerting/reporting in case that mails are dropped. 
 Would like to set up an alerting for the following recipient on a mca server in  case that mails are blocked based on the whitelist configuration:
[email]live-mca@mmtc-software.com[/email]
Can someone help me with this.

Note: Using Postfix

Thanks
Sameer

---

### Post by TheFu on 2022-07-15
Email delivery isn't guaranteed, ever.  If you need guaranteed delivery, use a different delivery method, like MQ-series.  There are F/LOSS implementations - like Rabbit MQ.  I don't know any other protocol that is guaranteed.  I suppose the closest would be running rsync multiple times and seeing that the 2nd attempt worked without any errors?

You could create a log watching script for the mail.log that looks for refused connections or bounced emails, but that won't help when people block at the firewall and simply drop all packets from the source.  That's what I do for some source IPs.  This eats up the spammer's CPU time and ports. They have to wait for the TCP packet timeout to know it didn't arrive. Most probably have altered the timeout from the default (30-90sec) to something like 5 seconds, so they can get onto spamming more systems.

Lots of email servers implement a greylist.  This rejects the first attempt automatically. Real email servers will wait 15-240 minutes and attempt delivery again.  In the old days (when we used overnight modem connections for email), delivery would be attempted for 4 days before returning a failed delivery message.  There is a greylist postfix addon, if you'd like to know more.

I've been running email servers since the mid-1990s.  Over all that time, things have drastically changed, mainly to deal with spammers and non-standard MTA programs.  Having some of that history can aid in understanding why things are the way they are today and certain methods used to combat spam which can break other non-standard expectations.  For example, there isn't any validation of the "FROM" field. It can be anything. It is a courtesy to have the FROM be correct, but it isn't in any standard.  Lots of people think the FROM needs to have a real domain. That isn't in the standard. Some even try to validate that the FROM is a valid email address - hah.

---

### Post by ActionParsnip on 2022-07-16
Same post is on [https://answers.launchpad.net/ubuntu/+question/702484](https://answers.launchpad.net/ubuntu/+question/702484)
I have replied there. Just something I Googled

---

