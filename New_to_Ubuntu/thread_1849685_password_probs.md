---
title: "password probs"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by spacejaz on 2011-09-25
Hello. I am brand new to UBUNTU and after trying to get UBUNTU 11 to work on my ACER Aspire laptop, with no success, i downloaded 10.04 which works just fine.
I have several problems now, as I can't configure it to connect to the internet AND when I use "sudo", the system askes for a password which doesn't work....even though I have made myself "administrator" on the system.
Can anyone help?
cheers

---

### Post by Gone fishing on 2011-09-25
If you are logged on as an administrator sudo password should work. Have you remembered that Linux is case specific?

---

### Post by haqking on 2011-09-25
> **spacejaz said:**
> Hello. I am brand new to UBUNTU and after trying to get UBUNTU 11 to work on my ACER Aspire laptop, with no success, i downloaded 10.04 which works just fine.
I have several problems now, as I can't configure it to connect to the internet AND when I use "sudo", the system askes for a password which doesn't work....even though I have made myself "administrator" on the system.
Can anyone help?
cheers

The password it asks for is **YOUR** password so make sure you type the password you login with etc.

As mentioned above, Linux is case sensitive so make sure the caps lock key is not on.

There will be no local echo of the password as you type either so if you are hoping to see some feedback on the screen you wont see any.

So as long as you are in the sudoers file (which you should be if you created the system) then whenever you use sudo or the system asks for a Password it is asking for your **YOUR** password.

read here to be clear [**ROOTSUDO**]("https://help.ubuntu.com/community/RootSudo")

---

