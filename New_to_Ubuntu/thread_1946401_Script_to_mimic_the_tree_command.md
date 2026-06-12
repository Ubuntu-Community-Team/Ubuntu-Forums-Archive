---
title: "Script to mimic the tree command"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by demonkingj on 2012-03-24
So I am just wanting to mimic the tree command. 
sample:
```
/etc/gdm
|-- Init
| '-- Default
|-- PostLogin
| '-- Default.sample
|-- PostSession
| '-- Defaul t
|-- PreSession
| '-- Default
|-- Xses s ion
|-- failsafeBlacklist
|-- failsafeDexconf
|-- failsafeXServer
|-- failsafeXinit
‘-- gdm.schemas
4 directories, 10 files
```I am fairly new to scripting.
I understand I need to iterate through each directive. I found that typing ```
dir -B1 *path*
``` is what I need, but I can't really pin point each directory with that.

I have done my positional parameters if
```
mytree [blank] [ --help] [directory]
```if blank then search from current directory which I can check with pwd.
if --help, conditional statement to display help command and if chosen directory then just start at that directory.

I just don't know how to 'pin point' a directory then search through all it's directories, and so on.

I have been using [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php) and [http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html), but haven't seen anything that could help me.

---

### Post by Jest3r on 2012-03-24
Hello & Welcome,

  It sounds like you are replicating the functionally of the find command ( awesome, but complex command )

```

 $ find /etc/gdm -name Default
/etc/gdm/PreSession/Default
/etc/gdm/PostSession/Default
/etc/gdm/Init/Default

```

If you are looking to iterate (or loop) over a list of files in a  directories you can use the **for** command.

A very common pattern is for is the following...

```
$ for i in `ls /etc/gdm`
> do
> echo "Found file: $i"
> done
Found file: custom.conf
Found file: gdm.schemas
Found file: Init
Found file: PostLogin
Found file: PostSession
Found file: PreSession
Found file: Xsession

```

Is this what you are after ?

---

### Post by demonkingj on 2012-03-24
> **Jest3r said:**
> Hello & Welcome,

  It sounds like you are replicating the functionally of the find command ( awesome, but complex command )

```

 $ find /etc/gdm -name Default
/etc/gdm/PreSession/Default
/etc/gdm/PostSession/Default
/etc/gdm/Init/Default

```

If you are looking to iterate (or loop) over a list of files in a  directories you can use the **for** command.

A very common pattern is for is the following...

```
$ for i in `ls /etc/gdm`
> do
> echo "Found file: $i"
> done
Found file: custom.conf
Found file: gdm.schemas
Found file: Init
Found file: PostLogin
Found file: PostSession
Found file: PreSession
Found file: Xsession

```

Is this what you are after ?

thanks for the welcome and response.the find command does seem helpful, but wouldn't help me in this situation. I don't know the name of the file. 

The for command doesn't seem to work for me. It just outputs File found: ls /etc/gdm   it didn't work like what you posted.

But this is how it should be I will explain.

Begin to execute.
If no parameters start at current directory ( pwd ). Search through it's sub-directories, files, and then if there is another directory go into it's sub-directories. If that directories sub-directory has ended go to the previous directory and continue the whole process above.

Once no more files or directories are left. 
Tally up the total number of directories and files.

IF there is a parameter, path, then start at that path.

I just don't know the code to make this happen.

---

### Post by Jest3r on 2012-03-24
Is this what your after?

I created a script called "file_count.bash" with the following contents
```

#!/bin/bash
DIR=${1}||$PWD
find $DIR | wc -l

```

Giving the script an argument it counts all the files and directories for that directory
```

$ ./file_count.bash /etc/gdm/
12

```

With no argument it counts all the files and directories in the current directory ( or pwd )
```
$ ./file_count.bash 
123175
```

Sorry if I have misunderstood what your after.

---

### Post by demonkingj on 2012-03-24
> **Jest3r said:**
> Is this what your after?

I created a script called "file_count.bash" with the following contents
```

#!/bin/bash
DIR=${1}||$PWD
find $DIR | wc -l

```

Giving the script an argument it counts all the files and directories for that directory
```

$ ./file_count.bash /etc/gdm/
12

```

With no argument it counts all the files and directories in the current directory ( or pwd )
```
$ ./file_count.bash 
123175
```

Sorry if I have misunderstood what your after.

I am also trying to display the files as well, but wanting to assign each file or directory to a variable. 

So i can do this
variable = file/directory
if [ -d $variable]; then
    echo 'something'
elif [-f $variable]; then
    echo 'something else'

These if statements is to display a tree-like structure like the example post from the initial post

---

### Post by codemaniac on 2012-03-25
Hello demonkingj ,
Try the below script that would create a tree of directories under current directory .
 
```
#!/bin/bash

olddir=$PWD;
color="off";
for option in "$@"
do
    case $option in
        --color ) color="on";
              shift;;
        -*    ) shift;;
        *       )      ;;
    esac
done
declare -i stackheight=0;

function listf {
    cd "$1";
    for file in *
    do
        for ((i=0; $i < $stackheight; i++))
        do
            printf "\t";
        done
        if [ -d "$file" ]
        then
            if [ $color == "on" ]
            then
                printf "\e[34m";
            fi
        fi
        printf "$file\e[0m\n";
        if [ -d "$file" ]
        then
            stackheight=$stackheight+1;
            listf "$file";
            cd ..;
        fi
    done
    let stackheight=$stackheight-1;
}
listf "$1";
cd $olddir;
unset i color stackheight;
```

---

### Post by demonkingj on 2012-03-25
> **codemaniac said:**
> Hello demonkingj ,
Try the below script that would create a tree of directories under current directory .
 
```
#!/bin/bash

olddir=$PWD;
color="off";
for option in "$@"
do
    case $option in
        --color ) color="on";
              shift;;
        -*    ) shift;;
        *       )      ;;
    esac
done
declare -i stackheight=0;

function listf {
    cd "$1";
    for file in *
    do
        for ((i=0; $i < $stackheight; i++))
        do
            printf "\t";
        done
        if [ -d "$file" ]
        then
            if [ $color == "on" ]
            then
                printf "\e[34m";
            fi
        fi
        printf "$file\e[0m\n";
        if [ -d "$file" ]
        then
            stackheight=$stackheight+1;
            listf "$file";
            cd ..;
        fi
    done
    let stackheight=$stackheight-1;
}
listf "$1";
cd $olddir;
unset i color stackheight;
```

Thank you for the reply. Could you please explain this to me? I understand a good portion, but haven't seen some of this code like..
declare, i assume it "declares" variable '-i' is integer?
for option @ thing i don't understand at all
the case thing i am not sure about that either.
Unset i color as well.

---

### Post by Vaphell on 2012-03-25
"$@" means list of all supplied parameters 
that code block is supposed to recognize options and set things up. For loop iterates over the param list and case tests current option against --color, -<anything> and <anything> and does things.

```
#!/bin/bash

for option in "$@"
do
   case $option in
      --color ) echo "'$option' matches --color";;
      -*      ) echo "'$option' matches -*";;
      *       ) echo "'$option' matches *";;
    esac
done
```
test:
```
./args.sh --color --color-range -xyz 1 -t 2
'--color' matches --color
'--color-range' matches -*
'-xyz' matches -*
'1' matches *
'-t' matches -*
'2' matches *

```

What i find strange is the existence of shift there. I don't think it does anything in case of for loop.
Shift removes $1 from param list and other params move to the front ($2 becomes $1). It is usually used with while loop, you test against non-empty list, analyze $1 and then shift.
```

while (( $# ))
do
  echo "$# parameter(s) remaining"
  case $1 in
    --color ) echo "'$1' matches --color";;
    -*      ) echo "'$1' matches -*";;
    *       ) echo "'$1' matches *";;
  esac
  shift
done
```
```

./args2.sh --color --color-range -xyz '--color aaa' -t 2
6 parameter(s) remaining
'--color' matches --color
5 parameter(s) remaining
'--color-range' matches -*
4 parameter(s) remaining
'-xyz' matches -*
3 parameter(s) remaining
'--color aaa' matches -*
2 parameter(s) remaining
'-t' matches -*
1 parameter(s) remaining
'2' matches *

```
while seems more powerful. Let's say you use some option with *-switch value* combo. You can conveniently take care of (-switch) and following (value) at once which would be more complicated in for loop
```

-switch ) option_a=on; shift; option_a_param=$1;

```

---

### Post by codemaniac on 2012-03-26
Although rarely used, the bash declare statement does have a couple useful options. It can mark a variable as read only and also mark it as being a number only.

To declare a variable as read only, use the following statement:
```
declare -r varname
```

---

