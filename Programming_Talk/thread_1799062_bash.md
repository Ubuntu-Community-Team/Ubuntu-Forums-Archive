---
title: "bash"
date: 2011-07-07
forum: Programming Talk
---

### Post by Drenriza on 2011-07-07
Can someone help me.

i try to make a script that checks if a statement is true. As seen below.

```
read -p "Type the room number, you want to search for " -e room

if [ "ls | grep $room | awk '{print $2}'" == $room ];
then
        echo "test working"

else
        echo room $room dosent exist
fi

```

But it just say that the room dosent exist, even if the room exists. Where do i go wrong?
In the first line of the if statement, do i need to read the line before i can test with == if it exists?
If so, how do i do that?

Thanks on advance.

---

### Post by Bachstelze on 2011-07-07
Try

```
read -p "Type the room number, you want to search for " -e room

if ls | grep $room
then
        echo "test working"

else
        echo room $room dosent exist
fi
```

---

### Post by Drenriza on 2011-07-07
i got it to work with

```
read -p "Type the room number, you want to search for " -e room

if (ls | grep $room)
then
        echo "room $room exists"

else
        echo room $room dosent exist
fi

```

But this can give a wrong output, isint is possible to say in the if statement, ls |grep $room == something? To eliminate it giving a incorrect output.

---

### Post by Bachstelze on 2011-07-07
if (ls | grep -q $room)

man grep is your friend ;)

---

### Post by sisco311 on 2011-07-07
You shouldn't use ls in scripts. Try something like:
```


exists=false
for file in *
do
    if [[ "$file" == "$room" ]]
    then
        exists=true
        break
    fi
done
```

---

### Post by Bachstelze on 2011-07-07
> **sisco311 said:**
> You shouldn't use ls in scripts.

Why not?

---

### Post by sisco311 on 2011-07-07
> **Bachstelze said:**
> Why not?

It doesn't work very well with files with special characters like spaces, newlines, leading and trailing whitespaces, backslashes... in their names.

---

### Post by Drenriza on 2011-07-08
Thanks for the info guys, its really helpful.

I wonder if u can help me one more time tho.

Dosen't the 

```
do
#something
while [ condition ];
done
```

exists in bash?
Or does their exists another loop that checks at the end of the loop instead at the beginning/top of the loop.

---

### Post by Arndt on 2011-07-08
> **Drenriza said:**
> Thanks for the info guys, its really helpful.

I wonder if [you] can help me one more time tho.

Dosen't the 

```
do
#something
while [ condition ];
done
```

exists in bash?
Or does their exists another loop that checks at the end of the loop instead at the beginning/top of the loop.

It seems there isn't, but you can do it this way:

```
n=0
while true;
do
  echo hej
  n=`expr $n + 1`
  if [ $n -eq 3 ]; then
      break
  fi
done
```

---

### Post by Drenriza on 2011-07-08
thanks for the info.

I ended up doing

```

while [ condition ]; do
if [ condition ]; then
#loop
else
break
fi
done
```

---

### Post by Drenriza on 2011-07-08
Maybe someone can explain this to me.

When i in bash make (what i know as) a field
```
something=ls |grep $room |awk '{print $1}'
```

and i ```
echo $something
```
i get no value. Do i do this correctly or am i doing something wrong, since it docent work?

---

### Post by sisco311 on 2011-07-08
You are looking for [command substitution]("http://mywiki.wooledge.org/CommandSubstitution").

There are two forms; the older one is `COMMANDS` and the POSIX-form $(COMMANDS). The usage of the POSIX-form is preferred.

---

### Post by Drenriza on 2011-07-08
Thanks for the link Sisco. But i stand no chance of understanding it.
```
 IPs=($(awk /"$(</etc/myname)"/'{print $1}' /etc/hosts))
```??? O.o

i tried
```
roomID=$(folio ls| grep $room |awk '{print $1}')
```
but when i echo roomID, it dosent contain anything.
Also tried
```
roomID=(folio ls| grep $room |awk '{print $1}')
```
Same result, and also without the () at the beginning and end.

---

### Post by Arndt on 2011-07-08
> **Drenriza said:**
> Thanks for the link Sisco. But i stand no chance of understanding it.
```
 IPs=($(awk /"$(</etc/myname)"/'{print $1}' /etc/hosts))
```??? O.o

i tried
```
roomID=$(folio ls| grep $room |awk '{print $1}')
```
but when i echo roomID, it dosent contain anything.
Also tried
```
roomID=(folio ls| grep $room |awk '{print $1}')
```
Same result, and also without the () at the beginning and end.

What is folio?

---

