---
title: "problem with PHP simplexml and doxygen generated XML"
date: 2009-04-03
forum: Programming Talk
---

### Post by hessiess on 2009-04-03
I have bean trying to right a PHP script to generate XHTML code from the class documentation xml files created by Doxygen(the HTML it outputs is invalid, messy and virtually imposable to integrate into another web page). One thing has bean causing problems, the tags which start with `@', for example:

```

SimpleXMLElement Object
(
    [@attributes] => Array
        (
            [kind] => function
            [id] => classhello_1f06929bd13d07b414a8be07c6db88074
            [prot] => private
            [static] => no
            [const] => no
            [explicit] => no
            [inline] => yes
            [virt] => non-virtual
        )
    ...

```

I cannot seam to find a way to access these with simplexml, the following code generates a syntax error for example.

```

print_r($xml->compounddef->sectiondef->memberdef[1]->@attributes);

```

Any advice would be gratily appreciated.

---

### Post by Arndt on 2009-04-03
> **hessiess said:**
> I have bean trying to right a PHP script to generate XHTML code from the class documentation xml files created by Doxygen(the HTML it outputs is invalid, messy and virtually imposable to integrate into another web page). One thing has bean causing problems, the tags which start with `@', for example:

```

SimpleXMLElement Object
(
    [@attributes] => Array
        (
            [kind] => function
            [id] => classhello_1f06929bd13d07b414a8be07c6db88074
            [prot] => private
            [static] => no
            [const] => no
            [explicit] => no
            [inline] => yes
            [virt] => non-virtual
        )
    ...

```

I cannot seam to find a way to access these with simplexml, the following code generates a syntax error for example.

```

print_r($xml->compounddef->sectiondef->memberdef[1]->@attributes);

```

Any advice would be gratily appreciated.

I'm learning PHP, and I found two ways. One is to use

```
$attr = '@attributes';
print_r($xml->compounddef->sectiondef->memberdef[1]->$attr);
```

The other is to use the braces syntax:

```
print_r($xml->compounddef->sectiondef->memberdef[1]->{'@attributes');
```

(The '' can be left out there, it seems, but I don't know if one should.)

What you say about Doxygen is interesting - we are going to use it in a current project, but I know nothing about it yet.

---

### Post by hessiess on 2009-04-03
> **Arndt said:**
> I'm learning PHP, and I found two ways. One is to use

```
$attr = '@attributes';
print_r($xml->compounddef->sectiondef->memberdef[1]->$attr);
```

The other is to use the braces syntax:

```
print_r($xml->compounddef->sectiondef->memberdef[1]->{'@attributes');
```

(The '' can be left out there, it seems, but I don't know if one should.)

What you say about Doxygen is interesting - we are going to use it in a current project, but I know nothing about it yet.

Thanks for your advice, however both of those methods just return:
```

SimpleXMLElement Object
(
)

```

insted of the @attributes array.

[edit]
This works:
```

print_r($xml->compounddef->sectiondef->memberdef[1]->attributes());

```

[http://uk.php.net/manual/en/function.simplexml-element-attributes.php](http://uk.php.net/manual/en/function.simplexml-element-attributes.php)

---

