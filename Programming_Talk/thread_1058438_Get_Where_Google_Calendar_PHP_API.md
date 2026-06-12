---
title: "Get Where: Google Calendar PHP API"
date: 2009-02-02
forum: Programming Talk
---

### Post by secondstage on 2009-02-02
For some blasted reason, I can not find a way to see where an event takes place using the Google Calendar API for PHP.

I tried to print_r the $event->where object to maybe see how to access it, but no avail. Here is an example of what "print_r($event->where)", where $event is definitely the correct value for the event object, looks like.

```
Array ( 
    [0] => Zend_Gdata_Extension_Where Object ( 
        [_rootElement:protected] => where 
        [_label:protected] => 
        [_rel:protected] => 
        [_valueString:protected] => School
        [_entryLink:protected] => 
        [_rootNamespace:protected] => gd 
        [_rootNamespaceURI:protected] => 
        [_extensionElements:protected] => Array ( ) 
        [_extensionAttributes:protected] => Array ( ) 
        [_text:protected] => 
        [_namespaces:protected] => Array ( 
            [atom] => http://www.w3.org/2005/Atom 
            [app] => http://purl.org/atom/app# 
            [openSearch] => http://a9.com/-/spec/opensearchrss/1.0/ 
            [rss] => http://blogs.law.harvard.edu/tech/rss 
            [gd] => http://schemas.google.com/g/2005 
        ) 
    ) 
) 
```

---

### Post by slavik on 2009-02-03
is this it?

```
        [_valueString:protected] => School
```

---

### Post by secondstage on 2009-02-03
I cannot call it though. Would it just be...
```
$event->where->_valueString
```
or do you include the squae brackets, or exclude the underscore?
I do not have much experience with objects, so sorry for my ineptitude.

---

### Post by secondstage on 2009-02-03
I got it. To access the value use...
```
$event->where->valueString
```

---

