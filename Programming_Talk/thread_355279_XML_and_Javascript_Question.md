---
title: "XML and Javascript Question"
date: 2007-02-07
forum: Programming Talk
---

### Post by neilp85 on 2007-02-07
I'm working on a Firefox extension and ran into an issue I couldn't figure out after a decent amount of searching. Is it possible to load a variable from Javascript to be the value of an attribute of an XML element (XUL specifically). Basically I would like to do something like the following:
```
...
<button id="foo" label="bar" disable="value from javascript"/>
...
```

---

### Post by runningwithscissors on 2007-02-07
> **neilp85 said:**
> I'm working on a Firefox extension and ran into an issue I couldn't figure out after a decent amount of searching. Is it possible to load a variable from Javascript to be the value of an attribute of an XML element (XUL specifically). Basically I would like to do something like the following:
```
...
<button id="foo" label="bar" disable="value from javascript"/>
...
```

Strange requirement.

I am not familiar with XUL much, but since it is just XML, I suppose you could manipulate the XML doc at runtime using Javascript's DOM tools, i.e. load the doc without any value for the "disabled" attribute and then set it from javascript.

---

### Post by neilp85 on 2007-02-07
Maybe some more explain would. My extension is used for visually browsing the DOM of the currently loaded webpage. It's meant to be a very simple interface for extracting content. The user interface is specified in XUL and controlled by Javascript. What I want to do is disable buttons if the user can't search the webpages DOM any further in a direction relative to their current position. The position and pruned DOM is maintained in my Javascript.

---

### Post by SuperMike on 2007-02-07
In the XUL page, or through XUL's way to load a separate Javascript page, add in:

<script>
document.getElementById('foo').disabled = true;
</script>


<button id="foo" name="foo" label="bar"/>

BTW, added "name" as well as "id" above because sometimes I find I need that occasionally.

Is that what you're looking for?

Another route is through an ENTITY DTD linkage like you see when you view the source for this page:

about:mozilla

...which has linkage to this DTD URL that sets the values:

chrome://global/locale/mozilla.dtd

---

### Post by neilp85 on 2007-02-07
Thanks for the advice Mike, I ended up doing something very similar to this. The main issue was my view of the problem. Trying to get the value from Javascript from within the XML rather than exporting the value to XML from Javascript.

---

