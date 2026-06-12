---
title: "libxml++ Node::find() function question"
date: 2009-12-06
forum: Programming Talk
---

### Post by Redalert Commander on 2009-12-06
Hi,

I seem to be stuck on some piece of XML programming in C++.
I'm using libxml++

The following code sample:
```

xmlpp::NodeSet nodes(root_node->find("descendant::*"));
for(xmlpp::NodeSet::iterator i=nodes.begin(); i != nodes.end(); ++i){
       xmlpp::Element * element = dynamic_cast<xmlpp::Element*>(*i);
       cout << "Xpath works: " << element->get_name() << endl;
}

```
gives the following output (I left out some data to keep it short)
```

...
Xpath works: status
Xpath works: data
...

```

However when I change the "descendant::*" to "descendant::data" or "//data", the output of that code sample remains empty. Same when using the full xpath expression like "/nodename/subnode/data", "//*" gives (as expected) the same output as "descendant-or-self::*".
Bu as soon as I try to use a name, it doesn't find anything.

Any ideas?
This is done on Ubuntu 9.10 (libxml++ 2.26.0-2), but has exactly the same behavior on Debian Lenny (libxml++ 2.22.0-1)

If I use several nested for loops with get_children(), it works fine, yet that results in about 5 loops, for just this element.

---

### Post by Redalert Commander on 2009-12-10
Got it fixed, I was constantly overlooking the default namespace URI on the root element, removing it fixes the issue.

It's all explained in this page I found after another google session: [http://www.edankert.com/defaultnamespaces.html](http://www.edankert.com/defaultnamespaces.html)

---

### Post by A_Fiachra on 2009-12-10
Namespaces ruined XML for me.

---

