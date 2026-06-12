---
title: "Make the terminal a friendly place; have it greet you!"
date: 2009-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by monsterstack on 2009-05-09
Perhaps you don't use the terminal so much because terminals aren't very friendly. Well then let's change all that. Let's make the terminal greet you. Let's make the terminal treat you like a princess.

This thread is for suggestions and ideas for making the terminal a more fun place to be. I hope you find something useful. If you want to learn how to customise your bash prompt with fancy colours and other fun things, check out MiCovran's [great thread]("http://ubuntuforums.org/showthread.php?t=614743") about it. This thread, though, is about having some fun with your terminal. You don't need to read this thread from start to finish, although reading the very basics can't hurt; beyond that just skip to whatever section takes your fancy.
[SIZE="4"]
**Contents.**[/SIZE]
[INDENT][LIST=1]
[*]Get to grips with your bashrc and create a simple greeting.
[*]Dynamic greeting messages.
[*]Greetings that are useful.
[*]Ascii pictures can greet you too.
[*]Dynamic ascii greetings.
[*]Let's geek it up with some Futurama ascii.
[*]Boring stuff: not essential to know, and not particularly fun, but useful all the same.
[*]More ideas from thread chit-chat.
[/LIST][/INDENT]

[SIZE="5"]
Part one: get to grips with your bashrc.[/SIZE]

There is a file in your home called ".bashrc". This file controls what happens whenever you open a bash session terminal. It can be used to do all sorts of things, but we're only interested in the silly things here.  It is worthwhile making a back-up of the basrc file, in case you do something horrible to it by mistake. To do that, just run this in your terminal:

```
cp .bashrc .bashrc.bak
```

I won't be telling you to change things around in your bashrc. Only to add a few things to the top of it. So if you do ruin things, just delete the additions you've made. Well now that's the safety briefing over and done with, go right ahead and start editing your bashrc with this command:

```
gedit .bashrc
```

It's worth giving yourself a bit of room to work with. Your bashrc won't break if you have lots of whitespace at the top of it, so feel free to push all that bash configuration down the page a bit. It'll help to separate your additions from the bulk of the technical gubbins. If you're a freak for neatness like me, it's possible to have all your bash-related additions in a completely separate file and have bashrc read it whenever you open a terminal. If you want to learn how to do that, go look at part seven: boring stuff.

To put in your custom message, just write an echo command at the very top of this file, something simple such as:

```
echo Hello!
```

Save and close. Now open a new terminal window and be amazed. It gosh darned greeted you!

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[SIZE="5"]
Part two: Dynamic greetings.[/SIZE]

So now your terminal greets you. But it's a bit wooden, don't you think? A little bit static, shall we say. Well, there are plenty of better things you can have your greeting be. Why not have it randomised each time? Let's have a thought-for-the-day type greeting. First make sure you have these packages:

```
sudo apt-get install fortunes fortunes-off
```

Now try running

```
fortune
```

to see a quote. Fortune has options too.

```
fortune -s   # for short quotes
fortune -l   # for long quotes
fortune -o   # for offensive quotes
```

You can combine those options a little, too. So for short, offensive quotes, go ahead and run

```
fortune -so
```

Not bad, eh? So put whichever one you prefer at the top of your bashrc file, save and close.

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[SIZE="5"]Part three: useful greetings.[/SIZE]

We can use command substitution to do a few fancy things with bash. Here is an example. Try running this command:

```
whoami
```

Well that makes sense. Let's try and incorporate it into our greeting with command substitution. Try running this:

```
echo "Hello $(whoami), today's thought is...\n $(fortune)"
```

Command substitutions are made by enclosing the command in brackets and adding a dollar sign to the beginning of them, as you can see. Also, the "\n" character tells the terminal to make a newline, which is helpful for breaking things up a bit.

Seeing as this is supposed to be the productive section of the howto, let's have a greeting that's actually useful. Let's use command substitution to tell you things about dates!

```
echo "Hello, $(whoami), today is $(date +%A)."
```

The date command has all kinds of options. You can see them all by running

```
date --help
```

You can have as many as you like in this command, too. How about this for instance,

```
echo "Hello, the time is $(date "+%k:%M, on %A, %d of %B, %Y.")"
```

Maybe you want something a bit more pleasant to look at. How about the "cal" application.

```
cal
```

This programme has options, too. Try running it as "cal -3", or "cal -y". Isn't it pretty! Add that to the top of your bash file and you'll never forget what day it is again!

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]


[SIZE="5"]Part four: ascii art to greet you![/SIZE]

There is an easter-egg in the application apt. Have a look for yourself:

```
apt-get moo
```

If you want to have a silly cow greet you, by all means put this command at the top of your bashrc. But there is a better way of doing it. Install this application:

```
sudo apt-get install cowsay
```

Now try running it with something you want to say,

```
cowsay Hello! I am awesome!
```

```

 ______________________
< Hello! I am awesome! >
 ----------------------
        \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

```

Now by using the -f option, you can choose other characters to greet you. Try out some of these:

```
cowsay -f tux "Hello I am groovy!"
cowsay -f sheep "Baaaaaaaa"
cowsay -f dragon "Rarr!"
```

To see all of the available options, run

```
cowsay -l
```

Once you've found one you like, go ahead and add it to the top of your basrc.

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[SIZE="5"]Part four: dynamic ascii art--fancy that.[/SIZE]

So you know how to have a random quote greet you. And you know how to have a funny ascii character greet you. Wouldn't it be great if you could have both? Well you can!

```
cowsay -f tux "$(fortune)"
```

```
 ____________________________________
/ To thine own self be true. (If not \
\ that, at least make some money.)   /
 ------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/

```

Now we're really getting somewhere! Combine some of the techniques we already know and we can do quite a few cool things. Let's try a few more commands!

```
cowsay -f dragon "Hello, the time is $(date "+%k:%M, on %A, %d of %B, %Y.")"
cowsay -f tux "$(fortune -so)"

```

Pretty cool. Maybe you would like one of these, hrmm?

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[SIZE="5"]Part six: let's geek it up with some Futurama ascii.[/SIZE]

Well, now we have lots of cool things for a fancy welcoming prompt. Let's try and incorporate the old geek-stable, Slashdot html-headers! You'll need an internet connection for this stuff, and faith in Slashdot's servers not exploding for some reason. First of all let's have a look at them:

```
curl -Is slashdot.org
```

If you look closely you'll see a random Futurama quote in there. Brilliant! We should use those for our greeting. And it turns out we can, by running the following command:

```
curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//'
```

which strips all the information except for the quote. Have a look at the "(F|B|L)" section. This part of the command dictates whether you receive a Fry, Bender, or Leela quote. At the moment it will get any of them, so for individual characters, you must run

```
curl -Is slashdot.org | egrep '^X-(F)' | sed 's/^..//'  # for Fry
curl -Is slashdot.org | egrep '^X-(B)' | sed 's/^..//'  # for Bender
curl -Is slashdot.org | egrep '^X-(L)' | sed 's/^..//'  # for Leela

```

Wouldn't it be awesome if we could use the ascii art from the cowsay application for these quotes? We could, but it might look a little odd:

```
cowsay -f tux "$(curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//')"
 ____________________________________
< Fry: I'll be whatever I wanna do.  >
 ------------------------------------
   \
    \
        .--.
       |o_o |
       |:_/ |
      //   \ \
     (|     | )
    /'\_   _/`\
    \___)=(___/
```

We're going to need some ascii art for Fry, Bender and Leela. Luckily for you, I'm going to give you [some]("http://www.gotfuturama.com/Multimedia/AsciiArt") [gotfuturama.com]. All you need to know is that cowsay uses cowfiles, which are stored in "/usr/share/cowsay/cows/"

For Fry,
```
gksudo gedit /usr/share/cowsay/cows/fry.cow
```
And paste the following into it:
```
the_cow = <<EOC;
   $thoughts
    $thoughts
             u
      .  x!X
    ."X M~~>
   d~~XX~~~k    .u.xZ `\ \ "%
  d~~~M!~~~?..+"~~~~~?:  "    h
 '~~~~~~~~~~~~~~~~~~~~~?      `
 4~~~~~~~~~~~~~~~~~~~~~~>     '
 ':~~~~~~~~~~(X+"" X~~~~>    xHL
  %~~~~~(X="      'X"!~~% :RMMMRMRs
   ^"*f`          ' (~~~~~MMMMMMMMMMMx
     f     /`   %   !~~~~~MMMMMMMMMMMMMc
     F    ?      '  !~~~~~!MMMMMMMMMMMMMM.
    ' .  :": "   :  !X""(~~?MMMMMMMMMMMMMMh
    'x  .~  ^-+="   ? "f4!*  #MMMMMMMMMMMMMM.
     /"               .."     `MMMMMMMMMMMMMM
     h ..             '         #MMMMMMMMMMMM
     f                '          (MMMMMMMMMMM
   :         .:=""     >       dMMMMMMMMMMMMM
   "+mm+=~("           RR     HMMMMMMMMMMMMM"
           %          (MMNmHHMMMMMMMMMMMMMMF
          uR5         dMMMMMMMMMMMMMMMMMMMF
        dMRMM>       dMMMMMMMMMMMMMMMMMMMF
       RMHMMMF=x..=" RMRMMMMMMMMMMMMMMMMF
      MMMMMMM       'MMMMMMMMMMMMMMMMMMF
     dMMRMMMK       'MMMMMMMMMMMMMMMMM"
     RMMRMMME       3MMMMMMMMMMMMMMMM
    XMMMMMMM>       9MMMMMMMMMMMMMMM~
   'MMMMMMMM>       9MMMMMMMMMMMMMMF
   tMMMMMMMM        9MMMMMMMMMMMMMM
   MMMMMMMMM        9MMMMMMMMMMMMMM
  'MMMMRMMMM        9MMMMMMMMMMMMM9
EOC

```

For Bender,
```
gksudo gedit /usr/share/cowsay/cows/bender.cow
```
And paste the following:
```

$the_cow = <<EOC;
   $thoughts
    $thoughts
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         $thoughts
|           |
|   .-------'._
|  / /  '.' '. $thoughts
|  $thoughts $thoughts @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """
EOC
```

For Leela,
```
gksudo /usr/share/cowsay/cows/leela.cow
```
And paste the following:
```
$the_cow = <<EOC;
             $thoughts
              $thoughts

                    '#%n.
            ..++!%+:/X!!?:              .....
              "X!!!!!!!!!!?:       .+?!!!!!!!!!?h.
              X!!!!!!!!!!!!!k    n!!!!!!!!!!!!!!!!?:
             !!!!!!!!!!!!!!!!tMMMM!!!!!!!!!!!!!!!!!!?:
            X!!!!!!!!!!!!!!!!!5MMM``""%X!!!!!!!!!!!T4XL
            !!!!!!!!!X*")!!!!!!!?L       %X!!!!!!!!!k `
           '!!!!!!X!`   !!XX!!!!!!L       'X!!!!!!!!!>
           'X!!!!M`    '" X!!!!!!!X        !!!!!!!!!!X
            X!!!f^~('>   X!!!!!!!!!        '!!!!!!!!!X
            X!!X     `.  X!!!!!!!!f        '!!!!!!!!!!
            !Xf  O    '  '!!!!!!X"         '!!!!!!!!!X
           "`f-.     :~  MX*t!X"           X!!!!!!!!!>
             >.         W! ~!             '!!!!!!!!!X
            :`             ':             X!!!!!!!!!!
            ~ ^`          '              '!!!!!!!!!X
            `~~~~~~~~     !              X!!!!!!!!!X
                `~~~      !             '!!!!!!!!!!>
                  >       !             (!!!!!!!!!X
                          !             !!!!!!!!!!X
                  >       '             '!!!!!!!!!!
                .:         /:`^-.        X!!!!!!!!!>
           /`  ~/         /(     `:       X!!!X!!!!!:
         /   : f         f'        !       `XX!M!!!!!%
        ~   / ~        :  >         4            "*!!!*
       ~   ~ '        ~   >          :
EOC
```

So now go ahead and try out your skills, run them to see if they work:

```

cowsay -f fry "$(curl -Is slashdot.org | egrep '^X-(F)' | sed 's/^..//')"
cowsay -f bender "$(curl -Is slashdot.org | egrep '^X-(B)' | sed 's/^..//')"
cowsay -f leela "$(curl -Is slashdot.org | egrep '^X-(L)' | sed 's/^..//')"
```

Now you may have noticed that the quotes don't always come through. That's mainly because there is only ever one quote in the headers at any one time. Searching for a Leela quote when there is only a Bender quote available will fail! Luckily, there is a way around this. What we need to do is search the headers for the quote, and then depending on whose quote it is, bring up the cowsay application accordingly. Well lucky for you I've already done it for you. Paste this code at the top of your bashrc:

```
function futurama() { wee=$(curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//'); if [[ $wee = "Fry"* ]]; then cowsay -f fry $(echo $wee | sed 's/^Fry: //'); fi; if [[ $wee = "Ben"* ]]; then cowsay -f bender $(echo $wee | sed 's/^Bender: //'); fi; if [[ $wee = "Lee"* ]]; then cowsay -f leela $(echo $wee | sed 's/^Leela: //'); fi; }
futurama
```

Now not only will you be greeted by a random ascii Futurama quote every time you open a terminal window, you can also get one just by typing the command "futurama" and hitting enter. :) This command is technically known as a function. Functions in your bashrc allow you to have complicated bits of shell script executable by a simple name. Clevercloggs among you will see in that bit of scripting above I've defined the function, then immediately called it by entering its name on the line below. So if you want to get a Futurama ascii quote by running the command "futurama", but you don't want it to pop up every time you open a terminal, simply remove the second line which reads "futurama". 

Here's some sample output:

```

 _________________________________
< I'm an outdated piece of junk.  >
 ---------------------------------
   \
    \
     ( )
      H
      H
     _H_ 
  .-'-.-'-.
 /         \
|           |
|   .-------'._
|  / /  '.' '. \
|  \ \ @   @ / / 
|   '---------'        
|    _______|  
|  .'-+-+-+|  
|  '.-+-+-+|         
|    """""" |
'-.__   __.-'
     """  


 _________________________________________
/ I don't regret this, but I both rue and \
\ lament it.                              /
 -----------------------------------------
   \
    \
             u                                 
      .  x!X                                 
    ."X M~~>                                 
   d~~XX~~~k    .u.xZ `  "%                
  d~~~M!~~~?..+"~~~~~?:  "    h              
 '~~~~~~~~~~~~~~~~~~~~~?      `              
 4~~~~~~~~~~~~~~~~~~~~~~>     '              
 ':~~~~~~~~~~(X+"" X~~~~>    xHL             
  %~~~~~(X="      'X"!~~% :RMMMRMRs          
   ^"*f`          ' (~~~~~MMMMMMMMMMMx       
     f     /`   %   !~~~~~MMMMMMMMMMMMMc     
     F    ?      '  !~~~~~!MMMMMMMMMMMMMM.   
    ' .  :": "   :  !X""(~~?MMMMMMMMMMMMMMh  
    'x  .~  ^-+="   ? "f4!*  #MMMMMMMMMMMMMM.
     /"               .."     `MMMMMMMMMMMMMM
     h ..             '         #MMMMMMMMMMMM
     f                '          (MMMMMMMMMMM
   :         .:=""     >       dMMMMMMMMMMMMM
   "+mm+=~("           RR     HMMMMMMMMMMMMM"
           %          (MMNmHHMMMMMMMMMMMMMMF 
          uR5         dMMMMMMMMMMMMMMMMMMMF  
        dMRMM>       dMMMMMMMMMMMMMMMMMMMF   
       RMHMMMF=x..=" RMRMMMMMMMMMMMMMMMMF    
      MMMMMMM       'MMMMMMMMMMMMMMMMMMF     
     dMMRMMMK       'MMMMMMMMMMMMMMMMM"      
     RMMRMMME       3MMMMMMMMMMMMMMMM        
    XMMMMMMM>       9MMMMMMMMMMMMMMM~        
   'MMMMMMMM>       9MMMMMMMMMMMMMMF         
   tMMMMMMMM        9MMMMMMMMMMMMMM          
   MMMMMMMMM        9MMMMMMMMMMMMMM          
  'MMMMRMMMM        9MMMMMMMMMMMMM9        

```

[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[SIZE="5"]Part seven: boring stuff.[/SIZE]

The terminal isn't all fun and games. It pays to keep your configuration tidy and neat. It can be useful to create a file especially for your zany additions. If you scan the lines of your bashrc, you'll see these lines somewhere:

```

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi
```

This snippet of bash checks to see whether you have a .bash_aliases file, and if so, uses it as an additional configuration tool. It isn't restricted to aliases, either. Think of it as another bashrc. You can put your welcome scripts in there too, if you prefer. If you want to use a .bash_aliases file, just go ahead and make sure those lines are uncommented and that .bash_aliases exists. You can create it by running this:

```
gedit .bash_aliases
```

And then saving the file. Bash aliases and functions are incredibly powerful terminal tools. If you want to learn more about them, there is a very extensive thread by mssever about them [here]("http://ubuntuforums.org/showthread.php?t=204382").

Here's just a quick example of their use:

```

function futurama() {
wee=$(curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//');
if [[ $wee = "Fry"* ]]; then 
cowsay -f fry $(echo $wee | sed 's/^Fry: //'); fi; 
if [[ $wee = "Ben"* ]]; then 
cowsay -f bender $(echo $wee | sed 's/^Bender: //'); fi; 
if [[ $wee = "Lee"* ]]; then 
cowsay -f leela $(echo $wee | sed 's/^Leela: //'); fi;
}
```

I don't know about you, but typing all that out every time I want to see a funny Futurama quote is not my idea of fun. But by declaring it a function in my bash_aliases, I can see one whenever I want, just by running the command "futurama". I can even do all of the usual shell stuff with this function. I want to output the thing to text file to email to someone? Not a problem:

```
futurama > output.txt
```

I can even make more functions that use the functions I've already declared:

```

function autofuture()
   {
   while true; do
   futurama;
   sleep 30; done;
   }
```
Now I can have automatic terminal ascii updates every thirty seconds.

There are thousands of reasons to use aliases and functions. A lot of them are actually useful too. :P

Told you it was boring, man.
[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]

[size="5"]Part eight: more ideas from thread chit chat.[/size]

People like to reply to these sort of threads. I'll put links to the other ideas people come up with here. All links point to other posts in this thread unless stated otherwise. 

[INDENT][cheesepenguins]("http://ubuntuforums.org/member.php?u=614511") comes up with a cool way to randomise the ascii greeting [here]("http://ubuntuforums.org/showpost.php?p=7331544&postcount=9") and and expanded on a bit [here]("http://ubuntuforums.org/showpost.php?p=7345814&postcount=10"). With this, a random ascii picture will greet you, and if it's a Futurama ascii, then the text will be a Futurama quote, too.

[danielrmt]("http://ubuntuforums.org/member.php?u=702969") has a slightly different way of mixing up the cowsay and fortune apps [here]("http://ubuntuforums.org/showpost.php?p=7346256&postcount=12"), which is somewhat easier on the eye than what I came up with.[/INDENT]



[center]**-----------------------------------------------------------------------------------------------------------------------**[/center]


The end.

If there is any interest, I'll add an extra section about modifying bash the proper way: with aliases and functions.

---

### Post by jpeddicord on 2009-05-11
Approved. The Futurama ascii art made me chuckle. Thank you for your contribution to T&T! :)

---

### Post by monsterstack on 2009-05-11
> **jacobmp92 said:**
> Approved. The Futurama ascii art made me chuckle. Thank you for your contribution to T&T! :)

Thanks a bunch. I just fixed up a bunch of bugs with some of the commands. Futurama quotes are now much more reliable.

---

### Post by monsterstack on 2009-05-11
Added some extra details and links to relevant threads.

---

### Post by draperdt on 2009-05-12
This thread was infact pretty cool and informative. Thanks.

---

### Post by binbash on 2009-05-12
Very detailed and cool howto.Thanks

---

### Post by kostkon on 2009-05-12
Wow, great how-to! Thanks!:P

---

### Post by LoloftheRings on 2009-05-12
Very nice! This is really something I missed in my terminal :D

---

### Post by cheesepenguins on 2009-05-23
Thank you for the very nice guide, I've thrown the following together in my .bash_aliases file, the idea being it will run one of any of the cow files at random with the fortune command as input, if its a futurama cow it then runs the futurama function (disregarding the cow choice from before). 

```
function futurama() { wee=$(curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//'); if [[ $wee = "Fry"* ]]; then cowsay -f fry $(echo $wee | sed 's/^Fry: //'); fi; if [[ $wee = "Ben"* ]]; then cowsay -f bender $(echo $wee | sed 's/^Bender: //'); fi; if [[ $wee = "Lee"* ]]; then cowsay -f leela $(echo $wee | sed 's/^Leela: //'); fi; }


function woots() { #!/bin/bash
cd /usr/share/cowsay/cows/
cows=(*.cow)
num=${#cows[@]}
((num=RANDOM%num))
randcow=`echo ${cows[$num]}`


if [[ $randcow = "leela.cow" ]] || [[ $randcow = "fry.cow" ]] || [[ $randcow = "bender.cow" ]];
then futurama;
else
phrase=`fortune -a`
cowsay -f $randcow $phrase
cd ~;
fi; 
}
woots

```

Sample output of the small script:
```
/ He: Let's end it all, bequeathin' our   \
| brains to science. She: What?!? Science |
| got enough trouble with their OWN       |
\ brains. -- Walt Kelly                   /
 -----------------------------------------
                       \                    ^    /^
                        \                  / \  // \
                         \   |\___/|      /   \//  .\
                          \  /O  O  \__  /    //  | \ \           *----*
                            /     /  \/_/    //   |  \  \          \   |
                            @___@`    \/_   //    |   \   \         \/\ \
                           0/0/|       \/_ //     |    \    \         \  \
                       0/0/0/0/|        \///      |     \     \       |  |
                    0/0/0/0/0/_|_ /   (  //       |      \     _\     |  /
                 0/0/0/0/0/0/`/,_ _ _/  ) ; -.    |    _ _\.-~       /   /
                             ,-}        _      *-.|.-~-.           .~    ~
            \     \__/        `/\      /                 ~-. _ .-~      /
             \____(oo)           *.   }            {                   /
             (    (--)          .----~-.\        \-`                 .~
             //__\\  \__ Ack!   ///.----..<        \             _ -~
            //    \\               ///-._ _ _ _ _ _ _{^ - - - - ~



[ m00z0r: ~ ]$ woots
 ________________________________________
/ Oh, so, just 'cause a robot wants to   \
\ kill humans that makes him a radical?  /
 ----------------------------------------
   \
    \
     ( )
      H
      H
     _H_
  .-'-.-'-.
 /         \
|           |
|   .-------'._
|  / /  '.' '. \
|  \ \ @   @ / /
|   '---------'
|    _______|
|  .'-+-+-+|
|  '.-+-+-+|
|    """""" |
'-.__   __.-'
     """


```

---

### Post by monsterstack on 2009-05-25
> **cheesepenguins said:**
> Thank you for the very nice guide, I've thrown the following together in my .bash_aliases file, the idea being it will run one of any of the cow files at random with the fortune command as input, if its a futurama cow it then runs the futurama function (disregarding the cow choice from before). 

That's pretty cool stuff, but when you've missed out the cd command from the first part of your if fork:

```

function woots() { #!/bin/bash
  cd /usr/share/cowsay/cows/
  cows=(*.cow)
  num=${#cows[@]}
  ((num=RANDOM%num))
  randcow=`echo ${cows[$num]}`
  if [[ $randcow = "leela.cow" ]] || [[ $randcow = "fry.cow" ]] || [[ $randcow = "bender.cow" ]];
    then
      futurama;
      [COLOR="Red"]cd ~;[/COLOR]
    else
      phrase=`fortune -a`
      cowsay -f $randcow $phrase
      cd ~;
  fi; 
}
```

That way you'll return home if you're lucky enough to get a Futurama quote. Even so you'll be returned to your home directory every time you run the woots command regardless of what folder you're in. So alternatively, if you don't want to have to change directories at all, do this:

```
function woots() { #!/bin/bash
  cows=(/usr/share/cowsay/cows/*.cow)
  num=${#cows[@]}
  ((num=RANDOM%num))
  randcow=`echo ${cows[$num]}`
  if [[ $randcow = "/usr/share/cowsay/cows/leela.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/fry.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/bender.cow" ]];
    then futurama;
  else
    phrase=`fortune -a`
    cowsay -f $randcow $phrase;
  fi; 
}
```

Sorry to nitpick! Thanks for enjoying the thread. :)

---

### Post by monsterstack on 2009-05-25
> **draperdt said:**
> This thread was infact pretty cool and informative. Thanks.
> **binbash said:**
> Very detailed and cool howto.Thanks
> **kostkon said:**
> Wow, great how-to! Thanks!:P
> **LoloftheRings said:**
> Very nice! This is really something I missed in my terminal :D

Thanks a lot tharr. :)

---

### Post by Tibuda on 2009-05-25
cowsay and fortune rocks! I have created this alias in my .bashrc:
```
alias fortune='clear && fortune -s | cowsay -f tux'
```

---

### Post by monsterstack on 2009-05-25
> **danielrmt said:**
> cowsay and fortune rocks! I have created this alias in my .bashrc:
```
alias fortune='clear && fortune -s | cowsay -f tux'
```

Nice stuff. That command's a little easier on the eyes than the one I came up with. I added this and cheesepenguin's cool idea to the original howto.

---

### Post by cheesepenguins on 2009-05-26
> **monsterstack said:**
> That's pretty cool stuff, but when you've missed out the cd command from the first part of your if fork:

```

function woots() { #!/bin/bash
  cd /usr/share/cowsay/cows/
  cows=(*.cow)
  num=${#cows[@]}
  ((num=RANDOM%num))
  randcow=`echo ${cows[$num]}`
  if [[ $randcow = "leela.cow" ]] || [[ $randcow = "fry.cow" ]] || [[ $randcow = "bender.cow" ]];
    then
      futurama;
      [COLOR="Red"]cd ~;[/COLOR]
    else
      phrase=`fortune -a`
      cowsay -f $randcow $phrase
      cd ~;
  fi; 
}
```

That way you'll return home if you're lucky enough to get a Futurama quote. Even so you'll be returned to your home directory every time you run the woots command regardless of what folder you're in. So alternatively, if you don't want to have to change directories at all, do this:

```
function woots() { #!/bin/bash
  cows=(/usr/share/cowsay/cows/*.cow)
  num=${#cows[@]}
  ((num=RANDOM%num))
  randcow=`echo ${cows[$num]}`
  if [[ $randcow = "/usr/share/cowsay/cows/leela.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/fry.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/bender.cow" ]];
    then futurama;
  else
    phrase=`fortune -a`
    cowsay -f $randcow $phrase;
  fi; 
}
```

Sorry to nitpick! Thanks for enjoying the thread. :)
I noticed my mistakes as well! :( I couldn't see a fix for the cd, except to add it to the other fork of the code (I'm pretty new to bash).

However here is what I've thrown together for my whole file, (I've included the solution you've put above :)), and some exaile commands and outputs. :)

```
function futurama() { wee=$(curl -Is slashdot.org | egrep '^X-(F|B|L)' | sed 's/^..//'); if [[ $wee = "Fry"* ]]; then cowsay -f fry $(echo $wee | sed 's/^Fry: //'); fi; if [[ $wee = "Ben"* ]]; then cowsay -f bender $(echo $wee | sed 's/^Bender: //'); fi; if [[ $wee = "Lee"* ]]; then cowsay -f leela $(echo $wee | sed 's/^Leela: //'); fi; }

#current song displayed
function currtune() {
exec 3>&2 2> /dev/null #Exaile was updated and now throws a few warnings, redirect them to a blackhole ;)
tunetitle=`exaile --get-title | awk -F'/usr/lib' '{printf $1}' | awk -F'locat' '{printf $1}' | awk -F'gc, sys' '{printf $1}'`
tuneartist=`exaile --get-artist | awk -F'/usr/lib' '{printf $1}' | awk -F'locat' '{printf $1}' | awk -F'gc, sys' '{printf $1}'`
tunealbum=`exaile --get-album | awk -F'/usr/lib' '{printf $1}' | awk -F'locat' '{printf $1}' | awk -F'gc, sys' '{printf $1}'`
tunelength=`exaile --get-length | awk -F'/usr/lib' '{printf $1}' | awk -F'locat' '{printf $1}' | awk -F'gc, sys' '{printf $1}'`
exec 2>&3; #Stop the error redirect, used below for next track etc.

if [[ $tunelength != "" ]];
then echo "d(-_-)b  Song: $tunetitle ($tunelength)" 
echo "d(o_o)b  Artist: $tuneartist"
echo "d(+_+)b  Album: $tunealbum";
else
echo "No song is currently playing. =(";
fi;
} 

#next track
function next() {
exec 3>&2 2> /dev/null
echo `exaile -n | awk -F'location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so before 3' '{printf $2}'`
exec 2>&3;}

#previous
function prev() {
exec 3>&2 2> /dev/null
echo `exaile -p | awk -F'location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so before 3' '{printf $2}'`
exec 2>&3;}

#play/pause
function play() {
exec 3>&2 2> /dev/null
echo `exaile -t | awk -F'location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so before 3' '{printf $2}'`
exec 2>&3;}

#play/pause
function pause() {
exec 3>&2 2> /dev/null
echo `exaile -t | awk -F'location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so before 3' '{printf $2}'`
exec 2>&3;}

#sound
function sound() {
exec 3>&2 2> /dev/null
echo `gnome-sound-properties`
exec 2>&3;}

function start() { #!/bin/bash
#Decides upon the ascii for cowsay
  cows=(/usr/share/cowsay/cows/*.cow)
  num=${#cows[@]}
  ((num=RANDOM%num))
  randcow=`echo ${cows[$num]}`

#if a futurama "cow" run the futurama function above.
  if [[ $randcow = "/usr/share/cowsay/cows/leela.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/fry.cow" ]] || [[ $randcow = "/usr/share/cowsay/cows/bender.cow" ]];
then futurama;
else #else run below.
phrase=`fortune -a`
cowsay -f $randcow $phrase
fi; 
currtune #run the current tune function above.
}
start
```

---

