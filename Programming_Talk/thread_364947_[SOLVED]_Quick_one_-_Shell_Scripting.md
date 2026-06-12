---
title: "[SOLVED] Quick one - Shell Scripting"
date: 2007-02-18
forum: Programming Talk
---

### Post by victorbrca on 2007-02-18
Hi all,


  I finally have got some time to learn Linux between my studies. I find it very important as I am a new user and don't want to be a noob forever... :)

  Nways, reading "LINUX: Rute User’s Tutorial and Exposition" and got a question about shell scripting..
 
  Why is that this command works when typed it in the shell:

```
echo $[6*6+2]
38

```

  But this one does not when saved as <filename.sh>?

```
#!/bin/sh

echo "I will work out X*Y"
echo "Enter X"
read X
echo "Enter Y"
read Y
echo "X*Y = $X*$Y = $[X*Y]"
```

Output

```
victor@victor-laptop:~/Desktop/studying$ ./7-1-2.sh
I will work out X*Y
Enter X
2
Enter Y
2
X*Y = 2*2 = $[X*Y]

```

Thanks,


Vic.

---

### Post by po0f on 2007-02-18
victorbrca,

Use double parentheses around the multiplication expression:
```
[FONT="Courier New"]echo "X*Y = $X*$Y = $((X*Y))"[/FONT]
```

---

### Post by victorbrca on 2007-02-18
> **po0f said:**
> victorbrca,

Use double parentheses around the multiplication expression:


Hi po0f,

  Tried that and also did not work... Works directly on shell but not on a .sh file

```
victor@victor-laptop:~/Desktop/studying$ X=2; Y=3; echo "X*Y = $X*$Y = $((X*Y))"
X*Y = 2*3 = 6
victor@victor-laptop:~/Desktop/studying$ ./7-1-2.sh
I will work out X*Y
Enter X
2
Enter Y
3
./7-1-2.sh: 8: arith: syntax error: "X*Y"

```


Vic.

---

### Post by po0f on 2007-02-18
victorbrca,

Sorry, I have "**echo -e**" as my echo command in my example but just modified what you posted.  It should be:
```
[FONT="Courier New"]$ cat blar.sh 
#!/bin/bash
echo "Enter X: "
read X
echo "Enter Y: "
read Y
echo -e "X * Y = $X * $Y = $((X*Y))"

$ bash blar.sh 
Enter X: 
2
Enter Y: 
2
X * Y = 2 * 2 = 4
[/FONT]
```

---

### Post by victorbrca on 2007-02-18
> **po0f said:**
> victorbrca,

Sorry, I have "**echo -e**" as my echo command in my example but just modified what you posted.  It should be:


Hi po0f,

  Thanks a lot!!!  :)

  I've also just noticed something from your command. My book tells me to execute the file by doing $ ./file-name.sh. This is apparently wrong as when I changed the command to $ bash file-name.sh all of the different codes worked.. (  "echo -e", "[]" and "(())"  ).


  Vic.

---

### Post by po0f on 2007-02-18
victorbrca,

Yes, I just noticed that your hash-bang line reads "#!/bin/sh", *which is linked to dash*.  The default shell interpreter in Ubuntu is dash, which is basically a gimped version of bash.  Do this from the command line to change it:

```
[FONT="Courier New"]$ sudo dpkg-reconfigure dash[/FONT]
```

and answer 'No'.

I always do this on a fresh install, the hash-bangs in all my scripts are "#!/bin/bash" and I always execute my scripts directly through bash if they don't reside in PATH.

HTH  :)

[EDIT]

Added italic part for clarification.

---

### Post by victorbrca on 2007-02-19
kewl! Thanks again po0f!!!!  :) 


Vic.

---

### Post by gradedcheese on 2007-02-19
> 
I always do this on a fresh install, the hash-bangs in all my scripts are "#!/bin/bash" and I always execute my scripts directly through bash if they don't reside in PATH.

yes, and keep this in mind: if you use bash-specific syntax (ex: &> ) mark your script as #!/bin/bash otherwise, if you don't use bash-specific syntax and your script is a pretty generic on, mark it #!/bin/sh

When ubuntu switched to dash, a lot of things broke because many #!/bin/sh scripts were actually using bash syntax.  It wasn't the ubuntu guys' fault, but it did cause a lot of trouble and perhaps they should have left /bin/sh pointing to /bin/bash after all.  However as I understand it dash is a little faster?

---

### Post by victorbrca on 2007-02-19
Ok, so just to confirm to see if I understood... I'm a noob with no programming experience/knowledge, so some of this is a little hard to grasp...

  Dash (Debian Almquist Shell) is based on ash and has less features than Bash, however it's faster. Ubuntu changed from Bash to Dash around June 2006.

  Bash allows some features that Dash of course does not (like "[]" and "(())"), hence why my code which started with "#!/bin/sh" (thus pointing to Dash) did not work. However if I put a "bash" before the file name or do "#!/bin/bash" it should work as it would be pointing to Bash.

  This all changed now as I have reconfigured dash (as instructed by po0f) and Ubuntu is now pointing to Bash.

Please, correct me if I'm wrong!!!!!!  :confused: 


Thanks a lot,


Vic.

---

### Post by po0f on 2007-02-19
victorbrca,

Correct, bash > dash.  :)

---

