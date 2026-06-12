---
title: "HTML standardizing look"
date: 2008-04-19
forum: Programming Talk
---

### Post by Sugz on 2008-04-19
Ok, i feel embarassed asking this but here it goes.
As my websites get bigger i find myself experimenting and making changes to the HTML on one page (usually to a menu hyperlinks or something) and that means that i need to go through about  a dozen more pages making the same changes.

I am familiar with CSS and the concepts behind it, but is there a way to for exaple make the website header, and main menu HTML inside file or something and refer to it in the HTML document.

So that way all i need to do is make changes to one HTML document the affect the global properties or all other HTML documents that refer to this file?

Many thanks 

-Sugz

---

### Post by zJerrik on 2008-04-19
> **Sugz said:**
> Ok, i feel embarassed asking this but here it goes.
As my websites get bigger i find myself experimenting and making changes to the HTML on one page (usually to a menu hyperlinks or something) and that means that i need to go through about  a dozen more pages making the same changes.

I am familiar with CSS and the concepts behind it, but is there a way to for exaple make the website header, and main menu HTML inside file or something and refer to it in the HTML document.

So that way all i need to do is make changes to one HTML document the affect the global properties or all other HTML documents that refer to this file?

Many thanks 

-Sugz

Are you willing to use, and is your webserver enabled with PHP? One standard I find is (I don't web code myself) is that developers will create a single file with two functions. Header() and Footer(). In each html/php page they make a call to Header() at the beggining and Footer() at the end. These contain the html information like metadata, standard CSS includes, etc. 

If you want some a coded example I can make you one =)

---

### Post by soapytheclown on 2008-04-19
you can use php and create a header page and a footer page then for each content page have and include statement like

<?php include ('/header.html'); ?> //css and js links in here as normal
           #
           #your normal xhtml content here
           #
<?php include ('/footer.php'); ?>

what that will do is put out the included content in the order of the includes as if those 'included pages' were part of the 'content' file..
otherwise a slightly more advanced way is using ajax but there are issues with the back button etc.. i use the mootools framwork ([www.mootools.net](www.mootools.net)) for my ajax apps

hope that makes sense its late here :)

-edit-

zJerrik you beat me to it!!

---

### Post by Sugz on 2008-04-19
Unfortunatly my server is NOTphp enabled, 
this is a piece of coursework if you must know, and the markers server is not PHP enabled. 
This is tricky, but surely it is as fundermental as using CSS?

Just ready your post again
haha i can sympathise, its later here in the UK, im going to bed soon i was hoping to have a answer to help me sleep heh :)

---

### Post by soapytheclown on 2008-04-19
without you having any server side control i could only recomend the ajax option since its done with Javascript it doesnt require any server side access to implement

edit

btw im from the UK too!

---

### Post by LaRoza on 2008-04-19
Just use a CSS stylesheet and link to it, that would be the easy way.

See my website (the Learn to Program link), look at the markup, there are no styles declared anywhere in the markup. A single stylesheet is used for every page.

---

### Post by ad_267 on 2008-04-19
If you need to change the actual html content, not just the appearance then you could make it easier by using a script or an editor that lets you search through files and find and replace specific text. I've used that before for static html websites but I used notepad++ in windows, I don't know the best way to do this in Linux yet but I'm sure there are plenty of ways.

---

### Post by soapytheclown on 2008-04-19
edit -opps-

---

### Post by Sugz on 2008-04-19
Ok, last post for the night
I have a Banner containing a logo and a menu. Im in the process of adding dropdown menus and its proving annoying to keep on adding the same code again again and again to all 12 - 20 pages of my website.
Its difficult to track changes.

Im not looking for a style sheet, thats fine im familair with that, im talking about HTML, importing HTML code from an external file and inserting it into a certain point.

I could use javascript, but it seems to act up when using str+= method to insert Function parameters. 

Anyway, im off Cya all many thanks for your support!

---

### Post by LaRoza on 2008-04-19
> **Sugz said:**
> Ok, last post for the night
I have a Banner containing a logo and a menu. Im in the process of adding dropdown menus and its proving annoying to keep on adding the same code again again and again to all 12 - 20 pages of my website.
Its difficult to track changes.

Im not looking for a style sheet, thats fine im familair with that, im talking about HTML, importing HTML code from an external file and inserting it into a certain point.

I could use javascript, but it seems to act up when using str+= method to insert Function parameters. 

Anyway, im off Cya all many thanks for your support!

You want a server side include. Perhaps this server being used has some way of doing this?

---

### Post by ad_267 on 2008-04-19
He's already stated that he can't use php.

I think a simple bash script would be easiest.
You could add a comment above the menu like <!--beginmenu--> and below the menu have <!--endmenu--> and put your menu in a separate file and use something like sed to open all of your html files and replace everything between those two comments with the contents of your menu file. Someone else could probably give you an example of a bash script to do this but my knowledge of bash isn't that good sorry.

---

### Post by soapytheclown on 2008-04-19
..create a main body for his site with all his static data... menus headers footers and then  use ajax to update a single "content" div...
again the main issue is with the back button but if its coursework in your writeup you would always mention that as a problem and mention implemeneting something like RSH - real simple history (i tihnk its called that) or i believe theres a jQuery plugin which tracks a users history in ajax.

but for simple ajax i definatley recommend mootools =D

---

### Post by elithrar on 2008-04-22
> **ad_267 said:**
> He's already stated that he can't use php.


I think there's a point being missed - he can't use a server-side language on his **marker's** machine, but what's stopping him from getting a quick LAMP install running (or a quick Django install!) and using templates on **his** development machine.

Use [FONT="Lucida Console"]{% include %}, {% extends %} or {% variablename %}[/FONT] tags (or the equivalent in PHP) to generate the final HTML files - then just grab the source once you're 'done' with the assignment - that way you can have completely uniform markup/headers/footers without having to trawl through pages and manually change things.

Frameworks can be wonderful things sometimes - the only problem with this solution is that you'll have to obviously spend a little time learning the language/framework, but there's plenty of information available for both - and templating in Django is very easy.

---

### Post by RIchard James13 on 2008-04-23
Does HTML have no ability at all to include code from another document? Other than CSS style sheets and javascript.

---

### Post by elithrar on 2008-04-23
> **RIchard James13 said:**
> Does HTML have no ability at all to include code from another document? Other than CSS style sheets and javascript.

Unfortunately not; HTML cannot 'include' code from base templates or other files by itself.

---

### Post by Wim Sturkenboom on 2008-04-23
Have a look at the iframe tag
[http://www.htmlhelp.com/reference/html40/special/iframe.html](http://www.htmlhelp.com/reference/html40/special/iframe.html)

I have never used it but as far as I understand it, it can be used as a 'kind' of include'

---

