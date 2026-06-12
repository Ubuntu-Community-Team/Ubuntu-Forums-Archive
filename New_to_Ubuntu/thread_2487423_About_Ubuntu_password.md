---
title: "About Ubuntu password"
date: 2023-06-04
forum: New to Ubuntu
---

### Post by gimpturkey on 2023-06-04
I installed Ubuntu 22.04. I wanted to change the password that was on the first installation. I can no longer access that password. Ubuntu asks for a password for every operation I want to do. I couldn't cancel. What should I do about it?

---

### Post by TheFu on 2023-06-04
After login, run the 'passwd' command and change the password for the user.

I suspect the>  "Ubuntu asks for a password for every operation I want to do" is hyperbole.  If you run **ls** or **cd** or **top** or a browser or **libreoffice**, it doesn't ask for a password, does it?  It only asks for a password for administrative stuff.

I can't see any images. Sorry.

---

### Post by Rubi1200 on 2023-06-04
Hi and welcome to the forums :-)

From your screenshot, you are trying to run the command ```
sudo -i
``` Lower case i not L. Please help us understand what you are trying to do so we can offer advice.

---

### Post by gimpturkey on 2023-06-09
Thank you. We solved the problem. The problem was this: Terminal was asking for a password for every job I was going to do, I changed this password. Then I forgot because I didn't save it somewhere. I didn't do anything without a password. Yes obvious programs work without password gmp, libreoffice etc. I could not solve the problem because it asks for a password when installing it on the terminal. We fixed the problem by reinstalling Ubuntu and setting a new password.

---

### Post by TheFu on 2023-06-09
Reinstall was 1 method and perhaps the easiest.

However, with an install ISO from the same version, but not necessarily the same flavor, of ubuntu, you could have used the "Try Ubuntu" mode, setup a chroot so the passwd and shadow files in the installed OS were available to the programs in the *Try Ubuntu* environment, then run the **passwd** command with sudo (as the 'ubuntu' username). Then just set the password for the account to what you wanted.  There are probably 100 how-to guides on the internet for this.  

I know that Ubuntu allows setting up some logins without any password, but this is a really, really, bad idea for accounts with sudo.  Without use, we forget passwords.  The solution is to start using a password manager to keep all your passwords inside a safe, encrypted, tool.  KeePassXC is one. I use it.  The password DB can be copied to any platform so shared with your phone, tablet, MS-Windows, OSX, Apple's IOS, Linux, BSD. It is binary compatible.  When setup to the full, secure, solution, it makes logging into websites easier with completely random credentials for each webapp.  For example, I don't know my username or password to my bank.  I haven't typed it in years.  Both are random.  

sudo uses the same password that the userid has already.  Changing it makes no difference. The new password gets used from that point forward.

Anyway, glad you found an answer.

---

### Post by dhotrum52 on 2023-11-20
Guys I have the same problem. But going to command line and running sudo -i it immediately asks for my password. I was trying to install xampp and somehow changed my password. I HAVE NO IDEA WHAT IT IS. Is my only option to try and reinstall UB 22.04? I have tried to enter the last known password and after I made it i wrote it down and have used it a few times. Now some how it is changed. Is there anyway to find it?

---

### Post by ian-weisser on 2023-11-20
> **dhotrum52 said:**
> But going to command line and running sudo -i it immediately asks for my password.

That is normal behavior. It's supposed to do that.
Folks can't just claim to be somebody else without proof. That would be a big security hole. The password is that proof.

> **dhotrum52 said:**
> Is my only option to try and reinstall UB 22.04?

No. There's a recovery mode, which you can access from GRUB.

---

### Post by dhotrum52 on 2023-11-21
So....are you gonna tell me the grub way to find it?

---

### Post by Rubi1200 on 2023-11-21
To reset the password follow the instructions here:
[https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](https://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

---

### Post by ActionParsnip on 2023-11-21
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by dhotrum52 on 2023-11-21
I tried this link: [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)
But that didn't work. I used my USB install and went as far as UB seeing my sda1 but entering the commands on that link did not work. I do not have access to admin password. What next? I took a picture of what happened when I trie dto use trhe reset at that link but where do I send the picture.?

---

### Post by Rubi1200 on 2023-11-21
Did you also try the instructions in the link I posted above?

> To reset the password follow the instructions here:
[https://askubuntu.com/questions/2400...ative-password](https://askubuntu.com/questions/2400...ative-password)


---

### Post by TheFu on 2023-11-22
> **dhotrum52 said:**
> So....are you gonna tell me the grub way to find it?

There is no way to uncover a prior password, since they aren't stored anywhere on the system. Just the hash from the correct input is stored in the passwd DB (often inside /etc/shadow).

There are lots and lots of how-to guides for setting a new password for specific users. Ubuntu isn't any different than other Linux systems, so any of those will work.  Telling people how to crack into random linux systems isn't the best thing we can do in these forums, as I'm certain you can understand.  There are a few different methods. I can think of 3 now, but all of them happen outside the booted OS.  1 hint: use maintenance mode from the advanced boot grub menu.

Also, if the OS is using LUKS encryption, none of those 3 methods will work.  You'll need to reinstall.  If you've wasted more than 15 minutes on this issue, you could have reinstalled already.

---

