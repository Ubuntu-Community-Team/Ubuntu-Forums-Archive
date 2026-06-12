---
title: "Problem with alarm clock script"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Zukaro on 2013-05-09
I'm having trouble with my script; I'm trying to make an alarm clock which talks then randomly selects a song out of a set of 3 songs (it doesn't play all 3 but rather only the one that's been picked).  After playing the selected song I want it to play one last sound file then exit.
I have the talking part working, but when I run this the songs play in the order they're defined rather than randomized and the script gives the following error:

```
/home/zukaro/Scripts/alarm.sh: line 19: syntax error near unexpected token `fi'
/home/zukaro/Scripts/alarm.sh: line 19: `                                               fi'
```

I have tried to just call the songs in the if statement rather than defining them before hand and when I do that they don't even play in the first place.  I'm not sure what I'm doing wrong.

Here's the script:
```

killall mplayer

echo "Good morning, today is '$(date +%A,%B,%_d,%_Y)'.  It is '$(date +%_I,%_M,%_p)'." | festival --tts

RSELECT="$(shuf -i 1-3 -n 1)"
SONG1="$(mplayer /home/zukaro/Sounds/Space_Cruise.mp3)"
SONG2="$(mplayer /home/zukaro/Sounds/House.mp3)"
SONG3="$(mplayer /home/zukaro/Sounds/You_Get_What_You_Give.mp3)"

if [ "$RSELECT" == "1" ]; then
        $SONG1
        else
                if [ "$RSELECT" == "2" ]; then
                        $SONG2
                        else
                                if [ "$RSELECT" == "3" ]; then
                                        $SONG3
                                        else
                                                fi
                                fi
                fi
mplayer /home/zukaro/Sounds/Day/Day.ogg
exit

```

---

### Post by Maxital on 2013-05-09
Hey, you have one 'else' statement to much at line 18.

```

if [ "$RSELECT" == "3" ]; then
     $SONG3
     # line:18 - one to much 'else' statement.
fi

```


**Working code:**
```

killall mplayer

echo "Good morning, today is '$(date +%A,%B,%_d,%_Y)'.  It is '$(date +%_I,%_M,%_p)'." | festival --tts

RSELECT="$(shuf -i 1-3 -n 1)"
SONG1="/home/zukaro/Sounds/Space_Cruise.mp3"
SONG2="/home/zukaro/Sounds/House.mp3"
SONG3="/home/zukaro/Sounds/You_Get_What_You_Give.mp3"

if [ "$RSELECT" == "1" ]; then
    mplayer "$SONG1"
else
    if [ "$RSELECT" == "2" ]; then
        mplayer "$SONG2"
    else
        if [ "$RSELECT" == "3" ]; then
            mplayer "$SONG3"
        fi
    fi
fi
mplayer /home/zukaro/Sounds/Day/Day.ogg
exit

```



What happen is that it is trying to execute code where there is none, you could have added a statement between the '**else**' and '**fi**' like;

```

if [ "$RSELECT" == "3" ]; then
    mplayer $SONG3
else
    echo >/dev/null
fi

# if you do not add any code to execute there will be error, the else statement here would be
# used if for any reason shuf didn't write the value 1, 2 or 3, you could use it as;

if [ "$RSELECT" == "3" ]; then
    mplayer $SONG3
else
    echo "shuf values are not set to 1-3, shuf value maybe to high?"
fi

```

**Edit:** Allso each time you state SONG1="$(mplayer  /home/zukaro/Sounds/Space_Cruise.mp3)" it calls mplayer and plays it,  better to do it how i show it now, i whas in derp mode i guess,^^ just  woke up, yeah yeah, thats what happens when you(me) try running the code  in my head :P


Hope this shades some light on this matter, happy hacking :grin:

/Max

---

### Post by Zukaro on 2013-05-09
Thanks; I thought you always needed an else statement after an if statement, which is why I'd put that extra one (pretty new to scripting/programming (I don't actually know how to write any sorta scripts/programs in anything but bash)).  :P
Anyways, here's what the working script looks like.  It works perfectly now.  :3

Thanks for the help


```

killall mplayer

echo "Good morning, today is '$(date +%A,%B,%_d,%_Y)'.  It is '$(date +%_I,%_M,%_p)'." | festival --tts

RSELECT="$(shuf -i 1-3 -n 1)"
SONG1="/home/zukaro/Sounds/Space_Cruise.mp3"
SONG2="/home/zukaro/Sounds/House.mp3"
SONG3="/home/zukaro/Sounds/You_Get_What_You_Give.mp3"

if [ "$RSELECT" == "1" ]; then
        mplayer $SONG1
        else
                if [ "$RSELECT" == "2" ]; then
                        mplayer $SONG2
                        else
                                if [ "$RSELECT" == "3" ]; then
                                        mplayer $SONG3
                                        fi
                        fi
        fi
mplayer /home/zukaro/Sounds/Day/Day.ogg
exit

```

---

### Post by Maxital on 2013-05-09
hehe, fixed my post at same time i here ding new mail :P well all fixed now happy coding :)

Also good to know that you may get in trouble if the song name is "blabla some space in the name.mp3"  better to do

mplayer "$SONG1"

and so on, then it less derpy. Just so you keep that in mind if it goes poff :)

This is also way to do it, both do there job, i bet we could get some hardcore shell scripter(is that a word even) to show up and tell us how it should be done xD

```

SONG1="mplayer song1.ogg"
$SONG1

```

as you noted when you state 

SONG1="$(mplayer song1.ogg)"

You allso execute the stuff inside, this is good in someways depending what you want to do with it. In this case it was derpy like crazy

/Max

---

