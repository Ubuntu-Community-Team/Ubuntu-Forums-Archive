---
title: "what's the deal with &lt;div&gt; tags?"
date: 2006-06-21
forum: Programming Talk
---

### Post by oldmanstan on 2006-06-21
can someone please explain to me precisely WHY divs are so much better than simple html tables? i mean, beyond the fact that they can be floated and whatnot. obviously tables had huge disadvantages but i don't see divs being much better...

every time i work with them i spend more time fighting to get them to do what i want than i do actually building a page or design.

specifically: why are they so "dumb", they don't realize when they're overlapping each other so enormous measures have to be taken to get them to play nice with one another and if you slap a new theme or template on a blog that uses them you suddenly find that all your images overlap everything else on the page.

also, when you put one <div> inside another <div> why does the outside one steadfastly refuse to expand when the inside one expands? what is the point of nesting them if they're just going to act like they're separate entities rather than containers?

am i the only one who gets frustrated by this? maybe it's just my ignorance, i'd really like to understand better.

---

### Post by TigerWolf on 2006-06-21
Its to do with the XHTML compliance standards. Im not exactly sure why but divs are better for compliance and also something to do with CSS. Not exactly sure, someone correct me on this.

---

### Post by LordHunter317 on 2006-06-21
[QUOTE=oldmanstan]can someone please explain to me precisely WHY divs are so much better than simple html tables?[/quote]The theory being that a div is an arbitrary block of content, while a table has the semantic meaning of tabular data.  

Besides for some accessiblity and some occasional rendering issues, the practical difference may be little.

> specifically: why are they so "dumb",They're not dumb.  THey follow the block element rules.  

> they don't realize when they're overlapping each otherThey shouldn't be unless you told them to.

I really think you need to read up on the CSS Box model and how it works, carefully.  Don't feel bad, it's really complicated and convoluted, so it's difficult to understand how the layout really works.

---

### Post by Xzallion on 2006-06-21
div tags are used for css because you can do alot more to them with css then you can with Tables, and make a website look completely different using them.  Check out the [css zengarden]("http://www.csszengarden.com/") to see how it works with templates.

They can do alot more because they are general containers and not a specific container.  check this out for some [info]("http://www.decloak.com/Dev/CSSTables/CSS_Tables_01.aspx").

Edit: Darn you beat me to it LordHunter317

---

### Post by SilverTab on 2006-06-21
Yup, if you know your CSS well, Divs are great!

Especially when you start messing with all those Web 2.0 JS library like script.aculo.us or Yahoo UI...(especially scriptaculous effects...they don't do well with tables)

I didn't use a single table in my latest web-designs...just divs and CSS...
It IS more complicated to get started with, but once you get the hang out of it, you have much more control over what you are doing...

---

### Post by oldmanstan on 2006-06-22
ok, i really have tried to figure it all out but every resource on the web seems to have the same info. the descriptions of the selectors and classes are all single sentences and i can't seem to figure my problem out.

basically i'm fine using CSS for most things, it's just with div tags i get messed up.

for instance: a two column layout is easy, two sets of div tags with one of them set to float left or right. the problem is when i try to put them in a container (to make it all look like a single smooth column rather than having to worry about the sidebar being shorter than the content, etc.)

the container won't wrap itself around the floated div tag, what gives? is there an obscure property i can set? or should i just rethink this and find another way?

i know it's possible since there are sites out there that seem to do it and i've looked at their sources (i just can't seem to figure out how exactly they get it to work), maybe i'm going about it the wrong way?

---

### Post by LordHunter317 on 2006-06-22
[QUOTE=oldmanstan]ok, i really have tried to figure it all out but every resource on the web seems to have the same info. the descriptions of the selectors and classes are all single sentences and i can't seem to figure my problem out.[/qote]Those aren't terribly relevant to the *box model*.  That's what you need to learn about.

> basically i'm fine using CSS for most things, it's just with div tags i get messed up.They're not really any different from <p> tag for the most part.

>  the problem is when i try to put them in a container (to make it all look like a single smooth column rather than having to worry about the sidebar being shorter than the content, etc.)

the container won't wrap itself around the floated div tag, what gives?Because you floated them.  The child divs are rendered and then pushed as far to the left or right as they can be.  The parent's position is set based on floating children.

---

### Post by oldmanstan on 2006-06-22
ok, i understand that the box model is the issue here, i read this page [http://www.w3.org/TR/REC-CSS2/box.html](http://www.w3.org/TR/REC-CSS2/box.html) thoroughly and i still do not understand how to solve my problem.

is it just impossible to get a containing div tag to expand to fit around a floating div tag within it? i understand that floating the box takes it out of the normal flow of the document but it is still within the container (not like positioning it absolutely)

the whole model annoys me because it almost seems like it is designed to be confusing.

---

### Post by s|k on 2006-06-22
[QUOTE=oldmanstan]can someone please explain to me precisely WHY divs are so much better than simple html tables? i mean, beyond the fact that they can be floated and whatnot. obviously tables had huge disadvantages but i don't see divs being much better...

every time i work with them i spend more time fighting to get them to do what i want than i do actually building a page or design.

specifically: why are they so "dumb", they don't realize when they're overlapping each other so enormous measures have to be taken to get them to play nice with one another and if you slap a new theme or template on a blog that uses them you suddenly find that all your images overlap everything else on the page.

also, when you put one <div> inside another <div> why does the outside one steadfastly refuse to expand when the inside one expands? what is the point of nesting them if they're just going to act like they're separate entities rather than containers?

am i the only one who gets frustrated by this? maybe it's just my ignorance, i'd really like to understand better.[/QUOTE]

Tables are for tabular data, they're not meant to hold spacer.gif and seamless images or portray your site graphically.

---

### Post by bieber on 2006-06-22
The trick to CSS design is practice, practice, practice.  I'd say it took me the better part of a year to become really comfortable with XHTML and CSS.  But once you know how to use it all, the idea of using tables just looks idiotic.  Tables are messy, obfuscated crap.  With CSS, you can keep your markup clean and easily readable, and move style information into a seperate document, which also makes it easy to switch styles for different screen resolutions and media and so on.  A lot of your problems seem to be stemming from using relative position of one type or another.  I used to try and do that, but it tends to get overly complicated.  Now I pretty much exclusively use fixed width absolute positioned designs (I aim for 800px or 640px wide screens, for the most part).  Here's a couple of sites I've done, I think the markup should be simple enough for you to understand (I try to keep it clean, indent properly, and so on).  The CSS might be a little cluttered, feel free to ask if you have any questions about it all.
[list]
[*][Two column layout with header, done for Real Estate company](http://bradenton-real-estate-connection.com)
[*][Single column and vertical tabs layout, for my personal site (desperately needs new graphics](http://www.bieberworks.net)
[*][Two column layout with header, class project](http://www.bieberworks.net/equations)
[/list]

In that last one, I sort of cheated and used divs like tables.  There was just no way I could think of to get the sidenote effect without compromising a little on semantics...

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=bieber] Tables are messy, obfuscated crap. [/quote]Not really.  For lots of layouts, the layout with a table is simpler and clearer to implement.  If HTML tables had a column-major form, then they'd almost certainly be better than any CSS based layout.

Anyway, CSS layouts have their own problems: lots of layouts require divs in divs: one for formatting/layout and one for the actual content, in order to appease the layout model.

>  Now I pretty much exclusively use fixed width absolute positioned designs (I aim for 800px or 640px wide screens, for the most part).Which while not a universal sin, is frequently a sin.  I have higher-res monitors, why shoyld I be forced to see the entire document in a narrow window?

---

### Post by oldmanstan on 2006-06-23
ok, lordhunter, one final, i've read a lot of different opinions and what not, if i wanted to do my basic layout using html tables (and i stress basic, i can use divs for any other areas) it sounds like i wouldn't be committing a horrible sin against the computer gods? am i correct?

because from everything i've read it is totally impossible to get a div tag to do exactly what i want it to do without positioning it absolutely (which i don't want to do for this layout) but with a simple 3 column html table i can get it to do exactly what i want.

also, thanks everyone for all the suggestions / advice / pointers, i have learned a lot!

---

### Post by bieber on 2006-06-23
You *really* don't want to use tables.  Just like you wouldn't want to design an application to run on Windows 95.  Tables are old, and already mostly rejected by the best of the web developers/designers, it's only a matter of time until they're rejected universally.  At which point, good luck trying to find a job when you're still using a technology that no one wants anymore, and didn't bother learning the new ways.

I'll say again, tables are not simpler.  They're easier to figure out, not to use in the long run.  Anywho, if you're looking to do a fluid three column layout, have a look-see here.
[http://www.alistapart.com/articles/holygrail/](http://www.alistapart.com/articles/holygrail/)

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=oldmanstan]ok, lordhunter, one final, i've read a lot of different opinions and what not, if i wanted to do my basic layout using html tables (and i stress basic, i can use divs for any other areas) it sounds like i wouldn't be committing a horrible sin against the computer gods? am i correct?[/quote]No.  A one-table layout is hardly a terrible sin.  I wouldn't go crazy and do nested-tables-in-tables in tables, but here's the engineering reality of the matter:[list][*]If the 3-column table will work[*]It will render correctly in the browsers you care about[*]It doesn't break any accessibility issues or Javascript or whatever else you're doing, and[*]It requires less work than getting the div layout going[/list]It is the superior solution.  That's the end of it.

[quote=bieber]Tables are old, and already mostly rejected by the best of the web developers/designers,[/quote]No, they're not.  They're rejected by the *most vocal web developers*, but that doesn't mean best.  In fact, they're usually the worst because their sites:[list][*]Have little to no real-world applications[*]Don't actually care about accessibility[*]Are slow or otherwise underperformant[*]Are difficult for low-bandwidth users[/list]

>  it's only a matter of time until they're rejected universally.Nope, table tags will be removed because some of us do actually need to display tables from time to time.

> At which point, good luck trying to find a job when you're still using a technology that no one wants anymore, and didn't bother learning the new ways.I've held several jobs working with legacy technology.  They're usually more lucrative than other jobs because the pool of talented people is smaller.  Less supply and higher demand means wages go up.  Good for me, bad for my employers.

---

### Post by foobar on 2006-06-23
once you know how to work with divs, you will never want to use tables again... unless you're pulling data out of a db.

for your your 3 column layout check out-
[http://css.maxdesign.com.au/floatutorial/](http://css.maxdesign.com.au/floatutorial/)

---

### Post by oldmanstan on 2006-06-23
[QUOTE=bieber]Anywho, if you're looking to do a fluid three column layout, have a look-see here.
[http://www.alistapart.com/articles/holygrail/](http://www.alistapart.com/articles/holygrail/)[/QUOTE]

ok, i checked it out but i already knew how to do that, my problem is that i want the divs to increase their height so that they are all the same height as the column with the most content, take a look at the [example]("http://www.alistapart.com/d/holygrail/example_1.html") from that site, the left column (at least at my display resolution and whatnot) is shorter than the others, i think that is ugly.

p.s. thanks for all your help everyone, it is an interesting debate, i never realized there were so many opinions, i think i'll stick to tables for now since a) i'm not looking to be a professional web designer anyway and b) i agree with the engineering model that if it works best it is best

---

### Post by s|k on 2006-06-23
[QUOTE=LordHunter317]Not really.  For lots of layouts, the layout with a table is simpler and clearer to implement.  If HTML tables had a column-major form, then they'd almost certainly be better than any CSS based layout.[/QUOTE]
No they would not be better because you are using tables incorrectly. Tables are meant for tabular data. There are software other than browsers accessing web sites, and not everybody access data in order to see how it looks graphically. HTML is meant for semantic structure, not graphical design. Using tables will never be better than using CSS for graphical display because that's not what it is used for. If you're thinking 'well it accomplishes the task I want it to' then you're thinking in very narrow terms.

---

### Post by digby on 2006-06-23
[quote=oldmanstan]ok, i checked it out but i already knew how to do that, my problem is that i want the divs to increase their height so that they are all the same height as the column with the most content, take a look at the [example]("http://www.alistapart.com/d/holygrail/example_1.html") from that site, the left column (at least at my display resolution and whatnot) is shorter than the others, i think that is ugly.[/quote] If I'm understanding you correctly, then what you want should be rather simple to implement.  The way I did this was to have a footer div beneath my columns that had the same width as my container and the css property clear: both;.  This made sure that it was at the bottom of the tallest column div and the other would auto-stretch to fill in.  It worked in IE and FF without trouble.  I never tested it in another browser, though.

[Link to my example]("http://umdrive.memphis.edu/mhollis/public/cleanlooks")
[Link to example's CSS]("http://umdrive.memphis.edu/mhollis/public/cleanlooks/style.css")

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=s|k]No they would not be better because you are using tables incorrectly. Tables are meant for tabular data.[/quote]And?  Columns can be considered a form of tables when you get down to it.  Saying there's an implied semantic meaning there is wonderful, but only useful when everyone agrees what that semantic meaning is.  

The problem is that HTML doesn't actually imply any higher-order semantical whatsoever with any elements.  <p> means "paragraph" but that's not actually what a <p> represents, gramatically speaking.

So semantic arguments are somewhat fundamentally shaky.  <table> doesn't actually mean, "This data is tabular" despite the fact it ought to.  There's no way to enforce that.  What it does mean is, "Render this data like a table".  Web designers would be smart to remember that.  Adding meaning that doesn't really exist is a rather precarious position when it comes to working with computers.

>  There are software other than browsers accessing web sites, and not everybody access data in order to see how it looks graphically.And they're ultimately to what the standard means.  Most tools looking at the data in other ways care little to none at all about the actual markup.

> HTML is meant for semantic structure, not graphical design.No, it's meant for semantical layout.  No more, no less.

> Using tables will never be better than using CSS for graphical display because that's not what it is used for.Clearly though, it does.  Especially given that CSS is stupidly inadequate for many types of layout tasks (arbitrary numbers of columns, for example).

Frankly, the rendering rules for a table (which is the only semantic meaning you always have with a <table> tag) make more sense than the CSS rules for blocks in a ton of situations.

>  If you're thinking 'well it accomplishes the task I want it to' then you're thinking in very narrow terms.Yet that's what engineers do and are paid to to.  That's how business make virtually all of their decisions.  So no, I'm not thinking in narrow terms.  Even if I were, that's all my customers care about.  The actual markup matters little if the content is delivered effectively at the end of the day.

---

### Post by bieber on 2006-06-23
You're forgetting that HTML isn't just meant to be arbitrarily interpreted, LordHunter.  There *are* standards for what it is all supposed to mean, per the W3C, and the standards have dictated, since the introduction of CSS, that (X)HTML should be used for laying out data in a sensical, semantic order, and then stylesheets should be applied to that data to allow the developer to control how it will be rendered on a screen.

In any case, tables may "just work" for some layouts, until you want to do a redesign.  Or until you want to allow your visitors to choose a style.  Or until you want your site to be easily readable on *any* browser, including text based and mobile platforms.  Or until you want to be able to hire a designer other than the one who originally created your site to modify it (and not have them have to start the whole thing over again from scratch because they can't understand the last designer's tag soup).  And as for the layouts where tables may be a little (stressing the word "little) bit easier, CSS3 is going to include a layout module to allow you to use CSS to lay out content in a grid like you would with tables (although I'd say we should really be focusing on getting *away* from the grid) without compromising on the semantics of your markup.

---

### Post by LordHunter317 on 2006-06-23
[QUOTE=bieber]You're forgetting that HTML isn't just meant to be arbitrarily interpreted, LordHunter.[/quote]You're correct.  But the claim, "tables are only meant for tabular data" is an arbitrary and wholly incorrect interpretation of any of the HTML and CSS standards, which was my whole point.

The only thing that is standardized is how elements are layout, rendered, and the syntax tree.  There's no standard that says '<p>' must be only used for paragraphs and '<table>' must only be used for tables.

> There *are* standards for what it is all supposed to mean,Actually, there really isn't.  More importantly, *they're not enforced*, so they really don't count.

> and the standards have dictated, since the introduction of CSS, that (X)HTML should be used for laying out data in a sensical, semantic order,And using tables for other than traditional tabular data may be semantically correct.  A group of columns is a table in all mathematical and computational senses.  That's the problem.  "Sensical and semantic" are pretty broad terms.

> and then stylesheets should be applied to that data to allow the developer to control how it will be rendered on a screen.Which would be wonderful if CSS didn't actually make simple things so damned bloody difficult.  There's a reason why no one is fully fully fully CSS 2.1 compliant.  The specification is complicated, poorly written, and ultimately bad in a whole host of respects. 

> In any case, tables may "just work" for some layouts, until you want to do a redesign.You've failed to show how divs make this eaiser.  They don't universally do so, that's for certain.  It takes a lot of forthought to design a website in such a way that radical presentation changes can be made without touching the HTML.  Mostly because again, CSS is rather poor at specifying what you really want to say.

> Or until you want to allow your visitors to choose a style.Not especially, given that choice usually comes down to color and other minor items.  All of which work just fine with tables.

Most sites don't support drastic layout changes because that's disorienting and makes other issues like support more difficult.  "Where's the link?" "It's over there"  "No it's not" and the like.

More importantly, the data driving your website may very well mandate only a few limited correct presentations.  And well written websites are data-driven anyway.

> Or until you want your site to be easily readable on *any* browser, including text based and mobile platforms.Text based is one concern (and I noted accessibility issues at teh beginning).  Mobile platforms usually get special content served to them anyway, because you don't want to be sending all the data.  It has as much to do with data as it does presentation.

> Or until you want to be able to hire a designer other than the one who originally created your site to modify it (and not have them have to start the whole thing over again from scratch because they can't understand the last designer's tag soup).There's nothing intrinsic about divs that ensure that.  And in my experience, divs can contribute highly to this problem simply because you can't always express everything about a block in a block.  You have to apply attributes to the parents as well, when you shouldn't.


 >  CSS3 is going to include a layout module to allow you to use CSS to lay out content in a grid like you would with tables (although I'd say we should really be focusing on getting *away* from the grid) without compromising on the semantics of your markup.Wonderful.  When browsers start supporting it, which will probably be not until the next decade or so, we can talk about it.

---

### Post by oldmanstan on 2006-06-24
wow, ya know, i really didn't know this was such a debate until i asked the question, however, having read both sides (here and now on some other sites) it seems like a lot of arguing about very little.

for instance, to say that using divs somehow fixes the "tag soup" problem is a little arrogant. first of all, many people nest div tags and use footers to do tricks with the layout (note that div tags are even used "incorrectly" in the sense that they are used to generate a specific "look" rather than just organizing data.

also, of all the [x]html and css source i've looked at the CSS source is the most tag soupish since custom class names are arbitrary and since the formatting is in a separate document it is often harder to get a handle on what is going on. ALSO, people tend to define different aspects of an attribute in different places, so in a 200 line CSS file you might have 4 different places where the <p> tag is being worked on. so if you want to change the formatting of this tag you have to hunt through the file (if you didn't write it or have forgotten) to find where exactly the attribute you want was defined, if at all.

i don't know, i think that as long as people demand complex formatting for their sites there is absolutely nothing that can give it to them without being complex, so to argue that xhtml and css is some magic bullet is just ridiculous. complexity and power are often positively correlated, there's no getting around it.

it seems also that the more complex we make the web technologies (and yes, css and xhtml ARE more complex just by the number of tags available) the less accessible the technology is to people like me (nonprofessionals).

back in the day (mid nineties) when compuserve finally loosened up internet access i remember throwing up my first web page and having it look fairly decent compared to many of the other pages out there. nowadays i would almost need to go to school to learn how to make pages that would be truly mine (not some template or "theme") and still be considered "ok" by most people.

it seems the more complex everything gets, the more it sort of "gets away" from ordinary people and the more there is this internet bourgeousie class that seems to like it this way. kinda sad.

just some thoughts from an amateur.

---

### Post by LordHunter317 on 2006-06-24
> **oldmanstan]for instance, to say that using divs somehow fixes the "tag soup" problem is a little arrogant. first of all, many people nest div tags and use footers to do tricks with the layout (note that div tags are even used "incorrectly" in the sense that they are used to generate a specific "look" rather than just organizing data.[/quote]Right, and the point to remember is (I'm driving this home because others don't seem to be getting it):**CSS forces you to do this said:**
> ALSO, people tend to define different aspects of an attribute in different places, so in a 200 line CSS file you might have 4 different places where the <p> tag is being worked on.Given that CSS is hierarchical, this may be perfectly correct:```
#sidebar p
// ...
#mainsite p
```Those two paragraphs are in different sections of the page and are unrelated when it comes to layout.  Hence, the two definitions.  This can be a little disconcerting at first, but makes sense when you realize that sinec HTML is hierarchical, CSS really must be too.

---

### Post by v8YKxgHe on 2006-06-24
Tables are for Tabular data, last time I checked a template is not tabular data. CSS positioned DIV's are the way to go, they are easier to use,maintain,style and also outputs cleaner faster code that is W3C compliant! 

Please, do the internet a favour and use DIV's and not Tables for templates. I really don't see why HTML is beeing used, XHTML and CSS is the way to go because most, if not all portable/hand held devices use XHTML/CSS to display webpages instead of HTML/Tables. 


[Read this on why Tables should not be used for templates]("http://web.archive.org/web/20041101045406/www.hotdesign.com/seybold/everything.html")

---

### Post by LordHunter317 on 2006-06-24
[QUOTE=AlexC_]Tables are for Tabular data, last time I checked a template is not tabular data.[/quote]Who said anything about templates?  More importantly, you missed my commentary about columns being tables.

> CSS positioned DIV's are the way to go, they are easier to use, maintain, style and also outputs cleaner faster code that is W3C compliant! No one has shown any of that to be true.  You're making the same arguments everyone else has made.  Only, you've failed to support them.  Your making an argument by declaration, and it's just as invalid as everyone else who's made it.

It may render slightly faster than a table, in certain situations, due to the rendering rules for a table.  But that's not the only way to measure speed, nor the only useful way.  

The time to emit all of the HTML may be vastly more important.  In fact, for dynamic applications, it's almost always more important.  The client only has to handle one connection, the server hundreds or thousands.

> I really don't see why HTML is beeing used, XHTMLXHTML fails to add a single truly useful thing to HTML at this point.  Making HTML documents XML isn't useful, because I still cannot use a XML parser for HTML at the end of the day (because not all HTML is XHTML).

On the server side, the only useful thing it enables is much easier XSL-driven generation of HTML documents.  But that ability would have occured even without XHTML: we'd either use XSL-FO (ick) or some sort of other XSL specialization for rendering SGML.  XHTML certainly isn't the only path to this solution.

On the client side, the only useful thing is to be able to embed other XML namespaces in an HTML document.  But the value of that currently (and likely into the future) is rather dubious, at best.

>  and CSS is the way to go because most, if not all portable/hand held devices use XHTML/CSS to display webpages instead of HTML/Tables.You're utterly and totally crazy.

The arguments on the page are rather specious as well.  Presentation data for an entire *site* usually measures in the few tens of kilobytes, at most.     If you care that much about bandwidth utilization, you ultimately have other problems to deal with that are more fundamental.

CSS doesn't really lend much to visual consistency by itself; with dynamic webpages it's trivial to enforce visual consistency in virtually any framework: ASP.NET, all of the J2EE frameworks, RoR, Turbogears, Django, several PHP frameworks, Perl's Mason and Template stuff, etc.  IOW, the argument that CSS leads to visual consistency isn't sufficent. 

 It's more than just the styles applied: if I render the same set of data (say a list of products on the search page and the category page) on two different pages, I have to use the same HTML tags as well if I want a consistent presentation.  CSS doesn't provides a solution for this; neither does HTML.  It's only a partial solution, but the problem is that the solution provided by the web framework can do everything CSS can (though perhaps not as easily or cleanly sometimes).  But CSS isn't a *requirement* for visual consistency, and it isn't a complete solution to that problem.

CSS does help lend to device independence, but the fallacy here is that we want to serve the same content to everyone. We frequently don't.  Mobile users generally get served less data to begin with, because they don't need or want the complexity of full pages; persuming they're served HTML at all, which isn't a safe assumption to make.

Also, the fundamental layout of data may be a problem: horizontial bars don't work well on mobile clients.  Neither do multiple columns, unless they're very narrow (and then on a say a cell-phone, they still may be useless).  This again, ultimately means that you have to do more than just change the CSS.  You frequently have to change the actual markup you're sending.

Also, CSS doesn't give any way to differentiate between browser types, so it's still not a complete solution anyway.  The media attribute of a link tag doesn't go far enough, so I can't just link in a mobile and regular stylesheet and expect everything to work correctly.

His table example with spacer gifs is excessive and wrong, most sites do not code that way.  And using tables doesn't require it, as his next example clearly shows.  So he does a great job of wrecking his own argument.

---

### Post by s|k on 2006-06-26
[quote=LordHunter317]You're utterly and totally crazy.[/quote]

LordHunter, you have really hijacked this discussion with angry language and dogmatic views. The idea that an HTML element has no semantic meaning in itself is like saying the graphical representation of numbers have no meaning.

It is a tautological argument with no direction. XHTML has a Document Type Definition and a schema that the developers of browsers (including Microsoft) have been a part of in developing (the W3C standards). For you it's just a matter of making it work, but you ignore the foundations of the technology. The DTD and the schema clearly explain the meaning and use of the elements. No, nobody is going to put a gun up to your head and enforce these rules on you. The internet is a collaborative environment where people voluntarily work together to create projects that enhance accessbility and strive to make diverse elements work through a common interface: the web. Unfortunately, this system has been abused by shady elements, and people who do not care about the works of others. 

The comment you made that XML doesn't add anything to HTML, shows that you have never worked with or at least learned to appreciate the vast adoption of XML technology in just about every major, widely used, high level programming language I can think of. With tools in PHP5, Python, and C I can take a valid XHTML page and traverse it using SimpleXML or DOM tools, very easily without having to resort to regular expression madness.

Overall, you are wrong on just about all accounts. You seem to be against the w3c standards for no good reason other than it does not suit your own purposes. Completely blind people and others with visual impairment were not left out of when HTML was designed, however your approach completely ignores them. It completely ignores other software that accesses data on the internet, it completely ignores the enourmous amount of effort that information professionals, engineers, various organizations, governments, and corporations are putting into making the internet more usuable, making it easier to find information, making it better. Your attitude is a detriment to your customers, and unfortunately they don't know better. Your attitude is also selfish and unprofessional.

..and honestly, why are you even using FOSS software or spend time on this forum? You obviously do not believe in or care about Ubuntu's message. You certainly haven't picked up on the friendlyness of the community.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=s|k]LordHunter, you have really hijacked this discussion with angry language and dogmatic views.[/quote]O RLY?

The **first person** to bring up the whole "Tables aren't for layout" issue was **you**.  So if you're going to get up on your high-horse and attack someone, make sure your pony hasn't drown in the mud first.

> The idea that an HTML element has no semantic meaning in itselfThat's not what I said.  What I said, is they don't have the semantic meaning you're attempted to apply to them.

> XHTML has a Document Type Definition and a schema that the developers of browsers (including Microsoft) have been a part of in developing (the W3C standards).So was HTML 4.1.  Your point?  Advancements in technology are great if they're useful advancements.  At this moment in time, XHTML in any of it's incarnations isn't not a very useful advancement.   It may become one later, it certainly has the potential to do so.  But at this moment, it offers me almost nothing I have over HTML 4.1.  And the few things it does offer me are almost all server-side things that people writing and/or designing HTML won't see or care about anyway, by and large.

Web page designers aren't going to write XSL transforms, for example (you're usually lucky if they know what XSL is) .  They're not going to leverage the ability to embed other namespaces in XSL stylesheet, unless maybe if you're using Wicket or another web framework of that sort.  Even then, the XML property of that isn't the really useful part (though Wicket couldn't function with out it).  I could write declarative commands to my server-side code in my "HTML" document without XHTML.  See ASP.NET for an example of this.

> For you it's just a matter of making it work, but you ignore the foundations of the technology. The DTD and the schema clearly explain the meaning and use of the elements.Sure, from a syntax tree point of view (DTD) and from a validation rules point of view (schema, which includes both syntatical and semantical rules).

But neither have the ability to describe the rules: '<p>' is solely for paragraphs and '<table>' is only for tables.  That's the point.  There's no way to enforce or even describe them to a computer effectively. Such rules operate as nothing more than guidelines.  And the thing about guidelines is that they're not absolute.

> The comment you made that XML doesn't add anything to HTML, shows that you have never worked with or at least learned to appreciate the vast adoption of XML technology in just about every major, widely used, high level programming language I can think of.No, I have.  What it shows is that **you didn't bother to read all of my comment.**

> With tools in PHP5, Python, and C I can take a **valid XHTML page** and traverse it using SimpleXML or DOM tools,(emphasis mine).  Valid XHTML are the operative words.  That's great  if I can ensure the content is actually valid XHTML.  But if I'm writing say, a screenscaper, a spider, a search engine, a CMS that accepts arbitrary content, etc.  I can't safely assume that.  Why?  Because XHTML is a **subset** of all the HTML pages out there.

>  very easily without having to resort to regular expression madness.But you wouldn't have to do that anyway.  HTML is SGML, and SGML parsers exist for all those major languages (usually HTML-specialized ones exist too).  And modifying them to handle the few XML incompatablities with SGML would not be difficult, if it has not already been done.  You're excluding a rather wide middle.  Do you think we never did document transforms before XML?  Yes, we did.  There's multiple languages to describe how to do SGML -> whatever transforms (i.e., rough XSL-FO equivalents).  There's multiple tools to do it programatically, if you don't want to take that approach.  XHTML is not a god-send here, *per se*.  It's certainly not the "killer feature" to make everyone convert all their HTML 4.1 stuff to valid XHTML. 

If I'm building a whole new site up and need to be able to do transforms on my markup?  Yes, it's great.  But that's a pitfully small class of problems, and those problems can (or easily could) be solved with the tools to solve larger classes of problems anyway.

> Overall, you are wrong on just about all accounts. You seem to be against the w3c standards for no good reason other than it does not suit your own purposes.No, I'm against them because they're by and large crap, they're slowly developed, they're clearly poorly written, and they do as much to hinder the progress of web development (because people insist on rapt adherence to poor standards before making any forward progress, which kills developer time) as they do help them.

Standards are great when they are good standards.  CSS, as drafted, is a terrible standard.

> Completely blind people and others with visual impairment were not left out of when HTML was designed, however your approach completely ignores them.No, it does not.  There screen reader must be ready to deal with tables.  More importantly, because tables were the only way to achieve these effect before and pages are still in widespread use that do that, the reader must be capable of handling tables solely for layout.  You've again, excluded the rather large middle.  

Using one table for layout isn't going to break a screen reader, unless the reader is that poor.  In which case it probably has such a hard time with a modern webbrowser it doesn't matter anyway.

Ultimately, screen readers and other devices likely need specialized content to best serve the user anyway.  A table is a great visual presentation device, but a terrible aural one.  So is any and all excessive detail.  So are "columns", for example.  There's no way to easily encode that a <div> is a sidebar to an audio reader: that the content may be relevant but shouldn't be spoken first, for example.  If we could put it closest to the relevant content, then that would be probably best, but even that's not ideal (they may not be interested at all, but we can't know ahead of time).  But putting it closest to the relevant content may not be possible (it could fall in the middle of a paragraph, and <div> can't nest in <p>) and like it or not, the ordering of tags still has a significant impact of the rendering of content (HTML structure and rendered layout are not fully indepedent).

So no, I don't buy that argument anyway.  Accessibility is still a solvable problem, when it needs to be considered.

> It completely ignores other software that accesses data on the internet,No, it does not.  They have to be prepared to handle all valid markup, that includes <table> tags.  <div> doesn't tell them anything more or less about the content anyway.  It never did, it never will.  Even if it could have, it certainly will not now, so the point is moot.

Like I pointed out, very little software out there is actually interested in:[list][*]The semantical meaning, be it explict or implied, by any markup[*]The markup itself, generally[/list]They care about the actual data, and have other means for identifying it.

> it completely ignores the enourmous amount of effort that information professionals, engineers, various organizations, governments, and corporations are putting into making the internet more usuable, making it easier to find information, making it better.Well, if your definition of "more usable" is the CSS 2.1 standard, then they're doing a crap job of it.  If your defintion of "more usable" is XHTML, then I think it hasn't really seen the light of day yet.

CSS 3.0 will be better, hopefully.  At least they're smart enough to recogonize when they've screwed up and right their wrongs.  Just like Sun is with J2EE 5.0, finally (well, the best Sun can manage, anyway).

> Your attitude is a detriment to your customers, and unfortunately they don't know better.My attitude of using the easiest, quickest, cheapeest solution that meets all of the requirements of the job?  Quite the contrary, that's what I get paid for.  That's what they drill into you at engineering school.  That's what all customer wants, in fact (well really, they want all that and a pony, but I don't deal with horses much).

> Your attitude is also selfish and unprofessional.Excuse me?  I'm not the one accusing people of things they plainly did not do.  I'm not the one making personal attacks.  I'm not the one attempting to pass off their arbitrary view of how to approach all jobs (always a fatal mistake) as gospel and being the only right way to do something.  

Your horse has sunk so far in the mud it has drown to death, I think.

> ..and honestly, why are you even using FOSS softwareBecause it serves my needs and frequently my customer's needs? But I don't see how that's relevant.

>  or spend time on this forum?Because I enjoy helping people with technical problems and I enjoy large parts of that the Ubuntu developers are doing?

>   You obviously do not believe in or care about Ubuntu's message.No, I don't believe in much of Ubuntu's message.  But that doesn't mean I don't care about it, at least some of the concepts are noble, if nothing else.  Certainly, those who believe in it are free to persue it, and I could think of far worse things, like debian-legal.

> You certainly haven't picked up on the friendlyness of the community.There's a difference between being friendly and not willing to stand up for what one believes.  Many people here seem to believe the first requires not doing the second, and I refuse to accept that.  I'm more than friendly (ask virtually anyone who's private messaged me ever, or sent me an email).

Oh, I'm not friendly because I tell people they've said something crazy when they have?  :rolleyes:  Well, I'm sorry about that.  I don't mean to offend anyone.  But no one will learn nothing if you don't point out when you think someone is wrong (or know it, in those situations where you can know).  But lots of people don't seem to like that.  It's only a big deal if you choose to make it one.

I'll admit that there's some social issues here: I don't view calling someone dumb, or stupid, or crazy, or a bunch of other things as negative.  I don't even notice them.  I call myself all of those things probably a thousand times a day, so I don't think about them being potentially derogatory when saying them to someone else.

But, if you'd (or whomever) simply say, "I didn't like that you called me crazy," you'd find I'd apologize and do my best to not say it towards you again.  But, most people can't be bothered to do that anymore, it seems.  Much eaiser to attack someone and accuse them of being cruel, unfriendly and uncaring then say, "I didn't like this, could you try to not to do this in the future."

Seriously, you'd find I'm a radically different person if you didn't respond to me the way you choose to.  If you have a personal issue with me, take it up personally (that means PM or email, I could care less) and we'll discuss it.  But if you post publically and accuse me of anything, you will raise my fustration level to the top pretty quickly.

---

### Post by v8YKxgHe on 2006-06-26
Dude, chill out! geee ](*,)

The W3C Standards are there for a reason, and there are no other standards - so why be ignorant and not use them? Keeping to the standards means: your site will load faster, higher search page ranking because your code is valid ( Spiders like valid code ), easier to fix errors, more people can use it and see it on different devices etc etc.

---

### Post by oldmanstan on 2006-06-26
i really don't mean to pour gasoline on a fire but i have a question... i understand that standards are important in many cases and that the internet functions best when information is arranged in such a way as to be accessible

BUT, what about my point that the more complex all this gets the less ACCESSIBLE it gets for small (read: nonprofessional) designers like myself who just want to make their own personal web site (which is what i am doing and why i asked the original question)?

i consider myself pretty tech saavy considering i am not an engineer and do not work in the industry. i pick up on stuff pretty quick and have ever since i was a kid playing with my dad's commodore. but even i have trouble keeping up on what i'm supposed to "do" to make my site acceptable as far as standards and whatnot.

i mean, is it going to come to a point where it's going to be almost impossible to "do it yourself" without being a pro? because THAT would be an internet i wouldn't want to be involved in at all

i say the simpler the better so that truly ANYONE can get involved. of course, if it's too simple then it can't be powerful, i dunno.

EDIT: I read the link from a couple posts ago and it makes some good points on why to use CSS and XHTML but every single point is irrelevant for anything but high-traffic corporate sites, I made it pretty clear I think that I was doing a small personal site... also, I think it's funny that no one mentions the fact that you can use CSS to affect the visual appearance of a page laid out with tables... before I knew <div> tags existed I used to use CSS applied to the cells to setup the visual appearance (this would seem to pretty much negate the "bandwidth ain't free argument" and also makes the use of spacer gifs pretty much unnecessary), not quite as flexible but it still worked well and made it easier to alter the pages and maintain consistency. Also if you scroll down to the part with the guy with the wrench the page points out that tables are still acceptable and alludes to the fact that they are actually more compatible with older browsers :)

ALSO: scroll down to the part about "things tables do better than CSS", MY EXACT QUESTION is answered on this page, they talk about how to do exactly what i want to do and conclude that it cannot be effectively done with XHTML/CSS, interesting

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=AlexC_]The W3C Standards are there for a reason, and there are no other standards - so why be ignorant and not use them?[/quote]Who says I don't?  What I'm not advocating is blind, strict adherence to the standards.  Especially a standard as poor as CSS2.  Saying, "Well there's nothing else" is a non-sequitur.

>  Keeping to the standards means: your site will load faster,You've failed to prove that.

>  higher search page ranking because your code is valid ( Spiders like valid code ),While true, it may or may not make a difference for ranking.  It depends on how many sites are like yours.

>  easier to fix errors,You've failed to prove that, just like any other of your claims.  Provide proof that it clearly does even in most circumstances.

And I owe s|k an apology.  He was not the first to bring the discussion up, but the second.

---

### Post by v8YKxgHe on 2006-06-26
> You've failed to prove that.
> You've failed to prove that, just like any other of your claims.
Then try it for your self, geee. 

I've just got back from work as a Web Dev, and I had to use someone's XHTML template and modify it to how we wanted it. Guess what, they were using Tables with inline styles that was non compliant W3C code. It was a right b**** to go through all of those <table><tr><td> tags, espically since the author was carless about indentation. 

If he had used <div> tags with a CSS file, my life would of been much much easier. THAT is why DIV's are so much better than tables. 

Go and do some tests for your self, see which is faster and easier - you will find that 2 <div></div> tags are easier than a min of 6 <table>........</table> tags

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=AlexC_]Then try it for your self, geee.[/quote]Which still isn't proof.  I'm not interested in a few ancetodal cases.  I want hard, statistically valid number or a logical proof.

> Guess what, they were using Tables with inline styles that was non compliant W3C code.Tables are allowed to have inline styles, that's not non-compliant.  I don't think you know what that word means.

> If he had used <div> tags with a CSS file, my life would of been much much easier. THAT is why DIV's are so much better than tables. Maybe it would have.  Maybe it wouldn't have.  The problem is you can't say it would be eaiser for every job.

[qute]Go and do some tests for your self, see which is faster and easier - you will find that 2 <div></div> tags are easier than a min of 6 <table>........</table> tags[/QUOTE]Perhaps.  But I didn't advocate 6 tables.  Hell, I didn't even advocate **any** nesting of tables.

So stop trying to suggest things that aren't even relevant.  I'm not advocating replacing divs with multi-layer nested tables.  I never did.  I never would.  What I am pointing out is simply that CSS is inadequate for some layouts and using a single table for layout is perfectly acceptable in those cases.  There's no reason why it isn't.

---

### Post by v8YKxgHe on 2006-06-26
> Which still isn't proof. I'm not interested in a few ancetodal cases. I want hard, statistically valid number or a logical proof.


Then what is Proof, to you? Me saying that it's better isn't proof, you trying it for your self isn't proof, What more do you want?! 

> tables are allowed to have inline styles, that's not non-compliant. I don't think you know what that word means.
I know tables are allowed inline styles and that they are compliant. I was refering to the code as a whole was not complaint.

> Perhaps. But I didn't advocate 6 tables. Hell, I didn't even advocate any nesting of tables.
I didn't say 6 tables did I? No. For 1 table you need a minimun of 6 _***tags***_ <table><tr><td></td></tr></table>

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=AlexC_]Then what is Proof, to you?[/quote]Valid statisical evidence or  a logical proof.  Please read what I wrote and don't make me repeat myself agian.

> I didn't say 6 tables did I? No.You said <table> tags.  That's difference from saying, the smallest table requires at least 6 tags.  You need to be more clear.  And that's not a valid argument. Number of tags, if structured, isn't a problem *per se*.

---

### Post by v8YKxgHe on 2006-06-26
> Valid statisical evidence or a logical proof. Please read what I wrote and don't make me repeat myself agian.

Just do some your self ,or find some your self if you want them that much. 

> You said <table> tags. That's difference from saying, the smallest table requires at least 6 tags. You need to be more clear. 

I said "<table>.......</table>", with a bit of common sense you should know that you need the <tr><td></td></tr> tags to go with it, and because it's so long to type out I just did dots. 

> And that's not a valid argument. Number of tags, if structured, isn't a problem per se.

Less tags = less mess, more tags = more tag soup. 

I seriosuly would love to know your definition of Valid and Proof.

Edit: last time i'm posting in this thread.

---

### Post by s|k on 2006-06-26
Personally, I think that calling someone one who with good faith was contributing to the discussion crazy is a personal attack, but that's just me. LordHunter you obviously have experience working in this field and have really intersting things to say, but I disagree with your attitude. We probably represent two different extremes of the spectrum (I am a librarian/developer who works with the Dublin Core and XML) and that explains our contention. I think the W3C is doing amazing work, but I'm not advocating standardization with blind faith. As a librarian making any sense out of the web is impossible without good metadata, without valid HTML/XHTML, without standardization. The benefits of centuries of librarian work when it comes to organizing information is lost out on the web. And as a librarian who has experience working with accessibility tools for disabled, the HTML on websites as they are now are terrible.

---

### Post by LordHunter317 on 2006-06-26
[QUOTE=AlexC_]Just do some your self ,or find some your self if you want them that much. [/quote]The burden of proof is on you, not me.  

> I said "<table>.......</table>", with a bit of common sense you should know that you need the <tr><td></td></tr> tags to go with it, and because it's so long to type out I just did dots. Since most people are rallying against nested tables, no that is not immediately obvious.

> Less tags = less mess, more tags = more tag soup. No, tag soup is not defined based on quantity, just like spahgetti code is not.  Sorry.

---

### Post by s|k on 2006-06-26
[QUOTE=LordHunter317]No, tag soup is not defined based on quantity, just like spahgetti code is not.  Sorry.[/QUOTE]I think simplicity is better than complexity whenever possible, but I agree a document's structure shouldn't be designed based on the number elements you want to use.

---

### Post by oldmanstan on 2006-06-26
[QUOTE=AlexC_]Guess what, they were using Tables with inline styles that was non compliant W3C code.[/QUOTE]

> If he had used <div> tags with a CSS file, my life would of been much much easier. THAT is why DIV's are so much better than tables.

But what if he had used tables with a separate style sheet? then it wouldn't have been much harder to edit than with the div tags, and as for the indenting, any file can be poorly indented, including one written with div tags and in fact even a CSS file can be poorly indented. so really, this guy was just a crappy coder and if he'd used div tags it might still have been a pain for you since you would have had 2 poorly indented files to work with instead of just one

---

### Post by Stromham on 2006-06-26
/offtopic
@LordHunter317 you seem to like to attack peoples opions and views, im not trying to boss you around or anything nor make you mad, i just ask that you slow down on the "fighting" before you make people mad and they quit :P knowing your a vet i wouldnt try to argue with you. please dont flame or "yell" at me for my views, snd opinions, i just will not respond to that. (just telling ya)

/ontopic
so people i have a good one for you guys, have you tried mixing the two? divs and tables, abiet tables can get quite messy and divs are cleaner (less tags) but it depends on the programmer and their use of indentation. having used tables for a good 3-4 years they have become a pain to me, with divs i can make a good website in a night and i have more control, plus when a picture is too big or words run over it will not break my site (provided its coded properly) or stretch our images, take a look at templates now n' days the new ones are made with css and seem to have a better more cleans and polished feel. 
(now these our my opinions/views)

---

### Post by oldmanstan on 2006-06-26
see, i agree with stromham. since i've started using them i have really liked some of the things you can do with divs, but as the web site referenced earlier mentioned, some things just cannot be done with divs and you have to go back to tables (at least for now, maybe in the future features will be added to the standards).

---

### Post by Stromham on 2006-06-26
also  you can make the first true rounded corners with them, and you dont need images like html.

---

