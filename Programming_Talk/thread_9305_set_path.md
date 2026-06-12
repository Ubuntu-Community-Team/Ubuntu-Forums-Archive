---
title: "set path?"
date: 2004-12-27
forum: Programming Talk
---

### Post by hesee on 2004-12-27
I'm beginning programming c with gcc, compilation went presumably ok, but cannot run compiled file a.out:

bash: a.out: command not found

I think i must set path to find the file, but how? I tried:

PATH=$PATH:/home/hesee/C-prog

but after that: echo $path gives only empty line... Anyone who can help?

---

### Post by haha on 2004-12-27
you can run a.out in your home dir by "./a.out". ^^

like this :

$ ./a.out

---

### Post by lordan on 2004-12-30
To answer you question about the path, echo $path will not show you anything (in bash) you need to type echo $PATH. In zsh, echo $path will show you your path (space separated). Remember, shell variables are case sensitive.

You should not get into the habit of doing this, but if you want the current directory to be included in the command search path, you need to do PATH=.:$PATH, since the dot denotes the current directory.

Usually a better idea is to prepend the name of the executable with ./, as haha suggested, or to move the file into a location that is used to hold executable files, such as /usr/local/bin or ~/bin (provided you have it in your search path).

---

### Post by hesee on 2005-01-01
Thanks for advices, I'll be doing as you suggested from now on!

---

### Post by markusfarkus on 2007-11-30
Once you have set a path is there a way to remove it from your path?

---

### Post by komputes on 2007-12-20
Markus, if you used the "PATH=<your_path_here>:$PATH" it will only stay there for the duration that the terminal window stays open. Open a new terminal window and the $PATH variable will be reset to NULL.

I think you can add a PATH from your home directory (in the shell)

```
gedit /home/markusfarkus/.profile
```

(besides .profile you can also edit .bashrc or .bash_profile, although I chose .profile, because the path line to my home/me/bin *(in the script written as ~/bin)* was already in there, so I just appended a directory to it for my personal compilations).

The file will look like this
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=**~/bin:**"${PATH}"
fi
```

I think it should be there if you need to delete or add any.
If you add any paths separate them by a   :   colon. 

EXAMPLE:

```
    PATH=**~/bin:**"${PATH}"
```
becomes
```
    PATH=**~/bin:/dir1/dir2/cprogs:**"${PATH}"
```

---

### Post by glasier777 on 2009-12-27
Another option for enabling commands such as 'll' is to uncomment the command aliases in the .bashrc file in user home directory.

When installed, .bashrc contains the following:

# some more ls aliases
#alias ll='ls -l'
#alias la='ls -A'
#alias l='ls -CF'

To enable one or all of these alias commands, remove the hash mark (#) from before the line and then save .bashrc.

For example, to enable long listing (ll) and all file listing (la), uncomment the following lines:

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
#alias l='ls -CF'


The aliases will be available after next terminal login

---

### Post by FRKiran on 2012-12-08
I want to know what the difference between PATHes in "~/.profile" and "/etc/envrinment " is?
Here it was mentioned that we may edit "~/.profile".For inserting the path what adress we should use?

---

### Post by nothingspecial on 2012-12-08
Rather than replying to an old thread, please start a new one.

Closed.

---

