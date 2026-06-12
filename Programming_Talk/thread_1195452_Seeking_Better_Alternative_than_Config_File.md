---
title: "Seeking Better Alternative than Config File"
date: 2009-06-23
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-06-23
I am making a program (has to be in C++) and I want it to be easy to configure.  The program will have several settings and a few ideas on how to store these settings popped into mind: text file, XML, SQLLite database.  Basically, I will need to generate a config file which will basically hold a bunch of attributes or properties.  I might want to store something like this:

define DataType HexDataType:
case "0" -> "0000"
case "1" -> "0001"
case "2" -> "0010"
case "3" -> "0011"
...
case "E" -> "1110"
case "F" -> "1111"

Or I might want to define something like this:
length 220
width 214

Or I might want to define a range like this:
define September 9/1 9/31

The program can specify how things are defined and will expect certain parameters to be defined.  For example, the program might be expecting a parameter called length that has one value and another parameter called September which has 2 values, but it will not know how many datatypes will be defined.  

Based on these requirements, I think XML might be the easiest way to do this, but the XML files can look a bit ugly.  Is there an application which can make the XML file?  I ask this because other people will need to setup the configuration info and I would like that to be as simple as possible.  For example, there is a SQL Lite Browser application which makes setting up SQL Lite databases easy.  I like the XMLEncoder / XMLDecoder features of Java, but not sure if something that simple exists for C++.

---

### Post by michael_1234 on 2009-06-23
There are (too) many C/C++ XML libraries. You would just have to choose...
  * List of: [http://www.ibm.com/developerworks/xml/library/x-ctlbx.html](http://www.ibm.com/developerworks/xml/library/x-ctlbx.html)
  * Two options: 
        => [http://xerces.apache.org/xerces-c/](http://xerces.apache.org/xerces-c/)
        => [http://expat.sourceforge.net/](http://expat.sourceforge.net/)

But adding xml for config normally just makes things convoluted. It's easy for programs to parse & generate, but tough (plain impractical) for humans to use.  If humans will edit the file, go with plain (non-xml) text.  

...And there's a lot to do with "plain" old properties (e.g., key / value pairs); e.g., see: libconfuse,
   * [http://www.nongnu.org/confuse/tutorial-html/index.html](http://www.nongnu.org/confuse/tutorial-html/index.html)
   * [http://www.nongnu.org/confuse/](http://www.nongnu.org/confuse/)

thanks,
-m

---

### Post by fr4nko on 2009-06-24
I believe a good idea would be to use [YAML]("http://www.yaml.org/") . It is a human readable, simple-minded format for configuration files and, more generally, to describe structured data set. It does have a C++ library and some [examples]("http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument") are availables to use it.

Francesco

---

### Post by SNYP40A1 on 2009-06-24
> **fr4nko said:**
> I believe a good idea would be to use [YAML]("http://www.yaml.org/") . It is a human readable, simple-minded format for configuration files and, more generally, to describe structured data set. It does have a C++ library and some [examples]("http://code.google.com/p/yaml-cpp/wiki/HowToParseADocument") are availables to use it.

Francesco

Thanks for the responses.  I do like YAML.  Looks pretty close to the object serialization that I am looking for producing a human-readable format.

---

