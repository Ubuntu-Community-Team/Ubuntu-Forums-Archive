---
title: "printer sharing - making printer on Gutsy available to Vista pc over wireless"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by guildofghostwriters on 2008-04-28
Binned XP and replaced with Gutsy last week. I used to share my printer with a Vista pc upstairs over wireless but I'm struggling to make this printer accessible to the Vista pc. According to the <a href="http://help.ubuntu.com/community/SettingUpSamba">samba guide</a> I should be able to do this without samba using CUPS. I've searched here and generally for how to set CUPS up for this purpose and there are so many guides that just don't agree - some say samba is necessary, some show changes to the cupsd.conf file that I'm reluctant to try because the guides are 2 - 3 years old and the cupsd.conf they are working with doesn't entirely resemble mine, and the guides I've tried haven't worked.

Can anybody please help?

Apologies for addled-headedness and general ignorance.

---

### Post by H.Callahan on 2008-04-28
I used the instructions [here](https://help.ubuntu.com/community/NetworkPrintingFromWinXP?highlight=%28printing%29) to get my XP machines to print to the Ubuntu box with the printer attached.  Worked first time with no problem.

---

### Post by guildofghostwriters on 2008-04-28
Thanks for replying. I'd followed those instructions previously and failed. I  just went over them again carefully in case I made any mistakes and it failed BUT it failed in a different way so I feel like I made some progress. When I try and add the network printer on the Vista machine, previously it just wasn't seeing it but I tried different combinations of hostname:631/printers etc and got it to the point where it seems to recognise there's a printer there but it's saying something about the spool and to restart that or the server. Unsure how to restart the spool, I've restarted the Gutsy pc and the printer but it's still reporting the same error. I think it's probably a problem at the Vista end rather than here so I'm going Googling for ideas but if you (anybody?) has any ideas in the meantime, I'd be grateful to hear them (except 'bin vista too' - much as I'd like to it's not my pc).

Cheers!

---

