---
title: "Yahoo UI widget help needed - treeview"
date: 2008-06-19
forum: Programming Talk
---

### Post by pmasiar on 2008-06-19
I am noob in javascript, and it shows. But I need to get this AJAX working. I did
managed to get dynamic tree working:

[http://developer.yahoo.com/yui/examples/treeview/dynamic_tree.html](http://developer.yahoo.com/yui/examples/treeview/dynamic_tree.html)

My tree has always 3 levels.

I need to add checkboxes to the leaves (3rd level), but I am lost how.

When I am adding new nodes (leaves, in string array sLeaves), as received from server [lines 29-31 of yahoo sample code]:

var tempNode = new YAHOO.widget.TextNode(sLeaves[i], node, false);

I am trying to add html for checkbox, but I have no idea how to add custom HTML to TextNode.

My ultimate goal would be to cross-breed dynamic tree and tasklist
tree (with hierarchical checkboxes)

[http://developer.yahoo.com/yui/examples/treeview/tasklist.html](http://developer.yahoo.com/yui/examples/treeview/tasklist.html)

so I will have hierarchical checkboxes (who "know" about parents and children, and are dynamically loaded via AJAX/AJAJ on request. I have server side solved no problem, client is killing me, my brain hurts, and reading YUI API does not give any clues. I tried to post to Yahoo Devel Network [ydn-javascript] but no responses.

---

