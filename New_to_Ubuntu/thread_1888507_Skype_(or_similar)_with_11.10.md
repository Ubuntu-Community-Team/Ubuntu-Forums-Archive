---
title: "Skype (or similar) with 11.10?"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Lalaith on 2011-11-29
Hi, 

I am new in the amazing linux world, I'm using Ubuntu 11.10 and tried to install skype.
I downloaded it from here: [http://www.skype.com/intl/es-es/get-skype/on-your-computer/linux/downloading.ubuntu64](http://www.skype.com/intl/es-es/get-skype/on-your-computer/linux/downloading.ubuntu64) (it's in spanish but I guess in every language is the same).

I've got 2 questions:

1) It appears it is a beta version, and very old. Where can I find a newer version and not beta? Is there any other program that I can use for videoconference? What do you use?

2) I'm using de default desktop of Ubuntu (Unity, right?). When I execute skype, if I close the window it keeps running the program but I cannot find it anywhere. (it disappears even from the left bar). If I go to the dash and execute skype, it says me that there is already an execution running. How can I see the skype window that is running?

If you need extra info please just let me know. Thank you :)

---

### Post by jockyburns on 2011-11-29
Sadly Skype only provide that "Beta version" for Linux at the moment. I don't know if there's any programs in the Ubuntu Software Centre, but if there were I suppose you'd be dependant upon whom ever you want to contact to have that same program installed.

PS Once Skype is running, when you close the window it's in, there should be a small Skype icon at the top bar of the screen (right hand side) Clicking that brings the Skype contacts window open again.

---

### Post by mikewhatever on 2011-11-29
1. That's what Skype has for Linux, a perpetual beta. That said, I much prefer the Linux version, as Skype for Windows got annoying and bloated with notifications and facebook integration.
There are lots of programs for video conferencing, but Skype is compatible with none, so if your friends and relatives use Skype, you are stuck.

2. Try removing what you had installed and then install Skype from the Ubuntu partner repository. It should have proper Unity integration.

---

### Post by Paddy Landau on 2011-11-29
With Ubuntu, whenever possible, please do not download programs but rather install them from the Ubuntu Software Centre. Not only is it far easier, but also more reliable.

If you have any problems with running Skype, then try: Uninstall Skype; start Ubuntu Software Centre; search for Skype; install. (**EDIT:** mikewhatever beat me to it.)

Skype does not offer an up-to-date version on Linux, unfortunately. It works, but you don't get the "Extras" that the Windows version has. I have version 2.2.0.35, which I believe is the latest version for Linux.

On the other hand, on Linux you can run two or more instances of Skype (with different logins) simultaneously. This is useful if you have (say) one user name for work and another for personal use. (I don't do this, but I know someone who does.)

---

### Post by Lalaith on 2011-11-29
Thank you all for the answers.

There's no little icon next to my mail icon, volume, dropbox icon... 

I first tried to install it from the repository (Ubuntu software centre) but although you can find the program, after the installation I couldn't find it on the dash. 

It's such a pity that we can only run a beta skype. On the while I am using gtalk and it works fine although it's much more simpler. 

thanks again

---

### Post by Lalaith on 2011-11-29
Oops. I just don't know how to uninstall Skype. 
It figures in the dash but it does not in the Ubuntu Software Center, "installed" programs, so I can't uninstall from there. 
If I open de .deb file I downloaded to install Skype, I can find the option to install, but not to uninstall.

How can I do it?:confused:

---

### Post by Paddy Landau on 2011-11-29
> **Lalaith said:**
> TI first tried to install it from the repository (Ubuntu software centre) but although you can find the program, after the installation I couldn't find it on the dash.
There is a bug where the Dash often doesn't see new programs until you log out and in again.

> **Lalaith said:**
> Oops. I just don't know how to uninstall Skype.
Open Synaptic Package Manager and uninstall from there; find *skype*, right-click, select Mark for Complete Removal, and Apply. (If you don't have Synaptic Package Manager, install it from Ubuntu Software Centre -- and log out and in again!)

Install from Ubuntu Software Centre or from Synaptic Package Manager (whichever you prefer), log out and in again, then try running Skype again.

---

### Post by Lalaith on 2011-11-29
Thank you, Paddy Landau.

I found it easy and fast. :)

---

### Post by jockyburns on 2011-11-29
As Paddy says, at least with Linux, it will allow you to run several instances of the same program,, whereas Windows wont allow you to run Skype accounts more than one at a time. (Linux does warn you that there may be more than one instance of this program running, but does allow it. )

---

