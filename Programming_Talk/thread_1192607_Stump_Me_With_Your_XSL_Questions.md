---
title: "Stump Me With Your XSL Questions"
date: 2009-06-20
forum: Programming Talk
---

### Post by SuperMike on 2009-06-20
I've been studying for my tough technical interview on a variety of topics, but this time I need to read up on XSL, XSLT, XPath, and XSL-FO. Go ahead and try and stump me with your tough questions, and perhaps I can see how good I am at beating this. Phew, this material is tough!

Also, XSL is a little strange in its naming because XSL means two things:

- Is the container of the XSLT, XPath, and XSL-FO technologies
- XSL-FO was officially named XSL by the W3C back in October 2001 ([SOURCE](http://www.w3schools.com/xslfo/xslfo_intro.asp))

So, by that, we now know this:

1. XSLT refers to transforming XML into another format.

2. XPath refers to a technology used inside of XSLT (also as a library in your programming language), to extract a portion of XML, usually to apply some transformation to it.

3. XSL (no longer called XSL-FO after Oct 2001) refers to the formatting of XML, not the transforming of it. And this includes new things called Pages, Regions, Block Areas, Line Areas, and Inline Areas.

And if I'm wrong above, please do correct me.

---

### Post by Reiger on 2009-06-20
If you are looking for something to keep yourself occupied with:

You transform almost all nodes to node of the name "entry". And entry either contains a name attribute which will be either made up of the original #ID value of a certain attribute (you get to chose the name, but there may be only 1 such attribute-type in any source document) or alternatively the local-name() of the original node that was transformed into this entry; or a ref attribute which is an #IDREF in DTD lingo. The entry has either a subtree of entries or a value node. The value node is either a plain string, a special formatted string containing plain strings and text nodes (text refers to a constant that may have been re-used; the key is this text node complicates matters further in the real task); or in turn the value may be a entry node with a ref attribute. In an entry node with the ref attribute the rule change slightly: everything descending from that ancestor carries a ref attribute instead of a name attribute with the same contents wherever applicable.

Consider you had an XML document which allows you to cross-reference with other elements: essentially importing their contents into the current one, using an attribute. (The XML elements that can be imported will have a (different) attribute which can be counted upon to conform to the ID requirements if a DTD were available.)

The XML elements that import other elements may specify `overrides' that is: they may re-defined certain sub-elements their own way. This means that the elements which are imported must *not* already exist within the **direct** descendants of the importing element (a name test will suffice).

Furthermore the XML elements that are imported may have been importing other XML elements themselves. You must take care of this by cascading the import effect. Make sure that this does not in-advertently undo any `overrides' in the final importing element!

Finally, due to a small oddity in the way the XML documents works you must ensure that you don't copy the entire imported trees: just the top-most node of whatever tree it is that is imported. Consider:

```

<root>
<foo id='example' imports='bar' />

<foo id='bar'><node1><child></node1><node2 /><node3>hello world!</node3></foo>
</root>

```

The resulting tree would be:
```

<entry name="root">
  <entry name="example">
    <value ref="bar">
      <entry ref="node1" />
      <entry ref="node2" />
      <entry ref="node3" />
    </value>
  </entry>
  <entry name="bar">
    <entry name="node1">
      <entry name="child">
        <value />
      </entry>
    </entry>
    <entry name="node2">
      <value />
    </entry>
    <entry name="node3">
      <value>hello world!</value>
    </entry>
  </entry>
</entry>

```

EDIT: I forgot to mention that when the imported nodes themselves would transform to either the plain string or the formatted string; you must make sure that this information is not lost. (There is only 1 true solution which is to copy over these elements.)

---

### Post by SuperMike on 2009-06-20
Phew! Reiger, what's your IQ? A lot to think about here. Still working on it, actually.

---

