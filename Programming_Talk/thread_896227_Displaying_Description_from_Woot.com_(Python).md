---
title: "Displaying Description from Woot.com (Python)"
date: 2008-08-21
forum: Programming Talk
---

### Post by jacensolo on 2008-08-21
I love coding and have done it off and on for a number of year, but I have never gotten very far. I've done a number of different languages but have never made a real world app, something I will actually use that I have been proud of making. Upon learning python I read somewhere to think of something I do, and write a script to automate it. It seemed everything I do is already easy though. But then I finally thought of something I could do fairly easily and actually use it, so I thought.

[Http://www.woot.com](Http://www.woot.com) is a site that has a different item up every day for relatively cheap price. I usually check it daily. What I want to do is make a script that takes the title, picture, price, and description, print it, and save it to a disk. Seems pretty easy, right?

I can open a file and save it fine. My problem is getting the description out of the tags. I suppose I could use re, but that just seems painful for something like this. I think what I want to do is use an html parser. I've looked at Python's api and tutorials, but it's one of those things that is not clicking. I also Googled for more tutorials but n one of them helped either. I think it is something about inheriting the class and changing the meathods. I understand inheritance, but from what I gather the original methods do nothing and are just a template. So I don't understand how this works... I'm lost just thinking about it. 

Any help would be appreciated. :)
[SIZE="1"]
PS. Any other ideas for applications to make? Part of my problem is I can never think of what to make, so I just start learning a different language (just a tiny, tiny  bit) to see if anything hit me. My current list includes: C, C++, Java, Dark Basic, C#, Visual Basic (took a class, didn't like it), Python (I think I know this the most as it is the most fresh, and it is my favorite) and I started peeking at lisp before I thought of this. Keep in mind this is over years as it was an on and off kind of thing. Python is from this year.[/SIZE]

Edit: I forgot to add that I know I can save it as an html file and skip the parsing, but I want to print the description to the console also.

---

### Post by pmasiar on 2008-08-21
> **jacensolo said:**
> make a script that takes the title, picture, price, and description, print it, and save it to a disk. 

text from page is easy. You don't need re: you can get page text into single string, split it to parts and find info you need. Plain string methods.

Later you can use BeautifulSoup. Parsing half-correct HTML (which is not even XHTML) is messy affair, better to stay away.

> Any other ideas for applications to make? 

Plenty, I was collecting ideas for 2 years now: see wiki in my sig.

---

### Post by jacensolo on 2008-08-21
> **pmasiar said:**
> text from page is easy. You don't need re: you can get page text into single string, split it to parts and find info you need. Plain string methods.

Later you can use BeautifulSoup. Parsing half-correct HTML (which is not even XHTML) is messy affair, better to stay away.


Wouldn't I have to know the all tags and which lines the description is on to split it? 

I'll have to look up what BeautifulSoup is. 

Oh it's an HTML Parser. Better than the one provided, I'm assuming? Didn't have much time to look at it.

---

### Post by Cheesehead on 2008-08-21
woot.com has an RSS feed (XML)

The feed might be what you want, already made for you.

Even if it's not an exact match, using python to parse and manipulate the XML is a easier and less confusing than HTML.

You can mail it to yourself, create a desktop popup, create an OpenOffice document, pipe it to conky to show up on your desktop, etc. It's fun!

---

### Post by pmasiar on 2008-08-21
> **jacensolo said:**
> Wouldn't I have to know the all tags and which lines the description is on to split it?

You just split at exact places you want to. You don't write universal parser, just a program to extract specific info from a specific page (== text file).

> I'll have to look up what BeautifulSoup is. 

Oh it's an HTML Parser. Better than the one provided, I'm assuming? Didn't have much time to look at it.

BS is parser who can tolerate common HTML structural mistakes and does not die on them, that's what I heard.

BTW I never used it, I was lucky to have valid XML and used excellent ElementTree.

---

### Post by Wybiral on 2008-08-21
> **pmasiar said:**
> BS is parser who can tolerate common HTML structural mistakes and does not die on them, that's what I heard.

BTW I never used it, I was lucky to have valid XML and used excellent ElementTree.

BS will work for most websites, it handles HTML very well (things that aren't XHTML or have mistakes or bad formatting in them, like most of the internet). It's very easy to use too.

For the most part it's just: doc.findAll("tag", {attributes})

And it will find the right elements for you and give you access to text nodes/attributes/etc.

---

### Post by ghostdog74 on 2008-08-22
> **jacensolo said:**
>  I usually check it daily. What I want to do is make a script that takes the title, picture, price, and description, print it, and save it to a disk. Seems pretty easy, right?
it would be easy if you know what you are looking for, and if the tags descriptions are fairly constant everyday.
```

wget -q -O- http://www.woot.com | awk '
/id=\"TitleHeader\"/{  #find specific tag
  gsub("<[^>]*>", "") #get rid of tags
  print "Title: " $0  
}
/id=\"PriceSpan\"/ {
  gsub("<[^>]*>", "")
  print "Price: " $0 
}
/<dd class=\"item\">/ {
  getline
  gsub(/<[^>]*>/, "")
  print "Description: " $0 
}'


```
output:
```

# ./test.sh
Title:      HP Pavilion Slimline Dual Core Media Center PC
Price:              $449.99
Description:                                        1 HP S3320F Athlon 64 X2 5200+, 2GB DDR, 500GB SATA, DL Lightscribe DVDRW, ATSC Tuner, Vista Home Prem


```

you can do the same in Python. For more complex operations, a parser library might be easier for you.

---

