---
title: "[SOLVED] [Python] Enter (as in line breaks)"
date: 2008-09-27
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-27
Hello,
I'm writing a Python program that takes a (huge)(read: 1000-2000 words) string from the user, converts it (it happens to take '<b>' and replace it with '**', among many other things), and spits it back out, converted.
Round 1 involved:
```

the_string = r'''Sample text. **Formatting**, "double-quoting", etcetera, it's all good. You can even
hit enter, and everything will be fine.'''

```
Which works, except it seems sloppy, at best.
So now I put in
```

the_string = raw_input("Text:")
```
Which also works...except that hitting enter submits it, it doesn't line break.
Yes, I could just say to use <BR> instead of actually hitting enter, but that's sloppy too. So is there a way to make Enter just line break, and something else (like Super-Enter) submit the raw_input?
Thanks in advance.

---

### Post by gomputor on 2008-09-27
Do they (your users) have to enter all these in the command line? Isn't it
better to write their old and new terms in a text file, maybe in a format
like this:
```
# a space separates the old with the new term
<b> **
</b> /**
<em> e*
</em> /e*
```
and then you just load that file, split the lines, so you have a list with
first the old term, and second the new one, and make your replacements?
Is the command line entering the only way? If not, then I can give you a
working example following my answer in your previous post.

---

### Post by fiddler616 on 2008-09-27
> **gomputor said:**
> Do they (your users) have to enter all these in the command line? Isn't it
better to write their old and new terms in a text file, maybe in a format
like this:
```
# a space separates the old with the new term
<b> **
</b> /**
<em> e*
</em> /e*
```
and then you just load that file, split the lines, so you have a list with
first the old term, and second the new one, and make your replacements?
Is the command line entering the only way? If not, then I can give you a
working example following my answer in your previous post.
One of us didn't have enough coffee this morning, and isn't making sense. I blame myself.
I already know what needs to be replaced with what (you were there in the previous thread, actually :) ), I just need the user to type in their *text*.
Example:
> 
Text #Yes, I suppose this is a command line: To install Ubuntu, put the <i>Live CD</i> in your tray, boot up your computer, and you should see a screen with: #Hitting <ENTER> here is the problem
<b>Try Ubuntu without making any changes to your computer</b>
<b>Install Ubuntu</b>
(Etcetera)
<img src=install.jpg>

and then the user submits, and receives
> 
 To install Ubuntu, put the _Live CD_ in your tray, boot up your computer, and you should see a screen with:
**Try Ubuntu without making any changes to your computer**
**Install Ubuntu**
(Etcetera)
=IMAGE=install.jpg=CAPTION= =>

Just reading a .txt file and spitting back the conversion would be FANTASTIC, except for all my reading into the 'file' function, I couldn't make it cooperate.

I also looked into EasyGUI, for making things both pretty *and* functional, but it didn't seem to do the trick either.

---

### Post by gomputor on 2008-09-27
> **fiddler616 said:**
> One of us didn't have enough coffee this morning, and isn't making sense. I blame myself.
Well, most certainly the blame is mine, and that's because english isn't
my native language, so I find it hard sometimes to express myself or to
understand what others say. I apologize for that. :)

Well ok, you know how to make the conversion as you say. But still I find
it better to read from a file and make the replacements, than to force the
user to enter all the text in the command line.
For example:
```

f = open('the_file_to_be_converted', 'r')
# data will hold the text of the file
data = f.read()
f.close()

# now work with data and make the replacements,
# ie if you use my method from your previous post
replace_all(data, dic)
# (or whatever method you chose for the replacement)
# Remember: the variable **data** holds the text that
# you want to make the replacements.
#
# and return the result in any way you want
# either printing it in the terminal or saving
# it in a file or whatever you want.

```

Still confused? Am I missing something? :)

---

### Post by pp. on 2008-09-27
Are you actually planning on writing a program which has the user enter a fair sized short story at the prompt of your program, without any possibility of editing?

---

### Post by fiddler616 on 2008-09-27
@gomputor: Thank you, that was brilliant.
@pp.: Given my Python skills, it was a toss-up between directly editing the source, or trying to put some kind of UI on it, so I made both (I'd already made the first one outside of this thread). But it's a moot point, since now it reads the .txt

---

