---
title: "xml schema queston"
date: 2009-07-11
forum: Programming Talk
---

### Post by badperson on 2009-07-11
Okay, this should be really easy, but I'm not finding a simple solutions. 

I have a <description> element, which has a child <title> element, and after that I want to have any combination of <heading> and/or <para> elements. 

Here's my schema definition: 

```
<!-- add richer description element -->
<xs:complexType name="descriptionType">
	<xs:sequence>
		<xs:element name="title"/>
		<xs:element name="text-element" type="descriptionTextType" maxOccurs="unbounded"/>
	</xs:sequence>

</xs:complexType>

<xs:complexType name="descriptionTextType">
	<xs:sequence>
		<xs:element name="heading" minOccurs="0"/>
		<xs:element name="para" maxOccurs="unbounded"/>
	</xs:sequence>
</xs:complexType>
```

Right now I got it to work by having a <text-element> tag that can have one optional <heading> tag followed by any number of paras. 

Is there a way to do it without having the text-element tag? 
thanks, 
bp

---

