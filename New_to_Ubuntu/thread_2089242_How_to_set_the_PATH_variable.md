---
title: "How to set the PATH variable?"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by littlewenwen on 2012-11-28
Dear All,

I installed a program(vpnui) which is in the directory
> /opt/cisco/vpn/binEach time when I try to run the program I have to navigate to that directory and issue the command, like following

```
littlewenwen@newuser1:/opt/cisco/vpn/bin$ ./vpnui
```So that I can excute the command everywhere, I edited the file  > ~/.profile, making following change in the file:

> PATH="$HOME/bin:$PATH"changed to

> PATH="$HOME/bin:$PATH:/opt/cisco/vpn/bin"After making this change, I went to my home directory and issued following command:

```
littlewenwen@newuser1:~$ ./vpnui
```And I got the following message:

> bash: ./vpnui: No such file or directoryWhat did I do wrong? How to set the PATH variable?

---

### Post by littlewenwen on 2012-11-28
Maybe I write too long..

My question is: how to set PATH variable so that I can run a program without quoting its absolute path?

---

### Post by papibe on 2012-11-28
Hi littlewenwen.

The line on .profile only gets executed when you login, and only if you have a ~/bin in your home directory.

I'd recommend making the changes at the end of your ~/.bashrc

After that, every new terminal with work with the new path. If you want to be valid for your whole session, logout and login again.

Let us know how it goes.
Regards.

---

### Post by MG&amp;TL on 2012-11-28
Also, once you've done what papibe suggests, you should omit the "./" - that tells bash it is to look in the current directory, not in $PATH.

---

### Post by littlewenwen on 2012-11-28
Thanks; but how to edit the ~/.bashrc? Here is the last part of my ~/.bashrc file and I did not see any word related to PATH:

```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
```

---

### Post by gnusci on 2012-11-28
$PATH should be always first,

export PATH=$PATH:$HOME/bin:/opt/cisco/vpn/bin

---

### Post by littlewenwen on 2012-11-28
Do you suggest add this line > export PATH=$PATH:$HOME/bin:/opt/cisco/vpn/bin to bashrc file?

---

### Post by MG&amp;TL on 2012-11-28
Yes, just add this line:

```
export PATH=$PATH:/opt/cisco/vpn/bin 			 		
```

to the end of ~/.bashrc. :)

---

### Post by littlewenwen on 2012-11-28
Thank you very much. It worked!

---

### Post by littlewenwen on 2012-11-28
By the way, i searched online: it seems tha there are many ways to set PATH (profile, bashrc, enviroment, ...), can anyone elaborate what is the difference among those methods?

---

### Post by papibe on 2012-11-28
Basically:
```

/etc/environment is for system wide
~/.bashrc        is personal and related to bash instances. e.g., for every terminal and script.
~/.profile       is personal but related to a login session.
```

As examples, take a look at [this]("http://ubuntuforums.org/showthread.php?t=1984328") and [this]("http://ubuntuforums.org/showthread.php?t=1974991&highlight=environment+bashrc").

Regards.

---

### Post by littlewenwen on 2012-11-29
Thank you very much.

---

