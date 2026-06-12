---
title: "accessing php variable in javascript"
date: 2007-10-03
forum: Programming Talk
---

### Post by mohtasham1983 on 2007-10-03
hello,
I'm facing a problem since i added some ajax code to my php page. 

I have a form in which there are 10 text entries. For each entry there is a button for entering comment about each of those 10 entries. It means if you click on the button related to entry number 3, all comments related to entry number 3 will be shown and there will be a new button for submitting each comment. At first I was facing problems with nested forms, but I figured it out how to get it working. My new problem is when I write a comment about for one comment, it works fine, but when I want to write comment for another entry, it just sends the text as undefined.

My 10 entry names are not constants and change time to time based on entry ID in database. So I tried to define my textarea name as a php variable based on entry ID like this:
```

$textarea_name=$match_id."desc";
"<td align='right' colspan='2'><textarea rows='5' cols='40' dir='rtl' name='{$textarea_name}'></textarea></td>"

```

Until here everything is fine and my textarea element will be assigned by the desired name. 

Then once the textarea element is filled, I want to call a javascript function and send textarea data to it.

```

"<a href='#{$match_id}' send_comment({$match_id},{$user_id},document.bet_form.{$textarea_name}.value);'" .
		" ><img src='pics/send_comment.png' width='70' height='30'></a>


```

As you can see, send_comment() uses 3 variables of 2 are simple php variables and work file. For the 3 parameters I want to pass the textarea value previously defined in my form. Unfortunately this method for some reasons that I really like to know, doesn't work.

I have tried to assign a constant name to textarea element. So when I set the third parameter as the constant name, everything worked fine which meant the send_comment function works properly. But since it was constant, all written comments would be added to that special entry.

I have tried different combinations of methods, which either returns undefined, nothing or javascript error.

Any idea how to solve this problem?

Thanks in advance

---

### Post by superyounan1 on 2007-10-03
explain send_comment() some more, what are the 3 inputs, what is the result.

the third parameter you're passing doesn't make sense, should it be a string?

you have [PHP]send_comment({$match_id},{$user_id},document.bet_form.{$textarea_name}.value);[/PHP]

try
[PHP]send_comment($match_id,$user_id,"document.bet_form" . $textarea_name . ".value");[/PHP]

---

### Post by mohtasham1983 on 2007-10-03
Basically send_comment() is a javascript function.

[PHP]
function send_comment(str,user_id,text)
{
if (str.length==0)
  { 
  document.getElementById(str).innerHTML="";
  return;
  }
xmlHttp=GetXmlHttpObject()
if (xmlHttp==null)
  {
  alert ("Your browser does not support AJAX!");
  return;
  } 
var url="functions/stats/add_match_comment_process.php?match_id="+str+"&user_id="+user_id+"&description="+text+"&location=bet";
xmlHttp.onreadystatechange=stateChanged;
xmlHttp.open("GET",url,true);

xmlHttp.send(null);

function stateChanged() 
{ 
	if (xmlHttp.readyState==4)
	{ 
		show_comment(str);
	}
}
} 

[/PHP]

Accidentally I erased onclick event, when posting my first post.

Basically the code should be like this:
[PHP]
<a href='#{$match_id}-1' onclick='send_comment({$match_id},{$user_id},\"document.bet_form\" . $textarea_name . \".value\");'" .
		" ><img src='pics/send_comment.png' width='70' height='30'></a>
[/PHP]

As you can see this function will call add_match_comment_process.php with extra parameters. As I mentioned in my post if the third parameter be constant, everything works fine without any problem.

And third parameter type should be string, as it contains the value of textarea element.


I tried what you suggested , but it didn't work either. :(

---

### Post by superyounan1 on 2007-10-03
The context is still not clear, is the link being generated as a string in PHP?

if yes, then this is how the link should be constructed:


[PHP]

$text = "document.bet_form".$textarea_name."value";
$link = "<a href='#$match_id' onClick=\"send_comment($match_id,$user_id,$text);\"><img src='pics/send_comment.png' width='70' height='30'/></a>

[/PHP]

---

### Post by mohtasham1983 on 2007-10-03
Thanks for help. I used your suggestion. Instead of sending the value of textarea field it sends undefined.

I tried to wrap the assigning part in a script tags like these, but they didn't work either:


[PHP]
print "<script>";
$text = "document.bet_form".$textarea_name."value";
print "</script>";
[/PHP]


[PHP]
print "<script>";
$text = "document.bet_form.".$textarea_name.".value";
print "</script>";
[/PHP]


[PHP]
$text = "document.bet_form.".$textarea_name.".value";
[/PHP]

I didn't get you what link you were talking about. I'm pretty sure that there is nothing wrong with send_comment() in javascript, since it can send constant string names. 


Here is a short description of send_comment():
By link, if you mean the one which is generated inside send_comment() JS function, that is values received from onclick event plus another string which tells the destination file that assigned parameters are coming from this file. Because the destination file process data based on where they are sent from.

---

### Post by superyounan1 on 2007-10-03
sorry, the code is too spaghetti for me to visualize clearly. 

I can't imagine i'll be able to figure it out without having all the code involved, the html, javascript, and php

---

### Post by mohtasham1983 on 2007-10-05
Basically this function has nothing to do with other functions.

Suppose that you have 10 news in your page and for each news by clicking a button a list of comment and a textarea element with a button will be opened under the news and users can send their comments. 

I can get it working if a user sends only one comment for each news in each page. But, if they open comments for second news and send their comments, they send  "undefined". This is because textarea element has the same name for both news. 

Consider following example. If we have a textarea element called "description" I can successfully send its value by calling a javascript function like this:

[PHP]
send_comment(1,2,document.bet_form.description.value);
[/PHP]

Now, since I have 10 news per page, I want to name each textarea based on news id so that there won't be any conflict between textarea elements. To do that, I set each textarea name using a PHP variable to $textarea_name

then I use the same javascript function:
[PHP]
send_comment(1,2,document.bet_form.{$textarea_name}.value);
[/PHP]

But it gives me the following error:
Error: missing ) after argument list
send_comment(1,2,document.bet_form.108.value);

I just don't know how to pass a php variable to javascript functions.

Any idea?

---

### Post by LaRoza on 2007-10-05
You can use PHP to generate the JavaScript, you will have to have the script's filename end in .php, but if you serve it with the MIME type "text/ecmascript", you'll have no problem.

---

### Post by mohtasham1983 on 2007-10-05
I just realized that It's not a problem of passing php variables to javascript.

In my send_comment(), if I pass some php variables to first 2 arguments, there s no problem, but for the third argument, it should pass the value of textarea field. 

if I add something like this:
[PHP]
onclick='send_comment($match_id,$user_id,document.bet_form.$text_area.value);'
[/PHP]

It gives me following error:
missing ) after argument list
[PHP]send_comment(109,2,docment.bet_form.109.value);[/PHP]

It's more like even though $text_area element is defined inside bet_form, it doesn't recognize it as an element for that form.

---

