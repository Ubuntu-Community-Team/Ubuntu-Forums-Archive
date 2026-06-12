---
title: "Re: Terminal won't let me type password"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by jmahone on 2012-03-11
hi there,
the terminal wont let me enter a password, i am a newbee to this and i am wondering what is the password?

It just comes up with:
enter password for password:
i dont know the password?:confused::icon_frown:

Thank You

---

### Post by aysiu on 2012-03-11
It's your own login password, and when you type it in there will be no visual feedback. Just type it and hit Enter when you're done.

Despite what others will tell you, this is **not** a security feature (maybe it was back in the 1970s). More details [here](http://psychocats.net/ubuntu/passwordinterminal).

---

### Post by imachavel on 2012-03-11
if you don't know it, you may need to google a bit to find out how to reset the password, etc. It should be in user account settings, in system settings I believe, that is if you are using the Unity interface, kde or gnome not sure but the concept is the same and it will be in a very similar place the interface doesn't usually change from pluto to mars that often.

resetting the password will of course require you enter the old password, so this method may not solve your problem. When you install ubuntu it asks you to enter a password upon installation. It is not wise to not have written this down. I am hoping you partitioned extra space off your disk by booting to a partition manager, and then installed ubuntu, instead of installing through windows after downloading it. Although it can easily be installed over, have you already transferred over all the files? Good luck man

---

### Post by aysiu on 2012-03-11
You can reset your password without knowing your old password. You can do it by booting into recovery mode:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by imachavel on 2012-03-11
well like you said a password hasn't had anything to do with open bsd and security since the 70s. After all, you can't reset the password in windows that easily, although there are password reset recovery mode .iso disks you can download and boot to and reset. I'd definitely print the page out though:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

let's hope your printer drivers are supported for your printer in ubuntu(generally it is), because recovery mode is terminal shell(bash) mode, so you need to know how to use the terminal, cd directories, be in root, be logged in as root. ls directories, etc. etc. etc. etc. and when you are done use

sudo reboot now!

it will ask you for a password so read:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

carefully

---

