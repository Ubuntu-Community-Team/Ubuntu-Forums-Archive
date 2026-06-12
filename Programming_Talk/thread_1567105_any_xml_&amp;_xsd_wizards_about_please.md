---
title: "any xml &amp; xsd wizards about please?"
date: 2010-09-03
forum: Programming Talk
---

### Post by muteXe on 2010-09-03
Hiya,

Sample xml:
```

    <Logging>
      <LoggingLevel level="low" />
      <LoggingSystemLocal file="filetx.log" directory="/proj/log" permissions="0600" />
    </Logging>

```

and corresponding xsd (auto-generated):

```

                          <xs:element name="LoggingLevel">
                            <xs:complexType>
                              <xs:attribute name="level" type="xs:string" use="required" />
                            </xs:complexType>
                          </xs:element>
                          <xs:element name="LoggingSystemLocal">
                            <xs:complexType>
                              <xs:attribute name="file" type="xs:string" use="required" />
                              <xs:attribute name="directory" type="xs:string" use="required" />
                              <xs:attribute name="permissions" type="xs:unsignedShort" use="required" />
                            </xs:complexType>
                          </xs:element>

```

i am trying to apply enumerations to certain attiributes.  For example, I only want the values "low" and "high" to be allowed for logging level.

I've read loads of pages and can't enumerations to work for some reason.  Something like the 2nd green box on this site: [http://www.w3schools.com/schema/schema_complex.asp](http://www.w3schools.com/schema/schema_complex.asp).  I'm thinking that as i'm trying to assign enums and min and max values to attributes, rather than elements, i need to do something extra but cant see what.
Anyone have any ideas?  I'm a xml/xsd noob.

Many thanks in advance,

Tom

---

### Post by Reiger on 2010-09-03
See here: [http://www.w3schools.com/schema/schema_facets.asp](http://www.w3schools.com/schema/schema_facets.asp)

---

### Post by stylishpants on 2010-09-03
I have no idea if you have design flexibility here, but I'll toss in a personal opinion anyway.

This is poor XML document design.  Library support for handling of attributes tends to be less consistent between libraries and more of a pain to use, validate and maintain than just plain tags.  

After designing a few XML-based systems using xsds and some other schema formats, I'm at the point where I avoid using attributes whenever possible.  The code to validate and parse ends up simpler to read and maintain this way.

Personally, if possible, I would take this:
```
    <Logging>
      <LoggingLevel level="low" />
      <LoggingSystemLocal file="filetx.log" directory="/proj/log" permissions="0600" />
    </Logging>
```

and change it to work like this:
```
    <Logging>
      <LoggingLevel>low</LoggingLevel>
      <LoggingSystemLocal>
        <file>filetx.log</file>
        <directory>/proj/log</directory>
        <permissions>0600</permissions>
      </LoggingSystemLocal>
    </Logging>
```

Certainly this approach is more verbose, but the payoff is simpler parsing code and simpler schemas.  You avoid some darker, less-used parts in the libraries that lead to weird bugs and limitations.

I think you might find an answer to your question but I also think you might be better off not needing to look for one.  This likely won't be the last issue you run into.

---

### Post by mendhak on 2010-09-04
Try this:

```
 <xs:element name="LoggingLevel">
  <xs:complexType>
    <xs:attribute name="level" type="xs:string" use="required">
     <xs:simpleType>
      <xs:restriction base="xs:string">
       <xs:enumeration value="low" />
       <xs:enumeration value="medium" />
       <xs:enumeration value="high" />
      </xs:restriction>
     </xs:simpleType>
    </xs:attribute>
  </xs:complexType>
 </xs:element>
```

---

### Post by muteXe on 2010-09-06
Thanks for all the replies.

@mendhak:  i get an error/warning on the '<xs:attribute' line saying "The type attribute cannot be present with either simpleType or complexType".  When i say "error/warning" i mean it gets underlined in blue (am opening up the xsd in visual studio).

@Reiger:  Although it says "Restrictions are used to define acceptable values for XML elements or attributes" at the top of that page it doesn't give any examples using attributes, they are all elements.  When i try and use the same kind of method with attributes I get errors similar to above.

@stylishPants: I'm not really sure if i have design flexibility to be honest.  I've just joined a new group at work, been given some xml files, and told to build a schema from these files.  I don't know much about this stuff, but I too would have preferred elements over attributes.  I will try this locally first, and see if i can get these damn restrictions working on elements rather than attributes.  If it works i'll talk to the boss.

Many thanks again all,

Tom

---

