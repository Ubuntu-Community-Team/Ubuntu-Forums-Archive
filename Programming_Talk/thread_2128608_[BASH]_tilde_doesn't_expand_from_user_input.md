---
title: "[BASH] tilde doesn't expand from user input?"
date: 2013-03-23
forum: Programming Talk
---

### Post by gandalf3 on 2013-03-23
I am learning some bash scripting, and I want to have the user type in a path to some directory and allow the use of ~
so that 
```
echo 'type path to somedir'
read -e -p "> " path
path=${path//\~/$HOME}
echo 'your path:'
echo $path
```
however, it seems the tilde charecter cannot be replaced??

EDIT:
fixed code, thanks.

---

### Post by schragge on 2013-03-23
Try
```
[COLOR=#000000][FONT=Ubuntu Mono]path=${path/#\~/$HOME}[/FONT][/COLOR]
``` [s]Actually, there's not much point in such substitution as you can force tilde expansion with *eval*:[/s] [highlight]Edit.[/highlight] Too dangerous, see **Vaphell**'s [post=12572485]post[/post] below.
```

read -ep 'type path to somedir ' path
eval echo your path: $path

```
Moreover, tilde not always expands to $HOME. E.g. *~user* means home directory of *user*, ~+ = $PWD, ~- = $OLDPWD, and so on.

Note also that your code has other problems, too: no prompt after *read -p* and single quotes in the last line (shell parameters get expanded only inside double quotes).

---

### Post by gandalf3 on 2013-03-23
> Try
     Code:
     
[COLOR=#000000][FONT=Ubuntu Mono]path=${path/#\~/$HOME}[/FONT][/COLOR]  
oh wow that worked! thanks.
thanks for the tip about eval, i think i'll use that.
though i can't get the variable path reassigend to the eval-ifide path??

```

read -ep '> ' path
path= eval echo $path
echo $path

```

EDIT


i can't mark as solved in "thread tools"?? 

im not used to the new interface yet.. probably just me being an idiot :oops:

---

### Post by schragge on 2013-03-24
> **gandalf3 said:**
> i can't mark as solved in "thread tools"??You need to edit the thread name manually as described in [post=12536730]this post[/post].

---

### Post by Vaphell on 2013-03-24
for gods sake  never eval user input.

what if someone types
```
; rm -rf ~
```
?

stick to ${path/#\~/$HOME}

---

### Post by schragge on 2013-03-24
:oops: You are right. Then maybe do it like this:
```

IFS=';&|()`'
read -ep '> ' path junk
path=$(eval echo $path)
echo $path

```:?: I see why this is suboptimal and rather fragile as it would break on paths containing characters listed in $IFS, but at least the full semantics of ~ would be preserved.

[highlight]Update.[/highlight]
After giving it some more thought, now I guess the most prudent way would be using the *case* statement:
```

#!/bin/sh
LC_ALL=C # for [a-z] to work as expected
test -n "$1" && path=$1 || read -p '> ' path
case $path in ~*)
 pfx=${path%%/*}; tag=${pfx#\~}; tail=${path#$pfx}
 case $tag in
  '')  path=$HOME$tail;;
  +) path=$PWD$tail;;
  -) test -n "$OLDPWD" && path=$OLDPWD$tail;;
  [a-z_]*) passwd=`getent passwd "$tag"` && pfx=${passwd%:*}&&path=${pfx##*:}$tail;;
# Some custom shortcuts
  DC) path=$HOME/Documents$tail;;
  DL) path=$HOME/Downloads$tail;;
  DT) path=$HOME/Desktop$tail;;
  ML) path=$HOME/Mail$tail;;
  MU) path=$HOME/Music$tail;;
  PC) path=$HOME/Pictures$tail;;
  PB) path=$HOME/Public$tail;;
  TL) path=$HOME/Templates$tail;;
  VD) path=$HOME/Videos$tail;;
  CF) path=$HOME/.config$tail;;
  LC) path=$HOME/.local/share$tail;;
  MD) path=/media$tail;;
 esac
esac
echo $path

```
The same in bash
```

#!/bin/bash
LC_ALL=C # for [a-z] to work as expected
shopt -s extglob # for $DIRSTACK
declare -A shortcuts
shortcuts=(
 [DC]=Documents [DL]=Downloads [DT]=Desktop [ML]=Mail [MU]=Music
 [PC]=Pictures [PB]=Public [TL]=Templates [VD]=Videos [CF]=.config
 [LC]=.local/share
)
[[ -n $1 ]] path=$1 || read -ep '> ' path
if [[ $path == ~* ]]; then
 pfx=${path%%/*}; tag=${pfx:1}; tail=${path#$pfx}
 case $tag in
 '') path=$HOME$tail;;
 +) path=$PWD$tail;;
 -) [[ -n $OLDPWD ]] && path=$OLDPWD$tail;;
 ?(+|-)+([0-9])) path=${DIRSTACK[$tag]}$tail;;
 DC|DL|DT|MU|PC|PB|TL|VD|CF|LC) path=$HOME/${shortcuts[$tag]}$tail};;
 MD) path=/media$tail;;
 [a-z_]*) ifs=$IFS;IFS=:; passwd=(`getent passwd "$tag"`)&&path=${passwd[5]}$tail; IFS=$ifs;;
 esac
fi
echo $path

```

---

### Post by gandalf3 on 2013-03-28
:shock: That is a LOT of stuff... for something as seemingly simple as makeing "~" work in the read command..
(i see the problem though.. there seems like there ought to be some way to eval just the tilde?)

im currantly sticking to


```
path=${path//\~/$HOME}
```

because it's in a situation where the user is unlikely to use ~ for anything other than $HOME.. 
good to know though, i'll keep it in mind for future use..

EDIT:

wow
I didn't realize bash and sh were that different!

---

### Post by Vaphell on 2013-03-28
sh is more suited for barebone stuff, like running system scripts that are relatively simple and using bash on them would just waste resources. Bash offers goodies that are more useful in userspace scripts. Some people even think bash is bloated ;-)

*path=${path/#\~/$HOME}* should be good enough in most cases (# forces the pattern to match from the left so eg file~ wont get a substitution). If you think user can have a file with ~filename, you could try doing a test if the file/dir with that exact name exists. If not, assume he meant $HOME and do a replacement, eg
```
[ -e "$path" ] || path=${path/#\~/$HOME}
```

---

### Post by gandalf3 on 2013-05-21
I found that it was just easer to do without the read command, instead have a command line argument. now the shell just expands it automatically before the script even gets a hold of it :) thanks

---

