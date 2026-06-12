---
title: "XMLSchema problem with XML document"
date: 2007-06-09
forum: Programming Talk
---

### Post by Samjiman on 2007-06-09
&#65279;Hello. I have this XML document:
```

&#65279;<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<vbtagsconf xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:noNamespaceSchemaLocation="vbtags.xsd">	
	
    <vbtag name="bold" params="false" group="basic">
        <regexp>\[/?b]</regexp>
        <code>&lt;b&gt;</code>
    </vbtag>
    <vbtag name="italic" params="false" group="basic">
        <regexp>\[/?i]</regexp>
        <code>&lt;i&gt;</code>
    </vbtag>

</vbtagsconf>

```

I have this XMLSchema:
```

<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">
	<!-- root element -->
	<xs:element name="vbtagsconf">
		<xs:complexType>
			<xs:sequence minOccurs="1" maxOccurs="unbounded">
				<!-- first tag with three attributes -->
				<xs:element name="vbtag">
					<xs:complexType>
					    <xs:attribute name="name" type="xs:string"/>
					    <xs:attribute name="params" type="xs:string"/>
					    <xs:attribute name="group" type="xs:string"/>
					</xs:complexType>
				</xs:element>
				<!-- next two tags with no attributes -->
				<xs:element name="regexp" type="xs:string"/>
				<xs:element name="code" type="xs:string"/>
			</xs:sequence>			
		</xs:complexType>
	</xs:element>
</xs:schema>

```

When I validate the document against the schema, I get this error message:
"No character data is allowed by content model". What does that mean? What have I done wrong?

Thanks in advance.

---

### Post by neo.patrix on 2007-06-09
I have some experience with XML and Oracle DBMS, probably there is some technical difference between characters and strings. 

Or also there code sum Unicode, non-Unicode character problem. It depends on what is specified in XML file header i.e. <?xml> tag.

---

### Post by Samjiman on 2007-06-09
I gave up eventually and stuck to a DTD. Proper validation of data isn't really necessary for this project I'm working on anyway.

Thanks anyway. :)

---

