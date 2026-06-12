---
title: "Tetris Java Applet"
date: 2007-07-14
forum: Programming Talk
---

### Post by huzzak on 2007-07-14
I've programmed a Tetris clone and I was hoping that some of you could take a look at it and critique the game and the code.  I'd really appreciate any suggestions or comments you might have about any aspect of the game or code.  Thanks!

[You can play it here.]("http://www.lelanophilus.net/codes/")

---

### Post by LaRoza on 2007-07-14
Being a big tetris fan, I feel I can tell you that is really, really good.

the back ground is slightly more distracting than what I am used to, but the game is better than most.

Good job.

I am not a Java fan, although I do know the language, so I won't talk about the code, although I will look at it.

---

### Post by apoth on 2007-07-14
I'm a professional Java programmer with little experience with Tetris.

The code's very good, not worth critiquing at all. It does have the feel of Java a few years ago though - do you have a background in C programming?

Personally I really like the background!

---

### Post by LaRoza on 2007-07-14
> **apoth said:**
> 

Personally I really like the background!

I like it also, especially the eyes. I am just not used to images in the background.

---

### Post by huzzak on 2007-07-14
Thanks!  I kind of felt like I had to put the background in to make it different, otherwise it would've completely been just another Tetris clone.  Now it is just another Tetris clone with a unique background.  The original idea was to have the background image change with each level, but that proved to be more work than my attention span allowed for.

My first program was in QBasic, but then I learned through C++.  It wasn't until last year that I picked up C and Java at about the same time.  What is it about the code that tips you off?

---

### Post by apoth on 2007-07-15
Little things like most people who've learned to program with Java would write:

```
public void method() {
}
```

where people from a C/C++ background would tend to move the first parenthesis down a line.

I also noticed I couldn't see any of the newer Java language features like Generics and then realised that you don't actually (as far as I can see) use any Java collections or even anything outside the java.applet/java.awt packages except java.util.Random.

That's not a criticism, the opposite if anything, 'born and bred' Java programmers will often use a Vector where an int[] would be better just because they're lazy when it comes to thinking about memory in their data structures, something a C/C++ programmer couldn't get by without doing. :)

You also commented your code well, shamefully much more thoroughly that I probably would for my own projects, but didn't use JavaDoc style commenting - a way of commenting your code so that HTML documentation can be generated from it.

We'd also probably use swing and webstart instead of an applet, just because they're out of fashion.

All of that together with a Java program that's written well usually means someone with previous C/C++ experience.

---

### Post by huzzak on 2007-07-15
Hmm.  You are a kind of Sherlock Holmes, which is pretty fun.

I remember discussing Generics in one of my classes, but don't rememeber anything about them.  I think I'll look into that as well as swing and webstart.  I did it with an applet because I ran across a tutorial and it did not seem to be complicated in the least.

I didn't realize the positioning of the open brace differed by background.  I always thought it was a purely aesthetic choice (which I guess it really is, though probably influenced by prior experience).  I prefer the symmetry.

Thanks for explaining.

---

