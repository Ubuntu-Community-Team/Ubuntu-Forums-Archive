---
title: "changing from check box to radio"
date: 2008-10-10
forum: Programming Talk
---

### Post by oneadvent on 2008-10-10
can i change this checkbox to two radio buttons, one that is of and one that is on?

Thanks, sorry i just dont know much about how java works.

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Frameset//EN">
<HTML>

<HEAD>
<META HTTP-EQUIV="expires" CONTENT="0">
<META HTTP-EQUIV="Pragma" CONTENT="no-cache">
<META HTTP-EQUIV="Cache-Control" CONTENT="no-cache">
<META NAME="ROBOTS" CONTENT="NONE">
<META NAME="ROBOTS" CONTENT="NOINDEX,NOFOLLOW">
<TITLE>Trigger</TITLE>
<SCRIPT Language="JavaScript">

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

function SaveStatus(){
	document.forms[0].ConditionSave.value = '1';
	document.forms[0].submit();
}
// -->

</SCRIPT>



</HEAD>



<BODY bgcolor="#333333" TEXT="#FFFFFF" LINK="#0000FF" VLINK="#0000FF" ALINK="#0000FF">



<FORM METHOD="POST" ACTION="http://68.157.251.100/CgiImageTransfer">



<INPUT TYPE="HIDDEN" NAME="Language" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="Page" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="TaskId" VALUE="2">

<INPUT TYPE="HIDDEN" NAME="MessageMode" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartTue" VALUE="4">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartThu" VALUE="16">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartFri" VALUE="32">

<INPUT TYPE="HIDDEN" NAME="PrimaryTimeMode" VALUE="86399999">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartAMPM" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartHour" VALUE="12">

<INPUT TYPE="HIDDEN" NAME="PrimaryStartMin" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="PrimaryStopAMPM" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryStopHour" VALUE="11">

<INPUT TYPE="HIDDEN" NAME="PrimaryStopMin" VALUE="59">

<INPUT TYPE="HIDDEN" NAME="PrimaryResolution" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryQuality" VALUE="8">

<INPUT TYPE="HIDDEN" NAME="PrimaryPreIntervalNum" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryPreIntervalPer" VALUE="1000">

<INPUT TYPE="HIDDEN" NAME="PrimaryPreNum" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryPreEnable" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryPostNum" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryPostEnable" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="SensorIgnoreTime" VALUE="10">

<INPUT TYPE="HIDDEN" NAME="PrimaryPostIntervalNum" VALUE="1">

<INPUT TYPE="HIDDEN" NAME="PrimaryPostIntervalPer" VALUE="1000">

<INPUT TYPE="HIDDEN" NAME="TransferMode" VALUE="48">

<INPUT TYPE="HIDDEN" NAME="TransferMailServer" VALUE="smtp.east.cox.net">

<INPUT TYPE="HIDDEN" NAME="TransferSMTPPortNo" VALUE="25">

<INPUT TYPE="HIDDEN" NAME="TransferPopServer" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferAuth" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="TransferPOP3PortNo" VALUE="110">

<INPUT TYPE="HIDDEN" NAME="TransferPopID" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferSMTPID" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferPopPassword" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferSMTPPassword" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferMailFrom" VALUE="oneadvent@gmail.com">

<INPUT TYPE="HIDDEN" NAME="TransferMailTo1" VALUE="8502925075@tmomail.net">

<INPUT TYPE="HIDDEN" NAME="TransferMailTo2" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferMailTo3" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferMailSubject" VALUE="">

<INPUT TYPE="HIDDEN" NAME="TransferMailText" VALUE="">

<INPUT TYPE="HIDDEN" NAME="Position" VALUE="255">

<INPUT TYPE="HIDDEN" NAME="MessageMode" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="MessageMailServer" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageSMTPPortNo" VALUE="25">

<INPUT TYPE="HIDDEN" NAME="MessagePopServer" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageAuth" VALUE="0">

<INPUT TYPE="HIDDEN" NAME="MessagePOP3PortNo" VALUE="110">

<INPUT TYPE="HIDDEN" NAME="MessagePopID" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageSMTPID" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessagePopPassword" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageSMTPPassword" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailFrom" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailTo1" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailTo2" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailTo3" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailSubject" VALUE="">

<INPUT TYPE="HIDDEN" NAME="MessageMailText" VALUE="">

<INPUT TYPE="HIDDEN" NAME="ClearImage" VALUE="">

<INPUT TYPE="HIDDEN" NAME="ConditionSave" VALUE="">

<table width=630 cellSpacing=0 cellPadding=0 border=0>

	<TR>

		<TD align=center>

			<font face="Arial" style="font-size: 28px" color="#9F1A1A"><b>Turn Off and On</b></font>

		</TD>

	</TR>

	<TR><TD>&nbsp;</TD></TR>

	<TR><TD><HR></TD></TR>

	<TR><TD>&nbsp;</TD></TR>

</TABLE>



<table width=630 cellSpacing=0 cellPadding=0 border=0>

	

	<TR>

		<td width=210 valign=TOP>

			<table width=420 cellSpacing=2 cellPadding=3 border=0>



				<TR>

					

				</TR>

				<TR>

					<td width=10></td>

					<TD colspan=2 bgcolor=#333333>

						**<input type="checkbox" name="TaskEnable" checked>**

						<font face="Arial" style="font-size: 15px" color="#FFFFFF">Check for On, Uncheck for off</font>

					</TD>

				</TR>

				<TR>

					<td width=10></td>

					<TD  bgcolor=#333333 WIDTH=190>

						<TABLE cellspacing=0 cellpadding=0>

							<TR>

								<TD width=25><BR></TD>

								<TD>

									

						</SELECT>

					</TD>

				</TR>

			</TABLE>

		</TD>



		<td width=210 valign=TOP>

			<table cellSpacing=2 cellPadding=5 border=0>

				<TR>

					<TD>

						<font face="Arial" style="font-size: 11px" color="#000000"><BR>

						</font>

					</TD>

				</TR>

			</TABLE>

		</TD>

	</TR>

</TABLE>



<table width=630 cellSpacing=2 cellPadding=3 border=0>

	

</TABLE>

<table width=630 cellSpacing=2 cellPadding=3 border=0>
<tr><td><hr></td></tr>
<tr><td align=center bgcolor='#333333'>


		

		<input type="button" name="Save" value="    Save    " onClick="JavaScript:SaveStatus();">

		<input type="button" name="Cancel" value="   Cancel   " onClick="JavaScript:ClickCancel();">

</td></tr>
</table>




</FORM>



</BODY>

</HTML>

```

---

### Post by Rich78 on 2008-10-10
Just replace:

<input type="checkbox" name="TaskEnable" checked>

with:

<input type="radio" name="TaskEnable" group="tasks" value="Enable" checked> Enable<br>
<input type="radio" name="TaskDisable" group="tasks" value="Disable"> Disable

---

### Post by LaRoza on 2008-10-10
Where is the Java?

---

### Post by Rich78 on 2008-10-10
> **LaRoza said:**
> Where is the Java?

<SCRIPT Language="JavaScript">

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

:) :) 

But I know what you mean.

---

### Post by oneadvent on 2008-10-10
Sorry again guys, this just isn't my forte. I am trying to make the page simple for my wife.

The above code worked great, however, if I click the Disable the dot doesn't move from the Enable, it just hangs out up there, so they are both selected.

Thanks again!

---

