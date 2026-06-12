---
title: "[SOLVED] [Python] Find-and-replace script--(Is it over my head?)"
date: 2008-09-23
forum: Programming Talk
---

### Post by fiddler616 on 2008-09-23
Hey,
I write articles for Free Software Magazine, which has a VERY idiosyncratic, unwieldly, unattractive markup code. I would much rather use <b> for bold, <a href> for links, <zoom> for 'zoomed' text, etc.
I know that I could just find and replace all of that, but it seems like more trouble/time than it's worth, so the question is: Can you guys point me in the right direction for making a Python script for it?
I don't know if the easiest thing is to make a program where you copy in the text file, and it just spits it back up with the markups changed, or if there's some kind of module that will let me do it to a .txt file or what.
I'm fairly competent at procedural programming (whiles, dictionaries) etc. but am still learning OOP.
Is...
-This possible, and easy, and help is attached
-This possible, but over my head
-Maybe possible, but far more trouble than it's worth
-Impossible
?

Thanks in advance.

---

### Post by mike_g on 2008-09-23
Yes, it should be quite easy to do. I just found an example [here](http://www.java2s.com/Code/Python/String/Replaceall.htm), which should show how to replace all instances of one string within another:
```
S = 'xxxxSPAMxxxxSPAMxxxx'
print S.replace('SPAM', 'EGGS')           # replace all
```
So, 'S' would be the content of your text file. 'Spam' would be one of your tags and 'Eggs' would be the converted tag. With that you can build a list mapping before-after tags then iterate over it to replace each of them.

---

### Post by gomputor on 2008-09-23
A quick solution might be:
```

my_string = '<b>Hello World</b>'  # the text of your file

replacements = {'<b>':'BOLD', '</b>':'END_BOLD','e':'3', 'o':'0'} # etc, etc....

for i, j in replacements.iteritems():
    my_string = my_string.replace(i, j)

print my_string  #prints 'BOLDH3ll0 W0rldEND_BOLD'

```

---

### Post by LaRoza on 2008-09-23
It would be easier if you posted what the syntax was. Is it like an XML syntax (then it would be easier) or something totally different?

---

### Post by pmasiar on 2008-09-23
You don't need OOP for this task: just read up re module. For parsing XML, ElementTree is the best.

---

### Post by LaRoza on 2008-09-23
> **pmasiar said:**
> For parsing XML, ElementTree is the best.

I assume that is a high level, easy to use module that makes the most common tasks very easy, but probably doesn't have the flexibility of the DOM?

---

### Post by fiddler616 on 2008-09-24
> **LaRoza said:**
> It would be easier if you posted what the syntax was. Is it like an XML syntax (then it would be easier) or something totally different?
[s][COLOR="Blue"]The syntax I'm *supposed* to be writing in, or the syntax I *want* to write in?
The first can be found here: [http://www.freesoftwaremagazine.com/files/www.freesoftwaremagazine.com/nodes/1338/template_article.txt](http://www.freesoftwaremagazine.com/files/www.freesoftwaremagazine.com/nodes/1338/template_article.txt)
(It's not just using _ for italics--read down 'til you get to images and tables and such)(Doable, but looking things up all the time is no fun)
And the one I want is...I guess the term is HTML-esque, but there's a few tags that I'd have to invent (like <Zoom>, for example).[/COLOR][/s] Edit: I hadn't quite realized how solved it was until I finished replying.
@mike_g, and gomputor: Thanks, both of you. I was going to ask if there wasn't some cleaner way so that the end-user wouldn't have to edit a .py file, but then I realized it really was the easiest--just pop in a r" at the beginning (so that quotes within don't make trouble), and then a ", and find/replace coding at the end.
Solved!

---

