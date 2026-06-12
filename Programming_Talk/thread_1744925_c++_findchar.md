---
title: "c++ find::char *"
date: 2011-04-30
forum: Programming Talk
---

### Post by highspider on 2011-04-30
what method in c++ should i use for searching a char *.

[COLOR=Red]PLEASE DON NOT TELL ME TO USE A STRING! or STRING FIND[/COLOR]

I have multiply pages of data large mb's from libcurl passed to a  many char *'s 

I want to search for things on the page like 

type  |  var        | contents 
char * page234 [<h1>cost this week</h1><p>$500</>]

and return 500.  while using only a char *

---

### Post by Arndt on 2011-04-30
> **highspider said:**
> what method in c++ should i use for searching a char *.

[COLOR=Red]PLEASE DON NOT TELL ME TO USE A STRING! or STRING FIND[/COLOR]

I have multiply pages of data large mb's from libcurl passed to a  many char *'s 

I want to search for things on the page like 

type  |  var        | contents 
char * page234 [<h1>cost this week</h1><p>$500</>]

and return 500.  while using only a char *

I see where it says 500, but what is the search criterion?

---

### Post by highspider on 2011-04-30
one of many pages like this example

a html web page 
 kind of a phrasing if you would.


<b>Product Description</b>
<br>[COLOR=Red]1" COPPER TUBE CAP[/COLOR]</td>
</b> $&nbsp;[COLOR=Red]11.770[/COLOR]&nbsp;ea<br>
<b>Your Price:</b> $&nbsp;[COLOR=Red]2.319[/COLOR]&nbsp;ea
 <tr><td><b>Total Availability:</b> [COLOR=Red]82[/COLOR]&nbsp;ea</td></tr>
     

here is the libcurl char * of the html page 
example of var char * page 
```

<!--** Version# 2 - 02/10/2002 - 10:41pm - ZACHW - develop -->
<!--** ECLIPSE WEB.FORMS~WOEB.MAIN.HTML -- Main Page **-->
<html>
  <!--** Version# 7 - 05/18/2007 - 07:17pm - RYANB - main -->
<head>
<title>XXXXXXXXXXXXXXXXXXXX</title>

<link href="[/WOEB/css/woe.css]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/css/woe.css")" rel=stylesheet>
<!--** Version# 9 - 10/27/2003 - 04:39pm - AKAUPISC develop -->
<style type="text/css">
#dropmenudiv{
position:absolute;
border:1px solid black;
border-bottom-width: 0;
line-height:18px;
z-index:100;
}
#dropmenudiv a{
width: 100%;
display: block;
text-indent: 3px;
border-bottom: 1px solid black;
padding: 1px 0;
text-decoration: none;
font-weight: bold;
color: white;
background-color: &BG.COLOR&;
}
#dropmenudiv a:hover{ /*hover background color*/
background-color: &BG.HIGHLIGHT&;
color: white;
}
.menuBar{
background-color: black;
color: white;
text-decoration: none;
font-weight: bold;
}
.menuBar a:hover{
background-color: &BG.COLOR&;
}
.menuBar a:visited{
color: white;
}
</style>
<script>
var myAccount='';
var myProdGroups='';
var myCarts='';
var checkout='';
var logoff='';

/***********************************************
* AnyLink Drop Down Menu- © Dynamic Drive ([www.dynamicdrive.com]("http://www.dynamicdrive.com"))
* This notice MUST stay intact for legal use
* Visit [http://www.dynamicdrive.com/](http://www.dynamicdrive.com/) for full source code
***********************************************/

function delayhidemenu(){
 //this space intentionally left blank.
}

function dropdownmenu(obj, e, menucontents, menuwidth){
 //this space intentionally left blank.
}

function verifySubmit(){
          msg = "Your order will be submitted.\nClicking this button a second time may result in a duplicate order.\nContinue?";
          return confirm(msg)
}
function enlarge(which,e){
  //Render image code for IE 4+
  if (document.all){
    if (showimage.style.visibility=="hidden"){
      showimage.style.left=document.body.scrollLeft+event.clientX
      showimage.style.top=document.body.scrollTop+event.clientY
      showimage.innerHTML='<img &ENLG.WIDTH& src="'+which+'" border=1>'
      showimage.style.visibility="visible"
    }else
      showimage.style.visibility="hidden"
      return false
    }
    else if (document.layers){
      if (document.showimage.visibility=="hide"){
        document.showimage.document.write('<a href="#" onMouseover="drag_dropns(showimage)"><img src="'+which+'" border=1></a>')
        document.showimage.document.close()
        document.showimage.left=e.x
        document.showimage.top=e.y
        document.showimage.visibility="show"
      }
      else
        document.showimage.visibility="hide"
        return false
    }
  else
  return true
}
  function checkAll()
  {
     var frm = document.group_detail
     for (var i = 0; i < frm.elements.length; i++)
     {
        var box = frm.elements[i];
        box.checked = frm.allbox.checked;
     }
  }
</script>

<script>
<!--
var trkNo = "J1681049700";
var expireDate = new Date();
expireDate.setTime(expireDate.getTime() + (28800000));
SetCookie("trackno",trkNo,expireDate,"/");
function SetCookie (name,value,expires,path,domain,secure) {document.cookie = name + "=" + escape (value) +
((expires) ? "; expires=" + expires.toGMTString() : "") +
((path) ? "; path=" + path : "") +
((domain) ? "; domain=" + domain : "") +
((secure) ? "; secure" : "");
}
// -->
</script>
</head>

<body leftmargin=0 rightmargin=0 topmargin=0 bottommargin=0 marginheight=0 marginwidth=0>
<div id="showimage" style="position:absolute;visibility:hidden"></div>
  <!--** Version# 20 - 05/18/2007 - 07:17pm - RYANB - main -->
<!--** ECLIPSE WEB.FORMS~WOEB.TOP.NAV -- Main Top Nav **-->

<body leftmargin=0 rightmargin=0 topmargin=0 bottommargin=0 marginheight=0 marginwidth=0>

<table class="menuBar" cellpadding=0 cellspacing=4 width="720">
  <tr class="menuBar">
    <td width="100" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700")"                                  class="menuBar" onMouseover="dropdownmenu(this, event, mainMenu,  '175px')"    onMouseout="delayhidemenu()">Main</a></td>
    <td width="100" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.ACCT.MAINT]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.ACCT.MAINT")"   class="menuBar" onMouseover="dropdownmenu(this, event, myAccount, '175px')"    onMouseout="delayhidemenu()">My Account</a></td>
    <td width="150" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.GROUP.MAINT]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.GROUP.MAINT")"  class="menuBar" onMouseover="dropdownmenu(this, event, myProdGroups, '175px')" onMouseout="delayhidemenu()">My Product Groups</a></td>
    <td width="100" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.CART.MAINT]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.CART.MAINT")"   class="menuBar" onMouseover="dropdownmenu(this, event, myCarts, '175px')"      onMouseout="delayhidemenu()">My Carts</a></td>
    <td width="100" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.ORDER.REVIEW]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.ORDER.REVIEW")" class="menuBar" onMouseover="dropdownmenu(this, event, checkout, '175px')"     onMouseout="delayhidemenu()">Checkout</a></td>
    <td width="100" align="center"><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.LOGOFF]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&TRACKNO=J1681049700&DISP.ID=WEBDISP.WOE.LOGOFF")"       class="menuBar" onMouseover="dropdownmenu(this, event, logoff, '120px')"       onMouseout="delayhidemenu()">Logoff</a></td>
  </tr>
</tr>
</table>

<script language="JavaScript" type="text/javascript">
<!--
function openUp(href)
{
  window.open(href,"","height=400,width=630,scrollbars=yes,resizable");
}
//-->
</script>

<table border="0" cellpadding="0" cellspacing="0" width="720">
  <tr>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
    <td>
      <table border="0" cellpadding="0" cellspacing="0" width="100%">
        <tr>
          <td class="logo" rowspan="3" width="150"><img src="[/WOEB/images/logo.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/logo.gif")" width="150" height="70"></td>
          <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
          <td class="topnav" align="center" valign="middle" width=100%><table border=0 cellpadding=0 cellspacing=0 width=100%><tr><td valign="top"><table border="0" cellpadding="5" cellspacing="0"><tr><td class="topnav" valign="top"><a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700")">Shipping Address</a> <a href="[/WOEB/help/shippingInfo.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/shippingInfo.html")" onClick="openUp(this.href);return false;"><img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" border=0></a><br>20658 BRINSON BLVD<br>BEND, OR 97701</tr></table></td><td valign="top"><table border="0" cellpadding="5" cellspacing="0" width=100%><tr><td class="topnav" valign="top"><a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700")">Shipping Info</a> <a href="[/WOEB/help/shippingInfo.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/shippingInfo.html")" onClick="openUp(this.href);return false;"><img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" border=0></a><br>Ship Via : BID BID ONLY<br>Ship Date : 04/30/2011</td></tr></table></td><td valign="top"><table border="0" cellpadding="5" cellspacing="0" width=100%><tr><td class="topnav" valign="top"><a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SHIP.INFO&TRACKNO=J1681049700")">Required Info</a> <a href="[/WOEB/help/shippingInfo.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/shippingInfo.html")" onClick="openUp(this.href);return false;"><img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" border=0></a><br>Required Date : 04/30/2011<br>Required Info : <b>PO #</b><br>
<b>Ordered By</b><br></td></tr></table></td><td valign="top"><table border="0" cellpadding="5" cellspacing="0"><tr><td class=topnav valign=top><a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.ORDER.REVIEW&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.ORDER.REVIEW&TRACKNO=J1681049700")">Shopping Cart</a> <a href="[/WOEB/help/checkout.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/checkout.html")" onClick="openUp(this.href);return false;"><img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" border=0></a><br>Items in Cart : 0<br>Subtotal : $ 0.00</td></tr></table></td></tr></table> </td>
        </tr>

        <tr>
          <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
          <td class="lightline" width="100%" height="1"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
        </tr>
        <tr>
          <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
          <td class="topnav" valign="top" align="center" width=100%>
            <table border=0 cellpadding=0 cellspacing=0 width=100%>
              <tr>
                <td>
                  <table border=0 cellpadding=0 cellspacing=3>
                    <form action="/eserv/eclipse.ecl" method="POST">
                    <input type="hidden" name="PROCID" value="WEBPROC.WOEB.MAIN">
                    <input type="hidden" name="TRACKNO" value="J1681049700">
                    <tr>
                      <td class="searchbox" valign="middle">
                      <a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SEARCH&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.SEARCH&TRACKNO=J1681049700")">Search</a></td>
                      <td align="bottom"><a href="[/WOEB/help/search.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/search.html")" title="Click for Help" onclick="openUp(this.href);return false;">
                      <img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" alt="Help" border=0 height=11 width=11></a></td>
                      <td><input type=text size=11 name="SEARCH" value=""></td>
                      <td><input type=image src="[/WOEB/images/go.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/go.gif")" border=0></td>
                    </tr>
                    </form>
                  </table>
                </td>

                <td><a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&MISC.ID=REORDER&CLEV=4&PLEV=1&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&MISC.ID=REORDER&CLEV=4&PLEV=1&TRACKNO=J1681049700")">Reorder Pad</a></td><td><a href="[/WOEB/help/reorder.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/reorder.html")" title="Click here for Help" class="header" onclick="openUp(this.href);return false;"><img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" alt="Help" border=0 height=11 width=11></a></td>

                <td align="right">
                  <table border=0 cellpadding=0 cellspacing=3>
                    <form action="/eserv/eclipse.ecl" method="POST">
                    <input type="hidden" name="PROCID" value="WEBPROC.WOEB.MAIN">
                    <input type="hidden" name="TRACKNO" value="J1681049700">
                    <tr>
                      <td class="searchbox" valign="middle">
                      <a class="header" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.QUICKPAD&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.QUICKPAD&TRACKNO=J1681049700")">Quickpad</a></td>
                      <td><a href="[/WOEB/help/quickpad.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/quickpad.html")" title="Click here for Help" class="header" onclick="openUp(this.href);return false;">
                      <img src="[/WOEB/help/images/help2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2.gif")" alt="Help" border=0 height=11 width=11></a></td>
                      <td><input type=text size=3 name="PN1" value="Part#1" onfocus="if (this.value=='Part#1') {this.value=''}" onblur="if (this.value=='') {this.value='Part#1'}"></td>
                      <td><input type=text size=3 name="PN2" value="Part#2" onfocus="if (this.value=='Part#2') {this.value=''}" onblur="if (this.value=='') {this.value='Part#2'}"></td>
                      <td><input type=text size=3 name="PN3" value="Part#3" onfocus="if (this.value=='Part#3') {this.value=''}" onblur="if (this.value=='') {this.value='Part#3'}"></td>
                      <td><input type=image src="[/WOEB/images/go.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/go.gif")" border=0></td>
                    </tr>
                    </form>
                  </table>
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
  </tr>

  <tr>
    <td class="darkline" colspan=3><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
  </tr>
</table>

  
  
  <!--** Version# 10 - 04/30/2002 - 04:42pm - DUSTINM - develop -->
<!--** ECLIPSE WEB.FORMS~WOEB.LEFT.NAV -- Main Left Nav **-->
<table border="0" cellpadding="0" cellspacing="0" width="720">
  <tr>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1" border=0 alt=""></td>
    <td>
      <table border=0 cellpadding=0 cellspacing=0 width=100%>
        <tr>
          <td class="leftnav" valign="top" width=150 height=350>
            <table border="0" cellpadding="0" cellspacing="0" width="150">
              <tr>
                <td class="leftnavbox" width=100% height=22>&nbsp;<b>Products</b></td>
              </tr>

              <tr>
                <td width=100% nowrap>
                  <table border="0" cellpadding="0" cellspacing="0" width=100%>
                    <tr>
                      <td class="leftnav"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="5" height="1"></td>
                      <td width=100%><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width=1 height=5 alt="" border=0><br><a class="leftnavlink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=1&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=1&CLEV=MORE&TRACKNO=J1681049700")">Plumbing Fixtures</a><br>
<img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width=1 height=5 alt="" border=0><br><a class="leftnavlink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=18&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=18&CLEV=MORE&TRACKNO=J1681049700")">Kitchen and Bath Faucets</a><br>
<img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width=1 height=5 alt="" border=0><br><a class="leftnavlink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=36&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=36&CLEV=MORE&TRACKNO=J1681049700")">Bradford White Heaters</a><br>
<img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width=1 height=5 alt="" border=0><br><a class="leftnavlink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&CLEV=MORE&TRACKNO=J1681049700")">Pipe Valves and Fittings</a><br></td>
                    </tr>
                  </table>
                </td>
              </tr>
            </table>
          </td>
          <td class="darkline" width=1><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1" border=0 alt=""></td>
  <!--** Version# 5 - 07/26/2001 - 12:42pm - ZACHW - develop -->
          <td width=100% valign="top">
            <table border=0 cellpadding=0 cellspacing=0 width=100%>
              <tr>
                <td width=100%>
                  <table border=0 cellpadding=3 cellspacing=0 width=100%>
                    <tr>
                      <td class="breadcrumbrow" height=22><img src="[/WOEB/images/triangle.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/triangle.gif")" width=10 height=9 alt=""><a class="breadcrumblink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&CLEV=MORE&TRACKNO=J1681049700")">&nbsp;Pipe Valves And Fittings</a>
<img src="[/WOEB/images/triangle.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/triangle.gif")" width=10 height=9 alt=""><a class="breadcrumblink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&ID~2=53&CLEV=MORE&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&ID%7E2=53&CLEV=MORE&TRACKNO=J1681049700")">&nbsp;Copper Pipe And Fittings</a>
<img src="[/WOEB/images/triangle.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/triangle.gif")" width=10 height=9 alt=""><a class="breadcrumblink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&ID~2=53&ID~3=55&CLEV=4&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&ID%7E2=53&ID%7E3=55&CLEV=4&TRACKNO=J1681049700")">&nbsp;Copper Fittings</a>
                      <img src="[/WOEB/images/triangle.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/triangle.gif")" width=10 height=9 alt="">&nbsp;Part #8577</td>
                    </tr>

                    <tr>
                      <td class="items" width=100%><table border=0 cellspacing=0 cellpadding=0 width=100%><tr><td class="items">  <table border=0 cellspacing=0 cellpadding=0>    <tr><td class="items" align="center" nowrap><a class="itemslink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&ID~2=53&ID~3=55&CLEV=5&PLEV=1&QLEV=1&PN=92886&ITEM.NO=1&PN.CT=438&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&ID%7E2=53&ID%7E3=55&CLEV=5&PLEV=1&QLEV=1&PN=92886&ITEM.NO=1&PN.CT=438&TRACKNO=J1681049700")">&nbsp;&nbsp;<<&nbsp;&nbsp;</a></td><td class="items" align="center">&nbsp;<b>Item&nbsp;2&nbsp;of&nbsp;438</b>&nbsp;</td><td class="items" align="center" nowrap><a class="itemslink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID~1=48&ID~2=53&ID~3=55&CLEV=5&PLEV=1&QLEV=1&PN=14073&ITEM.NO=3&PN.CT=438&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&ID%7E1=48&ID%7E2=53&ID%7E3=55&CLEV=5&PLEV=1&QLEV=1&PN=14073&ITEM.NO=3&PN.CT=438&TRACKNO=J1681049700")">&nbsp;&nbsp;>>&nbsp;&nbsp;</a></td></tr>  </table></td><td class="items" align="right" width="33%"><a href="[/WOEB/help/moreinfo.html]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/moreinfo.html")" onclick="openUp(this.href);return false;">More Information Help <img src="[/WOEB/help/images/help2-alt2.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/help/images/help2-alt2.gif")" border="0" height="11" width="11" alt="Click here for help"></a></td></tr></table></td>
                    </tr>
                  </table>
                </td>
              </tr>

              <tr>
                <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
              </tr>

              <tr>
                <td width=560><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="560" height="1" border=0 alt=""></td>
              </tr>

              <tr>
                <td valign="top">
                  <table border=0 cellpadding=3 cellspacing=0 width=100%>
                    <tr>
                      <td class="bodytext" width=100%><!--** Version# 16 - 03/28/2004 - 01:02am - RYANB - develop -->
<form method=post action="/eserv/eclipse.ecl">
<input type="hidden" name="PROCID" value="WEBPROC.WOEB.MORE.INFO">
<input type="hidden" name="TRACKNO" value="J1681049700">
<input type="hidden" name="PN" value="8577">
<input type="hidden" name="UOM" value="ea">
<input type="hidden" name="VAVAIL" value="OFF">
<input type="hidden" name="VCUST" value="OFF">
<input type="hidden" name="VTECH" value="OFF">
<input type="hidden" name="CLEV" value="5">
<input type="hidden" name="PLEV" value="1">
<input type="hidden" name="QLEV" value="1">
<input type="hidden" name="ITEM.NO" value="2">
<input type="hidden" name="PN.CT" value="438">
<input type="hidden" name="ID~1" value="48"><input type="hidden" name="ID~2" value="53"><input type="hidden" name="ID~3" value="55">
<input type="hidden" name="BANNERID" value="">

<table border=0 cellpadding=3 cellspacing=0 width=100%>
  <tr>
    <td align="center" valign="top" width=100%>
      <table border="0" cellpadding="3" cellspacing="1" width=100%>
        <tr>
          <td><b>Product Description</b>
          <br>1" COPPER TUBE CAP</td>
        </tr>

        <tr>
          <td><b>Retail:</b> $&nbsp;11.770&nbsp;ea<br>
          <b>Your Price:</b> $&nbsp;2.319&nbsp;ea
          
          </td>
        </tr>

        <tr><td><b>Total Availability:</b> 82&nbsp;ea</td></tr>
        

        <tr>
          <td><b>Quantity</b>
          <input type="TEXT" name="QTY" onFocus="javascript: this.select();" value="1" size="4">&nbsp;ea</td>
        </tr>

        <tr>
          <td><input type="image" name="CART.ADD" src="[/WOEB/images/orderaddthis.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/orderaddthis.gif")" border=0 alt=""></td>
        </tr>

        <tr>
          <td>
          <input type="image" name="GROUP.ADD" src="[/WOEB/images/productgroupsaddthis.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/productgroupsaddthis.gif")" border=0 alt="">
          </td>
        </tr>
        
        
        <tr><td><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&VAVAIL=OFF&VTECH=ON&VCUST=OFF&ID~1=48&ID~2=53&ID~3=55&CLEV=5&PLEV=1&QLEV=1&PN=8577&ITEM.NO=2&PN.CT=438&TRACKNO=J1681049700#TECH]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&VAVAIL=OFF&VTECH=ON&VCUST=OFF&ID%7E1=48&ID%7E2=53&ID%7E3=55&CLEV=5&PLEV=1&QLEV=1&PN=8577&ITEM.NO=2&PN.CT=438&TRACKNO=J1681049700#TECH")">View Technical Specifications</a></td></tr>
        <tr><td><a href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&VAVAIL=OFF&VTECH=OFF&VCUST=ON&ID~1=48&ID~2=53&ID~3=55&CLEV=5&PLEV=1&QLEV=1&PN=8577&ITEM.NO=2&PN.CT=438&EXACT.CPN=&TRACKNO=J1681049700#CUSTOM]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOEB.MAIN&VAVAIL=OFF&VTECH=OFF&VCUST=ON&ID%7E1=48&ID%7E2=53&ID%7E3=55&CLEV=5&PLEV=1&QLEV=1&PN=8577&ITEM.NO=2&PN.CT=438&EXACT.CPN=&TRACKNO=J1681049700#CUSTOM")">View Custom Part Numbers and Availability</a></td></tr>
      </table>
    </td>

    <td align="center" valign="top">
      <table border="0" cellpadding="5" cellspacing="0" width=100%>
        <tr>
          <td><b>Product Image</b>
          <br><img width=200 border=0 src="[/WOEB/images/notavailfull.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/notavailfull.gif")"></td>
        </tr>
      </table>
    </td>
    
  </tr>
</table>

<table border=0 cellpadding=3 cellspacing=0 width=100%>
  <tr>
    <td align="center" colspan=2 width=100%>
      <table border="0" cellpadding="3" cellspacing="1" width=100%>
        
        
        
      </table>
    </td>
  </tr>

  <tr>
    <td align="center" valign="middle" colspan=2 width=100%><br><b><u>External Links/Downloadable Files</u></b><br><a target="_blank" href=""></a><br><a target="_blank" href="[http://www.deltafaucet.com/products/]("http://ubuntuforums.org/view-source:http://www.deltafaucet.com/products/")">Delta Faucet WWW Catalog</a><br><a target="_blank" href="[011NI4114_039923.GIF]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/011NI4114_039923.GIF")">ASA PRD IMAGE</a><br><a target="_blank" href="[N2I/N2I_ACR00070_08-02.pdf]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/N2I/N2I_ACR00070_08-02.pdf")">ASA CUT SHEET LINK</a><br><a target="_blank" href="[N2I/N2I_ACR00070_08-02.pdf]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/N2I/N2I_ACR00070_08-02.pdf")">ASA MAIN URL</a><br></td>
  </tr>
  
</table>
</form> </td>
                    </tr>
                  </table>
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
  </tr>
</table>
  <!--** Version# 16 - 09/11/2007 - 03:32pm - RYANB - main -->
<!--** ECLIPSE WEB.FORMS~WOEB.FOOTER -- Main Footer **-->
<table border="0" cellpadding="0" cellspacing="0" width="720">
  <tr>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
    <td>
      <table border=0 cellpadding=0 cellspacing=0 width=100%>
        <tr>
          <td class="leftnav" valign="top" width=150>
            <table border="0" cellpadding="2" cellspacing="0" width="150">
              <tr>
                <td class="topnav">Subscribe here for special<br>e-mail sales & promotions!</td>
              </tr>
              <form method=post action="/eserv/eclipse.ecl">
              <input type="hidden" name="PROCID" value="WEBPROC.WOEB.MAIN">
              <input type="hidden" name="TRACKNO" value="J1681049700">
              <tr>
                <td valign="middle" class="topnav" width=150>
                  <table border="0" cellpadding="0" cellspacing="3">
                    <tr>
                      <td><input maxlength=100 size=11 value="" name="EMAIL" onfocus="if (this.value=='') {this.value=''}" onblur="if (this.value=='') {this.value=''}"></td>
                      <td><input type="image" src="[/WOEB/images/go.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/go.gif")" border=0></td>
                    </tr>
                  </table>
                </td>
              </tr>
              <tr>
                 <td class="topnav"><a class="footerbarlink" href="[/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.POPUP&PRIVACY=YES&TRACKNO=J1681049700]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/eserv/eclipse.ecl?PROCID=WEBDISP.WOE.POPUP&PRIVACY=YES&TRACKNO=J1681049700")" onClick="openUp(this.href);return false;">View our privacy statement</a></td>
              </tr>
              </form>
            </table>
          </td>
          <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
          <td width=100%>
            <table border=0 cellpadding=0 cellspacing=0 width=100%>
              <tr>
                <td bgcolor="#FFFFFF"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="567" height="5"></td>
              </tr>
              <tr align="center" bgcolor="#FFFFFF">
              <td align="center" valign="middle" width="567" height=80><img src="[HTTPS://www.XXXXXXXXXXXXXXX.com/WOEB/images/bannerads/defaultfullbanner.jpg]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/bannerads/defaultfullbanner.jpg")" alt="Front page banner with no link or link to URL/Product group" border=0> </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
  </tr>

  <tr>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
    <td class="footerbar">
      <table border=0 cellpadding=0 cellspacing=0 width=100%>
        <tr>
          <td class="footerbar" width=150 align="center" height=25>
          <script language="javascript">
          <!--
          if(document.images)
          {
            image11 = new Image;
            image12 = new Image;

            image11.src = "/WOEB/images/eclipse.gif";
            image12.src = "/WOEB/images/eclipseanim.gif";
          }

          function swapOn(imgLocation)
          {
            if(document.images)
            {
              document.images[imgLocation].src = eval(imgLocation + "2.src");
            }
          }

          function swapOff(imgLocation)
          {
            if(document.images)
            {
              document.images[imgLocation].src = eval(imgLocation + "1.src");
            }
          }
          //-->
          </script>

            <table border=0 cellpadding=0 cellspacing=0>
              <tr>
                <td><a class="footerbarlink" href="[http://www.eclipseinc.com]("http://ubuntuforums.org/view-source:http://www.eclipseinc.com/")" title="Supplying all your eCommerce needs" target="_blank">powered by </a></td>
                <td><a class="footerbarlink" href="[http://www.eclipseinc.com]("http://ubuntuforums.org/view-source:http://www.eclipseinc.com/")" onmouseover="swapOn('image1');" onmouseout="swapOff('image1');" target="_blank"><img name="image1" src="[/WOEB/images/eclipse.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/eclipse.gif")" border=0></a></td>
                <td><a class="footerbarlink" href="[http://www.eclipseinc.com]("http://ubuntuforums.org/view-source:http://www.eclipseinc.com/")" title="Supplying all your eCommerce needs" target="_blank"> eclipse</a></td>
              </tr>
            </table>
          </td>

          <td class="footerbar" width=568 align="center">Contact the <a class="footerbarlink" href="[EMAIL="webmaster@consolidatedsupply.com"]mailto:webmaster@XXXXXXXXXXXXXXXXXX.com[/EMAIL]"><u>Webmaster</u></a> with questions about this site.  &copy; 2011 XXXXXXXXXXXSupply. All Rights Reserved.</td>
        </tr>
      </table>
    </td>
    <td class="darkline"><img src="[/WOEB/images/spacer.gif]("http://ubuntuforums.org/view-source:https://www.consolidatedsupply.com/WOEB/images/spacer.gif")" width="1" height="1"></td>
  </tr>
</table>
</body>
</html>

```

---

### Post by highspider on 2011-04-30
o sorry on the return 500 i ment the the pages add up to sum like 500 mbs of info 

return 500 was an error 

  I personally blame the (corona) and find no fault  of my own (beer).

---

### Post by dwhitney67 on 2011-04-30
> **highspider said:**
> o sorry on the return 500 i ment the the pages add up to sum like 500 mbs of info 

return 500 was an error 

  I personally blame the (corona) and find no fault  of my own (beer).

Programming a computer to "think" is no different than you doing it yourself.

If there is a particular pattern in the "curl" results that will give you the tell-tale sign of what you are looking for, then I'm certain you can "teach" a computer to find it too.

As for your beer intake, kudos... I have just had my fill too... but will probably have more.

---

### Post by BkkBonanza on 2011-05-01
The typical (char *) string search function is strstr or stristr for simply finding a string in a string.

If you need more complex matches you might look at linking in something like libpcre (regex).

---

### Post by Jonas thomas on 2011-05-01
This kind of project I have on my backburners at the moment.  I've done some preliminary research on this... Seems like the the magic search google search term is "Information Extraction". Go figure...
I found a nice wiki link: [http://en.wikipedia.org/wiki/Information_extraction]("http://en.wikipedia.org/wiki/Information_extraction")

Which took me here:[http://www.gabormelli.com/RKB/Inform...xtraction_Task]("http://www.gabormelli.com/RKB/Inform...xtraction_Task")

Which took me here:
["Information Extraction: Distilling Structured Data from Unstructured Text."]("http://portal.acm.org/citation.cfm?doid=1105664.1105679")

This was a very interesting article on the subject that references an open source procect called lemur/indri.
[http://ciir.cs.umass.edu/~strohman/indri/]("http://ciir.cs.umass.edu/~strohman/indri/")

I don't know if this helps you or not. 
Too early in morning for a cerverza... Need caffination...

---

