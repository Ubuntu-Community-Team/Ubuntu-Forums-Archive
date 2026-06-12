---
title: "Standardize Ubuntu Installation Environment"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by Emiliano_Jordan on 2014-02-25
Hi,

I'm really new to Ubuntu and any Linux OS platform.  As I'm getting things set up on my "toy" computer I'm realizing I'd like to standardize the instillation of my work environment to all my computers once I'm happy.  What's the best way to do this? I'm thinking a .sh file but have no experience writing one.  Basically I'd like to have a simple file or small app I can run the will install all my programs and libraries using the commands I would normally type into my terminal.

Just for more details, I'd like it to set up my dev environment (LAMP stack, PHPStorm, Ruby, etc) on a clean version of Ubunut 12.,04 LTS.

If anyone has any links to tutorials or documentation that'd be huge help. Google has turned up a scarse ammount of info. 

Thanks!

---

### Post by grahammechanical on 2014-02-25
Here is an example:

```
sudo apt-get update && sudo apt-get upgrade
```

Those two commands will run one after the other. Create a txt file. Write in it a similar string of commands according to your choice. Then simply copy and paste the commands from the text file into the terminal.

You want a utility? It is called Ubuntu Software Centre. It will stack application installs and download and install them one after the other.

Regards.

---

### Post by newb85 on 2014-02-25
If you can find a way to do all your customization via terminal commands, putting together a script that will do it all is easy.

Here's another suggestion:  Ubuntu Software Center has a Sync Between Computers feature (that uses the Ubuntu One cloud service for package tracking).  Meanwhile, you could also use Ubuntu One to sync configuration files between machines.  (I haven't personally tested this method fully.  Truthfully, I've never wanted to exactly duplicate systems between machines because I generally want my better machines to do things my weaker machines are not practically capable of.)

---

### Post by Emiliano_Jordan on 2014-03-17
Thanks for the replies.  I can all of what I want done accomplished in Terminal so I'll look more into putting together a script.

---

