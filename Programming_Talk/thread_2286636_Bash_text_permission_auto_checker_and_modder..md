---
title: "Bash text permission auto checker and modder."
date: 2015-07-13
forum: Programming Talk
---

### Post by yuannan on 2015-07-13
This is a super simple script that check if the current file allows you to edit it and if it does it launches VIM or easily changeable to anything of your choice.

Source and Download here:

v2:[http://pastebin.com/FYS2ACFQ](http://pastebin.com/FYS2ACFQ)
V1:[URL="http://pastebin.com/RPSr5SrN"]http://pastebin.com/RPSr5SrN
[/URL]

Download this and place it in "/bin" or "/usr/bin" or add it to your PATH variable or what ever you want.
I'm new to Linux and Bash and created this out of boredom and constantly forgetting to sudo before all my commands.
Feel free to give me feedback and MODs  and move this if it's  in the wrong section or delete it if it's already made :eek:.

---

### Post by papibe on 2015-07-13
Hi yuannan. Welcome to the forum ):P

A few thoughts to improve your script:

Always quote your variables. For example, this would create a problem when the file has spaces on its name:
```
vim $file
```
This would solve that problem:
```
vim "$file"
```
It is always better to use internal bash functionality instead of calling an external command. For instance, to check if a file is writeable by the user is calling the script, you can use pre built tests:
```
if [ -w "$file" ]; then
    echo "$file is writeable"
else
    echo "$file is NOT writeable"
fi
``` 
In order to get the other permissions, I would avoid 'ls' and use 'stat' instead:
```
$ $ stat --format='%A'  a_file
-rw-rw-r--

```
Then I would get the substring using a bash string expressions (to avoid calling 'cut'):
```
$ perms=$(stat -c %A a_file )
$ echo ${perms:7:1}
r

```
Hope it helps.
Regards.

P.S.: Note that root can edit all files. Vim just warn you that the file is readonly, but you can force it by going :w! or :wq!

---

### Post by yuannan on 2015-07-14
Thanks for the feedback, I did some reserch and shortened the file down a bit and pushed out V2.

But can you explain to me this bit?

> **papibe said:**
> 
Then I would get the substring using a bash string expressions (to avoid calling 'cut'):
```
$ perms=$(stat -c %A a_file )
$ echo ${perms:7:1}
r

```


I understand the first bit as it assign the command output to $perms, but the second bit is quite confusing and when I ran it in my terminal it echoed a blank.

---

### Post by papibe on 2015-07-14
Replace 'a_file' with an actual file in your directory, or a path to a existing file. Also you can echo $perms as it is to make sure it's not empty.

Here's a good guide on the subject: [Extracting parts of strings]("http://mywiki.wooledge.org/BashFAQ/100#Extracting_parts_of_strings").

Hope that helps. Let us know if you have more questions.
Regards.

---

### Post by ofnuts on 2015-07-17
> **yuannan said:**
> TI'm new to Linux and Bash and created this out of boredom and constantly forgetting to sudo before all my commands.

You shouldn't because in practical use sudo-ing is fairly rare, especially to edit files. And if the files are read-only it is usually for some good reason. If you need sudo that often you aren't using your system properly, and your script is just helping you to live very dangerously.

For some scripts I use that requires root privs, instead of lacing the script with sudo's,  I make the script just reinvoke itself after a single sudo:

```

[[ $(id --user) -ne 0 ]] && { echo "Sudoing..." ; sudo $(readlink -e $0) "$@" ; exit 0 ; } # sudo ourself

# actual code start here, only executed if already sudoed, so it doesn't need sudo in front of each command
[...]

```

---

