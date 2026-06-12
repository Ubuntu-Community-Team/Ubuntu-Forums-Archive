---
title: "XSD Schema... Sequence indicator"
date: 2009-07-13
forum: Programming Talk
---

### Post by xsd_newbie on 2009-07-13
Hi everyone,

I'd like to know how I can modify an existing XSD so it can be more flexible. I have perhaps hundreds of complex elements which are defined with the <sequence> indicator, but the order in which the child elements are given really does not matter. I would like to permit any of the child elements written, but not require them in order (as with sequence indicator), nor require that they are ALL given (as with all indicator). Is there a way I can do this using XSD 2.20?

Bonus question:

I also have at least one complex type defined with <sequence> that contains a "nested" <choice>. If a change can be made to achieve my first goal, will this nested <choice> be affected?

EXAMPLE:

<xsd:complexType name="Sample">
<xsd:sequence>
<xsd:element minOccurs="0" ref="name" />
<xsd:choice>
<xsd:element ref="Person" />
<xsd:element ref="Organization" />
</xsd:choice>
<xsd:element minOccurs="0" maxOccurs="unbounded" ref="Address" />
</xsd:sequence>
<xsd:attribute name="id" type="xsd:ID" use="required" />
</xsd:complexType>

---

