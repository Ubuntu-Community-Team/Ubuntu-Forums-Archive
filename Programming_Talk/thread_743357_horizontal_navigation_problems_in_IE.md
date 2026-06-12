---
title: "horizontal navigation problems in IE"
date: 2008-04-02
forum: Programming Talk
---

### Post by bmeyer on 2008-04-02
If anybody could help with this, I'd SINCERELY appreciate it.

[http://www.groomgroove.com/index2.php](http://www.groomgroove.com/index2.php)

The red, horizontal navigation works perfectly in Firefox, but in IE6 the list refuses to be horizontal.  It's a unordered list with the list items floating to the left.

The stylesheet controlling the navigation is:
[http://www.groomgroove.com/style_common.css](http://www.groomgroove.com/style_common.css)

---

### Post by kostkon on 2008-04-02
Try to wrap the *<ul>* with id *#sddm* around a *<div>* (let's name it *#menuwrapper*) and float it, i.e.:
```
#menuwrapper { 
              float: left;
              etc.
}
```
also, better put the *list-style: none* in this *<ul>*, i.e.:
```
#sddm {
	       margin: 0;
	       padding: 0;
	       z-index: 30;
               list-style: none;
}
```
Also float the *<a>*s with class *.sddm_parent*, i.e.:
```
.sddm_parent {
	     display: block;
	     height:21px;
             float: left;
	     padding:8px 10px 0 10px;
	     color:#fff;
	     font-size:12px;
	     border-left:2px solid #601407;
	     text-decoration: none;
}
```

I know that I'm recommending you to float a lot, but give it a try. I believe it will fix the problem with IE, as long as other things don't break the float, like padding or margin conflicts, etc.

---

