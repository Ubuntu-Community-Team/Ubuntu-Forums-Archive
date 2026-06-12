---
title: "[First C++?] Project for work.. Extracting specification from Non standard text."
date: 2010-03-22
forum: Programming Talk
---

### Post by Jonas thomas on 2010-03-22
I'll get my VS installed at work and hopefully I can start getting off of VB6 and starting to code in C++.  I've been getting somewhat dangerous in my C++ class, and I've been itching for a real world project.

Here is my pain.
I'm datamining our database which has free text entries where I want to extract standard data, like spec call outs than are entered in a non standard manner.  There is usually a prefix that I can lock on to as a starting point, but not always.  

A simple example of what I'm Looking for data that looks like this:
PN-1234 <Normalized data to be put in the database
Valid entries could also be
PN1234
PN 1234
Invalid entries could be
PN:
PN:234adf234d
PN:1
PN:12345

Many other permuations and rules apply to other situations.

Creating a solution for this on particular situationis trivial. I am how ever interested in creating/using a template library that would search instances of  document/spec callouts in text but them in normalized form in a database.

My first thought was to create a human readable code that would define the rules for extraction.  Something like:
Prefix = "PN"
Pattern ="-#####"

This however has it's limitations.  Next thought was to Create some type of XML'ish template code
[TEMPLATE][PREFIX:"PN"][PREFIX\][FIXEDSPACEORNONE:"-"][FIXEDSPACEORNONE\][FIXED:NUMERIC_ONLY][FIXED\][TEMPLATE\]

Rather than re-inventing the wheel... I'm sure something like this been done?  It almost seems like the logic behind writing an interprator. As another example it seems like google does stuff like that all the time in search queries.

Any suggestions, magic search terms, stock lgpl solutions anyone can suggest that I need to research for my first work project using C++?

Thanks in advance.
JT

---

### Post by Jonas thomas on 2010-03-22
I've done a bit of research on this... Seems like the the magic search term I needed was "Information Extraction". Go figure...
I found a nice wiki link: [http://en.wikipedia.org/wiki/Information_extraction]("http://en.wikipedia.org/wiki/Information_extraction")

Which took me here:[http://www.gabormelli.com/RKB/Information_Extraction_Task]("http://www.gabormelli.com/RKB/Information_Extraction_Task")

Which took me here:
["Information Extraction: Distilling Structured Data from Unstructured Text."]("http://portal.acm.org/citation.cfm?doid=1105664.1105679")

This was a very interesting article on the subject that references an open source procect called lemur/indri.
[http://ciir.cs.umass.edu/~strohman/indri/]("http://ciir.cs.umass.edu/~strohman/indri/")

I think I need to dump out the data I need to XML figure out the C++ library and let her rip.  
Has anyone here messed around with this library? I hate to really start digging into this just to figure out, oh I should have done something else.

---

