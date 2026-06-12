---
title: "jaxb trouble"
date: 2008-07-23
forum: Programming Talk
---

### Post by rogier.de.groot on 2008-07-23
Is anyone here familiar with JAXB? I've got a collection of element in a bean that comes out wrong:

<elements>
  <element xsi:type="foo" />
  <element xsi:type="bar" />
</elements>

But it should come out as:

<elements>
  <foo />
  <bar />
</elements>

Anyone know how to make JAXB do that? All elements in the collection extends the same abstract base class ("element" in the example).

TIA

---

