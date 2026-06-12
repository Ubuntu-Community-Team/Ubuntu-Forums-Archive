---
title: "Setting JavaScript &lt;select&gt; list index w/ php"
date: 2009-07-16
forum: Programming Talk
---

### Post by DFHIII on 2009-07-16
I have a drop-down list on a form created with JavaScript.  How can I set the selectIndex for that list using php?  I can save the previous user selection using a session variable.  When the user returns to this form I would like to be able to set the index to his previous selection before the form is displayed.

Any help would be appreciated.

Thanks,

Dan H.

---

### Post by Tibuda on 2009-07-16
Generate the JavaScript from PHP.

---

### Post by smartbei on 2009-07-16
What you want to do is stick the word 'selected' inside the <option>. It would look like this:
```

<select name="example">
<option value="opt1">OPT1</option>
<option value="opt2" selected>OPT2</option>
<option value="opt3">OPT3</option>
</select>

```
when this is rendered by the browser, the default selected value will be OPT2, just as you want.

As for how this should be done - that depends entirely on your javascript. I am sure there is a way this could be done relatively simply.

---

### Post by DFHIII on 2009-07-17
Thanks for the hint.  It works very well.  I pass the $q_type as a parameter to the function and use it to insert "selected" at the proper option.  The code segment is as follows:

 <div id=main>
 <form name="frmUpdateQuestion" method=post action="update_question.php">
Question Type: 
  <select name="QType" size=1>
  <option value=0>select one
  <option value=1 <?php if($q_type == 1) echo 'selected'?> >Multiple Choice?
  <option value=2 <?php if($q_type == 2) echo 'selected'?> >Key Answer
  </select>
<br><br>

Dan H.

---

### Post by enz1m3 on 2009-07-19
Just a remark:

I see you're using HTML 4, you should consider using proper XHTML 1.0 and comply to W3C standards to make it a better web for everyone out there ;)

[http://www.w3.org/MarkUp/2004/xhtml-faq](http://www.w3.org/MarkUp/2004/xhtml-faq)

---

### Post by ebharv on 2009-07-21
> <div id=main>
 <form name="frmUpdateQuestion" method=post action="update_question.php">
Question Type: 
  <select name="QType" size=1>
  <option value=0>select one
  <option value=1 <?php if($q_type == 1) echo 'selected'?> >Multiple Choice?
  <option value=2 <?php if($q_type == 2) echo 'selected'?> >Key Answer
  </select>
<br><br>

Change the php code to 
```
<?php if($q_type == 1) echo 'selected="selected"; ?>
```

if you want your HTML to be valid. You can check [COLOR=SeaGreen]**HTML  **[COLOR=Black]errors with the [w3c validation service]("http://validator.w3.org/").[/COLOR][/COLOR]

---

### Post by Mirge on 2009-07-21
> **DFHIII said:**
> Thanks for the hint.  It works very well.  I pass the $q_type as a parameter to the function and use it to insert "selected" at the proper option.  The code segment is as follows:

 <div id=main>
 <form name="frmUpdateQuestion" method=post action="update_question.php">
Question Type: 
  <select name="QType" size=1>
  <option value=0>select one
  <option value=1 <?php if($q_type == 1) echo 'selected'?> >Multiple Choice?
  <option value=2 <?php if($q_type == 2) echo 'selected'?> >Key Answer
  </select>
<br><br>

Dan H.

Sometimes I use something similar for pre-populating forms (ie: error handling) that I find a little easier than the above technique. Take it or leave it.

```

$html = <<<EOT
<select name="QType" size="1">
<option value="0">Select One</option>
<option value="1">Multiple Choice?</option>
<option value="2">Key Answer</option>
</select>
EOT;

$html = str_replace("<option value=\"$q_type\"", "<option value=\"$q_type\" selected", $html);
print $html;

```

This will look for the selected value, and insert "selected" where appropriate. Especially useful for longer SELECT tags, ie: list of states or countries. You don't have to put an if() statement in each option.

---

