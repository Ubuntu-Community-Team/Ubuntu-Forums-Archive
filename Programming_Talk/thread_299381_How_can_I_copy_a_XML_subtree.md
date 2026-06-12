---
title: "How can I copy a XML subtree?"
date: 2006-11-14
forum: Programming Talk
---

### Post by mesh2005 on 2006-11-14
I want to copy a subtree from document A to document B. I tried to use ```
XML::DOM
``` but I got the error:
"```
XML::DOM::DOMException(Code=4, Name=WRONG_DOCUMENT_ERR, Message=nodes belong to different documents)"
```
I tried to use the ```
XML::LibXML
``` but I got the error:
```
XML::LibXML::Document::importNode() -- node is not a blessed SV reference
```
Could you please help me to find how to copy the subtree?
Thank you

---

### Post by mesh2005 on 2006-11-15
I solved it, here is the code:
```

$node = $source_node->cloneNode(1);
$node->setOwnerDocument($body->getOwnerDocument() );
$body->appendChild($node);

```
The setOwnerDocument is the golden key, if it was not used , the node wouldn't be added and an error would be generated about adding a node to a different document

---

