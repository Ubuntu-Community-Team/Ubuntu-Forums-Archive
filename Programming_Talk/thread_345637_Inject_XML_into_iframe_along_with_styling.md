---
title: "Inject XML into iframe along with styling"
date: 2007-01-24
forum: Programming Talk
---

### Post by samji on 2007-01-24
Hello everyone.

I am trying to write out the contents of a tag in an XML document to an iframe.
I can do that successfully with the following JavaScript code...

```

function constructMsgBody() 
{
// constuct message body from "message" tags;
// write out to iframe on view message dialog
var message =  msgsfile.getElementsByTagName("message")[msg].firstChild.nodeValue;
var writemsg = parent.frames['msgframe'];
writemsg.document.open();
writemsg.document.write(message);
writemsg.document.close();
}

```

But how can I get the stylesheet (CSS) referenced in the XML document to be applied to what I have injected into the iframe. Do I have to load the line where the stylesheet declaration occurs? This code is for a Firefox extension I am working on, so it only needs to be compatible with Firefox, although a standards compliant way would be best. :) 

Thanks in advance.

---

