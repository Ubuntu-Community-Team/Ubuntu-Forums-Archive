---
title: "internal error lsb-release 4.0-0ubuntu20.2"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by send2 on 2013-04-05
Hi all,

after a recent official update, and after I log in to my desktop, i am getting the following error:

[ATTACH=CONFIG]240998[/ATTACH][ATTACH=CONFIG]240999[/ATTACH]


I went to Synaptic and reinstalled lsb-release 4.0-0ubuntu20.2 but I am still experiencing the error appearing on my desktop, it does not freeze my desktop, I have no problems with the system, but I am baffled as to why I am getting this error!?

thanks in advance for pointers as to the solution....

---

### Post by Bashing-om on 2013-04-06
send2; Hi !

Do you have "teamviewer" installed on your system. From your attached bug report link:
> [TABLE]
[TR]
[TD][Brian Murray (brian-murray)]("https://launchpad.net/%7Ebrian-murray")             wrote             on 2013-03-25:[/TD]
[TD="class: bug-comment-index"]           [ #48]("https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/1094218/comments/48")[/TD]
[/TR]
[/TABLE]
                               This  bug could be closed for Ubuntu because it is not an issue with  lsb_release itself, however with how lsb_release is being called by  teamviewer.  Something about the way the environment is setup by  teamviewer's software is causing it to crash, and subsequently this is  not something the Ubuntu development team can fix.  It would be helpful  if someone who cares about this issue were to bring this matter to the  attention of the TeamViewer developers.
That thread also has a solution, if you are comfortable with editing a system file.


just try'n to help

---

### Post by send2 on 2013-04-06
> **Bashing-om said:**
> send2; Hi !

Do you have "teamviewer" installed on your system. From your attached bug report link:

That thread also has a solution, if you are comfortable with editing a system file.


just try'n to help

Hi Bashing-om! thanks for your help. Yes, I have "teamviewer" installed on my system. What system file changes are we talking about? 
Is it worth changing the system file for that matter or is it better to uninstall team viewer? Is there another program that is similar to teamviewer but is compatible with Ubuntu 12.04? thanks for your help :)

---

### Post by Bashing-om on 2013-04-06
send2;
Teamviewer posses no threat or problem, just the inconvenient messages. The address from the bug report:
DuplicateOf:
[https://bugs.launchpad.net/bugs/1094218](https://bugs.launchpad.net/bugs/1094218)
within that report is the instructions to remove the generation of the messages. Have a read and post back if you need additional help to edit the file. Always make a backup prior to editing any file !

As I do not use "teamviewer" I can not advise on any alternatives. As you use "teamviewer" why not keep it ? Else -by all means - clean up your system and remove unwanted/unused software.[INDENT=2]
I hope this helps

[/INDENT]

---

### Post by send2 on 2013-04-06
Thank you Bashing-om. I will look into the thread. Thanks for your help and advise. I will mark this thread solved, if I have any other questions or problems I will open the thread up.

---

