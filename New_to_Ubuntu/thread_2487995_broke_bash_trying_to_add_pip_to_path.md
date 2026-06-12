---
title: "broke bash trying to add pip to path"
date: 2023-06-20
forum: New to Ubuntu
---

### Post by gbp00 on 2023-06-20
the reason I was doing the vim method is I don't know how to edit root files. none of methods i saw worked. Will you say how? Since terminal not working i have to learn. 

vim .bashrc
press i to enter insert mode
append this:
export PATH= "$HOME/.local/bin:$PATH"
esc to enter cmdmode
save it:
:w 
exit terminal

check etc/bash.bashrc  , the updates are not there. which file was I editing?  when I search "bashrc" in home, only that file comes up.

reboot


now terminal isnt working at all.


bash: export: `/home/k/.local/bin:/home/k/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin': not a valid identifier


Thanks folks

---

### Post by ActionParsnip on 2023-06-20
You don't need the "export" bit. Here is what I have
```

PATH="$HOME/.local/bin:$HOME/bin:$PATH"

```

---

### Post by gbp00 on 2023-06-20
Yep thanks, misunderstood this guide [https://linuxize.com/post/how-to-add-directory-to-path-in-linux/](https://linuxize.com/post/how-to-add-directory-to-path-in-linux/)

Still need to edit the file again as Root which idk how to do. i see now, its a hidden file.

---

### Post by Holger_Gehrke on 2023-06-20
You don't need to be root to edit hidden files as long as you have permission to write to the file. Hidden files are hidden as a convenience so you don't see the dozens of hidden files and directories that programs use to store their settings. For example in my $HOME there are 129 hidden files and directories, but I mostly work with the 41 which aren't hidden. Not seeing them when I don't need to work on them is nice. There's a key in the file manager that acts as a toggle to switch the visibility of hidden files. Usually it's ctrl-h. So open your file manager, hit the toggle key, right click on '.bashrc' and open it with your favorite editor.

Holger

Edit: the error is caused by the space you have between '=' and '"' in your export line. 'export' marks variables as to be exported to child processes of the shell. It expects a list of space-separated variable-names each optionally followed by an equal sign and a value for the variable. By having a space between the '=' and the value you're telling export that this is a new variable (and it isn't and would be an illegal name for a variable anyway because of the colons in there ...).

---

### Post by TheFu on 2023-06-20
You didn't specify the full path to the file you wanted to edit, so it picked the file in the CWD, where ever that was.  That may or may not be the correct file.

You don't have to use vim for an editor if you don't want to.  You can use nano, with is easier for noobs.
Also, if you need to edit a system file, use the **sudoedit** command. It is the safest way to edit system files.

```
export PATH= "$HOME/.local/bin:$PATH"
```

There cannot be an extra space after the '=' character.  BTW, it would be smarter to check if the desired path were already in the PATH before blindly setting it. This will avoid it being added over and over and over and over and over and over .... 
$HOME/.local/bin:$PATH"
....
$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$HOME/.local/bin:$PATH"

that wouldn't be good, right?

---

### Post by gbp00 on 2023-06-20
".local" isnt found in the hidden bashrc when i search.
meaning the edit i made is not in .bashrc

So why is bash still giving an error?

sudo apt install ___ 
Gives error "bash: sudo: No such file or directory"

---

### Post by TheFu on 2023-06-20
Which .bashrc did you edit?  We still don't know.

BTW, whatever you did will probably not be something we can guess remotely.  Only you will be able to find and fix it. You could have touched/modified files without realizing it. You could have changed permissions on files accidentally. We don't know what you've done and our guesses will likely be wrong.

---

### Post by ActionParsnip on 2023-06-20
Try
```

/usr/bin/sudo /usr/bin/apt update

```

He's been messing with the path variable, not permissions (as far as I know). If the above works it's simply a malformed path variable

---

### Post by gbp00 on 2023-06-20
Sudo: bash: error remains.
This didn't solve the problem. I only did what I said in post, changed the paths as shown. the hidden .bashrc in /etc/ was edited most recently months ago which confuses me. Shouldn't it say updated recently?

---

### Post by TheFu on 2023-06-20
There's no .bashrc in /etc/ that is referenced by any bash startup.

The bash manpage says this:
```
       --rcfile file
              Execute  commands  from file instead of the system wide initial&#8208;
              ization file /etc/bash.bashrc and the standard personal initial&#8208;
              ization  file ~/.bashrc if the shell is interactive (see INVOCA&#8208;
              TION below).
...
       --noprofile
              Do  not read either the system-wide startup file /etc/profile or
              any  of  the  personal  initialization  files   ~/.bash_profile,
              ~/.bash_login,  or  ~/.profile.   By  default,  bash reads these
              files when it is invoked as a login shell  (see  INVOCATION  be&#8208;
              low).

       --norc Do  not  read  and  execute  the system wide initialization file
              /etc/bash.bashrc and the personal initialization file  ~/.bashrc
              if  the  shell  is interactive.  This option is on by default if
              the shell is invoked as sh.

```

Check your local manpage, since the version on your system could be different from that on my system.

Basically, it is considered bad form to modify the system init files for any shell and each user should be modifying their on inside their own HOME directory.

---

### Post by ActionParsnip on 2023-06-21
Are you using a capital S for sudo?

---

### Post by gbp00 on 2023-06-21
Good info, yes it was a local file. Turns out I "backed it up" before editing with vim out of paranoia.

---

### Post by TheFu on 2023-06-22
> **gbp00 said:**
> Good info, yes it was a local file. Turns out I "backed it up" before editing with vim out of paranoia.

So this is SOLVED now?

---

