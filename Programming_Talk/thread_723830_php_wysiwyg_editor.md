---
title: "php wysiwyg editor"
date: 2008-03-13
forum: Programming Talk
---

### Post by oneadvent on 2008-03-13
I am looking for what the title suggests for my website. It would  be nice to have an interface only as good as Kompozer. (Not much, just the abilty to see what I am doing)

Anyway, the only post I saw about this recommended Kompozer, but it does not support PHP.

Does anyone know something I dont? (something useful)

Thanks in advance.

---

### Post by LaRoza on 2008-03-14
PHP is for logic, not design. How would a WYSIWYG editor be useful for PHP?

---

### Post by bmeyer on 2008-03-14
Are you looking for an IDE (development environment) to speed up your PHP development?  I know Eclipse has a PHP plugin from Zend, but I think you have to pay for it.  I seem to remember several free PHP IDEs and frameworks that could help you out as well -- I'll have to find the names of them again.

Can't beat a text editor and php.net though ;)

---

### Post by mjamesd on 2008-03-14
If you're looking for an editor to place in a webpage, I usually use [FCKeditor]("http://www.fckeditor.net/"). It's a rich-text editor that integrates well into any website. It requires JavaScript and [jQuery]("http://jquery.com/") to work. It replaces &lt;textarea&gt; elements with the text editor.

---

### Post by oneadvent on 2008-03-14
Well HTML editors allow for you to place images, why cant a good HTML WYSIWYG support PHP? You could then build php pages with HTML in them and see what is happening. 

It could have an area to ask what the unknown variables are. It could fix many a logical error. Right now I change the php and refresh the page, so its kinda like a WYSIWYG built in.

---

### Post by LaRoza on 2008-03-14
> **oneadvent said:**
> Well HTML editors allow for you to place images, why cant a good HTML WYSIWYG support PHP? You could then build php pages with HTML in them and see what is happening. 

It could have an area to ask what the unknown variables are. It could fix many a logical error. Right now I change the php and refresh the page, so its kinda like a WYSIWYG built in.

I really don't understand.

---

### Post by Can+~ on 2008-03-14
I guess you want to see something like a real preview of the php file on execution with all the colors/bold/etc.

You should start with an html file with all the proper styling and later, adding the php sections.

I have apache2 installed with php and mysql running on my desktop, it allows me to see the progress of php sites even with different OSes and navigators on the network, I know this is not what you want, but it's pretty close.

---

### Post by oneadvent on 2008-03-14
exactly except with one ui like kompozer.

the HTML idea is a good one, but then when I want to add forms in php it gets....trying....

You know a plugin for PHP for Kompozer would be perfect. Hummm...well I guess I am getting the job done now, it would just be nice to have something like Dreamweaver for Linux

---

### Post by kellemes on 2008-03-14
> **oneadvent said:**
> it would just be nice to have something like Dreamweaver for Linux

Yes, that's it.. I knew this was coming.
Dreamweaver shows you can indeed WYSIWYG-design using php, and for designers feeling at home in DW there is just no alternative..
Trust me.. you're not going to get a lot of understanding in the tux-world I'm afraid. ;-)
If you're most productive using Dreamweaver, go dual-boot or setup a Windows-machine.

---

### Post by mssever on 2008-03-14
I've never used Dreamweaver, but it sounds like you want some sort of dynamic code generator/debugger. Probably, the Linux programmers who are good enough to write something like that are also good enough to be using some language other than PHP, and wouldn't be interested in fighting PHP's poor design decisions to make a program they'd never use.

Besides, if you structure your PHP code properly, you can abstract away most of the tedious bits. For example, when I'm forced to write PHP, I generally use the [Code Igniter]("http://codeigniter.com/") framework, which tames the beast quite a bit--especially forms.

---

### Post by Can+~ on 2008-03-14
If it's of any help, I have dreamweaver 8 on Wine and it runs great, a bit laggy when switching tabs, but great overall.

---

### Post by Netom on 2009-09-21
People who don't like WYSIWYG should let stop questioning programmers that are looking for this alternative. After all Linux and Ubuntu is about freedom of choice.

In some cases I've found that doing things in a WYSIWYG app is many times faster than the text editors way (try adding a column to a table with one click, or dragging an entire form to place it in another part of the program). PHP is not only for logic (as someone said in this forum) is also about constructing dynamic interfaces: forms, tables, layouts, etc. So we should have an alternative for Dreamweaver in the open source world.

If some programmers want to write their entire code in gEdit or vi or ed, that's fine, but stop preventing others to find their ways to be more productive.

---

### Post by oneadvent on 2009-09-28
for all those out there that are surely subscribed to this thread:

I found Aptana Studios which is based off eclipse. It has a great plugin for php and a wysiwyg ability. It is as close to dreamweaver as i have found.

I couldn't get dreamweaver to work btw because I dont have a windows pc to make it work with.

GL!

---

### Post by frankos44 on 2009-12-20
You should separate your php logic from your web design and keep your project well structured. Most projects evolve into something larger. From my experience its best to lean how to do things PROPERLY yourself and make sure that the client receives 100% compliant markup. If not you will pay the price later. I highly recommend using [www.ffwframework.com](www.ffwframework.com) and forget about wysiwyg and use web developer with mozilla when testing.

---

### Post by makoshark55 on 2010-01-09
NuSphere PhpEd works real good in _wine_ and it cost alot less the Zend software I found they have a linux version but it is way out of date.

---

### Post by hessiess on 2010-01-09
ALWAYS use an MVC framework with PHP and keep the HTML separate using templates.

---

### Post by brainbugg on 2010-03-17
> **LaRoza said:**
> PHP is for logic, not design. How would a WYSIWYG editor be useful for PHP?

Yes, I agree PHP is for logic, not for design. But what he means is the functionality in the program to edit .php files. Merely an HTML editor WILL NOT be able to edit files with .php extension, will they?

---

### Post by Xyro on 2010-03-17
Why not? They are both just text files. Displaying the output of the php script like it does the output of the html tags? No.

Does Dreamweaver have a PHP compiler built into it? This would be news to me.

Edit: Oh, n/m this thread is two months old... :S

---

### Post by sdaau on 2010-04-27
Hi all, 

> **Can+~ said:**
> I guess you want to see something like a real preview of the php file on execution with all the colors/bold/etc.


> **oneadvent said:**
> Well HTML editors allow for you to place images, why cant a good HTML WYSIWYG support PHP? You could then build php pages with HTML in them and see what is happening. 


> **mssever said:**
> I've never used Dreamweaver, but it sounds like you want some sort of dynamic code generator/debugger.

> **Xyro said:**
> Why not? They are both just text files. Displaying  the output of the php script like it does the output of the html tags?  No.

Does Dreamweaver have a PHP compiler built into it? This would be news  to me.


As far as I can remember about Dreamweaver back in the days, all it would do is replace PHP tags with an icon in its preview window, and otherwise ignore php code - say you have the following code:
```

<HTML>
<BODY>
<H1>test heading</H1>

<P> Here some test text </P>
<P> <?php echo "Here some test text by php"; ?> </P>
</BODY>
<HTML>

```If you opened it in Dreamweaver, in the live preview, everything between the <?php .. ?> tags would have simply been replaced with an icon... Which meant that for at least some applications in could have been useful - you could have, say, designed forms in the preview window, while keeping the php untouched.. Which pretty much helps with some tasks like this:

> **Netom said:**
> In some cases I've found that doing things in a WYSIWYG app is many times faster than the text editors way (try adding a column to a table with one click, or dragging an entire form to place it in another part of the program). ...


but not really for debugging and/or live php preview ( maybe there was a way to set it up, I don't know - haven't been working with Dreamweaver for a while )

But in any case - just this 'icon' preview was immensely helpful, as I didn't need to bother typing HTML forms from scratch (which I find tedious)


> **oneadvent said:**
> I found Aptana Studios which is based off eclipse. It has a great plugin for php and a wysiwyg ability. It is as close to dreamweaver as i have found.


Great, thanks - downloading it now; it seems kinda big (just the php development tools require some 80 MB of dependencies for download, it seems) ... 

All I'm looking for is some sort of iconified preview for the php code mixed with html code, so I can more easily design a form, not really debug functionalities - so I hope it has that :) 

Cheers!

EDIT: Just tried aptana - and first you need to install PDT (Php development tools); then you need to do what is recommended in [Setting your HTML preview preferences - Aptana]("http://docs.aptana.com/docs/index.php/Setting_your_HTML_preview_preferences#Accessing_your_HTML_preview_preferences") but for php - meaning that first you have to manually add *.php as extension in Preferences/Aptana/Editors/HTML (in File Associations); then add Aptana HTML Editor and Internal Web Browser as "associated editors" for *.php extension - and then finally a code like above in a *.php file will be treated as a HTML file - unfortunately, the preview will not ignore the <?php ?> tags as I hoped - instead it will output them verbatim :(

EDIT2: here is more [Aptana Forums &#8226; View topic - How to preview PHP? I can preview HTML](http://forums.aptana.com/viewtopic.php?t=4654) but it seems when they talk of "Aptana PHP" that is no longer active:
[quote="http://www.aptana.org/php"]
Aptana PHP is no longer included in Aptana Studio 2.0, and only PDT will be supported going forward. Developers who wish to continue using Aptana PHP may continue using Aptana Studio 1.5.x for as long as they wish. 
[/quote] 
Not easy to get a grasp on this one :)

---

### Post by Dolinko. on 2010-04-30
> **LaRoza said:**
> PHP is for logic, not design. How would a WYSIWYG editor be useful for PHP?
Because, you sometimes with this logic put in a picture, or somtehing like that(maybe an ad), that you need to see, for alignment reasons. Just my actual problem, nothing else...

---

### Post by Enk on 2010-04-30
This is no good solution imo. 

You should seperate your logic from the markup as strict as possible.

You should design the webpage in pure XHTML/CSS first, and when you're done add the logic and test it on a (local) server.

If you just want a picture/add then you definetly shouldn't start mixing PHP in before you have aligned the images.

I've never really understood the need for WYSIWYG-editors. CTRL-TAB + F5 is fast and you can be 100% sure it will render correctly (in that browser).

---

### Post by fawasp on 2010-06-06
Newest version of Kompozer version 0.8b1 build 2009-05-02 already able to open the php file :)

---

### Post by spc456 on 2010-12-08
> **mjamesd said:**
> If you're looking for an editor to place in a webpage, I usually use [FCKeditor]("http://www.fckeditor.net/"). It's a rich-text editor that integrates well into any website. It requires JavaScript and [jQuery]("http://jquery.com/") to work. It replaces &lt;textarea&gt; elements with the text editor.

Hello mjamesd.

It has been a long time that you posted this reply, however, how do you implement FCKeditor?
I have an appache2 server running on my Ubuntu 10.04 desktop and php5, mysql etc. 
I installed CKeditor (new name for FCKeditor) and all I see is text and not the editor that I see on the CKEditor demo.

I would appreciate if you can guide me to get it running.

Thank you,

Mark

---

