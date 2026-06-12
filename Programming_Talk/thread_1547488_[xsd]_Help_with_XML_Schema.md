---
title: "[xsd] Help with XML Schema"
date: 2010-08-06
forum: Programming Talk
---

### Post by hobbes84k on 2010-08-06
I've been trying to learn the basics behind XML Schema files in order to validate XML files and prevent errors before they occur. But there's this one particular thing I've been trying to do and nothing I have tried so far has worked.

Here is a simplified version of the XML I am trying to validate:
```

<ResultCollection>
  <Result type="web">
    <-- Stuff -->
  </Result>
  <Result type="image">
    <-- Stuff -->
  </Result>
  <Result type="video">
    <-- Stuff -->
  </Result>
  <Result type="news">
    <-- Stuff -->
  </Result>
</ResultCollection>
```

It has to be those four results, and those results have to be in that order. So here's what I currently have:

```

  <xs:complexType name="ResultCollection">
    <xs:sequence>
      <xs:element name="Result" type="ResultType" minOccurs="4" maxOccurs="4" />
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="Result">
    <xs:sequence>
      <-- Stuff -->
    </xs:sequence>
    <xs:attribute name="name">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="web"/>
          <xs:enumeration value="images"/>
          <xs:enumeration value="video"/>
          <xs:enumeration value="news"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
```

While this way of doing it insures that each result has a name attribute of one of my four accepted values, it doesn't insure that they all exist or what order that they are in. An XML file could have four web results or any other combination you could think of.

However, as I have said above, nothing else I have tried has been valid schema code. Below is one attempt I tried that failed:

```

  <xs:complexType name="ResultCollection">
    <xs:sequence>
      <xs:element name="Result" type="WebResultType" minOccurs="1" maxOccurs="1" />
	  <xs:element name="Result" type="ImageResultType" minOccurs="1" maxOccurs="1" />
	  <xs:element name="Result" type="VideoResultType" minOccurs="1" maxOccurs="1" />
	  <xs:element name="Result" type="NewsResultType" minOccurs="1" maxOccurs="1" />
    </xs:sequence>
  </xs:complexType>
```

And I defined each new type to be a type that used inheritance to have the same stuff but differed by the name attribute. I thought I had solved it. Nope. If the node is named "Result" then it has to be the same type as all the other nodes named result. It doesn't matter that they inherit from the same type, they have to be the exact same type.

So, I'm asking the experts out there. What should I do to specify the attributes in this way? Thanks in advance for your help.

---

### Post by Reiger on 2010-08-06
It's been some time since I've looked at XSD's (and I loathe 'em: they're ugly as sin and can't do co-constraints properly); however, a quick refresh course courtesy of w3c schools suggests to remove minOccurs & maxOccurs attributes from your particular failed attempt:

```

<xs:complexType name="ResultCollection">
  <xs:sequence>
    <xs:element name="Result" type="WebResultType"/>
    <xs:element name="Result" type="ImageResultType"/>
    <xs:element name="Result" type="VideoResultType"/>
    <xs:element name="Result" type="NewsResultType"/>
  </xs:sequence>
</xs:complexType>

```

---

### Post by hobbes84k on 2010-08-06
You got my hopes up that it was a simple solution like that, but I still get an error: 

> Elements with the same name and in the same scope must have the same type

---

### Post by hobbes84k on 2010-08-10
I guess I'll ping this one more time to see if anyone else has any suggestions. Here is the relevent part of my schema as it currently stands.

```

  <xs:complexType name="ResultCollection">
    <xs:sequence>
      <xs:element name="Result" type="WebResultType" />
	  <xs:element name="Result" type="ImageResultType" />
	  <xs:element name="Result" type="VideoResultType" />
	  <xs:element name="Result" type="NewsResultType" />
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="ResultType">
    <xs:sequence>
      <-- Stuff -->
    </xs:sequence>
  </xs:complexType>
  
  <xs:complexType name="WebResultType">
	<xs:complexContent>
		<xs:extension base="ResultType">
			<xs:attribute name="name" fixed="web"/>
		</xs:extension>
	</xs:complexContent>
  </xs:complexType>
  
  <xs:complexType name="ImageResultType">
	<xs:complexContent>
		<xs:extension base="ResultType">
			<xs:attribute name="name" fixed="images"/>
		</xs:extension>
	</xs:complexContent>
  </xs:complexType>
  
  <xs:complexType name="VideoResultType">
	<xs:complexContent>
		<xs:extension base="ResultType">
			<xs:attribute name="name" fixed="video"/>
		</xs:extension>
	</xs:complexContent>
  </xs:complexType>
  
  <xs:complexType name="NewsResultType">
	<xs:complexContent>
		<xs:extension base="ResultType">
			<xs:attribute name="name" fixed="news"/>
		</xs:extension>
	</xs:complexContent>
  </xs:complexType>

```

And here's the exception I get when I run System.Xml.XmlDocument.Validate using this schema.

```

System.Xml.Schema.XmlSchemaValidationException: Elements with the same name and in the same scope must have the same type.
   at System.Xml.Schema.XmlSchemaValidator.SendValidationEvent(XmlSchemaValidationException e, XmlSeverityType severity)
   at System.Xml.Schema.XmlSchemaValidator.RecompileSchemaSet()
   at System.Xml.Schema.XmlSchemaValidator.Init()
   at System.Xml.Schema.XmlSchemaValidator..ctor(XmlNameTable nameTable, XmlSchemaSet schemas, IXmlNamespaceResolver namespaceResolver, XmlSchemaValidationFlags validationFlags)
   at System.Xml.DocumentSchemaValidator.CreateValidator(XmlSchemaObject partialValidationType, XmlSchemaValidationFlags validationFlags)
   at System.Xml.DocumentSchemaValidator.Validate(XmlNode nodeToValidate)
   at System.Xml.XmlDocument.Validate(ValidationEventHandler validationEventHandler, XmlNode nodeToValidate)

```

Any suggestions out there for getting past this pointless requirement of schemas?

---

