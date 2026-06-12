---
title: "can someone explain to me this .sh file(uses YAD and zenity)"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-02
everything is important but what I most need is to know where the commands that tell the commands of the drop down menu start and end```
action=$(yad --width 300 --entry --title "Anime navigation GUI" \
    --image=/home/froylan/Pictures/11220.png \
    --button="ok:2" --button="cancel" \
    --text "select anime:" \
    --entry-text \
    "hyouka" "beelzebub" "Blassreiter" "hellsing Ultimate" "Kemeko Deluxe" "Angel Beats!" )
    ret=$?
[[ $ret -eq 1 ]] && exit 0

if [[ $ret -eq 1 ]]; then
vlc ~/Music/Tutturuu~.mp3
 exit 0
fi

case $action in
    hyouka*) cmd="vlc -f ~/anime/[Mazui]_Hyouka_[720p]" ;;
    beelzebub*) cmd="vlc -f ~/anime/Beelzebub" ;;
    Blassreiter*) cmd="vlc -f ~/anime/Blassreiter" ;;
    hellsing*) cmd="vlc -f ~/anime/Hellsing\ Ultimate" ;;
    Kemeko*) cmd="vlc -f ~/anime/[THORA]\ Kemeko\ DX" ;;
    Angel*) cmd="vlc -f ~/anime/Angel\ Beats!" ;;
    GTFO*)
esac

eval exec $cmd
``` the result of the sh file is this [ATTACH=CONFIG]239651[/ATTACH]

---

### Post by prodigy_ on 2013-03-02
Well, lines 1-6 are one huge command that create the GUI dialog and assigns the choice you made to the **$action **variable. The exit code is assigned to **$ret** (if you click cancel it'll be 1). 

```
[[ $ret -eq 1 ]] && exit 0 # stop execution and exit if "$ret" equals "1"

if [[ $ret -eq 1 ]]; then # double brackets are redundant, I'd use [ "$ret" -eq "1" ] instead
vlc ~/Music/Tutturuu~.mp3 # this will never be executed, guess why ;)
 exit 0
fi
```

The **case ... esac** block basically defines which command will be executed depending on the value stored in **$action**. Then **eval exec $cmd** executes the chosen command (stored in **$cmd**). This is also redundant, could execute right from the case construct.

---

### Post by Froylan on 2013-03-02
> **prodigy_ said:**
> Well, lines 1-6 are one huge command that create the GUI dialog and assigns the choice you made to the **$action **variable. The exit code is assigned to **$ret** (if you click cancel it'll be 1). 

```
[[ $ret -eq 1 ]] && exit 0 # stop execution and exit if "$ret" equals "1"

if [[ $ret -eq 1 ]]; then # double brackets are redundant, I'd use [ "$ret" -eq "1" ] instead
vlc ~/Music/Tutturuu~.mp3 # this will never be executed, guess why ;)
 exit 0
fi
```

The **case ... esac** block basically defines which command will be executed depending on the value stored in **$action**. Then **eval exec $cmd** executes the chosen command (stored in **$cmd**). This is also redundant, could execute right from the case construct.
thank you Mr.Prodigy, you have saved my day once more, you are a prodigy indeed

---

### Post by prodigy_ on 2013-03-02
You're welcome. :)

---

