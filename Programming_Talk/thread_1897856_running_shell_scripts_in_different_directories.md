---
title: "running shell scripts in different directories"
date: 2011-12-20
forum: Programming Talk
---

### Post by jamesbon on 2011-12-20
I have  a directory named 
```
tinkering
``` which has following sub directories

```
saraswati\ and\ durga\ pooja
64\ yogini\ pooja
52\ guruwar\ ke\ tap\ se\ unemployment\ finish
bajrang\ bali\ har\ lete\ ain\ devote\ dukh
bhoot\ bhagane\ ke\ tareke
bacho\ ko\ gussa\ ane\ ka\ karan
durga\ pooja
khatre\ ke\ nishan\ hanth\ mein
saraswati\ and\ durga\ pooja
seb\ chadhane\ se\ ma\ hinnamasta
bhoot\ bhagane\ ke\ tareke

```

each of these sub directories has a script name ```
script.sh
```
I wrote a script on terminal 
```

cd ~/tinkering/;
cd saraswati\ and\ durga\ pooja/;./script.sh;cd ..;cd 64\ yogini\ pooja/;./script.sh;cd ../;cd 52\ guruwar\ ke\ tap\ se\ unemployment\ finish/;./script.sh;cd ../;cd bajrang\ bali\ har\ lete\ ain\ devote\ dukh/;./script.sh;cd ../;cd bhoot\ bhagane\ ke\ tareke/;./script.sh;cd ..;cd bacho\ ko\ gussa\ ane\ ka\ karan/;./script.sh;cd ..;cd durga\ pooja/;./script.sh;cd ..;cd khatre\ ke\ nishan\ hanth\ mein/;./script.sh;cd ..;cd saraswati\ and\ durga\ pooja/;./script.sh;cd ..;cd seb\ chadhane\ se\ ma\ hinnamasta/;./script.sh;cd ..;cd bhoot\ bhagane\ ke\ tareke/;./script.sh;cd ..;

```

but this script did could not run. The purpose was rather than going to each sub directory and typing ./script.sh I be able to automate this process what mistake did I do in above?

---

### Post by Arndt on 2011-12-20
> **jamesbon said:**
> I have  a directory named 
```
tinkering
``` which has following sub directories

```
saraswati\ and\ durga\ pooja
64\ yogini\ pooja
52\ guruwar\ ke\ tap\ se\ unemployment\ finish
bajrang\ bali\ har\ lete\ ain\ devote\ dukh
bhoot\ bhagane\ ke\ tareke
bacho\ ko\ gussa\ ane\ ka\ karan
durga\ pooja
khatre\ ke\ nishan\ hanth\ mein
saraswati\ and\ durga\ pooja
seb\ chadhane\ se\ ma\ hinnamasta
bhoot\ bhagane\ ke\ tareke

```

each of these sub directories has a script name ```
script.sh
```
I wrote a script on terminal 
```

cd ~/tinkering/;
cd saraswati\ and\ durga\ pooja/;./script.sh;cd ..;cd 64\ yogini\ pooja/;./script.sh;cd ../;cd 52\ guruwar\ ke\ tap\ se\ unemployment\ finish/;./script.sh;cd ../;cd bajrang\ bali\ har\ lete\ ain\ devote\ dukh/;./script.sh;cd ../;cd bhoot\ bhagane\ ke\ tareke/;./script.sh;cd ..;cd bacho\ ko\ gussa\ ane\ ka\ karan/;./script.sh;cd ..;cd durga\ pooja/;./script.sh;cd ..;cd khatre\ ke\ nishan\ hanth\ mein/;./script.sh;cd ..;cd saraswati\ and\ durga\ pooja/;./script.sh;cd ..;cd seb\ chadhane\ se\ ma\ hinnamasta/;./script.sh;cd ..;cd bhoot\ bhagane\ ke\ tareke/;./script.sh;cd ..;

```

but this script did could not run. The purpose was rather than going to each sub directory and typing ./script.sh I be able to automate this process what mistake did I do in above?

Your approach is valid - I ran it here with success. What errors happened for you?

A more general (but less readable) way to do this is:

```
cd tinkering
for i in *; do if [ -d "$i" ]; then cd "$i"; ./script.sh; cd ..; fi; done
cd ..
```

Could it be your script itself that is confused by the presence of spaces in the directories? It is often necessary to enclose variable expansions in double quotes, like I did above.

---

### Post by jamesbon on 2011-12-20
Yes presence of spaces is one problem and the script you run I ran a similar script 
> for subdir in */; do
  cd "$subdir"
  ./script.sh
  cd ..
done
this did not went in the last directory.Rest of the directories it went.

---

### Post by Arndt on 2011-12-21
> **jamesbon said:**
> Yes presence of spaces is one problem and the script you run I ran a similar script 

this did not went in the last directory.Rest of the directories it went.

I don't know if you noticed that there are duplicates in the list of directories that you gave. Could that be the explanation?

---

### Post by SaintDanBert on 2011-12-21
While it uses another shell variable I like to use:
```

#=== control your loop
for i in *; do 
    #=== where are you working?
    myPlace="$i"
    #=== is that a folder
    if [ -d "$myPlace" ]; then
        #=== yessir, then use it 
        cd "$myPlace";
        #=== do the work on the current place 
        ./script.sh "$myPlace";
        #=== return to starting point 
        cd ..; 
    fi; 
done

```
Using one variable for control and another for work assures that your workings do not step on the loop controls easily. (grin) You can always write "i=something_else" ... but you need to work at that sort of snafu.

Another common trick is the following:
```

#=== grab the current folder
startHere=$(pwd)

...

#=== return to where you started
cd $startHere

```
instead of using the "cd double-dot" approach.  Should any of your processing land you somewhere else in your folder tree, the double-dot won't put you back where you think is does.

You need to adopt some convention with your scripts.  Does each script have responsibility to save and restore $(pwd) or does that responsibility lie with whatever is using the script?  I prefer the former so that I know my scripts are place agnostic.  Where ever I am $(pwd) when I launch a script, the script will remember, go where ever and do its work, and return where it started.

Good luck,
~~~ 0;-Dan

---

### Post by Habitual on 2011-12-21
SaintDanBert:

I stole the contents of the code-block0 for my personal use. :)
Code from code-block1 I've already known.

Merry Christmas / Happy Holidays

---

### Post by Vaphell on 2011-12-21
using
```
for i in "$PWD"/*; do ...
```
would produce a list of absolute paths that wouldn't require navigating back to the main directory after cd'ing.

---

### Post by jamesbon on 2011-12-22
> **Vaphell said:**
> using
```
for i in "$PWD"/*; do ...
```
would produce a list of absolute paths that wouldn't require navigating back to the main directory after cd'ing.

Thanks for this tip.

---

### Post by geirha on 2011-12-22
I prefer to just do the cd in a subshell.
```

for dir in ./*/; do
    ( cd "$dir" && ./script.sh )
done

```

Is script.sh the same script copied to each directory?

---

### Post by SaintDanBert on 2011-12-22
> **Habitual said:**
> SaintDanBert:

I stole the contents of the code-block0 for my personal use. :)
Code from code-block1 I've already known.

Merry Christmas / Happy Holidays

Pay it forward!!!

Find at least one posting and comment with something useful.

Happy Christmas,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-12-22
> **geirha said:**
> I prefer to just do the cd in a subshell.
```

for dir in ./*/; do
    ( cd "$dir" && ./script.sh )
done

```

Is script.sh the same script copied to each directory?


I still like the idea of passing the script target as a parameter to the script rather than relying on script working on $(PWD) which we all know will always be the correct place all of the time.
```

for dir in ./*/; do
    #=== script will process within the supplied folder
    [color=green]./script.sh "$dir"[/color]
    #..... script saves and restores $(pwd) if needed
done

```



Cheers,
~~~ 0;-Dan

---

