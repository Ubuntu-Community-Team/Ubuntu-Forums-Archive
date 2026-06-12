---
title: "No Skype in Ubuntu 14.04"
date: 2014-05-06
forum: New to Ubuntu
---

### Post by lyni on 2014-05-06
I have installed Ubuntu 14.04 but there is no Skype in the Software Centre. I went to the Skype website and they only have a Skype version for Ubuntu 12.04. can I install that one or how else can I get access to Skype?
thank you
lyn

---

### Post by monkeybrain20122 on 2014-05-06
You have to activate the Partner's repo. Go to Edit > Software Sources > Other Software and check the box "Canonical's Partners" (forget about source code), then restart Software Centre (?) and search for Skype. (I don't use the USW, in synaptic there is a 'reload' function to update the database after to add a repository, but 'reload' seems to be missing in USC, so I suppose you have to restart it)

---

### Post by lyni on 2014-05-07
thanks monkeybrain I went to Canonical Partners and then clicked reload but Skype is still not in the Software Centre.
lyn

---

### Post by Rockwell32001 on 2014-05-07
It's the first one, Client for Skype VOIP and instant messaging service.

---

### Post by LastDino on 2014-05-07
If you can't find it there, simply go into >download>''other'' (when selecting your Linux OS) option on skype website. Or better yet, just install synaptic, it is better than USC ones you get used to it.

---

### Post by Kurt_Alan on 2014-05-07
**[SIZE=5][/SIZE]**

It is a good idea to install Synaptic Package Manager.  Enter these lines in the terminal or CLI (command line interface) one at a time: ```
 sudo apt-get update
sudo apt-get upgrade
sudo apt-get install synaptic 
```

If the Synaptic icon does not appear on your Launcher, open Dash, type in Synaptic, and drag the icon to the Launcher.  With your cursor, you can drag and drop this icon to your location of preference on the Launcher. I like to put the Terminal at the top, then Synaptic, as these are frequently used tools/resources.

Then open Synaptic.  Find Search in the Edit menu and type in Skype.  Check the box in Skype, then click Apply and it will install.  To find Skype icon (program), do same as above.

---

### Post by drac-noc on 2014-05-10
I grabbed Skype directly from the website and installed the 12.04 multiarch. Seems to work perectly on my 14.04. I notice that the repo version in the Software Centre is marked as version 4.2.0.11-0ubuntu.0.12.04.2, suggesting that there's no change from the 12.04LTS version, but it is one step behind the version at skype.com, which is 4.2.0.13-1.

---

### Post by heidi3 on 2014-05-10
I too used the one directly from the website as drac-noc says. I've had no problems with it. Was just a simple download. Good luck. Hope it works for you. :D

---

### Post by stalkingwolf on 2014-05-10
you should be able to install synaptic from software center as well. thats about all i use software center for.

---

### Post by Cu Rua on 2014-05-12
Neither Synaptic nor Software Center had Skype in any way, shape or form for me ;.; The official site gave me i386 version for 12.04, but i have AMD64. I tried grabbing the Dynamic version, but it came in .tar.bz2 format and I don't know how to install that. Help!

---

### Post by monkeybrain20122 on 2014-05-12
> **Cu Rua said:**
> Neither Synaptic nor Software Center had Skype in any way, shape or form for me 

That is  because you have to activate the partner's repo.

---

