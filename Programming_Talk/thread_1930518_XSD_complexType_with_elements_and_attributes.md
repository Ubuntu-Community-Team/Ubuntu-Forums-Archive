---
title: "XSD complexType with elements and attributes"
date: 2012-02-23
forum: Programming Talk
---

### Post by laus_deo on 2012-02-23
I am trying to make an XSD file that can validate XML elements that have attributes. For example 

XML file:


```

<task>
         <constraint name="constraint"> 50 </constraint>
</task>

```

XSD file so far:

```

<xsd:schema>
      <xsd:element name="task">
           <xsd:complexType>
               <xsd:sequence>
                     <xsd:element name="constraint" type="xsd:integer" />
               </xsd:sequence>
           </xsd:complexType>
     </xsd:element>
</xsd:schema>

```

I know I left out some information that goes above all that, but this is the basic information. I have searched online for hours and found a few things, but nothing I've found seems to work. 

Thanks.

---

### Post by Arndt on 2012-02-24
> **laus_deo said:**
> I am trying to make an XSD file that can validate XML elements that have attributes. For example 

XML file:


```

<task>
         <constraint name="constraint"> 50 </constraint>
</task>

```

XSD file so far:

```

<xsd:schema>
      <xsd:element name="task">
           <xsd:complexType>
               <xsd:sequence>
                     <xsd:element name="constraint" type="xsd:integer" />
               </xsd:sequence>
           </xsd:complexType>
     </xsd:element>
</xsd:schema>

```

I know I left out some information that goes above all that, but this is the basic information. I have searched online for hours and found a few things, but nothing I've found seems to work. 

Thanks.

Something like this:

```
      <xs:element name="task">
           <xs:complexType>
               <xs:sequence>
                     <xs:element name="constraint">
		       <xs:complexType>
			 <xs:simpleContent>
			   <xs:extension base="xs:integer">
			     <xs:attribute name="name" type="xs:string" />
			   </xs:extension>
			 </xs:simpleContent>
		       </xs:complexType>
		     </xs:element>
               </xs:sequence>
           </xs:complexType>
     </xs:element>
```

I got it from [http://www.w3schools.com/schema/schema_complex_text.asp](http://www.w3schools.com/schema/schema_complex_text.asp)

---

