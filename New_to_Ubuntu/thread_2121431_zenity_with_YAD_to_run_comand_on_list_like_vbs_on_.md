---
title: "zenity with YAD to run comand on list like vbs on windows"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by Froylan on 2013-03-01
in windows vbs you write the lavel(lets use 'x') and the result you want according of the result like 
```
if x=yes then
```
but i want to do something like this[ATTACH=CONFIG]239604[/ATTACH] note that I am yet to fully customize this script, please give me your example to run a command depending on the results of the given list, I am not sure if I was clear but it's my fault if you don't understand since I am not an english native speaker :P
thanks in advance

---

### Post by Froylan on 2013-03-01
I fixed it here is a post of the result after edited and corrected
```
action=$(yad --width 300 --entry --title "Anime navigation GUI" \
    --image=gnome-shutdown \
    --button="ok:2" --button="cancel" \
    --text "select anime:" \
    --entry-text \
    "hyouka" "beelzebub" "Blassreiter" "hellsing Ultimate")
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
    GTFO*)
        case $(wmctrl -m | grep Name) in
            *Openbox) cmd="openbox --exit" ;;
            *FVWM) cmd="FvwmCommand Quit" ;;
            *Metacity) cmd="gnome-save-session --kill" ;; 
            *) exit 1 ;;
        esac
        ;;
    *) exit 1 ;;        
esac

eval exec $cmd
```

---

