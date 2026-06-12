---
title: "[SOLVED] How to fiddle with XSLT"
date: 2008-02-15
forum: Programming Talk
---

### Post by kentl on 2008-02-15
Hi

I am wondering what you use to fiddle with XSLT? I want to write my transformation and try it out.

I've been trying xsltproc a little. But perhaps there is something else? Do you use it from Java/PHP/Python etc? What do you recommend for learning XSLT and developing transformations which I later will use in <some> programming language? (no need to decide on programming language I presume, as the XSLT transformations should be the same regardless of which programming language I choose to use. Or?)

---

### Post by pmasiar on 2008-02-16
What kind of XSLT transformation are you trying to do?

I found XSLT extremely hard to read and hard to use. My eyes were bleeding from all that pointy braces! :-)

From Python, I have better experience in parsing XML by some parser (ElementTree works for me the best) and then generating XML using Kid.

---

### Post by Geekkit on 2008-02-16
> **kentl said:**
> Hi

I am wondering what you use to fiddle with XSLT? I want to write my transformation and try it out.

I've been trying xsltproc a little. But perhaps there is something else? Do you use it from Java/PHP/Python etc? What do you recommend for learning XSLT and developing transformations which I later will use in <some> programming language? (no need to decide on programming language I presume, as the XSLT transformations should be the same regardless of which programming language I choose to use. Or?)

Not sure what you mean 'fiddle'. To edit/create XSLT documents, you can use Geany or Gedit or Netbeans and Eclipse both have plugins that handle the syntax of XSLT.

As for performing transforms, that's usually (but not always) left up to server-side environments such as Java/JSP/Servlets/J2EE platform, C#/ASP/ASPX/.NET platform, or PHP/PHP platform.

You suggest the rules and the platform performs them. To get started check out:

[http://www.w3schools.com/xsl/](http://www.w3schools.com/xsl/)
[http://www.zvon.org/xxl/XSLTutorial/Books/Book1/index.html](http://www.zvon.org/xxl/XSLTutorial/Books/Book1/index.html)
[http://nwalsh.com/docs/tutorials/xsl/](http://nwalsh.com/docs/tutorials/xsl/)
[http://www.topxml.com/xsl/tutorials/intro/default.asp](http://www.topxml.com/xsl/tutorials/intro/default.asp)

The above links will help you see what you can do with it. I've used XSLT to create things such as XSD Schema documentation, skinnable Web sites, and even generate PDF documents using XSL-FO. It's quite rewarding but as pmasiar mentioned staring at it for long periods of time can make the eyes bleed. :)

---

### Post by Shin_Gouki2501 on 2008-02-16
yep you need an XSLT processor , like:
[http://saxon.sourceforge.net/](http://saxon.sourceforge.net/)

have fun 
;)

---

### Post by Geekkit on 2008-02-16
One other thing. The above links that I've posted for you to read, you can test all of these within a browser by linking your XML file to your XSLT like this:

[FONT="Courier New"]<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="./transformfile.xslt"?>
<stuff>
  <!-- your content here -->
</stuff>[/FONT]

Assuming both are in the same directory and you open the XML file in say Firefox, you will see the transform performed.

---

### Post by popch on 2008-02-16
Once you get the hang of it, you might find XSLT quite straight forward. Saxon is a very credible implementation, and the tip about using the browser for performing the transformation is very useful.

To be quite honest, I am using [XML spy]("http://www.altova.com/") (3.5) for most of my XSLT work. True, it cost some money, but it even runs in Wine and has a very powerful XML editor which greatly assists in producing valid XSLT, as far as that goes.

---

### Post by a9bejo on 2008-02-17
As an editor, I use [nxml-mode](http://www.thaiopensource.com/nxml-mode/), which transforms Emacs into a very powerful XML editor.  

The problem with xsltproc is that it does currently not support XSLT 2.0, which is a huge step forward from XSLT1.0.  Same goes for XALAN, which is a popular java based parser.  The solution is [Saxon](http://saxon.sourceforge.net/), which was already mentioned in another post.  It is very easy to use and it supports 2.0 .  You can use saxon from the command line, or call it from any language that runs on the java virtual machine.

XSLT1.0 is also supported by popular web browsers like firefox or internet explorer.  So you can also add a stylesheet link to an xml document you want to transform and then view the results of the transformation directly in your browser.

Another tool that should be mentioned is [trang](http://www.thaiopensource.com/relaxng/trang.html).  This is not directly related to XSLT, but you can use it to automatically create XML schema from XML files.  That is very handy with Emacs nxml-mode, because nxml can use [relax-ng](http://en.wikipedia.org/wiki/RELAX_NG) schemas to validate and autocomplete documents, and with trang you can also simply convert from W3C schema to relax-ng.

---

### Post by kentl on 2008-02-17
Thanks for all of your answers! I'll answer each of you below. :-)

[QUOTE=pmasiar]What kind of XSLT transformation are you trying to do?[/QUOTE]
I want to study XSLT in general. As a pet project for learning purposes I will be creating a XML-based formatting language which you can compile, using XSLT transformations, into HTML and LaTeX.

[QUOTE=Geekkit]
As for performing transforms, that's usually (but not always) left up to server-side environments such as Java/JSP/Servlets/J2EE platform, C#/ASP/ASPX/.NET platform, or PHP/PHP platform.[/QUOTE]
I want to focus on XSLT. That's why I asked for which environment you recommend. I want something which is not in the way while I'm focusing on XSLT. 

For example using **xsltproc** I do something like ```
xsltproc transform.xsl input.xml
``` and get the transformed output. That's pretty neat. I'm having some problems with it though, and I have a hard time finding support for it. Which is why I'm looking for some other environment/tool I can use.

[QUOTE=Shin_Gouki2501]http://saxon.sourceforge.net/[/QUOTE]
Ah! This is the kind of stuff I was looking for. I'll look into it! :-)

[QUOTE=Geekkit]
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="./transformfile.xslt"?>
<stuff>
<!-- your content here -->
</stuff>

Assuming both are in the same directory and you open the XML file in say Firefox, you will see the transform performed.[/QUOTE]
And this is also the kind of stuff I'm looking for! It could be useful while I develop my XSLT transformation. And then I decide on some language/platform with XSLT support and use it for my final implementation.

[QUOTE=popch]
To be quite honest, I am using XML spy (3.5) for most of my XSLT work. True, it cost some money, but it even runs in Wine and has a very powerful XML editor which greatly assists in producing valid XSLT, as far as that goes.
[/QUOTE]
I would prefer something which is OSS. But I do have XML Spy on my work computer. I could give it a go too. :-)
[QUOTE=a9bejo]
The problem with xsltproc is that it does currently not support XSLT 2.0, which is a huge step forward from XSLT1.0. Same goes for XALAN, which is a popular java based parser. The solution is Saxon, which was already mentioned in another post. It is very easy to use and it supports 2.0 . You can use saxon from the command line, or call it from any language that runs on the java virtual machine.
[/QUOTE]
I'm not really into Emacs, but I'll check it out. Apart from that the recommendation seems to be Saxon. And I'll check out Trang too.

---

### Post by Geekkit on 2008-02-17
> **kentl said:**
> [QUOTE=Geekkit]As for performing transforms, that's usually (but not always) left up to server-side environments such as Java/JSP/Servlets/J2EE platform, C#/ASP/ASPX/.NET platform, or PHP/PHP platform. 
I want to focus on XSLT. That's why I asked for which environment you recommend. I want something which is not in the way while I'm focusing on XSLT.[/QUOTE]

Okay then, my choice is Java but I make no claim that it is better or worse than any other platform choice that anyone else suggests in this thread or other threads for the simple reason I don't want to start or encourage a flame war of any kind. I do know that PHP and C#/.NET both offer handling of XSLT and so anyone using those platforms will most likely have same/similar comments to make about their platforms.

1.) Built right into the development/runtime environment. At least if you're using the latest JDK/JRE (1.6)
2.) Ease of use. For example, to create a simple command line XSLT transform application in Java:


```
import javax.xml.transform.TransformerFactory;
import javax.xml.transform.Transformer;
import javax.xml.transform.stream.StreamSource;
import javax.xml.transform.stream.StreamResult;
import javax.xml.transform.TransformerConfigurationException;
import javax.xml.transform.TransformerException;

public class Transit
{
	public Transit(String xml, String xslt, String html)
	{
		try
		{
		    TransformerFactory tfactory = TransformerFactory.newInstance();
		Transformer transformer =  tfactory.newTransformer(new StreamSource(xslt));
		transformer.transform(new StreamSource(xml), new StreamResult(html));

		} catch (TransformerException e)

		{
			e.printStackTrace();
		}
	}

	public static void main(String[] args)
	{
		if(args.length != 3 || args == null)
			System.out.println("Usage: java Transit <data.xml>"
				+ " <transform.xsl> <result.html>");
		else
		{
			Transit t = new Transit(args[0], args[1], args[2]);
		}
	}
}
```

3.) Easy integration with JSPs and related tag libraries. I did one Web application where the JSPs were programmatically generated and only contained something like the following:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.0 Transitional//EN"
  "http://www.w3.org/TR/REC-html40/loose.dtd">
<%@ page contentType="text/html; charset=ISO-8859-1" %>
<%@ taglib uri="http://java.sun.com/jstl/xml" prefix="x" %>
<%@ taglib uri="http://java.sun.com/jstl/core" prefix="c" %>

<c:import var="xmlfile" url="./xmlfile.xml">
<c:import var="xslfile" url="./xslt/template.xslt">

<x:transform xml="${xmlfile}" xslt="${xslfile}">]
```

The transformer did all the work and allowed me to skin the Web site by using an admin tool. Pretty easy.

Hope this helps. :)

---

### Post by kentl on 2008-02-18
Thank you for your answer! Java is my language of choice too. Nice to know how easy it is to use XSLT from it!

As I have my own server I'm able to install Tomcat on it and use it for web development. However I think it's nice to use XSLT when it's suitable, as it could be used from PHP as well. And thus will make porting easier. I think PHP is found at more cheap hosting solutions than hosting solutions where a servlet container is included. Which could be a motivation for porting. Enough rambling, thanks for all of your answers! :-)

---

### Post by pedro_orange on 2008-02-18
Got a bit of a side question that someone may be able to help with concerning XSLTs. (Sorry to hijack your thread)

But has anyone used an XSLT to transform an SVG?

Specifically changing an attribute within a tag of the SVG. Like font-size/family etc.
XML is from space if you ask me! :)

---

### Post by Geekkit on 2008-02-18
> **pedro_orange said:**
> Got a bit of a side question that someone may be able to help with concerning XSLTs. (Sorry to hijack your thread)

But has anyone used an XSLT to transform an SVG?

Specifically changing an attribute within a tag of the SVG. Like font-size/family etc.
XML is from space if you ask me! :)

You shouldn't jack threads - besides, your question is worth its own post is it not? Check this link out which has some great examples on how to do this:

[INDENT][http://www.carto.net/papers/svg/samples/xslt/](http://www.carto.net/papers/svg/samples/xslt/) [/INDENT]

and this one too:

[INDENT][http://www.w3.org/People/maxf/papers/2002-07-SVGOpen/svgopen.html](http://www.w3.org/People/maxf/papers/2002-07-SVGOpen/svgopen.html)[/INDENT]

Basically, it's no different than any other XML format, you just include the name space and perform your transforms with templates.

---

