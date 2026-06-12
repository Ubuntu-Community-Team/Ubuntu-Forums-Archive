---
title: "Keyring password"
date: 2024-05-25
forum: New to Ubuntu
---

### Post by jedwinjim69 on 2024-05-25
HI, I've recently put a clean install of Ubuntu on my laptop - my first time using linux for around 10 years. All is good except after login when I click the chrome browser I get a pop up asking for my default keyring password. I set only 1 password on install, which was my desktop login screen profile password. This password does not work. Leaving it blank does not work. If I untick the box and hit 'cancel' 3 times in a row the keyring password box disappears and I can open chrome and carry on - but clearly this is annoying. can anyone offer any help?

Thanks

---

### Post by #&amp;thj^% on 2024-05-25
What dose this show:
```
less  /usr/share/applications/google-chrome.desktop
```

---

### Post by TheFu on 2024-05-25
I've never used the "keyring". Never saw a good reason for it, but I suppose if you use the semi-built-in web-app connectors, it might be useful.  If you don't use cloudy services, you don't need it and it can be removed.  

I'm always confused when someone chooses to install a web browser from a huge marketing company who actually tells you they will track everything you do in the browser.  I suspect that Chrome might get used, if it is now your default application for those cloudy web-apps - perhaps gmail, calendar, file storage?  Then the credentials for those external services could be stored in the keyring?  IDK. [https://itsfoss.com/ubuntu-keyring/](https://itsfoss.com/ubuntu-keyring/) has an explanation.  I use a password manager for stuff like this and ssh-agent for unlocked ssh-keys, so I only get bothered to unlock them once per login.

You know, might be useful if you actually provide some basic information - which OS, which release, which DE?  Things like that. Nobody here can read your mind, though that's a bit annoying for you and us, I'm certain.

---

### Post by currentshaft on 2024-05-25
It's for the password manager. Just hit escape a few times if you don't plan on using it, or give it a password.

---

### Post by currentshaft on 2024-05-25
> **TheFu said:**
> I'm always confused when someone chooses to install a web browser from a huge marketing company who actually tells you they will track everything you do in the browser.

Why the hyperbole? Chrome is fast and secure, possibly the most secure of any browser available.

Features which are a privacy concern are clearly documented and can be turned off, even if it's tedious and there are a lot of configuration options to change.

---

### Post by TheFu on 2024-05-26
> **currentshaft said:**
> Why the hyperbole? Chrome is fast and secure, possibly the most secure of any browser available.

Features which are a privacy concern are clearly documented and can be turned off, even if it's tedious and there are a lot of configuration options to change.

[https://youtu.be/YnSv8ylLfPw](https://youtu.be/YnSv8ylLfPw) - not everyone wants to feed big brother, much less marketing companies, in exchange for the loss of privacy demanded. Do you work for Google?


There are other browsers than Google-marketing-Chrome that ARE secure AND come with built-in privacy. They use the same engine, if that's what you prefer.  I use a few alternatives when Dillo and Lynx aren't sufficient.

---

### Post by currentshaft on 2024-05-26
> **TheFu said:**
> [https://youtu.be/YnSv8ylLfPw](https://youtu.be/YnSv8ylLfPw) - not everyone wants to feed big brother, much less marketing companies, in exchange for the loss of privacy demanded. Do you work for Google?

There are other browsers than Google-marketing-Chrome that ARE secure AND come with built-in privacy. They use the same engine, if that's what you prefer.  I use a few alternatives when Dillo and Lynx aren't sufficient.

I hope the irony of sending readers to YouTube to justify paranoia about Google is not lost on you.

Yes, there are other Chrome-based browsers. What objective evidence do you have to guarantee their security?

---

