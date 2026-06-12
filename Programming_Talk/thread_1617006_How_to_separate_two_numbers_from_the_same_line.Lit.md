---
title: "How to separate two numbers from the same line.Little help here please..!!!"
date: 2010-11-08
forum: Programming Talk
---

### Post by nikkpap on 2010-11-08
hi i want to ask if we can separate into x= and y= from the a file with the following text  <coordinates>39,67882574656104,59,50864780739133,0</coordinates>
i use 
cpath=$ "~/Desktop" #just a test path.
value=$(grep '\<coordinates\>'$cpath *.kml) # with this i take the coordinates
notify-send "$value" #just to test the value faster than echo ;)

i just want to use 
x=39,67882574656104
y=59,50864780739133 and continue with further calculations.
thanks in advance. 
[email]nikkpap@gmail.com[/email]

---

### Post by worksofcraft on 2010-11-08
> **nikkpap said:**
> hi i want to ask if we can separate into x= and y= from the a file with the following text  <coordinates>39,67882574656104,59,50864780739133,0</coordinates>
i use 
cpath=$ "~/Desktop" #just a test path.
value=$(grep '\<coordinates\>'$cpath *.kml) # with this i take the coordinates
notify-send "$value" #just to test the value faster than echo ;)

i just want to use 
x=39,67882574656104
y=59,50864780739133 and continue with further calculations.
thanks in advance. 
[email]nikkpap@gmail.com[/email]

my first reaction is that you do well to use a decimal point instead of a decimal comma because using the same caharceter to separate between the two numbers is really gunna cause problems in the long run.

---

### Post by cipherboy_loc on 2010-11-08
Where [file] is the file where the thing is stored:

```
grep -io '<coordinates>[0-9, \.]\{1,\}</coordinates>' ./[file] | grep -oi '[0-9,]\{1,\}' | grep -io '[0-9]\{2\},[0-9]\{1,\}'
```

I could not get the last number (,0), but other than that..


Cipherboy

---

### Post by SeijiSensei on 2010-11-09
You can use sed and awk for this, though the fact that you use the comma as both a decimal point and a field separator makes it a bit more annoying than if you used a period.

```

value=$(grep '\<coordinates\>'$cpath *.kml | sed 's/<.coordinates>//g') 
x=$(echo $value | awk -F, '{print $1 "," $2}')
y=$(echo $value | awk -F, '{print $3 "," $4}')

```

The first line uses sed to remove the <coordinates> and </coordinates> elements, then awk splits the result using the comma as a delimiter.  Each field is referenced as $n and a literal comma is inserted between the fields using "," in awk's print command.

---

### Post by sreek_arc on 2010-11-09
See my not so elegant sed solution 
 
sed s'/<[a-z]*>//g' inputfilename | sed s'/<\/[a-z]*>//g' | sed s'/,/\t/2
 
sed one lines are great

---

### Post by nikkpap on 2010-11-10
i used a combination of your propositions and toke this 

cdts=$( grep '\<coordinates\>' $cpath | sed 's/<.coordinates>//g'| grep -oi '[0-9,]\{1,\}' ) 
xfa=$(echo $cdts | awk -F, '{print $1 "," $2}')
yfa=$(echo $cdts | awk -F, '{print $3 "," $4}')
notify-send "$xfa"
notify-send "$yfa"

thanks you all when i finish the script i will sent it to see it... ;) 

P.S. where i can find how to use mathematics calculations in bash
ex. 
r = (x2 + y2)^1/2 
&#952; = atan(y/x)
x = r cos(&#952;)
y = r sin(&#952;)

---

### Post by SeijiSensei on 2010-11-10
> **nikkpap said:**
> 
P.S. where i can find how to use mathematics calculations in bash
ex. 
r = (x2 + y2)^1/2 
&#952; = atan(y/x)
x = r cos(&#952;)
y = r sin(&#952;)

You can only do basic arithmetic operations in the shell. See [http://www.gnu.org/software/bash/manual/bashref.html#Shell-Arithmetic](http://www.gnu.org/software/bash/manual/bashref.html#Shell-Arithmetic).  No trig functions or anything like that.  To do advanced calculations within an interpreted language, you'll need to use something like Python.

---

### Post by trent.josephsen on 2010-11-10
You can use bc from a shell to do mathematical operations fairly easily:
```
$ bc -l <<<'sqrt(0.3^2+0.4^2)'
.50000000000000000000
$ bc -l <<<'a(1)*4'
3.14159265358979323844
$ bc -l <<<'c(0)'
1.00000000000000000000
```

It's not available everywhere, though.

---

### Post by nikkpap on 2010-11-10
May i continue in this direction [http://www.suite101.com/content/mathmatical-functions-and-linux-shells-a66284](http://www.suite101.com/content/mathmatical-functions-and-linux-shells-a66284)

with korn shell is it possible to make my calculations with this kind of shell i think all Ubuntu distros which i care more they have pre-installed the korn shell

and thank you all guys you are awesome ... really this is the way i want to live my life i like to share my knowledge open source open mind for ever for a better word without piracy .... thanks again

---

