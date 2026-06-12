---
title: "User Configuration Files"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by cforput on 2008-10-24
I have been configuring my Ubuntu for several things. I have multiple users on my laptop and I notice that some things work for on user but not the other. I have seen some posts that mention checking the user configuration files but I have no idea where they are (newbie here).

Can someone tell me where I can find the configuration files that load when I log in with a particular user.

---

### Post by SunnyRabbiera on 2008-10-24
what do you mean?
what stuff are you referring to?

---

### Post by taseedorf on 2008-10-24
well, a simple way may be to go to system -> administration -> user and groups......first, edit the users and check they have permissions, etc.... if they are trying to run things installed only for certain users, they will not have the permissions....such as certain icon themes, etc...

ALSO, add everyone to ONE group....say....notebookusers.... or even root if you don't care..... and than change permissions of group

like stated earlier, what doesnt work for other users?

---

### Post by cforput on 2008-10-24
Let me explain further. I spent hours last night and into the wee hours of the AM to get flash player to work. I tried so much stuff I don't even know what finally did it. To my surprise, I only found out flash was installed correctly by logging in as a different user on my laptop and flash worked. I then went back to the first user and flash doesn't work. It works on one user but not the other. 

I saw a post by someone that was trying to get something to work and one of the responses was something along the lines of: Try setting up a new user because it uses the system default settings. If that works then it is something in the user's configuration files.

I'm I making any sense here????

---

### Post by SunnyRabbiera on 2008-10-24
> **cforput said:**
> Let me explain further. I spent hours last night and into the wee hours of the AM to get flash player to work. I tried so much stuff I don't even know what finally did it. To my surprise, I only found out flash was installed correctly by logging in as a different user on my laptop and flash worked. I then went back to the first user and flash doesn't work. It works on one user but not the other. 

I saw a post by someone that was trying to get something to work and one of the responses was something along the lines of: Try setting up a new user because it uses the system default settings. If that works then it is something in the user's configuration files.

I'm I making any sense here????


well stuff like installing flash I can understand as only the main user by default can install applications.
But flash itself not being able to work for all users? strange as its supposed to work for all users.

---

### Post by cforput on 2008-10-25
I really do appreciate everyone's assistance to try and fix my problem but I would like to get back to my initial question. Where can I find the configuration files that are loaded when a user logs in? I would like to learn more about Ubuntu and the way it works.

---

### Post by jerome1232 on 2008-10-25
Well user specific settings are in your ~/ usually in hidden files (they have a '.' in front of them) hit ctrl+h to see them.


System wide settings are in /etc.

---

### Post by The Cog on 2008-10-25
Flash can be installed in two places.

It can be installed into /usr/lib/firefox-addons/plugins in which case it is available to all users. Only root can write to that directory.

Alternatively, each individual user can run a flash installer in which case it gets installed in $HOME/.mozilla/plugins and applies only to that particular user.

I think you could even have a situation where an old flash is in the system-wide plugins but one user has performed an upgrade so their own plugin runs a later version.

---

