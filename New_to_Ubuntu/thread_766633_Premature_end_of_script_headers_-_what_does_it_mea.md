---
title: "Premature end of script headers - what does it mean?"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Dee.Jarman on 2008-04-25
Hello all, 

I have done a fresh install of a Learning Management System called Ilias. All is looking good except for one screen that reports a HTTP error on explorer while Firefox reports - Internal Server Error, this is an error with your script, check your error log for more information. 

When I check the error log, it says the following: 
Premature end of script headers: ilias.php, referer: ://62.44.82.193/ilias3/ilias.php?ref_id=8&admin_mode=settings&obj_id=161&cmd=listDesktopItems&cmdClass=ilobjrolegui&cmdNode=1254&baseClass=ilAdministrationGUI

Could anyone advise me what I need to investigate?  Does this look like a mysql, php or access problem.  Is there anywhere I can look up Premature end of script header reports? 

Thanks in advance for your help with this

Dee

Dee

---

### Post by nhandler on 2008-04-26
This type of error drives me nuts. I've spent countless hours trying to diagnose the problem. The first thing I would check are the permissions of the file. I'm not the best at this, and since I'm the only user on my computer, I just set them to 777 (rwx for all). Also, make sure the script is executable.

If that doesn't do it, check your script. I don't know php, but in perl, I have to specify the document type as text/html at the very top. If I don't do that, it causes this error.

I'm not sure about how you are using mysql, so I don't know if it is the cause of the problem.

---

