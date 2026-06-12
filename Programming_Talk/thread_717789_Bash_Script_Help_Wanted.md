---
title: "Bash Script Help Wanted"
date: 2008-03-07
forum: Programming Talk
---

### Post by fallenshadow on 2008-03-07
I recently have been using the command line for the first time ever. I have made many attempts to create a bash file that would copy a folder and its contents to /Opt.

What is the command to copy a folder and its contents to a directory such as /Opt?

Any help would really be appreciated.

---

### Post by ruy_lopez on 2008-03-07
```
cp -r /folder /opt/
```

to copy /folder to /opt using "./script.sh /folder /opt"
```

cp -r $1 $2

```

You would typically add some checks for type, number of arguments etc.

---

### Post by fallenshadow on 2008-03-07
Thanks for the quick reply, and what is the home folder in bash. I think it is $home but im not sure.

---

### Post by fallenshadow on 2008-03-07
duplicate post

---

### Post by ruy_lopez on 2008-03-07
It is $HOME

---

### Post by fallenshadow on 2008-03-07
OK last question, I promise :) Is $HOME just home or is it home/username?

---

### Post by raijinsetsu on 2008-03-07
$HOME should be the home directory of the user executing the scripts.
For example, if your username were RUPEY, $HOME would be "/home/RUPEY".

Why are you copying files to /OPT anyways?

---

### Post by fallenshadow on 2008-03-07
I want to create an installer that would copy everything into /Opt as creating a .deb installer was too complicated. I have seen this type of installer before so I thought I would do the same.

---

### Post by Dr Small on 2008-03-07
Just run:
```
echo $HOME
```

to see it's output.

---

### Post by mssever on 2008-03-07
Note that Linux is case-sensitive. /Opt and /opt are entirely different directories. The first one doesn't exist unless you explicitly create it.

Also, any time you write a script to copy files (or use variables to store anything but numbers or fixed strings), be sure to surround the variables with double quotes. ```
cp -r "$1" "$2"
```If you omit the quotes, then Bad Things could happen if the variables contain special characters (including spaces).

---

### Post by Can+~ on 2008-03-07
If you need more things of bash:

[PHP]env[/PHP]
(enviromental variables)

And to learn bash, there's a lot of pages out there, otherwise, you can use the manual
[PHP]man bash[/PHP]
(a bit long, but you can search with "/keyword")

---

### Post by ghostdog74 on 2008-03-07
> **fallenshadow said:**
> I recently have been using the command line for the first time ever. I have made many attempts to create a bash file that would copy a folder and its contents to /Opt.

What is the command to copy a folder and its contents to a directory such as /Opt?

Any help would really be appreciated.

 you should go [here]("http://www.shelldorado.com/links/index.html#tutorials") first.

---

### Post by fallenshadow on 2008-03-08
Thanks for the help everyone, this Ubuntu forum is so much more helpful than other forums. (such as LXF where they tell you to go read a manual or something). This is what I like, straight forward answers.

---

### Post by fallenshadow on 2008-03-08
My script does work but you have to click run in terminal for it to work. I know this is because it is using sudo and not gksudo but when I try gksudo and click run it does not work. why?

---

### Post by mssever on 2008-03-08
> **fallenshadow said:**
> My script does work but you have to click run in terminal for it to work. I know this is because it is using sudo and not gksudo but when I try gksudo and click run it does not work. why?

I don't know if I'm understanding you properly, but unless it's a GUI script or a daemon, it can only run in a terminal, in almost all cases. Otherwise, where can it print what you tell it to print?

If I missed your question, please post some code. That'll make it much easier to answer.

---

### Post by fallenshadow on 2008-03-09
You did answer my question... I have been trying a command like this to move a ".desktop" file into "/usr/share/applications":

```
sudo mv "$HOME/Desktop/folder/test a.desktop" "/usr/share/applications
```

but this will not work, does anyone know why? 
I want to put a Gnome menu entry into the menu using bash.

---

### Post by ruy_lopez on 2008-03-09
Try using $HOME like this:

```

mv "${HOME}/path/to/source/file" "/path/to/dest/"

```

---

### Post by mssever on 2008-03-09
> **ruy_lopez said:**
> Try using $HOME like this:

```

mv "${HOME}/path/to/source/file" "/path/to/dest/"

```

The curly braces, while not harmful, won't make any difference in this situation.

@fallenshadow:
Are you running that command in a terminal? You should be. I can't see anything wrong with it, though.

What error message do you get? (and what exit status--available by looking at $? immediately after running the command in question)

---

### Post by ruy_lopez on 2008-03-09
> **mssever said:**
> The curly braces, while not harmful, won't make any difference in this situation.


It's not just the curly braces I was showing. The paths have no spaces.

You're right, though. The braces are superfluous.

---

### Post by mssever on 2008-03-09
> **ruy_lopez said:**
> It's not just the curly braces I was showing. The paths have no spaces.
Spaces in paths are OK as long as the path is quoted or the spaces are backslash-escaped.

I did notice a missing quote at the end of the code snippet fallenshadow posted--which could be the problem unless it's merely a copy-and-paste error.

---

### Post by ruy_lopez on 2008-03-09
Also, if folder /usr/share/applications doesn't exist, moving a file there will create a *file* called applications.

Including a trailing slash "/use/share/applications/" will produce an error if the directory doesn't exist.

All this is assuming /usr/share/applications is supposed to be a directory. I couldn't tell from the quoted code.

---

### Post by mssever on 2008-03-09
> **ruy_lopez said:**
> All this is assuming /usr/share/applications is supposed to be a directory. I couldn't tell from the quoted code.

/usr/share/applications is where .desktop files live.

---

### Post by ruy_lopez on 2008-03-09
It's still good practice to use a trailing slash when moving files into directories, in case the directory doesn't exist.

---

