---
title: "Unlock cannot authenticate"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Kissell on 2008-05-09
When I click on something like the network icon in the gnome user bar next to the time, and click "Manual Configuration" I get a box for "Network Settings" but all the options are grey'd out.  

When I click the UNLOCK button, instead of the expected option to authenticate, I get an error "Could Not Authenticate: An Unexpected Error has occurred".

That's not a helpful error message.  Anyone have any idea how I can fix this?

---

### Post by eangaga on 2008-05-09
Is this on a Laptop? If all the options seem inactive, look and see if you have enabled networking. My guess is you have not enabled it. I think this will fix your problem.

---

### Post by spiderbatdad on 2008-05-09
Are you running inside windows (wubi)? I see a cd mounted also, but it looks as though you have installed and are logged into a user account.

---

### Post by Kissell on 2008-05-09
No, I don't know what wubi is, this is just a stand install of i386 Ubuntu 7.10, that was upgraded to Hardy 8.04.  I don't know exactly when this started happening, but I first noticed it after the upgrade.

---

### Post by spiderbatdad on 2008-05-09
maybe kill nm-applet and restart it from the terminal to see if errors are reported.```
sudo killall nm-applet
sudo nm-applet
```

nm-applet will close when you close the terminal. You can start it and fork the process with ALT-F2 then enter nm-applet. I'm sure there is a way to fork from the terminal, but I don't know it.:oops:

---

### Post by spiderbatdad on 2008-05-09
If the problem persists you might contribute to this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/194496](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/194496)

First try typing users-admin in the terminal and see if the problem is eliminated.

---

### Post by Kissell on 2008-05-09
I tried what you suggested, but it didn't fix the problem.

At least I learned that nm-applet is the program for that icon for network settings i was talking about.

you can make it a process running when you close the terminal by putting an ampersand '&' after any command, like: 
> nm-applet &

At least we're both learning.  ;)

But I don't think the problem is with nm-applet, that's just a place where I can show an example/symptom of the problem.  The problem is the UNLOCK thingy in the GUI, which more than just the nm-applet use.

---

### Post by Kissell on 2008-05-09
When I type users-admin or sudo users-admin I get the user settings box, but the UNLOCK button is grayed out, and so are all the users except the user i logged into the GUI with...  when I click on properties of that user all the ACCOUNT tab is available, but the options under USER PRIVILEGES and ADVANCED tabs are all grayed out.  

NOTE: none of the boxes are checked in the USER PRIVILEGES tab, but i can't change that, it won't let me.

---

### Post by spiderbatdad on 2008-05-09
Well perhaps this:```
sudo usermod -a -G admin username
```

Where username is substituted with an existing user (belonging to a group) that you want to give admin privileges to. If user belongs to no group, leave out the -a flag.

---

### Post by Kissell on 2008-05-09
This is what happened...  I'll use root to demonstrate. :KS
> root@Server:/# sudo -a -G admin root
sudo: illegal option `-a'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
root@Server:/# 


was there supposed to be a command after sudo?  sudo doesn't seem to recognize -a or -G as options... 

hmm... I think you meant usermod
> sudo usermod -a -G admin <username>

So I did that, now when I go into users-admin the user priviledge "Administer the System" is checked, but I still don't have any control, I can't uncheck it or check any other boxes, and the UNLOCK button is grayed out so I can't even click it...  btw: UNLOCK is also grayed out in the nm-applet now...  so no more error...  but i still can't make changes to the network settings in nm-applet.  NOTE: I haven't changed anything we haven't covered in this thread.

---

### Post by spiderbatdad on 2008-05-09
Ack! I did mean usermod. Fixed my previous post. Well I'm stumped. It surely seems like a bug. Have you looked at the bug report I linked?  There was mention of making sure **PolicyKit-gnome, PolicyKit** were installed. You might check synaptic for those packages. Good Luck.

---

### Post by Kissell on 2008-05-10
That bug does appear to be the same issue.  

I tried to see if PolicyKit is installed, and my Synaptic Package Manager icon isn't in the menu...  huh...  that's new...

---

### Post by koma77 on 2008-05-12
I've got the exact same problem: unexpected error when trying to unlock the network settings.

I've got another problem as well that might be related: I cannot enter my WPA passphrase. The dialog box just appears again and again and refuses to connect to my wireless network.

Maybe these bugs are related...

---

### Post by Kissell on 2008-05-12
I'm still having the unlock issue, but my wireless WPA-PSK functionality is working just fine.  I don't think the issues are related, as I haven't come across anything until now.

However, I am also using a laptop, and perhaps this Unlock bug only happens on some laptops.

---

### Post by tarvid on 2008-06-22
System, Preferences, Main Menu, System, Preferences, Administration, Right Click Network, Properties, delete gksu in front of command.

---

### Post by buntunub on 2008-07-05
Same problem here exactly. My user also belongs to all the correct groups and none of the suggestions posted here did a thing to fix the issue.

What fixed it was [this]("http://ubuntuforums.org/showthread.php?t=653921&highlight=unable+find+session+cookie") thread.

In essence, the issue lies with -

1. Incorrect /etc/hosts setups.
2. Users not added to "polkituser" in /etc/group.

---

### Post by Neo Dagger on 2008-07-17
I had this problem and couldn't unlock.  kept wobbling and throwing out my password.  Checked keyboard layout and found that it had somehow been changed to USA instead of UK which was the original setup.  Changed it back and could enter fine.  Think it might have been the compiz stuff I installed.  failing that, I had installed xfce prior to that.  Just my two beans worth.  hope it helps someone.

---

### Post by Eldis on 2008-08-06
I have this problem aswell and the other thread mentioned here didn't fix it. Time Admin and User Groups don't work.

any more ideas ?

---

### Post by Eldis on 2008-08-13
Actually it ended up being a problem while connecting with nxclient, when I log in locally the unlock key can be accessed. I still don't know however why I can't access the unlock key when accessing with nxclient.

---

### Post by Snyper64 on 2008-08-13
Also having issues with this, until I get it fixed I can't install my new router due to setting up a static IP with my current router :(.

---

### Post by EmilyRose on 2008-08-27
Hi there, this just started happening to me. I've been able to unlock up till today, and not sure whats changed, sudo works in the command line, but I can't do ANYTHING that requires my password with a gui - not update, not unlock anything. Help?

---

### Post by Dr.C on 2008-09-01
As a number of others, a dialog box popped up with the message "Could not Authenticate" each time I attempted to unlock settings for USERS AND GROUPS and TIME AND DATE.  Taking cues from several who posted suggestions, I solved the problem by doing the following:

1) Engaged Synaptic Package Manager to re-install Policykit version 0.7-2ubuntu7 (hardy) and  Policykit-gnome version 0.7-2ubuntu1.1

2) Reset, from Regional & Language - System Settings, language settings to default (US English for my machine)

Unfortunately, I did not isolate the variables and can't say whether they engage separately or together.  Pax, ~rc

---

### Post by estanton on 2008-09-23
I have a hunch what is going on here. I just started suffering from this, and the only thing I've changed recently on the computer is adding a second user. I named the user admin, Since it was generic and I wasn't planning on using it much. In any case my regular log-in no longer has administrative capabilities and neither does the new admin account. I suspect that it was the actual creation of the second account that set this off. I am now paralyzed without proper root privileges from the system.
I remember when hardy was released somebody was shut out of their system completely because their login was pulse, which was no abrogated for the system. I think this is something similar.
Any thoughts?

---

### Post by Kentanner11 on 2008-10-05
> **estanton said:**
> I have a hunch what is going on here. I just started suffering from this, and the only thing I've changed recently on the computer is adding a second user. I named the user admin, Since it was generic and I wasn't planning on using it much. In any case my regular log-in no longer has administrative capabilities and neither does the new admin account. I suspect that it was the actual creation of the second account that set this off. I am now paralyzed without proper root privileges from the system.
I remember when hardy was released somebody was shut out of their system completely because their login was pulse, which was no abrogated for the system. I think this is something similar.
Any thoughts?

I did the EXACT same thing... added a new user named admin and was unable to unlock in both accts.... any solutions? 
I feel better knowing its not just me.

---

### Post by jagsir on 2008-10-11
>  I solved the problem by doing the following:

1) Engaged Synaptic Package Manager to re-install Policykit version 0.7-2ubuntu7 (hardy) and  Policykit-gnome version 0.7-2ubuntu1.1
 Pax, ~rc

Pax, Thanks. 

This worked for me. Doing just the step one, made the problem go away.

_Jagsir

---

### Post by maninsitu on 2008-10-24
After reading a number of threads and posts about pol-kit, I went to the Policykit Library Reference manual:

[http://hal.freedesktop.org/docs/PolicyKit/polkit-auth.1.html](http://hal.freedesktop.org/docs/PolicyKit/polkit-auth.1.html)

I used the following and have been able to unlock "Users and Groups"
root@ubuntu:/home/username# polkit-auth username --user root  
(replace username with your username)

The only problem remaining is the fact that I can't use the desktop Update Manager as I am still unable to authenticate. I think I may have to check the properties under the edit menu via a right click on Applications.

Or continue to review pol-kit. I think by the number of threads on this and pol-kit, I think there maybe some problems with it. I note that the version I have is 0.7, so it is a fairly new application. ):P

---

### Post by heatpumpcontrol on 2009-01-15
I ended up recreating my account. I noticed that under my other account I would not get the message. I figured it was account specific. After recreating my account, it works again. No errors.

---

### Post by bmullan on 2009-05-12
> **Eldis said:**
> Actually it ended up being a problem while connecting with nxclient, when I log in locally the unlock key can be accessed. I still don't know however why I can't access the unlock key when accessing with nxclient.
I've been fighting this same problem... did you ever get a solution?  
My problem is that I am using NXClient to access the Ubuntu because it is actually running out on Amazon's cloud and I don't really have a direct connection to it.

---

### Post by pallbearerx on 2009-07-29
I know this is an old thread, but I just wanted to say 'thanks' to the folks who figured this out.  I had an installation of 8.04 Server that was having this same issue, and the solution posed by Dr. C fixed this for me.  Many thanks!
> 
1) Engaged Synaptic Package Manager to re-install Policykit version 0.7-2ubuntu7 (hardy) and Policykit-gnome version 0.7-2ubuntu1.1

-pbX

---

