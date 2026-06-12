---
title: "the openening brace - a trivial C question"
date: 2006-03-28
forum: Programming Talk
---

### Post by Azrael on 2006-03-28
I am a (really) novice C programmer and I see two conflicting recommendations about C formatting. Some texts recommend putting the opening brace at the end of an expression. As shown by K&R:

construct (condition) {
    ...
}

Many others (me included) prefer it like this:

construct (condition)
{
    ...
}

The second I think looks a lot 'clearer' and makes missing/misplaced braces quicker to spot. So what is the advantage of the first method? Have people changed opinion about this (it seems more prevalent in the olden days?)? What do you prefer? Or do you want to flame me for wasting your time with this? 8)

---

### Post by bored2k on 2006-03-28
> construct (condition)
{
...
}Is the way I prefer it. It's a lot clearer and cleaner to me, and unlike my college C teacher, I'd rather have a clear and clean code that one with less spaces in it. It's even the prefered format in [one of the books I like the most]("http://www.amazon.com/gp/product/0672327112/qid=1143548950/sr=2-1/ref=pd_bbs_b_2_1/103-0018156-8439876?s=books&v=glance&n=283155").

---

### Post by Buffalo Soldier on 2006-03-28
[QUOTE=Azrael]construct (condition) {
    ...
}
[/QUOTE]
That sytle is called the One True Brace Style (1TBS) or K&R style. I prefer this style.

But my lecturer at college taught us the other style, the one that you (and most other people at the moment) seem to prefer.

Further reading on [indent style](http://en.wikipedia.org/wiki/Indent_style).

---

### Post by Azrael on 2006-03-28
[quote=Buffalo Soldier]Further reading on [indent style]("http://en.wikipedia.org/wiki/Indent_style").[/quote]
Excellent! That wiki has all the information I was looking for.

So the "One True Brace Style" is actually only motivated by preservation of screen real estate, which I think has become a bit of a deprecated reason, considering most high resolution 21 century screens. Yeah, I'll stick to the "BSD/Allman style".

---

### Post by LordHunter317 on 2006-03-28
[QUOTE=Azrael]So the "One True Brace Style" is actually only motivated by preservation of screen real estate, which I think has become a bit of a deprecated reason, considering most high resolution 21 century screens. Yeah, I'll stick to the "BSD/Allman style".[/QUOTE]Except it uses the second form for functions, where it is most appropriate.  For block expressions, I find having the brace on the second line less readable, especially when you have many levels of indentation.  Too easy to loose it.

---

### Post by Azrael on 2006-03-28
[quote=LordHunter317]Except it uses the second form for functions, where it is most appropriate.[/quote] Functions always start unindented on the first column, unlike block expressions, so I feel the two are sufficiently distinguished anyway.
[quote=LordHunter317]For block expressions, I find having the brace on the second line less readable, especially when you have many levels of indentation. Too easy to loose it.[/quote] The way I see it, the BSD style causes an opening brace to look like an exact mirror image of the closing brace, making it *less* easy to loose. We're all wearing slightly differently colored glasses I guess..

---

### Post by LordHunter317 on 2006-03-28
[QUOTE=Azrael]Functions always start unindented on the first column, unlike block expressions, so I feel the two are sufficiently distinguished anyway.[/quote]In C sure.  But not in most Algol-derivatives: Java, C#, C++, etc.

---

### Post by rplantz on 2006-03-28
In his C++ books, Cay Horstmann uses the style:
```

int main()
{  cout << "How many pennies do you have? ";
   int pennies:
   cin >> pennies;
   ---
}

```

I don't like the way this looks.

After 20+ years of reading/trying to read student programs, I got used to seeing many different styles. When I first started teaching, I tried to enforce my own style. I then realized that some students' styles looked better than mine. I became much more flexible.

I believe that documentation is one of the most important facets of a program. You can implicitly document your code by (1) being consistent in you indenting and braces placement and (2) using descriptive variable names.

#2 is where I have the biggest problem with K&R. I've always assumed that they used keyboards that gave an electric shock every time they pressed a key. :)

---

### Post by red_Marvin on 2006-03-29
Looking at the wikipedia page I find that the I use Whitesmith's style,
but GNU style seems good too, especially since modern IDE's let you specify
if the tab key is to represent a tab or a user specified number of spaces.

---

