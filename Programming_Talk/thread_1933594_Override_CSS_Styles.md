---
title: "Override CSS Styles"
date: 2012-02-29
forum: Programming Talk
---

### Post by jailbait on 2012-02-29
If I have a css file imported at the <head>, how can I override it without using inline?

---

### Post by juancarlospaco on 2012-02-29
[SIZE="3"]Server Side:[/SIZE]

use something like:
```
<style> .myCustomCSS { font: normal 12px Ubuntu; }; </style>
```


[SIZE="3"]Client Side:[/SIZE]

```

// ==UserScript==
// @name          OverrideCSS
// @description	  Override CSS, in this Example forces 12px Ubuntu font on the customz class
// @include       http://*
// @include       https://*
// ==/UserScript==

//
myNode = document.createElement('style');
myNode.innerHTML = '.customz{ font: normal 12px Ubuntu; };';
document.getElementsByTagName("body")[0].appendChild(myNode);
//

// name this example.user.js

```

into an interactive JavaScript Session:

```

**myNode = document.createElement('style');**
<style></style>
**myNode.innerHTML = '.customz{ font: normal 12px Ubuntu; };';**
".customz{ font: normal 12px Ubuntu; };"
**document.getElementsByTagName("body")[0].appendChild(myNode);**
<style>.customz{ font: normal 12px Ubuntu; };</style>

```

:)

---

### Post by Dimarchi on 2012-03-03
As juancarlospaco explained, that is one way. If you wish to completely avoid Javascript, there is another way. You probably know that there is a certain level of order when it comes to applying CSS stuff...linked CSS file, CSS in the HEAD element, and CSS in the specific element (the inline option) - each stronger that the previous. You can utilise that. If you have two linked CSS files which have the same specific id, class, or element styled in them, the styling in the latter linked CSS file is the one applied to the id, class, or element in question, overriding the styling in the previous linked CSS file.

That is my hazy recollection of the issue. :)

---

### Post by jailbait on 2012-03-04
> **juancarlospaco said:**
> [SIZE=3]Server Side:[/SIZE]

use something like:
```
<style> .myCustomCSS { font: normal 12px Ubuntu; }; </style>
```
[SIZE=3]Client Side:[/SIZE]

```

// ==UserScript==
// @name          OverrideCSS
// @description      Override CSS, in this Example forces 12px Ubuntu font on the customz class
// @include       http://*
// @include       https://*
// ==/UserScript==

//
myNode = document.createElement('style');
myNode.innerHTML = '.customz{ font: normal 12px Ubuntu; };';
document.getElementsByTagName("body")[0].appendChild(myNode);
//

// name this example.user.js

```into an interactive JavaScript Session:

```

**myNode = document.createElement('style');**
<style></style>
**myNode.innerHTML = '.customz{ font: normal 12px Ubuntu; };';**
".customz{ font: normal 12px Ubuntu; };"
**document.getElementsByTagName("body")[0].appendChild(myNode);**
<style>.customz{ font: normal 12px Ubuntu; };</style>

```:)
ah!
that does it :) .
Livefyre doesn't work properly in dark themes :)

---

