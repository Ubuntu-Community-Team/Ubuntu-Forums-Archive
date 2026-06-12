---
title: "javascript works on all but G-chrome -- why?"
date: 2011-04-08
forum: Programming Talk
---

### Post by highspider on 2011-04-08
On Firefox and IExplorer it works perfect; however, Google chrome it limits to 20 chars instead of 800. And I have no Idea why.

[COLOR=Red]RED - Related to code[/COLOR]
```

<html><body>
[COLOR=Red]<script type="text/javascript">
function textCounter(field,cntfield,maxlimit) {
 if (field.value.length > maxlimit) // too-long aka copy-paste trim it
   field.value = field.value.substring(0, maxlimit);
   // otherwise, update 'characters left' counter
 else
   cntfield.value = maxlimit - field.value.length;
}
</script>
[/COLOR] 
<form name="[COLOR=Red]emailform[/COLOR]" id="form_id" method="post" action="cgi-bin/email.pl">

<table>
 <tr><td colspan="2"><label for="MSG">
 <textarea maxlength='20' rows="20" cols="55" id="MSG" name="[COLOR=Red]MSG[/COLOR]" [COLOR=Red]
onKeyDown="textCounter(document.emailform.MSG,document.emailform.remLen1,800)"
onKeyUp="textCounter(document.emailform.MSG,document.emailform.remLen1,800)"[/COLOR]>
</textarea>
You have 
[COLOR=Red]<input readonly type="text" name="remLen1" size="3" maxlength="3" value="800">[/COLOR]
remaining characters. </td></tr>
<tr><td align="center" colspan="2"><input type="submit" value="Submit Message" />
</table></body>
</html>
```What it does its limit to 800 chars for the message so people don't get diarrhea of mouth filling up email messages. 
I'm not the original author I just edited it for my use ~Found on net by: ?~

NOTE: is part of a giant web page but error is still present in the condensed version.

---

### Post by Reiger on 2011-04-08
Well, have you actually looked at your textarea markup? It clearly spells out that the maximum length of the textarea is 20 characters. Try removing it.

---

### Post by highspider on 2011-04-08
Thank You.
 [COLOR=Red]maxlength='20'[/COLOR]
For some reason I missed that --- Grrr
 I thought it was the java and looked past the other code since all 800 chars worked with firefox, seamonkey, and IE. some how the other browser read past that!
THANK YOU

---

