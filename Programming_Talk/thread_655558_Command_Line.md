---
title: "Command Line"
date: 2008-01-01
forum: Programming Talk
---

### Post by havfunonline on 2008-01-01
I imagine this doesn't belong here, as its not strictly speaking programming, but I'll go for the question anyway.

I'm a complete Linux noob, but I've programmed before (HTML/CSS, Pascal, Java [but not a great deal]), and after just using Linux for about 4 days, I've discovered the incredibly necessity for commandline programming, which I have no idea about and fascinates me.

My question is essentially this: "How do I go about learning Command Line?"

---

### Post by Vixis on 2008-01-01
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by tadcan on 2008-01-01
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Also I found a book called 'Easy Linux Commands' by Emmons and Clark
 isbn 0975913506'

---

### Post by CptPicard on 2008-01-01
I suggest you just learn by using it. First learn the basics -- built-ins and the most common external commands. Then, check out pipes and redirection to and from files. Then, at least browse through some command and tool reference so that you at least know what sort of stuff is there, but don't bother learning them all at once. At this point you'll be a power-user.

I really wouldn't bother "programming" in shell, there are better ways to do that. Whenever you're doing something beyond a one- or two-liner or a really simple loop or a sequence of the aforementioned, move over to something more comfortable like Python...

---

### Post by MicahCarrick on 2008-01-01
When I first migrated to Linux, I found that going through a Linux System Administration book useful. It will give you introductory experience with basic commands, a bit of shell scripting, and use of standard utilities.

---

### Post by ghostdog74 on 2008-01-01
> **CptPicard said:**
> 
I really wouldn't bother "programming" in shell, there are better ways to do that. 
Some people are comfortable with shell programming. Just like you  are comfortable with Python. Let's be objective here. You don't encourage people like that.

---

### Post by ghostdog74 on 2008-01-01
> **havfunonline said:**
> "How do I go about learning Command Line?"
See [here]("http://www.ssuet.edu.pk/~amkhan/Linuxbooks/(ebook%20pdf)%20Teach%20Yourself%20Shell%20Programming%20in%2024%20Hours.pdf") for a start. After that [here ]("http://www.unix.org.ua/orelly/unix/sedawk/index.htm")and [here]("http://tldp.org/LDP/abs/html/")

---

### Post by CptPicard on 2008-01-01
> **ghostdog74 said:**
> Some people are comfortable with shell programming. Just like you  are comfortable with Python. Let's be objective here. You don't encourage people like that.

I'd say I'm comfortable with anything but shell and not necessarily a *huge* Python fan, and that I strongly feel like bash in particular should die and be replaced with something better, but unfortunately, old habits die hard. Some people might be comfortable with BASIC and I'd say the same thing.

IMO I am encouraging OP to recognize -- in particular if he's a programming beginner -- that the shell is good as I/O glue between tools, but that if one is interested in *programming*, time may be better spent looking elsewhere. Who knows, perhaps he will code us a better shell... it's good to know where to start, but also good to know where to stop ;)

---

### Post by bruce89 on 2008-01-01
It depends what you're trying to do, bash (or in fact dash in Ubuntu) should be used for wee scripts, "proper" languages for applications.

---

### Post by ghostdog74 on 2008-01-02
> **CptPicard said:**
> I'd say I'm comfortable with anything but shell and not necessarily a *huge* Python fan, and that I strongly feel like bash in particular should die and be replaced with something better, but unfortunately, old habits die hard. Some people might be comfortable with BASIC and I'd say the same thing.

These are your preferences so its up to you. I am not about to disagree with that.

> 
 that the shell is good as I/O glue between tools
So is every other languages. In Python, for example you can use shutil module to copy and move files. How do you do that? you use import ? this is how you "glue" your Python tools together to perform work for you isn't it? What's that difference with the shell? I just use cp. 
Also , shell tools/modules/functions/subroutine you name it ( there's not much difference anyway) are mostly in /usr/bin. Just like y Python modules/tools, they are all in the Python lib directories and site-packages. So is there any real big difference between them, in a bird's eye view? 

All I am saying is, this guy wants to learn the commandline. Let's just give him what he wants. Saying 
> 
I really wouldn't bother "programming" in shell, there are better ways to do that. 

might be too bold a statement to make.

---

### Post by pmasiar on 2008-01-02
This is question of balance. If all you want is ie copy the file, use plain bash. But if your processing needs are any deeper, learning universal and flexible sripting language like Python is IMHO preferable to becoming expert in obscure corners of bash.

And no, not all languages are good glue between tools. Ever tried to script os commands in Lisp or C? :-) Python was **designed** as platform-independent scripting language, and evolved to quite popular universal language.

@OP: you can learn bash as deep as you want, but IMHO you have better ROI (Return on investment - of time) by learning just bash basics, and deeper Python. YMMV.

---

