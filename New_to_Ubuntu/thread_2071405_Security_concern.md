---
title: "Security concern"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by r3bol on 2012-10-15
Hi, I have a pop-up that is appearing after start up which says, System program problem detected. Do you want to report the problem now? [Report problem | Cancel].
If I click "Report problem", it prompts me for my password. I am slightly suspicious of the message though and was wondering whether there was another way to verify this problem actually exists or at least the source of the message is legit?

Thanks.

---

### Post by Frogs Hair on 2012-10-15
That is Apport system. [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by grahammechanical on 2012-10-15
There is no point reporting the problem if you cannot provided all the details of the problem. Therefore, the program needs your permission to collect that data because it needs administrator authentication.

That program is called apport

[https://wiki.ubuntu.com/Apport]("https://wiki.ubuntu.com/Apport")

If it is going to collect data that could contain a password it will ask you for further authentication. Then you will be taken to a website called Launchpad

[https://launchpad.net/ubuntu]("https://launchpad.net/ubuntu")

It is here that the report gets logged (with your permission) provided that you have a Launchpad account.

Here is some more information about reporting bugs.

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

What you are seeing is an example of Ubuntu security. Although you are the administrator you are using Ubuntu as an ordinary user. This means that whenever we or the system needs to do something that requires administrator approval we get asked to authenticate.

This, in theory, should make it much more difficult for a program to run with administrator privileges without our authentication. Ubuntu system utilities do not break this rule.

regards.

---

### Post by mike acker on 2012-10-15
> **r3bol said:**
> Hi, I have a pop-up that is appearing after start up which says, System program problem detected. Do you want to report the problem now? [Report problem | Cancel].
If I click "Report problem", it prompts me for my password. I am slightly suspicious of the message though and was wondering whether there was another way to verify this problem actually exists or at least the source of the message is legit?

Thanks.

me having same problem   12.04 LTS
only on my admin account

---

### Post by lazarojhr16 on 2012-10-15
yea like the posts earlier, there is no risk of anything like a virus. i long time ago i had the same problem, i can't remember but it had to do with compiz and my graphics card. thats all i can remember hope it helps.

---

### Post by mike acker on 2012-10-15
> **lazarojhr16 said:**
> yea like the posts earlier, there is no risk of anything like a virus. i long time ago i had the same problem, i can't remember but it had to do with compiz and my graphics card. thats all i can remember hope it helps.

i just dismiss the dialog; everything seems to be working fine.

---

### Post by deadflowr on 2012-10-15
No need to be suspicious. Apport just needs to collect your systems info.
It's been installed on Ubuntu since something like 10.10 or something like that. However it was never enabled until 12.04.
Disabling it, if you so desire, is quite simple.
Open your favorite editor, in root, and edit the file /etc/default/apport. Change enabled=1 to enabled=0.
```
gksu gedit /etc/default/apport
```

[Apport]("https://wiki.ubuntu.com/Apport")

I keep it on for any pre-final release I'm running. Otherwise, the errors I'm getting are typically, my fault(triple clicking to close a window type stuff).

---

### Post by daslinkard on 2012-10-15
Chances are if you enter in your password and allow for everything to report....if you click on show details you will probably see the following error
```

/usr/bin/aptd
```

Let us know what the show details display.

---

### Post by OldNovice on 2012-11-12
> **deadflowr said:**
> No need to be suspicious. Apport just needs to collect your systems info.
It's been installed on Ubuntu since something like 10.10 or something like that. However it was never enabled until 12.04.
Disabling it, if you so desire, is quite simple.
Open your favorite editor, in root, and edit the file /etc/default/apport. Change enabled=1 to enabled=0.
```
gksu gedit /etc/default/apport
```

[Apport]("https://wiki.ubuntu.com/Apport")

I keep it on for any pre-final release I'm running. Otherwise, the errors I'm getting are typically, my fault(triple clicking to close a window type stuff).
Thanks. I edited /etc/default/apport to disable it.
I had the same issue with  this popup.  It started after I tried a suggestion I'd read about an issue when using zgv.  The guy suggested entering
 X :1 &
in order to get over a problem with "console ownership".  This turned out to be a very bad idea, as it mucked up my display, I completely lost control, and I had to let the battery run down to provoke a reasonably tidy shutdown.  System came back up ok, but this apport thing started appearing.

---

