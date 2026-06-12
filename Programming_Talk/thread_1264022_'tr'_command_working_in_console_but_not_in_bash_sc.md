---
title: "'tr' command working in console but not in bash script"
date: 2009-09-11
forum: Programming Talk
---

### Post by tgeer43 on 2009-09-11
Admittedly I'm fairly new to bash scripting. I've been putting together a script to handle most of my more mundane audio processing chores. All has been going extremely well with the following exception. I've got a line of commands to capitalize the first letter of each word in a song title. There are a number of ways to accomplish this but I'm trying to avoid calling other programs (ie. perl, ruby, awk, etc.). So I settled on using the 'tr' command to manipulate the string containing the file name.

If I enter this at the command line:
```
a="sample song title.mp3"; for i in $a; do b=`echo "${i:0:1}" | tr a-z A-Z`${i:1}; echo -n "$b "; done
```I get the desired output of: "Sample Song Title.mp3"

However, if I execute the same code in a shell script:
```
#!/bin/sh
a="sample song title"; for i in $a; do b=`echo "${i:0:1}" | tr a-z A-Z`${i:1}; echo -n "$b "; done
```I get the following error:
```
tgeer@tgeer:~$ sh ~/Scripts/process_mp3s.sh
/home/tgeer/Scripts/process_mp3s.sh: 2: Bad substitution
/home/tgeer/Scripts/process_mp3s.sh: 2: Bad substitution
```For the life of me I can't figure out why it's behaving differently when executed from within the script. Most likely I'm overlooking something fundamental about shell scripts but like I said, I'm kinda green in that department. :wink:

Would someone care to enlighten me?

Thanks in advance,

tgeer

---

### Post by Arndt on 2009-09-11
> **tgeer43 said:**
> Admittedly I'm fairly new to bash scripting. I've been putting together a script to handle most of my more mundane audio processing chores. All has been going extremely well with the following exception. I've got a line of commands to capitalize the first letter of each word in a song title. There are a number of ways to accomplish this but I'm trying to avoid calling other programs (ie. perl, ruby, awk, etc.). So I settled on using the 'tr' command to manipulate the string containing the file name.

If I enter this at the command line:
```
a="sample song title.mp3"; for i in $a; do b=`echo "${i:0:1}" | tr a-z A-Z`${i:1}; echo -n "$b "; done
```I get the desired output of: "Sample Song Title.mp3"

However, if I execute the same code in a shell script:
```
#!/bin/sh
a="sample song title"; for i in $a; do b=`echo "${i:0:1}" | tr a-z A-Z`${i:1}; echo -n "$b "; done
```I get the following error:
```
tgeer@tgeer:~$ sh ~/Scripts/process_mp3s.sh
/home/tgeer/Scripts/process_mp3s.sh: 2: Bad substitution
/home/tgeer/Scripts/process_mp3s.sh: 2: Bad substitution
```For the life of me I can't figure out why it's behaving differently when executed from within the script. Most likely I'm overlooking something fundamental about shell scripts but like I said, I'm kinda green in that department. :wink:

Would someone care to enlighten me?

Thanks in advance,

tgeer

Have you tried using /bin/bash instead of /bin/sh?

---

### Post by tgeer43 on 2009-09-11
No, I hadn't tried bash and always thought that bash and sh were interchangeable but after seeing your reply and doing a little reading I see that while very similar they are definitely not synonymous. In fact your suggestion worked perfectly and resulted in the desired output.

Do you happen to know specifically why sh can't handle this particular tr command while bash can? I've used tr before with the sh shell without incident. I know it must involve the handling of the $i variable but that's about all I know.

I guess the big questions now is: How will I know which shell is most appropriate for a given circumstance? I wouldn't mind changing my default shell to bash but don't want to run into any compatibility issues with existing scripts.

I really didn't need another monkey wrench in the works. I'm having enough trouble with the learning curve already.

Any advice?

tgeer

p.s. Thanks for the clue.

---

### Post by MadCow108 on 2009-09-11
the problem is the substring ${i:1:0} not the tr
that is apparently not support by the /bin/sh

is /bin/sh really your default shell?
I would recommend a bit more capable one like bash or ksh
scripts with the crunchbang #! will still call the shell they were made for, like /bin/sh.

---

### Post by tgeer43 on 2009-09-11
> **MadCow108 said:**
> the problem is the substring ${i:1:0} not the tr
that is apparently not support by the /bin/sh
Quite right. After a bit more reading I found that sh does not support the substring function.
> **MadCow108 said:**
> is /bin/sh really your default shell?
Until a few minutes ago it was. I changed it with the chsh command. I don't understand why it was because I'm the one and only user created during the install process and from what I've read the default should have been bash.
> **MadCow108 said:**
> I would recommend a bit more capable one like bash or ksh
scripts with the crunchbang #! will still call the shell they were made for, like /bin/sh.
That's what I needed to know. All of my user created scripts have the crunchbang so there shouldn't be any issues.

For anyone wanting to know the differences between various shells, there is a good article here:

_[COLOR=Blue][http://www.faqs.org/faqs/unix-faq/shell/shell-differences/](http://www.faqs.org/faqs/unix-faq/shell/shell-differences/)[/COLOR]_

Along with a lot of other good info, it contains a nice chart for a quick overview of the differences.

Thanks for all of your help, guys. I'm sure I'll be back with more questions.

tgeer

---

### Post by lensman3 on 2009-09-11
Try running your bash script as:

sh -xv "your script"           without the quotes.  Set if the verbose and execute mode will let you see the errors and the line more easily.

---

