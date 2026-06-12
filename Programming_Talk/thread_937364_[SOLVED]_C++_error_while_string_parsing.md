---
title: "[SOLVED] C++ error while string parsing"
date: 2008-10-03
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-03
so im making a program where i can enter vocab words, a definition, and the part of speech into a txt file and it is parsed and it will quiz me

but first i need to learn how to parse the string in the format that i type them in into three different strings

ive been looking at some tutorials for this and while trying to apply the string::find() and string::substr() functions i get some runtime error about out of range memory...and i cant figuere out for the life of me what's up

heres the code:

[PHP]int main()
{
	string chapters = "<chapter1> hello, a greeting, noun; <end1> <chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <end3>";
	string str;
	str = chapters.substr(chapters.find("<chaptertwo>"),chapters.find("<end2>"));
	cout << str;
	return 0;
}[/PHP]

---

### Post by raul_ on 2008-10-03
> **jimi_hendrix said:**
> so im making a program where i can enter vocab words, a definition, and the part of speech into a txt file and it is parsed and it will quiz me

but first i need to learn how to parse the string in the format that i type them in into three different strings

ive been looking at some tutorials for this and while trying to apply the string::find() and string::substr() functions i get some runtime error about out of range memory...and i cant figuere out for the life of me what's up

heres the code:

[PHP]int main()
{
	string chapters = "<chapter1> hello, a greeting, noun; <end1> <chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <end3>";
	string str;
	str = chapters.substr(chapters.find("<chaptertwo>"),chapters.find("<end2>"));
	cout << str;
	return 0;
}[/PHP]

I'm not sure what your problem is, but why did you mark it as PHP code? And why are you searching for "chaptertwo" when you wrote "chapter2"?

---

### Post by raul_ on 2008-10-03
Well, I just tested your code, and that was your problem. It didn't find the substring "chaptertwo" because you wrote "chapter2" before

```

[raul@horus ~]$ ./teste
<chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <e[raul@horus ~]$

```

Not sure if that's what you wanted though :cool:

---

### Post by jimi_hendrix on 2008-10-03
> **raul_ said:**
> Well, I just tested your code, and that was your problem. It didn't find the substring "chaptertwo" because you wrote "chapter2" before

```

[raul@horus ~]$ ./teste
<chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <e[raul@horus ~]$

```

Not sure if that's what you wanted though :cool:

wow......thats pretty sad on my part

---

### Post by raul_ on 2008-10-03
Well, i think the only people who find it sad are non-programmers. We know those things are pretty common so it's only fair that we cut some slack ;)

---

### Post by jimi_hendrix on 2008-10-03
> **raul_ said:**
> Well, i think the only people who find it sad are non-programmers. We know those things are pretty common so it's only far that we cut some slack ;)

thanks

> **raul_ said:**
> I'm not sure what your problem is, but why did you mark it as PHP code

php quotes color code most languages

---

### Post by raul_ on 2008-10-03
> **jimi_hendrix said:**
> thanks



php quotes color code most languages

ah, sweet! didn't know about that one

---

### Post by mssever on 2008-10-03
> **jimi_hendrix said:**
> php quotes color code most languages
But it doesn't handle all aspects of non-PHP languages correctly, and it annoyingly marks stuff as PHP.

Wybiral has a great [solution to this problem]("http://www.challenge-you.com/bbcode"). Just select the language, paste in your code, submit the form, and you get much-improved syntax highlighting you can paste into the forums.

Example:
```
[color=#B00040]int[/color] main()
{
    string chapters [color=#666666]=[/color] [color=#BA2121]"<chapter1> hello, a greeting, noun; <end1> <chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <end3>"[/color];
    string str;
    str [color=#666666]=[/color] chapters.substr(chapters.find([color=#BA2121]"<chaptertwo>"[/color]),chapters.find([color=#BA2121]"<end2>"[/color]));
    cout [color=#666666]<<[/color] str;
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

---

### Post by Lux Perpetua on 2008-10-04
> **mssever said:**
> Wybiral has a great [solution to this problem]("http://www.challenge-you.com/bbcode"). Just select the language, paste in your code, submit the form, and you get much-improved syntax highlighting you can paste into the forums.Excellent! I hate those PHP tags. Every time I see them, I think: "why the heck is this guy trying to do this in PHP? And what kind of PHP is this?!? ...no, wait, it's actually Python in PHP tags."

---

### Post by jimi_hendrix on 2008-10-04
why do we only have php tags and not tags for other big languages?

---

### Post by dribeas on 2008-10-04
> **mssever said:**
> Wybiral has a great [solution to this problem]("http://www.challenge-you.com/bbcode").
Example:
```
[color=#B00040]int[/color] main()
{
    string chapters [color=#666666]=[/color] [color=#BA2121]"<chapter1> hello, a greeting, noun; <end1> <chapter2> dog, a furry animal, noun; <end2> <chapter3> bye, a farewell, noun; <end3>"[/color];
    string str;
    str [color=#666666]=[/color] chapters.substr(chapters.find([color=#BA2121]"<chaptertwo>"[/color]),chapters.find([color=#BA2121]"<end2>"[/color]));
    cout [color=#666666]<<[/color] str;
    [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```

It makes it harder to answer/comment parts of the code as there are a bunch of color/format tags in the code. The output, while shown on the screen is better, but editing becomes much harder.

---

### Post by Kadrus on 2008-10-04
> Wybiral has a great solution to this problem. Just select the language, paste in your code, submit the form, and you get much-improved syntax highlighting you can paste into the forums.
I think he uses [Pygments]("http://pygments.org/").You can use it from your desktop.

---

### Post by issih on 2008-10-04
You aren't a real programmer until you've made a mistake that is so horrifyingly obvious when its pointed out that you feel utterly and entirely and irredeemably stupid...

Welcome to the club, we all do it :)

---

### Post by nvteighen on 2008-10-04
> **issih said:**
> you aren't a real programmer until you've made a mistake that is so horrifyingly obvious when its pointed out that you feel utterly and entirely and irredeemably stupid...

Welcome to the club, we all do it :)

You're so right!

---

### Post by mssever on 2008-10-04
> **dribeas said:**
> It makes it harder to answer/comment parts of the code as there are a bunch of color/format tags in the code. The output, while shown on the screen is better, but editing becomes much harder.
That's odd. When editing or quoting, I see colored text without any color tags (except when I've just pasted the text in and haven't submitted yet), so it's no more difficult than [noparse][code][/noparse] tags. I wonder why you and I see two different things. (By the way, I mostly use Firefox.)

---

### Post by nvteighen on 2008-10-05
> **mssever said:**
> That's odd. When editing or quoting, I see colored text without any color tags (except when I've just pasted the text in and haven't submitted yet), so it's no more difficult than [noparse][code][/noparse] tags. I wonder why you and I see two different things. (By the way, I mostly use Firefox.)

What? I use FF3 and don't see that... Maybe have you written a secret extension you don't want to share? ;)

---

### Post by mssever on 2008-10-05
> **nvteighen said:**
> What? I use FF3 and don't see that... Maybe have you written a secret extension you don't want to share? ;)
Maybe it's because of my forum settings. [Options]("http://ubuntuforums.org/profile.php?do=editoptions") > Message Editor Interface I use the Enhanced interface. I don't remember whether this is the default, but I know this is the interface I've seen for as long (or nearly so) as I've been a member here.

---

### Post by nvteighen on 2008-10-05
> **mssever said:**
> Maybe it's because of my forum settings. [Options]("http://ubuntuforums.org/profile.php?do=editoptions") > Message Editor Interface I use the Enhanced interface. I don't remember whether this is the default, but I know this is the interface I've seen for as long (or nearly so) as I've been a member here.
Yeah, that did the trick. Thanks!

---

