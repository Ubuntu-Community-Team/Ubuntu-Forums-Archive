---
title: "Login Key Ring"
date: 2012-12-15
forum: New to Ubuntu
---

### Post by johnwill on 2012-12-15
I am running Ubuntu 12.04 64 bit on a lenovo desktop and a dual boot with Windows 7.
I am now getting a message stating: The password you use to log in to your computer no longer matches your LOGIN KEYRING. When I enter my password again it states that the password is incorrect.
This message has been appearing for about three weeks or more.        I have not changed my password,and have updated security fixes (with generous help from this forum)
The only new software that I have downloaded is AVG Antivirus,this may have a bearing?
My password allows me to Log in as normal to these forums and to get online,and the message appears whenever I attempt these actions.
I would be grateful for help with this problem.

---

### Post by DuckHook on 2012-12-16
Hi John,

Please have a look at [this]("http://ubuntuforums.org/showthread.php?t=1917430") thread and try the solution offered by @LewisTM. If it doesn't fix the problem, post the full message back to this forum before deleting further keyrings.

---

### Post by johnwill on 2012-12-16
I have tried to get password/keys via  the  **Dash** to change password key as suggested in your post.
Have accessed help which gives the same information re: changing password keyring.
The resulting files in dash give mainly Microsoft files: am now at a loss on how to continue.

---

### Post by DuckHook on 2012-12-16
> **johnwill said:**
> I have tried to get password/keys via  the  **Dash** to change password key as suggested in your post.
Have accessed help which gives the same information re: changing password keyring.
The resulting files in dash give mainly Microsoft files: am now at a loss on how to continue.

I don't recall from previous posts of yours whether you installed using WUBI (which makes Ubuntu sit inside a file within Windows) or whether you installed Ubuntu into its own separate partition. From your description of above, I suspect that it is a WUBI installation. Please confirm.

The password keyring app in the dash is actually called *seahorse*. It is accessed by:

<SUPER>+<a>
then type *seahorse*

an app will be returned that is described as "passwords and keys" (I know. Why isn't it called seahorse?). Click on that app and you will then be able to follow the rest of the earlier instructions.

Post back to let us know how it goes.

---

### Post by johnwill on 2012-12-17
Hello: Thank you for your latest Post. I was unable to get Seahorse
with <SUPER>+<a>, tried sudo apt-get install seahorse; Success.
but when trying to change Password, was informed that my original password was incorrect,and after several failed attempts am no further forward.
My install of Ubuntu is  WUBI I did not partition.
You mentioned that learning Ubuntu is a steep learning curve: I agree but very interesting. 
No idea how to continue presumably I shall have to reset my original password?But how if the "change password" in the Key ring  will not let me continue.

---

### Post by DuckHook on 2012-12-19
Apologies for the time taken to reply. I've been held up by a combination of personal events and doing some research. Unfortunately, I'm at a loss at this point where to proceed next. Specifically, I'm stumped with the WUBI install. My knowledge is restricted to traditional dual-boot environments, and I don't know my way around the WUBI environment well enough to advise you without risk of borking not only your Ubuntu install, but your Windows one.

If this were a traditional installation, the solution would be similar to [this]("http://ubuntuforums.org/showthread.php?t=2093828"). But the cited solution by @Mr. Hibba only works if the LiveCD can see the Linux OS inside its own partition. When the Linux OS is hidden in a file (as it is with WUBI), I'm stumped on how to access it from "outside", as it were.

I will PM another poster who has some familiarity with WUBI to see if he might not have a solution for you here.

---

### Post by bcbc on 2012-12-19
So you can login to Ubuntu fine. But that same password doesn't unlock your login keyring? That usually happens if you've changed passwords.

(If you don't have an actual password problem, you don't need to change it - although you can do this by booting in Recovery mode, remounting read/write, and then dropping to a root shell. Then enter "passwd <username>" (whatever your username is).)

I think you probably just need to delete the keyring. See here: [http://askubuntu.com/questions/65281/how-to-recover-reset-forgotten-gnome-keyring-password]("http://askubuntu.com/q/65281/14916")

---

### Post by ken78724 on 2013-09-03
i tried the bcbc http guide on my Acer laptop with 12.04 Ubu Studio, which I had built from 9.02. I could not use the right click mentioned in the note posted by the third update. Whereas I have other work underway, I will get at it and try to unlock the keyring at another time.

---

