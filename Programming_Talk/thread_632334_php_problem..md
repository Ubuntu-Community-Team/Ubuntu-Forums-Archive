---
title: "php problem."
date: 2007-12-05
forum: Programming Talk
---

### Post by hockey97 on 2007-12-05
HI I made a php script to upload images to my database mysql.

I get this error failed to open stream: Permission denied  and another error saying fail to move . 

I googled around and found post saying it's a permission issue and to chmod the directory and the php file where it's and and were you want to store the image.

I done so and still get the same error, I even check php.ini if it was in safe mode and it was not on .  

I asked this question in my other post on the server & security area didn't get a response on this questions so I thought it might belong over here.

Do you know how I can fix this  is this a permission issue?? if so where and what do I have to change  in order to get this to work.

---

### Post by ThinkBuntu on 2007-12-05
Is this on a shared host or on your own computer? Maybe it is a permissions issue and you're referencing the wrong folder using "/" to begin your directory, placing the files relative to the DocumentRoot. Most servers restrict this.

---

### Post by hockey97 on 2007-12-05
It's my own computer I am using apache2 and the latest mysql.
and bind 9 , I also have the domain name paid for, to be internet published.

and I am getting that error.  

I am using the dir right  by doing somthing like /home/webpages/mysite 

I have the directories chmodded to 777 .

I am using virtual host in apache and the website works and all but I I just get an error on the part where  the user can upload pics to my mysql database where I then display them on my site.

I have seen so many post's giving different ideas to fix this problem and I tried alot and still havent fix the problem.


is their  any place I have to config  to allow php scritps to upload stuff??

I checked the php.ini and havent seen anything wrong in their.

---

### Post by ThinkBuntu on 2007-12-05
> **hockey97 said:**
> It's my own computer I am using apache2 and the latest mysql.
and bind 9 , I also have the domain name paid for, to be internet published.

and I am getting that error.  

I am using the dir right  by doing somthing like /home/webpages/mysite 

I have the directories chmodded to 777 .

I am using virtual host in apache and the website works and all but I I just get an error on the part where  the user can upload pics to my mysql database where I then display them on my site.

I have seen so many post's giving different ideas to fix this problem and I tried alot and still havent fix the problem.


is their  any place I have to config  to allow php scritps to upload stuff??

I checked the php.ini and havent seen anything wrong in their.
/ is not your root directory, it points to /var/www in Ubuntu and other places for other machines. DocumentRoot, /, is set in your httpd.conf file. Try running the same script with a URL relative to the upload page or to the script.

---

### Post by hockey97 on 2007-12-05
in the httpd.conf file I have nothing in that.

and my document root for the vhost points to the resource directory which is in /home/.... ect. 

but the files of the vhost's are in /var/www/sites-enabled.

so your saying I should in that script use a url type thing not the exact sorce ???

---

### Post by ThinkBuntu on 2007-12-05
Your local Apache server would not work without it:

On my httpd.conf file:
DocumentRoot "/Library/WebServer/Documents"

On yours, most likely:
DocumentRoot "/var/www"

---

### Post by hockey97 on 2007-12-05
are you talking about the mysite.conf ???   

I have 2 files  their both my website and contain info about my website directories. 

I have the  DocumentRoot  thing in them the directs them to the directory where my sites are and their not in /var/www.
on my computer I don't use /var/www that's for the localhost server.

I am using a virtual host in apache2 .

and using ubuntu 7.10 .

I do have a httpd.conf file but their is noting inside it.

---

### Post by geirha on 2007-12-05
Could you paste code (with any password and other sensitive information filtered out)? Preferrably a small test-case if possible, which gives you the error.

---

### Post by hockey97 on 2007-12-05
404

---

### Post by hockey97 on 2007-12-06
I got it fixed.  I was  gave the wrong permissions, is supposed to be 750  I done 777

---

### Post by geirha on 2007-12-06
You'll need to check that all of the directories in the path is accessible by apache. ```
ls -ld /home /home/aaron /home/aaron/WebPages /home/aaron/WebPages/sue.com /home/aaron/WebPages/sue.com/files /home/aaron/WebPages/sue.com/files/images
```

Apache needs execute permission for each directory in that path. chmod the ones that lack it with ```
chmod a+x *dir*
```

EDIT: On a closer look, you might want to change [php]$path="/home/aaron/WebPages/sue.com". $n;[/php] to [php]$path="/home/aaron/WebPages/sue.com/". $n;[/php]

---

### Post by hockey97 on 2007-12-07
thanks for the reply, I got it fixed, the last directory had the wrong permissions it was 777 but I needed 750 to have my web server able to use it.


I got another questions for php ,  is their any way for interactivity .

graphic wise.  Like I want to make something that with a mouse you can click tables and drag around.  is their anything that is a graphic library for php??

also is their any tips on how I can make my site secure and also make the files that are uploaded secure. What do the pros do with hackers and viruses ect???

---

### Post by Wybiral on 2007-12-07
> **hockey97 said:**
> thanks for the reply, I got it fixed, the last directory had the wrong permissions it was 777 but I needed 750 to have my web server able to use it.


I got another questions for php ,  is their any way for interactivity .

graphic wise.  Like I want to make something that with a mouse you can click tables and drag around.  is their anything that is a graphic library for php??

also is their any tips on how I can make my site secure and also make the files that are uploaded secure. What do the pros do with hackers and viruses ect???

You mean on a website? You should learn about DOM and SVG. DOM, in particular is how you would manage most of those kinds of effects (draggables/mouseovers). PHP has nothing to do with any of that, you need to learn some Javascript. My favorite DOM manipulation libraries are [jQuery]("http://jquery.com/") and [MochiKit]("http://mochikit.com/").

---

### Post by smartbei on 2007-12-07
Anything that works as 750 should work as 777. I am pretty sure that that was not the problem.

Interactivity has more to do with Javascript/ECMAscript than PHP. Take a look at the google personalized homepage for an example of a layout edited with Javscript, and saved on the server with AJAX - is this what you are looking for?

About your site - verify all user input and scan the files for viruses if you can (no idea how this is done actually :p).

EDIT: beaten by Wybiral :). +1 to jQuery.

---

### Post by hockey97 on 2007-12-07
> **smartbei said:**
> Anything that works as 750 should work as 777. I am pretty sure that that was not the problem.

Interactivity has more to do with Javascript/ECMAscript than PHP. Take a look at the google personalized homepage for an example of a layout edited with Javscript, and saved on the server with AJAX - is this what you are looking for?

About your site - verify all user input and scan the files for viruses if you can (no idea how this is done actually :p).

EDIT: beaten by Wybiral :). +1 to jQuery.

well when I chmod that directory to 777 I get that permission error, but when I put it on 750 it's all fine.

a post explained that whenever you have a webpage that will upload files or change anything with the filesystem   the place where you store it needs to be chmod 750  which lets the website access to it.

they claim that chmod 777 is only for all users on your linux system to be able to read and write to it.

now when I look at the properties of that dir I see owner [www.-data](www.-data)
 

I guess I start learning java.  I am making a web page layout which you can drag around and stuff like make a custom layout.
ect.
also jQuery Mochikit able to be downloaded onto ubuntu 7.10???

also If I wanted to make an interactive login, like have an animation which during the middle part of the animation the login slowly fades in.

so I would be able to drag a table around using those lib and javascript, and be able with the mouse to resize the table???
wish me luck.

and thanks for the help...

---

### Post by Wybiral on 2007-12-07
Javascript, not Java. You need to download whichever one you plan to use, and include it in your html document that you plan to use it in. Both sites have plenty of good examples, I suggest viewing the source of the demos to get an idea of how they're implemented.

---

### Post by hockey97 on 2007-12-07
ya I am going with javascrpt. 

but like in html  you can make tables and cells in that table.

will I be able to  with a mouse resize the table ?? 

I am looking at the examples right now and also googled around,
I am some what getting a hang of it.

---

### Post by Wybiral on 2007-12-07
jQuery has a plugin called "interface" that makes resizables pretty easy: [http://interface.eyecon.ro/demos/resize.html](http://interface.eyecon.ro/demos/resize.html)

---

### Post by hockey97 on 2007-12-07
in java script how do you add/ use the plugins.

like jquery  I look at most of the plugins that are out their.

How would I use all the plugins on one script??? 
and would I be able to use php to pass on variables to javascripts??

---

### Post by Wybiral on 2007-12-07
You use the plugins exactly like you use jQuery (just include it in the page using a script element and its "src").

For setting things in Javascript with PHP, all you have to do is generate the script code for it...

```

<?php
echo "<script type='text/javascript'>var x = '$SOMEVAR';</script>";
?>

```

---

### Post by hockey97 on 2007-12-10
the jquery  lib  is not running right.

I copied and pasted the exambples from the lib website and it didn't work.

like the first thing was to make a link when you click on it a popup window comes up saying hello world. 

I just get an ordanry link  just as if I wrote it in html.  do I need a package to download for apache2 to run javascripts???

or is somthing else wrong?

---

### Post by Wybiral on 2007-12-10
Explain in detail how you did it. You have to download jquery.js, then include that file in your HTML document like this:

```

<script type="text/javascript src="PATH_TO_JQUERY/jquery.js"></script>

```

Then you can use jquery in your HTML document. Javascript has nothing to do with the server, it's executed in the browser. So it will work on all browsers with Javascript enabled.

---

### Post by hockey97 on 2007-12-10
here is what I did and saved it as an html file. I have the  jquery.js file which I downloaded from their site.  I have java installed.

```

<html>
  <head>
    <script type="text/javascript" src="/home/aaron/WebPages/jquery.js"></script>
    <script type="text/javascript">
    $(document).ready(function() {
   $("a").click(function() {
     alert("Hello world!");
   });
   });
    </script>
  </head>
  <body>
    <a href="http://jquery.com/">jQuery</a>
  </body>
  </html>

```

that's what I have exactly and what I get is a link to jquery.js and  it just acts like a regular html script for the link.

---

### Post by hockey97 on 2007-12-10
Is their anything wrong with the script?? or on how I done it???

it's on my apache2 server and  when I  use firefox to get to my web browser I then click the file to run the html file.

the link supposed to spit out a window that say's hello world when the link is clicked but I tried it and nothing happens like like an regular link.

---

### Post by hockey97 on 2007-12-11
hi, with javascript script do you really think that I can create or make a website that you can grab the html tables with a  mouse and drag it anywhere on the html page and drop it down?? would it be possible to grab the location of it?? where the table has been dragged to??


I still can't figure out why the javascript is not working I followed what the tutorials said I even copied the exact same thing they gave as an example just added the dir to where the jquery file is at.

---

### Post by Wybiral on 2007-12-11
Yes, you can really create draggable and resizable tables with jquery and interface. If you're using FF, check the Javascript error console (tools->error console) and see if it gives you any warning when you load the page. That code should work, assuming you downloaded the right file.

---

### Post by hockey97 on 2007-12-11
for jquery file did  I have to compile the script??? 
I went in the download area and saw at the bottom that say's to use make or ant to  build jquery and also to have jdk  java development kit downloaded and installed too.

Also I just checked the firefox error console and found one error  for that one file  it said $ is not declared.

---

### Post by Wybiral on 2007-12-11
It's Javascript, not Java. You don't have to compile it, just download the uncompressed one. They only compress them for space and load efficiency (because the client-end downloads the script when the page is viewed, it's not executed on the server).

If you download the "jquery.js" file, put it in a web-accessible folder, and use that code you posted, it should work.

---

### Post by hockey97 on 2007-12-11
yes I got the jquery.js , I know it's javascript  and it's not java java is like c++ it's an application type lango .

I have the uncompressed jquery.js and it's in the webpage folder which is used in apache2.

in the firefox I have javascript enabled and I  looked in the error console and it spit out a $ not defined error.

---

### Post by Wybiral on 2007-12-11
OK, the "$ not defined" means that jquery isn't being included at all (this forum has the same issue, lol... I don't know why they refuse to fix it).

Check your path and make sure it has the right permission to be viewable.

EDIT:

To be real sure, put the "jquery.js" file in the same folder as the html document, then change the [src='path-to-jquery'] part to [src='./jquery.js']

---

### Post by hockey97 on 2007-12-11
just edited::::

it now works, i forgot to change the path to just jquery.js 

thanks I just tested it and now it works, I can see the window popup and say hello world.

now you just got to help this fourm out with their problem lol.

jk

thanks alot now I get to have some fun with javascript.

---

### Post by Wybiral on 2007-12-11
And for future reference, you use jquery plugins exactly the same. Just download the file and import it into the HTML like you did with the "jquery.js" file.

---

### Post by hockey97 on 2007-12-11
is ui.mouse.js  a plugin for jquery??

I went to the dragables demo area, and look at their script.

I tired to re-create it, which I did but  I can only drag the box when between the body tags I put script tags and the src to the url link area they gave in that example.

it will work but demo say's depends on  ui.mouse.js 

is that another file that I have to download??? 

or is it inside jquery.js ??

---

### Post by Wybiral on 2007-12-11
All the interface-plugin functionality I've ever used has come straight from "interface.js"

They may have smaller modules that let you use a certain functionality from it without the whole thing, but you should be able to just download the "interface.js" file and import it exactly like you did the "jquery.js" file.

EDIT:

As a quick example, here's how to make all "div"s draggable using interface:

```

<html>
    <head>
    <script type="text/javascript" src="./jquery/jquery.js"></script>
    <script type="text/javascript" src="./jquery/interface.js"></script>
    <script type="text/javascript">
    $(document).ready(function() {
        $("div").Draggable();
    });
    </script>
    </head>
    <body>
        <div style="width:128px; height:128px; background-color: #000000"></div>
    </body>
</html>

```

Note: This isn't an example of best practice, just a quick example to show you how easy it is. Change the paths to the correct files.

---

### Post by hockey97 on 2007-12-11
Thanks I know am getting somewhat used to it.
I will be doing more pratice and playing around with the stuff.

---

### Post by hockey97 on 2007-12-11
can you really save where the person draged the  table too????

and would I be able to customize my own password login, on how it looks like use my own art for the input boxes and also the button to submit.

---

### Post by Wybiral on 2007-12-11
Absolutely. Look at the "css" method of the jquery objects [here]("http://docs.jquery.com/CSS/css"). Then you can submit that via form to your server script, which can store it in a database. Later you can bring that back and restore the position by passing that to the page. Here's how you can get the x,y using the css method:

```

<html>
    <head>
    <style type="text/css">
        #object {
            width:128px;
            height:128px;
            background-color: #000000;
        }
    </style>
    <script type="text/javascript" src="./jquery/jquery.js"></script>
    <script type="text/javascript" src="./jquery/interface.js"></script>
    <script type="text/javascript">
    $(document).ready(function() {
        $("#object").Draggable();
        $("#getButton").click(function() {
            $("#display").val(
                $("#object").css("left")
                + ", "
                + $("#object").css("top")
            );
        });
    });
    </script>
    </head>
    <body>
        <input id="getButton" type="button" value="Get X,Y"/>
        <input id="display" type="text"/>
        <div id="object"/>
    </body>
</html>

```

EDIT:

> 
and would I be able to customize my own password login, on how it looks like use my own art for the input boxes and also the button to submit.


Yep. You can makes your submit button an image using the HTML element "img" and you can alter the look of your input fields using CSS.

---

### Post by hockey97 on 2007-12-12
I am planning to make a intro page to my website I want to create a 3d charater that splits the screen and  water vaper spits out of the cracks and freezes and slowly while freezing it becomes an icy user login  area.

would I do this using flash??? 
or could I get away with it by using blender 3d to make the animation images and then use javascript to  detect the last frame of the animation and then fade in a login prompt area??

Also is their any way I can create a page where it links up with the mail server, like to make a webpage that handels e-mail accounts where they can see what they have in the inbox and can also send e-mail or write an e-mail to other people.com?

---

