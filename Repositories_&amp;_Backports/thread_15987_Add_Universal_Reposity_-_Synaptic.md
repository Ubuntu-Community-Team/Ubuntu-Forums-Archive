---
title: "Add Universal Reposity - Synaptic"
date: 2005-02-18
forum: Repositories &amp; Backports
---

### Post by search66 on 2005-02-18
This is almost a "double post", but my inital question lead to repositories... so, I'm posting this in here.

How can I add the Universal Repository without having a network connection?

---

### Post by rwabel on 2005-02-18
[QUOTE=search66]This is almost a "double post", but my inital question lead to repositories... so, I'm posting this in here.
  
  How can I add the Universal Repository without having a network connection?[/QUOTE]
  
  I'm not sure if I understand your question right. You just want to add the repository?
 
 Open a terminal and write
  ```
sudo /etc/apt/sources.list
``` 
 
   then you add the universal repository to it
  **[color=black]for warty:[/color]**
   ```
deb http://archive.ubuntu.com/ubuntu/ warty universe
 deb-src http://archive.ubuntu.com/ubuntu/ wary universe
``` 
  
  **for hoary:**
   ```
deb http://archive.ubuntu.com/ubuntu/ hoary universe
 deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
 
```

---

### Post by search66 on 2005-02-18
Yea, I got that part... But doesn't the HTTP mean that it's trying to locate the set via the internet?  The workstation doesn't have a network connection yet.

I tried to add it via Synaptic, but it gave me about a half-dozen "warnings" because of an invalid path...

---

### Post by rwabel on 2005-02-19
[QUOTE=search66]Yea, I got that part... But doesn't the HTTP mean that it's trying to locate the set via the internet? The workstation doesn't have a network connection yet.
 
 I tried to add it via Synaptic, but it gave me about a half-dozen "warnings" because of an invalid path...[/QUOTE]
 
 Ah okay, I missunderstood you. You want to add a repository of universe which is not on the internet. I don't know how to do that. You must make kind of a mirror from the universe repository I guess.
 
 But the main repository you have also on CD. You'll have most important applications available without internet connection.

---

### Post by search66 on 2005-02-21
Ok, I'm back to square one.  Can anyone tell me how to add the universal repository without having an internet connection?  Is it on the CD?  If so, how can I install it?

---

### Post by Karny on 2005-02-25
[QUOTE=search66]Is it on the CD?  If so, how can I install it?[/QUOTE]

it isn't, so you can't.

---

