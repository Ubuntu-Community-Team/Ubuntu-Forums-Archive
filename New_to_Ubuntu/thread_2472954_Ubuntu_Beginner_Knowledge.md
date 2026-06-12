---
title: "Ubuntu Beginner Knowledge"
date: 2022-03-18
forum: New to Ubuntu
---

### Post by unincomplete1607bio on 2022-03-18
What are the main codes needed for a beginner to run Ubuntu terminal and other function properly ?
I am talking about those function such as, 'sudo apt-get update' for running updates.
I just wanted to learn other functions like this.  

[ATTACH=CONFIG]290161[/ATTACH]

I have only learnt this code till now..........
So I want to learn more codes.

---

### Post by ActionParsnip on 2022-03-18
What do you want to do? If you see this as "how do I do x" rather than "What are all the things I can do" then you'll be less frustrated.

Running the command "sudo apt update" doesn't install updates. It only reads the available updates. If you want to install them then run:
```

sudo apt -y upgrade

```

---

### Post by QIII on 2022-03-18
They are not "codes".  That is a gaming term.

For simple commands, they are not programming.  You don't need to be a programmer.  But things can get somewhat complex and require more knowledge. 

They are called "commands".  You are talking to your machine -- either issuing it instructions to do something specific or asking it to tell you something about itself.

[This]("https://ubuntu.com/tutorials/command-line-for-beginners#1-overview") might be a good place for you to start.  Note that at the end is a link to a downloadable pdf that is something like 600 pages long and covers everything in exhaustive detail.  You probably won't need 95% of that for general use.

---

### Post by Impavidus on 2022-03-18
Using the terminal isn't about memorising commands. There's a lot of structure in those commands and they can be combined in many ways. Even the commands that appear to do something very useless (tac, yes) may be great when combined with others. To use the terminal effectively, you have to learn that structure. The commands themselves are not so interesting. QIII gave a nice link for an introduction.

---

### Post by coley9225 on 2022-03-19
Welcome to linux. A long time ago,couple years or more, I ran across a great book for beginners. It's free to download, as a pdf. It explains a ton of thing you can do in your terminal, different commands and what they do, and exercises you can do to learn those commands better. You can find it here [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php). I couudn't remember where I found it, but recently found the link again. Get it, read it ,reread if you need to. It's a great deal of info. Best of luck.

---

### Post by TheFu on 2022-03-19
> **Impavidus said:**
> Using the terminal isn't about memorising commands. There's a lot of structure in those commands and they can be combined in many ways. Even the commands that appear to do something very useless (tac, yes) may be great when combined with others. To use the terminal effectively, you have to learn that structure. The commands themselves are not so interesting. QIII gave a nice link for an introduction.

tac is awesome - much more useful than cat.  99% of the time cat is typed, it isn't needed.

There are hundreds of commands on any Unix system. There is a method for each - they aren't random.  There is a manual for each command on your system too. Learning to read the "manpage" will help to understand the purpose, options, inputs and outputs from each command.
While many of the commands (really they are just programs) are very similar across all Unix-like OSes, there are slight differences, since every release will have a slightly different version of the same command - either with fixes or new options.  The manpage on your system is matched to the exact version of the command on your system.  My system will have a different version, unless we are running the same command version.

Memorizing commands isn't really too useful.  Commands will naturally be stuck in your head based on how often each is used. Same for the options.  I seldom use just the command. I almost always have 2-5 options for each based on prior knowledge.

You can search for any "Unix cheat sheet" or "Linux cheat sheet" or "Ubuntu cheat sheet", if that helps you to learn.
A good book, free to download, no hassles to get is here: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) .  This is the book I used with my beginning Linux classes. We did provide a 5 page "cheat sheet" of commands at the insistence of a faculty sponsor. I was against it.  Someone else's notes are never as good as your own notes.

If you want to actually learn Linux shells, then learn Linux shells.  Have a plan. I'd say to read and do the exercises in that book like 1 chapter per week. In 10 weeks, you'll know much more than most people here AND you would have learned concepts so that new commands fit into memory slots that your brain already has for the base knowledge already there.  Without that base knowledge, you'll just be memorizing stuff and not building the connections that lead to a deeper understanding.

If you want to become a programmer or systems admin, then the deeper understanding really is required learning.

OTOH, if you just want to point-n-click, you can be that type of user too and be happy.

---

### Post by mIk3_08 on 2022-03-20
> **unincomplete1607bio said:**
> What are the main codes needed for a beginner to run Ubuntu terminal and other function properly ?
I am talking about those function such as, 'sudo apt-get update' for running updates.
I just wanted to learn other functions like this.  
I have only learnt this code till now..........
So I want to learn more codes.
[Click here]("https://linuxcommand.org/tlcl.php") for more Linux command. Good Luck and Cheers

---

### Post by oldos2er on 2022-03-20
[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)

---

