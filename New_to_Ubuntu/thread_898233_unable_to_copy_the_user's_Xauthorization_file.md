---
title: "unable to copy the user's Xauthorization file?"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by m1ck on 2008-08-23
Hi all, i am trying to run the synaptic package manager and keep getting this error 

"Failed to run usr/sbin/synaptic as user root   
Unable to copy the user's Xauthorization file.".

I also get this error when trying to run the setup login screen, everything was working fine until this morning - i haven't changed or messed around with any settings either so what could be the problem?.

Any help would be greatly appreciated.

---

### Post by eightmillion on 2008-08-23
First make sure that users .Xauthority file is present in their home directory and make sure it has the correct permissions. running ls -l /home/username/.Xauthority should result in this output:
> -rw------- 1 username username 319 2008-08-22 19:35 .Xauthority
If it doesn't look like that, you may have to change the ownership and permissions manually:
> sudo chmod 600 /home/username/.Xauthority
sudo chown username:username /home/user/.Xauthority
Be sure to change all instances of username to the correct username.

---

### Post by eightmillion on 2008-08-23
It's probably a good idea to make sure the user is part of the admin group.
> sudo adduser username admin

---

### Post by m1ck on 2008-08-23
ls -l /home/username/.Xauthority i get "no such file or directory"

also i am part of the admin group

---

### Post by eightmillion on 2008-08-23
Are the permissions right one the users home directory? The .Xauthority file should be recreated on login if it's missing. Try:
> ls -l /home/
The output should look like this:
> drwxr-xr-x 61 username username 4096 2008-08-23 02:04 username
If the user's home directory is not owned by that user you'll have to change that:
> sudo chown -R username:username /home/username
And I have to ask, you did change username to the appropriate user's name, right?

---

### Post by m1ck on 2008-08-23
yes it comes up with my username.

"And I have to ask, you did change username to the appropriate user's name, right?"

 i only have my username on here if that's what you mean.

---

### Post by eightmillion on 2008-08-23
You'll probably need to run xauth. Type xauth in a terminal and it will give you a prompt. Run these commands one at a time:
> generate :0 . trusted
generate localhost.localdomain/unix:0 . trusted

---

### Post by m1ck on 2008-08-23
> **eightmillion said:**
> You'll probably need to run xauth. Type xauth in a terminal and it will give you a prompt. Run these commands one at a time:


i got this:
"  unable to open display "localhost.localdomain/unix:0."

---

### Post by m1ck on 2008-08-23
hey i've got it working sort of, i don't know what fixed but it working almost i can access synaptic but when i try to open the "setup login screen" it opens then disappears.

I've also just noticed that if i click on the applications menu nothing happens...places and system list with no problems

---

### Post by eightmillion on 2008-08-23
It really sounds like you're having issues with permissions. I would go ahead run this command:
> sudo chmod -R username:username ~/

---

### Post by m1ck on 2008-08-23
i keep getting chmod: invalid mode: `myusername:myusername'
Try `chmod --help' for more information

---

### Post by eightmillion on 2008-08-23
Sorry, that should have been **chown**.

---

### Post by m1ck on 2008-08-23
chown: cannot access `/home/username/.gvfs': Permission denied

---

### Post by eightmillion on 2008-08-23
> sudo chown -R username:username ~ 


.

---

### Post by m1ck on 2008-08-23
i dunno im totally lost - thanks for your patience though it's really appreciated.

---

### Post by eightmillion on 2008-08-23
No problem. I don't know why they even put that .gvfs directory in the home directory. It's nothing but trouble.

---

### Post by m1ck on 2008-08-23
[solved] well...sort of - i have just created another user so my desktop is back to normal.

---

### Post by freesitebuilder on 2008-10-05
I had this problem and have followed the instructions - but now I can't load any sys admin stuff, inlcuding terminal. 

If I go to recovery, and use "repair broken packages", will this cure it? As you can tell, I'm not a very experienced user!

---

### Post by ranger1021994 on 2011-09-12
I got .gvfs Permission Denied

---

