---
title: "XMLHttpRequest to post and stay on same page"
date: 2008-10-13
forum: Programming Talk
---

### Post by oneadvent on 2008-10-13
Can someone tell me in English how to make 
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Frameset//EN">
<html><head>
<meta http-equiv="expires" content="0">
<meta http-equiv="Pragma" content="no-cache">
<meta http-equiv="Cache-Control" content="no-cache">
<meta name="ROBOTS" content="NONE">
<meta name="ROBOTS" content="NOINDEX,NOFOLLOW"><title>Turn On/Off Camera</title>

<script language="JavaScript">
<!--
function ImageDelete() {
if (confirm("Are you sure you want to delete?") == false) {
return;
}
document.forms[0].ClearImage.value = '1';
document.forms[0].TransCondition.value = '4';
document.forms[0].submit();
return;
}
function ClickCancel() {
self.location = "http://68.157.251.100/CgiImageTransfer?Page=0&Language=0";
}
function ONStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = true
document.forms[0].submit();
}
function OFFStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = false
document.forms[0].submit();
}
// -->
</script>


<script type="text/javascript">
function ajaxFunction()
{
var xmlHttp;
try
  {
  // Firefox, Opera 8.0+, Safari
  xmlHttp=new XMLHttpRequest();
  }
catch (e)
  {
  // Internet Explorer
  try
    {
    xmlHttp=new ActiveXObject("Msxml2.XMLHTTP");
    }
  catch (e)
    {
    try
      {
      xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
      }
    catch (e)
      {
      alert("Your browser does not support AJAX!");
      return false;
      }
    }
  }
  }
</script>


 


</head>


<body style="color: rgb(255, 255, 255); background-color: rgb(51, 51, 51);" alink="#0000ff" link="#0000ff" vlink="#0000ff">
<center>
<br>
<br>
<br>


<form method="post" action="http://68.157.251.100/CgiImageTransfer">
<input name="Language" value="0" type="hidden">
<input name="Page" value="1" type="hidden">
<input name="TaskId" value="2" type="hidden">
<input name="MessageMode" value="0" type="hidden">
<input name="PrimaryStartTue" value="4" type="hidden">
<input name="PrimaryStartThu" value="16" type="hidden">
<input name="PrimaryStartFri" value="32" type="hidden">
<input name="PrimaryTimeMode" value="86399999" type="hidden">
<input name="PrimaryStartAMPM" value="0" type="hidden">
<input name="PrimaryStartHour" value="12" type="hidden">
<input name="PrimaryStartMin" value="0" type="hidden">
<input name="PrimaryStopAMPM" value="1" type="hidden">
<input name="PrimaryStopHour" value="11" type="hidden">
<input name="PrimaryStopMin" value="59" type="hidden">
<input name="PrimaryResolution" value="1" type="hidden">
<input name="PrimaryQuality" value="8" type="hidden">
<input name="PrimaryPreIntervalNum" value="1" type="hidden">
<input name="PrimaryPreIntervalPer" value="1000" type="hidden">
<input name="PrimaryPreNum" value="1" type="hidden">
<input name="PrimaryPreEnable" value="1" type="hidden">
<input name="PrimaryPostNum" value="1" type="hidden">
<input name="PrimaryPostEnable" value="1" type="hidden">
<input name="SensorIgnoreTime" value="10" type="hidden">
<input name="PrimaryPostIntervalNum" value="1" type="hidden">
<input name="PrimaryPostIntervalPer" value="1000" type="hidden">
<input name="TransferMode" value="48" type="hidden">
<input name="TransferMailServer" value="smtp.east.cox.net" type="hidden">
<input name="TransferSMTPPortNo" value="25" type="hidden">
<input name="TransferPopServer" value="" type="hidden">
<input name="TransferAuth" value="0" type="hidden">
<input name="TransferPOP3PortNo" value="110" type="hidden">
<input name="TransferPopID" value="" type="hidden">
<input name="TransferSMTPID" value="" type="hidden">
<input name="TransferPopPassword" value="" type="hidden">
<input name="TransferSMTPPassword" value="" type="hidden">
<input name="TransferMailFrom" value="oneadvent@gmail.com" type="hidden">
<input name="TransferMailTo1" value="8502925075@tmomail.net" type="hidden">
<input name="TransferMailTo2" value="" type="hidden">
<input name="TransferMailTo3" value="" type="hidden">
<input name="TransferMailSubject" value="" type="hidden">
<input name="TransferMailText" value="" type="hidden">
<input name="Position" value="255" type="hidden">
<input name="MessageMode" value="0" type="hidden">
<input name="MessageMailServer" value="" type="hidden">
<input name="MessageSMTPPortNo" value="25" type="hidden">
<input name="MessagePopServer" value="" type="hidden">
<input name="MessageAuth" value="0" type="hidden">
<input name="MessagePOP3PortNo" value="110" type="hidden">
<input name="MessagePopID" value="" type="hidden">
<input name="MessageSMTPID" value="" type="hidden">
<input name="MessagePopPassword" value="" type="hidden">
<input name="MessageSMTPPassword" value="" type="hidden">
<input name="MessageMailFrom" value="" type="hidden">
<input name="MessageMailTo1" value="" type="hidden">
<input name="MessageMailTo2" value="" type="hidden">
<input name="MessageMailTo3" value="" type="hidden">
<input name="MessageMailSubject" value="" type="hidden">
<input name="MessageMailText" value="" type="hidden">
<input name="ClearImage" value="" type="hidden">
<input name="ConditionSave" value="" type="hidden">




<table border="0" cellpadding="0" cellspacing="0" width="630">
	<tbody>

		<tr>
			<td align="center"> <font style="font-size: 28px;" color="#9f1a1a" face="Arial"><b>Turn
	Off and On</b>
	</font> 	</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
		</tr>

		<tr>
			<td>
			<hr></td>
		</tr>

</tbody>
</table>
<table border="0" cellpadding="0" cellspacing="0" width="630">
	<tbody>
		<tr>
			<td valign="top" width="210">

		<center> </center>
				<table style="width: 609px; height: 29px;" border="0" cellpadding="3" cellspacing="2">
	<tbody>
		<tr>
		</tr>
		<tr>

		<td>

<center>


<input name="ON" value=" ON " onclick="JavaScript:ONStatus();" type="button" style="width: 100px;height:50px"> 


&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp&nbsp


<input name="OFF" value=" OFF " onclick="JavaScript:OFFStatus();" type="button" style="width: 100px;height:50px"> 
</center>
		</tr>
	</tbody>
</table>
<table border="0" cellpadding="3" cellspacing="2" width="630">
</table>
<table style="width: 613px; height: 57px;" border="0" cellpadding="3" cellspacing="2">
	<tbody>

		<tr>
		<hr>
		</tr>

	</tbody>
</table>
</td>
</tr>
</tbody>
</table>
</form>
</body></html>

```

Post to another page but stay on the same page.

It would be cooler if it said "Successful" when it did what it does with the buttons....but not necessary. 

Furthermore I am impressed with anyone that understands AJAX.

---

### Post by rnodal on 2008-10-13
Could you define "post to another page but stay on another page"?

Also, I don't know if you are familiar or but there are many tutorials on AJAX. It is not complicated at all(the concept that is). Here is a tutorial just in case :)

[http://www.w3schools.com/Ajax/Default.Asp]("http://www.w3schools.com/Ajax/Default.Asp")

-r

---

### Post by oneadvent on 2008-10-13
I mean I want the web page to stay up even though the "ON" or "OFF" button was pushed, effectively making the webpage never changing. (Eventually I want to make this a touch screen application for my security system.)

And I read those totorials. I just dont get them. I am aparently too slow.

I can program in php and vb and stuff, so I'm not totally dumb but I just dont see what its doing, or how to make this page do it. I think one application that I am familiar with will help tremendously.

---

### Post by rnodal on 2008-10-14
You are not slow. Here is another link that goes over the concepts of AJAX.
[http://en.wikipedia.org/wiki/AJAX]("http://en.wikipedia.org/wiki/AJAX")

Here is a small text explaining why AJAX is needed for something like what you want to do.

> HTTP is a stateless protocol. The advantage of a stateless protocol is that hosts do not need to retain information about users between requests, but this forces web developers to use alternative methods for maintaining users' states. For example, when a host needs to customize the content of a website for a user, the web application must be written to track the user's progress from page to page. A common method for solving this problem involves sending and receiving cookies. Other methods include server side sessions, hidden variables (when the current page is a form), and URL encoded parameters (such as /index.php?session_id=some_unique_session_code).


Here couple of tutorials with sample code that should get you started.
[http://www.w3schools.com/PHP/php_ajax_database.asp]("http://www.w3schools.com/PHP/php_ajax_database.asp")

[http://www.ajaxf1.com/tutorial/ajax-php.html]("http://www.ajaxf1.com/tutorial/ajax-php.html")

Don't give up.

-r

---

### Post by oneadvent on 2008-10-15
Well I think this is what I need but I dont know:

```
// Get the HTTP Object
function getHTTPObject(){
if (window.ActiveXObject) 
return new ActiveXObject("Microsoft.XMLHTTP");
else if (window.XMLHttpRequest) 
return new XMLHttpRequest();
else {
alert("Your browser does not support AJAX.");
return null;
}
}
// Implement business logic
function doWork(){
httpObject = getHTTPObject();
if (httpObject != null) {
httpObject.open("GET", "/CgiImageTransfer"+document.getElementById('inputText').value, true);
+document.getElementById('inputText').value, true);
httpObject.send(null);
}
}
```

If I put that in my javascript for each submit button would it do it or would I blow my webpage up?

Btw: I have an updated page right now, so we are kept up to date:
```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Frameset//EN">
<html><head>
<meta http-equiv="expires" content="0">
<meta http-equiv="Pragma" content="no-cache">
<meta http-equiv="Cache-Control" content="no-cache">
<meta name="ROBOTS" content="NONE">
<meta name="ROBOTS" content="NOINDEX,NOFOLLOW"><title>Turn On/Off Camera</title>

<script language="JavaScript">
<!--
function OnStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = true
document.forms[0].submit();
}
function OffStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = false
document.forms[0].submit();
}
// -->
</script>


</head>


<body style="color: rgb(255, 255, 255); background-color: rgb(51, 51, 51);" alink="#0000ff" link="#0000ff" vlink="#0000ff">
<center>

<form method="post" action="http://68.157.251.100/CgiImageTransfer">
<input name="Language" value="0" type="hidden">
<input name="Page" value="1" type="hidden">
<input name="TaskId" value="2" type="hidden">
<input name="MessageMode" value="0" type="hidden">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartSun" VALUE="1">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartMon" VALUE="2">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartTue" VALUE="4">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartWed" VALUE="8">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartThu" VALUE="16">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartFri" VALUE="32">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartSat" VALUE="64">
<INPUT TYPE="HIDDEN" NAME="PrimaryTimeMode" VALUE="86399999">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartAMPM" VALUE="0">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartHour" VALUE="12">
<INPUT TYPE="HIDDEN" NAME="PrimaryStartMin" VALUE="0">
<INPUT TYPE="HIDDEN" NAME="PrimaryStopAMPM" VALUE="1">
<INPUT TYPE="HIDDEN" NAME="PrimaryStopHour" VALUE="11">
<INPUT TYPE="HIDDEN" NAME="PrimaryStopMin" VALUE="59">
<input name="PrimaryResolution" value="1" type="hidden">
<input name="PrimaryQuality" value="8" type="hidden">
<input name="PrimaryPreIntervalNum" value="1" type="hidden">
<input name="PrimaryPreIntervalPer" value="1000" type="hidden">
<input name="PrimaryPreNum" value="1" type="hidden">
<input name="PrimaryPreEnable" value="1" type="hidden">
<input name="PrimaryPostNum" value="1" type="hidden">
<input name="PrimaryPostEnable" value="1" type="hidden">
<input name="SensorIgnoreTime" value="10" type="hidden">
<input name="PrimaryPostIntervalNum" value="1" type="hidden">
<input name="PrimaryPostIntervalPer" value="1000" type="hidden">
<input name="TransferMode" value="48" type="hidden">
<input name="TransferMailServer" value="smtp.east.cox.net" type="hidden">
<input name="TransferSMTPPortNo" value="25" type="hidden">
<input name="TransferPopServer" value="" type="hidden">
<input name="TransferAuth" value="0" type="hidden">
<input name="TransferPOP3PortNo" value="110" type="hidden">
<input name="TransferPopID" value="" type="hidden">
<input name="TransferSMTPID" value="" type="hidden">
<input name="TransferPopPassword" value="" type="hidden">
<input name="TransferSMTPPassword" value="" type="hidden">
<input name="TransferMailFrom" value="oneadvent@gmail.com" type="hidden">
<input name="TransferMailTo1" value="8502925075@tmomail.net" type="hidden">
<input name="TransferMailTo2" value="" type="hidden">
<input name="TransferMailTo3" value="" type="hidden">
<input name="TransferMailSubject" value="" type="hidden">
<input name="TransferMailText" value="" type="hidden">
<input name="Position" value="255" type="hidden">
<input name="MessageMode" value="0" type="hidden">
<input name="MessageMailServer" value="" type="hidden">
<input name="MessageSMTPPortNo" value="25" type="hidden">
<input name="MessagePopServer" value="" type="hidden">
<input name="MessageAuth" value="0" type="hidden">
<input name="MessagePOP3PortNo" value="110" type="hidden">
<input name="MessagePopID" value="" type="hidden">
<input name="MessageSMTPID" value="" type="hidden">
<input name="MessagePopPassword" value="" type="hidden">
<input name="MessageSMTPPassword" value="" type="hidden">
<input name="MessageMailFrom" value="" type="hidden">
<input name="MessageMailTo1" value="" type="hidden">
<input name="MessageMailTo2" value="" type="hidden">
<input name="MessageMailTo3" value="" type="hidden">
<input name="MessageMailSubject" value="" type="hidden">
<input name="MessageMailText" value="" type="hidden">
<input name="ClearImage" value="" type="hidden">
<input name="ConditionSave" value="" type="hidden">
<SELECT NAME="TransCondition" style="display:none">
	<OPTION VALUE="4">
</SELECT>
<br>
<br>


<table border="0" cellpadding="0" cellspacing="0" width="630">
	<tbody>
		<tr>
			<td align="center"> <font style="font-size: 28px;" color="#9f1a1a" face="Arial"><b>Turn
	Off and On</b>
	</font> 	</td>
		</tr>
		<tr>
			<td>&nbsp;</td>
		</tr>
		<tr>
			<td>
			<hr></td>
		</tr>

</tbody>
</table>
<table border="0" cellpadding="0" cellspacing="0" width="630">
	<tbody>
		<tr>
			<td valign="top" width="210">
		<center>

		<input name="Save" value=" ON " onclick="JavaScript:OnStatus();" type="button" style="width: 100px;height:50px">

&nbsp&nbsp&nbsp&nbsp

		<input name="Save" value=" OFF " onclick="JavaScript:OffStatus();" type="button" style="width: 100px;height:50px"> 

</center>
				
		
<form>
<input name="TaskEnable" value="Enable" type="radio" style="display:none">

<input name="TaskDisable" value="Disable" type="radio" style="display:none">
</center> </td>
		</tr>
</form>
	</tbody>


<table border="0" cellpadding="0" cellspacing="0" width="630">
	<tbody>
		<tr>
			<td>
			<hr>
			</td>
		</tr>
	</tbody>
</table>
</td>
</tr>
</tbody>
</table>
</form>

</center>
</body></html>
```

---

### Post by oneadvent on 2008-10-15
I have been reading the above tutorials and I still have it doing nothing, and no error saying why.

This is what I have:
```
<script language="JavaScript">
<!--
function ImageDelete() {
if (confirm("Are you sure you want to delete?") == false) {
return;
}
document.forms[0].ClearImage.value = '1';
document.forms[0].TransCondition.value = '4';
document.forms[0].submit();
return;
}
function ClickCancel() {
self.location = "http://68.157.251.100/CgiImageTransfer?Page=0&Language=0";
}
function ONStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = true
{
var xmlHttp;
	{
	// Firefox, Opera 8.0+, Safari
	xmlHttp=new XMLHttpRequest();
	}
}
xmlHttp.onreadystatechange=function()
{
if (xmlHttp.ready&state==4)
	{
	document.myForm.time.value=xmlHttp.responseText;
	}
}
xmlHttp.open("POST","http://oneadvent.viewnetcam.com:50050/CgiImageTransfer",true);
xmlHttp.send()
}


function OFFStatus(){
document.forms[0].ConditionSave.value = '1';
document.forms[0].TaskEnable.checked = false
{
var xmlHttp;
	{
	// Firefox, Opera 8.0+, Safari
	xmlHttp=new XMLHttpRequest();
	}
}
xmlHttp.onreadystatechange=function()
{
if (xmlHttp.ready&state==4)
	{
	document.myForm.time.value=xmlHttp.responseText;
	}
}
xmlHttp.open('POST','http://oneadvent.viewnetcam.com:50050/CgiImageTransfer',false);
xmlHttp.send()
}
function ajaxFunction()
// -->
</script>
```

Can someone nudge me in the right direction please?

---

