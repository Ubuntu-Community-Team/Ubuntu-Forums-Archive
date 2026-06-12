---
title: "Help Setting Up A Dell A920 Printer"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Bugsysservant on 2008-06-07
As an utter linux newb (but loving it so far), I'm having some trouble setting up my printer. Its connected to the family computer, running XP, and is a Dell AIO A920. I'm not really sure where to proceed now, as I've tried to figure it out with the printing option in system>administration, but am really unsure of how to use it correctly, and it doesn't seem to have the correct drivers, at least that I can find with the "Dell" selection of printers. Sorry if I'm not supplying all the information necessary, but I'm new at this, and have tried a few things online, but none have worked. Thanks.

---

### Post by wolfen69 on 2008-06-07
Dell does not make their printers. it is made by one of the regular printer manufacturers. you will need to find out who makes it before we can help.

---

### Post by st33med on 2008-06-07
> **wolfen69 said:**
> Dell does not make their printers. it is made by one of the regular printer manufacturers. you will need to find out who makes it before we can help.

Uhh... I thought Dell DID make their own printers...

---

### Post by avtolle on 2008-06-07
I believe this particular printer/all in one is a Lexmark.

---

### Post by st33med on 2008-06-07
Since it is a local computer, you just need to share it from XP.
Go to this MS-bias link (:)): [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx]("http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx") and follow its instructions there.

Once you have that done, go back to your laptop. Go to System>>Preferences>>Printing. Hit the New Printer button and select "Windows printer via Samba" and browse for the printer. Make sure Windows is on and an admin account is logged in.

---

### Post by avtolle on 2008-06-07
> **st33med said:**
> Since it is a local computer, you just need to share it from XP.
Go to this MS-bias link (:)): [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx](http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx) and follow its instructions there.

Once you have that done, go back to your laptop. Go to System>>Preferences>>Printing. Hit the New Printer button and select "Windows printer via Samba" and browse for the printer. Make sure Windows is on and an admin account is logged in.
That should work. I misread your opening post, and thought you were asking how to install as a local printer on the Ubuntu machine. I'm doing the above procedure for a Brother MFC-240C, and it works well.

---

### Post by Bugsysservant on 2008-06-08
> **st33med said:**
> Since it is a local computer, you just need to share it from XP.
Go to this MS-bias link (:)): [http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx]("http://www.microsoft.com/windowsxp/using/networking/expert/honeycutt_july2.mspx") and follow its instructions there.

Once you have that done, go back to your laptop. Go to System>>Preferences>>Printing. Hit the New Printer button and select "Windows printer via Samba" and browse for the printer. Make sure Windows is on and an admin account is logged in.

I've done all that, and it still doesn't work. The printer had already been shared, since I used it with my old XP partition, but when I click the "Browse" button on the Samba Printer tab, the list is blank.

---

### Post by avtolle on 2008-06-08
OK, dumb question, the printer is powered up, right?, as is the XP box? (Not to be insulting, but I once spent an hour trying to figure a similar problem out, and it turned out the host computer was not powered up)

---

### Post by Bugsysservant on 2008-06-08
> **avtolle said:**
> OK, dumb question, the printer is powered up, right?, as is the XP box? (Not to be insulting, but I once spent an hour trying to figure a similar problem out, and it turned out the host computer was not powered up)

No, everything was on and connected, and no offense taken. Tech support wouldn't ask that in its first two questions if it didn't solve more problems then any other solution. :P

Anyway, the point is somewhat moot now, because my laptop has inexplicably died, so printing is somewhat irrelevant now. Thanks for your help though.

And, sorry to derail my own thread, but it seems silly to start a new one for a quick question. Can anyone tell me what might be the cause of a laptop that suddenly shuts down during normal activity with plenty of power left, and then won't turn on (no power at all, can't even get to bios or anything.)? Its pretty old, almost four years, so I was thinking perhaps a hard disk failure? I don't have all that much experience with these things. Thanks.

---

