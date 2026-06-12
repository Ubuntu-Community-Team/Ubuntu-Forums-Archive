---
title: "php: website system question."
date: 2009-05-18
forum: Programming Talk
---

### Post by hockey97 on 2009-05-18
Hi, I want to know how would someone manipulate the html and css files using php?

I basicly want to make a css file and a html file to be generated.

well, I mean  for example:  I want my users of my website to be able to customize their layout. 

So I was thinking that I cand create a default layout with html and css. Then they can use a editor I made that will be able to change anything on the layout from changing the sizes of elements to changing the element. 

Like for example: they deleted the layout so it's a white blank page. 
They then could add images/artwork for the background and add in photos, slide shows  and videos and music etc.


what I want to know is can I in php  be able to add html code and css code to the html and css files without overwriting stuff.

here is a example in theory not in code : 

the css file : 

```
 

font color 

body 

class_ads

class_img 

end

``` 

lets say I open this file in php. 

Is their a way I can add code in between class_ads  and class_img 

like could I ad a class inbetween those. 

If show how would you ?  I want this done by code, I don't want to open the file so the user themselves can edit it.


So the question would be ...  could php add code to a html file or a css file at lines that have no code at so I don't have to overwrite the file.



thanks ;)

---

### Post by Reiger on 2009-05-18
Is there a way? Yes. [That is what string/file manipulating functions are for, eh?]

[html]
<!-- stuff -->
<link rel="stylesheet" type="text/css" href="path/to/naive/css.php" />
<!-- more stuff -->
[/html]

[php]
<?php header('Content-type: text/css');
/* The really naive way is to read it into an array, and hardwire indices: */

$css = file('path/to/css/file.css');
$css = array_splice(/* arguments as appropriate, look it up in the manual */ );
echo implode(PHP_EOL,$css);
?>
[/php]

Would I want to do that were I tackling the same problem? No. [The beauty of cascading stylesheets is that they are... cascading! Last thing gets first priority. Simply including a custom CSS file at the end overwriting whatever values need be overwritten without actually *physically* overwriting anything at all... Are you still with me? It works brilliantly, though. ]

[html]
<!-- stuff -->
<link rel="stylesheet" type="text/css" href="path/to/default.css" />
<link rel="stylesheet" type="text/css" href="path/to/customized/css.php" />
<!-- more stuff-->
[/html]

[php]
<? header('Content-type: text/css');
/* echo the custom calculated CSS based on user preferences or whatever... */

?>
[/php]

---

### Post by hockey97 on 2009-06-02
ok, I see. Just one question. How would you with php generate html code on the fly? 

well like lets say I want the user to allow putting elements on the layout. 

Like images, youtube video, etc.  What I want to do is make a menu with javascript  which would  have a drop down menu and then a button next to it that will say add. Now  for example in the drop down menu if I select image. Then hit add button it will appear at a certain starting point on the layout editor. 

They then can drag it around and right click it to get a menu like image url etc.   This can be the same with graphics etc or youtube. 

but I want to add in to the layout html file and also css file these new elements.

what I am saying is how can I add the html code in the html file so it dosen't overwrite existing code in the html. I think this was answered the first answer you gave me.

Now how to know which element is witch? Do I just generate an ID ? 

Is their a way I can assign a element a number? so I can tell a image from image 1  from image 4  these can be the same image but posted in 2 different areas.

so I want to generate the html well not really generate it but grab the html code and insert it to the layout html file and also add in the css file. 

the css file should be able to grab values from javascript to insert the css values of the new element.

Thanks for the help. 

I did understand I can just make 2 css files one a default and one a custom css file. So I can use that. 

I am just asking about the html right now. Like can I just load in a html file and specify a new line but be able to reference that line again in case the user later on wants to delete it.

---

### Post by Reiger on 2009-06-02
I do not really see what the problem is?

If I want users to essentially customize a page I'd have 1 or more tables which track the customizations made; then have my PHP code compute the result from these pieces of `delta' information.

The key is to generalize. Arbitrary locations will require you to store the coordinates; but simply adding additional items to lists do not.

---

### Post by hockey97 on 2009-06-03
The problem I am facing is being able to open a file for example lets say a html file. 


I want to open it and with code figure  out whats what. 

that inplode function I looked it up in the manual and shows that is separates strings like  bob,ron,danny,  etc. 

what I am trying to figure out is that how in a html file will I know what code is what using just php scripts. 

For example lets say the person adds a youtube video and a image. 

and lets say after 2 weeks this guy decides to delete  just the youtube video.

Is their a way for me to use php to figure our where in the html file is the youtube code so I can delete it, and what if their was 2 youtube videos like he added one before he deleted the old one. How would I tell which youtube code is which?

Like can php search the html file for the difference in the source of the youtube video?

I am just trying to understand how would the php files be able to know the difference between the html tags. 

cause I think that php only thinks these are just strings like text. 

So I think that the computer won't know the difference between  html tags.

like <img></> <object></object>  etc.  

So it will just think it's text. Is this true or am I way off? 

basicly I am saying can you do the same thing as using sql a database way of doing things. 

Like with the html file can you like  scan the file for specific tags to select and either delete them or edit them like chance the src url.

---

### Post by Tibuda on 2009-06-03
Don't store it in a HTML file, it would require some pain XML parsing. Store it in a database, and generate the HTML on-the-fly. Something like this:
[php]<?php
include 'functions.php';
$username = $_SESSION['username'];
$style = query('SELECT selector, attr, value FROM styles WHERE username = $1', $username);
$blocks = query('SELECT id, content FROM blocks WHERE username = $1', $username);
?>
<!doctype here>
<html>
<head>
<title>Customizable page</title>
<link rel="stylesheet" type="text/css" href="base.css"/>
<style type="text/css">
<?php foreach ($styles as $style) {
  echo $style['selector'].' { '.$style['attr'].':'.$style['value'].'; }';
} ?>
</style>
</head>
<body>
<?php include 'header.php'; ?>
<?php foreach ($blocks as $block) {
  echo '<div class="block" id="block'.$block['id'].'">';
  echo $block['content'].'</div>';
  echo '</div>';
} ?>
<?php include 'footer.php'; ?>
</body>
</html>[/php]

---

