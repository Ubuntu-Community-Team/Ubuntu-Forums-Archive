---
title: "HTML help with my on-line resume"
date: 2010-06-19
forum: Programming Talk
---

### Post by Jimmmac1 on 2010-06-19
Good afternoon

I haven't programmed in many years, so when I tried to google an answer for this, I got many answers that I didn't understand.  Any help would be much appreciated, but please keep it simple.  I have my resume here, bit.ly/jmmres.  If you take a look at the source, you will see hundreds of &nbsp's.  I created it in Kompozer.  It looks ok in Internet Explorer, but is incorrectly spaced in Firefox.  I think there is a way to get rid of the &nbsp's, but it has been so long I can't remember, or can't find it.  I think if I do get rid of the &nbsp's, it will look right in any browser.  I tried downloading other editors, but wasn't able to get anywhere.  I would like to clean up the code, but don't have a clue how to do it.  Thanks for your help. 

Jim

---

### Post by trent.josephsen on 2010-06-19
> **Jimmmac1 said:**
> Good afternoon

I haven't programmed in many years, so when I tried to google an answer for this, I got many answers that I didn't understand.  Any help would be much appreciated, but please keep it simple.  I have my resume here, bit.ly/jmmres.  If you take a look at the source, you will see hundreds of &nbsp's.  I created it in Kompozer.  It looks ok in Internet Explorer, but is incorrectly spaced in Firefox.  I think there is a way to get rid of the &nbsp's, but it has been so long I can't remember, or can't find it.  I think if I do get rid of the &nbsp's, it will look right in any browser.

Not a chance.  Even after removing the non-breaking spaces, it's broken in so many ways I don't know where to start.  For starters, there's no declared character encoding and the [W3C Validator](validator.w3.org) claims it can't be parsed as UTF-8.  For another thing, all the layout is hard coded into the HTML, right down to the linebreaks.  It shouldn't even work in IE at small screen sizes -- try it.

Consider these category headings:

```
<div style="text-align: left; margin-left: 360px;"><big style=
"font-weight: bold;">PROFESSIONAL SUMMARY</big><br></div>

<div style="text-align: left; margin-left: 400px;">
<big><span style="font-weight: bold;">CERTIFICATIONS</span></big><br>
</div>

<div style="margin-left: 360px;"><big style=
"font-weight: bold;">PROFESSIONAL EXPERIENCE</big><br></div>

<div style="text-align: left; margin-left: 360px;"><big style=
"font-weight: bold;">EDUCATION</big><br></div>
```

Here's how I would write them:

```
<h1>Professional Summary</h1>

<h1>Certifications</h1>

<h1>Professional Experience</h1>

<h1>Education</h1>
```

All the rest can and should be done with CSS.  I know WYSIWYG editors are notorious for this sort of thing, but even so, for such a simple document I'm surprised Kompozer gave you such crappy markup.

> I tried downloading other editors, but wasn't able to get anywhere.  I would like to clean up the code, but don't have a clue how to do it.  Thanks for your help. 

Jim

I stripped out the &nbsp; entities with `perl -pe 's/(?:&nbsp;|\\s)+/ /g' resume.htm`, but this document needs a lot more work to look decent on most browsers and degrade gracefully under bad conditions (small screen size, for instance).  I can do that for you; PM me if interested.

---

### Post by soltanis on 2010-06-19
+1

You require more Cascading Style Sheets. What you should do is set up options such as layout, spacing, borders, etc using the style sheet. Then, when you are writing your HTML, it should be very simple, in similar style to what trent.josephson said. If you play your cards right, your HTML will be easily maintainable and your resume will look nice and well-formatted in almost any browser (except dillo...geez, dillo).

---

### Post by mainerror on 2010-06-20
And for the sake of readability please define the stylesheet in a separate .css file and then just reference the elements by their classes and ids.

---

### Post by Jimmmac1 on 2010-06-21
Hi all

Thanks for your responses.  I figured from the other research I have done that I would need a cascading style sheet.  But I have never done one of them.  Another learning curve.  I thought there might be an easy way to do this that I didn't know about without getting all of the ugly code.  Not sure what to do now.  Thanks again for your responses. 

Jim

---

### Post by simeon87 on 2010-06-21
It's not very difficult. If you want to do it cleanly, all you need to know is the following:

- How to link a CSS document to a HTML docment
- What a class and what an id is and how to specify properties for them

Any tutorial that is worth anything will tell you the above. After that, you can simply lookup in a list for the properties that you want to change (like font color and size) and enter them for the correct element(s). For your purposes, you can skip all the stuff about advanced selectors and all that.

---

### Post by Jimmmac1 on 2010-06-21
Hi Simeon87

Thanks for your response.  I have looked at a few CSS tutorials and it will take a while for me to figure out what they are trying to tell me.  I also tried downloading a Resume CSS template and that was just as confusing.  Do you have a recommendation for an on-line tutorial or book that I could get that would help me with this?  From the looks of everything I think it will take weeks before I can figure out what to do.  Thanks again for your response.  

Jim

---

### Post by trent.josephsen on 2010-06-21
*Head First HTML with CSS and XHTML* is a nice straightforward introduction to, well, HTML and CSS and not much else.  Certainly enough to make a good-looking CV.  I recommend it if you're interested.

If you just want the finished product and are not interested in the know-how, that's another question and the best answer is probably "hire a professional".

---

### Post by Jimmmac1 on 2010-06-21
Hi Trent.Josephson

The problem isn't the learning, the problem is the explanations I am getting, even from the places where the say 'Even an idiot can figure this out'. Well I am not an idiot and the explanations are lacking.  I was hoping NOT to have to go out and spend $40 on a book that I am only going to use for one page.  I am not rich.  I really should go out and learn this and then put up an explanation that ANYONE could understand.  This should not be rocket science, but everyone is making it out to be.  This is a simple resume.  No fancy colors, no fancy pictures, no fancy formatting. Just a simple every day resume.  If you want to see it, it is here, [http://bit.ly/jmmres](http://bit.ly/jmmres).  Very unassuming.  I wish I could find an explanation is unassuming.  Instead I get explanations full of id selectors, child selectors and so on and so forth.  I am sorry for blasting off, but I am getting frustrated.  Thanks again for all of you help.

Jim

---

### Post by soltanis on 2010-06-21
I can see you'd be frustrated since all you're trying to do is write a resume; and you're right, it's unreasonable to ask you to go and buy an entire book just to figure out how to do that.

Like you, I'm a little behind on the web times, but let me just explain it to you real quickly.

First of all, forget all of this crap CSS talks about; most of it really isn't important for you.

Real quick:

The "selector" is just the fancy term for what goes between the <>'s that you want to set the style for. Consider the following:

```

p {
color: red;
text-align: center;
}

```

As you can see, the stylesheet syntax is dictionary-like, with a bunch of name: value pairs. In that example, "p" was my selector. Now if I write an HTML document like this:

```

<link rel="stylesheet" type="text/css" href="stylesheet.css" />
<p>
This paragraph will have a red color and will be aligned to the center.
</p>

```

What happened was I "selected" all my paragraphs (HTML <p> elements) and added that style to them.
You can do this for basically any element.

```

h1 {
font-size: 20pt;
text-indent: 50px;
text-align: center;
}
p {
font-size: 12pt;
text-indent: 75px;
text-align: left;
}

```

With this simple document I can control the presentation and layout of all my header and paragraph elements in text. With just a little more research and addition of styles for list items, you should be basically done.

You should look at:
[http://www.w3schools.com/css/default.asp](http://www.w3schools.com/css/default.asp)

For more examples. I know, it's a tutorial, but you should not read it linearly; instead, do like I do, and learn by example. It should not take a lot of stylesheet to make your resume look stellar if you just tweak these settings a little bit. Don't get discouraged; it may take you one or two hours to get this down, but the resulting improvement and uniformity of your CV is worth it.

---

### Post by mainerror on 2010-06-22
Here is another very good site you might want to have a look at.

[http://net.tutsplus.com/category/tutorials/html-css-techniques/?tag=basix](http://net.tutsplus.com/category/tutorials/html-css-techniques/?tag=basix)

There are some articles which are only available for Premium Members (subscription) but also a lot of useful tips and examples which are free. The section I've linked you to is the HTML and CSS Basics section which should help you quite a bit. Another interesting point might be that some of the tutorials and articles are presented as a screencast maybe this helps too.

---

### Post by Jimmmac1 on 2010-06-22
Hi Solantis

Thanks for the info.   I think I actually might go out and buy that book, then learn the stuff and write a tutorial for the rest of us !  Maybe the w3 guys would publish it.  Thanks again.

Jim

---

