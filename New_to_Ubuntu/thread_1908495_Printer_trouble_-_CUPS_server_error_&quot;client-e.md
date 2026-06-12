---
title: "Printer trouble - CUPS server error &quot;client-error-not possible&quot;"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by kristamaranatha on 2012-01-13
Hello,

I have been using Ubuntu for exactly 2 days. I've always used Windows, and while I've been wanting to learn Linux I just never got around to it. Until I accidentally deleted Windows off one of our laptops. So I used Ubuntu Live CD and now that laptop runs Ubuntu, while the computer with the printer I am trying to connect to runs Windows XP. 

When I try to add a printer in Ubuntu (printer wizard?) I get the error:

CUPS server error
There was an error during the CUPS operation: "client-error-not-possible"

The printer is an HP Deskjet 3745

Is there something I need to install on Windows to make this work? I already installed Samba. Thanks!

---

### Post by lechien73 on 2012-01-13
Hi and welcome to the forums,

If the printer is shared on a Windows PC, then you need the "smbclient" package.

Try opening a terminal window (Ctrl+Alt+T) and typing:

```
sudo apt-get install smbclient
```

You will need to enter your password - it won't be visible while you type. When the package is installed, try adding the printer again.

---

### Post by kristamaranatha on 2012-01-13
I have done this, and it is still not working...

I found some instructions here: 

[http://www.liberiangeek.net/2011/10/first-30-days-with-ubuntu-11-10-oneiric-ocelotday-four/](http://www.liberiangeek.net/2011/10/first-30-days-with-ubuntu-11-10-oneiric-ocelotday-four/) 

...but how do I find the path I am supposed to type into the SMB Printer box?

---

### Post by lechien73 on 2012-01-13
The path is the *MACHINE_NAME/SHARED_PRINTER_NAME*. I would advise that you re-share the printer on the XP machine so that it doesn't have any spaces - so, for example, give it the sharename of *HPDeskJet*.

So, for example, if your XP machine is called PrinterServer, then the SMB path would be: *PrinterServer/HPDeskJet*

Put the local administrator username and password for the XP box into the authentication section.

---

### Post by kristamaranatha on 2012-01-13
So I renamed the computer and the printer, reestablished sharing of the printer, then went and typed in computer/deskjet3745 (new names) in the SMB Printer window. I hit "verify" and it said "Print share inaccessible." When I go to Printer Properties, under Printer State it says "Processing - connection failed: NT_STATUS_UNSUCCESSFUL"

---

### Post by kristamaranatha on 2012-01-13
Not sure if I did Samba right... in process of following these instructions: 
[http://www.liberiangeek.net/2011/11/first-30-days-with-ubuntu-11-10-oneiric-ocelotday-five/](http://www.liberiangeek.net/2011/11/first-30-days-with-ubuntu-11-10-oneiric-ocelotday-five/)

---

### Post by lechien73 on 2012-01-13
Could you try with the IP address of the XP machine instead of the machine name? So, if the XP machine is 192.168.0.1, then try: *192.168.0.1/deskjet3745*

---

### Post by kristamaranatha on 2012-01-13
That didn't work either...

Do I need to make sure the Ubuntu computer is on the same workgroup as the XP computer?

---

### Post by kristamaranatha on 2012-01-13
Well, I installed Samba, but when I click on it it prompts for my password and then does nothing...

---

