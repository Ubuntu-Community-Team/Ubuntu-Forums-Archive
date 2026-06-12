---
title: "Will anyone help me create a website's navigation system?"
date: 2007-06-23
forum: Programming Talk
---

### Post by SoloSalsa on 2007-06-23
I have been using html forever.  But I never really made projects larger than four pages.  Now, I am in charge of a 'real' site for the first time, and I am going mad at the simple site layout.  In the past, I put an identical menu in the body of *every* page.  For a real website, that is a bad habit, and bad to manage.  With that model, to add a page, I would need to add a link in *every* other page.  I need to make a menu that can be maintained independently from content pages (not a site map page, rather a navigation list on every page).
I will only use xhtml and css, no html 4.
I have tried using objects, and I think that is the best approach.  But I do not know how to target properly.  I mean, if I have a menu as an object, every link opens a page *in* that tiny menu object.  And, if I make a page with a menu, and the 'content' an object, I do not know how to tell that object to change directory.
Now, I *know* this can be done with a frameset document type (and I know how), but I would rather not get into that.
The page I am in charge of is [here]("http://www.niles-hs.k12.il.us/westFineArts/band/NEWNWBAND/index.htm").  It **horribly** written (I mean, errors, not layout and ease of navigation, because those are good).  It has javascript popping menus, which I eventually would like to make myself.  The last person knew *nothing* of text markup, and made it entirely from Dreamweaver.  I rally can not tell much from the complex (and error-packed) menu script, but I think the menu is hard-coded on *every* page.
It has that header on top, which is why I do not want to use frameset.
So, essentially, I need to make a menu, which can be very basic for now.  In programming, I would make a menu class (and menu.paint (), etcetera), but how do I do this in markup?
Thank you, so much, for offering help.

---

### Post by dempl_dempl on 2007-06-23
I've used PHP for my site. If you don't know PHP , don't worry , neither do I :D.
I've just inserted couple of lines like this into my code:

(let's say hello.html) :

[I]<html>
<head>
</head>
<body>

	<? readfile("up-frame.shtml"); ?>
	<? readfile("left-frame.shtml"); ?>

                   /* Site content goes here */

</body>
</html>[/I]


Note that "left-frame.shtml" and "up-frame.shtml" are NOT complete html files , i.e.  they should not have <html> or <body></body> tags.

When a web browser issues a request for hello.html  , web server will insert them directly into your current file. Something like Copy+Paste.

That means you won't see any results when playing with files at home. You have to copy them to web server first. 

There are other methods to do it without web-server, some Java-script stuff, but who cares, this one works just fine and it looks elegant :) .

Now , couple of notes:

On some servers , if you don't set extension to ".php" , it won't work.
Also , on those servers,  you have to put included files ( like up-frame.shtml )  to have ".shtml" extension. 

Another  thing : 
When writing something like:

*	<? readfile("up-frame.shtml"); ?>*

pay attention to spaces. I.e :

*< ?  [space]  readfile("up-frame.html"   )  ?>*  **  did not worked at my web server.**
Replace [space] with one real space, This forum "eats"  extra spaces in post.

That should do the job.
Cheers!

---

### Post by schallstrom on 2007-06-23
Hi, this is maybe not helping you very much directly, but in my opinion pure markup language like (X)HTML is not adequate for what you want to achieve. I would really suggest to make the effort and learn some script language suitable for web applications like PHP or Ruby (Ruby on Rails). It is really a pain to maintain a web site involving more than 10 pages via pure markup if the content is changing more or less on a regular basis.

---

### Post by SoloSalsa on 2007-06-23
> **schallstrom said:**
> I would really suggest to make the effort and learn some script language suitable for web applications like PHP or Ruby (Ruby on Rails).Or javascript, right?  Most menus use javascript, but I want the site to have basic accessibility.> **schallstrom said:**
> It is really a pain to maintain a web site involving more than 10 pages via pure markup if the content is changing more or less on a regular basis.But, this would work just fine using <frame>s.  This is what I had in mind.```
<!-- in index.html, where there is a slim menu on the left and a big content area on the right /-->
<frameset cols="1, 4">
<frame name="menuframe" src="menu.html" />
<frame name="contentframe" src="startpage.html" />
</frameset>

<!-- in menu.html /-->
<a href="index.calender.html" target="contentframe">a calender</a>
<a href="startpage.html" target="contentframe">back to start</a>
```With the frame implementation, I can edit menu.html any time, to add or reorder links, that open the pages in a big content frame.  But frames take up the whole screen.
Now, instead, I have searched a lot for a way to use the 'target=""' attribute on <object> elements, but I found nothing.  I wish I could have a main page (probably just index.html) with a menu in it, that targets an <object>.  Or, the opposite, with a bunch of unique pages, and a menu <object> that can navigate the whole page, not just within the object itself.
If there is any way to do that, **please tell me!**  Or if there is a way to place <frame>s with margins, not spanning the entire screen.  If there is no way, maybe I will try the PHP idea.

---

### Post by SoloSalsa on 2007-06-23
> **dempl_dempl said:**
> That means you won't see any results when playing with files at home. You have to copy them to web server first. 
On some servers , if you don't set extension to ".php" , it won't work.
Also , on those servers,  you have to put included files ( like up-frame.shtml )  to have ".shtml" extension.PHP is a magic word I sort of know about, but do not know.  Is it actual programing, like a host-side service?  I have no way to run server technologies, if that is what it is.  Just plain page delivery.  But if that is client side, like javascript, then maybe...  How do I position those, then?  Like this?```
<!-- in index.html or index.php /-->
<head><stylesheet is somewhere.css></head><body>
<div id="menufromphp"><*? readfile("up-frame.shtml"); ?></div>*
<div>content</div>
</body>

<!-- in stylesheet.css /-->
div#menufromphp {
width: 200px;
left: 0px;
}
```Is that right?  If there is no head inside the file read from php, are all styles inherited from the containing page?  Or is there some complete different way to handle this?
Thank you all for helping.

---

### Post by xtacocorex on 2007-06-23
Frames are so 90's.  Sorry for being brash, but it's the truth.

You're best off with CSS and something like PHP.  I just learned enough PHP to get the side bar for my model airplane's club website up, so it reads in a text file of the html that I want printed in the link column.
Here is the code that renders the sidebar.  cmalinks is a style for the div tag.
```

<!-- LINK BAR -->
<div class="cmalinks"><font size="2">
    <br><!-- This puts a nice gap under the dashed border -->
    <!-- THIS PHP CODE READS IN A TEXT FILE WITH THE LINK HTML FOR THE SIDEBAR SO CHANGES -->
    <!-- CAN BE MADE TO A SINGLE FILE AND WILL FITLER TO ALL THE PAGES -->
    <?php
        // Get a file into an array.  
        $lines = file("./sidelinks.txt");
        // Loop through our array and dump out the HTML code it contains
        foreach ($lines as $line_num => $line) {
            echo $line;
        }
    ?> 
</div>

```

Here is what is contained in sidelinks.txt:
```

    <!-- Main Items -->
    &nbsp;&raquo; <a class="sidebar" href="./index.php">Home</a><br>
    &nbsp;&raquo; <a class="sidebar" href="./about.php">About CMA</a><br>
    &nbsp;&raquo; <a class="sidebar" href="./officers.php">Club Officers</a><br>
    &nbsp;&raquo; <a class="sidebar" href="">Bylaws</a><br>
    &nbsp;&raquo; <a class="sidebar" href="">Calendar</a><br>
    &nbsp;&raquo; <a class="sidebar" href="./beginner.php">For Beginners</a><br>
    &nbsp;&raquo; <a class="sidebar" href="./field.php">Flying Field</a><br>
    <!-- Sub Item -->
    &nbsp;&nbsp;&nbsp;&nbsp;- <a class="sidebar" href="./fieldrules.php">Field Rules</a><br>
    &nbsp;&nbsp;&nbsp;&nbsp;- <a class="sidebar" href="./student.php">Student Manual</a><br>
    &nbsp;&raquo; Joining<br>    
    &nbsp;&nbsp;&nbsp;&nbsp;- <a class="sidebar" href="./joincma.php"><b>Join CMA</b></a><br>
    &nbsp;&nbsp;&nbsp;&nbsp;- <a class="sidebar" href="http://www.modelaircraft.org/membership_applications.asp">Join AMA</a><br>
    &nbsp;&raquo; <a class="sidebar" href="">Flightline Archives</a><br>
    &nbsp;&raquo; <a class="sidebar" href="">Photo Gallery</a><br>
    &nbsp;&raquo; <a class="sidebar" href="">R/C Links</a><br>

```

---

### Post by dempl_dempl on 2007-06-23
SoloSalsa: You don write entire page in PHP, you use  the HTML code, and for inclusion of l menu, you use 
code I posted .  If you have not understand my post, read it again. I not so good in explaining things, indeed :) , but do your best to understand me.

To recap:

<html>
your code
your code
your code
your code
....
//include menu file
<? readfile(¨menu.shtml¨) ?>  //  <----------- that all PHP there is to it ...
your code 
your code
etc...
</html>

---

### Post by SoloSalsa on 2007-06-23
Thank you, xtacocorex and dempl_dempl.  That does not look hard.  See, I never really knew what PHP was.  I thought it was something like SQL, something ran by the host, which I have no access to.  But, now I see that it is run by the client, just like javascript.  I never even considered it because I did not know about it.  But now it looks promising.
One question: how big is it on compatibility?  I know browsers toggle javascript (like me, I keep it disabled for unknown sites), but do people ever disable PHP?

---

### Post by xtacocorex on 2007-06-23
PHP has to be enabled on the server for it to work, so as long as the server supports it, it'll work.

I also don't know much about PHP.  The code I showed you I learned in about 5 minutes to do pretty much what schallstrom said about ease of maintaining a site.

Glad I could help out.

---

### Post by schallstrom on 2007-06-24
> **SoloSalsa said:**
> Thank you, xtacocorex and dempl_dempl.  That does not look hard.  See, I never really knew what PHP was.  I thought it was something like SQL, something ran by the host, which I have no access to.  But, now I see that it is run by the client, just like javascript.  I never even considered it because I did not know about it.  But now it looks promising.
One question: how big is it on compatibility?  I know browsers toggle javascript (like me, I keep it disabled for unknown sites), but do people ever disable PHP?

PHP **is** running on the **server**. So you need access to a web server which supports PHP processing. But almost every hosting company does include PHP support even in the cheapest offers today. If your hosting company does not support PHP, move away from them, they are bad.

PHP is a recursive acronym for PHP: Hypertext Preprocessor. And a Preprocessor it is, meaning there is some PHP code on the server side which gets processed by a PHP interpreter on the server. The result of this (pre)processing is (X)HTML code which then gets transferred to the client the request came from. So, no, PHP is not at all like JavaScript. The client will never see any of the PHP code. And yes, PHP is a real programming language.

There are alternatives to PHP which work basically the same way I described above: I already mentioned Ruby (and the Ruby on Rails framework) which is pretty fashionable these days. Or you could use Python which is a much nicer language then PHP. But PHP is the most common one and most supported by hosting companies, so to start you probably would be best off with PHP if you don't want to run your own server.

I suggest getting a O'Reilly book on PHP and read a bit and play a bit...

---

### Post by robgr85 on 2007-06-24
hi!

thanks for suggestions of usage 'readfile' on my website -seems to be a good ida.

In my webpages I used to do sth different. i've created one basic file with layout, and then used php to read contents of the webpages from MySQL databases. I think it is better way to, because You can create web-pages  and it gives the oportunity to edit code of Your pages form any html browser without logging onto server.

Robert

---

### Post by SoloSalsa on 2007-06-24
And when I looked into it, I found that PHP *does* running server side.  I am not using a paid host.  My high school has a directory for every club and activity (all hundred eight of them), and the band is one of the few that has content.  I'll have to see if the school has such support.

---

### Post by Freikia on 2007-06-24
I use PHP to generate my menus from an array. On each page I have a call similar to
```
<?php getMenu( 'news' ); ?>
```
which in turn gets the menu from a routine similar to:
```
// Output Navigation Menu
function getMenu( $name ) {
	$menu = array (
		array ( // Home Page
			"name" => "index",
			"page" => "index.php5",
			"desc" => "Go to home page",
			"text" => "Home"
		),
		array ( // News
			"name" => "news",
			"page" => "news.php5",
			"desc" => "Read news about this site",
			"text" => "News"
		),
		array ( // Feature
			"name" => "feature",
			"page" => "feature.php5",
			"desc" => "Featured sites, services and products",
			"text" => "Featured"
		),
		array ( // Contact
			"name" => "contact",
			"page" => "contact.php5",
			"desc" => "Contact site admin",
			"text" => "Contact"
		)
	);
	print "<div class=\"navbar\"><em>Navigate</em>\n";
	for ( $p = 0; $p < count( $menu ); $p++ ) {
		print "<a href=\"".DOMAIN.$menu[$p][page].'" ';
		if ( $menu[$p][name] == $name ) print 'id="current" ';
		print 'title="'.$menu[$p][desc].'">'.$menu[$p][text]."</a>\n";
	}
	print "</div>\n";
}
```
The 'name' field in the call is used to set "id=current" to highlight the current page using CSS. I find this makes adding a new page to my site very easy =)

---

### Post by robgr85 on 2007-06-24
> **SoloSalsa said:**
> And when I looked into it, I found that PHP *does* running server side.  I am not using a paid host.  My high school has a directory for every club and activity (all hundred eight of them), and the band is one of the few that has content.  I'll have to see if the school has such support.

make php file with the code:

```

<?php
phpinfo();
?>

```

---

