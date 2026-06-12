---
title: "XML Schema Problem"
date: 2010-01-19
forum: Programming Talk
---

### Post by dvlchd3 on 2010-01-19
I just started learning XML schemas.  I love the extensbility compared with DTDs, however, the complexity is killing me!  (I'm sure in due time it will become natural, but I had a far easier time picking up Perl then these darn schemas!)

Anyway, enough of my venting.  I'm attempting to define an element that can occur any number of times throughout the XML document.  The book I've been using, as well as several tutorials (including W3C's) shows that maxOccurs attribute can be applied to the 'element' element.  maxOccurs contains the maximum number of times that element can be defined within the relating XML document.  If the element can be declared as many times as needed, maxOccurs should be set to "unbounded".  However, every XML schema validator I've used (w3c and [http://www.validome.org/grammar/validate/](http://www.validome.org/grammar/validate/)) throw an error saying the value is not within the enumeration [0, 1].  Oddly, if I set maxOccurs to anything besides 1 or 0, the error occurs....

Lines of my schema in question:
```

<xsd:complexType name="ScheduleType">
	<xsd:all>
		<xsd:element name="Item" maxOccurs="unbounded" type="ItemType"/>
	</xsd:all>
	<xsd:attribute name="name" type="xsd:string"/>
</xsd:complexType>
```

The error message: (per w3c)
```

Schema validating with XSV 3.1-1 of 2007/12/11 16:20:05

    * Target: file:/usr/local/XSV/xsvlog/tmpZjv4lvuploaded
         (Real name: schedule.xsd)
    * docElt: {http://www.w3.org/2001/XMLSchema}schema
    * Validation was strict, starting with type [Anonymous]
    * The schema(s) used for schema-validation had
        no errors
    * 1 schema-validity problem was found in the target
       

Problems with the schema-validity of the target

file:/usr/local/XSV/xsvlog/tmpZjv4lvuploaded:8:4: Invalid per cvc-attribute.1.2: attribute type check failed for {None}:maxOccurs: unbounded not in enumeration [0, 1]

```

Can someone please enlighten me?

---

### Post by Arndt on 2010-01-21
> **dvlchd3 said:**
> I just started learning XML schemas.  I love the extensbility compared with DTDs, however, the complexity is killing me!  (I'm sure in due time it will become natural, but I had a far easier time picking up Perl then these darn schemas!)

Anyway, enough of my venting.  I'm attempting to define an element that can occur any number of times throughout the XML document.  The book I've been using, as well as several tutorials (including W3C's) shows that maxOccurs attribute can be applied to the 'element' element.  maxOccurs contains the maximum number of times that element can be defined within the relating XML document.  If the element can be declared as many times as needed, maxOccurs should be set to "unbounded".  However, every XML schema validator I've used (w3c and [http://www.validome.org/grammar/validate/](http://www.validome.org/grammar/validate/)) throw an error saying the value is not within the enumeration [0, 1].  Oddly, if I set maxOccurs to anything besides 1 or 0, the error occurs....

Lines of my schema in question:
```

<xsd:complexType name="ScheduleType">
	<xsd:all>
		<xsd:element name="Item" maxOccurs="unbounded" type="ItemType"/>
	</xsd:all>
	<xsd:attribute name="name" type="xsd:string"/>
</xsd:complexType>
```

The error message: (per w3c)
```

Schema validating with XSV 3.1-1 of 2007/12/11 16:20:05

    * Target: file:/usr/local/XSV/xsvlog/tmpZjv4lvuploaded
         (Real name: schedule.xsd)
    * docElt: {http://www.w3.org/2001/XMLSchema}schema
    * Validation was strict, starting with type [Anonymous]
    * The schema(s) used for schema-validation had
        no errors
    * 1 schema-validity problem was found in the target
       

Problems with the schema-validity of the target

file:/usr/local/XSV/xsvlog/tmpZjv4lvuploaded:8:4: Invalid per cvc-attribute.1.2: attribute type check failed for {None}:maxOccurs: unbounded not in enumeration [0, 1]

```

Can someone please enlighten me?

How about using xsd:sequence instead of xsd:all? And perhaps, if needed, put the maxOccurs="unbounded" on xsd:sequence instead of on the element.

---

### Post by dvlchd3 on 2010-01-21
Thank you!  Changing to <xsd:sequence> did the trick.

---

