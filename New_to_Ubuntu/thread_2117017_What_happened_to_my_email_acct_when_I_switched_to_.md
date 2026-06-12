---
title: "What happened to my email acct when I switched to Thunderbird?"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by skcgirl on 2013-02-17
So a few months ago I decided to make the switch from Windows to Linux. So far it's been pretty good (definitely miss the Calibri font in LibreOffice but that's ok) but can't seem to figure out how to resolve an issue with my email account.

My apologies if this is located in another thread but I couldn't find one that was close enough to my issue to resolve on my own. So here it goes.... I use AT&T's email service and when I started using Thunderbird for this email account, I completely lost the ability to see my old emails if I'm checking it on my iPhone, iPad or Windows. Additionally, when I check my emails on either of those other devices, it seems like they're only being stored for about 30 or so days max. However, if I check my emails in Thunderbird, all my emails are there and haven't been or are being deleted.

This is ok, except for the fact that I seem to have no way to check my emails on Thunderbird using my iPhone or iPad and since my Ubuntu is installed on my desktop which is at home, this makes checking emails on the go, a bit challenging.

Does anyone know if there's a way to get my email account to synchronize on all my devices OR if there's a way to check Thunderbird using Apple devices? Sorry for the long novel of a post, thanks in advance for your help!

---

### Post by MrKaliman on 2013-02-17
Are you using POP or SMTP ?

Make sure that all you devices are configured as SMTP.

---

### Post by skcgirl on 2013-02-17
[FONT=Arial]Hi Mr. Kaliman,[/FONT]
[FONT=Arial]Thanks for the suggestion, I just checked and it looks like the email acct on my iPhone and iPad's were previously set to SMTP. [/FONT]

[IMG]http://i48.tinypic.com/s60yon.png[/IMG]

---

### Post by presence1960 on 2013-02-17
In Account settings for thunderbird (Edit > Account settings) select the email account in question. In server settings make sure "Leave Messages on Server" is checked. Then select the timeframe to leave or until I delete them. You should now be able to view from other devices any messages from this point forward.

If this is not selected the messages are deleted from your email account server and downloaded to the disk of the device you used.

---

### Post by skcgirl on 2013-02-17
Just as soon as I typed my last post, I realized I also needed to check the Thunderbird acct and low and behold you guys were absolutely correct!! The Thunderbird one was set to POP and was set to delete after 14 days?! :confused: 
Wow, thank you so much Presense1960 and Mr.Kaliman!!! I've unchecked the 14 days and have it set to delete when I ask it to. That should do the trick now! :D I love this forum and the awesome people who make it so great. Have a great day!

---

### Post by MrKaliman on 2013-02-17
In the previous post I mentioned POP vs SMTP, it is not SMTP but IMAP that need to be configured. Hence Glad to read that the problem is solved.

---

