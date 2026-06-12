---
title: "Effective XML citation"
date: 2007-12-13
forum: Programming Talk
---

### Post by DouglasAWh on 2007-12-13
Our library here at UNC does not have the book *Effective XML*, so I was wondering if anyone could verify the citation used at [http://weblogs.asp.net/sbchatterjee/archive/2003/11/22/39257.aspx](http://weblogs.asp.net/sbchatterjee/archive/2003/11/22/39257.aspx).  

Here's the text I'd like to cite:
> 
I received 'Effective XML' a few days ago and here is an interesting excerpt (pg 230) -

“XML is not a database. It was never meant to be a database. It is never going to be a database. Relational databases are proven technology with more than 20 years of implementation experience. They are solid, stable, useful products. They are not going away. XML is a very useful technology for moving data between different databases or between databases and other programs. However, it is not itself a database. Don't use it like one.“


---

### Post by aks44 on 2007-12-13
I can't verify the citation, but let me anyway give my thoughts about that...


XML as in (full) DOM tree and/or flat (structured) text is indeed not meant to be a database (not more that unstructured flat text files are meant to, anyway). It would be either too slow or too memory hungry.

BUT

A few database engines have already showed that XPath / XQuery can be amazingly useful tools to query structured data. Plus when it comes to OOP, serialization & persistence become totally straightforward. I've not had the opportunity yet to use such a technology in a production project but from the little I've toyed with that, it is *very* promising IMHO.



Back to the citation: XML-DB may not (??) be a mature technology yet (at least not mature enough to handle critical data), but I'd bet it definitely *will* soon.

---

### Post by pmasiar on 2007-12-13
I don't have the book either, but I agree with aks44.

Which part of the citation you disagree with? XML is rather inefficient for storing data (too much markup info), even when exchanging big files you can save quite a lot of space if you transfer structure and tab-delimited data separately (of course then you need to make custom restructuring program on receiving end).

---

### Post by AZzKikR on 2007-12-14
> **DouglasAWh said:**
> Our library here at UNC does not have the book *Effective XML*, so I was wondering if anyone could verify the citation used at [http://weblogs.asp.net/sbchatterjee/archive/2003/11/22/39257.aspx](http://weblogs.asp.net/sbchatterjee/archive/2003/11/22/39257.aspx).  

Here's the text I'd like to cite:

Let me tell you that I've worked with an XML database at my work. Full 4 Kb documents (or even larger) are put into that database, growing over 6 months to over 2 Gb. When I tried to run queries on it (XSLT/XPath), most of the time some address space or memory issue occurred because of God knows what. 

In my honest opinion, XSL/XPath queries on an XML database can be very fast, simple and whatnot. Just not in this time of age, and I don't think any XML database will receive the status a relational database has these days.

XML is not designed to be a database. I hope it will never be, because I think the logic just does not speak for itself, whereas an object- or relational database is logical.

---

### Post by engla on 2007-12-14
I'm not an industry guy, but I think I agree with the citation.

As I understand it, you cannot safely and correctly handle an XML file without visiting every tag in the document (*almost* every), otherwise the document and the part you want to reach might not be well-formed.

The purpose of an XML file is to be slurped into a database or (when smaller) into some other data structure; for example web browsers will do that for their bookmarks and desktop music apps for their library. But then the dataset is so small that it can be effectively slurped into the database at launch, and at random times be written out in full again. The key point of mine would be that you can't search or randomly access an XML file, it is just an intermediate data store.

---

