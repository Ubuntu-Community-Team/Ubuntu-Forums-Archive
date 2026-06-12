---
title: "shell function with the same name calling built in utility"
date: 2008-08-07
forum: Programming Talk
---

### Post by chris200x9 on 2008-08-07
ok I'm having a hard time I'm trying to make sudo act like sudo -s as long as I don't input a command or argument. so far I have added this to my ~/.bash_profile ```
 sudo ()
{
command=$1

if [ -z "$command"]; then
sudo -s
esle
sudo
fi
}


``` but it seems to not be calling my function when I type sudo if I remember correctly functions take precedence over built in commands so I'm unsure why this isn't working. Sorry I am pretty new to shell scripting, I would appreciate any help. Thank you.

---

### Post by LaRoza on 2008-08-07
Besides the typo? (esle)

I recommend using an alias instead of a function. I also recommend not using the same name as "sudo" it may be recursive and that is just a bad idea.

---

### Post by dwhitney67 on 2008-08-07
After you edited your ~/.bash_profile, what did you do next?

Here's a hint of what you should do:
```
$ source ~/.bash_profile
```
P.S.  Don't forget to correct the spelling of 'esle' as shown in your OP.

P.S.S.  To avoid possible recursion, preface the 'sudo' in your script with /usr/bin so that it appears as /usr/bin/sudo.

---

### Post by mssever on 2008-08-08
There's nothing wrong with calling a function sudo. You just have to be careful how you do it. (And it would be difficult to do what the OP is trying to do in a readable manner using an alias. This is what functions are for.) Another option would be to write a separate script and put it on your $PATH.

In Bash, the precedence order is:

[LIST=1]
[*]Alias
[*]Function (not sure of the order of the first two)
[*]Built-in
[*]Program found via a $PATH search
[/LIST]
Bash runs the first commands it finds on that list. So if you're defining a sudo function, you're blocking access to the real sudo. You have two options: a) specify the absolute path to sudo, or b) use the [FONT=Courier New]command[/FONT] builtin to override the precedence lookup and do a $PATH search (type [FONT=Courier New]help command[/FONT] for details).

The command [FONT=Courier New]builtin[/FONT] is also useful to gain access to shell builtins that you've overridden.

Here's an example of doing something like this. I got tired of always typing [FONT=Courier New]ls[/FONT] after [FONT=Courier New]cd[/FONT]. So, I decided to automate it. The process of doing that taught me the above (if you do it wrong, you can crash bash). ```
cd() {
  builtin cd "$@"
  local status=$(($?)) # I have no idea why I used that syntax. It certainly isn't necessary.
                       # I haven't looked at this function in years.
  [ $status -eq 0 ] && ls
  return $status
  [ $status -eq 0 ] && ls
}
```

---

### Post by chris200x9 on 2008-08-08
I almost got it ```
  sudo () {  command="$@";    if [ -z "$command" ]; then
sudo -s;
else  sudo $command;  fi;  }

``` 

the only problem is it won't work with the name sudo, if I name it sudotest and type in sudotest it works perfectly just as I want but if i name it sudo and type in sudo it just hangs.:confused:

edit: I'm on archlinux in case that affects anything.

---

### Post by mssever on 2008-08-08
> **chris200x9 said:**
> I almost got it ```
  sudo () {  command="$@";    if [ -z "$command" ]; then
sudo -s;
else  sudo $command;  fi;  }

```the only problem is it won't work with the name sudo, if I name it sudotest and type in sudotest it works perfectly just as I want but if i name it sudo and type in sudo it just hangs.:confused:

edit: I'm on archlinux in case that affects anything.
Please indent your code properly. It's very difficult to read otherwise.

Try this (which is what I said in my previous post): ```
function sudo {
  command="$@"
  if [ -z "$command" ]; then
    command sudo -s
  else
    command sudo "$@"
  fi
}
```(I haven't tested this.)

---

### Post by chris200x9 on 2008-08-08
yes it works, thank you so much.

---

