---
title: "Ubuntu 20.04.6 LTS: https://www.flightradar24.com, Brave browser problem"
date: 2024-05-04
forum: New to Ubuntu
---

### Post by maketopsite on 2024-05-04
[https://www.flightradar24.com](https://www.flightradar24.com) does not work sometime in Brave browser:```

Issue with your browser
Unfortunately, your current browser does not support WebGL which is essential for the functioning of Flightradar24. Please change to a supported browser and try again. WebGL is supported by most major browsers including Chrome, Firefox, Safari, Edge and Opera.

```

Browser restart is needed to make it work again. Any idea please ?

---

### Post by TheFu on 2024-05-05
I've never had an issue.  Are you logged into your account or just using the free side?  I have an account.
I'm running brave in **firejail --private** on 20.04.  My system has an iGPU with Ryzen.  Don't know what to say, besides *it works here.*  Do you have webGL enabled?  I use brave to visit more dangerous parts of the internet almost always inside a private firejail environment.  I have brave setup to work with videos and more graphical websites.  

Firefox is my day-to-day browser where I keep all the dangerous new stuff disabled.  It runs in a firejail too, but not a private environment.  Things like webgl, webrtc, and javascript for most websites are disabled in firefox, but not under Brave.

brave-browser  v1.65.126

You can test if it is a userid-specific issue or a system issue by creating a new userid, leaving all the defaults and testing with brave.  If it works there, then it is something in your personal settings, most likely.

---

### Post by #&amp;thj^% on 2024-05-05
Works nicely with and without firejail, firejail --private.

I'm just on the free version here, or no account.

---

### Post by maketopsite on 2024-05-15
> **TheFu said:**
> I've never had an issue.  Are you logged into your account or just using the free side?  I have an account.
I'm running brave in **firejail --private** on 20.04.  My system has an iGPU with Ryzen.  Don't know what to say, besides *it works here.*  Do you have webGL enabled?  I use brave to visit more dangerous parts of the internet almost always inside a private firejail environment.  I have brave setup to work with videos and more graphical websites.  

Firefox is my day-to-day browser where I keep all the dangerous new stuff disabled.  It runs in a firejail too, but not a private environment.  Things like webgl, webrtc, and javascript for most websites are disabled in firefox, but not under Brave.

brave-browser  v1.65.126

You can test if it is a userid-specific issue or a system issue by creating a new userid, leaving all the defaults and testing with brave.  If it works there, then it is something in your personal settings, most likely.

It has almost never happened again since first post here.

I don't have an account.
No firejail etc, no plugin. Optimus laptop with NVIDIA.

Default config of Brave br. so WebGL should be enabled.
[https://get.webgl.org/](https://get.webgl.org/)
```
Your browser supports WebGL
```

---

### Post by maketopsite on 2024-05-15
> **1fallen said:**
> Works nicely with and without firejail, firejail --private.

I'm just on the free version here, or no account.

Thank you it seems to be OK again. (Maybe problems with cache ?)

---

