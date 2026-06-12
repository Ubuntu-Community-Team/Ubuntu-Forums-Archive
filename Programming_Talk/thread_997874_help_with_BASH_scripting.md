---
title: "help with BASH scripting"
date: 2008-11-30
forum: Programming Talk
---

### Post by AzraQ on 2008-11-30
Hi everyone

I'm having a really annoying syntax problem with my BASH script

what i want to do is rename the second arg in my script and add a .number to it

for example:
if the second arg is something.txt I want it to be something.txt.1 
so here is my code :

```
i=0
if [ -e $2 ]; then
{ 
echo "it exists"
while [ -e $2 ] 
do
i=$(("$i+1"))
$2="$2.$i"
done
}
fi
```

I've tries editing it in everyway, adding coloumns,$'s still the same problem on the lines inside the while loop

---

### Post by ghostdog74 on 2008-11-30
is its that simple as adding a number to it, why do you need that while loop?
```

i=1
if [ -e "$2" ];then
 newfile="$2.$i"
 i=$(( i+1 )) #check this syntax.
fi

```

---

### Post by AzraQ on 2008-11-30
i need that loop so i can be sure that there isn't a file named something.txt.1 too

i want to rename the second arg , I've tried what you just wrote ( i=$(( i+1 )) ), it seems that it's adding the number which is good but it isn't getting out of the loop for some reason?
it keeps adding a number then checking if the new $2 exists or not and even if it doen't it will keep entering the while loop! it's suppose to leave the loop when something.txt.1 is not in the current dir


```
i=0
while [ -e "$2" ] 
do
echo $2 # I added this just to see what is happening,, the file name is NOT changing for some reason
i=$((i+1))
$2="$2.$i"
done
}

```

---

### Post by geirha on 2008-11-30
You are not allowed to do "$2=$2.$i". You can only reset the arguments with the set command, but using a variable is the better choice in my opinion. Also if $2=$2.$i had worked, you would be getting "filename.txt.1", "filename.txt.1.2", "filename.txt.1.2.3" etc., which I believe is not the intension? 

```

filename="$2"
i=1
while [ -e "$filename" ]; do
  filename="$2.$i"
  i=$((i+1))
done

```

---

