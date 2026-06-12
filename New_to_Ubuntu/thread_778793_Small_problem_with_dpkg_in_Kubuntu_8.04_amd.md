---
title: "Small problem with dpkg in Kubuntu 8.04 amd?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by scrapmetal on 2008-05-02
[B]Manually installing Google Earth, from as below, have encounteredthis in terminal mode after getting to _NOTE:1._
 
 name@machine:~$ sudo apt-get install lib32nss-mdns
 [sudo] password for name:
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
 
 What do I do now? As there 5 packages avaiable for update and the 
 &#8220;updater reports&#8221; 
 
 &#8220;Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).&#8221;
 
 Would you like to attempt ot resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.&#8221;

 WHAT THE........ ???[/B]:confused:
 
 Code:
 sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
 Code:
 sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
 2) Install Google Earth; 
 Code:
 sudo apt-get install googleearth-4.3
 
[B] _NOTE:1._ sudo apt-get install googleearth-4.3 finished with OK(could NOT click on OK so used the enter key,....waited ... no change ...... closed the current terminal window, launched a new one, and tried below in a new terminal window)
 Unable to run.&#8220;Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).&#8221;[/B]
 
 3) Fix 32-bit DNS support on x86_64 Hardy. 
 Code:
 sudo apt-get install lib32nss-mdns
 To launch Google Earth; 
 Code:
 googleearth
 Alternatively, navigate to the Applications menu -> Internet -> Google Earth Hope that helps some people!
 Firefox-2 install went fine using Adept Manager.
 So did Skype using terminal using,
 sudo apt-get install ia32-libs lib32asound2; wget -O skype-install.deb [http://www.skype.com/go/getskype-linux-ubuntu;](http://www.skype.com/go/getskype-linux-ubuntu;) sudo dpkg -i --force-all skype-install.deb;
 
 :)
 
 So far 8.04 on an amd 3200+ with a nvida 6800Gt, on agigabyte motherboard and a sata 320 gig has run beutifully. Will be going on 2 others as soon as google earth runs and updates are restored. :)
 
** Thanks to all involved.**

---

### Post by Monicker on 2008-05-02
Make sure that none of your package managers are running, then do

```
sudo dpkg --configure -a
```


..from a terminal session


Then try to install any other packages you need.

---

### Post by scrapmetal on 2008-05-02
:) **Perfect...**
Worked, I am very impressed and will be installing 8.04 on the other 2 tomorrow.
Would have sent you an internal thanks but do not have 75 postings yet. Can you recommend a Kubuntu 8.04 for DUMMIES so I can learn more, or a forum for learning the basics. I keep reading postings but do not know enough to help others yet. Keene to learn and help, but dont know where to start with the basics of terminal usage. Any mentoring gratefully accepted.
[U][B]THANKS.
:).:).:)
[/B][/U]

---

### Post by Monicker on 2008-05-02
Hrmm.  I haven't done much with Kubuntu.  I just recently started dual booting Ubuntu 8.04 on my laptop, though I have run Debian with KDE on it for several years now.

You might try this site:

[http://www.kubuntu.org/doc/index.php]("http://www.kubuntu.org/doc/index.php")

It has not been updated with information specific to 8.04, but I would think most of the basic stuff still applies.

---

### Post by scrapmetal on 2008-05-02
Thanks.....
I have been thinking about loading debain on a machine to learn and experiment with, but don't know to find an equivalent forum of this quality for it. Thanks for the info, will stay up a bit longer.
THANKS..:)

---

