---
title: "How to get bash as default in terminal"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by raghulrajan on 2011-10-12
Hi
 I installed NCBI-blast in my ubuntu. To have a smooth working of this program, I added a environmental variable and a .bashrc file (saved at home folder) with the following content
 export PATH=/home/raghul/ncbi-blast-2.2.25+/bin

I also added contents to another .ncbirc file
  [BLAST]
BLASTDB=/home/raghul/ncbi-blast-2.2.25+/db

I restarted the system and typed the command pwd in the terminal and it showed the following
raghul@raghul-laptop:~$ whoami
Command 'whoami' is available in '/usr/bin/whoami'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
whoami: command not found

So I typed the command echo $PATH. It showed the following
raghul@raghul-laptop:~$ echo $PATH
/home/raghul/ncbi-blast-2.2.25+/bin

I am happy the BLAST Program is working but I also need bash shell to do other operations. Can any body suggest me to have both previous default PATH & also with the BLAST  env variable

I hope the above message is clear
I am Linux newbie & thats why I am confused!

Thank u
raghul

---

### Post by mikejonesey on 2011-10-12
usermod -s /bin/bash username

---

### Post by whitethorn on 2011-10-12
Take a look at this, by export PATH your overwriting the standard setting.

[http://askubuntu.com/questions/52611/i-think-i-accidently-deleted-the-path-variable](http://askubuntu.com/questions/52611/i-think-i-accidently-deleted-the-path-variable)

To get what you want it should look something like this

```

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/raghul/ncbi-blast-2.2.25+/bin

```

Then resource your bashrc.

```

source ~/.bashrc

```

---

### Post by mikejonesey on 2011-10-12
ps;
```
echo "export BLASTDB=/home/raghul/ncbi-blast-2.2.25+/db" > ~/.bashrc
```

---

### Post by raghulrajan on 2011-10-12
Hi
The following message appears when I typed as u said,

raghul@raghul-laptop:~$ usermod -s /bin/bash raghul
Command 'usermod' is available in '/usr/sbin/usermod'
The command could not be located because '/usr/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative priviledges associated with your user account.
usermod: command not found

Thank you
raghul

---

### Post by raghulrajan on 2011-10-12
Hi
I did the above step and it restored the bash shell. It is strange that the following earlier PATH variable reappeared -/home/raghul/ncbi-blast-2.2.23+/bin.How to remove this old variable & add the following new variable- /home/raghul/ncbi-blast-2.2.25+/bin ?

The following appeared after I executed the above instructions given.
raghul@raghul-laptop:~$ echo $PATH
/home/raghul/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/raghul/ncbi-blast-2.2.23+/bin

When I use ls command, all the contents are in white , is it possible to regain the coloring?
I am really sorry to ask such questions. I have bought a book  "Ubuntu-Up & running". The info given is minimal & for beginners.

thank you very much for your reply
raghul

---

### Post by whitethorn on 2011-10-13
I don't know how it looked like before. Here's a guide which shows you how to customize your bash. The important part starts with

```

PS1=...

```

You can make it look all sorts of cool. There's probably a way to get it back to normal. I'm not on my pc at the moment, check in /etc/skel/.bashrc look for the PS1= line.

[http://ubuntuforums.org/showthread.php?t=614743](http://ubuntuforums.org/showthread.php?t=614743)

---

