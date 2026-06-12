---
title: "Ultra-Newb Problem"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Corwin Amber on 2008-05-19
Ok, I have my dunce cap on:-) I installed Ubuntu 8.04 successfully. I wrote down my password. I thought it said that my User Name was just my name. I've tried every combination of my name using caps/non caps I can think of plus <xxxx-laptop> that I see at the bottom of the login screen. I tried the shell-PW changing procedure I found on this site in case I had written it down wrong. I still get "Incorrect username or password" error message when logging on.
Is there any way I can find out my user name without re-installing?

---

### Post by spiderbatdad on 2008-05-19
Gosh haven't thought of Zelazny in years.
You should see your user name in the lower right hand corner of the login screen.
You can also run ```
cat /etc/passwd
```From the recovery prompt and look at the end of the list for: Someuser:x 1000:1000.... this uid:1000 is the primary user account.

---

### Post by Corwin Amber on 2008-05-19
> **spiderbatdad said:**
> Gosh haven't thought of Zelazny in years.
You should see your user name in the lower right hand corner of the login screen.

[COLOR="Green"]   I thought that might be the case. I tried it as my username (plus all cap/noncap variations) No dice.[/COLOR]

You can also run ```
cat /etc/passwd
```From the recovery prompt and look at the end of the list for: Someuser:x 1000:1000.... this uid:1000 is the primary user account.
[COLOR="Green"][COLOR="Green"]Tried that. I got the recovery prompt and tried entering the code. The </> wouldn't appear when I typed them:-(
[/COLOR][/COLOR]

---

### Post by billgoldberg on 2008-05-19
Just install it again, it will take 20 min and the problem is fixed.

---

### Post by utUtu on 2008-05-19
> **Corwin Amber said:**
> Ok, I have my dunce cap on:-) I installed Ubuntu 8.04 successfully. I wrote down my password. I thought it said that my User Name was just my name. I've tried every combination of my name using caps/non caps I can think of plus <xxxx-laptop> that I see at the bottom of the login screen. I tried the shell-PW changing procedure I found on this site in case I had written it down wrong. I still get "Incorrect username or password" error message when logging on.
Is there any way I can find out my user name without re-installing?

If you have live CD, boot with it and then hopefully it will mount your hard drive.  Once mounted, browse your /etc for 'passwd' file.  list this file by cat /where-it's-mounted/etc/passwd

---

### Post by utUtu on 2008-05-19
Oh by the way, if your name was William Goldsberg, ubuntu suggests your user name as 'william' - always lower case, if you accepted it as is.

---

### Post by spiderbatdad on 2008-05-19
The live cd wont mount your root partition by default. You will have to manually mount it. Open the terminal and run ```
sudo fdisk -l
```sudo is necessary. You will see the root '/' partition perhaps /dev/sda1 .
You would the run```
sudo mkdir /media/sda
sudo mount -t ext3 /dev/sda1 /media/sda
```This will put the volume on your desktop. Double click the volume and browse to /etc/passwd (don't be confused by /etc/passwd- which you wont be able to open) and look at the end of the list for User:x 1000:1000 where 'User' is actually a user name. Once you know the username, close the terminal and reopen it.```
sudo umount /media/sda
```Shut down and remove the cd. Boot into recovery mode.

```
passwd -d User
```again 'User' is replaced with the actual username.
This deletes the user's password. Then give the user a new password.
```
passwd User
```Reboot and login.

---

### Post by saratchandra on 2008-05-19
Did you try with your first name as the username?

---

