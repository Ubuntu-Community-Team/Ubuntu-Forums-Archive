---
title: "LPD/LPR printer option in 16.04 / 64 bit"
date: 2017-02-16
forum: New to Ubuntu
---

### Post by denville on 2017-02-16
Hi, I have to convert some Windows applications to Ubuntu, so I started with the latest 16.04 64 bit.  I have to access very many legacy LPR text only printers but the LPD/LPR option in printer setup is not present.  I have spent two days already trawling for an answer to this.  I installed 14 / 32 bit on a spare box and the option is there, and the printer works fine.  Please, please, what do I have to do to get the LPR option back ?

Many thanks.

Denville.

---

### Post by SeijiSensei on 2017-02-16
Open a browser and point it at [http://localhost:631/](http://localhost:631/).  That will open the CUPS management page.  Click on "Adding Printers and Classes" then click the "Add Printer" button.  Enter your login name and password when prompted.  You should see an LPR/LPD option in the list.

---

### Post by denville on 2017-02-16
Thank you for the reply.  No, it's not there, it lists:
Internet Printing Protocol (ipps)
Backend Error Handler
Internet Printing Protocol (ipp14)
AppSocket/HP JetDirect
Internet Printing Protocol (ipp)
..................................(http)
..................................(https)
Windows Printer via Samba.

(The version 14 / 32 bit does list LPR, as the first option).

Thanks again for any suggestions.

Denville.

---

### Post by SeijiSensei on 2017-02-17
From a brief Google search it might be a fallout from the transition to systemd in 16.04.

Maybe you should stick with 14.04 for now?  It's supported through 2019.

If that's not an option, can you configure the 14.04 box to be a print server for all the LPD printers, then print to it from 16.04 clients?

You might consider posting a bug report here: [https://bugs.launchpad.net/ubuntu/+source/cups](https://bugs.launchpad.net/ubuntu/+source/cups)

---

### Post by denville on 2017-02-17
Thanks for the reply.  Isn't it a b****r - I spend a year persuading my client to abandon Microsoft and their antics in favour of Linux, and I run into the same sort of problem !  Thanks again, I'll report it as a bug as you suggest and hope the reply isn't just 'we've decided to drop that".

Sincerely,
Denville.

---

### Post by HermanAB on 2017-02-18
I think all you need to do is install the correct version of lpr as shown here:
[https://unix.stackexchange.com/questions/134083/how-do-i-get-the-right-lpr-for-cups-installed-on-ubuntu-server-14-04](https://unix.stackexchange.com/questions/134083/how-do-i-get-the-right-lpr-for-cups-installed-on-ubuntu-server-14-04)

---

### Post by denville on 2017-02-19
Thanks, I tried that.  No joy, I still can't install an LPR printer.  Actually, it was fine in 14.04, it's just the 'improvement' to 16.04 that's broken.

Thanks again for taking the time to reply.

Denville.

---

