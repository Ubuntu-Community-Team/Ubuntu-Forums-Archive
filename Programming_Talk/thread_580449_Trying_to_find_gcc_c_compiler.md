---
title: "Trying to find gcc c compiler"
date: 2007-10-18
forum: Programming Talk
---

### Post by Mr. Joe on 2007-10-18
I've been learning C on an xp computer at my school, i want to start programming in c on my home linux computer. I looked up the linuux compiler program (gcc), but i cant find gcc on add/remove. anyone know how i can get it? or is my book old and theres a new compiler in use?

any help would be appreciated
=)

---

### Post by Wybiral on 2007-10-18
First you need to install build-essential:
```

sudo apt-get install build-essential

```

Then you can use the compiler from the command line:
```

gcc some_file.c -o my_program

```

---

### Post by Mr. Joe on 2007-10-18
thanks alot, installing right now, looks like its working ^_^

---

### Post by Mr. Joe on 2007-10-18
ok, so a new question:

I wrote a tiny program, just to get my legs under me. but my book is rather old and gives no explanation of what to do with a program on linux once it is successfully compiled (as is mine)

so two questions: is there a particular naming convention i need to follow? 

and also, what is the command for running a program? my book, which as i said is old (damn libraries) only mentions unix, and it says to name the finished product (your file here).out and in order to run it just type the file name. I named mine inform.out and attempted to run it by just entering its name, as it said for unix. isn't working, getting "command not found"

can anyone help?

---

### Post by Keshik on 2007-10-18
I believe to run your newly compiled program you do:


./PROGRAM_NAME


Make sure you have the "./" in front.

I can't remember how long it took me to figure that one out... I'm sure someone else can explain why that is needed. I'm interested in getting the reminder :)

---

### Post by Wybiral on 2007-10-18
To execute it use:
```

./my_program

```

EDIT:

lol, Keshik beat me to it!

---

### Post by Mr. Joe on 2007-10-19
hahahaha it worked! thanks alot guys. and while i said i was new to c programming on linux, i should tell you (as you might have guessed yourselves lol) than i'm really new in gerneral. i'll have lots of questions for you guys in the future. so you guys can teach me and watch me grow, kinda like a chia pet XD


....or maybe... a c-a pet... lol cough*pun*cough

---

### Post by Mr. Joe on 2007-10-19
you guys know of a good (physical) book i could get at a borders type place that focuses on c and c++ programming on linux? or at least one that does linux justice? mine now is all about windows 98 & unix. ya, thats the newest book my library has =/

---

### Post by Celegorm on 2007-10-19
> **Keshik said:**
> I believe to run your newly compiled program you do:


./PROGRAM_NAME


Make sure you have the "./" in front.

I can't remember how long it took me to figure that one out... I'm sure someone else can explain why that is needed. I'm interested in getting the reminder :)

The dot in './' stands for the current directory, and it is needed because the current directory is not included in the $PATH environment variable (try 'echo $PATH' if you want to see what is). When you type in a command, the shell only looks for binaries to execute in the directories in $PATH, unless you explicitly specify the path to an executable file. For instance you can use simply 'vim' instead of '/usr/bin/vim' since /usr/bin is included in $PATH. You can change the $PATH variable if you wish, [here]("http://www.codecoffee.com/tipsforlinux/articles/030.html") is a short guide on how to change environment variables.

---

### Post by Wybiral on 2007-10-19
> **Mr. Joe said:**
> you guys know of a good (physical) book i could get at a borders type place that focuses on c and c++ programming on linux? or at least one that does linux justice? mine now is all about windows 98 & unix. ya, thats the newest book my library has =/

I learned C mostly from the internet, but I did pick up the [O'Reilly C pocket reference]("http://www.oreilly.com/catalog/cpr/") for when I needed to look up a specific standard function or detail. C isn't complex to learn (the language itself it really simple), it just takes a lot of practice to become comfortable with.

EDIT:

The hardest time I predict you'll have is learning the "ins and outs" of the compiler. "What does this error mean", "what does that warning mean", things like that. I will also advise you make 100% sure that whatever books/tutorials you learn are C99 compliant (there's nothing worse than learning the language wrong because of an old tutorial).

---

### Post by mitchi on 2007-10-19
try to visit **[mitchi.wordpress.com]("http://mitchi.wordpress.com")**

go to the **LFP** section.

---

### Post by Keshik on 2007-10-19
> **Wybiral said:**
> To execute it use:
```

./my_program

```

EDIT:

lol, Keshik beat me to it!

Hah! I win ;)

And thanks for the explanation of what the "./" is for. Makes sense :)

---

