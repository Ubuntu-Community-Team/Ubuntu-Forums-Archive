---
title: "Unable to install virtualenvwrapper"
date: 2015-07-10
forum: New to Ubuntu
---

### Post by pgslmatias on 2015-07-10
Hi, I'm a newbie linux user and newbie programmer as well. I was trying to do the installation process at newcoder.io as described here [http://newcoder.io/begin/setup-your-machine/](http://newcoder.io/begin/setup-your-machine/). However, I'm having a lot of trouble with installing virtualenvwrapper. I have already sent an email 2 days ago to the contact information listed on the website, but so far I haven't received anything and I'm really eager to code the projects. In the beginning I didn't understand what I was supposed to do, but after reading the documentation on the website of virtualenvwrapper I found out that those things were a shell script, and so I copy pasted it and ran it. It doesn't work, here is the terminal output:
```
The directory '/home/pedro/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/pedro/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Requirement already satisfied (use --upgrade to upgrade): virtualenvwrapper in /usr/local/lib/python2.7/dist-packages
Requirement already satisfied (use --upgrade to upgrade): virtualenv in /usr/local/lib/python2.7/dist-packages (from virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): virtualenv-clone in /usr/local/lib/python2.7/dist-packages (from virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): stevedore in /usr/local/lib/python2.7/dist-packages (from virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): argparse in /usr/lib/python2.7 (from stevedore->virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): six>=1.9.0 in /usr/local/lib/python2.7/dist-packages (from stevedore->virtualenvwrapper)
Requirement already satisfied (use --upgrade to upgrade): pbr<2.0,>=0.11 in /usr/local/lib/python2.7/dist-packages (from stevedore->virtualenvwrapper)
install.sh: 6: install.sh: source: not found
```
What can I do? I'm on xubuntu. Sorry for bad english and thanks for reading this.

---

### Post by Vladlenin5000 on 2015-07-10
What exactly have you copy pasted? It would be helpful to post the entire results of the terminal, including the commands used, not just the subsequent messages.
Use code tags to wrap that text -> Go Advanced, click # and paste inside. Thank you.

---

### Post by pgslmatias on 2015-07-10
Hey, thanks for replying. The command I ran there was just sh install.sh. There are multiple versions of the install.sh file, but they all do pretty much the same. I'm going to paste here the email I sent to the guy/gal behind newcoder.io, because it describes what I did really well. Here it goes (with the courtesies removed): 
"I already have pip, python 2.7.6, GCC and virtualenv installed  and setup. My problem is with virtualenvwrapper. I think what you posted  there is a shell script. So, I copy pasted the Debian/Ubuntu code into  gedit, removed the $ after trying it with them and ran the code.  However, I received an error. So, I googled and read the code, and  checked my file manager. Apparently, it didn't save any document called  virtualenvwrapper to the directory */etc/bash_completion.d/. So, I  started digging up a bit more. I went directly to the source here:  [http://virtualenvwrapper.readthedocs.org/en/latest/](http://virtualenvwrapper.readthedocs.org/en/latest/), because installing  pip had also failed using your method and so I installed pip via the pip  website, so I thought I could install virtualenvwrapper via the  virtualenvwrapper website. I noticed that the directory they listed in  this website was the same you listed in the bash script for fedora, so I  checked there and it was there! So, I copy pasted the code for fedora  and tried running it. Again, I had an error, this time a different one.  Here's the error: "install.sh: 6: install.sh: source: not found" So, I  tried a few more things, like typing out each line in the shell script  in the terminal and running it like it was a command, copying the shell  script from the website and running it, and again running each line of  the shell script in the website as a separate command. None of this  yielded fruit. So, I went back to the script you wrote for ubuntu. I  decided that maybe it had something to do with the virtualenvwrapper.sh  having to be in the directory [I]/etc/bash_completion.d/, so I learned how  to move a file from the terminal using cp as root, because for some  reason it didn't allow me to copy paste the file. I ran and got an error  again. Then, I noticed that in your script for ubuntu, the file doesn't  have the .sh ending, being just called virtualenvwrapper. I learned  another new command (mv) because it didn't allow me to rename it using  GUI, and ran the script again. It failed. I tried all of this again with  a file called virtualenvwrapper_lazy.sh that was there. It failed as  well. While it has been fun, and I learned lots of new commands, I  really want this to work so I can write some python.  The error I get  now, with all the directories and file names correct in 4 different  places (the 2 directories, one listed in the ubuntu script, the other in  the fedora script, and with virtualenvwrapper and  virtualenvwrapper_lazy) is the same I got back then: install.sh: 6:  install.sh: source: not found. This is the script (  [http://pastebin.com/deRkRFtB](http://pastebin.com/deRkRFtB) ), this is the full terminal output (  [http://pastebin.com/r8VQMj8V](http://pastebin.com/r8VQMj8V) ) and this is a print screen that shows  that there is a file called virtualenvwrapper.sh in the directory of the  script ( [http://i.imgur.com/vVFdfK2.png](http://i.imgur.com/vVFdfK2.png) )." *[/I]I copy pasted the code he/she has there in the website. ```
$ sudo pip install virtualenvwrapper
$ export WORKON_HOME=~/Envs
$ echo 'export WORKON_HOME=~/Envs' >> ~/.bash_profile
$ echo 'source /etc/bash_completion.d/virtualenvwrapper' >> ~/.bash_profile
$ mkdir -p $WORKON_HOME
$ source ~/.bash_profile
``` that is the ubuntu version, this was the fedora version:
```
$ sudo pip install virtualenvwrapper
$ export WORKON_HOME=~/Envs
$ echo 'export WORKON_HOME=~/Envs' >> ~/.bash_profile
$ echo 'source /usr/local/bin/virtualenvwrapper.sh' >> ~/.bash_profile
$ mkdir -p $WORKON_HOME
$ source ~/.bash_profile
```
Also, I am the one who needs to thank you.

---

### Post by sandyd on 2015-07-10
It doesn't look like you're in bash (unless you removed the content before the $), and in sh instead.

Run
```

bash
```
before running anything.

However, the default terminal shouldn't be opening like that.
Can you post the output of
```

cat /etc/passwd | grep *yourusername*

```

---

### Post by pgslmatias on 2015-07-11
Hey, thanks for replying!!! Does this help?```
pedro@pedro-Inspiron-3521:~$ cat /etc/passwd | grep pedro
pedro:x:1000:1000:pedro,,,:/home/pedro:/bin/bash
pedro@pedro-Inspiron-3521:~$ sh
$ bash
pedro@pedro-Inspiron-3521:~$ 


```
Yes, I had deleted pedro@pedro-Inspiron-3521:~ from the terminal output.

---

### Post by pgslmatias on 2015-07-12
Sorrry everyone who was bothered by this. I had forgotten to close my terminal and open a new one, to let the changes kick in. It's all good now.

---

