---
title: "[Python]Thinking like a programmer....."
date: 2009-11-03
forum: Programming Talk
---

### Post by swatto on 2009-11-03
Hey all  

Im currently reading a book (Python Programming for the Absolute Beginner second Edition) about Python and learning about the language, im understanding everything I read and when I look at the code I understand how it works however when I think to myself about how I would go about solving the same problem I have no idea where to start and how to write the code or structure it (its like I look at the code and it seems very intelligently written and I couldn't see myself producing something as complex/similar). 

Please could anyone tell me if they thought the same thing when first learning about programming as it puts me off continuing because I look at it and think there is no way I could write something like that.

Thankyou for any help

---

### Post by pi4r0n on 2009-11-03
Same with me and to the honest with you I hate that. I really would like to learn how to program and just f..... can not :(

I do understand JAVE, Bash, Ruby and Perl scripts so I don't know what is wrong with me :(

Ta

pi4r0n

---

### Post by brydonhunter on 2009-11-03
I guess the only suggestion I can offer is just to sit down and code. The more you code, the easier it will be to ***create*** code. You will start to develop your own style and thought processes.

Don't give up, this is common as far as I'm concerned.

---

### Post by Arndt on 2009-11-03
> **swatto said:**
> Hey all  

Im currently reading a book (Python Programming for the Absolute Beginner second Edition) about Python and learning about the language, im understanding everything I read and when I look at the code I understand how it works however when I think to myself about how I would go about solving the same problem I have no idea where to start and how to write the code or structure it (its like I look at the code and it seems very intelligently written and I couldn't see myself producing something as complex/similar). 

Please could anyone tell me if they thought the same thing when first learning about programming as it puts me off continuing because I look at it and think there is no way I could write something like that.

Thankyou for any help

I googled for "how to program" and several quite useful-looking hits turned up. Maybe one of those will help you. The first one used Python as its language, too.

---

### Post by Arndt on 2009-11-03
> **Arndt said:**
> I googled for "how to program" and several quite useful-looking hits turned up. Maybe one of those will help you. The first one used Python as its language, too.

And here is a whole (online, free) book, which looks good: [http://htdp.org](http://htdp.org). Someone (I forget who) mentioned it in some recent thread here.

---

### Post by tribaal on 2009-11-03
I had the same problem, and for be the turning point was to learn to decompose problems in "big chucks", then divide theses chunks into smaller components, then take one component and start thinking how it should work, then, finally, code it.

(Artificial) Example: I want a notepad application that will do synthax coloring

Big chunks:
- I want to be able to input text in a GUI (could be command line), so I need to find out how to make a GUI
- I want to save that text to the filesystem (I need to know how to write text to a file)
- I want to know how to color text (make text appear in a specific color)
- I want to change colors based on rules

So for example, the last item: 
"I want to change colors based on rules", you will:
- code one function that takes text as input, and a "rule", and output wether it matches or not.
- Add complexity to this until it reaches what you intend (you have to define what a "rule" is: is it a regexp? Is it natural speech?)

Once you break down problems in small, manageable parts life as a programmer becomes much easier.

Also, keep coding until your small problem is *solved*. I never get anything done if I jump from one to the other all the time.

That's just my 2 cents, I know it worked for me. Really, don't be scared to experiment :)

- Trib'

---

### Post by swatto on 2009-11-03
> **Arndt said:**
> And here is a whole (online, free) book, which looks good: [http://htdp.org](http://htdp.org). Someone (I forget who) mentioned it in some recent thread here.

Many thanks for your help - I will have a read ;)

---

### Post by underquark on 2009-11-03
Don't just read.  Do programming.

I think I was the same when I first learned to read (English) and then when I learnt to read music and then Basic and then Delphi etc.  i.e. it's normal.

With practice, the bits of your brain that do the learning of something physically alter until everything just clicks. It would be interesting to see a study of functional MRI scans in peolpe who have never programmed and then get them to do some programming and scan them again.  It's been done with London cab drivers, for instance, and they have been shown to have functionally and structurally different brains to non-cab drivers.  q.v. [here](http://www.boingboing.net/2008/09/14/inside-a-london-cabd.html).

---

