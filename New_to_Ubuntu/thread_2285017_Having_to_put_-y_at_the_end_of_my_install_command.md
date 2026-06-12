---
title: "Having to put -y at the end of my install command"
date: 2015-07-02
forum: New to Ubuntu
---

### Post by jeff131 on 2015-07-02
Just out of pure curiosity, I ask this question, and here's the story. I was installing Steam through the command line, as I found a video on how to do that. The link is [here]("http://www.youtube.com/watch?v=PXB89F4xoQM"). I was wondering, to deepen my understanding of the Linux command line, why do you have to put a -y at the end of the command? The command I use was, "sudo apt-get install steam -y"


There is no urgency to answer this as this is just out of pure curiosity, but a big thanks to anybody who answers this


EDIT- I couldn't use code tags because on the original post I forgot to add it, and I had to edit it, and I didn't see a code tag

---

### Post by howefield on 2015-07-02
It means to accept all prompts.

```
man apt-get
```

will give you the help page for the apt-get command.

>  -y, --yes, --assume-yes
Automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively. If an undesirable situation, such           as changing a held package, trying to install a unauthenticated package or removing an essential package occurs then apt-get
will abort. Configuration Item: APT::Get::Assume-Yes.

---

### Post by jeff131 on 2015-07-02
Thank you for answering my question!

---

### Post by vasa1 on 2015-07-03
> **jeff131 said:**
> Just out of pure curiosity, ... why do you have to put a -y at the end of the command? The command I use was, "sudo apt-get install steam -y"
...
I avoid using "-y". I think installing software interactively is more informative (and possibly safer).

Also, you maybe interested in "-s" which simulates what may happen if you issue the install command. You may like to go through [https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto). Lots of good stuff there.

> **jeff131 said:**
> ...
EDIT- I couldn't use code tags because on the original post I forgot to add it, and I had to edit it, and I didn't see a code tag
When you edit your post, you may see fewer options than when you start a new post or click on "reply" or "quote". To see all the options, look for the "go advanced" button. Clicking that should show you everything.

---

