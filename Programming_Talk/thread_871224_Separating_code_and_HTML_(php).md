---
title: "Separating code and HTML (php)"
date: 2008-07-26
forum: Programming Talk
---

### Post by Melindrea on 2008-07-26
Coming from a background in C# (and also C++ and Java, but that's not quite the same thing =), I'm going back to working in PHP a bit, so that I'm more secure with it.

However, here's my question: What is the best way to separate code and content? Use a bunch of requires, with one or two functions in each, or classes, or a large file with all the functions I'm going to be calling? 

I very vaguely recall (from my asp days) that you should avoid the start and end tags of server-side languages since the files get big and such... Is this still true? (we're talking vague recollections from 8 or 9 years ago... =)

And, finally... Doing a quick google search included a lot of talk of templates - though there seems to be varied ideas on how useful they are, and for what! What do you think, anything I should look closer into, if I want to keep my HTML and my PHP as separate as possible?

Thank you,
Melindrea

---

### Post by mech7 on 2008-07-26
You should take a look at the MVC Pattern... pretty much all serious PHP Projects make use of it... 

Don't want to build your own... use a framework CakePHP, Symfony, ZendFramework, CodeIgniter, Prado are some good ones :) 

About templates I prefer PHP as a template language... Smarty is being used allot... and it is ok. I use it at work, but it's just another syntax to learn... not much difference between:

<?php foreach($articles as $article): ?>

or 

{foreach from=$articles item=article}

Some prefer it so that designers in your project can scew up php, or claim that php is more difficult to learn as smarty. But it also creates more bloat and more limitations...

About start and end tags, you need start tags with php <?php it is a good habit to forget the closing tag at the end of document of full php files... so there cant be and accident space which would cause errors when sending headers.

---

### Post by slavik on 2008-07-26
I work alongside some web devs that use the MVC approach, but I find that the code becomes something like:

<html tag with stuff <? some php call?> >blah</end tag>

or:

<? if (cond_true) { ?>
some html code here
<? } ?>

which I find weird ...

---

### Post by LoneWolfJack on 2008-07-26
Smarty is always a good start: [http://www.smarty.net]("http://www.smarty.net")

Personally I don't use it as I think that if I am separating php and html, then for the reason that I want a HTML programmer be able to pick up where I left without having to know PHP. With smarty, he has to know smarty programming...

Other then that, consider building your own template system. Don't let yourself be intimidated by buzzwords like MVC. It's just a collection of rules that should be obvious to anyone who calls himself a professional programmer.

Slavik, what you posted there is so true for like 80% of the PHP programmers out there. It's madness. It was a valid approach 10 years ago, but anyone who does anything like that is an amateur at best.

---

### Post by Melindrea on 2008-07-27
Thanks all! 

I'll check up what MVC is, and I think I'll stay away from smarty for the reason lonewolfjack mentioned. Right now it's just me, but if I end up writing webapplications, I'm fairly certain that means I'm going to be doing PHP/C#/whatever, an someone else is going to be sitting with the actual HTML.

So, I think I'll go with a "functions" require, and if there's so many functions and such I need later, I'll separate them then. 

About my question for the <?php etc, this is pretty much what I was told 8-9 years ago: The tags used in asp (can't even recall what was used then =) were resource heavy or somesuch, so it was "bad coding" to write stuff such as:

<p><?php some code stuff ?></p>
|bunch of HTML
<?php some more code stuff ?>

What is the philosophy nowadays? =)

---

### Post by drubin on 2008-07-27
> **LoneWolfJack said:**
> Smarty is always a good start: [http://www.smarty.net]("http://www.smarty.net")

Personally I don't use it as I think that if I am separating php and html, then for the reason that I want a HTML programmer be able to pick up where I left without having to know PHP. With smarty, he has to know smarty programming...

I would disagree I have only been using smarty for the last few months but it makes sense It makes modifying the look/theme of an applications realy easy with out have to know any of the php back end.

As for knowing smarty programming it is SOO easy that any one that calls them selfs a programmer even if it is just html/css will be able to understand.

[PHP]{if $showOffline}
   {foreach item=row  from=$offlineList}
        {$row}
   {/foreach}
{/if}
[/PHP]

> **LoneWolfJack said:**
> 
Other then that, consider building your own template system. Don't let yourself be intimidated by buzzwords like MVC. It's just a collection of rules that should be obvious to anyone who calls himself a professional programmer.


Ye they aren't that difficult by why re-event the wheel (If there is something out there that suites your needs)

> **LoneWolfJack said:**
> 
Slavik, what you posted there is so true for like 80% of the PHP programmers out there. It's madness. It was a valid approach 10 years ago, but anyone who does anything like that is an amateur at best.

Please explain this statement I don't seem to understand why it is madness? Yes you may call me an amateur which I probably am only been doing php for about a year and a half.

---

### Post by Melindrea on 2008-07-27
> **rubinboy said:**
> Ye they aren't that difficult by why re-event the wheel (If there is something out there that suites your needs)

The best reason to be found: To learn how the spokes work, and what happens if I remove this? =)

---

### Post by mech7 on 2008-07-27
> **rubinboy said:**
> I would disagree I have only been using smarty for the last few months but it makes sense It makes modifying the look/theme of an applications realy easy with out have to know any of the php back end.

As for knowing smarty programming it is SOO easy that any one that calls them selfs a programmer even if it is just html/css will be able to understand.

[PHP]{if $showOffline}
   {foreach item=row  from=$offlineList}
        {$row}
   {/foreach}
{/if}
[/PHP]


:lolflag: How is that any easier to learn then:

[PHP]
</php if($showOffline):?>
 <?php foreach($offlineList as $item):
   <?php echo $item;?>
 <?php endforeach; ?>
<?php endif;?>
[/PHP]

Ok it save a few characters { instead of <?php :P

---

### Post by drubin on 2008-07-27
> **mech7 said:**
> :lolflag: How is that any easier to learn then:
Ok it save a few characters { instead of <?php :P

My main point was that it wasn;'t hard either way, But it nicer to separate your php from your html...

---

### Post by drubin on 2008-07-27
> **mech7 said:**
> :lolflag: How is that any easier to learn then:

[PHP]
</php if($showOffline):?>
 <?php foreach($offlineList as $item):
   <?php echo $item;?>
 <?php endforeach; ?>
<?php endif;?>
[/PHP]

Ok it save a few characters { instead of <?php :P

Why that syntax as apposed to with { } braces
[PHP]
<?php if($showOffline){?>
 <?php foreach($offlineList as $item){
   <?php echo $item;?>
 <?php }; ?>
<?php }?>
[/PHP]

---

### Post by mech7 on 2008-07-27
> **rubinboy said:**
> Why that syntax as apposed to with { } braces
[PHP]
<?php if($showOffline){?>
 <?php foreach($offlineList as $item){
   <?php echo $item;?>
 <?php }; ?>
<?php }?>
[/PHP]

The alternative syntax is a little more suited to use between html... with braces is better for full php... 

[http://php.net/alternative_syntax](http://php.net/alternative_syntax)

---

### Post by Reiger on 2008-07-27
Separating HTML and PHP is quite easy when you consider the HTML page as a whole to be merely output of a PHP script...

In fact if you need to... one can always load the HTML from an external file using simple_xml or DOMDocument API's; processing it; and then pass it straight to the browser by echo-ing a formatted XML/HTML string...

Check the PHP Manual.

===

At this point I'm working on a set of PHP scripts which retrieve some XML, transform it into XHTML using XSL and serve the page with a few bells & whistles. The reason for this approach is so that people with (virtually) 0 HTML skills can still actively edit & maintain the site + a more modular approach to the pages. (Remember the bad days of copying over malformed HTML all over the place, just to get a menubar working on every page? :D)

---

### Post by LoneWolfJack on 2008-07-27
> **rubinboy said:**
> I would disagree I have only been using smarty for the last few months but it makes sense It makes modifying the look/theme of an applications realy easy with out have to know any of the php back end.

As for knowing smarty programming it is SOO easy that any one that calls them selfs a programmer even if it is just html/css will be able to understand.


Well, I usually hire a HTML/CSS specialist for this kind of footwork. He's probably one of the best in terms of CSS programming and can do awesome things - but he doesn't know smarty at all - and he doesn't want to.

Also, if I hire someone to do HTML programming, I don't want him messing around with the site's logic - that's my job. If I let him mess around with the logic, I'll have another place to debug.

Then, if you learn smarty programming, you can as well stick with mixing HTML and PHP and hire an amateur PHP programmer.

Lastly, just a couple weeks ago I had a little job that I only did because one of my existing customers asked me to: modifying an open source community project that is using the smarty template engine. The templates were total garbage: for some of the tables there were template files 10kb in size where all the different table headers were present and organized through smarty-if's. - it took ages to even figure out what smarty if-block is used on what occasion.


> **rubinboy said:**
> 
Ye they aren't that difficult by why re-event the wheel (If there is something out there that suites your needs)


Over the years, I've been playing around with all of them... cakePHP, symfony, whatever... wasn't impressed by any of them so for projects we do from scratch, we always stick to our own set of standard classes.

Frameworks are certainly a good tool for amateurs. They even might cut down development time for professionals - but if you want to do things right, you do it all from scratch. Given your customer is willing to sign a huge paycheck, that is.

> **rubinboy said:**
> 
Please explain this statement I don't seem to understand why it is madness? Yes you may call me an amateur which I probably am only been doing php for about a year and a half.

Because it's impossible to debug. You never know where statements begin and where they end. It costs you too much time actually even locating the place an error *could* be located.

And lastly, it even looks amateurish, giving away your lack of experience.

---

### Post by Melindrea on 2008-07-27
> **Reiger said:**
> Remember the bad days of copying over malformed HTML all over the place, just to get a menubar working on every page? :D)

Yeah, I do. =) Now I just use various server-side includes. =) I think that going through XML and such is... slightly more work than what I'm planning on learning right =) So, I think I'll stick with a "functions" file, possibly to be divided into several smaller ones.

Thanks, anyways =)

---

### Post by mech7 on 2008-07-27
> **LoneWolfJack said:**
> Over the years, I've been playing around with all of them... cakePHP, symfony, whatever... wasn't impressed by any of them so for projects we do from scratch, we always stick to our own set of standard classes.

Frameworks are certainly a good tool for amateurs. They even might cut down development time for professionals - but if you want to do things right, you do it all from scratch. Given your customer is willing to sign a huge paycheck, that is.


Omg frameworks are for amateurs? programmers are lazy.. and it's better to do a joined effort then do all on your own... Even Yahoo is building apps with Symfony, and mozilla with Cake... and ZF is generating some buzz too... magento??? These are not projects run by amateurs ;)

If you are doing all from scratch over and over again then there is something wrong with your base code :)

---

### Post by LoneWolfJack on 2008-07-27
Building from scratch was referring to the project. This includes using our own framework (which I refuse to call a framework because frameworks are always in some way limiting you, which our default set of classes doesn't). Don't put things in my typing that aren't there.

As for the big companies using frameworks, this doesn't mean anything. You would be surprised what goes on behind closed doors at even the largest companies.

---

### Post by drubin on 2008-07-27
> **LoneWolfJack said:**
> 
Because it's impossible to debug. You never know where statements begin and where they end. It costs you too much time actually even locating the place an error *could* be located.

And lastly, it even looks amateurish, giving away your lack of experience.

How does a } differ from a ifend;  If code is well designed the syntax of the language makes no difference in my opinion. You still should know that  } denotes an end.

If your codes gets to the stage where by you can't work out where things begin and where they end.... There is something wrong with the way you designed it to start with.

---

### Post by Occasionally Correct on 2008-07-27
This was actually something I had been thinking about a few weeks ago. I designed a very small and trivial "templating" system.

Basically, you keep a "pages" directory where you have an HTML file accompanied by a PHP file of the same name. The job of the PHP file is to do any of the necessary logic stuff and set up an array of data that can be exposed to the HTML file.

The HTML file can use two lumps of syntactic sugar: {{x}}, {{x: y: z ...}} and {{x: 3..9}} are for accessing the data. [[template-name "param1" "param2" ...]] includes a template file, which is just a snippet of reusable HTML (say, the start or end of a content area), where "param1" et cetera replaces symbols in the form of {{0}}, {{1}}, ... {{*n*}} with the quoted contents. And that's all.

My advice to the OP: Just keep it simple. It doesn't have to exceed your needs just so it can fit your needs. Large frameworks aren't always necessary, but (like everything else) it depends on the situation. :)

> Personally I don't use it as I think that if I am separating php and html, then for the reason that I want a HTML programmer be able to pick up where I left without having to know PHP. With smarty, he has to know smarty programming...
This was one of my concerns as well. I didn't want to use Smarty because it was way too complex for my needs. I don't mind introducing new syntax into HTML though: the reason I separate PHP from HTML isn't because I have the greatest hygiene -- it's because I need to debug PHP code, not HTML. (That was my biggest beef with Smarty. It's still introducing logic into the HTML.) :)

---

### Post by pmasiar on 2008-07-28
It's funny how ridiculously bad advice you can get from people who pretend to be pros:
> **LoneWolfJack said:**
> consider building your own template system. Don't let yourself be intimidated by buzzwords like MVC. It's just a collection of rules that should be obvious to anyone who calls himself a professional programmer.

As any pro knows, you **never** start with wasting time on reinventing the wheel. Pros are not "intimidated" by MVC or any other design pattern, but understand them and apply as appropriate to get better, more flexible and maintainable design.

> **LoneWolfJack said:**
> Frameworks are certainly a good tool for amateurs. They even might cut down development time for professionals - but if you want to do things right, you do it all from scratch. Given your customer is willing to sign a huge paycheck, that is.

Pro will never cheat customer by billing for custom solution where generic reusable solution (like existing framework) is good enough.

> Because it's impossible to debug. You never know where statements begin and where they end. It costs you too much time actually even locating the place an error *could* be located

Part of "being the pro" is to know and understand your frameworks, use the appropriate one, and know how to fix tight spots.

Amateur will sell customer custom solution with  many custom bugs, and saddle customer with expensive contract to maintain that homegrown solution, instead of using appropriate industry standard one.

---

### Post by LoneWolfJack on 2008-07-28
> **pmasiar said:**
> It's funny how ridiculously bad advice you can get from people who pretend to be pros:


Yeah, that's so true. And I wish my time here wasn't so limited so I could help you enlighten them more often. :)


> **pmasiar said:**
> 
As any pro knows, you **never** start with wasting time on reinventing the wheel. Pros are not "intimidated" by MVC or any other design pattern, but understand them and apply as appropriate to get better, more flexible and maintainable design.


If this already invented wheel is only an approximation of a smooth rolling wheel, then this may be good enough for you or Joe Average, but it ain't for me. Every time you use an existing wheel you have so much garbage you don't need or that you have to change to your needs that it's rediculous.

> **pmasiar said:**
> 
Pro will never cheat customer by billing for custom solution where generic reusable solution (like existing framework) is good enough.


Perfectly right. And thanks for confirming what I said: that existing frameworks are not necessarily good enough.

> **pmasiar said:**
> 
Part of "being the pro" is to know and understand your frameworks, use the appropriate one, and know how to fix tight spots.


Every time I meet someone who has nothing to offer but customizing a bunch of existing solutions I am pretty sure that he just can't do better.

> **pmasiar said:**
> 
Amateur will sell customer custom solution with  many custom bugs, and saddle customer with expensive contract to maintain that homegrown solution, instead of using appropriate industry standard one.

Short of the fact that we almost never sell maintenance contracts, bugs are fixed any time - for free. If someone bought a custom solution from us five years ago and suddenly comes across a bug, it will be fixed without extra charge. However, this very rarely happens as usually, we contract independent testers to validate any beta release.

---

### Post by pmasiar on 2008-07-29
> **LoneWolfJack said:**
> If this already invented wheel is only an approximation of a smooth rolling wheel, then this may be good enough for you or Joe Average, but it ain't for me. Every time you use an existing wheel you have so much garbage you don't need or that you have to change to your needs that it's rediculous.

I see, you are just one of those rare programmers from Lake Wobegon "where all children are above average", and custom packages have no bugs and beat industry standard solutions every time.

---

### Post by drubin on 2008-07-31
> **pmasiar said:**
> I see, you are just one of those rare programmers from Lake Wobegon "where all children are above average", and custom packages have no bugs and beat industry standard solutions every time.

nicely worded.

---

### Post by LoneWolfJack on 2008-08-02
*shrugs* like I said, I've got too much work right now to make everyone see the point. 

keep using frameworks and keep twisting and bending them to your customer's needs if you're getting away with it.

perhaps some day a customer who intends to contract you for a project worth say 250k will come along, asking you "can't you do something from scratch that totally fits our needs?" and you will reply "sure, but framework xyz is soooo great, it just rocks!", and then the head of IT of your customer will look you straight in the eye and say "ok, but if you twist and bend this framework to our needs, this will mean we will have to hire you every time there's a security update for this framework because we can't any longer apply the patch as-is, right?".

then, your blood will freeze and you may realize the further implications of this question. and if you're lucky, you might also start to understand why custom-built solutions always beat the lot.

---

### Post by pmasiar on 2008-08-02
Funny you mentioning vendor lock-in...  Custom-build solutions **by definition** cannot by maintained by anybody else, and independent security patches would not be a problem either. "Security by obscurity" seems to be preferred way at Lake Wobegon :-)

But I do not care to argue anymore about this issue: every customer can pick the solution, if someone prefers custom "error-free", they are spending own money not mine...

---

### Post by runningwithscissors on 2008-08-03
I don't really like frameworks.

They have their own quirks and a lot of them need to be 'learnt' how to use even for programmers who have experience with the language the framework is written in.

Simple libraries are far better to manage and use. For example, if I were writing some webapp using python, I'd use CherryPy for the HTTP request processing, some template library and maybe sqlalchemy for the db. But I can easily choose to _not_ use any one of the three. Say, I don't really need db abstraction like sqlalchemy provides, I can just as easily drop that and just use MySQLdb.

Not every programme needs to have an MVC architecture or templating or a choice of 3000000 backends.

---

### Post by garak on 2008-09-09
> **runningwithscissors said:**
> I don't really like frameworks.

They have their own quirks and a lot of them need to be 'learnt' how to use even for programmers who have experience with the language the framework is written in.

Simple libraries are far better to manage and use. For example, if I were writing some webapp using python, I'd use CherryPy for the HTTP request processing, some template library and maybe sqlalchemy for the db. But I can easily choose to _not_ use any one of the three. Say, I don't really need db abstraction like sqlalchemy provides, I can just as easily drop that and just use MySQLdb.

Not every programme needs to have an MVC architecture or templating or a choice of 3000000 backends.
So, it's just a matter of decoupling.
You can use a loosely coupled framework like Zend Framework (it's just a collection of classes), or better an highly decoupled framework like Symfony (the best in my opinion), so you can use every feature if you need or just use features you want and forget about the rest

---

### Post by themusicwave on 2008-09-09
I'll admit I am a PHP noob.  The web is not my typical application space, but I am trying to get better.

Anyways, I know that we are not supposed to use mixed HTML and PHP and that you should have your PHP just output totally clean HTML, but I am not always 100% sure how to do this.

On one site I am working on(for free) I have code mixing HTML and PHP.  The only alternative I can think of is to just have the PHP print my HTML page.  But then my fiance who is working on the site who only knows XHTML will be totally lost.  She will lose her ability to edit the page anymore.

It's easy to spout "Use MVC", but I never really seen it done.  Right now I don't want to use a framework because the page is very small and because I want to understand what happens underneath.  I certainly plan to use frameworks in the future, but right now I want to know the basics.  It also isn't my webserver and they don't really offer any frameworks anyway. 

Right now the whole site used about 3 PHP libraries I wrote.  1 of them handles conference registration, another sends e-mails with attachments and a third handles my very basic templating system.

I have one ugly awful page that is the worst offender here is a snippet:

[PHP] 
<?php 
include("pagehandler.php"); 
include("regproc.php"); 

$regHandler = new RegHandler();

if(isset($_POST["submit"])){
	
	$regHandler->readData();
	$dataValid = $regHandler->validateData();

	if($dataValid){
		$regHandler->insertData();	
		
		//Redirect to payment page
		if($_POST["paymenttype"]==1){
			header("location: payreg.php");
		}
		else{
			header("location: mailreg.php");
		}
	}
	
}

?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Conference - Registration</title>
<link href="Styles/styles.css" rel="stylesheet" type="text/css" />


<?php printNavbar(); ?>

  <div id="contentwrap">
    <div id="maincontent">
      <p class="pageheader">Harvest 2008 Registration</p>

	  <p>Please fill out the following information to register.</p>
	  
	  <?php
	  
	  if(!$dataValid && isset($_POST["submit"])){
	  	print("<h2 class=\"error\">Please correct the errors in red below.</h2>");
	  }
	  
	  ?>
	  <form name="register" action="reg.php" method="post">
	  <h2>Personal Information</h2>
	  First Name&nbsp;&nbsp;<input <?php $regHandler->getClassStr("firstname"); ?> type="text" name="firstname" value="<?php $regHandler->getValue("firstname")?>" />&nbsp;&nbsp;
	  Last Name <input <?php $regHandler->getClassStr("lastname"); ?> type="text" name="lastname" value="<?php $regHandler->getValue("lastname")?>"/> 
	  
	  <span <?php $regHandler->getClassStr("gender"); ?> > <br /><br />
	  Gender&nbsp;&nbsp;M<input type="radio" name="gender" value="M" <?php $regHandler->getChecked("gender","M"); ?> />&nbsp;&nbsp;
	  F<input type="radio" name="gender" value="F"  <?php $regHandler->getChecked("gender","F"); ?> /></span>
	  <br />
	  
	  <br />Address&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<input <?php $regHandler->getClassStr("address"); ?> type="text" name="address" size="60" value="<?php $regHandler->getValue("address")?>" /> <br />
	  <br />Address(cont)&nbsp;&nbsp;<input <?php $regHandler->getClassStr("address2"); ?> type="text" name="address2" size="60"  value="<?php $regHandler->getValue("address2")?>" /> <br />
	  <br />City&nbsp;&nbsp;<input <?php $regHandler->getClassStr("city"); ?> type="text" name="city"  value="<?php $regHandler->getValue("city")?>" />&nbsp;&nbsp;
	  State&nbsp;&nbsp;<input <?php $regHandler->getClassStr("state"); ?> type="text" name="state" size="2" maxlength="2"  value="<?php $regHandler->getValue("state")?>" />&nbsp;&nbsp;
	  Zip&nbsp;&nbsp;<input <?php $regHandler->getClassStr("zip"); ?>  type="text" name="zip" size="5" maxlength="5"  value="<?php $regHandler->getValue("zip")?>" />
	  <br /><br />
	  Phone&nbsp;&nbsp;<input <?php $regHandler->getClassStr("phone"); ?> type="text" name="phone"  value="<?php $regHandler->getValue("phone")?>" />
	  <br /><br />
	  E-mail&nbsp;&nbsp;<input <?php $regHandler->getClassStr("email"); ?> type="text" name="email"  value="<?php $regHandler->getValue("email")?>" />&nbsp;&nbsp;
	  Confirm E-mail&nbsp;&nbsp;<input <?php $regHandler->getClassStr("confirmemail"); ?> type="text" name="confirmemail"  value="<?php $regHandler->getValue("confirmemail")?>" />
	  [/PHP]

So what do I do with a mess like that?

---

### Post by garak on 2008-09-09
themusicwave, if you really want to do everything by yourself, you can easily write a little library to hanlde simple template files. You can use a pure XHTML template files, with comments replacing logic and variables (something like <!-- $myvariable --> or <!-- if --> <-- endif -->) and let php replace that comments with "real" php code.
Your will to understand is a good thing. I can advice you to take a look to [TinyMVC](http://tinymvc.org/): it's small, so you can easily dive into its code, but it's still MVC.

---

### Post by themusicwave on 2008-09-09
What I struggle to understand is why riddling my code with HTML comments and then passing it through a script to fill them with code is any better than just using PHP mixed in.

How is having code riddled with <!--Some Function Call--> better than having <?php someFuctionCall;?>?

With this kind of thing I now have even more code to maintain.  Now not only do I need to maintain the actual PHP scripts to process my forms, but I also need a script to parse my pages and to replace <!--X--> with <?php x()?> or the result of x().  It seems like that is even less maintainable.

Is MVC in PHP just using some templating engine to do this sort of thing?  

I really don't know much of anything about it.

I also haven't done anything to elaborate simple because the site is small.  In total it is perhaps 15 pages, and about 3 PHP scripts.  It is only for a conference for this year, so it will not need extended.

---

### Post by garak on 2008-09-09
> **themusicwave said:**
> What I struggle to understand is why riddling my code with HTML comments and then passing it through a script to fill them with code is any better than just using PHP mixed in.

I misunderstood your previous post: I thought you needed a pure XHTML solution.
So, I totally agree with you: it makes more sense to use directly PHP inside XHTML (after all, PHP is born as a parsing language) and many MVC frameworks behave exactly like this (see already mentioned TinyMCE and Symfony)

---

