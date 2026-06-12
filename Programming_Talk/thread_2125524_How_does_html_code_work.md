---
title: "How does html code work?"
date: 2013-03-14
forum: Programming Talk
---

### Post by sharkninja on 2013-03-14
so i want to know how the html code produces the form displayed in the browser? any ideas guys?
[HTML] <head>
 <title>Exam entry</title>
 
<script language="javascript" type="text/javascript">
 
function validateForm() {
 var result = true;
 var msg="";
 
if (document.ExamEntry.name.value=="") {
 msg+="You must enter your Name. \n";
 document.ExamEntry.name.focus();
 document.getElementById('name').style.color="red";
 result = false;
 }
 
if (document.ExamEntry.subject.value=="") {
 msg+="You must enter the Subject. \n";
 document.ExamEntry.subject.focus();
 document.getElementById('subject').style.color="red";
 result = false;
 }
 
if (document.ExamEntry.examinationnumber.value=="") {
 msg+="You must enter the Examination Number. \n";
 document.ExamEntry.examinationnumber.focus();
 document.getElementById('examination number').style.color="red";
 result = false;
 }
 
if (msg=="") {
 return result;
 }
 
{
 window.alert(msg)
 return result;
 }
 
}
 </script>
 </head>
 <body>
 <p>
 <font face="Candara">
 <font size="2">
 <h1><u>Exam Entry Form</u></h1>
 <fieldset>
 <form name="ExamEntry" method="post" action="success.html">
 <table width="50%" border="0">
 <tr>
 <td id="name">Name</td>
 <td><input type="text" name="name" /></td>
 </tr>
 <tr>
 <td id="subject">Subject</td>
 <td><input type="text" name="subject" /></td>
 </tr>
 <tr>
 <tr>
 <td id="examination number">Examination Number</td>
 <td><input type="text"  name="examinationnumber" maxlength="4" 
 </tr>
 <tr>
 <script type="text/javascript">
function validateRadio(obj,correct){
  var result = 0
  for(var i=0; i<obj.length; i++){
    if(obj[i].checked==true && obj[i].value==correct) result = 1
  }
  if(!result && obj.value == correct) result = 1
  return result
}
</script>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected GCSCE')" name="a" value="1" type="radio"> GCSE
 </tr>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected AS')" name="a" value="2" type="radio"> AS
 </tr>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected A2')" name="a" value="4" type="radio"> A2
 </tr>
 </tr>
 <td><input type="submit" name="Submit" value="Submit" onclick="return validateForm();" /></td>
 <td><input type="reset" name="Reset" value="Reset" /></td>
 </tr>
 </table>
 </form>
 </p></font></size></body>[/HTML]

---

### Post by grahammechanical on 2013-03-14
The browser is programmed to react in specific ways to the instructions in the web page.

[http://www.w3schools.com/html/default.asp](http://www.w3schools.com/html/default.asp)

Start learning Hyper Text Markup Language (HTML)

Regards.

---

### Post by sharkninja on 2013-03-14
How does this html code produces the form displayed in the browser and how does the javascript function performs the validation check.Am a new guys, i just started programming two weeks ago so i lack a lot of knowledge, so please no hate and finaly how does the html calls the validation routine?tnx

[html]
<head>
 <title>Exam entry</title>
 
<script language="javascript" type="text/javascript">
 
function validateForm() {
 var result = true;
 var msg="";
 
if (document.ExamEntry.name.value=="") {
 msg+="You must enter your Name. \n";
 document.ExamEntry.name.focus();
 document.getElementById('name').style.color="red";
 result = false;
 }
 
if (document.ExamEntry.subject.value=="") {
 msg+="You must enter the Subject. \n";
 document.ExamEntry.subject.focus();
 document.getElementById('subject').style.color="red";
 result = false;
 }
 
if (document.ExamEntry.examinationnumber.value=="") {
 msg+="You must enter the Examination Number. \n";
 document.ExamEntry.examinationnumber.focus();
 document.getElementById('examination number').style.color="red";
 result = false;
 }
 
if (msg=="") {
 return result;
 }
 
{
 window.alert(msg)
 return result;
 }
 
}
 </script>
 </head>
 <body>
 <p>
 <font face="Candara">
 <font size="2">
 <h1><u>Exam Entry Form</u></h1>
 <fieldset>
 <form name="ExamEntry" method="post" action="success.html">
 <table width="50%" border="0">
 <tr>
 <td id="name">Name</td>
 <td><input type="text" name="name" /></td>
 </tr>
 <tr>
 <td id="subject">Subject</td>
 <td><input type="text" name="subject" /></td>
 </tr>
 <tr>
 <tr>
 <td id="examination number">Examination Number</td>
 <td><input type="text"  name="examinationnumber" maxlength="4" 
 </tr>
 <tr>
 <script type="text/javascript">
function validateRadio(obj,correct){
  var result = 0
  for(var i=0; i<obj.length; i++){
    if(obj[i].checked==true && obj[i].value==correct) result = 1
  }
  if(!result && obj.value == correct) result = 1
  return result
}
</script>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected GCSCE')" name="a" value="1" type="radio"> GCSE
 </tr>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected AS')" name="a" value="2" type="radio"> AS
 </tr>
 <tr>
<td><input onclick="if(!validateRadio(this,3)) alert('You have selected A2')" name="a" value="4" type="radio"> A2
 </tr>
 </tr>
 <td><input type="submit" name="Submit" value="Submit" onclick="return validateForm();" /></td>
 <td><input type="reset" name="Reset" value="Reset" /></td>
 </tr>
 </table>
 </form>
 </p></font></size></body>[/html]

---

### Post by varunendra on 2013-03-14
Duplicate threads merged.

Please do not create multiple threads for same question. It dilutes community efforts to help.

Thank you, and Welcome to the forums!

**PS:**
I have edited the Thread title to make it relevant to your question.

Also, please use suitable tags while posting codes. For example, follow the 'Code tags example' link in my signature to see an example of 'Code' tags.
The html/php code tags are located in the same place as code tag.

---

### Post by SeijiSensei on 2013-03-14
[http://oreilly.com/css-html/index.html](http://oreilly.com/css-html/index.html)

---

### Post by prodigy_ on 2013-03-14
First, you seem a bit confused. HTML doesn't produce anything. It's just a markup language that can be used to describe what should be where on the webpage when browser renders it. Particularly, <form></form> and <input></input> tags are used to describe forms. HTML by itself is completely static. For anything dynamic (say, evaluating conditions) you need to add a programming language, most commonly PHP and/or JS.

Second, your questions seem too broad. If your code works, you probably should just leave it untouched. :) If it doesn't, then what exactly goes wrong?

---

### Post by woxuxow on 2013-03-14
i think the only thing you should know at the beginning is that browsers decide how to produce the form by html codes that placed in the page and one can be deferent from the other one

---

### Post by dodo3773 on 2013-03-14
> **prodigy_ said:**
> First, you seem a bit confused. HTML doesn't produce anything. It's just a markup language that can be used to describe what should be where on the webpage when browser renders it. Particularly, <form></form> and <input></input> tags are used to describe forms. HTML by itself is completely static. For anything dynamic (say, evaluating conditions) you need to add a programming language, most commonly PHP and/or JS.

Second, your questions sound to broad. If your code works, you probably should just leave it untouched. :) If it doesn't, then what exactly goes wrong?

This ^^. Your page that you created (I haven't tested it) is full of javascript. That is what is handling the form in the browser. All of your variables, functions, and if statements are javascript. Not html. The html is just the visual formatting of the page not the script backend.

---

### Post by greenpeace on 2013-03-14
The validation routine is a JavaScript function called "validateForm".

Now have a look at the last <input> in the <form>... specifically where it says: "**onclick="return validateForm();**".  That's how the validation routine is being called.  If it returns "false" the form won't be forwarded to what is set as the "action" attribute on the <form> :

[HTML]<form name="ExamEntry" method="post" action="success.html">[/HTML]

Hope that helps!


To improve your understanding, try changing things on the page and opening it in your browser, and never ever stop reading  :)  Also, get a good text editor which will tell you when things are wrong, or weird.

Good luck!
Gp

---

