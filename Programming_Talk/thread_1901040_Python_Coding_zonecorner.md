---
title: "Python Coding zone/corner"
date: 2011-12-27
forum: Programming Talk
---

### Post by chevloschelios on 2011-12-27
Hi guys,
[COLOR=#006400]
little bit boring these days, so I did simple website(alfa version) with  some of my Python scripts for beginners or maybe  advanced users. Can  you please tell me what do you think about that ? Should I continue ?  Write me please your ideas. (here or to PM)
I really appreciate it. Thank you  [/COLOR]

URL of website: [http://pywned.vserver.cz/codes](http://pywned.vserver.cz/codes)

---

### Post by MG&amp;TL on 2011-12-27
Pretty cool, you might want to update the English translation though. "what I can make better" doesn't really flow very well in English. 

I'm not sure I like the text animation, maybe an immediate banner may be more appropriate for a web page. Not sure, have a fiddle.

Otherwise, pretty good site. :)

---

### Post by chevloschelios on 2011-12-27
Thank you for your response !

Yes, I know i am not advanced english speaker but this site is just "alfa version". I just want to know that somebody read it and then I can upload more  scripts. Now there are just very simple but I have some longer, better  projects.

---

### Post by MG&amp;TL on 2011-12-27
"alpha" :D

If at some point you want to forward the html to me, for spell-check (probs at some later date), drop me a PM for my email. :D

---

### Post by juancarlospaco on 2011-12-27
Cool site dude...   :)

---

### Post by Boludinux on 2011-12-28
Teach me how to make a website like yours! I loved it :)

---

### Post by chevloschelios on 2011-12-28
jQuery

---

### Post by chevloschelios on 2011-12-28
New scripts !!! Check site now guys :)) tell me want do you think about that

---

### Post by cgroza on 2011-12-28
If you want to keep that text animation, I recommend making it a lot faster.
The animation is significantly slower than most readers and personally, that made me lose time by waiting for all the text to show up.

Other than that, I really loved your design. Great work.

---

### Post by chevloschelios on 2011-12-28
HI, the design is not mine, check the source code.

I dont think that animation is slow ...

---

### Post by DangerOnTheRanger on 2011-12-28
Nice examples - short and too the point :) However, if you're targeting beginners in Python, I really think you need to comment some of your examples, and use better variable names. For example, the web crawler script was somewhat hard to follow due to both lack of comments (I doubt a Python newbie knows what a regular expression is) and relatively opaque variable names.

The only other thing you might want to change is inconsistent formatting across the examples. Some of the scripts (like the port scanner) are formatted somewhat poorly IMHO; I suggest looking at PEP8 for a good format guideline.

I apologize if my critique came off as overly harsh, but your scripts are pretty good - adjust the format, add some comments, and they'll serve as excellent tutorials :)

> **chevloschelios said:**
> 
I dont think that animation is slow ...

I have to say I agree with cgroza here - for those of us who can read quickly, waiting for the text to animate can be a little annoying. Maybe you could make a flat HTML version of your site?

---

### Post by chevloschelios on 2011-12-29
Hi,

thank you for your ideas. I think I can make the text static. I have updated the contact tab and now Im sorting script into categories. 

Keep watching !!

You can join the facebook page : [http://www.facebook.com/pages/Python-coding-corner/188505691246192](http://www.facebook.com/pages/Python-coding-corner/188505691246192)

---

### Post by Barrucadu on 2011-12-29
I have just a few points:

[list]

[*]The animation is too slow, and just looks silly. Unless there is some great reason why you need it, I suggest you remove it, or at least speed it up.

[*]Bold Impact is not a good font, it makes the names on the contact page nigh-unreadable. Actually, Impact in general is not a good font, it's just ugly.

[*]Why are you using tables to position your lists? That's what CSS is for - using tables for layout was acknowledged as being a terrible, terrible thing to do years ago.

[*]The contact lists look untidy, as the name of each contact method is a different size, so the equals signs don't line up vertically.

[*]If you are going to display the scripts with syntax highlighting, do that on the website - have it so that when you click the name of a script it opens up in a lightbox or something. There is no benefit in displaying it on a completely separate page

[*]If you are going to display the scripts with syntax highlighting, you also need to provide links to download the raw script, in plain text form, as otherwise you're making it awkward to download scripts, people have to resort to copying and pasting.

[*]Your site is neither valid HTML nor XHTML.

[*]Your CSS is not valid
[/list]

---

### Post by chevloschelios on 2011-12-29
Thanks for your reply


[LIST]
[*]Animation is removed
[*]What font do you recommended ?
[*]I will rewrite the code after I finish adding content
[/LIST]

Thank you again

---

### Post by MG&amp;TL on 2011-12-29
Comic Sans, or something similiarly anonymous.

Err... why a "[*]" at the title? Looks a bit weird to me.

Great, you fixed the animations, looks beter now. :)

Not sure about the snow in the background, but it is wintertime...

> Hello and welcome to the Python Coding Central. This website contains a few Python scripts that I and others have written over the past couple months. To access these files, please use the scripts button at the top right hand corner. If you would like, you can send me ideas on how to improve this website by using the contact button at the top right hand corner. If you have any troubles with Python we have several contacts to assist you with all your Python needs. And finally if you would like to contribute to the website, please contact me with a link to the program(s) you would like to submit. Thanks for using the Python Coding Central. 

 Cheers ;-] © pywned in 2011

My version:

> Welcome to Python Coding Central. The site contains Python scripts that others, along with myself, have created-take a look under the "scripts" header, and feel free to copy and paste. More scripts are added constantly, and you can help too! 


If you have any Python scripts you would like to contribute, please use the Contact button to send me either a link for your program, or plaintext if the program is small, for submission. Troubles, errors, and complaints/constructive criticism can all be directed to "Contact" too. 









[SIZE="1"]Cheers ;-] © pywned in 2011[/SIZE]

IDK if anyone agrees with my version, but I think it's a slight improvement. At least make the copyright notice smaller. :)

Hope this helps.

---

### Post by chevloschelios on 2011-12-29
Thank you for your version. 

How can I categorise the codes ?? What do you think guys? 

I have now: system codes, network codes, other codes


[LIST]
[*]Yes is wintertime ! :D
[*]
[*] because I like it
[/LIST]

---

### Post by Bodsda on 2011-12-29
Hi,

Great site, love the design and the feel. A few points from me


[LIST]
[*]Licensing information - could'nt find any
[*]Script consistency, needs addressing - could be tricky with multiple authors
[*]Bad code - some of the examples are riddled with poor practices and obvious flaws, for example the password generator manually creates a list of acceptable characters, rather than using the more logical string.printable or some of the other ones.
[*]shebang - some scripts include it, some dont
[*]variable names should have some correlation with the expected contents
[*]some scripts wont work without editing - the google search for example, the function is created, but never run
[*]The front page paragraph is ugly. Try splitting into 2 paragraphs, change the font and colour.
[*]Add more navigation buttons so that we can go from network scripts to system scripts without having to go back to the main script group selection thingy
[*]Contacts page needs some TLC, especially the font
[*]Whats with all the square brackets everywhere?
[*]On the main scripts page, the icons are clickable, but not the text - by design?
[*]Some scripts just wont work as you expect, lengthcounter.py for example wont produce the expected result for number of sentences given the following "I really like dogs!"
[/LIST]


But please don't take those comments the wrong way, they are purely constructive. I applaud your initiative and love the site. I might even submit a script or two.


Bodsda
Ubuntu Beginners Team

---

### Post by MG&amp;TL on 2011-12-29
> **chevloschelios said:**
> Thank you for your version. 

How can I categorise the codes ?? What do you think guys? 

I have now: system codes, network codes, other codes


[LIST]
[*]Yes is wintertime ! :D
[*]
[*] because I like it
[/LIST]

Newb Codes!

Some using a graphics library like Tkinter might be nice. (I sat tkinter as it's inbuilt, rather than it being a gtk tutorial)

---

### Post by chevloschelios on 2011-12-29
[Bodsda]("http://ubuntuforums.org/member.php?u=448461")

I really appreciate your comment. I will look for everything you suggest me. 




I dont like Tkinter, wxPython is better. But thanks Newbie script is good idea

---

### Post by MG&amp;TL on 2011-12-29
> **chevloschelios said:**
> [Bodsda]("http://ubuntuforums.org/member.php?u=448461")

I dont like Tkinter, wxPython is better. But thanks Newbie script is good idea

Agreed. Tkinter doesn't look so good. But the point I was making is that Tkinter is inbuilt, so you don't have to describe how to get it, how to get started, platform differences, just:

```
import tkinter
```

Also, if you're going to use an external library on a linux-oriented site, you may as well go with pygtk?

(I say linux-oriented, who puts shebangs in Windows?)

---

### Post by chevloschelios on 2011-12-29
I understand

I will try to download some Tkinter examples

---

### Post by marcosco on 2011-12-30
Very nice website, I like that design. Keep working man !!

---

### Post by chevloschelios on 2011-12-31
[LEFT]Thank you !!

Im working on it everyday ! So stay tuned !!!!!
[/LEFT]

---

### Post by marcosco on 2012-01-01
Yeah , I see. Nice new codes !

---

