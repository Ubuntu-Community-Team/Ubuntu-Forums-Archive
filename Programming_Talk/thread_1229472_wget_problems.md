---
title: "wget problems"
date: 2009-08-02
forum: Programming Talk
---

### Post by Tek-E on 2009-08-02
Wow its been a while since I posted something.
okay.  So lately I have been working on some programming missions at 
HTS (hackthissite.org)  And I need to retrieve some words from one of the pages for my programming solution.  So I though I would write a shell script to help me out.   

I have tried using the wget utility to get the source of the page I wish to view but have had no such luck and was wondering if anybody could help me fix this issue.

I have tried the following.
```

wget -E --http-user=USER --http-password=PASS http://www.hackthissite.org/missions/prog/1/

```
**NOTE I have substituted USER and PASS with my actual username and password in my attempts
**

I have also tried loading cookie information that I took while I was logged in viewing the page using

```

javascript:alert(document.cookie)

```
I then saved the cookie information to my computer and tried sending the information via wget trying

```

wget -E --load-cookies=cookiedata --user=USER --password=PASS http://www.hackthissite.org/missions/prog/1/

```

Anybody have an Idea as to what I am doing wrong??
Any help would be greatly appreciated.

Thank you.

---

### Post by benj1 on 2009-08-02
whats the actual problem? is it not logging in?

---

### Post by dwhitney67 on 2009-08-02
The funny thing is that the OP requires a Username/Password to perform his first hacking exercise.

If all that is needed is for one to pick words out of a web page, then start with a simple page, such as Google's home page, or even Ubuntu Forum's home page.

---

### Post by Tek-E on 2009-08-02
> **dwhitney67 said:**
> The funny thing is that the OP requires a Username/Password to perform his first hacking exercise.

If all that is needed is for one to pick words out of a web page, then start with a simple page, such as Google's home page, or even Ubuntu Forum's home page.

correct you are.  my first "hacking" exercise?? if thats what you want to call it does infact require a password. and that username and password is mine. Obviously im not going to post it here online.:confused:

The objective is to take ten scrambled words off of the webpage and unscramble them in 30 seconds using a program I wrote.  I need a way of getting those words other than copying and pasting. 

Im not trying to "hack" anything. I need to be logged in under my account to get the source of the page which contains the 10 words.  But using wget sending that information has not worked for me.

---

### Post by Tek-E on 2009-08-02
> **benj1 said:**
> whats the actual problem? is it not logging in?

yeah I cant get it to log in for me.

---

