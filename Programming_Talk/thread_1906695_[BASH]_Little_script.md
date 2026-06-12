---
title: "[BASH] Little script"
date: 2012-01-09
forum: Programming Talk
---

### Post by Tenshinkhan on 2012-01-09
Hey everyone,

I'm new here but propably I will becaome a solid member, so many useful things are here. I like it so much but never mind.

I have a problem with my absurdal script (need to make it work)

This error appear before -yesno dialog
So the error is ```
error syntax at line 39: unexpected end of file
```

and the code is ```

#!/bin/bash
plik="answer.$$"

dialog --title "Foldero tworzator" \
        --msgbox "Hello, press OK" 7 30 \
        --menu "pick 1 or 2" 13 60 6\
                1 "name1" \
                2 "name2" \
                3 "end" 2>$plik
                result=$?
                clear

odpowiedz=`cat $plik`

        if [ "$odpowiedz" = "1" ]; then
                dialog --yesno "wanna make folder called name1?" 10 50
                result=$?
                case $result in
                        0) mkdir /home/studinf/$USER/Desktop/name1 `date+%Y.%m.%d` ;;
                        1) echo "end" ;;
                        255) echo "[ESC] " ;;
esac

        if [ "$odpowiedz" = "2" ]; then
                dialog --yesno "Wanna make file called name2?" 10 50
                result=$?
                case $result in
                        0)mkdir /home/studinf/$USER/Desktop/name2 `date+%Y.%m.%d`;;
                        1) echo "end" ;;
                        255) echo "[ESC]" ;;
esac
        if [ "$odpowiedz" = "3" ]; then
                exit



esac
rm -f $plik


```

I'm new in programming so don't laugh please.

This script should in --menu ask and when you'll choose first answer it should ask with --yesno that you wanna make a file named with name1+actual date on desktop, and when you'll choose second option it should ask you to make file named with name2+date on desktop too. In third otion it should end dialog. I know it's stupid script but i need it and can't fix it alone so I'm asking You to help me :) I hope that somebody has understood what I tried to do.

If anyone could guide me or help with that script I will be very grateful.

BTW. Sorry for my english

~Tenshinkhan

---

### Post by sisco311 on 2012-01-09
Hi and welcome to the forums!

You didn't close any of your if statements. The syntax is:
```

if COMMANDS; then
    COMMANDS
**fi**

```

---

### Post by Tenshinkhan on 2012-01-10
thanks for answer but now have othher error...

```

syntax error near unexpected token newline'

line 24:   fi

```




```

#!/bin/bash
plik="answer.$$"

dialog --title "Foldero tworzator" \
        --msgbox "Hello, press OK" 7 30 \
        --menu "pick 1 or 2" 13 60 6\
                1 "name1" \
                2 "name2" \
                3 "end" 2>$plik
                result=$?
                clear

odpowiedz=`cat $plik`

        if [ "$odpowiedz" = "1" ] ; then
                dialog --yesno "wanna make file named name1?" 10 50
                result=$?
                case $result in
                        0) mkdir
/home/studinf/`whoami`/Desktop/name1 `date+%Y.%m.%d` ;;
                        1) echo "end" ;;
                        255) echo "[ESC] kliknales" ;;

                    fi

        if [ "$odpowiedz" = "2" ] ; then
                dialog --yesno "wanna make file named name2" 10 50
                result=$?
                case $result in
                        0)mkdir /home/studinf/`whoami`/Desktop/name2 `date+%Y.%m.%d`;;
                        1) echo "end" ;;
                        255) echo "[ESC] kliknales" ;;

                      fi

        if [ "$odpowiedz" = "3" ] ; then
                exit

                        fi




rm -f $plik


```

Any next tips or fixes?
I'm sick of that but this must be done for me ;/
I understand that propably I have stupid errors here, but I can't find all that things that's why I'm asking for a help

---

### Post by Vaphell on 2012-01-10
```
case ....
...
esac
```

besides use $() instead of `` and get used to quoting file names to prevent whitespace-induced disasters

---

### Post by Tenshinkhan on 2012-01-10
```

. / foldero.sh: line 19: date +% Y% m% d: command not found
. / foldero.sh: line 38: syntax error for unexpected token `esac '
. / foldero.sh: line 38: `esac
```


```

#!/bin/bash
plik="answer.$$"

dialog --title "Foldero tworzator" \
        --msgbox "Hello, press OK" 7 30 \
        --menu "pick 1 or 2" 13 60 6\
                1 "name1" \
                2 "name2" \
                3 "end" 2>$plik
                result=$?
                clear

odpowiedz=`cat $plik`

        if [ "$odpowiedz" = "1" ]; then
                dialog --yesno "wanna make folder called name1?" 10 50
                result=$?
                case $result in
                        0) mkdir /home/studinf/$USER/Desktop/name1`date+%Y.%m.%d` ;;
                        1) echo "end" ;;
                        255) echo "[ESC] " ;;
esac
fi

        if [ "$odpowiedz" = "2" ]; then
                dialog --yesno "Wanna make file called name2?" 10 50
                result=$?
                case $result in
                        0)mkdir /home/studinf/$USER/Desktop/name2`date+%Y.%m.%d`;;
                        1) echo "end" ;;
                        255) echo "[ESC]" ;;
esac
fi
        if [ "$odpowiedz" = "3" ]; then
                exit

esac
fi

rm -f $plik
```

any more help?

---

### Post by Lars Noodén on 2012-01-10
> **Tenshinkhan said:**
> any more help?

You might use an editor that helps with the indenting and syntax highlighting.  [emacs](http://www.gnu.org/software/emacs/tour/) will do that for you but you can also look at geany or kate.  They will be aware that you are making a shell script and manage the layout appropriately.

---

### Post by CoffeeRain on 2012-01-10
Yes, a good text editor would be good. As far as I can see, you have put an esac where there is no starting case. As for the date, there should be a space after the word "date." Right now, the program is trying to look for a command called date+%y.%m.%d instead of just date.

---

### Post by Tenshinkhan on 2012-01-10
> **Lars Noodén said:**
> You might use an editor that helps with the indenting and syntax highlighting.  [emacs](http://www.gnu.org/software/emacs/tour/) will do that for you but you can also look at geany or kate.  They will be aware that you are making a shell script and manage the layout appropriately.

Sry don't know what is it and how to use it. I don't have much time to learn that and mine trip with bash ends at that script. It's my first and last script in bash, because on other semesters on my studies we won't write in bash.

```

. / foldero.sh: line 40: syntax error for unexpected token `esac '
. / foldero.sh: line 40: `esac '
```

```

#!/bin/bash

NOWDATE=`date +%d%m%y`
plik="answer.$$"

dialog --title "Foldero tworzator" \
        --msgbox "OK" 7 30 \
        --menu "Wybierz na jakich zajeciach jestes" 13 60 6\
                1 "name1" \
                2 "name1" \
                3 "end" 2>$plik
                result=$?
                clear

odpowiedz=`cat $plik`

        if [ "$odpowiedz" = "1" ] ; then
                dialog --yesno "something with name1" 10 50
                result=$?
                case $result in
                        0) mkdir /home/studinf/`whoami`/Desktop/name1-$NOWDATE ;;
                        1) echo "end" ;;
                        255) echo "[ESC] " ;;
                        esac
                        fi

        if [ "$odpowiedz" = "2" ] ; then
                dialog --yesno "something with name2" 10 50
                result=$?
                case $result in
                        0)mkdir /home/studinf/`whoami`/Desktop/name2-$NOWDATE;;
                        1) echo "end" ;;
                        255) echo "[ESC]" ;;
                        esac
                        fi

        if [ "$odpowiedz" = "3" ] ; then
                exit
        esac
                        fi



rm -f $plik

```

I am so close to end that. This script is making already this folder in good localisation but after that im getting this error.

Anyone can see mistake? ;/

EDIT: 
> **CoffeeRain said:**
> Yes, a good text editor would be good. As far as I can see, you have put an esac where there is no starting case.

What do you mean exactly?

---

### Post by CoffeeRain on 2012-01-10
In
```

f [ "$odpowiedz" = "3" ] ; then
                exit
        esac
                        fi

```
You should delete that 'esac'. You have already closed the case.

---

### Post by Tenshinkhan on 2012-01-10
YEAH! now it work great!
You guys are awesome. Didn't even expected that somebody will answer me with that pointless script.

Thanks a lot guys :) how can I repay for that help? :)

---

