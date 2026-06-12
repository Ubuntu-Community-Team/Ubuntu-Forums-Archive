---
title: "LightDM / Unity-Greeter Bugs"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by andyrogers2008 on 2011-08-27
Hi

I think I have found about 3 bugs in LightDM/Unity-Greeter which is kind of putting me off from using it as my main Login Manager for the time being.

Could people read through these and see if they have noticed any of these as well:-

1) [https://bugs.launchpad.net/unity-greeter/+bug/835310]("https://bugs.launchpad.net/unity-greeter/+bug/835310")

[B]LightDM does will not log in an additional person, if one is already logged in.
[/B]

If you try to log in an additional session from the indicator-session menu by either choosing a user listed, or "Switch from xxxx...." .  When you get to lightdm and try to logon as the user, the password box disappears and nothing happens.

If you cycle through the other usernames, the password box is also gone.

Eventually lightdm seems to crash out, and iam returned to my locked session where I can log back in.  If I come to log back out, I don't get returned to lightdm as it has crashed out.

Has anyone else seen this?

2) [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/835311]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/835311")

**Does note default to chosen user if selected from indicator-session menu**

If you choose to go and log into another session from the indicator-session menu, in GDM you would be prompted just for the password with the chosen user already selected for you.  In lightdm this does not happen, you have to select the user yourself.

Has anyone else seen this?
3) [https://bugs.launchpad.net/lightdm/+bug/835312]("https://bugs.launchpad.net/lightdm/+bug/835312")

**Unity-Greeter does not indiciate if a user is already logged on when trying to log in a 2nd+ user, whilst the 1st user is already logged in**

If you go to login a 2nd+ user, when you get to lightdm it does not show if other users are already logged in.  In GDM this shows you other users who are currently logged in.

Has anyone else seen this happen aswell?

If anyone does see this issues as I have, please visit the linked bugs and mark then as "Effects Me" aswell please.

Thanks

Andy

---

### Post by MacUntu on 2011-08-28
Confirmed all three.

---

### Post by andyrogers2008 on 2011-08-31
With regards to my bug [https://bugs.launchpad.net/unity-greeter/+bug/835310](https://bugs.launchpad.net/unity-greeter/+bug/835310) , I have been asked to attach the log files from /var/cache/lightdm directory but however I have not got any log files on there.  Only a dmrc folder which does not contain much.

Does anyone know how to get the log files from lightdm which iam being asked for.  Have I got to enable debug mode somehow, if so how?

Thanks

Andrew

---

### Post by MacUntu on 2011-08-31
That was actually a mistake: the files you should add are in /var/log/lightdm.

---

### Post by andyrogers2008 on 2011-08-31
Thankyou MacUntu

---

### Post by andyrogers2008 on 2011-08-31
I have just raised a new bug against Unity-Greeter

**Unity-Greeter / LightDM does not re-focus onto Password box when Session Type has been chosed from menu**

[https://bugs.launchpad.net/unity-greeter/+bug/838392]("https://bugs.launchpad.net/unity-greeter/+bug/838392")

Notes....

When using Unity-Greeter, if you click the Cog in the top right hand corner of the chosen user to change the session type you are logging into (Gnome, Unity/Unity 2D etc). Once the popup menu has disappeared the focus of the cursor remains on the Cog button, if you press enter the Session Type menu reappears.

Surley it should refocus back into the password box so the user can either type their password, or just press enter so the chosen session can load up, without the need of clicking back into the password box first.

It would also be very very usefull, if a flashing type cursor could be made present in the password box aswell when it has got the focus, so the user knows the greeter is ready to take the entry of their password.

...

Have other people seen this behavior aswell?

Thanks

Andy

---

### Post by lidex on 2011-08-31
> **andyrogers2008 said:**
> I have just raised a new bug against Unity-Greeter

**Unity-Greeter / LightDM does not re-focus onto Password box when Session Type has been chosed from menu**

[https://bugs.launchpad.net/unity-greeter/+bug/838392]("https://bugs.launchpad.net/unity-greeter/+bug/838392")

Notes....

When using Unity-Greeter, if you click the Cog in the top right hand corner of the chosen user to change the session type you are logging into (Gnome, Unity/Unity 2D etc). Once the popup menu has disappeared the focus of the cursor remains on the Cog button, if you press enter the Session Type menu reappears.

Surley it should refocus back into the password box so the user can either type their password, or just press enter so the chosen session can load up, without the need of clicking back into the password box first.

It would also be very very usefull, if a flashing type cursor could be made present in the password box aswell when it has got the focus, so the user knows the greeter is ready to take the entry of their password.

...

Have other people seen this behavior aswell?

Thanks

Andy

Yes, and it is annoying.

---

