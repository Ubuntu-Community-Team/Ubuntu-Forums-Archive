---
title: "Parsing XML to get one value"
date: 2007-10-28
forum: Programming Talk
---

### Post by NeillHog on 2007-10-28
This is probably so easy that no tutorial anywhere deals with it. Sorry but I just can not find where to start.

I have an XML file as follows
</gpx>
  <trk>
    <name>070626KappellerAlp</name>
    <desc></desc>
    <trkseg>
      <trkpt lat="47.62788" lon="10.49729">
        <ele>876.38</ele>
        <time>2007-06-26T14:48:07.000Z</time>
      </trkpt>
      <trkpt lat="47.62777" lon="10.49757">
        <ele>876.38</ele>
        <time>2007-06-26T14:48:10.000Z</time>
      </trkpt>
    </trkseg>
  </trk>
</gpx>

The only data I am interested in at the moment is between the <ele> tags. Later I will need others but not yet.

I want to open the file, find the first <ele>, do something with it and then go on to the next <ele> and do it again. 
I want to cary on like this until there are no more <ele> left at which point I am finished.

It sounds so easy but for a newbie Python programmer it seems nearly impossible. I have read all about SAX and that seems to be what I need but I am totally confused. 

Could one of you experts please spare a few minutes to point me in the correct direction.

Thank you very much in advance.

For any one interested - this is part of a mountain bike track in GPX format and I am aiming at a profiler that calculates climb and descent based on a freely given threshhold.

---

### Post by Quikee on 2007-10-28
```

from xml.etree import ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
	iter = root.getiterator("ele")
	for i in iter:
		print i.text

```

But I think this will be more useful to you:

```

from xml.etree import ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
	trackSegments = root.getiterator("trkseg")
	for trackSegment in trackSegments:
		for trackPoint in trackSegment:
			print trackPoint.attrib['lat']
			print trackPoint.attrib['lon']
			print trackPoint.find('ele').text
			print trackPoint.find('time').text

```

---

### Post by slavik on 2007-10-28
> **Quikee said:**
> ```

from xml.etree import ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
	iter = root.getiterator("ele")
	for i in iter:
		print i.text

```

But I think this will be more useful to you:

```

from xml.etree import ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
	trackSegments = root.getiterator("trkseg")
	for trackSegment in trackSegments:
		for trackPoint in trackSegment:
			print trackPoint.attrib['lat']
			print trackPoint.attrib['lon']
			print trackPoint.find('ele').text
			print trackPoint.find('time').text

```
I'd suggest using regex ...

Perl version:
```

open $file, "test.xml" or die $!;
@array = map { $_ =~ /<ele>(.*?)<\/ele>/ } <$file>;
for $i (@array) {
  print $array[$i] . "\n";
}
close $file;

```

---

### Post by aks44 on 2007-10-28
> **slavik said:**
> I'd suggest using regex ...

And accept invalid XML without even blinking? :???:

---

### Post by Quikee on 2007-10-28
> **slavik said:**
> I'd suggest using regex ...

Perl version:
```

open $file, "test.xml" or die $!;
@array = map { $_ =~ /<ele>(.*?)<\/ele>/ } <$file>;
for $i (@array) {
  print $array[$i] . "\n";
}
close $file;

```

Sorry, but I don't see a single point (except in speed maybe) why this would be better.

---

### Post by NeillHog on 2007-10-28
Hello Quikee!

First thank you. Your code was short and understandable. Exactly what some one like me needs. And it was Python as I asked for :-)

I used your second suggestion on a test xml file (the same as I copied in to the question and "it worked" :-)

Thanks!

I then tried with my "real file" and I get no output.
I have copied the file below. Before I get in to an orgy of debugging - can you tell me which part is stopping the output.

Once again thanks. I love Python and Ubuntu - not because I always understand them but because some kind soul will always help me :-)

<?xml version="1.0" encoding="ISO-8859-1" standalone="yes"?>
<gpx
  version="1.1"
  creator="Touratech QV 4.0.87 Standard - http://www.ttqv.com"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  xmlns:topografix="http://www.topografix.com/GPX/Private/TopoGrafix/0/1"
  xmlns="http://www.topografix.com/GPX/1/1"
  xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">
<metadata>
  <time>2007-09-02T17:30:53Z</time>
  <bounds minlat="47.4481272697449" minlon="10.4949045181274" maxlat="47.6289081573486" maxlon="11.0962772369385"/>
</metadata>
<trk>
  <name>070902Garmisch</name>
  <cmt>ActiveLog_2007-09-02_001
Download Date: 02.09.2007 19:20:26</cmt>
  <trkseg>
    <trkpt lat="47.6289081573486" lon="10.4949045181274">
    <ele>867</ele>
    <time>2007-09-02T06:04:35Z</time>
    </trkpt>
  </trkseg>
</trk>
<extensions>
</extensions>
</gpx>

---

### Post by slavik on 2007-10-28
> **aks44 said:**
> And accept invalid XML without even blinking? :???:
In this situation, who cares if you have valid xml if you only care about certain tags?

---

### Post by aks44 on 2007-10-28
> **slavik said:**
> In this situation, who cares if you have valid xml if you only care about certain tags?

Because if the XML isn't valid then the contents of the tag is probably incorrect as well?

---

### Post by LaRoza on 2007-10-28
Using the DOM is much better than using regex. Now, the contents of the elements can be processed with regex, but this is not some arbitrary string, it an XML file.

---

### Post by slavik on 2007-10-28
> **aks44 said:**
> Because if the XML isn't valid then the contents of the tag is probably incorrect as well?
or if you haven't downloaded the entire file?

Jabber conversations are continuous XML streams :) (which causes a problem when one user disconnects)

---

### Post by aks44 on 2007-10-28
> **slavik said:**
> or if you haven't downloaded the entire file?

Jabber conversations are continuous XML streams :) (which causes a problem when one user disconnects)


"... So does crack cocaine. Existence is not a valid endorsement for being acceptable." -Geekkit (about goto)

;)

IOW, design mistakes in one program are not a reason to get bad habits.

---

### Post by slavik on 2007-10-28
since when are regex not acceptable?

---

### Post by aks44 on 2007-10-28
Simple regexs like the one you provided are not acceptable for parsing XML documents, since they can successfully parse things like:

```
<ele>foo & bar</ele>
```

which is not even close to valid XML.

BTW, in my previous post I was referring to Jabber's way as being "not acceptable", not regexs in general.

---

### Post by NeillHog on 2007-10-28
Sorry! I didn't want to cause an argument :-)
Hopefully one day I will understand what you are all arguing about.
Until then could some one give me a pointer where my problem is with the GPX file.

Thank you!

OK! Found what is causing the problem. It is something in the long <gpx> tag.
But I don't know why so any help is still appreciated. Especially as the files are created by another program and I would like to use them as they are.

---

### Post by Quikee on 2007-10-28
> **NeillHog said:**
> Sorry! I didn't want to cause an argument :-)
Hopefully one day I will understand what you are all arguing about.
Until then could some one give me a pointer where my problem is with the GPX file.

Thank you!

OK! Found what is causing the problem. It is something in the long <gpx> tag.
But I don't know why so any help is still appreciated. Especially as the files are created by another program and I would like to use them as they are.

Yes.. the second xml you provided is using xml namespaces which makes things a little different:
```

from xml.etree import ElementTree

if __name__ == "__main__":
	namespace = "http://www.topografix.com/GPX/1/1"
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
	trackSegments = root.getiterator("{%s}trkseg" % namespace)
	for trackSegment in trackSegments:
		for trackPoint in trackSegment:
			print trackPoint.attrib
			print trackPoint.attrib['lat']
			print trackPoint.attrib['lon']
			print trackPoint.find('{%s}ele'% namespace).text
			print trackPoint.find('{%s}time'% namespace).text

```

The tags like <trkseg> are in fact <http://www.topografix.com/GPX/1/1:trkseg> as defined by <gpx xmlns="http://www.topografix.com/GPX/1/1"> element. If you don't understand xml namespaceing read [here]("http://www.w3schools.com/xml/xml_namespaces.asp") or use google. ;)

---

### Post by NeillHog on 2007-10-28
That works!

Great - thank you.

I'll be back ina few weeks once I have read up enough to understand what is now happening. But at least I know that it is worth reading up on because it works :-)

---

### Post by slavik on 2007-10-29
> **aks44 said:**
> Simple regexs like the one you provided are not acceptable for parsing XML documents, since they can successfully parse things like:

```
<ele>foo & bar</ele>
```

which is not even close to valid XML.

BTW, in my previous post I was referring to Jabber's way as being "not acceptable", not regexs in general.
why isn't it valid xml?

---

### Post by ghostdog74 on 2007-10-29
> **slavik said:**
> why isn't it valid xml?
to reference an actual "&" in XML, you have to define it as &amp; eg
```

<ele>foo &amp; bar</ele>

```

---

### Post by runningwithscissors on 2007-10-29
Who craes if it's valid XML? The OP just wanted the value between a particular tag.

regex is the most efficient way to get it.

---

### Post by pmasiar on 2007-10-29
> **slavik said:**
> 
I'd suggest using regex ...

In this situation, who cares if you have valid xml if you only care about certain tags?

This attitude, and power of Perl regexes, if reason of the mess in what Perl is now, IMHO.

If something as dangerous to use improperly is so easy to access, like Perl regex is (part of syntax, not even a library!), many people **will** use it wrongly, and they do. Who will clean the mess?

If you ask PerlMonks how to parse XML by simple regexes, first thing you get back is "don't - it is a sucker's game".

---

### Post by NeillHog on 2007-10-29
Between all the philosophy about right and wrong and what the monks would do...

Quikee wrote that as the xml file I am using makes use of namespace I have to include
> namespace = "http://www.topografix.com/GPX/1/1"
OK! I went off and read about namespace but a question remains (at least for mere mortals like me)
How do I know what value I have to give for "namespace"?
I realise that it is in the XML file but the way I understand things I can only read the file if I know the namespace value.

Sorry if I am being really dense here. Please bear with me. I am learning. Four months ago I had never heard of Ubuntu and three months ago I thought that Python wa a snake :-)

Thanks!

---

### Post by pmasiar on 2007-10-29
Python still is a snake. Language Python was named not after the snake, but after british comic group "Monty Python Flying Circus". If you wan't seen "Life of Brian" you are missing a lot. :-)

---

### Post by LaRoza on 2007-10-29
The namespace of an XML document, means nothing. It is usually an URI of some sort, so they are more likely to be unique, but that URI is not followed.

The namespace of a document can be different, The namespace will be in the root element, and may be prefixed with a word and a colon. In my page, laroza.freehostia.com/home, you'll see this line in the source:

```

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">

```

I declared an XML namespace (xmlns) of "http://www.w3.org/1990/xhtml". This is a global namespace, all child elements are part of this namespace. The xml:lang="en" attribute is prefixed with xml: because that attribute belongs to another namespace. I could have written:

```

<html xhtml:xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">

```

But I would have had to write xhtml: before all elements of this namespace. It doesn't have to be xhtml, it could have been almost any word, but giving the namespace a logical name make sense.

I don't know what the XML looks like that you are reading, and haven't use the functions you are using, so I don't know if it gets the xml of one namespace out of several, or that is the global namespace.

I hope this helps, but I was not sure exactly what you are asking.

---

### Post by NeillHog on 2007-10-29
I am 44 and originally come from England so I think that answers your question.
But the lumberjack song and the dead parrot are both better than life of brian.

But ...
How do I find a value for namespace. It is in the root string in 
> namespace = "http://www.topografix.com/GPX/1/1"
	tree = ElementTree.parse("test.xml")
	root = tree.getroot()
but there must be a function to find it. 

Mustn't there.

I really "wanted to be a lumberjack" but when I told the careers advisor that he assumed I had ovedosed on Monty Python. :-)

---

### Post by skeeterbug on 2007-10-29
Use the DOM example posted, or your own SAX handler. Please don't use a regex, it will be much more difficult to maintain. You may only want one node now, but how about in a month? What if the XML changes?

If you are parsing unstructured data, use regex. It is very powerful. XML is structured and we have libraries to easily work with it, use them!

---

### Post by Quikee on 2007-10-29
if you look at a part of your xml:
```

<gpx
  version="1.1"
  creator="Touratech QV 4.0.87 Standard - http://www.ttqv.com"
  xmlnssi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:topografix="http://www.topografix.com/GPX/Pr ivate/TopoGrafix/0/1"
  xmlns="http://www.topografix.com/GPX/1/1"
  xsi:schemaLocation="http://www.topografix.com/GPX/ 1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">
  <metadata>
    <time>2007-09-02T17:30:53Z</time>
    <bounds minlat="47.4481272697449" minlon="10.4949045181274" maxlat="47.6289081573486" maxlon="11.0962772369385"/>
  </metadata>
....

```

you see that <gpx ..> has a attribute xmlns="http://www.topografix.com/GPX/1/1" which means that gpx is part of "http://www.topografix.com/GPX/1/1" namespace and all its children (practically all other elements) are part od this namespace as well. 

If you look even further you see that <gpx..> element has a attribute xmlns:topografix="http://www.topografix.com/GPX/Pr ivate/TopoGrafix/0/1" which means that all attributes defined as <topografix:someElementName> is part of "http://www.topografix.com/GPX/Private/TopoGrafix/0/1" namespace.

Which namespace and which element "fit together" is defined in the specs of gpx format (the shema of the xml). 

In other words namespaces are just some sort of a discriminator for elements that have the same name.

---

### Post by NeillHog on 2007-10-29
Quikee is always there when you need him :-)

Thank you! I understand all that now. After your hints yesterday I read up al about namespace.

my problem is that it seems like I need to know that the namespace variable is "http://www.topografix.com/GPX/1/1" before I can start parsing. However I can not know what the value for namespace is until I have parsed the file. 
Like the chicken and egg :-)

Depending on which programme creates a GPX, the namespace variable is different so before starting reading the elevations I need to know what the value for namespace is. 

In your example you have hardcoded the value but that will only work if it agrees with the XML file.

As I wrote, the namespace is in the string I see by using "print root".
But I assume that there is some clever way of getting the namespace out of the file. My experiments so far have failed.

Thanks for all your time and help :-)

Neill

---

### Post by aks44 on 2007-10-29
> **NeillHog said:**
> But I assume that there is some clever way of getting the namespace out of the file. My experiments so far have failed.

You should be able to parse your XML document into a DOM tree, and from there extract the namespace from the root element.

Something like:

```
tree = ElementTree.parse("test.xml")
root = tree.getroot()
namespace = root.getnamespace("") // empty string for default namespace
```


I used to do it using the Xerces parser, so I guess Python's parser can do it too. Better check the API reference.

---

### Post by Quikee on 2007-10-29
> **NeillHog said:**
> 
Depending on which programme creates a GPX, the namespace variable is different so before starting reading the elevations I need to know what the value for namespace is. 

In your example you have hardcoded the value but that will only work if it agrees with the XML file.

As I wrote, the namespace is in the string I see by using "print root".
But I assume that there is some clever way of getting the namespace out of the file. My experiments so far have failed.

Thanks for all your time and help :-)

Neill

This is weird. Usually a format defines a namespace (or many of them) for its elements and they are always the same as long you parse the same format of the same version. To have different formats is nonsense - it is like ie, firefox and opera would define its own namespaces for HTML elements. Just imagine the confusion. ;)

ElementTree that is build into Python 2.5 handles namespaces in a very strange way. That's why I prefer [lxml]("http://codespeak.net/lxml/") which provides the same interface as the built-in ElementTree + its addons and backend. One of the "add-ons" is a namespace map (nsmap) which is a map/dictionary of all namespaces defined on the current element.

```

from lxml import etree as ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("gpxExampleNS.xml")
	root = tree.getroot()
	namespace = root.nsmap[None]
	print root.nsmap
	trackSegments = root.getiterator("{%s}trkseg" % namespace)
	for trackSegment in trackSegments:
		for trackPoint in trackSegment:
			print trackPoint.attrib
			print trackPoint.attrib['lat']
			print trackPoint.attrib['lon']
			print trackPoint.find('{%s}ele'% namespace).text
			print trackPoint.find('{%s}time'% namespace).text

```

lxml is in the ubuntu repository. 

I don't know how to do this in normal ElementTree.

---

### Post by NeillHog on 2007-10-29
Weird it may be but here are the xmlns tags from two GPX files.
They are only a tiny bit diferent but different enough.
xmlns="http://www.topografix.com/GPX/1/0"
xmlns="http://www.topografix.com/GPX/1/1"
I think the difference is the version but none the less hardcoding isn't going to work.
:-(

Is it possible to use the first code you sent me (none namespace)  to parse for the xmlns part of the gpx tag. If that was possible then I would have the namespace and couls use your second (namespace) code to do the rest using the xmlns part as the namespace?

Another possibility would be to extract the namespace from the root.
When I do "print root" I get
<Element {http://www.topografix.com/GPX/1/1}gpx at b7d506ec>
This contains the namespace that I am looking ffor but is not a string and will not let me do any string operations on it.

One of these solutions would be ideal because they use only standard python.

Sorry about all these questions but this is slowly sending me mad. Once I have the values the rest will be easy (famous last words!)

Thanks
Neill

---

### Post by pjkoczan on 2007-10-29
> **slavik said:**
> I'd suggest using regex ...

Perl version:
```

open $file, "test.xml" or die $!;
@array = map { $_ =~ /<ele>(.*?)<\/ele>/ } <$file>;
for $i (@array) {
  print $array[$i] . "\n";
}
close $file;

```

Point of interest, this also assumes that the opening and closing tags are on the same line. This is the case in the OP's example, but this won't even come close to working in general.

---

### Post by Quikee on 2007-10-29
Well if the only difference between those 2 is the version then you could do something like this: 
```

from xml.etree import ElementTree

if __name__ == "__main__":
	tree = ElementTree.parse("gpxExampleNS.xml")
	root = tree.getroot()
	
	if 'version' in root.attrib:
		version = root.attrib['version']
		if version == '1.0':
			namespace = "http://www.topografix.com/GPX/1/0"
		elif version == '1.1':
			namespace = "http://www.topografix.com/GPX/1/1"
	else:
		namespace = root.tag.split('}')[0][1:]
	
	trackSegments = root.getiterator("{%s}trkseg" % namespace)
	for trackSegment in trackSegments:
		for trackPoint in trackSegment:
			print trackPoint.attrib
			print trackPoint.attrib['lat']
			print trackPoint.attrib['lon']
			print trackPoint.find('{%s}ele'% namespace).text
			print trackPoint.find('{%s}time'% namespace).text

```

If you know the version of gpx then use the version. If the version is not known - parse the namespace from gpx. The right action if the version is not known would be to raise an exception IMHO.

---

### Post by NeillHog on 2007-10-29
Thanks again. It is late now but I will try that tomorrow.
I'll keep you informed.
:-)

OK! Couldn't wait. tried it now.
This finds the version in the root tag but that is not what I was after. I know I explained myself badly. Sorry!

All the files have 
<?xml version="1.0" encoding="ISO-8859-1" standalone="yes"?>
The difference is in the <gpx> tag.
Is there no way to read out the xmlns value from <gpx> without knowing the namespace?
I could then use this as the namespace.

I am sure you have had enough of this by now but you are my last hope of getting this working.
Maybe I should just give up and write another "hello world" programme :-)

Neill

---

### Post by runningwithscissors on 2007-10-30
> **NeillHog said:**
> Quikee wrote that as the xml file I am using makes use of namespace I have to include

OK! I went off and read about namespace but a question remains (at least for mere mortals like me)
How do I know what value I have to give for "namespace"?
I realise that it is in the XML file but the way I understand things I can only read the file if I know the namespace value.An XML namespace is just like a namespace in any other language, i.e. tags or entities you define under that namespace are distinct from the same tags defined under other namespaces.
i.e. say you've defined a namespace "localtags", and defined a <blah> tag under it. The definition of that tag would be specific to your namespace, i.e your tag is known as localtags:blah
Similarly you can have another definition for <blah> in another namespace, say "foreigntags". foreigntags:blah is completely distinct from localtags:blah

So yes, if you're writing logic to parse XML, you must know what namespace the tags are in.

The value for the namespace can be any string.

---

### Post by slavik on 2007-10-30
> **pjkoczan said:**
> Point of interest, this also assumes that the opening and closing tags are on the same line. This is the case in the OP's example, but this won't even come close to working in general.

```

open $file, "test.xml" or die $!;
$f = join '', <$file>;
@array = $f =~ /<ele>(.*?)<\/ele>/gis;
for $i (@array) {
  print $array[$i] . "\n";
}
close $file;

```

better? :-P

---

### Post by ghostdog74 on 2007-10-30
> **slavik said:**
> ```

open $file, "test.xml" or die $!;
$f = join '', <$file>;
@array = $f =~ /<ele>(.*?)<\/ele>/gis;
for $i (@array) {
  print $array[$i] . "\n";
}
close $file;

```

better? :-P

why not use the m operator for multiline match?

---

### Post by NeillHog on 2007-10-30
Quikee wrote
> use lxml
which I did and it works.

I think I understand that I shouldn't have to read the namespace out of the file but that does not change the fact that I have to.
I want my programme to read gpx files no matter which programme created them. If the different programmes write slightly different values for name space then I will have to keep using lxml.

Thank you Quikee and all the others who helped. I now understand a lot more than before.

Neill

---

### Post by winch on 2007-10-30
I think this is a good situation to use a stream parser. The files have a  pretty flat structure with a potentially large number of points.
I have my GPSr log a point every second so a weekend ride can result in tracks with ~50,000 points.

No point loading it all into memory building a big tree if all you do with the tree is transform it into some other data structure.

I guess for python you would use this [http://docs.python.org/lib/module-xml.sax.html](http://docs.python.org/lib/module-xml.sax.html)

---

### Post by slavik on 2007-10-30
[quote=ghostdog74]why not use the m operator for multiline match?[/quote]

s tells it to treat it as a single line.

---

### Post by OmahaVike on 2008-02-12
here's how i'm parsing some weather data from the gov.  xml file looks something like:

```

blah blah blah
blah blah blah
blah blah blah
        <temperature_string>9 F (-13 C)</temperature_string>
        <temp_f>9</temp_f>
        <temp_c>-13</temp_c>
        <relative_humidity>80</relative_humidity>
        <wind_string>From the Northeast at 10 MPH</wind_string>
        <wind_dir>Northeast</wind_dir>

```

and the awk (think it may actually be gawk) code following will only snag the stuff between the <temp_f> and </temp_f> tags:

```

awk '/temp_f/ {gsub(/<temp_f>/,"",$0);gsub(/<\/temp_f>/,"",$1);print}' filename.xml

```

hope this helps someone in need.

---

### Post by ghostdog74 on 2008-02-12
> **OmahaVike said:**
> here's how i'm parsing some weather data from the gov.  xml file looks something like:

```

blah blah blah
blah blah blah
blah blah blah
        <temperature_string>9 F (-13 C)</temperature_string>
        <temp_f>9</temp_f>
        <temp_c>-13</temp_c>
        <relative_humidity>80</relative_humidity>
        <wind_string>From the Northeast at 10 MPH</wind_string>
        <wind_dir>Northeast</wind_dir>

```

and the awk (think it may actually be gawk) code following will only snag the stuff between the <temp_f> and </temp_f> tags:

```

awk '/temp_f/ {gsub(/<temp_f>/,"",$0);gsub(/<\/temp_f>/,"",$1);print}' filename.xml

```

hope this helps someone in need.

this is an old thread. anyway, the awk statement can be shortened
```

awk '/temp_f/ {gsub(/<temp_f>|<\/temp_f>/,"");print $0}' file

```

---

