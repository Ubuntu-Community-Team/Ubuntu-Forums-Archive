---
title: "Parsing HTML"
date: 2007-12-24
forum: Programming Talk
---

### Post by LeTenken on 2007-12-24
Hello everyone, im trying to work on a little project to parse data from a folder of my favorite websites in HTML to a excel file. (or just a text file, i can import it manually)

I havent really did any programming outside of high school and college and im a little unsure on how i should start this.  If not too much trouble, any help would be appreciated, im just not sure where to start.
basically i just want the program to read the HTML document, search for all elements between the <b> </b> tags, and then write them to a file.

---

### Post by LaRoza on 2007-12-24
Use the DOM with Python or another language. It will be easy (ish).

[http://docs.python.org/lib/module-xml.dom.html](http://docs.python.org/lib/module-xml.dom.html)

Start at section 8. (Scroll down) there are several solutions, SAX, the DOM and the HTML modules.

The DOM is easy to use, and you want to use the getElementsByTagName() method.

---

### Post by LeTenken on 2007-12-24
thanks so much for the quick response, i will get on reading! ( i actually already started).  Hopefully i can still remember the python i was taught 4 years ago :(

---

### Post by LaRoza on 2007-12-24
> **LeTenken said:**
> thanks so much for the quick response, i will get on reading! ( i actually already started).  Hopefully i can still remember the python i was taught 4 years ago :(

[http://docs.python.org/lib/markup.html](http://docs.python.org/lib/markup.html)

You have more options than the DOM (which is used for XML and will through errors if it is not well formed)

---

### Post by ThinkBuntu on 2007-12-24
Exporting data to CSV is pretty easy with PHP, I even used it for a portable mailing list on two websites for a client. Let me give you my imperfect code. I've cut out the unnecessary parts, and you may need to make some minor changes to adapt it to your circumstances.
**mailing.php**
```
<form action="scripts/mailing_list.php" method="post">
	<fieldset>
		<ol>
			<li><label>Name:<em>*</em></label>	<input type="text" name="name"/></li>
			<li><label>Company:</label>	<input type="text" name="company" /></li>
			<li><label>Title:</label>	<input type="text" name="title" /></li>
			<li><label>Address:<em>*</em></label>	<input type="text" name="address" /></li>
			<li><label>Address 2:</label>	<input type="text" name="address2" /></li>
			<li><label>City:<em>*</em></label>	<input type="text" name="city" /></li>
			<li><label>State:<em>*</em></label>
			<select style="width: 50px;" name="state">
				<option value="AK">AK</option>
				<option value="AL">AL</option>
		
				<option value="AR">AR</option>
				<option value="AZ">AZ</option>
				<option value="CA">CA</option>
				<option value="CO">CO</option>
				<option value="CT">CT</option>
				<option value="DC">DC</option>
		
				<option value="DE">DE</option>
				<option value="FL">FL</option>
				<option value="GA">GA</option>
				<option value="HI">HI</option>
				<option value="IA">IA</option>
				<option value="ID">ID</option>
		
				<option value="IL">IL</option>
				<option value="IN">IN</option>
				<option value="KS">KS</option>
				<option value="KY">KY</option>
				<option value="LA">LA</option>
				<option value="MA">MA</option>
		
				<option value="MD">MD</option>
				<option value="ME">ME</option>
				<option value="MI">MI</option>
				<option value="MN">MN</option>
				<option value="MO">MO</option>
				<option value="MS">MS</option>
		
				<option value="MT">MT</option>
				<option value="NC">NC</option>
				<option value="ND">ND</option>
				<option value="NE">NE</option>
				<option value="NH">NH</option>
				<option value="NJ">NJ</option>
		
				<option value="NM">NM</option>
				<option value="NV">NV</option>
				<option value="NY">NY</option>
				<option value="OH">OH</option>
				<option value="OK">OK</option>
				<option value="OR">OR</option>
		
				<option value="PA">PA</option>
				<option value="RI">RI</option>
				<option value="SC">SC</option>
				<option value="SD">SD</option>
				<option value="TN">TN</option>
				<option value="TX">TX</option>
		
				<option value="UT">UT</option>
				<option value="VA">VA</option>
				<option value="VT">VT</option>
				<option value="WA">WA</option>
				<option value="WI">WI</option>
				<option value="WV">WV</option>
		
				<option value="WY">WY</option>
			</select></li>
			<li><label>Phone:<em>*</em></label>	<input type="text" name="phone" /></li>
			<li><label>Email:<em>*</em></label>	<input type="text" name="email" /></li>
		
			<p><input type="submit" value="Sign Up" class="submit" /></p>
		</ol>
	</fieldset>
</form>
```
**mailing_list.php**
[php]<?php

// Grab the form and assign to variables
$name		= $_REQUEST['name'];
$company	= $_REQUEST['company'];
$title		= $_REQUEST['title'];

$address	= $_REQUEST['address'];
$address2	= $_REQUEST['address2'];
$city		= $_REQUEST['city'];
$state		= $_REQUEST['state'];

$phone		= $_REQUEST['phone'];
$email		= $_REQUEST['email'];

// Dump the data to our flat text file

$list_file		= $_SERVER['DOCUMENT_ROOT'].'/admin/files/mailing_list.csv'; // Locate the mailing list
$mailing_list	= fopen($list_file,'a+'); // Open the list file
$member			= "$name\t$company\t$title\t$address\t$address2\t$city\t$state\t$phone\t$email\n"; // Define new data
$member			= chr(255).chr(254).mb_convert_encoding( $member, 'UTF-16LE', 'UTF-8'); // Format the info for CSV import
fwrite($mailing_list, $member); // write the info
fclose($mailing_list); // close the file

?>[/php]

---

### Post by ThinkBuntu on 2007-12-24
By the way, the previous script has one important problem: If a field is left empty, the layout of the spreadsheet suffers since there's no blank field entered to the CSV file. If someone knows how to do this, that would be very useful. I tried to use strlen() to replace empty fields with whitespace, but the whitespace in the CSV file never worked as expected...

---

### Post by tyoc on 2007-12-25
Why not simply fill it with a default value like  1MBL4NK or some like that?
---
I dont remember much PHP, but from what I see, you are only concatenating the values that have been imported and separating them with TAB char \t. Thought I dont think that is what a comma separated value file is about see [http://tools.ietf.org/html/rfc4180](http://tools.ietf.org/html/rfc4180) or [http://www.creativyst.com/Doc/Articles/CSV/CSV01.htm](http://www.creativyst.com/Doc/Articles/CSV/CSV01.htm) from that

> sqlite3 -csv test.sqlthen
> 
sqlite> create table testnulls(id integer primary key, x1 string, x2 string, x3 string);
sqlite> insert into testnulls(x3) values("with, the other no exist");
sqlite> insert into testnulls(x1) values("with2 the other no exist");
sqlite> insert into testnulls(x2) values('with2 the" other" no exist');
sqlite> select * from testnulls;
1,,,"with, the other no exist"
2,"with2 the other no exist",,
3,,"with2 the"" other"" no exist",


---

### Post by ThinkBuntu on 2007-12-25
My problem was with detecting the empty fields more than anything. I can do it with JS, but not so well w/ PHP.

---

### Post by tyoc on 2007-12-25
From this [http://www.webdeveloper.com/forum/showthread.php?t=71760](http://www.webdeveloper.com/forum/showthread.php?t=71760) see answer 4 and 5 you can search for them on the official site.

Also I suguest taht you put your name of fields inside an array. Then you can loop and test each 1 without need to hand write all those if isset $_REQUEST["handWritedField"], and also concatenate the "," and check if is the last field for dont append the ending "comma". By the way, you can internally perhaps check the internal representation of the fields, for see if it is a "good field" inthe sense of CSV and if not apply a function, and return it to concatenate, or allways call the funciton and the function return the same string without modification or the new string that is a "good field" in the sense of CSV.

With the name of fields, you can access the names with a index, IIRC in PHP there is a map thing also, thus you can map them names to indices if you want in certain place of code access the index without know the actual index, but see that you should update your map if you update the field order in the array.

---

### Post by LeTenken on 2007-12-25
hi everyone, thanks to the first few replies i managed to parse the html document i need

however all i managed to do was use write() onto a txt document, is there anyway i can have python make files on its own? 
and also how would i make excel files, lets say out of this: 
```

1	1:35	12	21
1	1:30	13	21
1	0:19	16	23
1	0:03	16	25

```
so far i just have it outputted into a txt file.

thanks for any help~

---

### Post by ghostdog74 on 2007-12-25
show how you parse your html.

---

### Post by Compyx on 2007-12-25
If you really, really want to write .xls files, [this link]("http://www.wotsit.org/download.asp?f=excel&sc=251864439") might help.

Mind you, the code to generate Excel files will probably be many times the size of the code to parse the html, so you might just want to stick to using .csv-files and importing those in Excel.

Relying on anything Microsoft came up with is generally a bad idea, given the closed nature of their software and their appalling quality of implementation.

---

### Post by LeTenken on 2007-12-25
what are csv files exactly? and how would i write them?

---

### Post by LaRoza on 2007-12-25
> **LeTenken said:**
> what are csv files exactly? and how would i write them?

Comma Separated Values.

Example:

```

1, LaRoza
2, LeTenken
3, ghostdog74

```

Stick stick a comma between the values. When Excel opens it, it will put the values into cells.

---

### Post by ThinkBuntu on 2007-12-25
Separating can be like this:
```
name		address		city		state
name2		address2		city2		state2

```
with tabs. There are many options, especially since OpenOffice Calc and Excel support all varieties of CSV.
Note that those fields should line up, but this forum isn't rendering whitespace entirely correctly.

---

### Post by LeTenken on 2007-12-25
thanks for all the csv help, i managed to output it neatly to an excel file, but it turns out the data is too large (too many pages), so i think i will have to consider making a database later, i very much appreciate the help so far, perhaps when i have questions about SQL i will ask here again.

anyways.

is it possible for python to use read() on HTML documents that are online? 
how do i get python to connect to websites?
thank you for all the help so far !

---

### Post by LaRoza on 2007-12-25
> **LeTenken said:**
> 
is it possible for python to use read() on HTML documents that are online? 
how do i get python to connect to websites?
thank you for all the help so far !

Yes, it is simple [http://docs.python.org/lib/module-urllib.html](http://docs.python.org/lib/module-urllib.html)

It is surprising what Python has standard.

---

### Post by LeTenken on 2007-12-25
omg urllib is so fun :)

---

### Post by LaRoza on 2007-12-25
> **LeTenken said:**
> omg urllib is so fun :)

I thought so too.

---

### Post by ThinkBuntu on 2007-12-25
> **LeTenken said:**
> thanks for all the csv help, i managed to output it neatly to an excel file, but it turns out the data is too large (too many pages), so i think i will have to consider making a database later, i very much appreciate the help so far, perhaps when i have questions about SQL i will ask here again.

anyways.

is it possible for python to use read() on HTML documents that are online? 
how do i get python to connect to websites?
thank you for all the help so far !
Gnumeric may do a better job of loading a huge spreadsheet.

---

### Post by LaRoza on 2007-12-25
> **ThinkBuntu said:**
> Gnumeric may do a better job of loading a huge spreadsheet.

Or OO Calc.

---

### Post by CptPicard on 2007-12-25
> **LaRoza said:**
> Or OO Calc.

OO Calc just absolutely chokes on loading a huge CSV btw, have a lot of negative experiences about that...

---

### Post by LaRoza on 2007-12-25
> **CptPicard said:**
> OO Calc just absolutely chokes on loading a huge CSV btw, have a lot of negative experiences about that...

In that case, disregard my statement.

I don't have experience in this, would normally use a database.

---

### Post by ghostdog74 on 2007-12-25
> **LeTenken said:**
> omg urllib is so fun :)

you should also check out urllib2

---

### Post by LeTenken on 2007-12-26
hi again guys! im almost about done with the program im trying to write.
the following might be a incredibly simple question that i might be able to answer myself after a few minutes of reading the python tutorial, however since i F5 this page every few minutes wonder if i can get the answer faster in here.

im trying to create a string that looks like 'yyyymmdd'
where yyyy = the year, mm = the month, and dd = day
so far ive been using a while loop to generate the days, and months but i have a problem if the month or day is single character, is there a way i can make str(1) = '01' by any chance?
also ive been using both  "" and ' ' for the strings in this program, i forgot whats the difference between "" and ' ' in python.

thanks again for all the help! im beginning to really love this community!

---

### Post by LaRoza on 2007-12-26
> **LeTenken said:**
> hi again guys! im almost about done with the program im trying to write.
the following might be a incredibly simple question that i might be able to answer myself after a few minutes of reading the python tutorial, however since i F5 this page every few minutes wonder if i can get the answer faster in here.

im trying to create a string that looks like 'yyyymmdd'
where yyyy = the year, mm = the month, and dd = day
so far ive been using a while loop to generate the days, and months but i have a problem if the month or day is single character, is there a way i can make str(1) = '01' by any chance?
also ive been using both  "" and ' ' for the strings in this program, i forgot whats the difference between "" and ' ' in python.

thanks again for all the help! im beginning to really love this community!

[http://docs.python.org/lib/module-datetime.html](http://docs.python.org/lib/module-datetime.html) Maybe something is there that can help. I am not sure how you are getting the dates, so I don't know what the answer is. That module can turn a string into a formatted datetime object.

The difference is that one will do variable substitution and the other won't.

I love this community too.

---

### Post by ghostdog74 on 2007-12-26
> **LeTenken said:**
> , is there a way i can make str(1) = '01' by any chance?

```

if len(day) < 2 :
    day = "0" + day

```
or 
```

>>> d="1"
>>> d.zfill(2)
'01

```

> 
also ive been using both  "" and ' ' for the strings in this program, i forgot whats the difference between "" and ' ' in python.

I leave it to you to read the docs.

---

### Post by LeTenken on 2007-12-26
hi again everyone, now its time for me to put my program together!
thanks to the help here i managed to create 3 separate py files that i need and now its time for me to put them together into one nice objected oriented program.
lets say the programs are x, y, z
program x returns strings which are urls
im having trouble with this:
say this is program x
```

def stringmaker():
	return 'http://www.someurl.com/somepage.html'
	


```

and say this is program y
```

def playbyplay(pbp):
	import urllib
	f = urllib.urlopen(pbp)

```

when i do y.playbyplay(x.stringmaker())
i get a "global name urlopen is not defined", why?

i hope my question makes sense if i can clarify my question more please let me know! thanks again!

---

### Post by LaRoza on 2007-12-26
Is the module imported?

---

### Post by LeTenken on 2007-12-26
> **LaRoza said:**
> Is the module imported?

i have no idea what this means, so i guess no, what should i do?
thanks for all your help on this so far btw :)

---

### Post by LaRoza on 2007-12-26
> **LeTenken said:**
> i have no idea what this means, so i guess no, what should i do?
thanks for all your help on this so far btw :)
Does the file with that import urllib?

---

### Post by LeTenken on 2007-12-26
program y
```

def playbyplay(pbp):
	import urllib
	f = urllib.urlopen(pbp)

```
this is what i have, but it doesnt seem to let me use it, does "import urllib" have to be somewhere else?

i also tried just running python in the terminal and running >>> import urllib before i started running my program, still didnt work.

---

### Post by LaRoza on 2007-12-26
> **LeTenken said:**
> program y
```

def playbyplay(pbp):
	import urllib
	f = urllib.urlopen(pbp)

```
this is what i have, but it doesnt seem to let me use it, does "import urllib" have to be somewhere else?

i also tried just running python in the terminal and running >>> import urllib before i started running my program, still didnt work.

Put it at the top.

---

### Post by LeTenken on 2007-12-26
still gives me the name error when i move it outside of playbyplay(pbp)

this is what the name error looks like:
```

  File "y.py", line 3, in playbyplay
    def playbyplay(pbp):
NameError: global name 'urlopen' is not defined

```
kinda strange how the error is on this line rather then where i actually use urlopen()
hmm...

---

### Post by LaRoza on 2007-12-26
> **LeTenken said:**
> still gives me the name error when i move it outside of playbyplay(pbp)

this is what the name error looks like:
```

  File "y.py", line 3, in playbyplay
    def playbyplay(pbp):
NameError: global name 'urlopen' is not defined

```
kinda strange how the error is on this line rather then where i actually use urlopen()
hmm...

Is this function a member of a class?

---

### Post by LeTenken on 2007-12-26
> **LaRoza said:**
> Is this function a member of a class?

im not sure, i guess not, im actually not to familiar with what you mean, being the newbie that i am
i basically ran y.playbyplay('http://www.someurl.com/somepage.html')
wouldnt y be the class?

---

### Post by ghostdog74 on 2007-12-26
does it occur to you that showing all that you have done might be much easier for us to help you with your problem? Also ,  i would suggest you at least read up some python material and understanding certain concepts.

---

### Post by LeTenken on 2007-12-26
i just thought dumping a bunch of code and asking for specific help might be a bit rude, as it might seem as if im asking you guys to do all the work
and i have been reading the python tutorial and using the library reference, as i am learning (or re-learning) python as i go along
regardless, i have learned a lot so far in this thread

is it really necessary to dump all my code?

---

### Post by ghostdog74 on 2007-12-26
> **LeTenken said:**
> 
is it really necessary to dump all my code?

it really doesn't matter. The countless worthless flame wars occurring around here takes up more bandwidth than your code. so yes, its necessary so that you can solve your problem quicker instead of you post bits and pieces and we have to guess what's wrong.

---

### Post by RIchard James13 on 2007-12-26
x, y and z are files.

To tell python to run a function from file x in file y your need to tell python you are doing so. You do this by importing the file. 

So if in file X you have

```
def somefunction():
```

And in Y you have

```
def otherfunction():
    somefunction()
```

When python reads and executes Y it knows nothing about X. You will get:
```
NameError: name 'somefunction' is not defined
```

If you change Y to
```

from X import *
def otherfunction():
    somefunction()
```

Then Python will read in the contents of X then Y and know what somefunction() is.

This is called scope. Normally when you write a program you put most functions into a single file, then you don't have the python doesn't know about bar.py when executing foo.py problem. Only when you get many functions and the program begins to be hard to understand should you break it across files.

---

### Post by LeTenken on 2007-12-26
> **RIchard James13 said:**
> x, y and z are files.

To tell python to run a function from file x in file y your need to tell python you are doing so. You do this by importing the file. 

So if in file X you have

```
def somefunction():
```

And in Y you have

```
def otherfunction():
    somefunction()
```

When python reads and executes Y it knows nothing about X. You will get:
```
NameError: name 'somefunction' is not defined
```

If you change Y to
```

from X import *
def otherfunction():
    somefunction()
```

Then Python will read in the contents of X then Y and know what somefunction() is.

This is called scope. Normally when you write a program you put most functions into a single file, then you don't have the python doesn't know about bar.py when executing foo.py problem. Only when you get many functions and the program begins to be hard to understand should you break it across files.


thank you for this, i think i know where im going wrong now :)

---

### Post by LaRoza on 2007-12-26
> **RIchard James13 said:**
> 
```

from X import *
def otherfunction():
    somefunction()
```

Then Python will read in the contents of X then Y and know what somefunction() is.

This is called scope. Normally when you write a program you put most functions into a single file, then you don't have the python doesn't know about bar.py when executing foo.py problem. Only when you get many functions and the program begins to be hard to understand should you break it across files.

Don't use "from library import *" in Python programs. Use this:

```

from library import function

```

So:

```

from sys import exit

```
 
Would allow you to use exit() without typing sys.exit().

If you import * you get everything and that defeats the purpose of namespaces.

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> If you import * you get everything and that defeats the purpose of namespaces.

maybe he wants to use everything from the os module without quantifying with os.<module> ? 

If Python allows one to use "from library import *" , then the matter of right or wrong, should or should not, is only just subjective.

---

### Post by LaRoza on 2007-12-26
> **ghostdog74 said:**
> maybe he wants to use everything from the os module without quantifying with os.<module> ? 

If Python allows one to use "from library import *" , then the matter of right or wrong, should or should not, is only just subjective.

In some cases, it makes sense to do that, but that is rare. It is subjective, but there are best practices that shouldn't be broken on whims

> 
Special cases aren't special enough to break the rules.
...
Namespaces are one honking great idea -- let's do more of those!


The rare instance I have seen it useful to import * is when using Tkinter where its members have names that won't be used by other modules.

---

### Post by RIchard James13 on 2007-12-26
> **LaRoza said:**
> Don't use "from library import *" in Python programs. Use this:

```

from library import function

```

So:

```

from sys import exit

```
 
Would allow you to use exit() without typing sys.exit().

If you import * you get everything and that defeats the purpose of namespaces.

I don't think he understands scope or namespaces yet. He needs to put everything in one file, but first he needs to understand how python is working through the files. Avoiding namespace pollution is a more advanced topic.

When you run python X.py what gets executed and when? Why doesn't Y.py get executed? Actually when you use import Y.py is not executed why not?

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> In some cases, it makes sense to do that, but that is rare. It is subjective, but there are best practices that shouldn't be broken on whims

Its rare but it doesn't mean it can't happen to someone, somewhere.
Yes, there are best practices, but I believe, "best practices" should be enforced. Just like Python interpreter enforces indentation. If the interpreter enforces no one can use " from library import * ", but only can use "from library import somefunction, another function", then all is right. If its not enforced, then the choice is up to the programmer.

---

### Post by LaRoza on 2007-12-26
> **ghostdog74 said:**
> Its rare but it doesn't mean it can't happen to someone, somewhere.
Yes, there are best practices, but I believe, "best practices" should be enforced. Just like Python interpreter enforces indentation. If the interpreter enforces no one can use " from library import * ", but only can use "from library import somefunction, another function", then all is right. If its not enforced, then the choice is up to the programmer.

Python doesn't actually enforce a lot. It gives you the freedom to do what you want. Like "private" member data, isn't really private, it is just convention that is understood.

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> It gives you the freedom to do what you want. 
and so you said it. Freedom. So this 
> 
Don't use "from library import *" in Python programs.

should be rephrased.

---

### Post by LaRoza on 2007-12-26
> **ghostdog74 said:**
> 
should be rephrased.

Don't do it unless you have a really good reason.

---

### Post by LeTenken on 2007-12-26
thank you so much for the discussion regarding namespaces and scope, even though i do not fully understand it yet i at least found out where i went wrong and know what to read next.
however when i attempted to fit x.py y.py z.py into one file it turns out  having my program do everything in one swoop took way too much time. i ended up with a file too big to open in text editor so instead i just had x.py write to x.txt (and then had to edit it so i wasnt getting too many webpages) and had y.py read the sized-down x.txt to make y.txt and then finally run z.py to read y.txt to make the information that i needed.
i probably didnt explain the above correctly, but it worked anyways.


now... what to do with my gigantic text file..............:confused:
guess im going to be asking database questions after i cram the sql i learned in high school.
but first, sleep!

thank you so much everyone, and since i finally realized theres a "thanks" button, im going to press it for everyone~
gosh it feels great to get a program to work

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> Don't do it unless you have a really good reason.
it should be :
"Don't do it unless you have a really good reason, like  for example if you don't want to quantify every module with the module and the dot, or if you feel like you want to do it your way. "

---

### Post by LaRoza on 2007-12-26
> **ghostdog74 said:**
> it should be :
"Don't do it unless you have a really good reason, like  for example if you don't want to quantify every module with the module and the dot, or if you feel like you want to do it your way. "

"and you want to clutter the global namespace"

---

### Post by ghostdog74 on 2007-12-26
> **LaRoza said:**
> "and you want to clutter the global namespace"

"and you want to clutter the global namespace, but that doesn't matter since I may using all the global namespace anyway, and most importantly, I like it."

---

### Post by LaRoza on 2007-12-26
> **ghostdog74 said:**
> "and you want to clutter the global namespace, but that doesn't matter since I may using all the global namespace anyway, and most importantly, I like it."

"Because you might want to memorize all the contents of every module you use so you don't accidently over ride it"

I am not entirely serious about this, so don't take anything personally. 

I don't recommend using import * unless you understand what it does and what the implications are.

I must admit, I have used it for somethings.

---

### Post by RIchard James13 on 2007-12-26
Most of what you are talking about regards importing from an external module to the project using "import *". Can anyone give me a reason why a python file should not import another python file in the same project using "import *"? Because I have never done it before I have never considered doing it but if my project is large enough then I would not see a problem since I would regard my projects namespace to be spread across all the files.

---

### Post by LaRoza on 2007-12-26
> **RIchard James13 said:**
> Most of what you are talking about regards importing from an external module to the project using "import *". Can anyone give me a reason why a python file should not import another python file in the same project using "import *"? Because I have never done it before I have never considered doing it but if my project is large enough then I would not see a problem since I would regard my projects namespace to be spread across all the files.

Some modules, like Tkinter, are often used in this manner because the contents of that module are unlikely to conflict with any function in scope, and because large amounts of that library are usually used. [http://docs.python.org/lib/node686.html](http://docs.python.org/lib/node686.html) the contents begin with tk anyway.

Other modules should not used this way, because you rarely use a large portion, in fact, if you use one or two function from the module, then you can import only those fuctions:

```

from sys import exit

```

This allows you to call exit(), but doesn't clutter the namespace.

If you are using a large portion of the module, and the names of the modules contents are not likely to be used by accident, you can use import *. I find this useful only in GUI modules.

---

### Post by skeeterbug on 2007-12-26
Hey,
It is a matter of preference:

```

from sys import *

def exit():
    print "this is mine.."

if __name__ == "__main__":
    sys.exit()

```

sys.exit() is still being called over my exit, if I dropped sys., it would call my modules exit. It seems pretty clear to me. If it looks like this though:
```

from sys import *

if __name__ == "__main__":
    exit()

```

I can see where you would run into problems. If you import * and use the use the proper namespace in your call to functions/members, you will be fine.

```

from sys import *

if __name__ == "__main__":
    sys.exit()

```

---

### Post by RIchard James13 on 2007-12-26
Sorry I don't mean external modules like Tkinter I mean files within your own project.

---

### Post by LaRoza on 2007-12-26
> **RIchard James13 said:**
> Sorry I don't mean external modules like Tkinter I mean files within your own project.

It depends, if you had a large complex module, which you will be using with other modules, I would keep it in a namespace, however, if the problems won't occurs, and you plan on using the majority of the functions/objects it would make sense to import *

---

### Post by RIchard James13 on 2007-12-26
> **LaRoza said:**
> It depends, if you had a large complex module, which you will be using with other modules, I would keep it in a namespace, however, if the problems won't occurs, and you plan on using the majority of the functions/objects it would make sense to import *

Ok I was just wondering since in C/C++ you can group things within your makefile and I think Java just does it some other way. I was wondering whether there was any python specific way of doing it.

---

### Post by pmasiar on 2007-12-27
> **LeTenken said:**
> hi again everyone, now its time for me to put my program together!
thanks to the help here i managed to create 3 separate py files that i need and now its time for me to put them together into one nice objected oriented program.

You don't need OOP until you have objects, which seems to me you don't. Don't try to make it more complicated that it has to be.

> 
lets say the programs are x, y, z
program x returns strings which are urls
im having trouble with this:
say this is program x
```

def stringmaker():
	return 'http://www.someurl.com/somepage.html'
	


```

and say this is program y
```

def playbyplay(pbp):
	import urllib
	f = urllib.urlopen(pbp)

```

when i do y.playbyplay(x.stringmaker())
i get a "global name urlopen is not defined", why?


In program z you need to import both x and y so you  can use them as you did in code above.

As a beginner, you may consider not bothering about OOP, put it all into single file (if it is not tto big) and just use it as is, without making fancy OOP dance.

---

### Post by pmasiar on 2007-12-28
> **RIchard James13 said:**
>  Can anyone give me a reason why a python file should not import another python file in the same project using "import *"? .

1) if error is reported in a function, it will be easier to track where it is defined. Otherwise, you just have to remember what module defines what functions.

2) name clash. This happened in real life: 

my friend  defined his own function with same name as imported by "import *". Silent clash, no errors reported (Python lets you rebind function name with another body if you need it) and rather confusing error resulted.

3) because Guido told you so :-)

---

