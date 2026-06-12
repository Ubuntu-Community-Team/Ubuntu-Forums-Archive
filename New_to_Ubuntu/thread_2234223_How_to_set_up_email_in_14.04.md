---
title: "How to set up email in 14.04?"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by Quaixemen on 2014-07-13
Hello.  I just bought a computer that had Ubuntu preloaded on it.  It was a fresh install.  I don't know how to set it up so I can receive my email on it.  I've clicked on everything.  I tried to install thunderbird but it tells me it is already installed.  How do I set this up?  thanks.

---

### Post by Vladlenin5000 on 2014-07-13
Hi, welcome.

Thunderbird is already installed indeed. All you have to do is open it and an initial configuration wizard will pop up. Later you can edit/change this configuration, add more accounts, etc. It's exactly the same as using Thunderbird in Windows or MacOS.
Needless to say you can also access any webmail using the default browser - Firefox - or any other that you eventually install later.

---

### Post by Quaixemen on 2014-07-13
Thanks you for your reply.  As I said, I have tried all the buttons that I can see to click on and I have not been able to see anything that opens the email.  I need specific directions.  What do I click on to open it?  thanks

---

### Post by howefield on 2014-07-13
Open the Dash by pressing the Super key or the Ubuntu icon on the top of the launcher. Start typing thunderbird and the icon should appear.

---

### Post by philinux on 2014-07-13
Try this [http://www.youtube.com/watch?v=Nig5s-6GGIo](http://www.youtube.com/watch?v=Nig5s-6GGIo)

---

### Post by Vladlenin5000 on 2014-07-13
So... You actually need specific directions on how to open an app which isn't in the launcher already, right?

Click on the first icon in the launcher (or Super key), the dash opens with all its scopes at the bottom of the window. You don't need to use them for the purpose but it's always good to know what they are and, conveniently, the second one (letter A) shows all the apps installed (you can also activate one or more filters to trim down the results to certain types of apps. However you can search right away from the Home scope if you want and for that just type the first letters of the app you're looking for. Just by typing "T" you'll immediately see Thunderbird there.

Keep this mind for future use.

---

### Post by Quaixemen on 2014-07-13
Thank you for your replies.  I clicked the top Icon (super key right?).  Not sure what the "launcher" is.  Anyway, I typed in thunderbird and got the thunderbird icon.  I clicked on it.  But now I'm getting a message that says, "unable to locate mail spool file".  What should I do now?  thanks.

---

### Post by Quaixemen on 2014-07-13
I'm trying to think of what I should try.  Should I uninstall thunderbird and then reinstall it and try it again?  I never got the screen that came up in the video that asked if I wanted to add new email address.  Advice on this?

---

### Post by philinux on 2014-07-13
> **Quaixemen said:**
> I'm trying to think of what I should try.  Should I uninstall thunderbird and then reinstall it and try it again?  I never got the screen that came up in the video that asked if I wanted to add new email address.  Advice on this?

Open thunderbird mouse up to top left to reveal the menu. Edit > account settings> add account button

---

### Post by Vladlenin5000 on 2014-07-13
That error shouldn't be showing. Although you said "*it was a fresh install*" it seems it has been used before. Supposedly at least an attempt to setup an email account has been done before. Anyway, what's really important is finding a solution regardless of the cause.
Please try the following procedure (with the Thunderbird closed, for the moment):

1. Click on the second icon of the launcher (AKA the vertical bar on the left), your file manager. It should open in your home folder
2. Press CTRL+H to reveal hidden folders/files
3. Search for and delete the *.thunderbird *folder (yes, there's a "." preceding the name indicating that such folder is hidden)
4. Open Thunderbird again and setup your account(s).

If the error appear after setting up a **GMail** account then probably you have a 2-steps verification and you need to generate specific passwords for every app/machine you intend to use that account with.

---

### Post by coffeecat on 2014-07-13
With the unable to locate mail spool file message, have a look at this:

[http://askubuntu.com/questions/328143/thunderbird-showing-unable-to-locate-mail-spool-file-on-installing-gmail-accou](http://askubuntu.com/questions/328143/thunderbird-showing-unable-to-locate-mail-spool-file-on-installing-gmail-accou)

Something possibly happened to the configuration files when you were trying to open it, but not to worry. Deleting the hidden .thunderbird folder as in those instructions will reset Thunderbird to its default state. You don't need to re-install it. This is not Windows! :) 

Some of your problems are to do with unfamiliarity with the Unity desktop that comes with Ubuntu. When you have time, have a look at the 14.04 desktop guide link in my sig. 

Also - do you need an email client such as Thunderbird or does your email provider have a webmail page? If the latter, all you need to do is to use Firefox, the default web browser.

---

### Post by bapoumba on 2014-07-13
> **Quaixemen said:**
> Thank you for your replies.  I clicked the top Icon (super key right?).  Not sure what the "launcher" is.  Anyway, I typed in thunderbird and got the thunderbird icon.  I clicked on it.  But now I'm getting a message that says, "unable to locate mail spool file".  What should I do now?  thanks.

Others have suggested fixes. Just to comment on the error : you probably choose the wrong account type. Which account are you using ?

---

### Post by Quaixemen on 2014-07-13
Thanks for all the help.  I got it going.  Couldn't have done it without your advice.

---

