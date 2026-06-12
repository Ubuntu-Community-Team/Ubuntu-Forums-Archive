---
title: "I can't install Steam."
date: 2013-02-16
forum: New to Ubuntu
---

### Post by Raolu on 2013-02-16
Hello, I'm new to Ubuntu and I got a question.

As the title says, I can't seem to install Steam. When I run the installer I get the following message:
[SIZE=2]
[/SIZE]
> [SIZE=2]De[SIZE=2]pendency is not satisfiable[SIZE=2]: libc6 (>[SIZE=2]=2.15[SIZE=2])[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][SIZE=2]

Can someone tell me what this me[SIZE=2]ans?[/SIZE][/SIZE]

---

### Post by GameX2 on 2013-02-16
You've tried installing it from the Software Center ?

---

### Post by CharlesA on 2013-02-16
How are you installing it?

You could always install via gdebi:

```
sudo apt-get install gdebi
```

```
sudo gdebi /path/to/steam.deb
```

[https://wiki.ubuntu.com/Valve](https://wiki.ubuntu.com/Valve)

---

### Post by swarfega on 2013-02-16
What about installing ia32-libs? Also after trying sudo dpkg -i steam_latest.deb which produces those errors, try sudo apt-get install -f which should install any dependences and steam itself.

---

### Post by Bölvaður on 2013-02-16
2Guys above me: Please write so a beginner would clearly understand what to do. This is not it. You actually need to tell the person you need to open up Terminal and put your cryptic commands in there.


Raolu: How did you attempt to install it?
I recommend opening the Software Centre (that shopping bag on the left panel) and "buy" steam (for free). That should automatically sort all problems out.


If that fails then you should start looking at the posts above me and copy and pasting those commands. Please feel free to ask anything related to this in this thread, any new problems should go in a new thread dedicated to that new problem.

---

### Post by Raolu on 2013-02-17
Installing it from the Software Center works! Thanks for the help.

---

