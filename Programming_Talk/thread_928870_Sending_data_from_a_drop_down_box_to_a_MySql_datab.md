---
title: "Sending data from a drop down box to a MySql database"
date: 2008-09-24
forum: Programming Talk
---

### Post by suforum on 2008-09-24
Hi,

Can someone explain to me, how to send data selected from a dropdown menu into a MySQL database, I understand how the coding would work, but not when you have several choices to pick from as shown:-

> Choose the Type of Issue
<select name="dropdown" Id="dropdown">
  <option value="General">General</option>
  <option value="Server">Server</option>
  <option value="Database">Database</option>
  <option value="Environment">Environment</option>
  <option value="Requirement">Requirement</option>
</select>

I'd like to understand how I could fit in these options. I understand you must post it like this:-

> // Get values from form 
 $comments=$_POST['']; 

And I'm guessing this [''] would contain the name of the form, in this case 'dropdown' if im right? but not sure what the ID can be used for as above?

I am also guessing a if statement maybe required based on the option selected by the user, and the particular option selected has that 'string' sent into the database, for example in my previous post:


> if ($priority != NULL) { 
$priority = 1; 
} 
else { 
$priority = 0; 
}  

______________________
[Permanent Links](http://www.submitedge.com)

---

### Post by PC-XT on 2008-10-03
I believe you are using PHP, in which case $_POST['dropdown'] in your example would equal the value of the selected option. That is, if Server is selected, its value is "Server", so the value of $_POST['dropdown'] would be 'Server'. It the name or text displayed is different from the value attribute, the value attribute is the one that is used here. To test which one was selected when the form was sent, you could use either if statements, or a switch structure:```
if ($_POST['dropdown']=='General'){...}else if($_POST['dropdown']=='Server'){...}...
//You could assign some variable to $_POST['dropdown'] to avoid repitition

//swtich construct:
switch($_POST['dropdown']){
case 'General':
//stuff to run for general
break;
case 'Server'
//stuff for server
break;
...
default:
//used if value is not listed
}

```

---

### Post by mssever on 2008-10-03
> **suforum said:**
> And I'm guessing this [''] would contain the name of the form, in this case 'dropdown' if im right? but not sure what the ID can be used for as above?$_POST['dropdown'] will contain the value of the selected item (the value attribute of the option tag. The "id" attribute (notice the case) is a handle you use to reference that element from CSS or Javascript.

I am also guessing a if statement maybe required based on the option selected by the user, and the particular option selected has that 'string' sent into the database, for example in my previous post:

> [quote]if ($priority != NULL) { 
$priority = 1; 
} 
else { 
$priority = 0; 
}[/quote]Why are you setting $priority to 1 any time it's currently non-null? You're potentially losing data. Try: ```
if($priority == NULL) $priority = 0;
```
Note that you should use [noparse][code][/noparse] tags, not [noparse][quote][/noparse] tags for pasting code.

---

