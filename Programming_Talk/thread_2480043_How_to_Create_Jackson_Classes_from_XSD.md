---
title: "How to Create Jackson Classes from XSD"
date: 2022-10-17
forum: Programming Talk
---

### Post by ronakmehta on 2022-10-17
Jackson does not provide a tool for generating Jackson classes from XSD or JSON, as JAXB does for a specific XSD.


The JAXB class generator was used to generate a set of classes for the specified XSD schema. For polymorphic types, for example, JAXB provides the following annotation to identify the name based on the name of an XML element.
```
[COLOR=#141414][FONT=inherit]@XmlElements[/FONT][/COLOR][COLOR=#141414][FONT=inherit]([/FONT][/COLOR][COLOR=#141414][FONT=inherit]{[/FONT][/COLOR]
    @XmlElement(name = [COLOR=#AA1111]"Dog"[/COLOR], type = [COLOR=#0000FF]Dog[/COLOR].[COLOR=#770088]class[/COLOR]),
    @XmlElement(name = [COLOR=#AA1111]"Cat"[/COLOR], type = [COLOR=#0000FF]Cat[/COLOR].[COLOR=#770088]class[/COLOR])
}) [COLOR=#770088][FONT=inherit]protected[/FONT][/COLOR][COLOR=#0000FF][FONT=inherit]List[/FONT][/COLOR][COLOR=#141414][FONT=inherit]<[COLOR=#0000FF]Animal[/COLOR]>[/FONT][/COLOR][COLOR=#141414][FONT=inherit] animal[/FONT][/COLOR][COLOR=#141414][FONT=inherit];[/FONT][/COLOR]
```

Can such courses be offered in Jackson? Specifically, determining the type based on the name of an XML element.

---

