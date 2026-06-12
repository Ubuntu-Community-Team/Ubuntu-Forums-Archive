---
title: "Where is Grive?"
date: 2014-04-01
forum: New to Ubuntu
---

### Post by 171742 on 2014-04-01
Hi,

I just installed grive via terminal, but cant find it in my programms? Id loke to work with it visually, only terminal is a bit spooky. But it works. 

Thanks!

---

### Post by monkeybrain20122 on 2014-04-01
grive is command line only. Just type grive in the terminal. If you want a gui apparently you have to install something call grive-tools. 
[http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)

---

### Post by gifford on 2014-04-01
I agree with using grive-tools. It works wonderfully, makes gdrive readily available and does the work Google has not done for Linux.

---

### Post by 171742 on 2014-04-02
Hey,

it does not work and does this:

o@o-A6Rp:~$ 2~sudo apt-get install grive-tools
2~sudo: command not found
o@o-A6Rp:~$ sudo apt-get install grive-tools
[sudo] password for o: 
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut       
Statusinformationen werden eingelesen... Fertig
E: Paket grive-tools kann nicht gefunden werden
o@o-A6Rp:~$ sudo add-apt-repository 
Error: need a repository as argument
o@o-A6Rp:~$ sudo add-apt-repository 
Error: need a repository as argument
o@o-A6Rp:~$ sudo add-apt-repository
Error: need a repository as argument
o@o-A6Rp:~$ BBCBAA

what to do?

---

### Post by su:bhatta on 2014-04-02
> **171742 said:**
> ...
o@o-A6Rp:~$ sudo add-apt-repository
Error: need a repository as argument
o@o-A6Rp:~$ BBCBAA

what to do?

You have to give the repository name otherwise it does not know what to do. In the link provided by monkeybrain :[http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools](http://www.thefanclub.co.za/how-to/ubuntu-google-drive-client-grive-and-grive-tools)
you will see that this is given :

```
sudo add-apt-repository ppa:thefanclub/grive-tools 
sudo apt-get update 
sudo apt-get install grive-tools
```

Please put the output of the Terminal in the Code Tags, given as # in the reply tools.

P.S.: monkeybrain, thanks for that link, I had no clue about Grive/grive-tools. Works neatly.

---

