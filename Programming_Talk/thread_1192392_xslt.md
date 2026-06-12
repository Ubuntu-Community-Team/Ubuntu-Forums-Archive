---
title: "xslt"
date: 2009-06-20
forum: Programming Talk
---

### Post by leblancmeneses on 2009-06-20
how is white space managed in xslt?

I'm going write a code generation tool that 
writes my model from my database.


I would like to create from this code:

 ```

<column name="Name" type="int" />
 
```the following:

```

public Int32 Name
{
    get;
    set;
}

```
i plan to use xslt to "choose" to decide how to convert database types to language types.

my question is can a template provide a pretty output as in that property without

```

public
        Int32
                 Name
{
      get;
       set;
}

```

how is white space managed? in xslt template?

lm

---

### Post by Reiger on 2009-06-20
You could use the following property:
```

<xsl:output method="text" />

```


Combined with a top level variable ```
<xsl:variable name="myindent" select="''" />
``` and indent stuff like so: ```
<xsl:value-of select="$myindent" />
``` Just make sure that you give $myindent a proper value.

If it had been XML you were outputtting things would've been easier:
```

<xsl:output method="xml" indent="yes" />
```

---

### Post by leblancmeneses on 2009-06-21
seems i can also do it using a named template.

except i don't know how to dynamically assign:
_propertyDatatype 

```


    <xsl:template name="CreateProperty">
        <xsl:param name="propertyDatatype" required="yes" />
        <xsl:param name="propertyName" required="yes" />
        public <xsl:value-of select="$propertyDatatype"/> <xsl:value-of select="$propertyName"/>
        {
            get;
            set;
        }
    </xsl:template>

    
    
    <xsl:template match="Columns/Column">
        <xsl:variable name="_propertyDatatype" select="'Int32'" />     
        <xsl:choose>
            <xsl:when test="ColumnType[text()='OrmInt']">
                _propertyDatatype = 'Int32'     
            </xsl:when>
            <xsl:when test="ColumnType[text()='OrmTextShort']">
                _propertyDatatype = 'String'             
            </xsl:when>
            <xsl:otherwise>
                _propertyDatatype = 'Unknown'                      
            </xsl:otherwise>
        </xsl:choose> 
        <xsl:call-template name="CreateProperty">
            <xsl:with-param name="propertyDatatype" select="$_propertyDatatype"/>
            <xsl:with-param name="propertyName" select="@Name"/>
        </xsl:call-template>
    </xsl:template>

```

anyone?


what are the popular xslt designers ... kinda like wysiwyg

---

### Post by Reiger on 2009-06-21
You are dealing with a mostly functional programming language. You do not have destructive update: you define the value of your variable once, and only once. Fortunately for you: the value of your variable may be a function of its input:
```

<xsl:variable name="foo">
  <xsl:choose>
    <xsl:test when="local-name() = 'foo'"><xsl:value-of select="'case foo'"/></xsl:test>
    <xsl:test when="local-name() = 'bar'"><xsl:value-of select="'case bar'"/></xsl:test>
    <xsl:otherwise><xsl:value-of select="'default'"/></xsl:otherwise>
  </xsl:coose>
</xsl:variable>

```

And it can be much more complex than that: you could have the result of a template call on the current node be stored in $foo this way, to be used later on.

EDIT: Also I am not aware of `designers' like that. While it is in theory possible to write programs that generate your XSLT on the fly (on rules defined via drag-drop or whatever have you); I doubt it is very widespread. You don't see many generic 'visual designers' for writing generic C solutions to a given problem either.

---

### Post by leblancmeneses on 2009-06-22
this stuff is pretty impressive!


quick code review:

currently accessing ancestor is very coupled to xml layout

instead of: ../../../../../  is there a way i can say 
(select-parent-of-type="Project")/@NameSpace

rather than current implementation?
```

    <xsl:template match="/Projects/Project/Database/Schemas/Schema/Tables/Table">
namespace <xsl:value-of select="../../../../../@NameSpace"/>
{
    public class <xsl:value-of select="@Name"/>
    {
        <xsl:for-each select="Columns/Column">
            <xsl:apply-templates select="." />
        </xsl:for-each>
    }
}
    </xsl:template>

```




clearing up spacing in xslt.
right now i'm having to use 'concat' to achieve proper spacing between:
Int32 and column name.

maybe this is specific to msxsl.exe i'm using or is spacing ignored in the line once xsl tag is encountered?
```


    to get a property to have space:
        public Int32 customer_id
        {
            get;
            set;
        }


  I had to use concat a ' ' space else it would look like this:
        public Int32customer_id
        {
            get;
            set;
        }





    <xsl:template name="CreateProperty">
        <xsl:param name="propertyDatatype" required="yes" />
        <xsl:param name="propertyName" required="yes" />
        public <xsl:value-of select="concat($propertyDatatype, ' ')"/> <xsl:value-of select="$propertyName"/>
        {
            get;
            set;
        }
    </xsl:template>


```

---

### Post by Reiger on 2009-06-22
Well there are ways, all of them boil down to a more comprehensive understanding of XPath. [http://www.w3schools.com/xpath/xpath_axes.asp](http://www.w3schools.com/xpath/xpath_axes.asp)

For instance you need not look at a DOM tree in terms of `how many ancestors came before me?', but you could also look at it in terms of `do I have an ancestor called Fred?': e.g.:
test.xml:
```

<?xml-stylesheet type="text/xsl" href="test.xsl"?>
<tree><fred><frank><me /></frank></fred>
<frank><me /></frank></tree>

```

test.xsl:
```

<xsl:transform version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="/">
    <test>
      <xsl:apply-templates />
    </test>
  </xsl:template>
  
  <xsl:template match="//me">
    <result>
      <xsl:choose>
	<xsl:when test="ancestor::fred">
	  <xsl:text>Bingo!</xsl:text>
	</xsl:when>
	<xsl:otherwise>
	  <xsl:text>Nope!</xsl:text>
	</xsl:otherwise>
      </xsl:choose>
    </result>
  </xsl:template>
</xsl:transform>
```

Use a browser like Opera to see the result (by browsing to file://localhost/[some directory here]/test.xml)

---

### Post by leblancmeneses on 2009-06-27
xslt is getting pretty large.

I need to do something as follows

any template in scope of .  -> /Projects/Project
is evaluated with passed variable propertyProjectGUID  // auto generated by function - should be consistent across all templates

and output is piped to result-document?

code as follows would be the goal
```

        <xsl:variable name="projectname" select="concat($projectDirectory, '/', $projectNameSpace, '.csproj')" />
        <xsl:result-document href='{$projectname}' format="textFormat">
            <xsl:apply-templates select=".">
                <xsl:with-param name="propertyProjectGUID" select="$projectguid"/>
            </xsl:apply-templates>
        </xsl:result-document>

```

---

### Post by Reiger on 2009-06-27
If you want to basically `dynamically include' other XML documents there are XIncludes. Note that this will require you to adopt the more formal and verbose element declarations.

I have never done this extensively myself so I am probably wrong in the details; take care to ensure that the code is correct yourself:
```

<xsl:element name="include" namespace="this-is-wrong-look-up-the-correct-Xinclude-ns">
<xsl:attribute name="parse"><!-- include as plain text, change to XML or remove to include as XML -->
<xsl:value-of select="'text'/>
</xsl:attribute>
<xsl:attribute name="href"><xsl:value-of select="$doc-to-include"/></xsl:attribute>
</xsl:element>

```

That should generate something like:
```
<xi:include xmlns:xi="this-is-wrong-look-up-the-correct-Xincludes-ns" parse="text" href="somefile" />

```
Then you may either need to pass it through something to resolve the include, or you may already get that for free. That will depend on the tools/libraries you use.

---

