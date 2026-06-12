---
title: "Beginning web development"
date: 2008-07-05
forum: Programming Talk
---

### Post by hey_ram on 2008-07-05
Hi!

I wanted to start developing my own web pages..
and publishing them on the web...

i am pretty confused as to which language i should start writing in..

there seems to be a whole lot of languages out there....html, python, css etc. etc...

i may not even know the exact difference between them but want to learn...

any advice would be most welcome...

thanx

---

### Post by wrtpeeps on 2008-07-05
I recommend PHP for web development. :)

---

### Post by hey_ram on 2008-07-05
hi wrtpeeps..

thanx for the quick reply..
any specific reason why i should choose php and not any other language?

the reason im asking this is because i need to set my website up in a very short time...and then learn the finer points over a period of time...

so if php has a steep learning curve, i may not be able to put my website up in a short time..

hope u got my point..

---

### Post by Gorgonkernel on 2008-07-05
Hello, in my opinion you should start with some simple languages such as html, xhtml, css, javascript. Learn as much as you can, read code..try to modify here and there and see what`s happening. After you have some decent knowledge you can move to php and why not mysql.

[Here]("http://w3schools.com") is a link with some free tutorials...html,xhtml css..all that you need in order to learn and create websites. Good luck and if you have more questions you can pm me. I will be happy to help you.:KS

---

### Post by CptPicard on 2008-07-05
HTML is the base page description language, CSS is for styling (and layout). Start with those, at [http://www.w3schools.com/](http://www.w3schools.com/).

All the rest are programming languages which you are not interested in at the moment. They can be used to do server-side dynamic generation of the page, but you want to be able to just write HTML by hand to begin with.

---

### Post by wrtpeeps on 2008-07-05
If you want to set your site up quick (and I should have really said to learn HTML first and then learn php) then use html. Once you are confident with it (won't take long, it's really simple) learn PHP so you can do some more fun stuff with your site.

---

### Post by pmasiar on 2008-07-05
If you want really quick simple pages, use a wiki - wikidot.com is what I currently recommend, even if my own old wiki is on pbwiki.com.

Wiki is simplest way to publish content, you just edit text in simplified markup **much** simpler than HTML, and you can select from like 20 predefined styles. 

So you can publish data as fast as you can type text, and customize your styles later.

Couple months later, when you learn some programming, you can create more dynamic webpages - and if you do it on Google App Engine (GAE), Google will host your web application for free.

GAE uses Python, which is cleaner web app language than PHP, and is more generic - if popular also outside web apps. See wiki in my sig for links.

---

### Post by hey_ram on 2008-07-05
hey pmasiar..

just checked out that site...seems like a good place to try it out..

but the site that i have been talking about is my web page hosted by the university...so i can have my details and my resume and that sort of stuff 
on it...

thats y i needed help with what programming language to use..

---

### Post by pmasiar on 2008-07-05
> **hey_ram said:**
> but the site that i have been talking about is my web page hosted by the university...so i can have my details and my resume and that sort of stuff 
on it...

they won't let you run programs on that server. If you have just couple of pages, and don't worry about perfect appearance, plain HTML will be just fine.

And consider suggesting to your IT support person to  host a wiki - any wiki will greatly improve simplicity if page creation for all students. With wiki, you don't need any special HTML GUI design program, nor FTP to upload the files - you just change plain text in your browser's edit window, and save the page. If you can edit text with notepad, you can edit wikipage.

---

### Post by tinny on 2008-07-05
> **CptPicard said:**
> HTML is the base page description language, CSS is for styling (and layout). Start with those, at [http://www.w3schools.com/](http://www.w3schools.com/).

All the rest are programming languages which you are not interested in at the moment. They can be used to do server-side dynamic generation of the page, but you want to be able to just write HTML by hand to begin with.

Yeah, HTML is absolutely fundamental to web development. You need a good understanding of this before you go any further.

---

### Post by T2manner on 2008-07-05
hello!
I'm currently learning how to make webpages too.
I think the best way to start would be learning html/xhtml then css.
I can also recommend a very good book which you can find [here]("http://www.amazon.com/XHTML-Sixth-Visual-Quickstart-Guide/dp/0321430840/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1215315122&sr=8-1")  It's a Very good book for beginners with no prior knowledge of coding
It teaches html/xhtml then css.

---

### Post by elithrar on 2008-07-06
You'll just be using HTML + CSS to start with - and maybe some JavaScript once you're confident in those two. I'd highly recommend forgetting about Python/PHP/Ruby/Perl for now until you've learnt the basics of front-end markup & layout.

---

### Post by hey_ram on 2008-07-15
hi!

I went through the tutorials given on w3schools.com and can say that i am comfortable with HTML, XHTML and CSS. 

I have a question though:
On the basis of what i read, i tried to make my own website. i am unable to get the image to display. the line of code that i am using for the image is as follows:

<img src="DSC02970.jpg" alt="Picture of me" width="200" height="180" align="right" >

the trouble is, though the image displays correctly when i preview the webpage on my system, it does not display after i upload my website on the university server. 

any reason why that may not be happening? any remedy that can oversome the problem?


and more importantly, after CSS, whats nexT?

---

### Post by era86 on 2008-07-15
Check and make sure the image is on the university server.  Also end the tag with />.  After xhtml and CSS, I'd learn JavaScript.  This way, you can add some dynamic effects to your page.

---

### Post by hey_ram on 2008-07-15
hey era86,

thanx for the reply...
i checked...the image is in the same folder as the html file. and i tried closing the tag as well, but it still does not display.

any other suggestions?

---

### Post by mssever on 2008-07-15
> **hey_ram said:**
> hey era86,

thanx for the reply...
i checked...the image is in the same folder as the html file. and i tried closing the tag as well, but it still does not display.

any other suggestions?
Right click where the image should be and choose View image. Then you'll see what the server is sending to the browser. It's likely a permissions problem, but there are many other possibilities.

---

### Post by hey_ram on 2008-07-15
> **mssever said:**
> Right click where the image should be and choose View image. Then you'll see what the server is sending to the browser. It's likely a permissions problem, but there are many other possibilities.

i tried that...

and the error i get is as follows:

error-page not found

HTTP Error Code 404

any suggestions?

---

### Post by hey_ram on 2008-07-15
i tried to look the error up on the web...

and one website says that the "HTTP code 404" is displayed when the server 
a. does not find anything matching to the request.
b. the server cannot display any other error message (because no other is applicable) or when the server does not wish to reveal the exact grounds on which the request was refused. 

the last reason sounds somewhat vague...but given that i am storing the picture to be displayed in the same folder as the html file, it does seem weird why it will display on the pc but not through the server...

any suggestions are welcome.

---

### Post by mssever on 2008-07-15
Verify that the picture actually exists at the path being referenced. 99% of the time, that's the cause of 404 errors.

In some cases, servers are configured to say that a file doesn't exist (404) when in fact some other error occurred. If this is the case, you'll have to do some more detective work (starting with checking the permissions) to find out the real error. However, before considering this as an option, quadruple-check that the file actually exists at the referenced path, because that's the most likely cause.

---

### Post by tuxxy on 2008-07-15
I would start with XHTML forget HTML unless you want to look at HTML transitional or something if the need is there, like if you really wanted to learn about tables... but imo you best sticking with the web compliance of XHTML.

CSS is used with XHTML, the linked stylesheet gives your page its style, the XHTML gives it content, structure.

As PHP can be used within XHTML then it provides a good base for learning to begin PHP, MYSQL etc

---

### Post by Rutger on 2008-07-16
In order to start with webdevelopment, you must start with xhtml because it's the foundation where all the other languages can build on. For example you use css to style your xhtml and JavaScript to add events to your xhtml. But they are of less importance then your xhtml(=content).

---

### Post by leemajors on 2008-07-16
have you checked that the image name on the server wasn't converted to lower case? your image tag is referencing an image name that is all in upper case, and since apache is case-sensitive if the image is named in a different case than the referencing code it just won't display. some ftp clients automatically convert files to lower case when you upload them.

it's a good idea always to use lowercase filenames. that way you won't get into trouble.

and yes, learn html first. learn it like the back of your hand. learn to hand-code.

then learn css. learn that by heart as well. read articles. learn from the community.

by the time you're done with those two, you will have absorbed enough other technologies to have a grasp on what you need, but you should definitely have a look at php, and a database application such as mysql or postgre. 

have fun!

---

### Post by hey_ram on 2008-07-27
hi all!

thanks for the replies!
it turns out the problem was indeed one of character translations. 

i had used the following line for the image descriptor: 

<img src="DSC02970.jpg" /> 

while the actual image was listed with the filename: DSC02970.JPG the trouble came with the file extension, as you can see.

i think my own PC was able to translate the filename but the server was not. some random tries yielded the result. thanx to all those who replied!!

apart from that: i had this question. I was trying to generate an HTML version of my resume and one of the lines has some information aligned right and then the rest of the information aligned to the left. a sample of this is:

some information  (aligned right most)                              July 06 to present (aligned left most)

given this sort of information, how do i encode it using HTML and CSS?
i hope you got my query.

any help is most welcome.

thanx in advance

---

### Post by Reiger on 2008-07-27
If you have not been using CSS then it must be your choice of tags. Two fundamental concepts to understand with XHTML is the idea of block elements and the idea of inline elements. <img>'s and <span>'s are inline; which is to say: these are displayed without carriage returns/line feeds. <div>'s and <p>'s are blocks which means these do have an opening & closing newline auto-inserted around them.

<p>'s are paragraphs for a reason ;-).

---

### Post by mssever on 2008-07-27
> **hey_ram said:**
> i had used the following line for the image descriptor: 

<img src="DSC02970.jpg" /> 

while the actual image was listed with the filename: DSC02970.JPG the trouble came with the file extension, as you can see.

i think my own PC was able to translate the filename but the server was not. some random tries yielded the result. thanx to all those who replied!!You must have been using Windows for development. The important lesson here is that Windows filenames are case-insensitive. In *nix, filename case matters. So foo.jpg is a completely different file than foo.JPG. Be careful of filename case.

> apart from that: i had this question. I was trying to generate an HTML version of my resume and one of the lines has some information aligned right and then the rest of the information aligned to the left. a sample of this is:

some information  (aligned right most)                              July 06 to present (aligned left most)

given this sort of information, how do i encode it using HTML and CSS?
Several options:

[LIST]
[*]Tables are the easiest to set up, but technically, tables are for tabular data, not layout.
[*]You might be able to use the CSS properties float and, if necessary, display.
[*]Failing that, experiment with positioning, though I think that's overkill for this situation.
[/LIST]
One other thing to consider: If you're trying to put this info on the same line, what happens when someone uses a narrow screen (such as a cell phone or PDA) to view your résumé? You should test that case and make sure it looks acceptable.

---

### Post by hey_ram on 2008-07-28
hey..

thanks for the replies...i am using CSS stylesheets for my resume...
i figured i may want to use inline elements for my problem...so im using the <span> element. i defined a class in the stylesheet for the <span> class..the code is as follows:

span.right
{
 text-align: right;
}

but when i try to use it, for example, in the following line...

<li> <strong> <span class="proj_title"> This is project 1 </span> </strong> <span class="right"> May '05 - Jul '05 </span> <br/>
</li>

the text in the first span (with class name proj_title) comes out correctly but not the <span> element with class="right". the text does not align itself to the right. 

where am i going wrong?

and mssever...that was a very good point u raised about accessibility of web pages...i have been reading up on web designing and one of the basic requirements for designing a website seems to be one that is independent of browser configurations, or platform and device constraints..in other words, a web page that can be accessed from anywhere...

but how do u implement it? i mean..can u explain the "float" and "display" properties in some more detail?

thanx

---

### Post by mssever on 2008-07-28
> **hey_ram said:**
> span.right
{
 text-align: right;
}
text-align applies to block elements, but span is inline unless you explicitly change it to block.
> and mssever...that was a very good point u raised about accessibility of web pages...i have been reading up on web designing and one of the basic requirements for designing a website seems to be one that is independent of browser configurations, or platform and device constraints..in other words, a web page that can be accessed from anywhere...

but how do u implement it? i mean..can u explain the "float" and "display" properties in some more detail?
The best place to learn about various properties is to read their documentation. I've used [http://htmlhelp.com/reference/css/](http://htmlhelp.com/reference/css/) in the past for a CSS reference (my CSS knowledge is likely a bit outdated; if there's a better reference, hopefully someone will chip in) and [http://quirksmode.org/css/contents.html](http://quirksmode.org/css/contents.html) for browser compatibility tables.

Implementing what you want is a bit tricky unless you use tables. I couldn't tell you how to do it off the top of my head. I'm thinking, though, that you might be making the mistake of trying to use the same ideas for producing printed documents as for web pages. A layout that makes sense in one might not make sense in the other. It's a good idea to visit [http://useit.com/](http://useit.com/) and subscribe to the Alertbox newsletter.

---

### Post by hey_ram on 2008-08-04
hi mssever!!

thanks for the help. i figured it out and used the following lines in the CSS stylesheet:

span.right
{
 float: right;
 margin-right: 50px;
}

this works just fine. and u were right, the text-align property would work only for block elements and not inline elements. the alignment between the title of the project and the date is not exactly picture-perfect (as in..they are not on the same line) but i think il go along with it for now...

---

