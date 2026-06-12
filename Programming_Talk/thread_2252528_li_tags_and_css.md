---
title: "li tags and css"
date: 2014-11-12
forum: Programming Talk
---

### Post by TheodoreP on 2014-11-12
So, it's been awhile since I could actually enjoy in the development of my website. As such I'm trying to rework the navigation of the site and would like to know if it possible to add a hover action to plain li tags without anchor tags linking to other pages? How might I perform this css if it's possible?

---

### Post by papibe on 2014-11-12
Tittle changed to better reflect OP's concern.

Moved to **Programing Talk**.

---

### Post by Lars Noodén on 2014-11-12
(Hmmm.  It's not programming) :)

Anyway, any [HTML or XHTML](http://www.w3.org/TR/html4/index/elements.html) element can use the [**title** attribute](http://www.w3.org/TR/html4/index/attributes.html).  It is the **title** attribute which will give text on mouseover.  If you asign it to **li** then, the user will have to aim for the list bullet or number to see the text.  But if you enclose the text to be affected with **span** or **a name** (an anchor) then the title will apply to a larger block of text.  

```

<ul>
<li><span title="foo">
wed 12.11.2014 21.13.23 +0200
</span>
</li>
</ul>

```

---

### Post by Lars Noodén on 2014-11-13
Or do you mean pulldown menus or some other effect like in the navigation menu here: 
[http://www.ubuntu-fi.org/](http://www.ubuntu-fi.org/)

That's done with something like this:

```

  UL { padding: 0; margin: 0;
       list-style: none; }

  UL LI { float: Left; 
       position: relative;
       width: 10em;
   }

  UL LI UL { top: auto; left: auto;
          position: absolute; 
          display: none;
  }

  UL LI:hover UL { display: block; }

  LI {
    border: thin solid #fff;
    background-color: #222;
  }

```

---

