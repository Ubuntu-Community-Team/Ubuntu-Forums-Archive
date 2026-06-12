---
title: "User account can't fathom passwords"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Fergus Pearson on 2012-08-28
I'm struggling to get to grips with passwords. I've reinstalled twice to try to sort it but still have problems. I've learnt not to try to get rid of passwords. The current problem is that when I created an additional account (a standard one) it didn't ask me to create a password, so I didn't. I clicked to log on automatically. This works fine: when I switch the laptop on it goes automatically to that standard account. The trouble is when I then go to my admin account, and back again to the standard account, it asks for a password. I've tried 'none' and my admin password, etc but doesn't work. I have to shut down and boot up again to get into it. I know how to delete that acc and start again, but how can I prevent this happening again?

---

### Post by wojox on 2012-08-28
Just create a password for the additional account. Click on Account Disabled.

---

### Post by Fergus Pearson on 2012-08-28
Thanks Wojox - I'll have to do that. Do I presume then that it's impossible to set up even a standard account without setting a password?

I'm having trouble deleting that standard account. It says that it will leave the computer in an unstable state (or words to that effect) because I'm not logging out of that account (I can't log out because I can't get in).  

Also I find I can't shut down the computer - is that because I can't log out of that standard account? I've had to press the on/off button to close down.

---

### Post by mansonfan78 on 2012-08-28
Open a terminal and type:  "sudo gedit /etc/lightdm/lightdm.conf" (leave out the quotes), find the line that says "autologin user" and either delete the line (or add a # in front of it) save and close.  Now when you restart the computer login to your admin account and try to delete the other account.  You should only be logged in to your admin account and shouldn't have any trouble.

---

### Post by mansonfan78 on 2012-08-28
And to answer your other question:  every account HAS to have a password.

---

### Post by Fergus Pearson on 2012-08-29
Thanks very much! That has sorted me out.  Hopefully I'll be properly password-aware from now on. I appreciate your help.

---

