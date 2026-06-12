---
title: "Help with bash script to display xterm color escape sequences"
date: 2010-11-30
forum: Programming Talk
---

### Post by fhsm on 2010-11-30
I've been looking around at customizing my bash prompt and reading about how [colors]("http://www.funtoo.org/en/articles/linux/tips/prompt/") work in xterm. 

I found this list: ```
txtblk='\e[0;30m' # Black - Regular
txtred='\e[0;31m' # Red
txtgrn='\e[0;32m' # Green
txtylw='\e[0;33m' # Yellow
txtblu='\e[0;34m' # Blue
txtpur='\e[0;35m' # Purple
txtcyn='\e[0;36m' # Cyan
txtwht='\e[0;37m' # White
bldblk='\e[1;30m' # Black - Bold
bldred='\e[1;31m' # Red
bldgrn='\e[1;32m' # Green
bldylw='\e[1;33m' # Yellow
bldblu='\e[1;34m' # Blue
bldpur='\e[1;35m' # Purple
bldcyn='\e[1;36m' # Cyan
bldwht='\e[1;37m' # White
unkblk='\e[4;30m' # Black - Underline
undred='\e[4;31m' # Red
undgrn='\e[4;32m' # Green
undylw='\e[4;33m' # Yellow
undblu='\e[4;34m' # Blue
undpur='\e[4;35m' # Purple
undcyn='\e[4;36m' # Cyan
undwht='\e[4;37m' # White
bakblk='\e[40m'   # Black - Background
bakred='\e[41m'   # Red
badgrn='\e[42m'   # Green
bakylw='\e[43m'   # Yellow
bakblu='\e[44m'   # Blue
bakpur='\e[45m'   # Purple
bakcyn='\e[46m'   # Cyan
bakwht='\e[47m'   # White
txtrst='\e[0m'    # Text Reset
``` on the [Arch wiki]("https://wiki.archlinux.org/index.php/Color_Bash_Prompt") but wanted to find a way to show all possible options.

So I found this shell script ([pastebin]("http://pastebin.com/DUu2e3bM")): 
```

#!/bin/bash -
#===============================================================================
#
# FILE: colors.sh
#
# USAGE: ./colors.sh
#
# DESCRIPTION: Bash colors
#
# OPTIONS: —
# REQUIREMENTS: autogen
# BUGS: —
# NOTES: —
# AUTHOR: Amit Agarwal (AKA), amit.agarwal@amit-agarwal.co.in
# COMPANY: Individual
# VERSION: 1.0
# CREATED: 09/21/2009 06:12:07 PM IST
# REVISION: —
#===============================================================================
for c in `seq 0 255`;
do
    t=5;
    [[ $c -lt 108 ]]&&t=0;
    for i in `seq $t 5`;
    do
        #Display the codes also for easier lookup in terminal
        echo $i;${c}
        echo -e "\e[0;48;$i;${c}m|| $i:$c `seq -s+0 $(($COLUMNS/2))|tr -d '[0-9]'`\e[0m";
    done;
done

# setup_colors - Adds colors to array CC for global use
# 30 - Black, 31 - Red, 32 - Green, 33 - Yellow, 34 - Blue,
# 35 - Magenta, 36 - Blue/Green, 37 - White,
# 30/42 - Black on Green '30\;42'

function setup_colors() {
    declare -a CC;
    for i in `seq 0 7`;
    do
        ii=$(($i+7));
        CC[$i]="\033[1;3${i}m";
        CC[$ii]="\033[0;3${i}m";
    done;
    CC[15]="\033[30;42m";
    R=$'\033[0;00m';
    X=$'\033[1;37m';
    export R X;
}

function display_colors() {
    for i in $(seq 0 $((${#CC[@]} – 1))); 
    do 
        echo -e "${CC[$i]}[$i]\n$R"; 
    done
}

``` but it is well above my basy understanding.

When I run it I get a block of color and an error for each iteration of the loop. The output is: ```

|| 5:143 
5
colors.sh: line 27: 143: command not found
colors.sh: line 28: /2: syntax error: operand expected (error token is "/2")

``` where *|| 5:143* has a background color. 

I'm wondering if someone could help me understand how this shell script works & help get me point in the right direction to fix it.

---

### Post by m_duck on 2010-11-30
I apologise that I don't know what is wrong with the script you posted, however, here is another one (also from the Arch wiki) which does work (at least, on my Arch installs and an almost vanilla Ubuntu install):
```
#!/bin/bash
#
#   This file echoes a bunch of color codes to the 
#   terminal to demonstrate what's available.  Each 
#   line is the color code of one forground color,
#   out of 17 (default + 16 escapes), followed by a 
#   test use of that color on all nine background 
#   colors (default + 8 escapes).
#

T='gYw'   # The test text

echo -e "\n                 40m     41m     42m     43m\
     44m     45m     46m     47m";

for FGs in '    m' '   1m' '  30m' '1;30m' '  31m' '1;31m' '  32m' \
           '1;32m' '  33m' '1;33m' '  34m' '1;34m' '  35m' '1;35m' \
           '  36m' '1;36m' '  37m' '1;37m';
  do FG=${FGs// /}
  echo -en " $FGs \033[$FG  $T  "
  for BG in 40m 41m 42m 43m 44m 45m 46m 47m;
    do echo -en "$EINS \033[$FG\033[$BG  $T  \033[0m";
  done
  echo;
done
echo

```

I have also found that at times, it is useful to escape the colour sequences, though I cannot vouch as to why. So, for example, your 'txtred' may become:```
txtred="\[\e[0;31m\]
```Usually, the added '\[' and '\]' escape the colour sequences properly, meaning that bash doesn't start overwriting lines, though sometimes it just displays the extra charaters and I've no idea why.

---

### Post by fhsm on 2010-11-30
That's an interesting script. Thanks for posting it. 

I'd still be interested in someone explaining how the OP works.

Thx.

---

### Post by Arndt on 2010-12-01
> **fhsm said:**
> That's an interesting script. Thanks for posting it. 

I'd still be interested in someone explaining how the OP works.

Thx.

I don't know how it works, but I could repair it so it works. This line

 ```
       echo $i;${c}

```
needs to be

```
        echo "$i;${c}"
```

Then, the variable COLUMNS is apparently not exported from bash, so this script doesn't see it. One way to obtain it is to use the 'resize' command. But it's not critical, just write 40 in the appropriate place.

---

### Post by fhsm on 2010-12-01
Thanks for the tip. It looks like the only part of the file that really matters is:

```
for c in `seq 0 255`;
do
    t=5;
    [[ $c -lt 108 ]]&&t=0;
    for i in `seq $t 5`;
    do
        #Display the codes also for easier lookup in terminal
        echo -e "\e[0;48;$i;${c}m|| $i:$c `seq -s+0 $((40))|tr -d '[0-9]'`\e[0m";
    done;
done
```

This gives rows instead of a table but that's okay.

What's going on at```
[[ $c -lt 108 ]]&&t=0;
```?

How does a double bracket differ from a single bracket and why doesn't it include if,then,fi?

---

