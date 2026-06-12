---
title: "[SOLVED] Customizing bash prompt"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-21
Hi, all:

I've been googling, and I'm having the devil of a time trying to figure out how to alter my bash prompt.  So, I want my bash prompt for username to be "[tarahmarie-desktop:~] GO BLUE $" or whatever.  I tried editing the bash.bashrc file in /etc, and it's not changing anything.  Where can I fix this?

I found a tutorial here: [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

but once I'd rebooted, the change I made to PC1 reverted back to the Ubuntu default.

---

### Post by Mornedhel on 2008-09-21
I believe the relevant line in ~/.bashrc is this one :

PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"'

Uh, have fun ?

---

### Post by tarahmarie on 2008-09-21
Erm, that looks a bit like gibberish to me.  What precisely would I do to it to get a prompt like these for username and root, respectively:

current directory: Your Wish Is My Command, O Queen of Everything $

current directory: Darth Prompt #

---

### Post by Mornedhel on 2008-09-21
Ok, I'm getting curious as well.

echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"

From man echo :
-n is for "do not output the trailing newline"
-e is for "enable interpretation of backslash escapes"

From random Google searches : what we're interested in is everything between "\033]0;" and "\007". I have no idea what they mean exactly, so I'm leaving them alone.

From experience :
${USER} is your username
${HOSTNAME} is your hostname (how original)
${PWD} is your current directory, and here it's modified so as to replace your home directory ($HOME) by "~" if it's in the current directory, for instance : echo ${PWD/o/e} gives me "/heme/mornedhel". Note, only the longest match is modified. For the terminally curious, man bash explains it better. Look for "${parameter/pattern/string}".

So for :

current directory: Your Wish Is My Command, O Queen of Everything $

We get :

echo -ne "\033]0;${PWD/$HOME/~}: Your Wish Is My Command, O Queen of Everything \007"

(which IMHO eats up a lot of horizontal space, but hey, your wish is my command.)
I've tried it in the terminal by removing the \033]0; and \007 parts, and it seems to work.

For Darth Prompt, try the same modifications in /root/.bashrc .

Disclaimer : I do not consider myself a Bash expert. The above advice is at your own risk.

---

### Post by mister_pink on 2008-09-21
I am also no expert but the above advice looks right. I'd just like to add that I believe the numbers are to do with the colour of the prompt. 

Also, generally you don't want to be putting things in the system wide configuration if its not something that is a system wide change (ie dont edit the file in /etc)

---

### Post by tarahmarie on 2008-09-21
I tried modifying my /etc/bash.bashrc like this:

    PROMPT_COMMAND='echo -ne "\033]0;${PWD/$HOME/~}: Your Wish Is My Command, O Queen of Everything \007"'

and uncommented it.

Still doesn't work.  Rats.  Any other ideas?

---

### Post by Mornedhel on 2008-09-21
You need to edit your own .bashrc (in your own home folder), and optionally root's .bashrc, in /root/.bashrc.

The difference between all of those bashrc files, as shamelessly copypasted from a Google search, copypasted itself from man bash, apparently :

> When bash is invoked as an interactive **login shell**, or as a non-interactive shell with  the --login option,  it  first reads and executes commands from the file /etc/profile, if that file exists.  After reading that file, it looks  for  ~/.bash_profile,  ~/.bash_login,  and  ~/.profile,  in  that order, and reads and executes commands from the first one that exists  and is readable.  The --noprofile option may be used when the shell is started  to  inhibit this behavior.
...
When an interactive shell that is **not a login shell** is started,  bash  reads  and  executes  commands  from /etc/bash.bashrc and ~/.bashrc, if these files exist.  This may be inhibited by using the --norc option.  The --rcfile file option will force bash to read  and  execute commands from file instead of /etc/bash.bashrc and ~/.bashrc.

Edit. Bash sees ~/.bashrc after /etc/bash.bashrc, and thus overwrites your PROMPT_COMMAND from etc/bash.bashrc with the one in ~/.bashrc.

---

### Post by tarahmarie on 2008-09-21
I am officially taking a 42-minute break from fiddling with the damn thing to watch Commander Trip Tucker holler "Keep yer shirt on" at Captain Archer.

Bother the bash shell.  I'll come back to it when I'm inspired by Okudagrams--give me an hour.

---

### Post by tarahmarie on 2008-09-22
ARRG! (Too bad it's no longer Talk Like A Pirate Day!)

WHY isn't this working?

[tarahmarie@tarahmarie-desktop:~] $export PS1="\w\]: Your Command, Supreme Empress? $  "
~: Your Command, Supreme Empress? $  exec bash
[tarahmarie@tarahmarie-desktop:~] $


I restart bash and the prompt goes right back to what it was.  Why does it work for others and not me?

---

### Post by lswest on 2008-09-22
very useful site, it's what I used to do so: [http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/](http://linuxowns.wordpress.com/2008/09/05/custom-terminal-prompt/)

---

### Post by tarahmarie on 2008-09-22
Aha!  I've googled til I cain't google no more, and it seems that a synergy of responses was needed to fix this ickle customization problem.

Here is the quickest, easiest way to customize your bash prompt:

To edit your root prompt, paste a line like this in the bottom of your /root/.bashrc file:

export PS1="\w: Darth Prompt (8<| \\$ "

To edit your username prompt, paste a line like this in the bottom of your /home/username/.bashrc file:

export PS1="\w : Yes, Supreme Empress? $ "

Then, restart bash by running "exec bash"

Here are the results:

/: Darth Prompt (8<| # exit
exit
/ : Yes, Supreme Empress? $ 

Thanks to all the posters; this one took a village.

---

### Post by iconoclast1979 on 2008-10-09
I'm a total newbie (so I admittedly know very little about linux), but I've been reading a lot about this subject and learned about the "PS1" environment command and I've found that it isn't necessary to add the "export..." line at all.

There is a line in the "[COLOR=Blue]**.bashrc**[/COLOR]" file that controls the default prompt already, so customizing it is a simple matter of altering the corresponding line(s). 

This is the part you're looking for:

[COLOR=Blue][B]if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi[/B][/COLOR]

The first of the "PS1" lines controls the default prompt for the "root" user, while the second of the two corresponds to the current user's default prompt (assuming the current user isn't "root", obviously).

The stuff between the quotes dictates what the prompt will look like, so whatever you type there will be displayed as your prompt by default. There are also those short-cut switches:

"[COLOR=Blue]**\u**[/COLOR]" displays the current user's username
"[COLOR=Blue]**\w**[/COLOR]" displays the "present working directory"
"[COLOR=Blue]**\$**[/COLOR]" displays the current user's access-level
"[COLOR=Blue]**\t**[/COLOR]" adds a timestamp to each occurrence of the prompt
"[COLOR=Blue]**\d**[/COLOR]" adds the date to each occurrence of the prompt

I'm sure there are other options/switches that I haven't learned yet, but these are probably the ones used most commonly.

So, for instance, if one were to change the first "PS1" line to:

[COLOR=Blue]**PS1="\$\u - Master of the Universe:"**[/COLOR]

Then the default prompt for "root" would look like this:

[COLOR=Blue]**#root - Master of the Universe:**[/COLOR]

Et cetera...

Incidentally, one can also temporarily change the prompt at any time using the "PS1" command from the prompt (though it will only work for that one instance of the terminal).

I know that this issue has already been solved, but I just thought I'd put my two-cents in about this alternate way of solving the problem. I hope this helps someone else who is looking for a solution to this issue.

*Edit: Just after posting this, I found a post on another thread with a great list of switches and even colours for the "PS1" command. It can be found [here]("http://ubuntuforums.org/showthread.php?t=674446&highlight=change+terminal+prompt").

---

