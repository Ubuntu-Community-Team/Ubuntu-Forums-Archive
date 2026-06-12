---
title: "ClamTk Virus Scanner"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-26
I downloaded this, and i wanted to update the signatures, but it says that I need to be logged into root to do this. I know how to login to root, but I read a lot topics where people were saying to never do this. How would I go about updating this without logging into root?

Also, ClamTk isn't in any of my menus, and everytime i want to open it, i gotta go to the run command and type it in there, how do i add this program to the applications menu?

---

### Post by bumanie on 2008-05-26
Clam tk front end is in synaptic. I think you have to use root to update as this is ans adminstration function. You can however scan without the need of the sudo command.

---

### Post by darioniro on 2008-06-26
You have to go to System --> Administration --> Synaptic Package Manager 

Once opened go to "Installed (upgradable)" and select clamav (on the rigth panel) ans with rigth-botom select "Mark for upgrade", then select Apply. Regards:)

---

### Post by Nepherte on 2008-06-26
To update the virus definitions with a terminal command:
[code]sudo freshclam[code]

---

### Post by Pjotr123 on 2008-06-26
Tip: take a little time to read this:
[http://ubuntutip.googlepages.com/security](http://ubuntutip.googlepages.com/security)

---

