---
title: "sudo apt-get update &amp;&amp; apt-get upgrade &amp;&amp; apt-get install returns error"
date: 2017-02-19
forum: New to Ubuntu
---

### Post by rashhashan on 2017-02-19
sudo apt-get update && apt-get upgrade && apt-get install 

returns 

```
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

but i am sudo, so i am root?

---

### Post by Perfect Storm on 2017-02-19
Make sure to close the software center or any update/upgrade software first.

---

### Post by lisati on 2017-02-19
You might wish to try this:
```
 sudo apt-get update && **sudo** apt-get upgrade && **sudo** apt-get install 
```

---

### Post by rashhashan on 2017-02-19
I just tried to restart and that didn't even fix it

---

### Post by rashhashan on 2017-02-19
> **lisati said:**
> You might wish to try this:
```
 sudo apt-get update && **sudo** apt-get upgrade && **sudo** apt-get install 
```

That did it, thanks!

---

### Post by oldos2er on 2017-02-19
> **rashhashan said:**
> sudo apt-get update && apt-get upgrade && apt-get install 

returns 

```
W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)
W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

but i am sudo, so i am root?

Each apt-get command in your string requires *sudo*

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install
``` but *sudo apt-get install* requires a package name to install.

Also see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kingneutron on 2017-02-21
--To try and make things easier for you, I looked up a way to chain commands together with sudo.

REF: [http://stackoverflow.com/questions/5560442/how-to-run-two-commands-in-sudo](http://stackoverflow.com/questions/5560442/how-to-run-two-commands-in-sudo)

--If you don't want to put multiple commands into a bash script and then run the script with sudo (which may be easier) try something like:

$ sudo -s sh -c -- 'apt-get update && apt-get upgrade'

---

### Post by rashhashan on 2017-02-21
> **kingneutron said:**
> --To try and make things easier for you, I looked up a way to chain commands together with sudo.

REF: [http://stackoverflow.com/questions/5560442/how-to-run-two-commands-in-sudo](http://stackoverflow.com/questions/5560442/how-to-run-two-commands-in-sudo)

--If you don't want to put multiple commands into a bash script and then run the script with sudo (which may be easier) try something like:

$ sudo -s sh -c -- 'apt-get update && apt-get upgrade'

what is the 

```
sh
```

command and how can i learn how to write with it? Is it bash shell scripts?

---

### Post by cariboo on 2017-02-21
That seems to be a lot of typing every time you do and update and upgrade. I created an alias in ~/.bashrc:

```
alias update='sudo apt update && sudo apt dist-upgrade -y'
```

Just type update, then your password and sit back.

---

### Post by yetimon_64 on 2017-02-21
> **cariboo said:**
> That seems to be a lot of typing every time you do and update and upgrade. I created an alias in ~/.bashrc:

```
alias update='sudo apt update && sudo apt dist-upgrade -y'
```

Just type update, then your password and sit back.

Good idea, only I ended up with so many aliases I put them all in their own file to keep .bashrc tidy. 
I use a "~/.bash_aliases" file to keep aliases in; it is picked up by the next bit of code within the .bashrc file itself ...
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```
My aliases specifically for updating/upgrading ...
> ```
alias agu='sudo apt-get update'
alias agg='sudo apt-get -y upgrade'
alias agug='sudo apt-get update && sudo apt-get -y upgrade'
alias agdu='sudo apt-get -y dist-upgrade'
alias upd8.full='agug && agdu'

```
The last one strings two other aliases together to do a full update/dist-upgrade together. "agug" would be what I type in with my password to do the same command as the OP asked about, but with the "-y" switch set for no prompting (just how I use the aliases when in terminal).

Edit: with respect to the install command, my aliases for installing reinstalling and purging etc ...
Edit2: note the end of the next three aliases all have a space at the end of the command for the package name that is to follow.
> ```
alias install='sudo apt-get -y install '
alias reinstall='sudo apt-get -y --reinstall install '
alias remove='sudo apt-get -y remove '
alias purge='sudo apt-get -y purge '

```To use I'd type something like ...
```
install foo
```
... to install the application named "foo". Same with removing, purging and reinstalling, first the alias then the package name > Enter > Password & Enter etc.

---

