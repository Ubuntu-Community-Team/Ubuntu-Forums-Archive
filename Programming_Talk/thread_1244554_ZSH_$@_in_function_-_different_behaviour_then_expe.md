---
title: "ZSH $@ in function - different behaviour then expected"
date: 2009-08-19
forum: Programming Talk
---

### Post by slakkie on 2009-08-19
Hello all,

I have the following case:

```

foo() {
   my_foo=$@

   for i in $my_foo ; do 
      echo $i
   done
}

```

I have this function defined in my .zshrc, when I do 

foo bla bla

The command executes and echo's 

bla bla

and not
 
bla
bla

When I put this function in a seperate script and put at the end:

foo $@

and call the script:

foo.sh bla bla

it echo's

bla
bla

How come the function sourced by my .zshrc doesn't work as expected? The same function in bash (also sourced from .bashrc) does work like intended.

---

### Post by DaithiF on 2009-08-19
Hi,
unlike bash, zsh doesn't split variables according to the IFS by default.  You can force it do it for a particular variable by saying:
${=variable}
so in  your example, 
for i in ${=my_foo}; do

you can also set a global option to make this the default behaviour - SH_WORD_SPLIT

as to why it works when you define the function & call from within a script -- well the only thing I can think of is that your script is actually getting run by bash rather than zsh?  If I try it in script under zsh I get the single line of output.

---

### Post by slakkie on 2009-08-19
Thnx for the SH_WORD_SPLIT, added this to my .zshrc and it is working like expected. 

The script where foo gets called it run as a zsh script, no #!, so it executes as zsh, bash, or whatever shell you are using atm. Just a file which is made executable.

I stand corrected, the file is run as a dash script, I've added the following:

echo `ps -p $$ | egrep -v "PID|TTY|TIME|CMD" | awk '{print $NF}' | sed -e 's/[^A-Za-z0-9]//g'`

Which then returns sh, which is a symlink to dash, when running the script with #!/usr/bin/env zsh it also prints bla bla on one line.

---

