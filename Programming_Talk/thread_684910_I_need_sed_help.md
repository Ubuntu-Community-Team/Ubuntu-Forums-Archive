---
title: "I need sed help"
date: 2008-02-01
forum: Programming Talk
---

### Post by newnet on 2008-02-01
```
ls -1 | sed <insert missing code>
```
What I am trying to do is have sed print the file names twice.  So it would look something like this:
```

first.foo first.foo
second.foo second.foo
third.foo third.foo

```
Must be sed; no awk or others please.  If it can not be done with sed, let me know.

---

### Post by YoG%*@ on 2008-02-01
hi,

how about something like 
```
for file in `ls`; do echo $file $file; done
``` ?
would that be an option (i know it's not using sed, but maybe it can help you anyway) ? 

hth,
mux

---

### Post by ghostdog74 on 2008-02-01
> **mux said:**
> hi,

how about something like 
```
for file in `ls`; do echo $file $file; done
``` ?
would that be an option (i know it's not using sed, but maybe it can help you anyway) ? 

hth,
mux

Use shell expansion, instead of ls
```

for file in * 
do
 .....
done

```

---

### Post by ghostdog74 on 2008-02-01
> **newnet said:**
> 
Must be sed; no awk or others please.  If it can not be done with sed, let me know.

then you must be doing some homework or assignment. I am going to give you awk solution anyway
```

ls -1  | awk 'print $0 , $0 }'

```

---

### Post by newnet on 2008-02-01
Thanks, mux!  It did the job fine.

However, I am still curious how it is done with sed.  If anyone knows, please show me.

ghostdog74, the code from mux worked fine.  On the contrary, your code did not work, because bash thinks "....." is a command.

Additionally:

> then you must be doing some homework or assignment.
Way to go on making a blunt assumption there, ghostdog74.

If so, it would have been far more convenient to post the entire homework and assignment and have others do it for me, yes?  Of course.

If I am really doing my homework or assignment, and asked a question, would it really hurt to help answer a single question?  Or are you too elite to help others?

If you must know (even if you did not asked), it is because I asked the question 2 days ago, and I have already been given an answer in awk here:

[http://ubuntuforums.org/showthread.php?t=682763](http://ubuntuforums.org/showthread.php?t=682763)

Some people ask for help in a specific program/language/tool because they do not want to learn/use a new program/language/tool for something so small.

> I am going to give you awk solution anyway
If someone asked not to give it in awk specifically (a good guess would be they do not want to know or already know in awk) and you still do it for the emotional response, it constitutes as trolling.

---

### Post by pmasiar on 2008-02-01
> **newnet said:**
> 
Way to go on making a blunt assumption there, ghostdog74. ...

Or are you too elite to help others? ...

If you must know (even if you did not asked), it is because I asked the question 2 days ago, and I have already been given an answer in awk here:

...it constitutes as trolling.

If you bothered to post this awk-solution link when you asked for help, ghostdog would not wasted his valuable free time writing answer for you.

Or you are too elite to bother, and forum volunteers re your slaves? And then, after you are given decent answer to your incomplete description, you try to judge a person, who volunteered time for you? Good way to gain friends.

---

### Post by LaRoza on 2008-02-01
> **newnet said:**
> 
ghostdog74, the code from mux worked fine.  On the contrary, your code did not work, because bash thinks "....." is a command.

If so, it would have been far more convenient to post the entire homework and assignment and have others do it for me, yes?  Of course.

If I am really doing my homework or assignment, and asked a question, would it really hurt to help answer a single question?  Or are you too elite to help others?

If someone asked not to give it in awk specifically (a good guess would be they do not want to know or already know in awk) and you still do it for the emotional response, it constitutes as trolling.

The elipsis was meant to signify "your code here".

If the other code worked, why do you need it in sed?

Yes, homework is not allowed. Are you trying to get a rise out of ghostdog74 by making accusations of elitism and trolling? Those are pretty insulting accusations.

The problem has been solved, albeit using a different tool. Perhaps if you gave a reason for the sed requirement so homework isn't suspected, you'd get a better response.

---

### Post by ghostdog74 on 2008-02-01
> **newnet said:**
> 

ghostdog74, the code from mux worked fine.  On the contrary, your code did not work, because bash thinks "....." is a command.

here's why mux code may not work.
```

# touch "files with spaces"
# touch file.with.no.spaces
# ls
file.with.no.spaces  files with spaces
# for file in `ls`
> do
> echo $file
> done
file.with.no.spaces
files
with
spaces
# for file in `ls`
> do
> echo "$file"
> done
file.with.no.spaces
files
with
spaces
# for file in "`ls`"; do echo "$file"; done
file.with.no.spaces
files with spaces
# for file in *
> do
> echo $file
> done
file.with.no.spaces
files with spaces

```

using `ls`, you have to take care of files with spaces....

---

### Post by Trumpen on 2008-02-02
@ ghostdog74

I don't want to seem too fussy but actually 

```
 for file in "`ls`"; do echo "$file"; done
```

is not suitable because it doesn't work as it may appear. 
In fact in the above code "`ls`" returns a single string with each filename separated by a newline character. 
These newlines are then interpreted "correctly" by *echo* but actually the for loop lasts only one iteration.

You can check it by running this snippet:

[PHP]count=0;

for file in "`ls`"; do 
          echo "$((count++)) $file"; 
done[/PHP]

$count is incremented only one time.

So, in the rare event you need to use `ls` instead of *, you can solve the files-with-spaces problem by assigning a new value to the Internal Field Separator ($IFS):

[PHP]OLD=$IFS;
IFS=$'\n'; 

for file in `ls`; do 
         echo $file; 
done;

IFS=$OLD[/PHP]

@newnet

if you want to use *sed* you can try this:

```
ls -1 | sed 's/^.*$/& &/'
```

Hope this helps!

---

### Post by newnet on 2008-02-04
Kudos!  Trumpen, thank you very much!

> If you bothered to post this awk-solution link when you asked for help, ghostdog would not wasted his valuable free time writing answer for you.
The real reason I kept out of Programming Talk in the first place is because there are people like you around.  You are not even devoting to the topic; you only posted to defend ghostdog74 and at the same time take a jab at me.

Tell me, is mentioning "no awk" too hard to understand?  Must I provide all known or other solutions too in which I do not want in order not to be given that solution anyways?

If someone says "no awk" and someone gives it in awk anyways, it does not help at all.

Was I being too rude when I said "**no** awk or others **please**"?  So much so that I needed to be taunted?

And no, he did not waste his valuable free time writing the answer for me.  He **knew** that was not the answer I was looking for; he replied for other reasons.  If ghostdog74 did not want to help in compliance with my specific request, then he should have not replied.

In accordance to "How to ask a question properly", I was specific on what I would like to use (sed) for the solution.  Moreover, I was also specific on what not to use (awk) for the solution.

Should I have titled my topic with "I need help!", then in the topic asked "How do I print the file name twice?"  A very good chance the first question asked back would be "With what tool/language/program?"  Or would people take their time and give me all the possible answer: bash, sed, awk, python, ruby, C, C++, etc.?

If I asked without specifying the tool I would like to use, I am sure I will get different answers.  That would be the real "wasted" time.

> Or you are too elite to bother, and forum volunteers re your slaves?
All help topics are requests; not orders.  People who know the answer have the choice to answer or not.  If they do not want to help, fine.  But there is no need to provoke the OP.
> And then, after you are given decent answer to your incomplete description,
See the long reply above.  I was **specific**; I was not looking for any answer.

And about the "incomplete description", which part of "What I am trying to do is have sed print the file names twice" is "incomplete"?  The first person who responded understood it fine.  No one as yet been confused over what I am trying to ask for in my "incomplete description."  Knee jerk.

> you try to judge a person, who volunteered time for you? Good way to gain friends.
Again, he did not reply to help but to taunt.

> If the other code worked, why do you need it in sed?
I did not want to post the entire background story.  If you are curious, then I will tell you: I already know some sed.  Therefore, I wish to continue using/learning sed.  I believe that if something can be done with a certain utility, and I already have some experience with it, then I should use it more.  

Coding a little bit in sed, coding a little bit in awk, and many more bits in others just makes my scripts look disorderly. 

Usually, sed has the shortest codes for editing texts.  The basic shell only displays 80 characters in length; anymore it would be truncated and require me to scroll.  Breaking the code into a new line is possible, but I rather not.  So I can fit more code into the screen.

> Are you trying to get a rise out of ghostdog74 by making accusations of elitism and trolling? Those are pretty insulting accusations.
No, but I based it on something.  Albeit very limited, but nonetheless, something.  He accused me of trying to pass my homework/assignment onto others to do.  Because of what?  I did not declare "This is not homework/assignment!" in the topic?  I do not think that is needed.  If he asked if this is homework/assignment or not before deciding to help or not, that is fine.  But taunting was uncalled for.

> The problem has been solved, albeit using a different tool. Perhaps if you gave a reason for the sed requirement so homework isn't suspected, you'd get a better response.
I was not aware this is a suspicion-prone forum.  And seriously, it is 1 question.  I do not see how that justifies the suspicion of someone not doing their homework/assignment.

I did not give a reason for the sed specification because I wanted to keep it short and simple.

I give out (a) reason(s) why I want sed instead of awk or others, it will just turn it into a discussion of what is better than what.

The answer has been given (thanks again)!  Best if a moderator closed this thread.

---

### Post by LaRoza on 2008-02-04
> **newnet said:**
> 
I was not aware this is a suspicion-prone forum.  And seriously, it is 1 question.  I do not see how that justifies the suspicion of someone not doing their homework/assignment.

The answer has been given (thanks again)!  Best if a moderator closed this thread.

This forum gets a lot of requests for homework. If something looks like homework, it is suspected. I am not accusing you, but some thought it looked like it and were hesitant to completely answer.

At your request, I am closing it for you.

---

