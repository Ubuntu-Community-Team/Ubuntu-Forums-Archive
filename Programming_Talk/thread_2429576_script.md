---
title: "script"
date: 2019-10-20
forum: Programming Talk
---

### Post by aminedz22 on 2019-10-20
Hi, i am new user of linux and i want pls script [COLOR=#1D2228][FONT=&amp]
[/FONT][/COLOR]

---

### Post by TheFu on 2019-10-20
Is this work or a school assignment?
Bash: [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
and [https://www.tldp.org/LDP/abs/html/](https://www.tldp.org/LDP/abs/html/)
I would split the file to make processing easier using some delimiter.  Don't be afraid to use temporary files as needed.  If you can't clearly explain how to parse the entire file, then you can't create a program to parse it either.

For certain problems, I'd use perl, python, ruby instead of bash, but you don't want this to be the first program for a language you don't know.

---

### Post by aminedz22 on 2019-10-20
Thank you for your reply,I am a student and the script will help me get the results quickly because I have a lot of files

---

### Post by TheFu on 2019-10-20
Doing homework for students isn't something I do.

We will help you fix a script, but you need to post specific questions.  If I don't see some honest code attempted, I will not help.

If the problem is not clearly stated, nobody can help.   There simply isn't enough information provided so far.
If all you care about is only the data for \Polar .... until \Quadrupole, then I'd remove all the other characters outside those delimiters using something like sed.

---

### Post by Skaperen on 2019-10-20
are you asking for someone else to do all the work for you ... for free?  or are you paying (advertising is not allowed here and we don't do quid pro quo).  you don't even give details like what language to script in (bash, lua, perl, pike, python, ruby, etc).  and your problem explanation makes no sense.

---

### Post by aminedz22 on 2019-10-20
I want to use the script[COLOR=#333333]
[/COLOR]

---

### Post by aminedz22 on 2019-10-20
You have the time and patience to write without helping

---

### Post by QIII on 2019-10-20
Now that you have worked on a script of your own, you might receive some help.

Our purpose is to *provide support*, not to do projects for users.

If you present a script and say "Why isn't this working", that would be support.  Asking for the script to be written is not.

---

### Post by spjackson on 2019-10-20
Assuming your text is in a file data.txt then something like the following should get the values you are looking for.
```

tr -d '\n' < data.txt | sed 's/\\/\n\\/g' | fgrep '\Polar=' | sed 's/\\Polar=//'
tr -d '\n' < data.txt | sed 's/\\/\n\\/g' | fgrep '\HyperPolar=' | sed 's/\\HyperPolar=//'

```
This joins all the text into 1 line, splits the line at each backslash and finally greps for the required lines and removes the unwanted portion.

---

### Post by aminedz22 on 2019-10-20
a big thank-you

---

### Post by aminedz22 on 2019-10-21
Merci pour votre réponse 
sur ce fichier ca ne marche pas?

```
27414883,-2.80068849|H,0,4.89327009,-1.34123111,-2.87880029|H,0,4.3242
1214,0.13713561,-3.61614147|H,0,5.88491835,0.09663742,-2.83152488|S,0,
3.89127457,0.68531615,1.04602614|N,0,2.75224157,0.37073704,-1.34208351
|C,0,2.46629481,0.26170773,0.10229667|C,0,-1.18498553,-0.48084873,1.14
872849|C,0,-2.51925065,-0.24639872,1.11216704|H,0,-3.08287955,-0.21978
07,2.02129511|C,0,-3.2242556,-0.01828171,-0.23784427|C,0,-2.47973629,-
0.05453266,-1.42474961|C,0,-3.12451627,0.15290131,-2.64416588|H,0,-1.4
262708,-0.2396526,-1.39574775|C,0,-5.19376387,0.41681869,-1.42835439|C
,0,-4.49885349,0.39152727,-2.6452469|H,0,-2.57493853,0.12940427,-3.561
94158|H,0,-6.24805815,0.59941779,-1.42374322|H,0,-5.0178681,0.55379693
,-3.56676326|C,0,-5.30306335,0.24604441,0.99393235|H,0,-5.65827947,-0.
73712145,1.22220047|H,0,-4.66559353,0.58704325,1.78276189|H,0,-6.13489
763,0.91169194,0.89460909|N,0,-4.54803605,0.21376345,-0.26693706|C,0,1
.277252,-0.12114555,0.62781309|C,0,0.96240823,-0.23339178,2.12690427|O
,0,1.78752312,0.06085701,3.03032755|N,0,-0.42192908,-0.70691343,2.4054
198|C,0,-1.00824367,0.02300324,3.53871445|H,0,-1.02309561,1.07014608,3
.31923491|H,0,-2.00772113,-0.32064631,3.70559721|H,0,-0.42068753,-0.14
919014,4.41622638|C,0,1.98832937,-0.60842131,-2.12858654|H,0,2.2258831
1,-1.59701338,-1.79518916|H,0,0.94113936,-0.43051314,-1.99958381|H,0,2
.24192071,-0.51045803,-3.16347523|S,0,-0.15652992,-0.54034701,-0.29721
188||Version=EM64W-G09RevE.01|State=1-A|HF=-1648.7772651|RMSD=7.048e-0
09|Dipole=-5.5676511,0.0412021,-2.5393295|Polar=332.7991262,-0.6193637
,99.8786764,6.6211561,0.5968292,235.4350169|HyperPolar=-310.268231,136
.8596018,-26.8950518,-39.5777845,-294.0528687,77.9741809,-11.1576499,-
521.9044356,35.3931657,-215.8164|Quadrupole=52.8616985,-38.9536683,-13
.9080303,-8.8113919,-9.2244524,2.8179156|PG=C01 [X(C16H18N3O1S2)]||@
```

---

### Post by wildmanne39 on 2019-10-21
Hello you posted in an English only forum, please translate your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by spjackson on 2019-10-21
> **aminedz22 said:**
> Merci pour votre réponse 
sur ce fichier ca ne marche pas?

In your original post, you had backslash characters (e.g. \Polar=) but in this example where it does not work, you have pipe characters (e.g. |Polar=). Therefore you would need to change the backslash characters to pipes in the command, i.e.
```

tr -d '\n' < data.txt | sed 's/|/\n|/g' | fgrep '|Polar=' | sed 's/|Polar=//'
tr -d '\n' < data.txt | sed 's/|/\n|/g' | fgrep '|HyperPolar=' | sed 's/|HyperPolar=//'

```
There might be a more efficient way to do it. There might be a way to handle either pipes or backslashes in a single command, but I can't think of one at the moment without making it much more complicated.

---

