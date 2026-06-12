---
title: "writing alias for root and user"
date: 2012-04-29
forum: Programming Talk
---

### Post by ClientAlive on 2012-04-29
Hi,

I started writing some aliases but there's a special situation I'm not sure how to handle. I need to have aliases with the same alias name, one for when I'm logged as root and one when logged under my user name. The definitions would be almost identical except that one has "sudo" in it and (root obviously) doesn't.

For example - I have three aliases I use now when logged in under my user name:

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias install='sudo apt-get install'

These all work when I'm logged in under my user name; but, of course, when logged in as root I get an error.

If I recall correctly I'm storing these in a separate aliases file and point .bashrc to that file. How can I get the same aliases, with the same alias names to work when logged in as root?

I have a guess but I'm not sure if the approach would work, is the best approach even if it did, or if my bash script syntax is on target.

Something like...

```

In file: ~/.bashrc

if <some test to match against being logged in as rootr>

# point to that (root alias file)

elif <some test to match against being logged in as user>

# point to that (user alias file)

fi

```Or maybe there's a way to use the same, single aliases file and script a single test statement in .bashrc to check if I'm logged in as user to prepend the word "sudo" to a certain group of aliases? Maybe, in the future I end up with some aliases that don't require sudo so maybe in the aliases file I somehow define those aliases that should take sudo from those that don't - then if the test in .bashrc tests true for being logged in as user then it determines whether the particular alias needs sudo prepended or not?

idk...

whadaya think? How could I pull something like this off?
---------------------------------------

Edit:

Or maybe there's a way better, more robust way to accomplish something like this? Maybe it takes a little more work and involves a couple extra files but sets me up for growth in the future (maybe I add more user accounts for some reason later).  ??

---

### Post by sudodus on 2012-04-29
I must admit that I don't understand. If you are logged in as root (which is not recommended, but yes, if you know what you are doing)  you can run a command with and without sudo. Or should I say: I can run a command with and without sudo, and it makes no difference, that I can see, for example:
```
# apt-get update
``` and ```
# sudo apt-get update
``` both work (# is the root prompt, not the comment sign in this case).

By the way, how do you start running as root? Via [FONT="Courier New"][SIZE="3"]sudo -i, sudo -s[/SIZE][/FONT] or some other method? Maybe you should tweak root's own environment (for example its [FONT="Courier New"][SIZE="3"].bashrc[/SIZE][/FONT]).

---

### Post by ClientAlive on 2012-04-29
> **sudodus said:**
> I must admit that I don't understand. If you are logged in as root (which is not recommended, but yes, if you know what you are doing)  you can run a command with and without sudo. Or should I say: I can run a command with and without sudo, and it makes no difference, that I can see, for example:
```
# apt-get update
``` and ```
# sudo apt-get update
``` both work (# is the root prompt, not the comment sign in this case).

By the way, how do you start running as root? Via [FONT=Courier New][SIZE=3]sudo -i, sudo -s[/SIZE][/FONT] or some other method? Maybe you should tweak root's own environment (for example its [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT]).


Yes, I understand the implications of running as root. I don't just run as root all the time  ;)

Sometimes I log in as root when I know I have multiple administration type tasks to perform and I don't want to have to type sudo and my password to do them. What I've done is set a root acct password. I log in as root in one of two ways: (1) If I know I need to do admin stuff before I even boot the compter, I type root at the login prompt and just log in as root. (2) If I've been doing other stuff and encounter a situation where I need root, I type su at the command prompt and log in that way.

Yeah, when logged in as root you can tell you are because the command line does contain the hash symbol "#" at the end of your command prompt. In addition, the command prompt will read "root@<domain>..." as well.

Anyhow, (when _logged in as root_) in .bashrc I have the standard, default script for pointing to an aliases file:

```

if [ -f ~/._bash_aliases_ ]; then
   . ~/._bash_aliases_
fi

```And, (when _logged in as user_) in .bashrc I have the script for pointing to my aliases file:

```

if [ -f ~/._aliases_ ]; then # Note modification to file name
   . ~/._aliases_
fi

```And,  (_logged in as user_) a file ~/.aliases contians

```

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias install='sudo apt-get install'

```if, at the command prompt, I run "update" while logged in as user it asks me for my password, I give it, and everything proceeds fine. If logged in as root however, I run "update", I get...

```

No command 'update' found, did you mean:

#followed by suggestions of packages containing that command

```I assume this is because it's merely replacing the word "update" with "sudo apt-get update" on the command line and root doesn't take sudo? Or maybe there are more than one .bashrc files?

Now I hadn't noticed it before just now; but, if .bashrc contains those differences between when I'm logged in as root or as user, then perhaps there are actually two different .bashrc? Also, when logged in as root, the file .aliases is not present in ~/  but when logged in as user it is present. This seems to further support that each user on a Linux system (root being a user) may have it's own .bashrc, home directory, and contents thereof? If this is true then all I'd have to do is make an .aliases file for root and I'd be golden?
-----------------------------

---

### Post by dwhitney67 on 2012-04-29
> **ClientAlive said:**
> Yes, I understand the implications of running as root. I don't just run as root all the time  ;)

By having a root account, you have now given your adversaries half the information they require to gain access to your system.  Typically one requires a user-id and a password; now that the user-id is known... nevermind... I'm digressing into a void here.

Back to your question, in lieu of using simple one-liner aliases, define a function.  This function can check the effective user-id of the user running the function.  For example:
```

function update
{
    SUDO="sudo"

    if [ `id -u` -eq 0 ]; then
        SUDO=""
    fi

    $SUDO apt-get update
}

```
Frankly, I cannot fathom why typing sudo for each of a series of commands is an issue for anyone other than the lazy.  Seriously, are you updating your system every few minutes, or perhaps only once a week?  You could always run 'sudo -i' to run an interactive shell as root, without providing a password for the root account.

---

### Post by sudodus on 2012-04-29
> **ClientAlive said:**
> ...
Now I hadn't noticed it before just now; but, if .bashrc contains those differences between when I'm logged in as root or as user, then perhaps there are actually two different .bashrc? Also, when logged in as root, the file .aliases is not present in ~/  but when logged in as user it is present. This seems to further support that each user on a Linux system (root being a user) may have it's own .bashrc, home directory, and contents thereof? If this is true then all I'd have to do is make an .aliases file for root and I'd be golden?
Yes, root has it's own [FONT="Courier New"][SIZE="3"].bashrc[/SIZE][/FONT]

In my main computer OS (Ubuntu 10.04 LTS) it is located in the directory [FONT="Courier New"][SIZE="3"]/root[/SIZE][/FONT]

---

### Post by ClientAlive on 2012-04-29
> **dwhitney67 said:**
> By having a root account, you have now given your adversaries half the information they require to gain access to your system.  Typically one requires a user-id and a password; now that the user-id is known... nevermind... I'm digressing into a void here.

Back to your question, in lieu of using simple one-liner aliases, define a function.  This function can check the effective user-id of the user running the function.  For example:
```

function update
{
    SUDO="sudo"

    if [ `id -u` -eq 0 ]; then
        SUDO=""
    fi

    $SUDO apt-get update
}

```Frankly, I cannot fathom why typing sudo for each of a series of commands is an issue for anyone other than the lazy.  Seriously, are you updating your system every few minutes, or perhaps only once a week?  You could always run 'sudo -i' to run an interactive shell as root, without providing a password for the root account.


I just chose that particular alias "update" as my test case while learning about this. It seems it's a safe enough command to run until I learn (and a good enough example for a forum thread). There will likely be other aliases added to the system in the future though. This particular o/s happens to be the host o/s for a virtualization platform so yeah I anticipate times where I may need to do rather more extensive system admin and config.

Thank's for what you point out in your first paragraph btw. To be honest, I figure I know just enough to be dangerous. So I'm not familiar with all the pros and cons, or even all my options, for accomplishing my goal. (Goal being to simplify the performance of admin and config tasks so they aren't so tedious when there are a lot to do). I'll look into the arguments for/ against having a root account and what alternatives are avail (pros/cons) - as well.


> **sudodus said:**
> Yes, root has it's own [FONT=Courier New][SIZE=3].bashrc[/SIZE][/FONT]

In my main computer OS (Ubuntu 10.04 LTS) it is located in the directory [FONT=Courier New][SIZE=3]/root[/SIZE][/FONT]


Thanks for pointing that out.

---

