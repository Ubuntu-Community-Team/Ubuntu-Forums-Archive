---
title: "Help with a sed command"
date: 2012-12-06
forum: Programming Talk
---

### Post by Dispatch on 2012-12-06
Hey guys, I'm trying to use a sed command to search a huge dictionary file for a word and pull out some lines after it containing definitions.  The command I have so far is:

sed -n "/\<$word\>/,/Defn: /p " dict.txt

I have the script setup so it asks what word you want to look up, but the problem is, say the word you want to lookup is Iron.  I'll get back Cast Iron, Bridle Iron, Harping Iron, etc.  I want only the word "Iron" to be looked for.  How can I limit the scope that it searches for.  I tried adding a ? after $word and that limited the search to things like Irony or Ironist, but I haven't been able to get just the word Iron and it's driving me crazy!

EDIT: Of course, as I'm hitting submit I realize I wrote sec in the title instead of sed... oops. Fixed

---

### Post by Vaphell on 2012-12-06
assuming $word is the very first thing in the line
```
sed -n "/[COLOR="Blue"]^[/COLOR]\<$word\>/,/Defn: /p" 
```

---

### Post by Dispatch on 2012-12-06
> **Vaphell said:**
> assuming $word is the very first thing in the line
```
sed -n "/[COLOR="Blue"]^[/COLOR]\<$word\>/,/Defn: /p" 
```


This essentially reversed the problem.  Now I get back all the instances that begin with Iron, but have other words following such as Ironbark, Iron-fisted, Iron-hearted etc.  I've tried adding a $ in different places after $word to try to get it to read just $word, but I haven't had any luck.

---

### Post by steeldriver on 2012-12-06
it would help a lot if you posted a small section of your dictionary file

---

### Post by Dispatch on 2012-12-06
> **steeldriver said:**
> it would help a lot if you posted a small section of your dictionary file

```
ABADA
Ab"a*da, n. Etym: [Pg., the female rhinoceros.]

Defn: The rhinoceros. [Obs.] Purchas.

ABADDON
A*bad"don, n. Etym: [Heb. abaddon destruction, abyss, fr. abad to be
lost, to perish.]

1. The destroyer, or angel of the bottomless pit; -- the same as
Apollyon and Asmodeus.

2. Hell; the bottomless pit. [Poetic]
In all her gates, Abaddon rues Thy bold attempt. Milton.

ABAFT
A*baft", prep. Etym: [Pref. a-on + OE. baft, baften, biaften, AS.
be<E6>ftan; be by + <E6>ftan behind. See After, Aft, By.] (Naut.)

Defn: Behind; toward the stern from; as, abaft the wheelhouse. Abaft
the beam. See under Beam.

ABAFT
A*baft", adv. (Naut.)

Defn: Toward the stern; aft; as, to go abaft.

ABAISANCE
A*bai"sance, n. Etym: [For obeisance; confused with F. abaisser, E.
abase]

Defn: Obeisance. [Obs.] Jonson. 
```


As you can see the file itself is kind of a mess, which is why I feel like this is so difficult.  I want to have it find, say ABAFT, then print the next line after ABAFT that begins with Defn:

Another problem that I'm going to need to address down the line will be for words that don't have a single definition, but instead have the definitions labeled 1.  definition 1    2. definition 2     and so on.

---

### Post by steeldriver on 2012-12-06
OK so how about something like

```
sed -n "/^$word[[:space:]]*$/,/Defn: /p " dict.txt
```so that the only thing allowed between $word and the end of the line is (optional) whitespace?

EDIT: if you want it to skip stuff between the heading $word and the Defn: then I think that a little stateful parser in awk or perl would be easier

---

### Post by Vaphell on 2012-12-06
**/^${word}$/,/Defn/** ?

> Another problem that I'm going to need to address down the line will be for words that don't have a single definition, but instead have the definitions labeled 1. definition 1 2. definition 2 and so on.

use awk, sed is too limited/annoying to do complicated stuff.
*awk "/pattern1/,/pattern2/ { print $0 }"* is the equivalent of your sed line

```
awk -v word="$word" '$0==word,/Defn/{ print $0; }' dict.txt
```

Can you modify your dict file or create a derivative file with data formatted in a more convenient way?

---

### Post by Dispatch on 2012-12-06
Thanks for the help guys I'll try out those suggestions.  

As for formatting the file in a more convenient way, I'm not sure how I would go about doing that.  The file is huge.  I've looked around for a dictionary file that's organized in a better way, but I haven't come across a better one. 

 I'm in a shell scripting class and I'm doing this for a project, it's my first time writing my own script from scratch and it's way more frustrating than I expected haha

EDIT: Okay so I've made some progress in narrowing down what gets returned.  I know I should probably switch to awk or write a perl script like you guys suggested, it's getting kind of ridiculous trying to use sed commands.  i don't know how to use awk very well and know very basic perl stuff, but I gotta start somewhere so I'm going to start looking into those options.

Anyways, here's my script as of now:

```
#!/bin/bash

looptest=y
while test "$looptest" = "y"
do
  clear
        echo -n "What word would you like to look up? "; read word
        sed -n "/^$word[[:space:]]*$/,/Defn: /p " dict.txt > def.tmp | sed -n "/$word/,/1. /p" def.tmp | sed -n "/1. /,+3p" def.tmp

        echo -n "Would you like to look up another? (y)es or (n)o: "; read looptest
  clear
  if test "$answer" = "n"
        then
                clear; exit
  fi
done
```

One of the problems with that is that I have to type in the word I lookup twice.  I think it has something to do with the part that writes to def.tmp not working properly.

---

### Post by rnerwein on 2012-12-10
> **Vaphell said:**
> assuming $word is the very first thing in the line
```
sed -n "/[COLOR=Blue]^[/COLOR]\<$word\>/,/Defn: /p" 
```
must i be "sed"
may be you can use this:
 grep -inH ' iron ' `find . -type f` bla.txt
notice: there are spaces around " Iron "

---

### Post by Vaphell on 2012-12-10
```
sed -n "/^$word[[:space:]]*$/,/Defn: /p " dict.txt > def.tmp | sed -n "/$word/,/1. /p" def.tmp | sed -n "/1. /,+3p" def.tmp
```

what is this? you either read from file or from pipe so what you do here doesn't make much sense.

---

