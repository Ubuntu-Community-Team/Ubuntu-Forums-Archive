---
title: "hello need help cat &amp; gep funcions"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by saltenis on 2013-06-11
hello i have work and idk how use thogether cat and grep. 
here me task: 
Create a script that find this file all records of Johns and put them in a file zmonesj.txt

i done cat > zmones.txt
[FONT=monospace]Johns 1990
[/FONT]

[FONT=monospace]Petras 1989[/FONT]

[FONT=monospace]Linas 1991[/FONT]

[FONT=monospace]Jonas 2000[/FONT]

[FONT=monospace]Vaidas 1988[/FONT]

[FONT=monospace]Johns 1993
command ctrl+z
cat > zmonesj.txt

Create a script that find this file all records of Johns and put them in a file zmonesj.txt

cat zmones.txt>zmonesj.txt - zmones.txt where insert GREP and transfer Johns
[/FONT]
[FONT=monospace] 
[/FONT]

---

### Post by squakie on 2013-06-11
We're not here to do your homework for you.  Also, avoid things like "idk" as there are many English as a 2nd language people here (and some of us old folks) who prefer complete words.

---

### Post by saltenis on 2013-06-11
plesae help me i will avoid "IDK"

---

### Post by Impavidus on 2013-06-11
grep will read input and search for a pattern in every line. If the pattern is present, it writes the line to standard output. Add a redirect to get it into an output file. Use **man grep** for more details on grep. If you want to use the command line it's best to get used to reading man pages. You may want to search the internet on how to use pipes.

---

