---
title: "I am new to this os kindly help me !"
date: 2018-05-21
forum: New to Ubuntu
---

### Post by riteshpandey7 on 2018-05-21
i was installing neo4j to my laptop and have done this ,,
step 1 -  opend this site [https://neo4j.com/docs/operations-manual/current/installation/linux/debian/](https://neo4j.com/docs/operations-manual/current/installation/linux/debian/)    
and copied this and pasted on terminal  
[LIST]
[*][COLOR=#3300AA]echo[/COLOR] [COLOR=#AA1111]"deb [http://httpredir.debian.org/debian](http://httpredir.debian.org/debian) jessie-backports main"[/COLOR] | [COLOR=#3300AA]sudo[/COLOR] [COLOR=#3300AA]tee[/COLOR] [COLOR=#0000CC]-a[/COLOR] /etc/apt/sources.list.d/jessie-backports.list
[COLOR=#3300AA]sudo[/COLOR] apt-get update
[*] after this when i enter sudo apt-get update it says
[*]E: Malformed line 2 in source list /etc/apt/sources.list.d/jessie-backports.list (type)E: The list of sources could not be read.

how to fix this pplease tel me easy way since m new
[/LIST]

---

### Post by deadflowr on 2018-05-21
What operating system?

---

### Post by riteshpandey7 on 2018-05-21
ubuntu 18.04 LTS

---

### Post by coffeecat on 2018-05-21
Let's look at the file which has the malformed line. Open a terminal and run this command:

```
cat /etc/apt/sources.list.d/jessie-backports.list 
```

Post the output. You can do this by highlighting the output with the mouse, right-click -> copy and then paste into your post with right-click -> paste, or ctrl-v. Please enclose the output between BBCode code tags. There's a link in my sig if you don't know how to apply code tags.

---

### Post by riteshpandey7 on 2018-05-21
echo "deb [http://httpredir.debian.org/debian](http://httpredir.debian.org/debian) jessie-backports main"












sudo tee -a /etc/apt/sources.list.d/jessie-backports.list










sudo apt-get update






udo apt-get -t jessie-backports install ca-certificates-java

---

### Post by coffeecat on 2018-05-21
> **riteshpandey7 said:**
> echo "deb [http://httpredir.debian.org/debian](http://httpredir.debian.org/debian) jessie-backports main"












sudo tee -a /etc/apt/sources.list.d/jessie-backports.list










sudo apt-get update






udo apt-get -t jessie-backports install ca-certificates-java

Please re-read my post and run the command I suggest.

---

### Post by riteshpandey7 on 2018-05-21
when i copy and paste it in the terminal it shows the same thing i have replied

---

### Post by kerry_s on 2018-05-21
> Prerequisites (Ubuntu 14.04 and Debian 8 only) 

18.04, not even close.

---

### Post by coffeecat on 2018-05-21
> **riteshpandey7 said:**
> when i copy and paste it in the terminal it shows the same thing i have replied

Will you **please** simply post the output from the command I suggested.

Are you saying the output from the command contains all those echo, sudo tee and sudo apt-get lines?

---

### Post by riteshpandey7 on 2018-05-21
yes

---

### Post by coffeecat on 2018-05-21
> **riteshpandey7 said:**
> yes

Really?

Are you truly, absolutely saying that the output of the command:

```
cat /etc/apt/sources.list.d/jessie-backports.list
```

... is ...

```
echo "deb http://httpredir.debian.org/debian jessie-backports main"












sudo tee -a /etc/apt/sources.list.d/jessie-backports.list










sudo apt-get update






udo apt-get -t jessie-backports install ca-certificates-java
```

?

If so, you did not follow the instructions in the link you provided in the first post correctly. And if so, you have managed to get a lot of extraneous material into your /etc/apt/sources.list.d/jessie-backports.list.

And, frankly, I do not believe that is really the output of the cat command. Let me explain.

You provided a link to a tutorial that you followed. Part of the tutorial contains a terminal command that creates a file called /etc/apt/sources.list.d/jessie-backports.list. This file contains information needed by the package manager in order to install neo4j. The malformed line message that you posted in your first post is telling you that the file is not readable by the package manager. The cat command I asked you to run simply prints out the contents of the /etc/apt/sources.list.d/jessie-backports.list file so that we can examine it and advise on what needs to be done. Notwithstanding the steps you said you took, it is more important to see what the end result is. As I said, I find it difficult to believe that the contents of your post #5 really is the contents of the file.

So that we can be absolutely sure of the contents of /etc/apt/sources.list.d/jessie-backports.list , please run the cat command I suggested in post #4 and include  everything that you see in the terminal in your post. We must be sure that we are seeing the correct information.

---

### Post by oldfred on 2018-05-21
Just checked in 18.04 using synaptic and it has this, plus other related files:neo4j-client

neo4j-client supports secure connections to Neo4j server, sending of
statements (including multiline statements), persistent command history, and
rendering of results to tables or CSV.

---

