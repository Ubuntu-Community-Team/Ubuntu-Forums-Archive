---
title: "$PATH set up"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by bgcngm on 2012-07-10
I need some help from you guys. This is my $PATH variable:

```
bgcngm@ubuntu:~$ echo $PATH
/home/bgcngm/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/bgcngm/bin:/home/bgcngm/android-utility:/home/bgcngm/android-utility/utility:/home/bgcngm/android-sdk/platform-tools/:/home/bgcngm/android-sdk/tools:/home/bgcngm/android-sdk-linux_x86/tools:/home/bgcngm/android-sdk-linux_x86/platform-tools
```

I don't know what is adding these folders to the $PATH: **/home/bgcngm/android-sdk/platform-tools/:/home/bgcngm/android-sdk/tools**. I've already searched on /etc/environment and ~/.bashrc without any luck.

---

### Post by oldos2er on 2012-07-10
Post moved to its own thread.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

### Post by Krytarik on 2012-07-10
> **bgcngm said:**
> I don't know what is adding these folders to the $PATH: **/home/bgcngm/android-sdk/platform-tools/:/home/bgcngm/android-sdk/tools**. I've already searched on /etc/environment and ~/.bashrc without any luck.
Maybe this guide helps:

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

Regards.

---

### Post by bgcngm on 2012-07-11
Thanks for the quick reply, but I had already seen that guide. Unfortunately I have looked into all files that set system-wide environment variables without any success. I appreciate any further help to find how what is messing my $PATH.

---

### Post by papibe on 2012-07-11
Hi bgcngm. Welcome to the forums!

Did you check all your personal files?
```
~/.pam_environment
~/.profile
~/.bash_profile
~./bash_login
~/.profile
~/.bash_profile
~/.bash_login
~/.bashrc
```
Regards.

---

### Post by bgcngm on 2012-07-11
Yes, I've checked those files as well. Actually, I only have these ones:

```

~/.profile
~/.bashrc
```

---

### Post by papibe on 2012-07-11
Could you post the result of these commands?
```
diff /etc/skel/.bashrc  ~/.bashrc

diff /etc/skel/.profile ~/.profile
```
Regards.

---

### Post by bgcngm on 2012-07-11
Sure, here are the results:

```
diff /etc/skel/.bashrc ~/.bashrc
3a4
> # 
8,10c9,11
< # don't put duplicate lines or lines starting with space in the history.
< # See bash(1) for more options
< HISTCONTROL=ignoreboth
---
> # don't put duplicate lines in the history. See bash(1) for more options
> # ... or force ignoredups and ignorespace
> HISTCONTROL=ignoredups:ignorespace
23,26d23
< # If set, the pattern "**" used in a pathname expansion context will
< # match all files and zero or more directories and subdirectories.
< #shopt -s globstar
< 
107a105,107
> 
> export PATH=${PATH}:/home/bgcngm/android-sdk-linux_x86/tools:/home/bgcngm/android-sdk-linux_x86/platform-tools
>

```

This is okay. ~/.bashrc is where I add **/home/bgcngm/android-sdk[COLOR="Red"]-linux_x86[/COLOR]/tools:/home/bgcngm/android-sdk[COLOR="red"]-linux_x86[/COLOR]/platform-tools** to the $PATH. The problem is that I'm looking for what is adding **/home/bgcngm/android-sdk/platform-tools/:/home/bgcngm/android-sdk/tools**. These folders don't even exist in my setup.

```
diff /etc/skel/.profile ~/.profile 
13,16c13,16
<     # include .bashrc if it exists
<     if [ -f "$HOME/.bashrc" ]; then
< 	. "$HOME/.bashrc"
<     fi
---
> # include .bashrc if it exists
> if [ -f "$HOME/.bashrc" ]; then
> . "$HOME/.bashrc"
> fi
21c21
<     PATH="$HOME/bin:$PATH"
---
> PATH="$HOME/bin:$PATH"
22a23,28
> export LANG="en_IE.UTF-8"
> export LANGUAGE="en_US:en"
> export LC_MESSAGES="en_US.UTF-8"
> export LC_CTYPE="en_US.UTF-8"
> export LC_COLLATE="en_US.UTF-8"
> 

```

---

### Post by papibe on 2012-07-11
> **bgcngm said:**
> The problem is that I'm looking for what is adding **/home/bgcngm/android-sdk/platform-tools/:/home/bgcngm/android-sdk/tools**. These folders don't even exist in my setup.


They are being set before the execution of ~/.bashrc (because of its order on PATH).

These are also being set before:
```
/home/bgcngm/android-utility:/home/bgcngm/android-utility/utility
```

So I would check again the global files:
```
/etc/environment
/etc/profile
/etc/bash.bashrc 
```
Regards.

---

### Post by bgcngm on 2012-07-11
Checked and double checked...

**/etc/environment**

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"
LC_NUMERIC="en_IE.UTF-8"
LC_TIME="en_IE.UTF-8"
LC_MONETARY="en_IE.UTF-8"
LC_PAPER="en_IE.UTF-8"
LC_NAME="en_IE.UTF-8"
LC_ADDRESS="en_IE.UTF-8"
LC_TELEPHONE="en_IE.UTF-8"
LC_MEASUREMENT="en_IE.UTF-8"
LC_IDENTIFICATION="en_IE.UTF-8"
```

**/etc/profile**

```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
```

**/etc/bash.bashrc**

```
# System-wide .bashrc file for interactive bash(1) shells.

# To enable the settings / commands in this file for login shells as well,
# this file has to be sourced in /etc/profile.

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, overwrite the one in /etc/profile)
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '

# Commented out, don't overwrite xterm -T "title" -n "icontitle" by default.
# If this is an xterm set the title to user@host:dir
#case "$TERM" in
#xterm*|rxvt*)
#    PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD}\007"'
#    ;;
#*)
#    ;;
#esac

# enable bash completion in interactive shells
#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

# sudo hint
if [ ! -e "$HOME/.sudo_as_admin_successful" ] && [ ! -e "$HOME/.hushlogin" ] ; then
    case " $(groups) " in *\ admin\ *)
    if [ -x /usr/bin/sudo ]; then
	cat <<-EOF
	To run a command as administrator (user "root"), use "sudo <command>".
	See "man sudo_root" for details.
	
	EOF
    fi
    esac
fi

# if the command-not-found package is installed, use it
if [ -x /usr/lib/command-not-found -o -x /usr/share/command-not-found/command-not-found ]; then
	function command_not_found_handle {
	        # check because c-n-f could've been removed in the meantime
                if [ -x /usr/lib/command-not-found ]; then
		   /usr/bin/python /usr/lib/command-not-found -- "$1"
                   return $?
                elif [ -x /usr/share/command-not-found/command-not-found ]; then
		   /usr/bin/python /usr/share/command-not-found/command-not-found -- "$1"
                   return $?
		else
		   printf "%s: command not found\n" "$1" >&2
		   return 127
		fi
	}
fi
```

This is the content of my files. Nothing wrong here. :confused:

---

### Post by bgcngm on 2012-07-11
> **papibe said:**
> They are being set before the execution of ~/.bashrc (because of its order on PATH).

These are also being set before:
```
/home/bgcngm/android-utility:/home/bgcngm/android-utility/utility
```

Now that you pointed that, I went to the folder where that tool is installed... Upon the installation this code was executed:

```
bpro3 ()
{	echo "andutil not in path. Writing to .bashrc"
	echo "" >> $HOME/.bashrc
	echo "export PATH=$HOME/bin:$HOME/android-utility:$HOME/android-utility/utility:$HOME/android-sdk/platform-tools/:$HOME/android-sdk/tools:\${PATH}" >> $HOME/.bashrc
	enter
}

```

According to that it was supposed to have those entries on my ~/.bashrc. Where to look more? Could it be that there's some else file setting the path after the upgrade from Ubuntu 11.10 to 12.04?

---

### Post by papibe on 2012-07-11
EDIT: I think you got it.

> Could you post the result of this command?
```
more /etc/profile.d/*
```
Regards.

---

### Post by bgcngm on 2012-07-11
```
more /etc/profile.d/*
::::::::::::::
/etc/profile.d/au.sh
::::::::::::::
export PATH=${PATH}:$HOME/bin:$HOME/android-utility:$HOME/android-utility/utilit
y:$HOME/android-sdk/platform-tools/:$HOME/android-sdk/tools
::::::::::::::
/etc/profile.d/bash_completion.sh
::::::::::::::
# Check for interactive bash and that we haven't already been sourced.
[ -z "$BASH_VERSION" -o -z "$PS1" -o -n "$BASH_COMPLETION" ] && return

# Check for recent enough version of bash.
bash=${BASH_VERSION%.*}; bmajor=${bash%.*}; bminor=${bash#*.}
if [ $bmajor -gt 3 ] || [ $bmajor -eq 3 -a $bminor -ge 2 ]; then
    if shopt -q progcomp && [ -r /etc/bash_completion ]; then
        # Source completion code.
        . /etc/bash_completion
    fi
fi
unset bash bmajor bminor
```

That's it! Thanks for your great support. :)

---

### Post by papibe on 2012-07-11
:D Super! You are very welcome.

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")) when you have the chance.

Regards.

---

