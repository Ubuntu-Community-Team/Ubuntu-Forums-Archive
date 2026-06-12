---
title: "very veryurgent..shell script needed...assignment tommrrow is last date of submission"
date: 2008-04-03
forum: Programming Talk
---

### Post by Avikal on 2008-04-03
plz help..................tommrrow final day ...other wise will flunk....see the attachment

---

### Post by CptPicard on 2008-04-03
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by ghostdog74 on 2008-04-03
i will not do your homework..however, i can at least provide you some guidance. If you click at the Learn Bash Scripting link in my sig, you can go to  [this page ]("http://tldp.org/LDP/abs/html/parameter-substitution.html#VARMATCH")to see how you can get the first part of the file before the extension
next you can go to see [Simple for loops]("http://tldp.org/LDP/abs/html/loops1.html#EX22") where you can use it to loop through your files one by one. To unpack files, read the man page of tar command.

---

### Post by sekinto on 2008-04-03
I sent you a message how to do it in Python, of course you have to custom fit the code to the types of archives you will be extracting. Please look over the code and learn from it.

---

### Post by Avikal on 2008-04-03
help plz......i kno ur policies......was enrollled 3 days back n now the assignment....plz:confused:

---

### Post by pedro_orange on 2008-04-03
We don't do homework.

I just did a google, and found a script you can use to get you 55% with a bit of tweaking. Have you heard of google? 
[www.google.com](www.google.com)

The remainder of the assignment is only a little extra tweaking. This could be done in 30 minutes if you put your mind to it.

---

### Post by Wybiral on 2008-04-03
[IMG]http://ubuntuforums.org/customavatars/avatar148462_3.gif[/IMG]

=D>

---

### Post by Siph0n on 2008-04-03
I love these threads :) Very urgent, homework is due!!! :) You know the policies of the forum, yet u still wanna go against them? ... It looks like you didn't even try the problem... Have you?

---

### Post by CptPicard on 2008-04-03
Yeah, well, you know, I've got this WORK assignment due like yesterday, and my boss is breathing down my neck... plz do it for me!!1 HELP

---

### Post by pedro_orange on 2008-04-03
> **CptPicard said:**
> Yeah, well, you know, I've got this WORK assignment due like yesterday, and my boss is breathing down my neck... plz do it for me!!1 HELP

Spend less time on these forums & more time in debug!

---

### Post by brennydoogles on 2008-04-03
> **Avikal said:**
> help plz......i kno ur policies......was enrollled 3 days back n now the assignment....plz:confused:

How long ago was the project assigned? Have you written any code for it yet? If you would be willing to post evidence that you have tried ANYTHING, people might be willing to help save your rear. Until then, I fear you may be SOL.

---

### Post by Bruce M. on 2008-04-03
> **ghostdog74 said:**
> i will not do your homework

Good for you.  :)

And a HUGE [SIZE="5"]Thank You[/SIZE] for the links in your sig for bash scripting.

New to Linux and just stretching my wings with bashrc aliases and stuff. I hope that link helps.  :)

Have a nice day
Bruce

---

### Post by CptPicard on 2008-04-03
Yeah, actually, thanks as well. I would have been stumped (without researching of course) at how to strip the file extension...

---

### Post by Avikal on 2008-04-05
dir=`pwd`
mkdir archive_store
ls -lrt | grep .tar | awk '{ print $9 }' > tmp.txt
for file_names in `cat tmp.txt`
do
cd $dir
len=`echo $file_names |wc -c`
name_len=`expr $len - 5`
mkdir `echo ${file_names:0:$name_len}`
mv $file_names `echo ${file_names:0:$name_len}`
cd `echo ${file_names:0:$name_len}`
tar -xvf $file_names
mv $file_names ../archive_store
done
cd $dir;rm tmp.txt

---

### Post by aysiu on 2008-04-05
Yeah, as people have mentioned, it's up to you to do your own homework. People have also been kind enough to post guidance on where to go from here. So, with that, I'm closing this thread.

---

