---
title: "[SOLVED] javascripting..."
date: 2008-02-29
forum: Programming Talk
---

### Post by hockey97 on 2008-02-29
Hi I am using jquery. I am having a tough time making a html page to have tables draggable and resizable and once all set and done a save function. 

I am making a social website and I want the user to be able to customize their own layout of their page.

I wanted to have the tables resizable and draggable and also have a way where they can edit the background images to their own. Just by adding their own url.

How can this be done is their any demo examples??

---

### Post by Wybiral on 2008-02-29
The draggable/sizable stuff is easy to do with "interface" for jQuery. [Here are some demos]("http://interface.eyecon.ro/demos"). Just look at the source and read the docs.

---

### Post by hockey97 on 2008-02-29
Well I understand how to apply the dragging and resizing  I just don't know how I can save the values  like if a user resises a table and dragged it somewhere else on the page  I want them to be able to save what they done so that it will stay in that position.

I also would like to know how I can have the use able to input a url for the background of the page would  the url just be a text input???
and add that url text in where the background tag is at?

---

### Post by mike_g on 2008-02-29
You might want to look at using an SQL database to store that stuff as javascript can't write to files. In JS you could always write the data to cookies, but that would be destroyed when cookies are cleared and wouldent work if a user logs in from another computer.

---

### Post by soapytheclown on 2008-02-29
i use mootools but im sure there will be something similar to using cookies to store positions of things locally on the users machine:-

[http://demos.mootools.net/Hash.Cookie](http://demos.mootools.net/Hash.Cookie)

---

### Post by hockey97 on 2008-02-29
Ya I know I have mysql.  I am just trying to figure out how to input it into the database would that be just  use php???

like when the user registers I have a pre-made layout that is stored in the database  this is all the html and css coding  in that database.

The am confused on how I can have the user to input their url of a background they want  so that url would replace the default one I put in.

that goes for the main background and also want the user to be able to select the tables in the layout to put a background on those .
I know how to add values from php from the user as input and put it into mysql database but I don't know if the input should be text only??? would that work and if it does how would I make it to replace the url that I provided?

Is their any way other than cookies to save the positions of the tables that the user moved??? can't if grab the x,and y values or css left and top those values and import them into the database in some way??

I have all the html and css code for the persons default layout which I made. SO in the database it's noting but code now I want to be able to change the css position of the table they dragged and dropped and also change the background url ect.

Cant that be done in php??

---

### Post by mike_g on 2008-02-29
> 
The am confused on how I can have the user to input their url of a background they want so that url would replace the default one I put in.
Is this kinda like what you are after:
```
<script>
	function ChangeBackground()
	{
		document.body.background = document.getElementById("url").value;
	}
</script>

<html>
	<head>
	</head>
	
	<body>
		<input id="url" />
		<button onclick="ChangeBackground()">Change</button>
	</body>
</html>
```

---

### Post by hockey97 on 2008-02-29
yes. but would I be able to send that input value into a sql database??  would I use php or can javascript handel to input it into mysql??

---

### Post by mike_g on 2008-02-29
Sure you can. Just put it in a form and post it.

Edit: you will need php to deal with the post data tho

---

### Post by naugiedoggie on 2008-02-29
> **hockey97 said:**
> Hi I am using jquery. I am having a tough time making a html page to have tables draggable and resizable and once all set and done a save function. 

I am making a social website and I want the user to be able to customize their own layout of their page.

I wanted to have the tables resizable and draggable and also have a way where they can edit the background images to their own. Just by adding their own url.

How can this be done is their any demo examples??

Is JQuery the right tool for this job?  I don't know anything about it beyond what I just looked at on the web site, but it kind of sounds like you are using it to reinvent the wheel.

You really want a widget toolkit, like GWT (google web toolkit).  If you know Java, GWT will make the page designs you need, using widgets to design it (in Java) and then compiling the Java into Javascript.

To save settings in the way you describe, you must use a backend datasource of some kind.  If the site is expected to handle much traffic, then a RDBS -- you need to provide the hooks on your page to connect to it.  For low-volume, simply serializing to XML probably would do it.

I think you've actually tackled a significant project.  I'd look for a toolkit that will enable you to burp out the JS for the interface without having to get a PhD because the client-server interaction for saving those user settings will be nontrivial.

Sounds like fun!

Thanks.

mp

---

### Post by mike_g on 2008-02-29
Yeah that bit would be a little more difficult, but on the bright side its easier than an MMORPG :)

---

### Post by mssever on 2008-02-29
To save the settings, just use AJAX to post the information to a server side script (PHP, Intercal, etc.) which will store it in the database.

When it comes to setting the background, you can use whatever input method you like: text box, upload field, Javascript prompt, color picker, snail mail to you, etc.

---

### Post by hockey97 on 2008-03-01
ok I am some what stuck now lol  . I have the html page in my database meaning just the coding in the script.

In order for me to apply the javascript to that file I have to mode the script by script.

Like right now I am using php to grab the html code out of the database but how can I modifiy the html code without having to mode the html file?? 

I want to only add the javascript just to edit modifiy the users page which is in html.

like what I have so far is the php script grabbing the html code out of my database now I have to add the javascript  for only that session meaing this page I am making is the edit page where the users can mod their html page.

so after I grab the html code I can't  figure out how I can apply the javascript to it ? should I use a div?  how can I  script it so that only during that page session ect that those javascript will be applied and also how I can script it to certain html tables?

---

### Post by mike_g on 2008-03-01
> Like right now I am using php to grab the html code out of the database but how can I modifiy the html code without having to mode the html file??
I dont know what you mean by 'mode' but you can update the inner HTML of any tag (except in IE, which causes problems with updating inner html in some table elements and some other things). Heres an example: 
```
<script>
	function UpdateText(el, newContent)
	{
		document.getElementById(el).innerHTML = newContent;
	}
</script>

<html>
	<head>
	</head>
	
	<body>
		<h1>Enter stuff to change content of a div</h1>
		<input id="input" />
		<button onclick="UpdateText('d', document.getElementById('input').value)">Change</button>
		
		<div id="d">
		This will be updated
		</div>
	</body>
</html>
```

---

### Post by hockey97 on 2008-03-02
I see waht your saying.  what I meant about mode was the page I am making right now has to edit an html page that I have the code saved in mysql.

I am using css to control the tables positions and height and width.

So  should I have the css code in my database and then play with that??

Thanks for the help I know I am annoying  hahaha lol.

---

### Post by Can+~ on 2008-03-02
Let me get things straight for you. To create a successful web app, you need the following:

-You don't store html/php files on a database (you may store direction to them on sql, but that's another story).
-PHP is designed to produce HTML output (well.. anything..), so therefore, if you want to build a posting application it would be something like:

HTML Form (or php generated) -> PHP uploader script -> Database(MySQL)

And then they retrieve that

Database(MySQL) -> PHP outputs Html -> HTML output.

-In terms of layout, you should use CSS, create all kinds of stuff on CSS, and make your PHP output that, for instance, if you want to each post made into a separate div:

[PHP]	while ($row = mysql_fetch_assoc($db_result)) {

			echo "<div class='myclass'><span class='highlight'>".$row['username']."</span> 

			<span class='shadow'>(".$row['postdate'].") (".$row['posttime'].")</span>\n<br />";

			echo "<p>".$row['message']."</p></div>";

		}[/PHP]
(This example is just a simple piece, the $db_result is the return of a query made to the database (which I didn't put), the while explores the content and echoes the output stored in a the array $row)

Then PHP outputs a div with highlighted text using css. And Javascript is something you add for the last client layer. Javascript should be something more like creating dynamic thingies on client side.

I think you should start with something simpler like a posting application, something on your home server where you post something, uploads it, and then show it on another page. I even have a sample of that around my folders.



Or.. maybe, by database you're meaning your webserver?

---

### Post by hockey97 on 2008-03-02
Well  here is what I have so far:   ok   I have a system that is like myspace.com 

where users posts messages and create their page (layout) 

I have apache 2 webserver and mysql database.

I have the register now page and login page and the profile display page.


So for the profile page  I have the php script grab html code that is saved in the mysql database.

When the user registers the register script will create a default profile page layout.

i am now currently working  on a page where when they click in the account page that they can edit their layout.

I want them to be able to drag and drop tables around on their profile page  to position it where they want and  also put their own background for the page....

... and  the background of the tables so it can have a personal touch.


I have so far on the edit page that it checks the session if the user is still the user ect.....

.... and also  after checking if the user is the user  ect then it grabs that users profile.

that's all I have so far.

The problem I have  is I don't know how I can add the javascript  to certain tables.

Their are ad tables and logo table for my site then the rest tables left over is the users  I only want them to edit only the users tables and not touch the website logo and ad table.

I  don't know how I can tell php or javascript to have the table elements draggable I know I can use a div tag.

But  in the mysql database I have just the html code I don't have the file saved into mysql.

So I don't know  how I can make the changes to have the tables to be draggable  without directly changing the html code.

I have the system working  like the html file is the users profile.

So I have succeeded on registering a user and logging the user in and grabbing the users profile to display it.

but now I have to add the feature to edit  the layout to their liking.

when I mean the html code is in the mysql database I mean like  if you have mysql  and you logged into the database and you manually 

type in the database table  html code and save it.

So when I am making the edit page I  am having a hard to to figure out how I can directly modify  the html well css in this case.  I don't have a css code saved in the database.

to what you explained it seemed like you explained me how to display the contents.

here is a pic form of what's happening

user registers(auto generate layout for user profile) 

-> put the generated layout user profile in mysql database . 

->  when user logs in grab user profile from mysql  

-> if user hits edit profile button grab profile from mysql database  then 
add javascript for drag and drop and resize tables on layout, display it. 

-> user makes modifications on tables ,on position and size ,save the mods and then update mysql database with new modifications to user profile layout.
-------------------------------------------------------------------------------------

Now I just don't know how I can directly make the tables that are controlled by css to be dragable and resizeable in javascript.

like I can do this if I went to the html file and opened it in notepad and done the modifications but how can you do it by code meaning just by php where I can add the javascript to the css/html code that was saved in the  mysql database.

The html code  has css applied to it. the html code only has tables no widths or height defined to them just plain html elements.

The css would define the widths and heights ect.

---

### Post by Can+~ on 2008-03-02
Thank you for clearing things up, I maybe misunderstood your first messages.

Ok, now that I understand your problem, let me give you my opinion:

I feel you have to do this in another method, as storing html code on sql seems impractical, because MySQL, and most languages, are designed to store mostly plain content, and leave the PHP (or any other method) handle the rest, you would be storing loads of <tag> content, tabs, spaces, for nothing.

I'm not insulting you, or your method, it just seems a bit over complicated, when you could do things much simpler like:

-Creating a user.php display, that displays the current user id (for instance, in your sql you have user 1234, and if you load the page is something like *[http://mypage.com/user.php?uid=1234](http://mypage.com/user.php?uid=1234)*. And PHP inserts, and also loads the preferences of the user.

Now, this covers the first thing, viewing the user account, now, how to load the personal styling?

Leave them the CSS file to be edited, then you store this CSS file somewhere, and when loading the account, you insert the referenced CSS file on a "user_stylesheets". Or alternatively, create a friendly interface that lets users edit their css like:

"your background : [_______________][Upload][Link]"
"your ... [_______________][Upload][Link]"

This would be a more complicated thing to do, but it would add to the user experience, instead of editting a cold css file. It all depends on your target audience, if your audience are programmers, you could give them a piece of script to do it themselves (j/k), but as I guess that your social page will be directed to just anyone, I would go for friendly GUIs.

Then store the changes by replacing the user-referenced css file.

And to do the thing of the drag and drop, use DIVS! divs are far better for dragging and dropping, since they can be detached (fixed, absolute, etc), and maybe the table should be a container for divs that can be dragged in between the cells, or just leave the divs be floating around.

Maybe, to save the positions for later, make the cells of the table a coordinate system, let's say something like:

```

0-----1-----2
| ??  |     |
1----1,1---1,2
|     |     |
2----2,1---2,2

```

And store their position on sql in a simple coord (a,b) and then, load it and paste it on it's respective position (let the php do that), or save it via css somehow.

Hope my opinion helps you. :guitar:

---

### Post by Can+~ on 2008-03-02
Adding to my above message, I would like to add an statement about mySQL and databases in general.

You should try to store ALWAYS medular information, let the objects around it set the rules on how to display it.

Programmers have to deal on how to store data, and that's what programming is, moving data around, that's why we use bulk tasks like for( in ), whiles, and all sorts of things to break information apart and move it from format A to B.

Databases should always store the most abstracted form of data, not heavy loaded html, because when you do that you'll have stuff like:

[COLOR="Red"](Example 1, wrong)[/COLOR]
[PHP]Id, User 1, Page layout
1, Peter, <div class="a">My name is....</div><div class="w">.....</div>
2. David, <div class="b">Hello from ...</div><div class="x">.....</div>
3, Tom, <div class="c">I'm a writer..</div><div class="y">.....</div>
4, Harvey, <div class="d">I like cookies..</div><div class="z">.....</div>[/PHP]

You're repeating content, #1 mistake of databases.

[COLOR="Green"](Example 2, better (but not perfect))[/COLOR]
[PHP]Id, User 1, Message, Class1, Class2
1, Peter, My name is...., a, w
2. David, Hello from ..., b, x
3, Tom, I'm a writer.., c, y
4, Harvey, I like cookies.., d, z[/PHP]

In this later example, everything has been stripped, and the classes left apart, but still, it won't be perfect until we split the data from the styling, and that's why I sugges using separate css files referenced:

[COLOR="Green"](Example 3, ideal)[/COLOR]
[PHP]Id, User, Message, CSS_id
1, Peter, My name is...., 123
2. David, Hello from ..., 124
3, Tom, I'm a writer.., 1245
4, Harvey, I like cookies.., 2128[/PHP]

We leave the css references to some other database, or a plain file. That's the beauty of CSS, we split the style, and compress it into a form of data. So we can go like "use style number XXX" and ready to go.

Good luck with your project, and I hope this helps any other person having troubles with Databases. Any comments/suggestions/erros, I'm open.

---

### Post by hockey97 on 2008-03-02
I understood everything you said until example 3.


What do you mean by separate css files referenced??

do you mean have like 3 or 4 css files with different styles and use the ref id to apply those to different users?

and  would I  make css files for each users and then save the link in the database so it could be modified when  users log in??

I am just trying to edit the layout of there profile which I would use javascript to be applyied to the tables.

to add the javascript drag thing how could I do this?  like  do I have to open up notepad to edit the html/css file??  or can I just by php or somthing while loading the edit page the php would add the javascript  and the divs to the specifi tables I want to be dragable?

Other than that I understood.

---

### Post by Can+~ on 2008-03-02
> **hockey97 said:**
> I understood everything you said until example 3.


What do you mean by separate css files referenced??

do you mean have like 3 or 4 css files with different styles and use the ref id to apply those to different users?

and  would I  make css files for each users and then save the link in the database so it could be modified when  users log in??

My idea of the css is that you have a css associated to the guy, for instance, when page loads, it loads the css corresponding to the user, and all his data on the corresponding places.

You probably would have to make css files per user, or better, a CSS default file, and if the user wants to personalize, then it will save a user_id.css. For instance, if user 1234 makes a page he will have a :

user_1234.css file associated to him, alternatively, he could load some of the pre-made css files (just an idea!), or maybe load the style of someone else, like having another database with "css file, public/private" this is completely up to you.

> ... or can I just by php or somthing while loading the edit page the php would add the javascript  and the divs to the specifi tables I want to be dragable?

Other than that I understood.

Yes you can. Sample content:
[PHP]<html>... blah blah
<head><title><?php echo "Viewing profile: $user_name" ?></title>
<?php echo "<link href="$user_style" rel="stylesheet" type="text/css" />" //Attach the style ?> 
<script ...>
    myDragFunction()  //Define your javascript function (or external file)
    {
          do stuff
    }
</script>
</head>
<body>
<?php
     echo "<div class='blahblah'  onclick='javascript:myDragFunction(this)'>$user_content</div>"; //Print with the proper javascript function call.
    ?>
</body>
</html>
[/PHP]

*edit* Bascially, php let's you print output anywhere on the file, so, you can do any nasty trick with php+js+html as you please. You can even run the php before the whole code to query the database and fill the blanks.

*edit2* I added the title to my example.

---

### Post by hockey97 on 2008-03-02
oh ok I get it now.  Thanks  Can+~

---

### Post by hockey97 on 2008-03-07
ok one more thing to ask. using php how could I generate and save a css file for each user??

I have the base default html page and the css file that have the defaul settings which is what they will use.

Like how would you when the person edits the page how would you save those new settings and generate a css file which will be saved in a directory I specifie .

I can handel the database on puting the url link of the css file that the user create but I am having trouble seeing how I can generate a css file for each user that wants to customise their page.

---

### Post by hockey97 on 2008-03-08
I deleted the html code in my mysql database and then just put the info for where my html file is at.

I am having trouble on displaying my html page this is the based html file where later on they can customize it.

can you give a example of a method of displaying the html without having to put the html code in the database??

---

### Post by Can+~ on 2008-03-08
> **hockey97 said:**
> can you give a example of a method of displaying the html without having to put the html code in the database??

Like putting the html inside a .html file? (in this case .php)
[http://www.w3schools.com/html/html_examples.asp](http://www.w3schools.com/html/html_examples.asp)

I don't understand what the problem is, a site is a collection of files on your local tree that the user can view rendered from html by the browser to a graphical interface.

PHP is another layer that creates html (or any plain text, but we're talking about online) on server side, then sends the result to the user. So if you enter into

userview.php?id=1234

Now userview.php will grab the 1234 id and search in the database for the user 1234, the database has a link to the css, php pastes the css link on the head and all the user data on the body of the page.

I'm starting to doubt that you can build a Social site, you should learn more before jumping onto something like this.

---

### Post by mssever on 2008-03-08
Example (with no error checking; read about SQL injection before running such code on a live site):
[php]<?php
$qry = mysql_query("SELECT `name`, `favorite_color` from `users` WHERE `id` = $user_id;");
$result = mysql_fetch_assoc($qry);
?>
<p>Hello, <?=$result['name']?>! I remember that your favorite color
is <em><?=$result['favorite_color']?></em>.</p>[/php]You need to spend some serious time reading the PHP manual. Given all the trouble you're having, I'm beginning to think that programming might not be for you. You can't write programs unless you can figure out problems of this sort on your own--with the help of the proper manual. So I'm wondering if you have what it takes to become a programmer. Unless you're just lazy and would rather waste other people's time instead of learning for yourself. I'd hate to assume that about someone, though.

---

### Post by LaRoza on 2008-03-08
You can write CSS in PHP, just send the correct MIME type.

[php]
<?php
    header("Content-Type: text/css\n\n");
/*CSS here and PHP*/
?>
[/php]

It would be simpler, in my opnion, to have one CSS file, and just change the markup according to user preferences. (It would just be attributes)

---

### Post by hockey97 on 2008-03-08
sorry lol  just got confused... I had a php script that what do a lookup in the database and now just figured out it's not needed so instead of redirecting the user from the login page to a php file I just redirected the user to the html file.

I just got confused .

I got the whole thing to work I have the link of the .css in the database and it gets plugged into the html file becuse on the user login.

I have one more questions and it's about security is anyone can help me on ways to pass the variable on...

like when the user logs in  then in  browser it would show profile.html?id=user

and I notice if I were to just copy that whole url and then find user names I can just type at the end where id=user I can type in any user that exists and I would get into their account without having to log in.

I do have what it takes to be a programmer. I have certifications in html, php, and c++ programming.  I have tooken classes in highschool that tought me about the hardware side using logic gates and may more. I am currently in college going for accounting.

I wasn't have trouble with the database I just got confused I haven't been eating 2 for 2 days just liquids, energy drink and pop.  I got confused.

it's right now working as we speak.

I forgot it was the css link I had to get, and I thought it was the html link then I got confused and that's where my problem was.

---

### Post by mssever on 2008-03-08
So make your script check the user's credentials before showing them the page.

---

### Post by hockey97 on 2008-03-08
I do check before I load the page for them.   

it would still load  even if that is not your account all you need to know is the users name and you can get into their account.

Well I will deal with that some other day.

Thanks for the help though.

---

### Post by mssever on 2008-03-08
If you're already checking the user's credentials, then simply take some appropriate action if the check fails. E.g., send them to a login page, display an error and exit, etc.

A simple if statement is all you need...

---

