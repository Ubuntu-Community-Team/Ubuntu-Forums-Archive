---
title: "^@ / Null character spam"
date: 2018-02-23
forum: New to Ubuntu
---

### Post by deagahelio on 2018-02-23
I switched to Ubuntu a couple weeks ago, everything is going fine so far but I've ran into a problem and I'm not sure how to solve it.
The problem is, Ubuntu thinks I'm typing a null character every second or so.

I use a Brazilian Portuguese keyboard which has dead keys and it's pretty annoying when I'm trying to type a backtick and end up with Ç, or when I try to type ã but end up with &#8182;.
When I try to login in the virtual terminal it keeps spamming ^@ so it doesn't let me type anything properly.
And while playing a SDL game it keeps complaining on the terminal about not recognizing the null character.

What I found on the internet were these two SE questions:

[https://stackoverflow.com/questions/41905525/null-input-character-spamming-linux-tty](https://stackoverflow.com/questions/41905525/null-input-character-spamming-linux-tty)
[https://unix.stackexchange.com/questions/396192/spam-in-tty-but-seems-to-be-system-wide](https://unix.stackexchange.com/questions/396192/spam-in-tty-but-seems-to-be-system-wide)

But none of the solutions worked for me.

So, is there a way to disable this? Or is it a normal thing? Am I missing something obvious?

---

### Post by ubname on 2018-02-24
In settings input sources i'd try to configure the keyboard with portoghese (brasil without dead keys) hope it may help :(

---

### Post by deagahelio on 2018-02-24
I wanna still be able to use the dead keys though. It also doesn't stop the null character spam

---

### Post by deagahelio on 2018-02-27
Nevermind, blacklisting input_polldev actually seems to work, I was probably doing it wrong the first time.
Anyways, if anyone has the same problem in the future just add this to the /etc/modprobe.d/input_polldev.conf file:
```

blacklist input_polldev
install input_polldev /bin/false

```

---

