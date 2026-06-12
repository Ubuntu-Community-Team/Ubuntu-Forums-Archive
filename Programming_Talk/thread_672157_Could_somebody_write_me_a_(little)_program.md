---
title: "Could somebody write me a (little) program?"
date: 2008-01-19
forum: Programming Talk
---

### Post by Martje_001 on 2008-01-19
Hi,
Can somebody write me this in tk:
```

Question 1: What's your name?
INPUTBOX
echo $INPUTBOX to terminal

Question 2: What's you age?
INPUTBOX
echo $INPUTBOX to terminal
```

Please? :)

---

### Post by popch on 2008-01-19
Homework assignment?

---

### Post by aks44 on 2008-01-19
Does [this]("http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2") answer your question?


In the even I'm mistaken, you should ask specific questions (what are you stuck on?) as there's very little chance that anyone is going to help you if you're not willing to show that you at least tried.

---

### Post by LaRoza on 2008-01-19
> **Martje_001 said:**
> Hi,
Can somebody write me this in tk:
```

Question 1: What's your name?
INPUTBOX
echo $INPUTBOX to terminal

Question 2: What's you age?
INPUTBOX
echo $INPUTBOX to terminal
```

Please? :)

I am sure any Tcl/tk tutorial would give enough information to do this. See my wiki.

Noone is going to write this for you, if you have specific problems with Tcl, state them. It can be a confusing language at first.

---

### Post by Martje_001 on 2008-01-19
> **popch said:**
> Homework assignment?
No, it's just for myself ;).

Yes, I've tried to follow this tutorial:
[http://www.bin-co.com/tcl/tutorial/contents.php](http://www.bin-co.com/tcl/tutorial/contents.php)

But when I come to entry box:
```

proc push_button {} {
	.ent insert end "Hello"
}
entry .ent
button .but -text "Push Me" -command "push_button"
pack .ent
pack .but
```
I don't really understand why the message box doesn't close if I press "Push Me". And how can I make the input 'echo-ed' in the terminal?

---

### Post by LaRoza on 2008-01-19
> **Martje_001 said:**
> No, it's just for myself ;).

Yes, I've tried to follow this tutorial:
[http://www.bin-co.com/tcl/tutorial/contents.php](http://www.bin-co.com/tcl/tutorial/contents.php)

But when I come to entry box:
```

proc push_button {} {
	.ent insert end "Hello"
}
entry .ent
button .but -text "Push Me" -command "push_button"
pack .ent
pack .but
```
I don't really understand why the message box doesn't close if I press "Push Me". And how can I make the input 'echo-ed' in the terminal?

The Tk funtion for putting text to a terminal is "puts".

Why are you mixing GUI and terminal IO?

---

### Post by Martje_001 on 2008-01-19
> **LaRoza said:**
> Why are you mixing GUI and terminal IO?
Because I'm better with bash. I already wrote a bash script around ~500 KiB, which  needs input from a GUI.

thank you!

---

### Post by LaRoza on 2008-01-19
> **Martje_001 said:**
> Because I'm better with bash. I already wrote a bash script around ~500 KiB, which  needs input from a GUI.

thank you!

Did it work?

---

### Post by stevescripts on 2008-01-19
Martje_001 

More than you may ever want to know about tcl/tk:

[http://wiki.tcl.tk/](http://wiki.tcl.tk/)

Interactive experimentation in a tclsh will help -
just "package require Tk"  (no quotes)

FWIW - your little script does exactly what it is supposed to do.

I just took a quick look at the "tutorial" you referenced.

I suggest you look at this one instead : [http://en.wikibooks.org/wiki/Tcl_Programming](http://en.wikibooks.org/wiki/Tcl_Programming)
Written by a long-time friend of mine.

You might also take a look at the little wish program I put in the thread
"Hello Ubuntu" in every programming language - [http://ubuntuforums.org/showthread.php?t=497579&page=17](http://ubuntuforums.org/showthread.php?t=497579&page=17)
it might be helpful.

Again, if you're still stuck feel free to mail me

Steve

---

### Post by Martje_001 on 2008-01-20
> **LaRoza said:**
> Did it work?
Well, it was night here in Holland so I went to bed ;). I will continue after I've done my homework. 

> Again, if you're still stuck feel free to mail me

Steve
Thank you, I will sure do!

@stevescripts,LaRoza: Thank you very much for you help!

---

### Post by Martje_001 on 2008-01-20
I think I'm getting better :P.
```
proc push_button {} {
	.ent insert end "Hello"
}
```
This stands for what the "push_button" should do, right? Insert "Hello" at the end of the line.

What does:```

pack .ent
pack .but
```
stand for?

---

### Post by pmasiar on 2008-01-20
> **Martje_001 said:**
> 
@stevescripts,LaRoza: Thank you very much for you help!

You have little "thank you" button for that. Looks like a medal. Creates good karma for people providing good answers.

---

