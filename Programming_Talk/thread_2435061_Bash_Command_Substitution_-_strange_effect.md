---
title: "Bash Command Substitution - strange effect"
date: 2020-01-15
forum: Programming Talk
---

### Post by chl-z on 2020-01-15
Sometimes one has to worry about the difference between the Real User and the Effective User. 'whoami' gives the effective user. More useful are 'id -run' and 'id -un' to obtain real and effective respectively. Here is a little script

```
#!/bin/bash
set -x
su - control <<EOF
set -x
id -un
id -run
echo `id -un`
echo `id -run`
```

Note that 'control' is some user, preferably not the one running the script and preferably not a sudoer.

Now run this script as root by calling

```
sudo name-of-script
```

Now you might suspect that, inside, the real and effective users might be different (root and control are the obvious candidates), but what you actually get is

> + su - -s /bin/sh control
++ id -un
++ id -run
+ id -un
control
+ id -run
control
+ echo root
root
+ echo root
root


So, according to the first calls of 'id' , the real and effective users are both control. But when I put those same calls inside a command substitution (e.g. `id -run`) they are suddenly both root. Whatever is going on? And what is the workaround so that I can get the name 'control' as a piece of text to incorporate further down in the text? Note that all this is happening under Ubuntu 18.04.

What I am actually trying to construct is something that will deliver
```
pgrep --euid control gnome-keyring
```
so that I can find out the pid of and instance of gnome-keyring that is running under user control, so that I can kill it. It has to be run under root, because it is to be run in the middle of the night when the machine is woken up after having been put to sleep.

---

### Post by norobro on 2020-01-16
> **chl-z said:**
> So, according to the first calls of 'id' , the real and effective users are both control. But when I put those same calls inside a command substitution (e.g. `id -run`) they are suddenly both root. Whatever is going on? From the bash man page under command substitution:> `command`

Bash performs the expansion by executing command in a subshell environment ...The shell you are running is owned by root therefore so is the subshell. In the subshell you are not su'ed to user control.


After reading your post a couple of times, I'm still not clear about what the problem is. If you know the username why not, as root, execute: ```
kill $(pgrep --euid control gnome-keyring)
```

---

### Post by chl-z on 2020-01-20
> **norobro said:**
> From the bash man page under command substitution:The shell you are running is owned by root therefore so is the subshell. In the subshell you are not su'ed to user control.
I started in a shell owned by root, but then I did a 'su -' to control, so I expected to find myself in a new shell (as if I was logged in as control). It had certainly been all the way through control's .profile. But if I was still in the original shell, owned by root, then I would have expected the Real user to be root, which was not so.

> **norobro said:**
> After reading your post a couple of times, I'm still not clear about what the problem is. If you know the username why not, as root, execute: ```
kill $(pgrep --euid control gnome-keyring)
```
Basically, I was trying to write a more general purpose script which would have picked up whatever user I had 'su'ed to.

---

### Post by Skaperen on 2020-01-22
cat the script and look at the echo commands.  perhaps you added the echo commands to the script via an echo command.  if so then, what would happen is the [COLOR=#0000cd][FONT=courier new]**`id -un`**[/FONT][/COLOR] got evaluated when the command to add it to the script happened.  did you do this?
```

echo "echo `id -un`" >> name-of-script

```
if you did that then the [COLOR=#0000cd][FONT=courier new]**`id -un`**[/FONT][/COLOR] would be evaluated at the time of appending. and the result would be the same as if you did:
```

echo "echo root" >> name-of-script

```
double quote allows shell evaluation inside, including variable substitution and $().  but single quotes do not.  by using single quotes this issue can be prevented.
```

echo 'echo `id -un`' >> name-of-script

```
i'm just guessing that maybe this is what you did.  you can cat the file if you don't remember.  bash easily can do many things in unexpected contexts giving very unexpected results.

---

### Post by chl-z on 2020-01-23
> **Skaperen said:**
> cat the script and look at the echo commands.  perhaps you added the echo commands to the script via an echo command.  if so then, what would happen is the [COLOR=#0000cd][FONT=courier new]**`id -un`**[/FONT][/COLOR] got evaluated when the command to add it to the script happened.  did you do this?
```

echo "echo `id -un`" >> name-of-script

```
if you did that then the [COLOR=#0000cd][FONT=courier new]**`id -un`**[/FONT][/COLOR] would be evaluated at the time of appending. and the result would be the same as if you did:
```

echo "echo root" >> name-of-script

```
No, I did not do that; everything was constructed within gedit. However, you did give me the clue as to what was really going on.
Here is my original script with a couple of lines (indented, so you can see them)
```
#!/bin/bash
set -x
su - control <<EOF
   echo script running
set -x
id -un
id -run
    echo `pwd`
echo `id -un`
echo `id -run`
EOF 
```
and when you run this, you get
> $ sudo ./bash-test-orig+ su - control
++ pwd
++ id -un
++ id -run
script running
+ id -un
control
+ id -run
control
+ echo /home/chl/tests
/home/chl/tests
+ echo root
root
+ echo root
root

So you can see that the *\pwd\* which I have added was actually evaluated before the *su* had been activated, so that when it came to be echoed, it wasn't control's or root's home directory that was printed, but my own from where the test was being run.

So here now is the same thing split into two scripts

bash-test```
#!/bin/sh
set -x
su -l control < ./bash-script

```and bash-script```
#!/bin/sh
set -x
   echo script running
id -un
id -run
echo `id -un`
echo `id -run`

```
and if you run that with *sudo ./bash-test* you get
> + su -l control
+ echo script running
script running
+ id -un
control
+ id -run
control
++ id -un
+ echo control
control
++ id -run
+ echo control
control

which is exactly what I expected in the first place. The real and effective users inside the script are both control, however you test them.

---

### Post by trent.josephsen on 2020-01-24
Yes, this is how heredocs work. When the delimiter (EOF) is unquoted, the contents of the heredoc are expanded more or less the same way as if they were typed directly on the command line (after all, they kind of are). This is done by the shell running the script, not by the su command.

To avoid this, you can either not use a heredoc as you already discovered, or you can quote the delimiter string:

```

su - control <<'EOF'
   echo script running
set -x
id -un
id -run
    echo `pwd`
echo `id -un`
echo `id -run`
EOF
```

---

