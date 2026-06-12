---
title: "Bash tab-auto complete not working 100%"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by sffvba[e0rt on 2011-10-20
Recently installed 11.10 and it is working very well.

One issue I have run across is that in Terminal only the first command will tab-auto complete...

Example:

I want to use "sudo apt-get update".
Only sudo will tab-auto complete, the rest I must type out.

Normally I could hit tab for all three words.

Any thoughts and suggestions are welcomed :)



Cheers
404

---

### Post by kaldor on 2011-10-20
Had a similar issue on Fedora a while back. [_This_]("http://www.linuxquestions.org/questions/fedora-35/tab-does-not-auto-complete-in-terminal-440190/#post2224063") did it for me.

Just a shot in the dark :)

---

### Post by sffvba[e0rt on 2011-10-20
> **kaldor said:**
> Had a similar issue on Fedora a while back. [_This_]("http://www.linuxquestions.org/questions/fedora-35/tab-does-not-auto-complete-in-terminal-440190/#post2224063") did it for me.

Just a shot in the dark :)

That didn't help 100%.

It did auto-complete more than normal... but when I hit the tab auto-complete after "sudo apt-get" and wanted to have "install" it gave me a list of applications that started with "ins" and not the variables for apt-get as I am used to with previous releases :(

I have removed the two lines in the link you have given me for now...


Cheers
404

---

### Post by sffvba[e0rt on 2011-10-20
Thanks to inetpro over at #ubuntu-za on Freenode I was able to get it working.

The link he supplied me was [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/) ...

I edited my etc/bash.bashrc file and uncommented the following bit:
```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

Worked like a charm...


404

---

### Post by Kossilar on 2012-03-19
Thanks for the fix! Any idea why such an obviously useful feature is disabled by default?

---

### Post by mistry on 2012-11-29
> **not found said:**
> Thanks to inetpro over at #ubuntu-za on Freenode I was able to get it working.

The link he supplied me was [http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/](http://embraceubuntu.com/2006/01/28/turn-on-bash-smart-completion/) ...

I edited my etc/bash.bashrc file and uncommented the following bit:
```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```Worked like a charm...



Had the completion lines on as shown above, but sudo would not complete anymore on Quantal as well as wanting a way to quickly complete known computers I connect to.  I added the following to my ~/.bashrc after doing the above, but I only added what is below in my home directory's bashrc file (~/.bashrc)  . . .

```


if [ "$TERM" != "dumb" ]; then
     complete -W "$(echo `cat ~/.ssh/known_hosts | cut -f 1 -d ' ' | sed -e s/,.*//g | uniq | grep -v "\["`;)" ssh
     complete -W "$PATH" sudo
     complete -cf sudo
fi


```

---

### Post by ksatta1 on 2012-12-02
On my VPS:
```

sudo apt-get install bash-completion
sudo apt-get update

```- uncomment completion stuff from /etc/bash.bashrc
- comment out completion stuff from ~/.bashrc

Now it works like it should, I think. All steps might not be needed, but it works like that for me.

---

### Post by RichardCain on 2013-04-11
Another thing I found which sorted my problems was the last few lines of *~/.bashrc*:
> # Enable auto-complete function fully
complete -cf sudo
complete -cf man

Make sure these two lines are commented out, otherwise it will list every single possible option for autocomplete.

---

### Post by mdlueck on 2013-08-24
I followed #4 on Ubuntu Server 12.04 and it still refuses to work for files within a given directory.

Any suggestions which of the various remedies talked about on this thread gets tab auto complete working again for files?

---

