---
title: "Describe how this HTML code produces the form displayed in the browser?"
date: 2014-03-10
forum: Programming Talk
---

### Post by jacob27 on 2014-03-10
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000][FONT="Arial"]Describe how this HTML code below produces the form displayed in the browser? Any Ideas?
Thanks
Jacob [/FONT]
<head>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<title>Exam entry</title>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<script language=”javascript” type=”text/javascript”>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000][/COLOR][/FONT] 
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]function validateForm() {[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][CENTER][CENTER][FONT="Courier New"][SIZE=3][COLOR=#000000]var result = true;[/COLOR][/SIZE][/FONT][/CENTER][/CENTER][FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]var msg=””;[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]if (document.ExamEntry.name.value==””) { msg+=”You must enter your name \n”; document.ExamEntry.name.focus(); document.getElementById(‘name’).style.color=”red”; result = false;[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]}[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Calibri"]
[COLOR=#000000] [/COLOR][/FONT][FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]if (document.ExamEntry.subject.value==””) { msg+=”You must enter the subject \n”; document.ExamEntry.subject.focus(); document.getElementById(‘subject’).style.color=”red”; result = false;[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]}[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]if(msg==””){[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]return result;[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT="Courier New"]}[/FONT][FONT="Courier New"][/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]{ alert(msg) return result;[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]}[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][SIZE=3][COLOR=#000000][FONT="Courier New"]}[/FONT][FONT="Courier New"][/FONT][/COLOR][/SIZE]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</script>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</head>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<body>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<h1>Exam Entry Form</h1>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<form name=”ExamEntry” method=”post” action=”success.html”>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<table width=”50%” border=”0”>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td id=”name”>Name</td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td><input type=”text” name=”name” /></td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td id=”subject”>Subject</td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td><input type=”text” name=”subject” /></td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td><input type=”submit” name=”Submit” value=”Submit” onclick=”return validateForm();” /></td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]<td><input type=”reset” name=”Reset” value=”Reset” /></td>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</tr>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][COLOR=#000000] [/COLOR][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</table>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</form>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT="Courier New"][SIZE=3][COLOR=#000000]</body>[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]

---

### Post by jacob27 on 2014-03-10
[FONT="Arial"][COLOR=#000000]Describe how the JavaScript function below performs the validation check? Any Ideas?
Thanks Jacob
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<head>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<title>Exam entry</title>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<script language=”javascript” type=”text/javascript”>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]function validateForm() {[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][CENTER][CENTER][FONT="Courier New"]var result = true;[/FONT][/CENTER][/CENTER][FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]var msg=””;[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]if (document.ExamEntry.name.value==””) { msg+=”You must enter your name \n”; document.ExamEntry.name.focus(); document.getElementById(‘name’).style.color=”red”; result = false;[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]}[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Calibri"]
 [/FONT][FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]if (document.ExamEntry.subject.value==””) { msg+=”You must enter the subject \n”; document.ExamEntry.subject.focus(); document.getElementById(‘subject’).style.color=”red”; result = false;[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]}[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]if(msg==””){[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]return result;[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]}[/FONT][FONT="Courier New"][/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]{ alert(msg) return result;[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]}[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]}[/FONT][FONT="Courier New"][/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</script>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</head>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<body>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<h1>Exam Entry Form</h1>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<form name=”ExamEntry” method=”post” action=”success.html”>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<table width=”50%” border=”0”>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td id=”name”>Name</td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td><input type=”text” name=”name” /></td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td id=”subject”>Subject</td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td><input type=”text” name=”subject” /></td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td><input type=”submit” name=”Submit” value=”Submit” onclick=”return validateForm();” /></td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]<td><input type=”reset” name=”Reset” value=”Reset” /></td>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</tr>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT=Calibri] [/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</table>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</form>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][FONT="Courier New"]</body>[/FONT]
[FONT=Times New Roman][SIZE=3]  [/SIZE][/FONT][/COLOR][/FONT]

---

### Post by ofnuts on 2014-03-10
Is this cheating on homework/exam?

---

### Post by ofnuts on 2014-03-10
Is this cheating on homework/exam?

---

### Post by Elfy on 2014-03-10
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you.

Closed.

When you need hints only - let me know and I will open it again.

---

### Post by bapoumba on 2014-03-10
Sorry to post in a closed thread. The dup thread has been merged in.

---

