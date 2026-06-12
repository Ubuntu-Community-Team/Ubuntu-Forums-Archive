---
title: "Pulling random text from a file in bash"
date: 2009-12-30
forum: Programming Talk
---

### Post by Max_Mackie on 2009-12-30
Ive got a text file full of block quotes (all separated by a blank line) and I would like to call this file and echo a random quote using bash.
Ive crawled around and Im not sure how to do this. Im also very new to bash.
Thanks for helping.

---

### Post by ghostdog74 on 2009-12-30
show examples and describe what you want from those examples.

---

### Post by Max_Mackie on 2009-12-30
Let's say my script goes something like this:

```

#!/bin/bash
echo Welcome to your computer
echo
"echo random quote"

```

Naturally, I would collect quotes and place them in a text file in blocks like this (using a blank line as a delimiter):

```
quote quote quote

quote quote
quote

quote quote quote quote

etc...
```

I hope you understand I'm trying to accomplish here :s
Thanks!

---

### Post by x33a on 2009-12-30
i think awk could help you out. though i cannot help as i am very poor with bash myself :P

---

### Post by ghostdog74 on 2009-12-30
```

awk 'BEGIN{RS="";srand()}
{
    quote[++c]  = $0
}END{
    RAND=int(rand()*c+1)
    print quote[RAND]
}
' file



```

---

### Post by Rany Albeg on 2009-12-30
though ghostdog's solution is much cleaner I'm giving another option :


[PHP]#!/bin/bash
#####################################################
# Output random text that is bounded by blank lines.
#####################################################

sen_loc=$HOME/Desktop/sentences #Location of file.
sen_arr=()                      #Array of sentences.
sen_rand=                       #Random sentence.

sen_arr=($(grep -n "^$" "$sen_loc"|sed 's/://')) #All blank lines.
sen_rand=$((RANDOM % (${#sen_arr[@]}-1)))        #Random index in sen_arr.
from="${sen_arr[$sen_rand]}"                     #From above random index.
to="${sen_arr[$((sen_rand+1))]}"                 #To next index in sen_arr.

echo "from : $from to: $to"
sed -n "$from,$to"p "$sen_loc" #Print from-to range

exit 0[/PHP]

---

### Post by Max_Mackie on 2009-12-30
Thanks guys.
ghostdog (this might be completely obvious), but the " 'file " part. What does that mean? Where exactly am I editing this code?

Rany, ive got my file made but it still doesnt seem to work. I believe im calling it correclty. When run in a terminal I get this:

line 12: RANDOM % 0: division by 0 (error token 0)
sed: -e expression #1, char 1: unknown command: ","

Sorry, Im sure this is completely obvious but its the first time i dabble in these things :)

---

### Post by MaxIBoy on 2009-12-30
There is already a program to do this, it's called "fortune." Find it in the repos, read the man page. You can tell it to use a custom database of "fortunes" and select one at random.
[https://www.linuxquestions.org/questions/linux-software-2/how-to-create-fortune-database-221315/](https://www.linuxquestions.org/questions/linux-software-2/how-to-create-fortune-database-221315/)

You only need to do this stuff once for each edit of your database:
```
gedit database_file #edit the database to your satisfaction, add all the quotes you need.
strfile database_file #generate a database_file.dat, 
#which should be kept in the same folder as your main database_file. 
#neither file should be deleted. However, you can move them around.
```Then, just cd to the directory of your database and
```
fortune database_file
```


The difference is that instead of blank lines, it uses a line with a single "%" on it.

---

### Post by Max_Mackie on 2009-12-30
Thanks MaxIBoy, it seems to work!
The only thing is, its only recognizing my file as 1 string :S
I've formatted it correctly, Im sure. I even tried making another file with slightly smaller quotes just to check and it worked. What could be causing this?

---

### Post by MaxIBoy on 2009-12-30
Seems to be working for me, and I know fortune can handle some really long quotes. You can see some other examples in /usr/share/games/fortunes. 

Could you show us what is in the database file (assuming it's not sensitive information or something?)

Each entry needs to be separated by a single line with nothing but the character "%" in it. You need to run the strfile command whenever you make a change to your database.

If that doesn't help, I'm not sure what the issue is.

---

### Post by Max_Mackie on 2009-12-31
Yeah your first post was super clear. I even tried it on another smaller file.
My guess is its either some of the symbols in the quotes and/or the length of the file (but technically that shouldn't matter, right?)

I attached the file.

---

### Post by MaxIBoy on 2009-12-31
It is working OK for me.

However, there is one possibilty. I just happened to open it with notepad on a windows box, and it didn't suffer from [lack of carriage return.]("http://kb.iu.edu/data/acux.html") If it had been created with any UNIX text editor, there would have been little squares instead of new lines. But notepad displayed it OK. Then I pasted it into a gedit window I had running over SSH on my Linux server, and of course it deleted any carriage returns when saving the file.

In other words, it looks like the file was created using a Windows text editor, or a text editor in some kind of Windows compatibility mode, or something was originally copied from a Windows text file, thus it has carriage returns in it. I don't think that would cause the problem, but it's the only reason I can think of why it would work for me and not you on the exact same file.

Since my gedit would have auto-corrected that potential problem when saving it, and since I'm conveniently working with my server here, I'm hosting it for you here:
<LINK REMOVED>
Try downloading that version, re-running the strfile command on it, see if it works then.

---

### Post by Max_Mackie on 2009-12-31
It worked perfectly :)
And you're right, it was created in a windows system and then I transferred in onto my ubuntu box. Thanks ALOT for your help on something that was so......easy :)

---

### Post by MaxIBoy on 2009-12-31
No problem. The carriage return thing wouldn't have been at all obvious. It's something you just need to find out by having something break. (For me it was having someone complain about the weird text files I was sending her... oops!)

You can mark the thread as solved so that people googling for the same problem can see it has a solution. It's in the "thread tools" menu right above the first post.

I trust you got the file downloaded OK, I'm removing it from the server.

---

### Post by Max_Mackie on 2009-12-31
I got the file, everything is a-ok.
Thanks again.

....damn windows...

---

### Post by Rany Albeg on 2009-12-31
Max_Mackie , 

I forgot a -1 in line 11 so i edited to code.
Also be sure that the whole text is bounded by blank lines.
It needs to start with a blank line and end with a blank line.

Actually , i used blank lines to bound a sentence , so you must start the text file with a blank line in order to randomly select the first sentence and the same for the last sentence.
The -1 i forgot to add is for telling the program not to select the last blank line as lower bound - because the file ends there.

It seems to work fine after a few tests i made.

I hope it will be useful but i still think ghostdog's solution is better and simpler.

Have a nice day.

---

