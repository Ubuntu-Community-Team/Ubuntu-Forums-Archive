---
title: "javascript gallery/php site..helllp!!"
date: 2008-11-07
forum: Programming Talk
---

### Post by terra.one on 2008-11-07
I hope someone can help, Im having problems adding a javascript gallery to a php site...it doesnt work, and i cant figure out why not......???


[SIZE="3"]this is the header where Ive linked the .js and .css
[/SIZE]
[PHP]<?php
if($_GET['p']=="bboys"){ ?>
<script type="text/javascript" href="<?=$PATH_TO_CSS?>jquery.js"></script>
<script type="text/javascript" href="<?=$PATH_TO_CSS?>jquery.galleria.pack.js"></script>
<link rel="stylesheet" type="text/css" href="<?=$PATH_TO_CSS?>gallery.css" />
<script type="text/javascript"> 
	
	jQuery(function($) {
		
		$('.skratch_gallery').addClass('gallery_class'); // adds new class name to maintain degradability
		$('.nav').css('display','none'); // hides the nav initially
		
		$('ul.gallery_class').galleria({
			history   : false, // deactivates the history object for bookmarking, back-button etc.
			clickNext : true, // helper for making the image clickable. Let's not have that in this example.
			insert    : undefined, // the containing selector for our main image. 
								   // If not found or undefined (like here), galleria will create a container 
								   // before the ul with the class .galleria_container (see CSS)
			onImage   : function() { $('.nav').css('display','block'); } // shows the nav when the image is showing
		});
	});
	
	</script>


<?php
}
?>
[/PHP]


[SIZE="3"]this is the actual content of the page...
[/SIZE]
[PHP]function get_content_bboys()
    
    {
    
    //$query = ("SELECT * FROM bboys WHERE id = 'bboys'");
    //echo $query;
    //$result = mysql_query($query);
    
    $result = mysql_query("SELECT * FROM bboys WHERE id = 'bboys'");
    
    $content = "<div class='demo'>\n";
    $content .= "<ul class='skratch_gallery'>\n";
    $content .= "<li'>\n";
    
    while ($row = mysql_fetch_array($result));
    {
       
    
    $content .= "<a href='index.php?p=bboys" . $row['id'] . "' title='" . $row['name'] . "'>
						<img src='/skratch/bboys/" . $row['img_file'] . "'  alt='" . $row['name'] . "' />
					</a>\n";
           
    }
    
    $content .= "</li'>\n";
    $content .= "</ul>\n";
    $content .= "</div>\n"; 
    
    return $content;
    }      
    
[/PHP]

[http://http://www.teragraphix.com/skratch/index.php?p=bboys]("http://http://www.teragraphix.com/skratch/index.php?p=bboys")


if theres any additional info...jus say =]

---

### Post by Delever on 2008-11-07
There are many things which may not be right, like is "$PATH_TO_CSS" actually pointing to anything, or $_GET['p'] actually equal to "bboys".

Look at source you get on web page, look if <script type="text/javascript"> tags actually point to right files, install firefox web developer plugin, look for any javascript errors.

---

### Post by terra.one on 2008-11-07
the "$PATH_TO_CSS" is cool, as it works for a different page...and the $_GET['p'] works in the same way....theres just something with the jquery...i dont understand, its saying its not defined, and to my humble knowledge it is lol...i can send you a file of the gallery...its three files?? 

I dunno whats going on:confused:

---

### Post by lapubell on 2008-11-07
i'm getting a "jquery undefined" error when I view some of your pages.

I don't think you need the

jquery(function($)...

when you use jquery.

try just using

$(function() { 
  //page onload functions here...
});

---

### Post by drubin on 2008-11-07
> **lapubell said:**
> i'm getting a "jquery undefined" error when I view some of your pages.

I don't think you need the

jquery(function($)...

when you use jquery.

try just using

$(function() { 
  //page onload functions here...
});


Those are the same thing

The reason you get a undefined is your  href="<?=$PATH_TO_CSS?> might not be defineded in php so would be blank and your pathing would be wrong.

---

