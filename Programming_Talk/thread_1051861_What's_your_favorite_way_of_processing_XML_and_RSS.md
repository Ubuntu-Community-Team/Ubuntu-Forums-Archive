---
title: "What's your favorite way of processing XML and RSS"
date: 2009-01-27
forum: Programming Talk
---

### Post by NinjaWork on 2009-01-27
Hi everyone,

I program in Perl/PHP/Python and am picking up Ruby. I used to use 100% regular expressions to process XML. Basically, just split everything on the main container tag, then loop through the containers. This works and is very fast, but always makes my mind hurt when I come back to revisit the code ;)

Lately, I've been reading up on XML, learning about DOM and SAX and seeing what each language has to offer. For Perl, I see a lot of outdated modules out there. I discovered the beauty of LibXML. For Python, I just did a project using Minidom, which I did not like at all! I want to look into using ElementTree and lxml. I haven't done anything yet with PHP. I hear the old Ruby XML parser is very slow, but they just released Libxml-Ruby.

So I'm curious what everyone else does. Do you set up a SAX parser, go with using DOM or XPath, just parse it with regexes, etc. Also (important), how portable is using the Libxml2 bindings...can you expect most hosts to have it installed?

---

