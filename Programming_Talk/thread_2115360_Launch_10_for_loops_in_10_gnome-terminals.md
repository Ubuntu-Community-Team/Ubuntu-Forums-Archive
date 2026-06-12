---
title: "Launch 10 for loops in 10 gnome-terminals"
date: 2013-02-12
forum: Programming Talk
---

### Post by ntzrmtthihu777 on 2013-02-12
Having recently discovered for looping and wget with the -pk options, I would like to try my hand at mirroring an entire site. I have created a shell script that, in theory, should launch 10 scripts with for-looped wgets each in their own terminal window.

It looks like it works at first, 10 windows open just fine, but they immediately shut. Running the scripts individually works just fine, but launching them all at once does not work.

Could any bash guru out there give me a hand?

---

### Post by |{urse on 2013-02-12
Post the script, else no-one will be able to help ya.

---

### Post by |{urse on 2013-02-12
You probably just need to nest each xterm or gnome-terminal call in a do-while loop so the terms stay open. Or even use -t

> xterm -t somecommand

Then you will be required to press enter to close the terminal, probably not what you're looking for but I can't see your script so I am left to postulation.

Actually, since I'm just making random guesses, your issue is probably that you arent making use of & or && correctly.

Okay that's all I have for psychic solutions today. :lolflag:

---

### Post by |{urse on 2013-02-12
This thread could be a pretty fun game, please move to Cafe. ;)

---

### Post by ntzrmtthihu777 on 2013-02-12
Well the scripts are pretty simple themselves, I just want a "master script" that runs all 10 simultaneously.

For examples sake, each script is more or less the same, just the for loop has staggered numbers:
```

for i in {1..100}; do wget -pk http://foo.com/bar/$i; done
for i in {101..200}; do wget -pk http://foo.com/bar/$i; done
for i in {201..300}; do wget -pk http://foo.com/bar/$i; done
for i in {301..400}; do wget -pk http://foo.com/bar/$i; done
for i in {401..500}; do wget -pk http://foo.com/bar/$i; done
...
```

You get the picture, begins a download of the pages [http://foo.com/bar/1](http://foo.com/bar/1) - [http://foo.com/bar/500](http://foo.com/bar/500) in 5 equal 100 page portions.

---

### Post by Vaphell on 2013-02-14
```
params=()
for n in {1..901..100}
do
  params+=( --tab -e "bash -c 'for(( i=$n; i<$n+100; i++ )); do echo \$i; done; echo job done\!; read;'" )
done
printf "%s\n" "${params[@]}"
gnome-terminal "${params[@]}"
```

---

### Post by greenpeace on 2013-02-14
> **ntzrmtthihu777 said:**
> You get the picture, begins a download of the pages [http://foo.com/bar/1](http://foo.com/bar/1) - [http://foo.com/bar/500](http://foo.com/bar/500) in 5 equal 100 page portions.

Just beware that by doing this, you might not be making yourself popular with the site's webmaster.  You may also fall foul of limits on the numbers of connections or requests/hour that you can make, or just plain old blacklisting of your IP.

---

