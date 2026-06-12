---
title: "[SOLVED] sh Shell: loop through and run system commands stored in array"
date: 2008-08-01
forum: Programming Talk
---

### Post by munkyeetr on 2008-08-01
I am pulling my hair out! Let me start with that, and get to the point.

I have an array which holds commands I would like to run from my shell script. (Note that I have been trying so many different things this afternoon that the array may not even be constructed correctly anymore :confused: Sometimes I run the script with the looping code commented out, and the commands still run, so I have probably done something wrong)
```

declare -a commands
commands=( "`uptime > system-uptime`"
	   "`dpkg --get-selections | grep -v deinstall > installed-packages`"
	   "`ps aux > system-processes`"
	   "`fdisk -l > system-fdisk`"
	   "`df -l > system-df`"
	   "`lspci > hardware`" )

```

So I want to store these commands in the array, then loop through it and run them. I want the output files from these commands to be stored in a specific directory, which is stored in the variable ${dest} which is always /tmp/<date>/reports/

```

#-----------------------------------------------------------------
# Create Master Backup files in /tmp/<date> directory
#-----------------------------------------------------------------
	target=/tmp/`date +%m-%d-%y`
	mkdir -p ${target}

#-----------------------------------------------------------------
# Run any system commands, reports, etc...
#-----------------------------------------------------------------
# If there are commands to run, create a 'reports' directory
	if [ ${#commands[@]} -gt 0 ]; then
		dest=${target}"/reports"
		mkdir -p ${dest}
                cd ${dest}
# and run the commands
		for cmd in ${commands[@]}
		do
			${cmd}
		done
	fi

```

My thinking says that because I have used **cd ${dest}** and am now working from that directory, that when the commands run, they should create the output files there. However, they create the files in the directory containing the script, which is not what I need.

Obviously my thinking is skewed right now. Can anyone offer some assistance and/or advice?

---

### Post by ghostdog74 on 2008-08-01
why the need to keep an array of commands ?
```

#-----------------------------------------------------------------
# Create Master Backup files in /tmp/<date> directory
#-----------------------------------------------------------------
    target=/tmp/`date +%m-%d-%y`
    mkdir -p ${target}

#-----------------------------------------------------------------
# Run any system commands, reports, etc...
#-----------------------------------------------------------------
# If there are commands to run, create a 'reports' directory
    if [ ${#commands[@]} -gt 0 ]; then
        dest=${target}"/reports"
        mkdir -p ${dest}
              
# and run the commands
       uptime > ${dest}/system-uptime
       dpkg --get-selections | grep -v deinstall > ${dest}/installed-packages
       ps aux > ${dest}/system-processes
       fdisk -l > ${dest}/system-fdisk
       df -l > ${dest}/system-df
       lspci > ${dest}/hardware
    fi

```

---

### Post by munkyeetr on 2008-08-01
because it's a backup script that i want people to be able to just plug variables into in order to customize to their needs. part of that is offering them a single place to put all the system commands they want to run, and then letting the script take care of it for them.

so with an array, one command per index, should be fairly straightforward i would think.

and yes, i could (and they could) just plug them in where you have suggested, but that doesn't answer my question. if anything, it's good for learning.

any ideas?

---

### Post by munkyeetr on 2008-08-01
And even to edit it like ghostdog74 suggested doesn't work. I still cannot get the output files to go into /tmp/<date>/reports; they only write to the directory that contains the script.

And I don't think it is a permissions issue, I am running the script as root.

---

### Post by mssever on 2008-08-01
I'm pretty sure that your commands are getting run when the array is created, not when the loop is running. Try protecting them with single quotes and see if that helps. Also, it can help in debugging if you echo your array.

---

### Post by ghostdog74 on 2008-08-01
try declaring your destination before commands array, then defining the destination 
eg
dest=blah
commands = ( `uptime ...` > ${dest}/system-process 
...
..)

---

### Post by munkyeetr on 2008-08-01
> **mssever said:**
> I'm pretty sure that your commands are getting run when the array is created, not when the loop is running. Try protecting them with single quotes and see if that helps. Also, it can help in debugging if you echo your array.

That has definitely been happening sometimes. I have tried single quotes, double quotes, no quotes, just the ` ` type of quotes...same problem.

> **ghostdog74 said:**
> try declaring your destination before commands array, then defining the destination 
eg
dest=blah
commands = ( `uptime ...` > ${dest}/system-process 
...
..)

The destination declaration and the looping are performed inside a function. The array is declared outside of the function.

But as I say, even if I completely comment out the array and just hard code in the commands, it still won't output them into the /tmp/<date>/reports directory, only into the directory where the script resides.

The script is working (in a sense), it's just not writing them where I want them. If you want I can post the whole script, though it's quite long. What I've been writing today is a refinement and adding of options to an original Backup script. And even with the other, which didn't use an array to hold these commands, I couldn't write them directly into the /tmp path. I had to create them in the current directory, then mv them into the /tmp path. I am hoping to clean that up, because I don't like it. It's sloppy.

---

### Post by unutbu on 2008-08-01
```
#!/bin/sh

declare -a commands
commands=( 
    'uptime > system-uptime' 
    'dpkg --get-selections | grep -v deinstall > installed-packages' 
    'ps aux > system-processes' 
    'fdisk -l > system-fdisk' 
    'df -l > system-df' 
    'lspci > hardware' )

# #-----------------------------------------------------------------
# # Create Master Backup files in /tmp/<date> directory
# #-----------------------------------------------------------------
	target=/tmp/`date +%y-%m-%d`
	echo "$target"
 	mkdir -p ${target}

# #-----------------------------------------------------------------
# # Run any system commands, reports, etc...
# #-----------------------------------------------------------------

if [ ${#commands[@]} -gt 0 ]; then    # I'm not sure if this is really necessary
    dest=${target}"/reports"
    mkdir -p ${dest}
    cd ${dest}
    for ((i=0;i<${#commands[@]};i++)); do
	echo ${commands[${i}]}
	eval ${commands[${i}]}
    done
fi

```

---

### Post by munkyeetr on 2008-08-01
unutbu: THANK YOU. Worked perfectly.

Also:
```

if [ ${#commands[@]} -gt 0 ]; then    # I'm not sure if this is really necessary

```
it is necessary for the overall script because if a particular user doesn't want to run any reports during their backup, they can leave the array empty and it will be skipped over. There's basically a whole section where the user sets their options, then the script runs and acts on those options.

---

