---
title: "Thunderbird no longer supports links"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by merkigil on 2012-07-26
Ubunto 10.04/Thunderbird no longer supports links. I have re-installed Thunderbird bu that did not solve the problem.

---

### Post by androssofer on 2012-07-26
> **merkigil said:**
> Ubunto 10.04/Thunderbird no longer supports links. I have re-installed Thunderbird bu that did not solve the problem.

what happens when you click them? 

have links that once worked now stopped?

---

### Post by Bufeu on 2012-07-26
What links? mailto-links or links within the emails?

---

### Post by merkigil on 2012-07-27
> **Bufeu said:**
> What links? mailto-links or links within the emails?
Links within the emails.

---

### Post by merkigil on 2012-07-27
> **androssofer said:**
> what happens when you click them? 

have links that once worked now stopped?
 
A window opens at the bottom of the screen with the sender's URL which disappears when I move the cursor over the window.

Previously, accessing links in emails worked as it should.

---

### Post by Bufeu on 2012-07-27
> **merkigil said:**
> A window opens at the bottom of the screen with the sender's URL which disappears when I move the cursor over the window.

Previously, accessing links in emails worked as it should.Maybe there's no default program for HTTP/HTTPS-link? [http://www.libre-software.net/change-the-default-application-ubuntu-linux](http://www.libre-software.net/change-the-default-application-ubuntu-linux)

---

### Post by hypnot0ad on 2012-07-27
I have 10.04.04 on another laptop and it works.
What machine are you running this on?

---

### Post by merkigil on 2012-07-29
> **Bufeu said:**
> Maybe there's no default program for HTTP/HTTPS-link? [http://www.libre-software.net/change-the-default-application-ubuntu-linux](http://www.libre-software.net/change-the-default-application-ubuntu-linux)

Thanks, your default clue solved my problem!
 
 1. For 10.04 in the System menu, open Preferences, then Preferred Applications.
2. On the Internet tab under **Web Browser**, choose **Firefox** in the drop-down.
     [The previous setting was **custom**. I don't know why.]
3. Press Close.

---

