---
title: "Bash programing isue"
date: 2015-04-04
forum: Programming Talk
---

### Post by ethan26 on 2015-04-04
Hi people, i am new to this form as this is my first post on this fourm or any other fourm for that matter but i find fourms useful when learning new programing launguages and so to get to the problem i am having:
I am atempting to write a code that will echo a random number untill a key is pressed. When a key is pressed it should echo on the same line DONT TOUCH THE KEYBOARD. its not going well. so far i have this:
```
&#65279;#!/bin/bash
while true; do 
while true; do echo -n $RANDOM; & read -n1 -s VAR
echo "DONT TOUCH THE KEYBOARD"
```
to break down what i was trying to do the while true; do was supost to echo $RANDOM forever untill a key was pressed then the & was supost to execute the two commands (do echo -n $RANDOM and read -n1 -s VAR) at the same time. If any key was pressed the read command would break and it would echo DONT TOUCH THE KEYBOARD. now that i look at the code again i realize that i should have added the -n option to the echo command and made a loop around all of it but if you guys could help me out i would really apriciate that.
Thanks

---

### Post by bardo2 on 2015-04-05
in my own understanding, the choice to use bash for that purpose is a weird one. Bash is not a programming language, it is a shell scripting language, best used to glue a couple of commands into a script.

That said, first thing to investigate/learn, i'd suggest the trap command, which prevents unexpected interruption of the script. i frequently use it to clean up after something got interrupted, but you can also just ignore events.

Next, read (a.k.a. readline) doesnt see keypresses, only waiting for a line terminator. I am certain, there will be some alternative too, but let's be clear: nothing is ever going make bash a good choice for the purpose. If you were my son, i'd recommend to have a look at python, which can be easy as "BASIC" used to be, yet modern (object-oriented), versatile (nothing you couldnt do with it), and very many libraries around to make your task easier by incorporating other peoples work.

just my 2 cents

---

### Post by ethan26 on 2015-04-05
Thanks for your input. I have a freind who knows python and im shure he could help me to learn it. But does python require dowloading somthine special to run the program because I want to avoid that at all costs. Wich is why I havent learned java. so what would you sugest bash for?
thanks again!

---

### Post by bardo2 on 2015-04-05
on most 'nix standard installs (you didnt mention yours), there is some version of python already installed, especially in ubuntu, because parts of ubuntu are effectively written in python. You can check by issuing
```
python -V
```
from a commandline

---

### Post by ethan26 on 2015-04-05
I just checked the command you gave me and i got
```
*****@*****-E6610:~$ python -V
Python 2.7.6
```
wich means that i do have python installed! :KS
also my computer is runing ubuntu 14.04 LTS
and what is the extention for puthon script (the equivelent of .sh to be clear
and how would you write this type of script in python.
thanks

---

### Post by bardo2 on 2015-04-05
ask google, it turned up plenty of examples

---

### Post by ethan26 on 2015-04-05
ok

---

### Post by ethan26 on 2015-04-05
I like the input that have given me but you still did not answer my original question or provide any help about the code that i provided. i do apriciate you taking your time and responding but I was really looking for help with bash not python.
thanks, and happy easter!:p

---

### Post by bardo2 on 2015-04-05
??? read again my post #2

edit: i use keywords "bash keypress" and find answers right away, you should be more involved. complaining wont help

---

### Post by ethan26 on 2015-04-05
sorry, didnt understand what you were saying at the time. i thought you were giving commands in python to test.

---

### Post by bardo2 on 2015-04-05
it's ok.
again, if you were my son, i'd say: "you seem to be interested in playing a song. That is nice. But up till now, you are using the drums only. But maybe, to learn the piano is too difficult on your own. I understand that. Go get a teacher (which i am not)."

---

### Post by ethan26 on 2015-04-05
coincidentely i do play the piano

---

### Post by bardo2 on 2015-04-05
great! :KS

---

### Post by ethan26 on 2015-04-05
im going to leave this thread open as i am open to sugestions

---

### Post by bardo2 on 2015-04-05
very happy to have seen this: [http://ubuntuforums.org/showthread.php?t=2272247]("http://ubuntuforums.org/showthread.php?t=2272247")
indicating, you found an excellent way to make progress.

Well done!

---

### Post by steeldriver on 2015-04-05
Not sure exactly what you're looking for, but based on your attempt to use a while loop in your original post, perhaps something like this?

```

#!/bin/bash

msg='DON'\''T TOUCH THE KEYBOARD'

while : 
do 
  if read -s -t1 -n1 input; then 
    printf "%s\r" "$msg"
  else 
    printf "%-*s\r" "${#msg}" "$RANDOM" 
  fi
done

```

I'll leave you to study it - you should find

```

help read

help printf

man 3 printf

```

useful.

---

### Post by ethan26 on 2015-04-05
Thanks this is basicly what i was hoping for however i wanted th output to look somthing like

```
641323118328764317907212711766144291401910961230119651209021282711618899822853425288201127263261840111652952147591000226889932317115224481215473525
629190207944811812410302895270216961477728622259002892993794312109024502229022862910617305101894024539221142530081603065895892963032734662028400356
230516826294012031313057110943110316939277422392118218297911188514491270932188828867203331827513812822717657286701604191249820394817409192376279682
966629622617540981337314624419629152297831671215296245911396528102624131180323379798660822634298682616517085201481791818052200931865921591225192891
759661196923503139481392128680302332426837314372008716126215711483030928251712320030869901555098972697750341986712398250828062498184892710124070101
6713525177671628623315205060330799167534248139482025111777576588831529DONT TOUCH THE KEYBOARD832363218095122191992151981584725026929422935166
565877265183133317040224202270420555411017083217881605957972163392451287313491927860401119377032183727890167932455521162992718138203605942690532137
314231266231812129221687125917983410123134752702732917130132861922932323667202081646427290192833203312461241821330238612490319460265171579091023135
327056219731464979051053227251015412002162098034213826333768104762173920010221781712327159120665982314171041223016064300665342167722022210802574311
```
But thank you so much. i am doing homework but when i am done i will tweak the code and post it back here
thank you again. this forum is so helpful!
and to [ 						 							]("http://ubuntuforums.org/member.php?u=1975410")[**[COLOR=#000000]bardo2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1975410"):
i am so glad you endorse my efort to engage the commutiy to help me learn python. in all honisty i was hesitant to post that tread as i thought that you would get mad if you saw it.
Thanks to all and happy easter!:p

---

### Post by ethan26 on 2015-04-05
ok so i edited it and got this
```
#!/bin/bash

msg='DON'\''T TOUCH THE KEYBOARD'

while : 
do 
  if read -s -t1 -n1 input; then 
    echo "$msg"
  else 
    echo -n "$RANDOM" 
  fi
done
```
but it gives me this:
```
139721741720565DON'T TOUCH THE KEYBOARD
15329451820933107308571176093655807164332078772079110032224732423252521577462171526411493160166
```
if you could sho me how to make it echo the random number directly after $msg that would be terific!
except its a litte slow, lol. i need help with that too.
thanks in advance!

---

### Post by steeldriver on 2015-04-05
Did you read any of the documentation I suggested? 

Obviously I misunderstood what you meant by "on the same line" - you seem to have discovered the 'echo' command's -n option (although you could have simply removed the '\r' carriage return from the printfs), so think about how that affects your output

For the speed, I really do suggest you read the documentation for the 'read' built-in ('help read' - or 'man bash' if you want more detail) and make sure you understand the usage of its command line options

---

### Post by ethan26 on 2015-04-06
lol! i completely missed that! then when i tried to edit the code and took out the -t1 opyion it didnt work but i figured it out:
```
#!/bin/bash

while : 
do 
  if read -t0.02 -s -n1 input; then 
    echo -n "D"
    sleep 0.02
    echo -n "O"
    sleep 0.02
    echo -n "N"
    sleep 0.02
    echo -n "T"
    sleep 0.02
    echo -n " "
    sleep 0.02
    echo -n "T"
    sleep 0.02
    echo -n "O"
    sleep 0.02
    echo -n "U"
    sleep 0.02
    echo -n "C"
    sleep 0.02
    echo -n "H"
    sleep 0.02
    echo -n " "
    sleep 0.02
    echo -n "T"
    sleep 0.02
    echo -n "H"
    sleep 0.02
    echo -n "E"
    sleep 0.02
    echo -n " "
    sleep 0.02
    echo -n "K"
    sleep 0.02
    echo -n "E"
    sleep 0.02
    echo -n "Y"
    sleep 0.02
    echo -n "B"
    sleep 0.02
    echo -n "O"
    sleep 0.02
    echo -n "A"
    sleep 0.02
    echo -n "R"
    sleep 0.02
    echo -n "D"
  else 
    echo -n "$RANDOM" 
  fi
done
```
i figured i didnt need the hasle of the printf command and the apostraphe as i saw they would cause me trouble in the future
thank you all so much and i will leave this thread open for sugestions

---

### Post by ethan26 on 2015-04-06
Update:
i edited the code to make it look for the package beep and install it if need be and play fun beep sounds and i got this:
```
#!/bin/bash
echo "some of the commands used in this script reqire the sudo command witch requiers "$USER"s password"
PKG_OK=$(dpkg-query -W --showformat='${Status}\n' beep|grep "install ok installed")
echo Checking for stuff: $PKG_OK
if [ "" == "$PKG_OK" ]; then
  echo "No packege Setting up some stuff."
  sudo apt-get --force-yes --yes install beep
fi
sudo modprobe pcspkr
while : 
do 
  if read -t0.01 -s -n1 input; then 
    echo -n " "
    beep -f 200
    echo -n "D"
    beep -f 300
    echo -n "O"
    beep -f 400
    echo -n "N"
    beep -f 500
    echo -n "T"
    beep -f 600
    echo -n " "
    beep -f 700
    echo -n "T"
    beep -f 800
    echo -n "O"
    beep -f 900
    echo -n "U"
    beep -f 1000
    echo -n "C"
    beep -f 900
    echo -n "H"
    beep -f 800
    echo -n " "
    beep -f 700
    echo -n "T"
    beep -f 600
    echo -n "H"
    beep -f 500
    echo -n "E"
    beep -f 400
    echo -n " "
    beep -f 200
    echo -n "K"
    beep -f 300
    echo -n "E"
    beep -f 400
    echo -n "Y"
    beep -f 500
    echo -n "B"
    beep -f 600
    echo -n "O"
    beep -f 700
    echo -n "A"
    beep -f 800
    echo -n "R"
    beep -f 900
    echo -n "D"
    beep -f 1000
    echo -n " "
    beep -r 3 -f 200
  else 
    echo -n "$RANDOM"
    beep -l 15 -f 261.63 
  fi
done
```
and i love the result thanks to everyone who helped me on this thread and i hope to hear from you soon
thanks again!

---

### Post by bardo2 on 2015-04-07
cute drum solo there ;-)

...but...

a whole lot of things, that could be improved upon, but hey: that is how learning goes...

Just a few hints from me:
[LIST]
[*]use comments (you yourself might find them useful - or funny - later)
[*]it is considered bad style to incorporate a one-time installation into a (hopefully) many times to be called script - those are mostly kept separate - or to change a user systems config without his consent
[*]you could also straighten things somewhat (when you find many repetitions in a program, those give a clue for a higher abstraction level to be likely available)
[*]i am sure, you could even change the frequencies used by beep to make them play a bunch of real notes/a tune
[*]--force-yes is WAY too much (read the documentation/man apt-get) you would STOP a surgery, if you were asked: "you are about to cut into vital functions, do you want to continue anyway?"
[/LIST]

Still, hey! you are on your way discovering some of the things you can do with an Ubuntu system :-) =d>

---

### Post by ethan26 on 2015-04-07
Thank you for the input! the code i used for the installation was from the internet and all i did with that is change the packege name to beep so it would work for my perposes but i am going to make a song play and post it back here again!
if you have any song sugestions let me know.
thank you so much youve really been a big help!

---

### Post by fugu2 on 2015-04-07
you might also want to check out ```
http://stackoverflow.com/questions/5297638/bash-how-to-end-infinite-loop-with-any-key-pressed
```might help you along your way
However, I would add this to the top of that script```
trap "if [ -t 0 ]; then stty sane; fi" EXIT
``` so that if your script exits early, it will automatically make you stty sane again

---

### Post by ethan26 on 2015-04-07
Thank you but what do you mean by:
> so that if your script exits early, it will automatically make you stty sane again
thak you again

---

### Post by fugu2 on 2015-04-07
so the command ```
stty -echo -icanon -icrnl time 0 min 0
``` basically stops normal operation of pressing a key and printing a character. instead it can listen for keys to be pressed and make a decision based on if it detects a key pressed. if you didn't set it back to sane when your program ends, then you might notice non-normal behavior in the console (like no characters showing up when you type). when the script exits, you want to undo this non-blocking effect in the console. the "trap" command is useful for running something later when some condition is met, in our case when the program EXIT. when the program exits it will reset the blocking behavior of the console. You may have noticed the Crtl-C command already which will stop your script before it finishes. If you were to Crtl-C on  the middle of the demo script on stackoverflow, it would never execute the stty sane part of the script. the trap would make sure even if you exit early, it will still run stty sane.

---

