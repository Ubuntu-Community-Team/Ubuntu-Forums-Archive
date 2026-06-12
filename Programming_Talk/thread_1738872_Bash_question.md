---
title: "Bash question"
date: 2011-04-25
forum: Programming Talk
---

### Post by XerXeX on 2011-04-25
Hi, how come I can successfully manage to move large amount of files if I simply type a for loop in a terminal like this:

for i in *{0001..3333}*; do mv $i reel_1/; done

but fail if I make a bash script as such;

for i in *{$1..$2}*
do
	mv $i $3
done

mover.sh 0001 3333 reel_1/

What have I missed? Thanks!

---

### Post by roccivic on 2011-04-25
I don't know why your code doesn't work...

But consider the following:

```
#!/bin/bash

for ((i=$1;i<$2;i++)); do
  mv $i $3
done

```

---

### Post by XerXeX on 2011-04-25
Thanks roccivic,

Unfortunately the files that I need to move are large tiff sequences that are usually named "movie_title0001.tiff" or similar. That is why I have to use wildcards *{0001..3333}* to filter out everything but the number and then move the sequences into respective folder. 

As I said, everything works fine as long as I type it in a terminal. I cannot figure out why the same would fail as a bash script...!

---

### Post by r-senior on 2011-04-25
Is it definitely a bash script? Did you put #!/bin/bash at the top? I don't know dash (which is what /bin/sh links to by default) but I'm thinking it may not expand the '..' the same way as bash?

---

### Post by Vaphell on 2011-04-25
it's simple
bash expands that pattern BEFORE variable substitution, it doesn't see 0001..3333 there but $a and $b
It's not trivial to parametrize {..}, i can think of one ugly hack that will do that, using eval.

but there is still hope
```
a=1; b=5; c=xxx
for i in $( seq -f "%04g" $a $b )
do
    echo mv my_porn${i}.tiff $c
done
```

result:
```
mv my_porn0001.tiff xxx
mv my_porn0002.tiff xxx
mv my_porn0003.tiff xxx
mv my_porn0004.tiff xxx
mv my_porn0005.tiff xxx

```

as you can imagine %04g controls the padding with zeroes to 4 digits

---

### Post by XerXeX on 2011-04-25
> **r-senior said:**
> Is it definitely a bash script? Did you put #!/bin/bash at the top?

Yes r-senior, it is a bash script, I just didn't wrap code tags around the script. Here is the full (non-working) script:

```

#!/bin/bash

for i in *{$1..$2}*
do
	mv $i $3
done

```

> **Vaphell said:**
> it's simple
bash expands that pattern BEFORE variable substitution, it doesn't see 0001..3333 there but $a and $b
It's not trivial to parametrize {..}, i can think of one ugly hack that will do that, using eval.

but there is still hope
```
a=1; b=5; c=xxx
for i in $( seq -f "%04g" $a $b )
do
    echo mv my_porn${i}.tiff $c
done
```

result:
```
mv my_porn0001.tiff xxx
mv my_porn0002.tiff xxx
mv my_porn0003.tiff xxx
mv my_porn0004.tiff xxx
mv my_porn0005.tiff xxx

```

as you can imagine %04g controls the padding with zeroes to 4 digits

That probably works but it is still a bit ugly and not really optimal. 

For your info we are not moving large pron files but building DCP packages for cinema distribution. Each movie is exported to 2k resolution tiff frames before we split them up at certain a certain frame number and move the sequence to their respective reel folder.

I have no problems opening up 6 terminals and write a simple for loop in each to get the job done. The intention was to write a script that anyone in the office could use if needed, typing just the script name, first frame #, last frame # and destination folder and get the job done!

---

### Post by XerXeX on 2011-04-25
> **Vaphell said:**
> but there is still hope
```
a=1; b=5; c=xxx
for i in $( seq -f "%04g" $a $b )
do
    echo mv my_porn${i}.tiff $c
done
```

Vaphell, thanks for the code. With a little modification we have ourselves a dummy proof version:

```

#!/bin/bash

for i in $( seq -f "%06g" $1 $2 )
do
	mv *${i}* $3
done

``` 

Thanks everyone. Love bash!

---

