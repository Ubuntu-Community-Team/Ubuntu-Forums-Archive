---
title: "Create a limited user"
date: 2018-04-28
forum: New to Ubuntu
---

### Post by mahdi87gh on 2018-04-28
Hi, I'm new to lubuntu . I want to create a user account which can't change the ip address of the system. is it possible?
Thanks

---

### Post by sevendogsbsd on 2018-04-28
Yes, the "standard" user in the settings --> details --> users dialog cannot make changes to the system as they do not have sudo access.

---

### Post by mahdi87gh on 2018-04-28
> **sevendogsbsd said:**
> Yes, the "standard" user in the settings --> details --> users dialog cannot make changes to the system as they do not have sudo access.
Thanks. The question is how to make a standard user?
I created a new user from system->users and groups. then logged in with that user which I saw it was able to change IP address.

---

### Post by sevendogsbsd on 2018-04-29
I read the question and there are 2 types of users in Ubuntu: "standard" and "administrator". What I didn't realize, because I have never tried, is that the standard user can change the system IP address. This is a security issue in my opinion because a user set up as "standard" should not be able to change any system related settings, other than for their own profile. I don't use a Linux desktop in a corporate environment, only servers, and those are locked down. I am disappointed this is possible, even in a home setting.

---

### Post by shanmukhateja on 2018-05-06
How about removing the user from the netdev group, says something like:

# gpasswd -d <username> netdev

I believe you need to reboot for changes to take effect.

---

### Post by mahdi87gh on 2018-05-06
Thanks,
I found out when I create a user using user-interface , it shows it as a custom user, there is an option to change it to desktop user. then this new user cannot change IP Address.

---

### Post by SeijiSensei on 2018-05-06
> **sevendogsbsd said:**
> I read the question and there are 2 types of users in Ubuntu: "standard" and "administrator". What I didn't realize, because I have never tried, is that the standard user can change the system IP address. This is a security issue in my opinion because a user set up as "standard" should not be able to change any system related settings, other than for their own profile. I don't use a Linux desktop in a corporate environment, only servers, and those are locked down. I am disappointed this is possible, even in a home setting.

You would not be able to use a computer with wifi if ordinary users cannot set the IP address.  After the computer boots, the user must specify the SSID for the wifi connection.  You can make an SSID the default, but the connection still happens only after the user logs in.

---

### Post by sevendogsbsd on 2018-05-06
Understood, thanks for the clarification.

---

