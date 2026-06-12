---
title: "shell script permission?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by garyed on 2008-09-22
Is there any way to make a shell scripts contents unreadable to the user yet still be executeable?

The problem I have is I have a script that runs at start-up that uses sudo & automatically enters my password at boot up. I've tried to make it unreadable but if I do it won't run. Any ideas?

---

### Post by LowSky on 2008-09-22
Did you know Ubuntu has a autologin feature, no scripts needed. Also why do you need sudo at start up, operating as super user all the time is mighty dangerous

---

### Post by garyed on 2008-09-22
> **LowSky said:**
> Did you know Ubuntu has a autologin feature, no scripts needed. Also why do you need sudo at start up, operating as super user all the time is mighty dangerous

I might not have explained myself completely.
I know about auto login but what I've done is written a small shell script that gives me a warning when my next boot will be a forced file check.
I put it in my start up sessions so every boot it checks my numbers of boots since the last check. In order to run it needs sudo & my password  to call the tune2fs command. I'm not logging in as root so its just for that one command. The script works fine but I'm just trying to figure a way that no one else could open up the script & read my password.

---

### Post by Mornedhel on 2008-09-22
> **garyed said:**
> what I've done is written a small shell script that gives me a warning when my next boot will be a forced file check.

I think there's something like that in the repositories already...

Anyway, "chmod 111 somefile" makes the file executable only (non-readable, non-writable) to everyone but root.

---

### Post by anotherdisciple on 2008-09-22
I'm fairly confident that chmod 111 won't work properly. I don't think you can execute something that you can't read. Let me know if I'm wrong though.

---

### Post by Mornedhel on 2008-09-22
Good call. I had to chmod 511 it. Never noticed before, but makes sense.

511 works and will prevent anyone but you and root from reading it anyway. So if they're reading it, your password is busted already.

---

### Post by garyed on 2008-09-22
The problem I see is that a shell script won't run unless it has read & execute permission so if any one can run it that means they can read my password. I have my machine set to auto logon so who ever starts it up has my user priviliges. I'm not really worried about it but I was thinking there should be some way to solve this problem without changing auto logon.

---

### Post by hyper_ch on 2008-09-22
write the program in another language (like c) and then compile it. Then you have a unreadable binary.

---

### Post by garyed on 2008-09-22
> **hyper_ch said:**
> write the program in another language (like c) and then compile it. Then you have a unreadable binary.

Its funny you say that because I actually wrote the first part that uses the password in C & compiled it & then called it in the script & it works. My programming skills are really very basic.

---

### Post by ibuclaw on 2008-09-22
You do know that there is always the sudoers file :)

type in
```
export EDITOR="gedit"
```
or nano, emacs, vim, leafpad, kwrite (whatever your fancy).

Then run:
```
sudo -E visudo
```
and at the **bottom** of the file, insert the following
```
%name    ALL=NOPASSWD: /path/to/script
```
where **name** is your username and **/path/to/script** is the full file path to the script you wish to run.
ie:
/home/tinivole/bin/foobar.sh

Save and quit.


Then have in your sessions manager:
```
sudo /path/to/script.sh
```
or
```
sudo script.sh
```
if the script is within one of your $PATH paths.

Regards
Iain

---

