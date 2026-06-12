---
title: "help bringing my html up to standards"
date: 2008-11-26
forum: Programming Talk
---

### Post by mpgarate on 2008-11-26
my first website, [power-pirate.com]("http://power-pirate.com/") works perfectly in firefox, but in opera and google chrome the images on the about page do not align properly. I'm sure this is by some fault of mine, but nothing I try fixes it in these browsers. here is the code from that section of the site:

```
          <div ID="about" CLASS="content">
            <img SRC="img/header.jpg" ALT="Power Pirate"><br>
            <strong>About Us:</strong><br>
            <center>
              <table ALIGN="center" CLASS="image">
                <caption ALIGN="bottom">
                  Emily - Guitar, Vocals
                </caption>
                <tr>
                  <td>
                    <a HREF="http://www.myspace.com/powerpirate"><img SRC="img/emily.jpg" ALT="Emily"></a>
                  </td>
                </tr>
              </table>
              <table ALIGN="center" CLASS="image">
                <caption ALIGN="bottom">
                  Michael - Keyboards
                </caption>
                <tr>
                  <td>
                    <a HREF="http://www.myspace.com/powerpirate"><img SRC="img/mike.jpg" ALT="Mike"></a>
                  </td>
                </tr>
              </table>
              <table ALIGN="center" CLASS="image">
                <caption ALIGN="bottom">
                  Annika - Drums
                </caption>
                <tr>
                  <td>
                    <a HREF="http://www.myspace.com/powerpirate"><img SRC="img/annika.jpg" ALT="Annika"></a>
                  </td>
                </tr>
              </table>
		<br>
	<table align="center" class="image"><b>___________________________________________________</b><br><b>Power Pirate</b> is an Electronic-Rock band from Washington DC formed <br>by  <b>Michael Garate</b>, <b>Emily Pakulski</b>, and <b>Annika Monari</b> in 2007.<br> The group formed after a friend recommended they play together. <br>They have been hard at work recording, writing, and gigging ever since. <br><b>&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;&#65507;</b></table>
            </center>
          </div>
```

thanks!

---

### Post by MicahCarrick on 2008-11-26
Looking very quickly at your code, I have a hunch but do not know for sure. I see that your .image CSS class, used on each of those tables containing the images, specifies 'display: inline;' for those tables. Now, I have never applied a 'display' style directly to a table before, but the logic of making it inline makes sense. However, a quick glance at [http://www.w3.org/TR/CSS21/tables.html]("http://www.w3.org/TR/CSS21/tables.html") indicates that perhaps you want to specify 'display: inline-table;' instead. This is news to me, but that would be the first thing I try.

Another note, when you are working on cross browser compatibility, you'll find that the best starting point is 100% valid code. Use the W3C HTML Validator on your code before debugging rendering issues and you'll save yourself a lot of time. Personally, I write my code using Firefox (up until v3) and now using Opera. When it works good in Opera or other more compliant browsers, and is valid, you are at a good starting point. The next step is to identify and work around any Internet Explorer bugs. Give a read through the blogs once in a while discussing IE bugs so you know what you're dealing with when they come up--there are some odd ones.

Good luck

---

### Post by mpgarate on 2008-11-26
thanks for your reply! the CSS inline-table bit worked great for opera, but the site still shows up funny in chrome

---

### Post by MicahCarrick on 2008-11-26
I don't have Chrome, but you're going to have to keep tweaking until you find something all browser like. Personally, and this may be totally wrong, but it seems to me that I can more quickly get my code to work in all browsers when using XHTML strict as opposed to HTML transitional.

If you are pressed for time and cannot resolve the issue using what you have, you could try wrapping each of those tables in a DIV with 'display: inline;' and see what happens.

Also, both Opera and Firefox have VERY handy utilities to help you tweak CSS on the fly to see how it effects layout. For firefox you will want to have FireBug add on and for Opera you want the DragonFly tool.

---

### Post by Peter76 on 2008-11-26
What I would do is drop the table ( but then I have no experience with them for web layout :-) and use absolute positioning with css:

Make a div containing the images, float the images to the left, and position the div on the center of the page.
This works for me cross-browser wise.

Good luck

---

### Post by hessiess on 2008-11-26
Use the strict DTD and don't use tables for layout!

---

### Post by SeanHodges on 2008-11-27
As hessiess said, always avoid using tables for layout. Use <table>'s for drawing tables, and <div>'s for laying out the page. Not doing this makes things seem easier in the short term, but a real pain once the pages get more complicated and you want to make your site cross-browser compliant.

The following should work in most browsers. I have not tested Google Chrome but it should work on that too:

```

<style>
	div.header
	{
		width: 100%;
		text-align: center;
		font-weight: 800;
		margin-bottom: 20px;
	}

	div.imagecontainer
	{
		margin-left: auto;
		margin-right: auto;
		width: 620px;
		text-align: center;
		margin-bottom: 20px;
	}

	div.image
	{
		float: left;
		padding-left: 10px;
		padding-right: 10px;
		text-align: center;
	}

	p.caption
	{
		margin-top: 2px;
	}

	div.description
	{
		clear: left;
		margin-left: auto;
		margin-right: auto;
		width: 500px;
		text-align: center;
	}

	hr {
		height: 1px;
		border-style: solid;
		border-top: 0px;
		color: #9090B4;
	}
</style>

<div CLASS="header">
	<img SRC="img/header.jpg" ALT="Power Pirate"/><br/>
	<p>About Us:</p>
</div>
<div CLASS="imagecontainer">
	<div CLASS="image">
		<a HREF="http://www.myspace.com/powerpirate">
			<img SRC="img/emily.jpg" ALT="Emily"/>
		</a>
		<p CLASS="caption">Emily - Guitar, Vocals</p>
	</div>
	<div class="image">
		<a HREF="http://www.myspace.com/powerpirate">
			<img SRC="img/mike.jpg" ALT="Mike"/>
		</a>
		<p CLASS="caption">Michael - Keyboards</p>
	</div>
	<div class="image">
		<a HREF="http://www.myspace.com/powerpirate">
			<img SRC="img/annika.jpg" ALT="Annika"/>
		</a>
		<p CLASS="caption">Annika - Drums</p>
	</div>
</div>

<div CLASS="description">
	<hr/>
	<b>Power Pirate</b> is an Electronic-Rock band from Washington DC formed by <b>Michael Garate</b>, <b>Emily Pakulski</b>, and <b>Annika Monari</b> in 2007.<br/> The group formed after a friend recommended they play together. <br/>They have been hard at work recording, writing, and gigging ever since. <br/>
	<hr/>
</div>

```

This should also work in IE6 (the current site does not), but you must add the following to the top of each page to make sure IE6 does not use "quirks mode", which often breaks the standards:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
	"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
```

Be sure to check out the [W3C Schools]("http://www.w3schools.com/") website if you want to learn how to design websites using the standards. Also, if you haven't tried the "Firebug" extension for Firefox, I can't recommend it enough for helping with web design.

---

