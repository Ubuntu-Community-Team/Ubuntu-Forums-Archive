---
title: "Thunderbird not downloading new IMAP messages"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by Paddy Landau on 2011-10-10
I have Thunderbird set up to access my IMAP accounts on two different computers.

As far as I can see, the settings are identical.

However, on one machine (10.04), Thunderbird checks and downloads new messages from the IMAP server on starting up and every few minutes (as specified in my account settings).

But on the other machine (11.04), Thunderbird won't check for new mail unless I click on the email folder. Unfortunately, I have several folders (due to message filters on the IMAP server), so to check for new messages, I have to click (and wait) on every single folder several times a day!

Clearly, one of the settings is different -- but which one? How can I get the 11.04 Thunderbird to check for new messages automatically?

Both machines use Thunderbird 3.1.15.

---

### Post by jtarin on 2011-10-10
Would there be any harm to copy over your good settings to your problem client. (eg; /home/username/.thunderbird)?
Same mail account...just different computers??? Must be a setting to "open a folder" when you click or double click on it. I don't use Thunderbird anymore so couldn't tell you exactly.

---

### Post by Paddy Landau on 2011-10-10
Thanks for the idea, jtarin. I have recreated my account from scratch as there is a lot of dross left over from the years.

I think I will head over to the Thunderbird forums and ask there. I'll post back here when I get the answer.

BTW, even if I press the Get Mail button, it checks only the Inbox and not any of the other mail folders, which have changed in the meantime.

---

### Post by Paddy Landau on 2011-10-10
Well, I didn't find the answer, but I did find a simple workaround.

Edit > Account Settings > *[account]* > Synchronisation & Storage > *check* Keep messages for this account on this computer

It means it will take up a little extra disk space, but I'll just exclude it from my backups, and all is fine.

Curiously, this option is not set on my other computer, so I'm still in the dark as to why I needed to set this.

I'll mark this as solved.

---

