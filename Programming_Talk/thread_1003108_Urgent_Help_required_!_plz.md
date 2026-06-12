---
title: "Urgent Help required ! plz"
date: 2008-12-05
forum: Programming Talk
---

### Post by cation007 on 2008-12-05
Hi,
I am trying to find out if a string contains tab or not.

I tried using if [[ $string == *\t* ]]

but it is not detecting some lines containing tabs.

Is the syntax wrong ?

I have do it in BASH and not any other language.

Please Help :(


Thanks,

---

### Post by p_quarles on 2008-12-05
> **cation007 said:**
> Hi,
I am trying to find out if a string contains tab or not.

I tried using if [[ $string == *\t* ]]

but it is not detecting some lines containing tabs.

Is the syntax wrong ?

I have do it in BASH and not any other language.

Please Help :(


Thanks,

Hi, 

We will not do your homework for you. So, to help allay any suspicions, please explain why 

A) this is "urgent"

and 

B) you have to use Bash. 

Thanks

---

### Post by kjohansen on 2008-12-05
try

```

if [[ $string =~ *\t* ]]


```

*notice the ~

---

### Post by Phenax on 2008-12-05
```
if [[ $string =~ \t ]]
```
Asterisks would mess it up.

---

### Post by slavik on 2008-12-05
> **p_quarles said:**
> Hi, 

We will not do your homework for you. So, to help allay any suspicions, please explain why 

A) this is "urgent"

and 

B) you have to use Bash. 

Thanks
I am really interested in answers to A and B :)

---

### Post by ghostdog74 on 2008-12-05
> **cation007 said:**
> Hi,
I am trying to find out if a string contains tab or not.

I tried using if [[ $string == *\t* ]]

but it is not detecting some lines containing tabs.

Is the syntax wrong ?

I have do it in BASH and not any other language.

Please Help :(


Thanks,

and what are you going to do after you detected tabs? do you want to remove them? If that's the case, there's no need to check for tabs. Just remove them.

---

### Post by p_quarles on 2008-12-05
Several people have posted answers, which I have made invisible as of now.

Don't do that, people. Read the thread first.

---

### Post by kjohansen on 2008-12-05
his problem is more than likely a typo that he does not see.  He posted the entire solution that he needs with one symbol incorrect, even if it is homework, he isnt asking for an entire solution without providing work, all he needed was some "proofreaders" to help him see what he has missed.

---

### Post by Sinkingships7 on 2008-12-06
Yeah, last I checked, we gave help to those who gave an honest effort. This is a simple problem, and the OP's provided his code in order to show that he's attempted this. I'm sure he'll figure it out on his own before he comes back here, but that's not the point.

Setting aside the fact that the title was a little strong, I see nothing wrong with helping this person.

---

### Post by cation007 on 2008-12-06
wow.
So many replies...

Thanks for the replies.

Yes. It was a small part of my homework.
I searched google but nothing was helpful. 
I tried all the regexps I knew but nothing helped.

So, I thought I would give it a shot.

For some reason, the solutions provided here also did not work. So, I came up with my own using awk.

Thanks,

---

### Post by p_quarles on 2008-12-06
> **cation007 said:**
> wow.
So many replies...

Thanks for the replies.

Yes. It was a small part of my homework.
I searched google but nothing was helpful. 
I tried all the regexps I knew but nothing helped.

So, I thought I would give it a shot.

For some reason, the solutions provided here also did not work. So, I came up with my own using awk.

Thanks,
Well, first of all, thanks for being honest.

Beyond that, please understand that this isn't a homework service, and we frown on questions like this. That said, and as others have pointed out, you did put in most of the work needed.

Just understand that when we see someone with a low post count posting a question that screams "homework assignment," a lot of red flags are raised. Good luck with the rest of the current term. :)

---

### Post by slavik on 2008-12-06
> **p_quarles said:**
> Well, first of all, thanks for being honest.

Beyond that, please understand that this isn't a homework service, and we frown on questions like this. That said, and as others have pointed out, you did put in most of the work needed.

Just understand that when we see someone with a low post count posting a question that screams "homework assignment," a lot of red flags are raised. Good luck with the rest of the current term. :)
commies raise red flags regardless :D

but yeah ... big difference between == and =~ ... I am sure =~ isn't part of the POSIX standard.

---

