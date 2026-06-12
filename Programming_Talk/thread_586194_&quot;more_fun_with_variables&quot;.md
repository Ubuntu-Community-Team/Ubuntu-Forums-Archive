---
title: "&quot;more fun with variables&quot;"
date: 2007-10-22
forum: Programming Talk
---

### Post by nickoli on 2007-10-22
I'm having a heck of a time writing a script that is passed four arguments. the first argument is a file extension and the next three are regular expressions. it must search my current directory and only list the name of the files that contain all three regular expressions. So far all my attempts have been horrendous
I started out like this.
filename=$1
reg1=$2
reg2=$3
reg3=$4
a=find "*$filename" | sed "s/$reg1,$reg2,$reg3/$a/"
I'm not even sure I have the proper syntex for the sed command. Am I on the right path or am I even close. Any help will be appreciated. Thanks for your time.

---

### Post by cwaldbieser on 2007-10-22
How about:

```

find -f -iname "*$EXTENSION" -print | grep -e "$regex1" | grep -e "$regex2" | grep -e "$regex3"

```

---

### Post by ghostdog74 on 2007-10-22
my advice, is to start reading and practicing with  a unix shell scripting book/site.

---

### Post by nickoli on 2007-10-22
I'm actually enrolled in a college course for unix programming. I need some more help than the book or my lectures seem to provide. I figure if I get stumped theres a reason so thats why I come here to help figure out why I'm stumped. I don't just copy the programs word for word I look at how someone with some knowledge would approach the problem than I play with it until I understand it. I use my book and class lectures plus what ever advice I can attain here. So far I have this as my program.

file="$1"
reg1="$2"
reg2="$3"
reg3="$4"
if grep "$reg1" *$file | grep "$reg2" *$file | grep "$reg3" *$file
then
    echo *$file
else
   echo file not found
fi

It works great except for a tiny little problem. It will echo the name of the regular expressions I pass it. It also echo's the filename which is perfect I just need to stop it from echoing the regular expressions and I'll be happy. Any help anyone can give me in this matter will be greatly appreciated.Thanks.:)

---

### Post by nickoli on 2007-10-22
I solved my problem and the program works perfectly. All I had to do was add >/dev/null to the end of the if statement. Thanks everyone for your time.:popcorn:

---

