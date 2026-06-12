---
title: "web site programming...."
date: 2008-01-25
forum: Programming Talk
---

### Post by hockey97 on 2008-01-25
Hi I  seen this website  :  [http://www.5gum.com/five/index.do#](http://www.5gum.com/five/index.do#)

and wanted to know what programming knowledge you would need to know to make such a webiste??

I am guessing their using flash?? but not sure.

I would like to be able to create such a site but using a language that is free for commerical use.

---

### Post by Balazs_noob on 2008-01-25
you only need Flash for it
and some basic (x)HTML ...

i don't know yet any free way to make
flash in Linux yet, but lets hope somebody
smarter comes and nows how to do it
because Adobe products are expansive....
[off]
but really i am the only now who hates those
kind of sites ??? it takes forever to load :P
i have a 512/128 net connection
[/off]

---

### Post by Sockerdrickan on 2008-01-25
I hate those kind of sites too.
I just got a faster connection but I HATE the sounds it makes.

---

### Post by DirtDawg on 2008-01-25
> **Balazs_noob said:**
> you only need Flash for it
and some basic (x)HTML ...

i don't know yet any free way to make
flash in Linux yet, but lets hope somebody
smarter comes and nows how to do it
because Adobe products are expansive....
[off]
but really i am the only now who hates those
kind of sites ??? it takes forever to load :P
i have a 512/128 net connection
[/off]

You're not the only one. Flash sites seem cheap to me. They also take too long to load, I never feel like I'm really in control, and they are often hard for me to feel immersed in. Since I have Flashblock installed, half the time i don't even bother opening a site if they're Flash based.

I tried to sit through that one, but I got bored on the elevator thing.  What was that website even for? Gum or deodorant or something?

Anyways, OP, yes you can use Flash to make a site like that. An alternative is to use a combination of HTML, CSS, Javascript and PHP.

---

### Post by Sam on 2008-01-25
Flash is really anoying for web development if you want to make your site search bots friendly. A usual search bot won't follow any flash link nor index the content so it will only index the home page without any text.


Flash is only acceptable for a welcome screen (as long as the "skip intro" link is in html) or for a header (eg: with an animated logo). But this is my point of view...

---

### Post by yino on 2008-01-25
For that page you only need, flash, html and a few knowledeges of javascript.

But I hate those sites too, as a developer they are a hard to maintain since they don't separate the content from the presentation. An alternative for it is SVG and javascript but they have serious browser compatibility issues.

---

### Post by hockey97 on 2008-01-25
well I am trying to make my website look more of a game style then just a nice looking website.

Do you think  I can create somthing like that with javascript??

can you guy's tell me what kind of stuff javascript can do??

i know javascript but I don't know the max it can do.

I been working on a script where the users could resize the table and also move the table around.

I want to make a website that when people use it, they feel the art is soft and the website is interactive.

what I mean about soft in art I mainly mean that the overall website the art blends together acting like one whole part that you can't tell that certain parts of the website are seprate.

and that website advertises about gum lol the elevators take you to a top secret lab where they show you experiments about the gum.
which are noting but advertisments that they show on tv.

I don't plan on using expensive software to create websites it's bad enough I have to pay for a domain name. lol

---

### Post by yino on 2008-01-25
What you need is DHTML, this is the mixture of HTML and Javascript DOM functions (you probably use them at your table resize script), Ajax is recommended too, since it can make your site go smoother without the need of reloading the whole page after clicking a link.

---

### Post by pmasiar on 2008-01-25
> **hockey97 said:**
> 
and that website advertises about gum lol the elevators take you to a top secret lab where they show you experiments about the gum.


useit.com is excellent website about usability (looks ugly, because author designed **usable** design in 96 and did not changed it since). One of the main rules is "users spend most of the time on other websites". If your website looks/navigates differently from most, not many people will waste time understanding how to move around, and will just leave to other "normal" websites.

So I bet not that many people used "lift" to go to "secret lab" - and those who did were in many cases kids with lots of curiosity and free time. It might, and might not, be the desired audience. :-)

---

### Post by Liam-Gorham on 2008-01-25
You should try dreamweaver from adobe it cost's but you can get a free 30 day trial which can be installed on ubuntu using wine. It handles alomst all flash types and is extremly easy to use its more or less drag and drop.


Hopes this helps.

---

### Post by rosegarden78 on 2008-01-25
Wowzers!  My favorite flash game is Boxhead: More Rooms.  You can make games in JavaScript you just need to use an engine like:

script language="javascript"
do
game code here
loop while playing="true"

Or a for/next loop.  Look into Coolnerds Clock or any javascript timer script that uses the built-in timers to make a game engine in JavaScript.  You can make lists of coordinates and use them in a loop to change screen position of sprites.  As long as you can assign event handlers to the keyboard in JavaScript you can probably make a game.

But if you use Flash like Boxhead: More Rooms it's more live action.  JavaScript and PERL maybe used for RPGS multi-player online in the past.  Dungeons and Dragons, on mouse overs that kind of stuff.

---

### Post by hockey97 on 2008-01-25
well right now I am just trying to make 2 websites one is my companies website and the other is a social network place for gamers.

I am currently  trying to build a game console but so far working on websites and hoping to find ways to be able to help fund such a project.

I do plan to later on , on my websites I would like to create either a online game or a game that you can download from my website that connects you to my server and you will play it only in online mode but not  using a web browser.

so any suggestions on any programming language that would let me be able to create a website that when you first open it you can tell this site is about games and gives a gamish interative feeling when you first see my website.

---

### Post by rosegarden78 on 2008-01-25
Well I use the website crazymonkeygames.com it's too bad you can't get a backport of Flash MX it's stable with WINE. :KS

---

### Post by hockey97 on 2008-01-26
what can you do with javascript?? just give me some ideas of when  javascript would be used?? I am using a jquery for javascript stuff.

but I haven't been using javascript long enough to know what advanteges is has.

---

### Post by LaRoza on 2008-01-26
> **hockey97 said:**
> what can you do with javascript?? just give me some ideas of when  javascript would be used?? I am using a jquery for javascript stuff.

but I haven't been using javascript long enough to know what advanteges is has.

First focus on good XHTML and CSS code. 

You don't want to be sticking scripts in for no reason.

When you have enough experience in designing valid pages, you'll find the uses for scripts.

See: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

Valid code, with a little script to enhance the site.

ECMAScript is in [http://laroza.freehostia.com/home/script](http://laroza.freehostia.com/home/script) if you want to see it. It does three things:

0. It highlights the link for the current page
1. It makes the entire block (li) a link, instead of just the text
2. It makes the cursor a pointer so the block element looks like a link

Those are simple enhancements to a site. You can also do form validation (to make it easier and faster for users), which was the original purpose of JavaScript, you can create elements and add content (not really the best thing to do a lot) you can get information, and do simple animations. It allows you to make decisions on the client. Ajax, the use of ECMAScript to communicate with the server to update the page without reloading the page is the newest thing. 

ECMAScript is a tool, it should never be abused and should only be used to enhance a site and it should degrade gracefully.

---

### Post by hockey97 on 2008-01-26
some in another fourm suggested me to use phpnuke.

Just asking here what is the purpose of phpnuke??

and is phpnuke free for commercial use?

---

### Post by LaRoza on 2008-01-26
[http://phpnuke.org/](http://phpnuke.org/)

People suggest what they use, not what would benifit others.

---

### Post by hockey97 on 2008-01-26
but is phpnuke free?? to me it looks like their are restirctions I looked on their site about commercial licenses for 300 bucks per domain.

I know html nd xhtml and css I am certified in it. I just have a problem making the artwork look as one mines like choppysih. I created a html table and tried making the looks of the table to make it look professional I made the tab that supposed to be on top of the table and the backround of the table  but when displayed they become a small line no art is seen so I am having trouble with that.

---

### Post by hockey97 on 2008-01-26
Right now I am having problems with my html table.  I have 2 images one to be like the top part of the table like a tab looking thing. The other image is for the backround of the datacell of the table . I  am having weird outcomes. How do in html made a  backround image to cells??  I have this  <td background="c:\www\tablebk.png" align="left" width"50%" heights"50%">Hello how are you??</td>

that code the outcome is that image is the backround and shows up but now shows that image 2 times and then the hello how are you part that test is centered.


How do you guys deal with sizes how can I figure out what sizes the art needs to be?

---

### Post by Oblique63 on 2008-01-26
> **hockey97 said:**
> Right now I am having problems with my html table.  I have 2 images one to be like the top part of the table like a tab looking thing. The other image is for the backround of the datacell of the table . I  am having weird outcomes. How do in html made a  backround image to cells??  I have this  <td background="c:\www\tablebk.png" align="left" width"50%" heights"50%">Hello how are you??</td>

that code the outcome is that image is the backround and shows up but now shows that image 2 times and then the hello how are you part that test is centered.


How do you guys deal with sizes how can I figure out what sizes the art needs to be?

Could you maybe post a screenshot of that, and some more of the code (and CSS if u have any for that object)?  Im having a hard time visualizing exactly what you mean

Im also a (X)HTML, CSS, Javascript designer and stuff btw...

---

### Post by hockey97 on 2008-01-26
well here is a screen shot I made and I am hosting the shot from my server which means it wont be on the whole day ect.

here is the link :   

here is all the html code and css that I have in it. Thanks for the help.


do you got any ideas where I went wrong?? is the images too big??  do I need to make the images small to fit nicely.

SOLVED....

---

### Post by hockey97 on 2008-01-26
any ideas?? I been playing around with the code and still haven't solved it.

---

### Post by LaRoza on 2008-01-26
Fix the code, use the w3c validator to assist in this.

Your code is wrong, and I doubt it would work in any browser.

---

### Post by Oblique63 on 2008-01-26
well, this is what I came up with (not my best coding here, but for ur purposes, maybe it'll work):

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<style TYPE="text/css">
	.deepsea, .deepsea TD, .deepsea TH {
		background-image:url(c:\www\tablebk.png);
		color:#0C4B86;
		font-family:sans-serif;
		font-weight:600;
	}

	body {
		background-image: url(C:\www\chillenvillenart\backround.png);
	}
</style>

<body>

<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="255" height="30"></td>
	</tr>
</table>

<table width="10" height="10"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="30" height="215"></td>
		<td><img src="http://www.mexicanpictures.com/archives/photos/amdo/raulinhiselement.jpg" width="195" height="215"></td>
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="30" height="215"></td>
	</tr>
</table>

<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="255" height="30"></td>
	</tr>
</table>

<table width="50%" height="50%" border="0" cellpadding="0" cellspacing="0" class="deepsea">
	<tr>
		 <th style="background-image: url(c:\www\smtab.png); width: 45%; height: 30%;"></th>
	</tr>
	<tr>
		<td style="background-image: url(c:\www\tablebk.png); text-align: left; clear: left;" width="50%" height="50%">
        Hello how are you??
        </td>
	</tr>
</table>
</body>
</html>

```

just a few minor changes. I cant really ensure it'll work tho, seeing as how I dont have access to some of the image files, but try it and see how it comes out.

---

### Post by LaRoza on 2008-01-26
Check out the <head> element, which is required.

---

### Post by hockey97 on 2008-01-26
does doc type really matter?? like do I really need to put the doctype?

---

### Post by Oblique63 on 2008-01-26
> **LaRoza said:**
> Check out the <head> element, which is required.

haha, wow... nice catch, I didnt even notice there wasnt a head in the original...

do over:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">

<head>
<style TYPE="text/css">
	.deepsea, .deepsea TD, .deepsea TH {
		background-image:url(c:\www\tablebk.png);
		color:#0C4B86;
		font-family:sans-serif;
		font-weight:600;
	}

	body {
		background-image: url(C:\www\chillenvillenart\backround.png);
	}
</style>
</head>

<body>

<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="255" height="30"></td>
	</tr>
</table>

<table width="10" height="10"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="30" height="215"></td>
		<td><img src="http://www.mexicanpictures.com/archives/photos/amdo/raulinhiselement.jpg" width="195" height="215"></td>
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="30" height="215"></td>
	</tr>
</table>

<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">
	<tr bgcolor="darkred">
		<td><img src="http://images.closetorganizersource.com/mgen/swatch:SCI007_16_WoodCherryFinish.jpg" width="255" height="30"></td>
	</tr>
</table>

<table width="50%" height="50%" border="0" cellpadding="0" cellspacing="0" class="deepsea">
	<tr>
		 <th style="background-image: url(c:\www\smtab.png); width: 45%; height: 30%;"></th>
	</tr>
	<tr>
		<td style="background-image: url(c:\www\tablebk.png); text-align: left; clear: left;" width="50%" height="50%">
        Hello how are you??
        </td>
	</tr>
</table>
</body>
</html>

```

---

### Post by Oblique63 on 2008-01-26
> **hockey97 said:**
> does doc type really matter?? like do I really need to put the doctype?

THats one thing that Im not sure about, but I know that in the past that has (somehow??) fixed a few layout issues for me, so better safe than sorry I guess...

---

### Post by LaRoza on 2008-01-26
Use the w3c validator.

Yes it is required. 

Look at mine: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

I use XHTML 1.1 and state I do because that is the only way the clients (browsers, in this case) can use your code. If they assume otherwise, and go into quirks mode or something, you get unpredictable results. Always stick to the standards (at least, the standards that are implemented)

The w3c validator says it has 47 errors when validated against the DOCTYPE XHTML 1.1.

---

### Post by jan quark on 2008-01-26
and in my opinion 

I would strongly recommend to distinguish between style and content

content is html

style is css

make another css file and implement it into your html
in makes the coding cleaner and more elegant

try this website I learned there how to make my page
[http://htmldog.com/](http://htmldog.com/)

---

### Post by LaRoza on 2008-01-26
> **jan quark said:**
> 
I would strongly recommend to distinguish between style and content


Or my page, which keeps all Markup, Presentation and Behavior separate. (XHTML, CSS, ECMAScript)

Your page has script mixed with the markup. Probably not your choice though right?

---

### Post by Oblique63 on 2008-01-26
> **jan quark said:**
> and in my opinion 

I would strongly recommend to distinguish between style and content

content is html

style is css

make another css file and implement it into your html
in makes the coding cleaner and more elegant

try this website I learned there how to make my page
[http://htmldog.com/](http://htmldog.com/)

I concur... take all my style 'hacks' and stuff and put it on an external file and link it via ```
<link rel="stylesheet" type="text/css" href="*stylesheet*.css" />
```

its a lot easier to deal with once you assign all your attributes in a separete file and leave the html as minimal as possible

---

### Post by jan quark on 2008-01-26
boy 

that was a lot of work but I looked through my whole html code and now every single page is xhtml strict valid

I am proud to have this little w3c sign[IMG]http://www.w3.org/Icons/valid-xhtml10-blue[/IMG]on every page 


it gives me a good feeling and shows my respect towards the reader of my page

and it makes the internet a better place...

and I strongly recommened this way of validating your page to you

---

### Post by LaRoza on 2008-01-26
> **jan quark said:**
> boy 

that was a lot of work but I looked through my whole html code and now every single page is xhtml strict valid

I am proud to have this little w3c sign[IMG]http://www.w3.org/Icons/valid-xhtml10-blue[/IMG]on every page 

it gives me a good feeling and shows my respect towards the reader of my page

and it makes the internet a better place...

I like it too, although I use a text link. XHTML 1.1 I use.

[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Flaroza.freehostia.com%2Fhome&warning=2&profile=css2&usermedium=all](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Flaroza.freehostia.com%2Fhome&warning=2&profile=css2&usermedium=all)

CSS is good too. I just checked it, and it is good on the first try.

---

### Post by jan quark on 2008-01-26
how did you check my css?

---

### Post by LaRoza on 2008-01-26
> **jan quark said:**
> how did you check my css?

I checked mine.

---

### Post by LaRoza on 2008-01-26
> **jan quark said:**
> how did you check my css?

[http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fhtmldog.com%2F&warning=1&profile=css21&usermedium=all](http://jigsaw.w3.org/css-validator/validator?uri=http%3A%2F%2Fhtmldog.com%2F&warning=1&profile=css21&usermedium=all)

You're good too.

Good job.

/me pats back and my own

---

### Post by hockey97 on 2008-01-26
> **jan quark said:**
> and in my opinion 

I would strongly recommend to distinguish between style and content

content is html

style is css

make another css file and implement it into your html
in makes the coding cleaner and more elegant

try this website I learned there how to make my page
[http://htmldog.com/](http://htmldog.com/)

I am making a table of buttons kinda like a control panel thing where you click buttons to do certian things like edit or add music ect.

would I be able to make a table with css?? I am trying to make a rectangle box with buttons in it that each button does different things.

I am having problems getting the backround graphic to size the way I want it.

---

### Post by jan quark on 2008-01-27
have a look at 

[http://www.csszengarden.com/](http://www.csszengarden.com/)

there you can click through many css designs and even see the css code
so you can learn how to achieve the visual presentation

its a great site, I have learnt and still learn a lot from it

---

### Post by LaRoza on 2008-01-27
> **jan quark said:**
> have a look at 

[http://www.csszengarden.com/](http://www.csszengarden.com/)

there you can click through many css designs and even see the css code
so you can learn how to achieve the visual presentation

its a great site, I have learnt and still learn a lot from it

[http://laroza.freehostia.com/home/apps/styleTester/index.php](http://laroza.freehostia.com/home/apps/styleTester/index.php)

I wrote this to allow developers to see what styles did in different browsers and platforms.

---

### Post by hockey97 on 2008-01-27
ok I got a question about css with backround is their any ways where I can resize the backround image??? I have heard rumors that css3 would have a way to handle backround images by resizing that image.

---

### Post by hockey97 on 2008-01-27
I read tutorials on css and also videos on css to what I saw css can only position tables and images ect any elements but it can't resize the backround image.

So how in css can I make an image to be able to put other images on top of it??

I am trying to create a panel of buttons but the backround has to look like a nice table looking thing. I created a backround art of 100px width and 300px in height. 

Now I made the table with those same dimesions. I then test it and no backround image. It wont display. I am using div tags and ids to apply css to my table

---

### Post by LaRoza on 2008-01-27
> **hockey97 said:**
> I read tutorials on css and also videos on css to what I saw css can only position tables and images ect any elements but it can't resize the backround image.

So how in css can I make an image to be able to put other images on top of it??


I don't think you can resize background images.

Look into z-index and position.

---

