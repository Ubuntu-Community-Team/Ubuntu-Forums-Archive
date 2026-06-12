---
title: "ClamAV not running - can't open a DB?"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Balt603 on 2008-08-18
Hi,
    I have installed ClamAV using the following command

> sudo apt-get install clamav clamav-freshclam clamtk

which appeared to install without problems. However, when I open ClamTK using "sudo clamtk" and try to scan a file, I get the following errors

> LibClamAV Error: cli_hex2str(): Malformed hexstring: 8c3762e9e148c97 (length: 15)
LibClamAV Error: cli_loadmd5: Malformed MD5 string at line 50250
LibClamAV Error: cli_loadmd5: Problem parsing database at line 50250
LibClamAV Error: Can't load /var/lib/clamav//main.inc/main.mdb: Malformed database
ERROR: Malformed database


I can see it's a problem with a DB, but I would like to know how it got that way, and more importantly, how to fix it!

Cheers :-)

---

### Post by nicedude on 2008-08-18
For starters let me ask why you feel you have to run ClamAV at all. The only really good reason I know of is if you are running an Email server and want to scan all mail for attachments with Viruses. The next best reason would be you have both XP or Vista and Ubuntu and want to scan your Windows partitions for viruses ( this is probably better to do inside windows since you can use a on access virus scanner like AVG and also clamwin on demand scanner in windows to scan stuff when you choose to have extra confirmation - both are free ). And last would be a misguided attempt to find Ubuntu viruses with it ( which since there are 0 Ubuntu viruses that will be a lost cause all together )

So if it is reason #1 then it is a good thing to use. If it is reason #2 or #3 then I would uninstall it and forget the word virus while in a Linux environment ( outside of catching the FLU since that is a virus that can get you while using linux :-) )


Please let me know though what you are trying to do and I will help you figure it out.

---

