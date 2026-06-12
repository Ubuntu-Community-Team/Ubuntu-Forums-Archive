---
title: "Loop in bash script"
date: 2014-03-16
forum: Programming Talk
---

### Post by alfirdaous on 2014-03-16
Hello everybody,

I would like to delete a batch of MP3 files lyrics, so I need to do a loop, MP3 files name are like below:

001, 002, 003,... and so on

Bash code:

```

#!/bin/bash
read -p "Please enter a starting number to delete lyrics? : " Start
read -p "Please enter a ending number to delete lyrics? : " EnD

for i in {$Start..$EnD}
do
/usr/bin/python /usr/bin/eyeD3 --remove-lyrics --remove-all $i.mp3
echo "Lyrics has been deleted successfully"
done

```

Result:
```

File Not Found: {1..5}.mp3

```

Thanks in advance

---

### Post by Lars Noodén on 2014-03-16
Maybe with seq?

```

a=2;b=5;
for i in $(seq $a $b);do echo $i;done

```

---

### Post by Vaphell on 2014-03-16
bash does {} interpretation first and expects proper values, $var substitution goes next, so {$x..$y} can't work

bash supports C-like for loop that can be used for that purpose

```
#!/bin/bash

read -p "Please enter a starting number to delete lyrics? : " start
read -p "Please enter a ending number to delete lyrics? : " end

for(( i=start; i<=end; i++ ))
do
  printf -v f '%03d.mp3' $i  # f is a variable that stores 0-padded 3-digit wide $i.mp3
  /usr/bin/python /usr/bin/eyeD3 --remove-lyrics --remove-all "$f"
done
```

btw echo will print regardless of the result of the actual command
you should chain eye3d and echo with && so echo gets executed only when it's actually true
is there a reason why you use full paths for python and eyeD3?

---

### Post by alfirdaous on 2014-03-17
@[**[COLOR=#DD4814][B]Lars Noodén**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643"): I think seq is deprecated

@[**[COLOR=#000000]Vaphell[/COLOR]**]("http://ubuntuforums.org/member.php?u=347382"): Thx for your help

---

### Post by mörgæs on 2014-03-17
If this solves your problem please mark the thread so.

---

### Post by alfirdaous on 2014-03-17
> is there a reason why you use full paths for python and eyeD3?

If not precising the path, will show an error that python and eyed3 not found

---

### Post by Vaphell on 2014-03-17
what did you do to your PATH that you don't have /usr/bin in it? o.O

---

