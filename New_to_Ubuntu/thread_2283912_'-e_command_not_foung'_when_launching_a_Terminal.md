---
title: "'-e: command not foung' when launching a Terminal"
date: 2015-06-25
forum: New to Ubuntu
---

### Post by obergam on 2015-06-25
I setup my machine with Selenium IDE and other tools to use for automation. I had to overwrite the PYTHONPATH and I think there was a typo so I had to run the commands twice. I ended up getting '-e: command not found' every time I launch a Terminal.

Can someone help please ? :)

---

### Post by steeldriver on 2015-06-25
Hello and welcome to the forums

It would help if you could tell us what "the commands" were that you ran twice

However (at a guess) you appended something to your ~/.bashrc or ~/.profile or ~/.bash_profile file - and you will need to open the file in question and correct it

---

### Post by obergam on 2015-06-25
This is what I ran twice:

a) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/obergam/Desktop:$PYTHONPATH' | tee -a ~/.bashrc 
b) echo -e '# Overwrite PYTHONPATH\nexport PYTHONPATH=/home/obergam/Desktop:$PYTHONPAT H' | tee -a ~/.profile

thank you

---

### Post by yetimon_64 on 2015-06-25
Removed, wrong info... thanks for picking that up steeldriver. You're right of course I did "unbalance" the quotes, sorry for the misinfo.

---

### Post by steeldriver on 2015-06-25
@yeti each echo contains 2 lines (note the [FONT=courier new]\n[/FONT], and the use of [FONT=courier new]-e[/FONT] to allow its interpretation): the first is a comment and the second is an actual [FONT=courier new]export[/FONT] command

The [FONT=courier new]| tee -a ~/.bashrc[/FONT] should **not** be part of the quoted string - and your version has unbalanced quotes (count 'em: 3)

The commands that obergam posted are fine IMHO with the exception of the space in the final [FONT=courier new]$PYTHONPA[COLOR=#ff0000]T H[/COLOR][/FONT] - but possibly mistype in practice (putting the *first* quote before the -e perhaps?)

Regardless, the answer is to open up the two files in question and fix them

---

### Post by obergam on 2015-06-26
How do I open the two files and fix them?

---

### Post by Habitual on 2015-06-26
> **obergam said:**
> How do I open the two files and fix them?
in a terminal >
```
bash --norc
```
then ```
vi .bashrc
```
and then ```
vi .profile
```
and remove the offending line(s) from each.

Or you can simply run ```
gedit $HOME/.bashrc
```
and
```
gedit $HOME/.profile
```
How that's 'run' on Ubu, I have no idea, I use Alt+F2 on my distro.

---

### Post by obergam on 2015-06-26
I've removed the lines but how do I save and quit Vim?

---

### Post by obergam on 2015-06-26
I found the answer here:
[http://askubuntu.com/questions/252760/how-do-i-save-files-edited-with-vim](http://askubuntu.com/questions/252760/how-do-i-save-files-edited-with-vim)

Thank you so much, problem is fixed

---

### Post by sandyd on 2015-06-26
Hi, if you have found a solution, please mark thread as solved via

Thread Tools -> Mark Thread As Solved.

Thanks!

---

### Post by llamabr on 2015-06-27
vim is great, obviously, but for those a bit newer to editing text files, try nano, or gedit.  nano has a handy set of commands at the bottom, in case you forget how to exit.

---

