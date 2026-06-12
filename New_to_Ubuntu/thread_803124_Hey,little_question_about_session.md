---
title: "Hey,little question about session"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by shewenhao on 2008-05-22
I am new in Ubuntu and I installed the 8.04

I just found that there is a interesting tool to set up the session startup for system. I accidently clicked the button Remember the currently running application..... Then I found out that next time when I log in, all the old application will come out by themselves directly. Somehow, it is nice if you want to continue something last time. But after clicking this, I found that I could not get a "Freshing restart"..... Every time I got some thing left last time. But there is no button like"Remove all these session memomry....."Of course, I could close all application and let this session to remember again the currently running application. Then next time the system seems not so  massive.

BUT, How could I tell ubuntu that :"forget about everything I let you remember before, please give me a refreshing and totally new log in??"


Thank you in Advance,

Have a nice day!!

---

### Post by iaculallad on 2008-05-22
> **shewenhao said:**
> I am new in Ubuntu and I installed the 8.04

I just found that there is a interesting tool to set up the session startup for system. I accidently clicked the button Remember the currently running application..... Then I found out that next time when I log in, all the old application will come out by themselves directly. Somehow, it is nice if you want to continue something last time. But after clicking this, I found that I could not get a "Freshing restart"..... Every time I got some thing left last time. But there is no button like"Remove all these session memomry....."Of course, I could close all application and let this session to remember again the currently running application. Then next time the system seems not so  massive.

BUT, How could I tell ubuntu that :"forget about everything I let you remember before, please give me a refreshing and totally new log in??"


Thank you in Advance,

Have a nice day!!

Go to System->Preferences->Sessions and from the "Session Option" tab, uncheck "Automatically remember...."

---

### Post by shewenhao on 2008-05-22
Hi,

You are right about the session option tab, and I already unchecked the "Automatically remember...." option.

BUT, the problem still over there. Did you notice that right under the line "Automatically remember...." there is a button called "Remember the currently running application". I am quite sure that I did click this once before and then every time I restart there will be skype firefox or something started up by system automatically.....I thought I may have to click this again after closing every application. Then I just closed every thing consuming the Ram and clicked again. But it seems like does not help. 


I installed the AWN for dock bar. I build a session before to let system to start this automatically and I also selected the option "automatically start AWN" in the AWN-Manager.... Then there are two dock bar .....and I did deselected the option in AWN manager and also delete the "awn" session (I guess it may cause the problem.. I probaby should untoggle the "awn" in the session first then remove it... I just removed it ). 


How could I get a fresh started system?? It is OKAY for me to do revert all these annoying session thing, but can you tell me how to do this? Is  there a command to rebuild whole session to the original session right after installation of Ubuntu??

Thank you very much!

---

### Post by c98928 on 2008-05-25
i have exactly the same problem,and it's really freaking me out
hope somebody could help~~~

---

### Post by c98928 on 2008-05-25
i just found a workaround,it works but i dont know if it's the correct way of doing this,but anyway,i simply remove the file ~/.gnome2/session,and relogin,problem is then solved.

---

### Post by sayakb on 2008-05-25
Delete the Saved session files in the ~/.nautilus folder and login again.

---

### Post by markbuntu on 2008-05-25
By default, Ubuntu will reboot with your last session because it remembers you and what you did to it and is trying to be nice by giving you your desktop as you left it. It is also smart enough to know that you may have done something incredibly bad and ugly and may need a way to go back to the original setup because you can't remember how and what you did or it would take just forever to fix everything individually.

So,you can always reboot and by clicking on the little icon in the lower left corner of the login window and choosing session /gnome or /run xfce or even /gnome safe mode, go back to the original setup as it came "out of the box". Just do not choose /use last session which is the default at the top.

This will open gnome or xfce without all that stuff you did to it and then you can mess it all up again in an entirely new and more interesting fashion.

---

