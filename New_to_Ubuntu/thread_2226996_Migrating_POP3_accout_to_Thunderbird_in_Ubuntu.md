---
title: "Migrating POP3 accout to Thunderbird in Ubuntu"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by erich4 on 2014-05-30
Hi. First, I apologize if this has already been asked. I could not find it on the forum if it has.

I just got Ubuntu for the first time. I previously had Outlook on my Windows XP. It was provided through my local service provider, Telus, in Canada. I believe it is POP3. I tried to migrate it to the Thunderbird email in my new Ubuntu set up. I filled in the automatic info, and it looked ok. Currently, I can send emails from my old email address, so that's all good. But I cannot receive emails-it is not downloading them.

When I first log in I get the following message: "The Kerberos/GSSAPI ticket was not accepted by the POP server. Please check that you are logged in to the Kerberos/GSSAPI realm."

This message also pops up when I hit "Get Mail" in the Inbox. I have no idea what to do next. Any help is SUPER appreciated. If this issue has already been dealt with please direct me to the appropriate thread. Also, I'm not a computer expert, I only have a layman's knowledge. Thanks!!!!!

---

### Post by Vladlenin5000 on 2014-05-30
Hi, welcome.

The setup you previously used in your Microsoft Outlook should work as well in Thunderbird and it's OS independent. Please check if you still have the Windows XP with the Outlook properly configure and/or contact your service provider. 
Note: Unlike what happens with IMAP, emails already downloaded and deleted from the POP3 server can only be retrieved from the software - email client - that handled them. This is unrelated with new emails. New ones should be download as before provided the email client - Outlook, Thunderbird or any other - is properly configured.
Keep in mind some providers require atypical settings (special authentication method, special ports, etc.).

Last but not least, your question has little to nothing to do with Ubuntu. Thunderbird is multiplatform. Had you installed it in Windows you would have stumbled in the same issue.

---

### Post by amanchesterman on 2014-05-30
Suggest you look on the Telus website. They give you the correct settings there to work with any email client. The default settings proposed by the Tbird automatic setup wizard aren't always correct.

---

### Post by buzzingrobot on 2014-05-30
Be sure you have the account set up with the correct ports, server names, authentication and encryption options.  The provider's site should specify those. 

Don't know aout the Kerberos error, but here's something from the Mozilla site: [https://support.mozilla.org/en-US/questions/996304](https://support.mozilla.org/en-US/questions/996304). (That this references Win8 should not make a difference.)

In Thunderbird, look for the entry to change account settings under "Edit" in the menu. (The current Thunderbird defaults to not showing the menu bar, so if it isn't there right click the three-barred logo in the right corner, select Preferences and enable the Menu Bar.)

---

### Post by Drowz0r on 2014-05-30
I always prefer having an e-mail address that isn't linked to my provider, so if I change provider I keep my mail address or avoid changes for keeping it.

mail.com have some pretty good ones, just fyi.

---

### Post by erich4 on 2014-05-30
Thank-you everyone for your input and help. It's all very useful. I apologize that my question wasn't specific to Ubuntu-I didn't realize Thunderbird was independent of Ubuntu, as it came automatically with the Ubuntu version I downloaded.

It sounds like I should contact my provider, Telus, and see that I have it configured to work with their service. I'm sure a tech there can help out. Thanks again!

---

### Post by buzzingrobot on 2014-05-30
> **erich4 said:**
> 
It sounds like I should contact my provider, Telus, and see that I have it configured to work with their service. I'm sure a tech there can help out. Thanks again!

Many customer service shops at ISP's are Windows-only, with grudging and/or bad Linux advice, if they just don't say they don't support Linux.

In any case, what you are after, at this point, are the correct IMAP and SMPT server names for Telus (SMTP is outgoing mail), the port number each uses, the encryption they use to make the connection (Thunderbird calls this "Connection Security"; it wil be "None", StartTls", or "SSL/TLS"), and authentication method (Thunderbird has an entry for kerberos of you need that).

Those settings should be available at the Telus site.  Nothing at all unusual or Windows-specific about the settings parameters needed. (In Thunderbird, it's Edit->Account Settings->Server Settings.  The SMTP settings are in the "Outgoing Server (SMTP)" panel.  You'll see it.)

---

