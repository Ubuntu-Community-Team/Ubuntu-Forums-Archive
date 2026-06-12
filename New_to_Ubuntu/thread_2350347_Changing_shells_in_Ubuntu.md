---
title: "Changing shells in Ubuntu"
date: 2017-01-23
forum: New to Ubuntu
---

### Post by heatopher2 on 2017-01-23
Hi, I'm a bit confused about this....

Maybe half a decade ago I spent a little time working with shell-scripting, but it's been a while since I did any of this heavy stuff, and I seem to be a bit rusty. What I do remember is that I liked using the zsh shell, and have even found a backup of my old .zshrc file. 

So, I've just come back to Linux from a few years on Windows, and one of the first things that I am wanting to do is to have zsh as my default shell. I've been trying to set that up today, but it's been a bit weird.

I followed these instructions here:

[https://www.thinkingmedia.ca/2014/10/how-to-install-oh-my-zsh-on-ubuntu-14/](https://www.thinkingmedia.ca/2014/10/how-to-install-oh-my-zsh-on-ubuntu-14/)

and here:

[https://gist.github.com/tsabat/1498393](https://gist.github.com/tsabat/1498393)

... and that seemed to have worked, as I had zsh 

...but I have just rebooted and I still have bash. The weird part is that when I do (as in those instructions):

cat /etc/passwd | grep $(whoami)

I'm supposed to have zsh as my shell.

However, when I do chsh, I'm getting this:

kizza@heatopher:~$ chsh
You may not change the shell for 'kizza'.

kizza@heatopher:~$ chsh -s which zsh
chsh: user 'zsh' does not exist

kizza@heatopher:~$ chsh -s `which zsh`
You may not change the shell for 'kizza'.
kizza@heatopher:~$ whoami
kizza

OK, so maybe I need to do sudo......

kizza@heatopher:~$ sudo chsh
[sudo] password for kizza: 
Password: 
chsh: PAM: Authentication failure


Well, I haven't changed or forgotten my password. So what is going on there??? Obviously  I'm going a bit by trial and error, without fundamental knowledge of this stuff, so I am well confused! :confused:

---

### Post by heatopher2 on 2017-01-23
One more thing. I just tried following these instructions: 

**Install Errors**

 If you saw an error massage like one of the following chsh: option requires an argument or Password: chsh: PAM: Authentication failure then the script is having trouble setting ZSH as the default shell.

 You can resolve this problem by running the install script manually.

 rm -fr .oh-my-zsh/
curl -L [http://install.ohmyz.sh](http://install.ohmyz.sh) > install.sh
sh install.sh[INDENT]On some Linux platforms you have to run bash install.sh instead of sh install.sh.



 [/INDENT]
and I'm getting this:

[INDENT]kizza@heatopher:~$ bash install.sh
Cloning Oh My Zsh...
Cloning into '/home/kizza/.oh-my-zsh'...
remote: Counting objects: 829, done.
remote: Compressing objects: 100% (699/699), done.
remote: Total 829 (delta 14), reused 731 (delta 9), pack-reused 0
Receiving objects: 100% (829/829), 565.03 KiB | 0 bytes/s, done.
Resolving deltas: 100% (14/14), done.
Checking connectivity... done.
Looking for an existing zsh config...
Found ~/.zshrc. Backing up to ~/.zshrc.pre-oh-my-zsh
Using the Oh My Zsh template file and adding it to ~/.zshrc
Time to change your default shell to zsh!
You may not change the shell for 'kizza'.
[/INDENT]

I may not change my own shell?!?!?!? Weird!

---

### Post by kevdog on 2017-01-24
I think you can change your login shell -- if you've installed the shell -- within /etc/passwd.  You'll have to login back in and out.

---

### Post by steeldriver on 2017-01-24
Just wanted to point out you don't need oh-my-zsh to install and use zsh - you should be able to just install the zsh package from the repository

As to you chsh issues, may we see the output of

```

ls -l $(which chsh)

ls -l /etc/{passwd,shadow}

sudo pwck -qr

```

---

### Post by heatopher2 on 2017-01-24
If, as I suspect, you're referring to this line from that file:

kizza:x:1000:1000:Kizza,,,:/home/kizza:zsh

.... well, I already did that, and mentioned it above, but no good

Sorry, with reference to the slightly more helpful second post, which I didn't notice at first :~)

```
kizza@heatopher:/etc$ ls -l $(which chsh)
-rwsr-xr-x 1 root root 40432 Mar 29  2016 /usr/bin/chsh
kizza@heatopher:/etc$ ls -l /etc/{passwd,shadow}
-rw-r--r-- 1 root root   2274 Jan 23 23:19 /etc/passwd
-rw-r----- 1 root shadow 1274 Jan 22 04:36 /etc/shadow
kizza@heatopher:/etc$ sudo pwck -qr
[sudo] password for kizza:
```

The thing is that noobs like me just flail around a lot with this stuff, reading different and sometimes seemingly inconsistent information, and when it doesn't work we probably all feel like we're doing damage somewhere, or causing the system to bloat with unnecessary junk. Well, I suppose it's the same with learning anything, right?

Oh wait.... This is how you change shell?

```
kizza@heatopher:/etc$ zsh
&#10140;  /etc echo $SHELL
zsh


```

Sorry, like I said, I'm rusty with this stuff.... (But why do some places say to do chsh???)

So, OK, that works and I've got my changes in .zshrc. But that still doesn't sort out the default startup shell issue.

---

### Post by steeldriver on 2017-01-24
Hmm... well those all look in order to me - I don't know why chsh is not working for you.

[It will also fail if zsh has not been added to the /etc/shells file - but the error in that case should be different i.e. "xxx is an invalid shell"]

---

### Post by SeijiSensei on 2017-01-24
Change the entry in /etc/passwd to read /bin/zsh (assuming that's where it is).  Always use full paths.

---

### Post by heatopher2 on 2017-01-24
> **SeijiSensei said:**
> Change the entry in /etc/passwd to read /bin/zsh (assuming that's where it is).  Always use full paths.

Thank you! That was the one!

---

### Post by SeijiSensei on 2017-01-24
Glad I could help.  Please go to the Thread Tools link at the top of the page to mark this thread [SOLVED].

---

