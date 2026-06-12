---
title: "display picture in html from an xml document"
date: 2008-11-09
forum: Programming Talk
---

### Post by KMuchane on 2008-11-09
Hi,
 I would like to display a photo from an xml document in HTML. The simple xml file below represents the general idea of what I have done:

<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="car.xsl"?>
<!DOCTYPE car  SYSTEM "data1.dtd">

<car>
	<make>
	VW Beetle
	</make>
	<dom>
	1974
	</dom>
	<cc>
	1199
	</cc>
	<picture>
	pix pic="&pix;"
	</picture>
</car>

I read that binary data like the picture can only be referenced in an an attribute. And for some reason the "data1.dtd" is not being read

The simple external dtd looks like:

<?xml version="1.0" ?>
<!ENTITY pix SYSTEM "car.gif">
<!ELEMENT car (make, dom, cc, picture)>
<!ELEMENT make (#PCDATA)>
<!ELEMENT dom (#PCDATA)>
<!ELEMENT cc (#PCDATA)>

Here I am at a loss as to how I would describe the picture element, but my biggest problem is  how I would get the car.gif file to be read as a file not as a string. In the present scheme of things Firefox says the entity &pix is not defined, while Opera returns it as a string, with the rest of the elements. When I put the entity pix in an internal dtd the file path name is read as a string :(
Here is the 'car.xsl' file

<?xml version="1.0" ?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

	<xsl:template match="/car">
		<p><b><xsl:value-of select="."/></b></p>
	</xsl:template>
	
	<xsl:template match="/car">
		<html>
		<title>GARI</title>
		<body>
		<xsl:apply-templates/>
		</body>
		</html>
	</xsl:template>
	
</xsl:stylesheet>

There is something I am missing. I would very much appreciate some guidelines, thanx!
Kinuthia...

---

### Post by achelis on 2008-11-09
I would use the "img" tag in html to display images. Have a reference to the filename in the xml-file and transform it using xslt.

And if you use "CODE" tags to post code you should avoid getting smileys.

---

