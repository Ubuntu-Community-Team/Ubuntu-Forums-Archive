---
title: "expansion of $@ in a script"
date: 2013-03-07
forum: Programming Talk
---

### Post by jamesbon on 2013-03-07
I have come across a small script as follows

```


declare -a args=( [COLOR=#800000]"$@"[/COLOR] ) echo ${#args[@]}  [COLOR=gray]#
[/COLOR]
```

this is being run as 
bash demo1.sh *.pdf

where it is being checked how many pdfs are there in the directory.

I read the man page of bash which says
>  An indexed array is created automatically if any variable is assigned to using the syntax name[subscript]=value.  The subscript is  treated
       as  an  arithmetic  expression  that must evaluate to a number.  If subscript evaluates to a number less than zero, it is used as an offset
       from one greater than the array's maximum index (so a subcript of -1 refers to the last element of the array).  To  explicitly  declare  an
       indexed  array,  use  declare  -a  name  (see SHELL BUILTIN COMMANDS below).  declare -a name[subscript] is also accepted; the subscript is
       ignored.




I am not clear with 2 things
```


declare -a args=( [COLOR=#800000]"$@"[/COLOR] ) 
```what does this means? and what it gets evaluated to what does ("$@") mean and in the second line what does ```
 echo ${#args[@]}  [COLOR=gray]#[/COLOR]
```
gets expanded to?what is meant by ${}and args[@] expands to what

---

### Post by steeldriver on 2013-03-07
The @ mean different things depending on the context[FONT=courier new]

args=( "$@" )[/FONT] constructs an array called args from the script's argument list $@

See [http://tldp.org/LDP/abs/html/internalvariables.html#APPREF](http://tldp.org/LDP/abs/html/internalvariables.html#APPREF)

[FONT=courier new]${#args[@]}[/FONT] is shorthand for the number of elements in the array called args

See [http://tldp.org/LDP/abs/html/arrays.html](http://tldp.org/LDP/abs/html/arrays.html)

---

### Post by Vaphell on 2013-03-07
in case one only wants to get the number of parameters, array is somewhat roundabout way to achieve that. The number of parameters script/function gets is directly accessible with $#

```
$ args() { echo $#; arg=( "$@" ); echo ${#arg[@]}; }
$ args *.sh
69
69
```

---

