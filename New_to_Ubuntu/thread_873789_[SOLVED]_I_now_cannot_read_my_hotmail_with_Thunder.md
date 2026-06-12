---
title: "[SOLVED] I now cannot read my hotmail with Thunderbird"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by pjhartt on 2008-07-29
I was able to read my hotmail account up until July 1st 2008, I can no longer. I have used it for several years and don't pay for it.

I use Linux Mint Daryna and thunderbird 2.0.0.16

If anyone can help?

Regards

Peter

---

### Post by hyper_ch on 2008-07-29
did you ask hotmail if they changed everything?

---

### Post by phidia on 2008-07-29
Exactly what errors or messages are you getting when you try to open the hotmail url?

---

### Post by philinux on 2008-07-29
Working ok here.

Try updating your addons.

Tools > Addons then click find updates.

You might need to have TB 3.0 to get the latest updates though.

---

### Post by pjhartt on 2008-07-30
There are no error messages it just does not do anything.

---

### Post by pjhartt on 2008-07-30
There are no updates for addons

---

### Post by pjhartt on 2008-07-30
I have tried to update webmail but get the error shown in the attached picture. What does it have to do with Firefox?

TB 3 is only in beta form and the down loads are only in .tar.bz2 which I don't understand, Mint wants .deb files.

> **philinux said:**
> Working ok here.

Try updating your addons.

Tools > Addons then click find updates.

You might need to have TB 3.0 to get the latest updates though.

---

### Post by gerben1 on 2008-07-30
> **pjhartt said:**
> I have tried to update webmail but get the error shown in the attached picture. What does it have to do with Firefox?

You get that message when you click on a link to a Thunderbird addon in Firefox. Just right click the link choose "save as" and save the add-on somewhere, then open Thunderbird and go:
Tools->Add-ons->install, and select the downloaded .xpi file

---

### Post by philinux on 2008-07-30
> **pjhartt said:**
> I have tried to update webmail but get the error shown in the attached picture. What does it have to do with Firefox?

TB 3 is only in beta form and the down loads are only in .tar.bz2 which I don't understand, Mint wants .deb files.

I just checked my install for you and I have TB 2.0.0.16 with

webmail 1.3.2 and
webmail/hotmail 1.2.17

which is working ok.

---

### Post by Ben Carlin on 2008-07-30
I have just installed the webmail plugin so I can read my hotmail emails.. it didn't work straight away as I had to change all the ports in the webmail settings above there defaults so I changed them to the recomended 1024 setting for all of them. to set up the account I then just followed this guide off there site: [http://webmail.mozdev.org/setup.html](http://webmail.mozdev.org/setup.html)
However it still didn't work and then I thought perhaps the defualt In account settings for the server is wrong and it was the defualt was 110 so I changed this to 1024 and everything works perfectly.. if thats any help to anybody!

Cheers!

---

### Post by pjhartt on 2008-07-30
My setting for the port was 2000. I changed it to 1024 as suggested but got the error "could not connect to localhost; the connection was refused"

I changed it back to 2000 It connected but no new messages.

Peter

> **Ben Carlin said:**
> I have just installed the webmail plugin so I can read my hotmail emails.. it didn't work straight away as I had to change all the ports in the webmail settings above there defaults so I changed them to the recomended 1024 setting for all of them. to set up the account I then just followed this guide off there site: [http://webmail.mozdev.org/setup.html](http://webmail.mozdev.org/setup.html)
However it still didn't work and then I thought perhaps the defualt In account settings for the server is wrong and it was the defualt was 110 so I changed this to 1024 and everything works perfectly.. if thats any help to anybody!

Cheers!

---

### Post by pjhartt on 2008-07-30
> **pjhartt said:**
> My setting for the port was 2000. I changed it to 1024 as suggested but got the error "could not connect to localhost; the connection was refused"

I changed it back to 2000 It connected but no new messages.

Peter

I re installed webmail with success (see Screenshot 1.jpg)

I the tried to install Hotmail addon and got error in Screenshot 2.jpg, still it refers to Firefox not Thunderbird.

To make sure there was a new message I sent one to myself and checked that it was there on hotmail website. It Was!

Regards
Peter

---

### Post by gerben1 on 2008-07-31
> **pjhartt said:**
> I re installed webmail with success (see Screenshot 1.jpg)

I the tried to install Hotmail addon and got error in Screenshot 2.jpg, still it refers to Firefox not Thunderbird.

I don't see where it refers to Firefox...

The error message seems to indicate that the add-on you downloaded got broken somehow. I would just delete it and try downloading it again.

This one:
[http://download.mozdev.org/webmail/hotmail-1-2-18.xpi](http://download.mozdev.org/webmail/hotmail-1-2-18.xpi)
works fine here. I just tried installing (and uninstalling) it and it installs fine in Thunderbird 2.0.0.16

---

### Post by pjhartt on 2008-07-31
> **gerben1 said:**
> I don't see where it refers to Firefox...

The error message seems to indicate that the add-on you downloaded got broken somehow. I would just delete it and try downloading it again.

This one:
[http://download.mozdev.org/webmail/hotmail-1-2-18.xpi](http://download.mozdev.org/webmail/hotmail-1-2-18.xpi)
works fine here. I just tried installing (and uninstalling) it and it installs fine in Thunderbird 2.0.0.16

Yep you were right I downloaded from your URL and it down loaded and installed. 

BUT big BUT
I still have no new messages since 01/07/08

Peter

---

### Post by pjhartt on 2008-08-05
> **pjhartt said:**
> Yep you were right I downloaded from your URL and it down loaded and installed. 

BUT big BUT
I still have no new messages since 01/07/08

Peter

I have now updated my LinuxMint to Elyssa. As a result everything had to be reinstalled including Thunderbird, Webmail and Hotmail .xpi's.

After setting things up my hotmail is now working. Whoopie

On the old version I had even tried to completely uninstall Thunderbird but each time I reinstalled it all my mail settings and Mail messeges were still there. This may have been the problem that I could not completely remove Thunderbird. 

An answer to this may be useful in the future and for others experiencing this sort of problem but it does seem a bit extreme to install a new system just to get the mail to work correctly when probably it was a glitch or a finger problem on my part. 

I am still very new to this and am very used the the ease that windows provide but definitely like the Linux setup and speed. I do find it difficult when installing things but so far on this Mint Elyssa it is much easier.

Many thanks to all who have tried.
Peter

---

### Post by pjhartt on 2008-08-14
> **pjhartt said:**
> I have now updated my LinuxMint to Elyssa. As a result everything had to be reinstalled including Thunderbird, Webmail and Hotmail .xpi's.

After setting things up my hotmail is now working. Whoopie

On the old version I had even tried to completely uninstall Thunderbird but each time I reinstalled it all my mail settings and Mail messeges were still there. This may have been the problem that I could not completely remove Thunderbird. 

An answer to this may be useful in the future and for others experiencing this sort of problem but it does seem a bit extreme to install a new system just to get the mail to work correctly when probably it was a glitch or a finger problem on my part. 

I am still very new to this and am very used the the ease that windows provide but definitely like the Linux setup and speed. I do find it difficult when installing things but so far on this Mint Elyssa it is much easier.

Many thanks to all who have tried.
Peter

The above worked but I then found I could not send Hotmail.
[B][U]
Here is my Solution[/U][/B]

I have finally got Thunderbird to work correctly with Hotmail.

I installed Webmail 1.3.2 and Webmail-Hotmail 1.2.18

Under Tools > Add-ons select Preferences > Servers

I set the POP port to 1024 and the SMTP port to 2000 and restarted ports
Close Webmail options and Add-ons.

Then under Edit > Account Settings

Select Webmail Server settings and set localhost Port to 1024
Select Outgoing Server (SMTP)

Then Select Webmail-localhost and edit it

The Port is default 25 (I first changed this to 2000 but got errors)
Change it back to 25 BUT then had the idea to set the Server Name from localhost to my own SMTP server name (in my case auth.smtp.1and1.co.uk)

NOW my Hotmail working correctly receiving and sending mail

I hope this will be of use to many of you

Good Luck
Peter

---

