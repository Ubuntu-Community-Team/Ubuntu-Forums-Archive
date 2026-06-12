---
title: "Samba permissions"
date: 2017-11-06
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2017-11-06
I wanted a central location to store pdfs of receipts of bills paid online and scanned. I setup an nfs share to my laptop, no problems. Also setup a samba share to my wife's laptop. I created a receipts group on the server and put both of us in it, changed ownership of the shared directory to root:receipts with permissions of 775. Already had a share for my wife previously so no other setup was required. I cannot create files / open existing files on the share from the wifes laptop due to permissions issues. Temporarily for it to work I have it restricted to just her user with 777 permissions. Not ideal obviously. How can I sort this out to have normal permissions instead of 777 on the folder?

---

