---
title: "Describe how this HTML code produces the form displayed in the browser?"
date: 2014-03-10
forum: Programming Talk
---

### Post by jacob27 on 2014-03-10
[SIZE=2]I've got to do some research on the questions below any advice and hints you can give me for I'd be grateful for.
Thanks
Jacob
[/SIZE][SIZE=2][FONT=Arial][COLOR=#000000]Describe how this HTML code produces the form displayed in the browser?[/COLOR][/FONT][/SIZE]
[SIZE=2] 
[/SIZE][SIZE=2][FONT=Arial] 
 
[COLOR=#000000]Describe how the JavaScript function performs the validation check?


[/COLOR][/FONT][/SIZE][SIZE=2][FONT=Arial][COLOR=#000000] 
[/COLOR][/FONT][/SIZE][FONT=Arial][SIZE=3][COLOR=#000000][SIZE=2][FONT=Courier New]<head>[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]<title>Exam entry</title>[/FONT][/SIZE]

[SIZE=2]
[/SIZE][SIZE=2][FONT=Courier New]<script language=”javascript” type=”text/javascript”>[/FONT][/SIZE]

[SIZE=2]
[/SIZE][SIZE=2][FONT=Courier New]function validateForm() {[/FONT][/SIZE]
[CENTER][CENTER][SIZE=2][FONT=Courier New]var result = true;[/FONT][/SIZE][/CENTER]
[/CENTER]
[SIZE=2][FONT=Courier New]var msg=””;[/FONT][/SIZE]

[SIZE=2]
[/SIZE][SIZE=2][FONT=Courier New]if (document.ExamEntry.name.value==””) { msg+=”You must enter your name \n”; document.ExamEntry.name.focus(); document.getElementById(‘name’).style.color=”red”; result = false;[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]}[/FONT][/SIZE][SIZE=2]
[/SIZE] 
[SIZE=2][FONT=Courier New]if (document.ExamEntry.subject.value==””) { msg+=”You must enter the subject \n”; document.ExamEntry.subject.focus(); document.getElementById(‘subject’).style.color=”red”; result = false;[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]}[/FONT][/SIZE] [SIZE=2]

[/SIZE] 
[SIZE=2][FONT=Courier New]if(msg==””){[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]return result;[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]}[/FONT][/SIZE]   [SIZE=2]

[/SIZE] 
[SIZE=2][FONT=Courier New]{ alert(msg) return result;[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]}[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]}[/FONT][/SIZE]   [SIZE=2]

[/SIZE] 
[SIZE=2][FONT=Courier New]</script>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</head>[/FONT][/SIZE]   [SIZE=2]

[/SIZE] 
[SIZE=2][FONT=Courier New]<body>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<h1>Exam Entry Form</h1>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<form name=”ExamEntry” method=”post” action=”success.html”>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<table width=”50%” border=”0”>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<tr>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td id=”name”>Name</td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td><input type=”text” name=”name” /></td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</tr>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<tr>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td id=”subject”>Subject</td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td><input type=”text” name=”subject” /></td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</tr>[/FONT][/SIZE]
[SIZE=2]
[/SIZE] 
[SIZE=2][FONT=Courier New]<tr>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td><input type=”submit” name=”Submit” value=”Submit” onclick=”return validateForm();” /></td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]<td><input type=”reset” name=”Reset” value=”Reset” /></td>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</tr>[/FONT][/SIZE]
[SIZE=2] 
[/SIZE] 
[SIZE=2][FONT=Courier New]</table>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</form>[/FONT][/SIZE]

[SIZE=2][FONT=Courier New]</body>[/FONT][/SIZE]

[/COLOR] 
[/SIZE] 
[/FONT]

---

### Post by bapoumba on 2014-03-10
Please see here : [http://ubuntuforums.org/showthread.php?t=2210391&p=12953049#post12953049](http://ubuntuforums.org/showthread.php?t=2210391&p=12953049#post12953049)

If you want your thread reopened, please ask so with a valid explanation. You can have an Admin have la look if you start a thread in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"), thanks.
Closing again.

---

