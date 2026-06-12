---
title: "html - tables repeating in firefox?"
date: 2008-02-21
forum: Programming Talk
---

### Post by Mr.popo on 2008-02-21
My html file works perfectly fine in IE but in Firefox It duplicates itself. Please can you help me sort this out. Thanks
screenshot of problem: [http://i111.photobucket.com/albums/n145/generalgfx/Screenshot-4.png](http://i111.photobucket.com/albums/n145/generalgfx/Screenshot-4.png)

Code of html page:
```

<html>
<head>
<style type="text/css">
	img
	{	
		border: none;
	}
	.content
	{
		padding: 30px 30px 20px;
	}
	.nav
	{
		padding: 10px 22px 6px;
		font-size: 12px;
	}
	.mnav
	{	
		border: none;
	}
	/* link styles.. */
	a:link
	{
		color: #000000;
		text-decoration: none;
	}
	a:visited
	{
		color: #000000;
		text-decoration: none;
	}
	a:hover
	{
		color: #FFFFFF;
		text-decoration: none;
	}
</style>
<title> Index </title>
<script src="flash/AC_RunActiveContent.js" type="text/javascript"></script>
</head>
<body background="images/bg.jpg"><table align="center" cellspacing="0" cellpadding="0">

<tr>
<td width="652" ><script type="text/javascript">
AC_FL_RunContent( 'codebase','http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,28,0','width','652','height','69','title','banner','src','flash/banner','quality','high','pluginspage','http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash','movie','flash/banner' ); //end AC code
</script><noscript><object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,28,0" width="652" height="69" title="banner">
  <param name="movie" value="flash/banner.swf">
  <param name="quality" value="high">
  <embed src="flash/banner.swf" quality="high" pluginspage="http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash" type="application/x-shockwave-flash" width="652" height="69"></embed>
</object></noscript></td>
</tr>
<tr>

<td class="mnav"><a href="Index.html"><img src="images/eportfolio-v1_04.gif"></a><a href="Publications.html"><img src="images/eportfolio-v1_05.gif"></a><img src="images/eportfolio-v1_06.gif"><a href="Danceometer development.html"><img src="images/eportfolio-v1_07.gif"></a><a href="Review.html"><img src="images/eportfolio-v1_08.gif"></a></td>
</tr>

<tr>
<td height="35" background="images/eportfolio-v1_09.gif" class="nav">
<!-- --></td>
</tr>
<tr> <td background="images/eportfolio-v1_10.gif" width=582 height=630 valign="top" class="content"> <font face="Arial">
  <p><font color="#FFFFFFF"><font color="#FFFFFFF" face="Pristina" size="5"><u><Center>Welcome!</centeR></u></font><br> <br>Welcome to my Dance O' Clock Eportfolio!<br>
        <br>

    The Eportfolio is a showcase of all the work I have made throughout the Dance 'O Clock project.
    Evidence of the publications and a review of the whole project is also included in the eportfolio. Below is the required information for the eportfolio.
    </font></p>
  <p><font color="#FFFFFFF"><hr color="#969696" width="540">
  <br>
    <font color="#FFFFFFF">Name:  &nbsp; Richard Dyson</font><br>
    <font color="#FFFFFF">SPB title:  &nbsp;Dance o'Clock Level 2 </font> <Br>

    <font color="#FFFFFF">Registration number: &nbsp; 9086 </font> <br>
    <font color="#FFFFFF">Center name: &nbsp; Whitchurch High school</font> <br>
    <font color="#FFFFFF">Center number: &nbsp;68751</font><br> 
    <br>

  </font>
  <hr color="#969696" width="540">
    <Br>
  <p><font color="#FFFFFFF" face="Pristina" size="4"><u>Recommendations</u></font></p>
  <p>
      <font color="#FFFFFF">Browser: &nbsp;Internet Explorer</font><br>
      <font color="#FFFFFF">Resolution: &nbsp;1024 * 968</font><br>

      
      
      
    
    </font>  </p></td> 
</tr>
</table>
</body>
</html>

```

cheers :)

---

### Post by Nemooo on 2008-02-21
You don't have an opening <table>. Could be it.

---

### Post by LaRoza on 2008-02-21
> **Nemooo said:**
> You don't have an opening <table>. Could be it.

No, it is next to the <body> tag though.

---

### Post by DrMega on 2008-02-21
> **Nemooo said:**
> You don't have an opening <table>. Could be it.

The table tag is there. Its just on the same line as other tags. Technically that in its self is not a problem, but it does make it harder to trace through.

Tip: If the tags are indented such that the opening and its corresponding close tag or at the same indent level, and indented in from whatever contains them, it will be much easier to read and debug.

Like this:

```

</html>
  <body>
    <table>
      <tr>
        <td>Some text</td>
      </tr>
    </table>
  </body>
</html>

```

---

### Post by LaRoza on 2008-02-21
The code very invalid, and it is no wonder it renders oddly. Try to stick to following the standards.

I won't begin to try to figure out why it renders the way it does. If it renders at all, it is a bug to me.

---

### Post by Nemooo on 2008-02-21
> **LaRoza said:**
> No, it is next to the <body> tag though.

I see it now, it's just some odd code. It's not very well written.

To the OP: First of all you should sort out your code, so it's easier to read and debug. Try using CSS for everything, if you're using it and not just the fonts. It's a lot easier to read and edit later on for yourself and others.

---

### Post by LaRoza on 2008-02-21
> **Nemooo said:**
> I see it now, it's just some odd code. It's not very well written.

To the OP: First of all you should sort out your code, so it's easier to read and debug. Try using CSS for everything, if you're using it and not just the fonts. It's a lot easier to read and edit later on for yourself and others.

Yes, it took me a couple seconds as well. (I only noticed it because of the long <body> line)

Also, to the OP: Validate your code before posting. That code has a lot of errors. I know that most browsers silently accept errors, but consider that a single error in a program will halt the program, and your code has 46 errors, and throws all kinds of warnings.

---

### Post by Mr.popo on 2008-02-21
I have fixed the bug by removing the pointless <font face="arial"> away from my code, however I accidentally posted the code for an earlier version. I cant seem to fix my latest version :(

Here's the code I should have posted:

```

<html>
<head>
<style type="text/css">
	img
	{	
		border: none;
	}
	.content
	{
		padding: 30px 30px 20px;
	}
	.nav
	{
		padding: 10px 22px 6px;
		font-size: 12px;
	}
	.mnav
	{	
		border: none;
	}
	/* link styles.. */
	a:link
	{
		color: #000000;
		text-decoration: none;
	}
	a:visited
	{
		color: #000000;
		text-decoration: none;
	}
	a:hover
	{
		color: #FFFFFF;
		text-decoration: none;
	}
</style>
<title> Index </title>
<script src="flash/AC_RunActiveContent.js" type="text/javascript"></script>
</head>
<body background="images/bg.jpg"><table align="center" cellspacing="0" cellpadding="0">

<tr>
<td width="652" ><script type="text/javascript">
AC_FL_RunContent( 'codebase','http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,28,0','width','652','height','69','title','banner','src','flash/banner','quality','high','pluginspage','http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash','movie','flash/banner' ); //end AC code
</script><noscript><object classid="clsid:D27CDB6E-AE6D-11cf-96B8-444553540000" codebase="http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,28,0" width="652" height="69" title="banner">
  <param name="movie" value="flash/banner.swf">
  <param name="quality" value="high">
  <embed src="flash/banner.swf" quality="high" pluginspage="http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash" type="application/x-shockwave-flash" width="652" height="69"></embed>
</object></noscript></td>
</tr>
<tr>

<td class="mnav"><a href="Index.html"><img src="images/eportfolio-v1_04.gif"></a><a href="Publications.html"><img src="images/eportfolio-v1_05.gif"></a><img src="images/eportfolio-v1_06.gif"><a href="Danceometer development.html"><img src="images/eportfolio-v1_07.gif"></a><a href="Review.html"><img src="images/eportfolio-v1_08.gif"></a></td>
</tr>

<tr>
<td height="35" background="images/eportfolio-v1_09.gif" class="nav">
<!-- --></td>
</tr>
<tr> <td background="images/eportfolio-v1_10.gif" width=582 height=630 valign="top" class="content"> <font face="Arial">
  <p><font color="#FFFFFFF"><font color="#FFFFFFF" face="Pristina" size="5"><u><Center>Welcome!</centeR></u></font><br> <br>Welcome to my Dance O' Clock Eportfolio!<br>
        <br>

    The Eportfolio is a showcase of all the work I have made throughout the Dance 'O Clock project.
    Evidence of the publications and a review of the whole project is also included in the eportfolio. Below is the required information for the eportfolio.
    </font></p>
  <p><font color="#FFFFFFF"><hr color="#969696" width="540">
  <br>
    <font color="#FFFFFFF">Name:  &nbsp; Richard Dyson</font><br>
    <font color="#FFFFFF">SPB title:  &nbsp;Dance o'Clock Level 2 </font> <Br>

    <font color="#FFFFFF">Registration number: &nbsp; 9086 </font> <br>
    <font color="#FFFFFF">Center name: &nbsp; Whitchurch High school</font> <br>
    <font color="#FFFFFF">Center number: &nbsp;68751</font><br> 
    <br>

  </font>
  <hr color="#969696" width="540">
    <Br>
  <p><font color="#FFFFFFF" face="Pristina" size="4"><u>Recommendations</u></font></p>
  <p>
      <font color="#FFFFFF">Browser: &nbsp;Internet Explorer</font><br>
      <font color="#FFFFFF">Resolution: &nbsp;1024 * 968</font><br>

      
      
      
    
    </font>  </p></td> 
</tr>
</table>
</body>
</html>

```


thanks

---

### Post by LaRoza on 2008-02-21
That has 23 errors in it.

[http://validator.w3.org/](http://validator.w3.org/)

---

