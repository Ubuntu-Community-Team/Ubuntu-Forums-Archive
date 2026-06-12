---
title: "Calling external java script function in XSLT"
date: 2008-01-30
forum: Programming Talk
---

### Post by mohtasham1983 on 2008-01-30
Hi,

I'm using xslt to transfer xml to html. Some of the html elements which are generated in xslt file have event handler. For example for an anchor element I have defined an onclick event handler to execute a function; however, in IE the function handler cannot be called.

A few days ago I realized that if I write my javascript function inside the same xsl file, everything works fine, however based on my website structure, I had to use an external function to do that. Then I transfer my entire javascript file to an xsl file and included that xsl file in my main xsl file and it worked well for some of the functions. 

Since I'm using YUI, some of my javascript function use YUI APIs which are not inside any xsl document and it s not very convenient to make all yahoo library files in to an xsl element.



Here is a few piece of code:

The following code works fine:

[PHP]
<a class="btn">
							<xsl:attribute name="id">
								<xsl:value-of select="news_id"/>	
							</xsl:attribute>
							<xsl:attribute name="onclick">
    									sayhi(this); 
<script language="Javascript">
function sayhi(e) {
	alert(e.id);
	return false;
}
</script>
							</xsl:attribute>
							HELLO
							</a>	
[/PHP]

but if I write my sayhi function inside an external js file it won't work in IE.

Any idea how I can call external javascript functions in my page so that i works in IE?

---

### Post by clasificado on 2008-01-31
¿That is an error?

You cant put a <script> tag **inside** the onclick="" attribute. You should put it somewhere in the document, remaining valid xml.

The HEAD section of your HTML is a good place.

Clasificado

---

