---
title: "Systemd?"
date: 2020-04-14
forum: New to Ubuntu
---

### Post by wyattwhiteeagle on 2020-04-14
OK, my laptop suspending or entering sleep or hybernation mode is beginning to get a bit annoying.

Every time I open my lid or come back to the laptop I find the screen has locked and requires a password after pushing any key and lifting the "screensaver" (MS Windows term)

I consulted the Ubuntu desktop guide about it.

UDG mentions Tweaks and says the settings wont work unless systemd is being used.

A general search in UDG reveals that is the only place where systemd is mentioned and directs the user to contact the Distro for more info.

I need to change the settings. I don't have the need to keep things hidden from those who are around me. It's only me and my better 1/2 who gets on my system and there's nobody else. She and I don't keep secrets from each other so I don't have the need for my system to require me to "log in" that often.

I prefer to only need to enter a password when restarting and using the terminal.

How do I make sure I'm using systemd or is there a quicker easier way in the terminal?

---

### Post by Impavidus on 2020-04-14
systemd is the system deamon. It's a programme running in the background and doing a lot of useful tasks and a bit more. If you use a recent Ubuntu, you use systemd.

I type my password many times each day. It takes me about three seconds each time. The password is stored in my motor memory; I would be unable to type my password when switching keyboard layout. And I trust everybody who might get physical access to my computer, some of whom would be able to hack their way in anyway.

---

### Post by GhX6GZMB on 2020-04-14
Your problem is Xscreensaver, I have the same issue as well, but have until now not found a satisfactory solution. I had the same question here:
[https://ubuntuforums.org/showthread.php?t=2440681](https://ubuntuforums.org/showthread.php?t=2440681)

---

### Post by deadflowr on 2020-04-14
> **ml9104 said:**
> Your problem is Xscreensaver, I have the same issue as well, but have until now not found a satisfactory solution. I had the same question here:
[https://ubuntuforums.org/showthread.php?t=2440681](https://ubuntuforums.org/showthread.php?t=2440681)

That depends if they have an install that uses xscreensaver.
Ubuntu does not use xscreensaver.


To the OP have you tried this:
[https://askubuntu.com/questions/1048774/disabling-lock-screen-18-04]("https://askubuntu.com/questions/1048774/disabling-lock-screen-18-04")

As far as systemd, you are using it.
Ubuntu uses it by default

---

