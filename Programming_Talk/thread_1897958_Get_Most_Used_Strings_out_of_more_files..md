---
title: "Get Most Used Strings out of more files."
date: 2011-12-20
forum: Programming Talk
---

### Post by ryanrio95 on 2011-12-20
I have more files that i want to sort on most used strings in these files.

for example of have:

file1.txt containing:
firefox
thunderbird
gnome-control-center

file2.txt containing:
ephipany
evolution
gnome-control-center

file3.txt containing:
firefox
evolution
gnome-control-center

and than i want to sort on which word is most used in all these files.

so the output would be:
gnome-control-center
firefox
evolution
epiphany
thunderbird

could someone make a little script for this?

Thanks in advance.

---

### Post by Petrolea on 2011-12-20
I won't write the script, that's your job. But I can help you though. 

Since there are more files, you should loop through all of them and save their contents into one place (maybe array of strings or one file). It would then be much easier to analyse. 

Now when you've done this (or not) you can take line by line, then compare each line to the rest of the lines. Save the amount of the times they occur, then sort it and write it out.

That's how I'd do it. But depending on a language that you are planing to use, you might have some of those functions predefined (sort, find, etc.).

---

### Post by CoffeeRain on 2011-12-20
I would use python and have a dictionary that increments every time a file is found. Something like {'Firefox': 0} and when a string is found, do d['Firefox']=d['Firefox']+1. Make sure the number is an int not a string. (don't quote it) Yah.

---

### Post by ryanrio95 on 2011-12-20
okay i  have one file now. with everything inside.
now i only have to sort them on most used in this file.

---

### Post by CoffeeRain on 2011-12-20
Do you have experience with Python?

---

### Post by ryanrio95 on 2011-12-20
i already got it :)

sort xxxpackages | uniq -c | sort -r > zzzpkgs
sed -i '/^      0 /d' zzzpkgs
sed -i '/^      1 /d' zzzpkgs
sed -i '/^      2 /d' zzzpkgs
sed -i '/^      3 /d' zzzpkgs
sed -i '/^      4 /d' zzzpkgs

---

### Post by ryanrio95 on 2011-12-20
it now sorts on most frequently in file.
can it sort alphabetic after that?

---

### Post by Petrolea on 2011-12-20
> **ryanrio95 said:**
> it now sorts on most frequently in file.
can it sort alphabetic after that?

What's the point of sorting it to one then to another order? 
And yes it can, I think 'sort' command can do that.

---

### Post by ofnuts on 2011-12-20
> **ryanrio95 said:**
> I have more files that i want to sort on most used strings in these files.

for example of have:

file1.txt containing:
firefox
thunderbird
gnome-control-center

file2.txt containing:
ephipany
evolution
gnome-control-center

file3.txt containing:
firefox
evolution
gnome-control-center

and than i want to sort on which word is most used in all these files.

so the output would be:
gnome-control-center
firefox
evolution
epiphany
thunderbird

could someone make a little script for this?

Thanks in advance.
```

cat file*.txt | sort | uniq -c | sort -rn

```
"cut" pipe stage to remove the count left as an exercise to the reader.

---

### Post by ryanrio95 on 2011-12-20
Thanks man, i'am now doing it like this:

sed -i 's/\t/\n/g' xxxpkgs
sed -i 's/ /\n/g' xxxpkgs
sed -i '/^0/d' xxxpkgs
sed -i '/^1/d' xxxpkgs
sed -i '/^2/d' xxxpkgs
sed -i '/^3/d' xxxpkgs
sed -i '/^4/d' xxxpkgs
sed -i '/^5/d' xxxpkgs
sed -i '/^6/d' xxxpkgs
sed -i '/^7/d' xxxpkgs
sed -i '/^8/d' xxxpkgs
sed -i '/^9/d' xxxpkgs
sort xxxpkgs | uniq -c | sort -nr > yyypkgs

sed -i 's/      6 /1.  /g' yyypkgs
sed -i 's/      5 /2.  /g' yyypkgs
sed -i 's/      4 /3.  /g' yyypkgs
sed -i 's/      3 /4.  /g' yyypkgs
sed -i 's/      2 /5.  /g' yyypkgs
sed -i 's/      1 /6.  /g' yyypkgs
sort yyypkgs | sort -n > zzzpkgs

sed -i 's/1.  //g' zzzpkgs
sed -i 's/2.  //g' zzzpkgs
sed -i 's/3.  //g' zzzpkgs
sed -i 's/4.  //g' zzzpkgs
sed -i '/^5.  /d' zzzpkgs
sed -i '/^6.  /d' zzzpkgs
sed -i '/^gparted/d' zzzpkgs
sed -i '/^gnome-terminal/d' zzzpkgs
sed -i '/^plymouth-theme/d' zzzpkgs
sed -i '/^thunderbird/d' zzzpkgs
sed -i '/^xterm/d' zzzpkgs

rm -f yyypkgs

---

### Post by ofnuts on 2011-12-20
> **ryanrio95 said:**
> Thanks man, i'am now doing it like this:

sed -i 's/\t/\n/g' xxxpkgs
sed -i 's/ /\n/g' xxxpkgs
sed -i '/^0/d' xxxpkgs
sed -i '/^1/d' xxxpkgs
sed -i '/^2/d' xxxpkgs
sed -i '/^3/d' xxxpkgs
sed -i '/^4/d' xxxpkgs
sed -i '/^5/d' xxxpkgs
sed -i '/^6/d' xxxpkgs
sed -i '/^7/d' xxxpkgs
sed -i '/^8/d' xxxpkgs
sed -i '/^9/d' xxxpkgs
sort xxxpkgs | uniq -c | sort -nr > yyypkgs

sed -i 's/      6 /1.  /g' yyypkgs
sed -i 's/      5 /2.  /g' yyypkgs
sed -i 's/      4 /3.  /g' yyypkgs
sed -i 's/      3 /4.  /g' yyypkgs
sed -i 's/      2 /5.  /g' yyypkgs
sed -i 's/      1 /6.  /g' yyypkgs
sort yyypkgs | sort -n > zzzpkgs

sed -i 's/1.  //g' zzzpkgs
sed -i 's/2.  //g' zzzpkgs
sed -i 's/3.  //g' zzzpkgs
sed -i 's/4.  //g' zzzpkgs
sed -i '/^5.  /d' zzzpkgs
sed -i '/^6.  /d' zzzpkgs
sed -i '/^gparted/d' zzzpkgs
sed -i '/^gnome-terminal/d' zzzpkgs
sed -i '/^plymouth-theme/d' zzzpkgs
sed -i '/^thunderbird/d' zzzpkgs
sed -i '/^xterm/d' zzzpkgs

rm -f yyypkgsYour call :)

---

### Post by trent.josephsen on 2011-12-20
> **ofnuts said:**
> ```

cat file*.txt | sort | uniq -c | sort -rn

```
"cut" pipe stage to remove the count left as an exercise to the reader.

That was my first thought as well.  Although... is that 'cat' unnecessary?  'sort file*.txt' would work, no?  In any case, it's a nitpick.

---

### Post by ofnuts on 2011-12-20
> **trent.josephsen said:**
> That was my first thought as well.  Although... is that 'cat' unnecessary?  'sort file*.txt' would work, no?  In any case, it's a nitpick.You're right... my first test started with uniq without a preliminary sort (forgot it needed one) and uniq doesn't take several files. So now down to
```

sort *.txt | uniq -c | sort -rn | awk '{print $2}'

```

---

