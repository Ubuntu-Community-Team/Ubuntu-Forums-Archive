---
title: "Poll on XML Document Parsing"
date: 2008-01-22
forum: Programming Talk
---

### Post by river22_34 on 2008-01-22
Hi everyone,
I am conducting an online poll on XML document parsing. Everyone can cast your votes based on the arguments that I have provided below:-

The SAX API allows you to use a SAX parser to process the XML documents serially, using a data stream. The DOM API allows you to use the DOM parser to process the XML documents in an object oriented manner. In short, SAX provides serial access while DOM provides a tree-based hierarchical access to the data in the XML documents.

Please cast your votes regarding this discussion. Thank you.

---

### Post by LaRoza on 2008-01-22
> **river22_34 said:**
> Hi everyone,
I am conducting an online poll on XML document parsing. Everyone can cast your votes based on the arguments that I have provided below:-

The SAX API allows you to use a SAX parser to process the XML documents serially, using a data stream. The DOM API allows you to use the DOM parser to process the XML documents in an object oriented manner. In short, SAX provides serial access while DOM provides a tree-based hierarchical access to the data in the XML documents.

Please cast your votes regarding this discussion. Thank you.

I voted for the DOM. 

I always use it, with no real experience with SAX.

I write most of my code in ECMAScript, and use the DOM everywhere.

Examples of my use of it: 

Site: [http://laroza.freehostia.com/home/apps/rpn/default.html](http://laroza.freehostia.com/home/apps/rpn/default.html) Script: [http://laroza.freehostia.com/home/apps/rpn/script/script.js](http://laroza.freehostia.com/home/apps/rpn/script/script.js)

Site: [http://laroza.freehostia.com/arlines](http://laroza.freehostia.com/arlines) Script: [http://laroza.freehostia.com/airlines/script/](http://laroza.freehostia.com/airlines/script/)

My home page: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home) Scripts are in a "script" directory for each page. The web applications have their own directories, same name. Just in case anyone wants to look at my use of the DOM to completely separate script from markup.

I use the DOM because it is a very logical way of looking at XML documents, also, as far as I know, SAX has no specification and is not used in ECMAScript. My programming is web based, and typically in a browser (when dealing with XML), so the advantages of SAX (not having to read the entire document) are moot.

<edit>
Why are you asking this? If you are asking because you need to parse XML, give the language and reason for this so the answers we give are not just our opinions/experience speaking.
</edit>

---

### Post by clasificado on 2008-01-22
Whoooooooooooa! another A vs B situation!
Ruby or Python? ReiserFs or Ext3? Gnome or KDE? DOM or SAX?

First at all, god creates bits, and from there he created the creatures that lives on the ground (DOM) and the creatures that lives underwater (SAX) :confused:

Seriously now: The DOM and SAX exists by two very different needs.

If you need a compressive point of view of your XML document, like inside and HTML (usually javascript), DOM is correct. So, the initial processor cost (by tree building) is justified.

Now, if you has a 3 GB xml file, the DOM parser will explode, the processor will explode, your computer will explode, and flames will be everywhere. Then SAX comes to rescue.

If you dont FEEL the need of SAX, use DOM.

Believe me: When SAX is needed, you will know.

Clasificado

---

### Post by popch on 2008-01-22
Both methods are equally useful, but for different tasks. There is considerable overlap, i.e. cases where you can argue equally well for either.

Besides, the poll is incomplete in the sense that there are parsers which do roughly the same but do not qualify for either category. That's because SAX and DOM refer to some explicit standards, and some parsers implement different event or tree models.

---

### Post by pmasiar on 2008-01-22
Neither.

I prefer ElementTree :-)

---

### Post by skeeterbug on 2008-01-22
I used either DOM or XML serialization/de-serialization for .NET. When I started in Perl/Python I looked into SAX. It was awkward at first, but I now prefer SAX over DOM. Though serializing the XML to a POCO (Plain old C# object) is pretty damn nice too.

---

### Post by LaRoza on 2008-01-22
> **pmasiar said:**
> Neither.

I prefer ElementTree :-)

I am reading up on ElementTree, it looks interesting.

---

### Post by legolas_w on 2008-01-22
OK, I want to give my opinion here,
SAX and DOM are really really different things when it come to internal structure and their use case.
DOM uses a lot of memory and need to create an entire tree in the memory before let you traverse in the document, so If you document is very big, you will need to wait for some times before parser completely parse the document and create the tree. 
On the other hand, DOM can be useful when you need to navigate between the nodes up and down, right and left ;-). you can traverse between them freely and  you can change the value of attributes or node on your will. So you can write XML documents using DOM APIs.

Here your parser client is not binded to the parser and after an initial work of the parser you can perform what you need.

SAX, is a push parser, as mentioned it is stream based and when a node parsed you can not go back and check its value again, all you can do is handling different events  when parser sees different elements.
SAX does not allows you to write XML documents, It is a one way parser and your parser client will be bindded to the parser to complete its task.


StAX: which is not included in the Poll, let you have what ever SAX provides in addition to XML authoring. using StAX your parser client is not binded to the parser work, indeed client pull events by calling the parser to move step by step over the XML document. 

* Some DOM parser make several fragment of the XML document and then work on fragment to have some memory optimization.


my vote: Both, each for its place.

---

