---
title: "Bash script read mouse events -- need help"
date: 2008-12-20
forum: Programming Talk
---

### Post by starcannon on 2008-12-20
[B]I'm putting this on the back burner, I will finally go ahead and learn a more readable language like Python; then, once I understand things a bit better, I will return to this script with knowledge that may help me better understand it. I don't know why, but this script fascinates me, I guess we all have our jumping off place, and this must be mine lol. 

Thanks for all the replies, hints, and pointers. Feel free to continue commenting if you like, but I will be absent from this thread as I am going to concentrate on Python.

Gratefully,
Rob
[/B]I'm going to be reading up on the **read** man pages; that said, I could really use some advice on how to use read to capture mouse events, as demonstrated (but not understood by me *yet*) in the script located at this URL [http://cfaj.freeshell.org/shell/scripts/mouse-demo-sh](http://cfaj.freeshell.org/shell/scripts/mouse-demo-sh)
The code from the given address is:
```

#!/bin/bash
# Mon Jan  5 10:59:00 EST 2004
# NAME: mouse-demo
# Copyright 2004, Chris F.A. Johnson
# Released under the terms of the GNU General Public License

about() #== Information about mouse-demo
{
    cat <<EOF
          ${B}mouse-demo${U}
 
              A bash script that can be controlled entirely with the
              mouse.
 
          Requires: bash 2.0x or greater, ANSI/xterm window
 
          Author: Chris F.A. Johnson
 
          Date: 5 January 2004
 
          Copyright 2004 Chris F.A. Johnson
          This program may be copied under the terms of the
          GNU General Public License, Version 2.
EOF
}

clear_body()
{
    printat $(( $bar_line + 2 )) 1 "${NA}${cles}"
}

help()
{
    local n=0
    clear_body
    while [ $n -lt ${#button_cmd[@]} ]
    do
      printat $(( $n + $bar_line + 2 )) 1
      printf "%15.15s %-10.10s - %s"  ${button_keys[$n]} "(${button_cmd[$n]})" "${help_strings[$n]}"
      n=$(( n + 1 ))
    done
}

now()
{
    local n=3
    local DATE YEAR MONTH DAY TIME HOUR MINUTE SECOND
    eval `date "+DATE=\"%c\" YEAR=%Y MONTH=%B DOW=%A DAY=%d TIME=%H:%M:%S HOUR=%H MINUTE=%M SECOND=%S"`
    printat $((n += 1)) 20 "       DATE: $DATE"
    printat $((n += 2)) 20 "       YEAR: $YEAR"
    printat $((n += 1)) 20 "      MONTH: $MONTH"
    printat $((n += 1)) 20 "        DAY: $DAY"
    printat $((n += 1)) 20 "Day of week: $DOW"
    printat $((n += 1)) 20 "       HOUR: $HOUR"
    printat $((n += 1)) 20 "     MINUTE: $MINUTE"
    printat $((n += 1)) 20 "     SECOND: $SECOND"
}

d2c () #== convert a decimal number to the corresponding ASCII character
{
    x=`printf "%x" $1`
    printf "%b" "\x$x"
}

set_chars() #== load string of all 255 chars from file (create if necessary)
{
    charfile=$HOME/.chars
    if ! [ -s $charfile ]
    then
      for c in `seq 1 255`; do
    [ $c -eq 127 ] && c=9  ## 0x7f causes problems
    d2c $c
      done > $charfile
    fi
    chars=$(< $charfile)
}

cls() #== clear screen
{
    printf "${CLS:=`clear`}"
}

printat() #== print arguments 3-... at Y=$1 X=$2
{
    [ $# -lt 2 ] && return 1
    local y=$1
    local x=$2
    shift 2
    local msg="$*"
    printf "${CSI}%d;%dH%b" ${y//[!0-9]} ${x//[!0-9]} "$msg"
}

index() #== index return position of STR2 in STR1
{
    local idx
    case $1 in
        *$2*)
            idx=${1%%"${2}"*};
            _INDEX=$(( ${#idx} + 1 ))
        ;;
        *)
            _INDEX=0
        ;;
    esac
}

mouse_info() #== print mouse press information
{
    local frmt="%16s %3d"
    clear_body
    xx=$(( $COLUMNS / 3 ))
    yy=3 ##$(( $LINES - 25 ))
    printat $((yy++)) $xx
    printf "$frmt" Button: $mouse_b
    printat $((yy++)) $xx
    printf "$frmt" Column: $mouse_x
    printat $((yy++)) $xx
    printf "$frmt" Row: $mouse_y
    printat $((yy++)) $xx
    printf "$frmt" "Mouse modifier:" $mouse_m
    printat $((yy++)) $xx "$cle"
    printf "Var. Length: B=%d X=%d Y=%d " ${#_MOUSE1} ${#_MOUSE2} ${#_MOUSE3}
    printat $((yy++)) $xx "$cle"
    printf "MOUSE1=%s MOUSE2=%s MOUSE3=%s " `ascii "$_MOUSE1$_MOUSE2$_MOUSE3"`
}

mouse_pos() #== convert character to mouse position
{
    local MOUSE=$1
    if [ "$MOUSE" = $'\x7f' ]
    then
      _MOUSE_POS=95
    elif [ "$MOUSE" = "\\" ]
    then
      _MOUSE_POS=60
    else
      index "$mouse_val_str" "$MOUSE"
      _MOUSE_POS=$_INDEX
    fi
}

read_mouse() #== decode mouse press information
{
    IFS= read -r -d '' -sn1 -t1 _MOUSE1 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE2 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE3 || break 2
    index "$mouse_val_str" "$_MOUSE1"
    mouse_b=$(( ($_INDEX & 3) + 1 ))
    mouse_m=$(( $_INDEX & (4 | 8 | 16) ))
    mouse_pos "$_MOUSE2"
    mouse_x=$_MOUSE_POS
    mouse_pos "$_MOUSE3"
    mouse_y=$_MOUSE_POS
}

get_key() #== store keypress from list of permissible characters
{
    local OKchars=${1:-"$allkeys"}
    local k
    local error=0
    local gk_tmo=${getkey_time:-${DFLT_TIME_OUT:-600}}
    local ESC_END=[a-zA-NP-Z~^$]
    mouse_x=0 mouse_y=0 mouse_b=0 mouse_line=0
    printf "$mouse_on"
    stty -echo
    while :; do
      IFS= read -r -d '' -sn1 -t$gk_tmo _GET_KEY </dev/tty 2>&1 || break
      index "$OKchars" "$_GET_KEY"
      if [ "$_INDEX" -gt 0 ]
      then
    case $_GET_KEY in
        ${ESC})
        while :; do
          IFS= read -rst1 -d '' -n1 k </dev/tty || break 2
          _GET_KEY=$_GET_KEY$k
           case $k in
              $ESC_END)
              [ "$_GET_KEY" = "$MSI" ] && { read_mouse; }
              break 2
              ;;
          esac
        done
        ;;
         *) break;;
    esac
      fi
    done
    printf "$mouse_off"
    return $error
}

button_widths() #== initialize width of buttons
{
    [ $verbose -gt 0 ] && {
    yy=6
    printat  $(( yy++ )) 1  " Configuring button widths:"
    printat  $(( yy++ )) 1  "     COLUMNS=$COLUMNS"
    }
    bnum=${#buttons[@]}
    bwidth=${buttons_width:=$(( $COLUMNS - 1 ))}
    button_width=$(( ($bwidth - $bnum) / $bnum ))
    button_junk=$(( $buttons_width - ( ($button_width + 1 ) * $bnum) + 1))
    local n=0
    while [ $n -lt $bnum ]; do
    pad=${spaces:0:$(( ($button_width - ${#buttons[$n]}) / 2 ))}
    [ ${#pad} -lt 0 ] && { printf ":$pad:\n"; break; }
    buttons[$n]=${pad}${buttons[$n]}${pad}
    [ ${#buttons[$n]} -lt $button_width ] && buttons[$n]="${buttons[$n]} "
    n=$(( $n + 1 ))
    done
    bk_list=${button_keys[@]}
    bk_list=${bk_list// /}
    [ $verbose -gt 0 ] && {
    printat  $(( yy++ )) 1  "     button_width=$button_width"
    printat  $(( yy++ )) 1  "     button_junk=$button_junk"
    printat  $(( yy++ )) 1  "     bk_list=$bk_list"
    printat  $(( yy += 2 )) 1  "     PRESS ANY KEY"
    read -sn1
    }
}

button_bar() #== print buttons
{
    button_width2=$(( $button_width + 1 ))
    cmd=99
    printat $bar_line ${buttons_left:-1} "$bar_attr$NA"
    printf "$bar_attr%${button_width}.${button_width}b$NA " "${buttons[@]}"
    printf "$cle"
}

highlight_button()
{
    local num=${1:-$cmd}
    good_button || return
    printat $bar_line $(( ($num % ${#buttons[@]}) * $button_width2 + $buttons_left ))
    printf "${highbar_attr}%${button_width}.${button_width}s${NA}" "${buttons[$num]}"
}

button_pressed() #== check whether press was in the button area
{
    [ ${mouse_x:-0} -ge ${buttons_left} ] &&
    [ ${mouse_y:-0} -eq $bar_line ] &&
    [ ${mouse_x:-0} -le $(( $buttons_left + $buttons_width )) ]
}

do_button()
{
    local cmd=${1:-$cmd}
    highlight_button $cmd
    printat $body_line 1 "${NA}${cles}"
    printat $body_line 1
    good_button || return
    case ${button_cmd[$cmd]} in
    exit) confirm_exit && exit ;;
    *) body_lines=$(( ${LINES:=24} - 4 ))
        ${button_cmd[$cmd]} | head -${body_lines#-}
    esac
    _DO_BUTTON=$cmd
}

good_button()
{
    local num=${1:-$cmd}
    [ $num -ge 0 ] && [ $num -lt ${#buttons[@]} ]
}

next_button()
{
    local num=${1:-$_DO_BUTTON}
    cmd=$(( (${num:-0} + 1) % ${#buttons[@]} ))
}

prev_button()
{
    local num=${1:-$_DO_BUTTON}
    cmd=$(( (${num:-0} + ${#buttons[@]} - 1) % ${#buttons[@]} ))
#    [ $cmd -lt  ] && cmd=1
}

confirm_exit()
{
    local _LAST_KEY=$_GET_KEY
    _DO_BUTTON=${cmd}
    clear_body
    printat $(( $bar_line + 2 )) 10 "${B}Exit [y/N]?${NA}${CVIS}\a "
    get_key "$alphanumeric" #"yYnNqQ$ESC$LF$RT$TAB"
    case $_GET_KEY in
    y|Y|q|Q) return 0 ;;
    $LF) prev_button ;;
    $RT) next_button ;;
    esac
    clear_body;printf "$CINV"
    _GET_KEY=$_LAST_KEY
    false
}

action()
{
    button_bar
    if button_pressed
    then
      cmd=$(( ($mouse_x - $buttons_left) / $button_width2 ))
    else
      case "$_GET_KEY" in
      $NL) printf "\a" ;;
      $MSI ) mouse_info; cmd=-1 ;;
      $TAB|$RT ) next_button ;;
      $LF) prev_button ;;
      [$bk_list]) index $bk_list $_GET_KEY
         [ $_INDEX -gt 0 ] && [ $_INDEX -le ${#buttons[@]} ] && {
         cmd=$(( $_INDEX - 1 ))
         }
         ;;
      e|q|x) confirm_exit && exit ;;
      esac
    fi
    highlight_button ##$cmd
    [ $cmd -lt 0 -a $cmd -ge ${#buttons[@]} ] && return
    [ "${button_cmd[$cmd]:-c}" = exit ] && confirm_exit && exit || do_button
}

cleanup() #== restore terminal
{
    trap 0
    button_bar
    stty $stty_orig
#    stty sane
    printf "%s${NL}${NL}${NL}${NL}" "$CVIS"
#    tput reset
    exit
}

trap "COLUMNS=`tput cols`;LINES=`tput lines`; cls;button_widths; button_bar" SIGWINCH

[ $verbose -gt 0 ] && printat 10 10 COLUMNS=$COLUMNS
verbose=0
COLUMNS=${COLUMNS:-`tput cols`}
LINE=${LINES:-`tput lines`}

case $1 in
    -v) verbose=1;;
esac

bra='['
ket=']'
ESC=$'\e'
NL=$'\n'
TAB=$'\t'
CSI=${ESC}${bra}
cle=${CSI}K
cles=${CSI}J
CVIS="${CSI}?25h"
CINV="${CSI}0;8m"
MSI=${CSI}M
NA=${CSI}0m
B=${CSI}1m
U=${CSI}0m
UP=${CSI}A
DN=${CSI}B
RT=${CSI}C
LF=${CSI}D
mouse_type[0]=${CSI}?9h     ## report mouse button press
mouse_type[1]=${CSI}?1000h  ## report mouse button press and release
mouse_on=${mouse_type[0]}
mouse_off=${CSI}?9l${CSI}?1000l
upper=ABCDEFGHIJKLMNOPQRSTUVWXYZ
lower=abcdefghijklmnopqrstuvwxyz
numeric=0123456789
alphanumeric=$upper$lower$numeric
spaces='                                                                   '
spaces=$spaces$spaces$spaces
CVIS=${CSI}?25h
CINV=${CSI}?25l
allkeys=$chars

trap "cleanup" 0
set_chars
mouse_val_str=${chars:32}
mouse_on=${mouse_type[0]}
cls

## commands to be placed in buttons
button_cmd=( cal df uptime who ps "ls -l" now help about exit )

## labels for button (customize if different from commands
buttons=( "${button_cmd[@]}" )

## keys for each button
button_keys=( c d u w p l n h a q )

## info to show with help command
help_strings=(
    "Display amount of free and used memory in the system"
    "Report filesystem disk space usage"
    "Tell how long the system has been running"
    "Show who is logged on"
    "Report process status"
    "Long listing of as many files as will fit on screen"
    "Display date and time information"
    "Help!"
    "About this script"
    "Exit"
)

bar_attr="${CSI}1;41;37m"
highbar_attr="${CSI}1;37;40m"

bar_line=1
body_line=$(( $bar_line + 2 ))
buttons_left=1
printf "$CINV"
button_widths
button_bar

stty_orig=`stty -g`
while :; do
  get_key "xe$bk_list$ESC$TAB$LF$RT"
  case $_GET_KEY in
#      $LF) printat 10 10 KEY=left;;
#      $RT) printat 10 10 KEY=right;;
#      q|exit) break ;;
      \?) help;;
  esac
  action
done
cleanup

``` If anyone can help shed light on how **read** works, and in particular, how it works in that script, I would be grateful for accelerating my learning. A simple "on mouse event echo message" example would likely help me a lot if anyone has time.

Off to read my man pages, bbl.

Thanks in advance for any advice or insight that can be leant to me :)

---

### Post by starcannon on 2008-12-20
Okay so far using a bit of trial and error, and a very very vague understanding of **read** I can now echo a message when I click the middle mouse button.
```

#!/bin/bash
read -r -d '' -sn1
echo "hello Mouse Button"

```So the question now is, why the middle mouse button? why not the left or the right or the scroll? further what are the set of single quotes doing?

I see that it says literally

**read** no new line continuation, terminate with input no new line, ' ' (space? or what?), after 1 input character, silently return.

I know I probably am not reading it correctly, and that on top of not fully understanding whats going on is going to exacerbate my ignorance. If anyone can bring it home for me I'd much appreciate your consideration and guidance.

Thanks some more :) 
Rob

---

### Post by jpkotta on 2008-12-21
The reason that the read man page didn't help is because read is a bash built-in.  You can get the documentation for it with
```
help read
``` or from the bash man page.  

read is used for getting input and storing it in bash variables.  

The reason why middle clicking works is because middle click pastes the X clipboard by default.  You have some data in the X clipboard, and the middle click writes it to the terminal.  It's exactly like typing, and has essentially nothing to do with the mouse, in the sense that the script doesn't know that it got the data via a mouse click or a keyboard stroke.

This is a very neat script, I didn't know that you could do that in bash.

---

### Post by starcannon on 2008-12-21
Excellent, and thank you for the insights jpkotta, the "help read" is a great tip, I had to google read and did find good information that way as well, but I particularly like starting with man pages in the terminal.

I did finally figure out why middle click was working, and was slightly discouraged when I discovered that it was not for the reasons I had initially thought.

I agree, the script is very cool, and the man that wrote it seems very brilliant; I googled his name and he seems to be a very interesting gentleman, he even has a book out.

I came back in to post a list of things I think may be useful for me to learn in order to better understand his mouse-demo script, I will post them in some code tags to make scrolling easier. Anything on the list that anyone is willing or has time to address will be very gratefully received, and I will continue googling and reading and checking back here every so often.

Here's my list
```

List of things to learn in so that I may better understand the mouse-demo.sh script:

case
local
the use of $trings and {urly braces
the use of $trings with addi+ion symbols and order of operations inside (urved braces what for instance is n=$(( n + 1 )) about?
bash flags of many sorts and combinations -lt for instance or -gt for another
How to use S[]uare braces, how to use them inside {urly braces, and with functions()
eval
printf
learn about the .chars file
shift
&
&&
return
full set of mathmatical operators
when is a / a slash, and when is it a mathmatical operator?
How is \ backslash used?
read
How to use p|pes inside ()'s for instance.. mouse_m=$(( $_INDEX & (4 | 8 | 16) ))
What does function "variable" do? for instance.. mouse_pos "$_MOUSE3"
How do I use || break, or || return? it appears to be involved with cases
How to understand something like this.. bnum=${#buttons[@]}
stty
tty
tput as well as tput reset
The full set of \commands \e for instance means ESCape?
When to use x="quotes" and when to use x='quotes' and when to use x=`hyphens` and when not to use anything x=nothing, particularly speaking of vars
how to use redirections like.. 2>&1 

```
Thanks again to anyone who has time and knowledge to help me on my way.
Rob

---

### Post by mssever on 2008-12-21
That's a long list of things to learn. I think you'd do well to study the [*Advanced Bash-Scripting Guide*]("http://tldp.org/LDP/abs/html/"). It's a detailed document, but you'll learn a lot.

---

### Post by starcannon on 2008-12-21
> **mssever said:**
> That's a long list of things to learn. I think you'd do well to study the [*Advanced Bash-Scripting Guide*]("http://tldp.org/LDP/abs/html/"). It's a detailed document, but you'll learn a lot.

Aye, I've been using it, as well as the [Bash Guide for Beginners]("http://tldp.org/LDP/Bash-Beginners-Guide/html/") , I only ask for additional help in the forums because I know that real world knowledge and experience can often times teach a point better than a book; just the same, I thank you heartily for your interest and consideration. 

I'm wading through **cases** in both guides, and have learned a bit about them, and have quite a bit more to learn of them yet. I'm also getting hints about certain variables. **IFS** for instance, when I saw that variable in the mouse-demo.sh script, I thought it was a variable name that the author of the script chose, then in my reading found out it is a particular variable with a particular use in **cases**, I got sleepy and so have not followed that rabbit down its hole yet.

Thanks and keep the comments and suggestions coming, I really do appreciate everything.
Rob

---

### Post by jpkotta on 2008-12-21
IFS is used not just with case statements, it is important for almost every part of bash.  It stands for Internal Field Separator.  When you present arguments to a command, function, control block, etc., it just sees text.  In order to break down a text string into separate words, bash looks for the characters in IFS to separate them.  Usually, IFS is whitespace, which is why you separate the arguments to a command with spaces.  In this case, IFS is the null string, and no word splitting occurs.

---

### Post by starcannon on 2008-12-21
ah ha ah, I see, IFS lets you use something other than default blank spaces as field separators, so
```
IFS=$'-'
```would for instance let me use a dash in place of what normally would have been white space.

I guess the next thing I need to understand is how, and why, this is useful.

I'm going to look at the IFS modifications made in that script and see if I can understand better what he was doing there. 

>  In this case, IFS is the null string, and no word splitting occurs.If you have time to expound on that a bit, I would find it very helpful.
```

    IFS= read -r -d '' -sn1 -t1 _MOUSE1 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE2 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE3 || break 2

```
So is this saying that _MOUSE1, 2, and 3 should be interpreted as though the space bar had been pressed?

Thank You very much jpkotta, everything is still hazy, but I'm starting to see shapes in the fog.

---

### Post by jpkotta on 2008-12-21
> **starcannon said:**
> 
If you have time to expound on that a bit, I would find it very helpful.
```

    IFS= read -r -d '' -sn1 -t1 _MOUSE1 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE2 || break 2
    IFS= read -r -d '' -sn1 -t1 _MOUSE3 || break 2

```
So is this saying that _MOUSE1, 2, and 3 should be interpreted as though the space bar had been pressed?

No.  AFAICS, the author has designed that read statement to never interpret any characters.  If IFS was not set to "", and the terminal got a TAB from the mouse (which is possible, the mouse is sending raw binary data), the TAB would be interpreted as a word delimiter instead of getting passed through to the _MOUSE? variable.

---

### Post by mssever on 2008-12-21
> **starcannon said:**
> Aye, I've been using it, as well as the [Bash Guide for Beginners]("http://tldp.org/LDP/Bash-Beginners-Guide/html/") 
Thanks for the heads up. I wasn't aware of that, and it seems to be more appropriate to refer beginners to than the Advanced Bash Scripting Guide. Bookmarked.

---

### Post by starcannon on 2008-12-21
> **jpkotta said:**
> No.  AFAICS, the author has designed that read statement to never interpret any characters.  If IFS was not set to "", and the terminal got a TAB from the mouse (which is possible, the mouse is sending raw binary data), the TAB would be interpreted as a word delimiter instead of getting passed through to the _MOUSE? variable.
That makes sense from what little I can understand of the mouse-demo script so far. He actually set the mouse button to respond as though it were any one of 32 characters in the ~/.chars file if I understand it correctly:
```
trap "cleanup" 0
set_chars
mouse_val_str=${chars:32}
mouse_on=${mouse_type[0]}
cls

```
Am I reading that about right?
Thanks again, and I've said it once, and I'm saying it again, we have the greatest forums going.

---

### Post by starcannon on 2008-12-22
Okay I've been reading and picking at this script a lot; and even if I don't figure it out right away, I'm learning an insane amount trying.

So what I've come up with so far is this:
He is using:
```

read -r #to grab the raw data, thanks jpkotta
printf %b #to poke an escape sequence into a variable

```
He is also using **IFS** and **VAR** both of which I am only aware of and have no understanding of. I am also struggling with how he is capturing the escape sequences, or whether I am even thinking about this in the right way.
My goal is to put together a script that will echo a message if I click the mouse on the terminal, once accomplished I will feel I have solved the puzzle I put before myself. I have a grand idea, but its not worth mentioning until I have solved this riddle first.

Thanks in advance again, for any help in picking this thing apart and grepping a command that will help me accomplish my goal.
Rob

---

### Post by starcannon on 2008-12-22
Okay maybe its not a false lead... When I run the script, the dump only happens after a mouse click no data is dumped when using the keyboard to navigate his menu system, I put the dump in the read_mouse() function after each IFS reassignment; further I am starting to see a bit better how cases work. If I understand correctly during read_mouse() IFS is being set to read raw data(from the mouse? how? it says /dev/tty... still lost on this matter), fed into _MOUSE? and then _MOUSE? is fed into case. Anyone who is following this thread, can you confirm or correct me where I have it right, and where I have it wrong?

Thanks again,
Rob

False lead for me I guess, looks like the octal dump I received is the default for $IFS; ah well, forging on, and continuing to learn.

Okay today I learned to do an octal dump, I had them written to a text file and set them up in various places all through the mouse-demo script, and here is what:
```
echo $IFS | od -bc
```dumped out:
```

0000000 012
         \n
0000001

```I believe 012 reperesents \n, however what do the 0000000 and 0000001 represent? Or better still how can I learn to understand it myself?

Thanks for any help on this or any of my other questions.

Rob

---

### Post by starcannon on 2008-12-22
I'm just going through and grabbing variable values to start trying to piece this thing together; there may be better ways of figuring things like this out, but I'm a complete noob so I'm just winging it.
I started monitoring mouse_pos() using 
```
echo $MOUSE >> ~/Robs-Projects/mouse_pos.txt
```I modified the code to look like this:
```

mouse_pos() #== convert character to mouse position
{
    local MOUSE=$1
    if [ "$MOUSE" = $'\x7f' ]
    then
echo $MOUSE >> ~/Robs-Projects/mouse_pos.txt
      _MOUSE_POS=95
    elif [ "$MOUSE" = "\\" ]
    then
echo $MOUSE >> ~/Robs-Projects/mouse_pos.txt
      _MOUSE_POS=60
    else
echo $MOUSE >> ~/Robs-Projects/mouse_pos.txt
      index "$mouse_val_str" "$MOUSE"
      _MOUSE_POS=$_INDEX
    fi
}

```And clicking around in the authors interface brings up different ascii characters, clicking in the same general area more than once will bring up the same character, even after clicking somewhere else, and the coming back to click in a same location. So its converting mouse movement to ascii characters, which is no secret in the script, he leaves some comments that say as much, this only shows what the characters are.

I am wondering now what character the left mouse button is being converted to, or if its being converted to an ascii char at all; I am trying to understand how he is getting mouse input to begin with, and so far am just seeing results of the mouse input; what I really am after is to know how mouse input being gathered.

Thanks for any help you can give.
Rob

---

