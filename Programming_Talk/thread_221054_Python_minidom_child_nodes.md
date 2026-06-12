---
title: "Python minidom child nodes"
date: 2006-07-22
forum: Programming Talk
---

### Post by anthro398 on 2006-07-22
I've been playing with (re)writing a python cgi to parse National Weather Service XML weather pages.  My question is, can help me create a list of all child nodes of a given node?  It's easy enough to write with explict parsing instructions for each node, but I'd like to just loop through all the nodes.  See the example:

```
#!/usr/bin/env python

### Import Python modules
import cgi#, cgitb; cgitb.enable()
from urllib import urlopen
from xml.dom import minidom
from sys import exit

## Set url variable.  Get url from http://www.nws.noaa.gov/data/current_obs/
url = "http://www.nws.noaa.gov/data/current_obs/KRDU.xml"

# Acquire, parse, and normalize xml from NWS.  Return xml tree object.
def getXML(url):
	try:			
		content = urlopen(url).read()
		xml = minidom.parseString(content)
		xml.normalize()	
		return 	xml
	except IOError:
		print " No valid data at ", url
		exit()	

# Parse out selected elements and populate variables.  Return variable dictionary.
def getElements(xml):
	root = xml.getElementsByTagName('current_observation')

	location = (root[0].getElementsByTagName('location')[0]).childNodes[0].data.encode('iso-8859-1')
	weather = (root[0].getElementsByTagName('weather')[0]).childNodes[0].data.encode('iso-8859-1')
	temperature_string = (root[0].getElementsByTagName('temperature_string')[0]).childNodes[0].data.encode('iso-8859-1')
	relative_humidity = (root[0].getElementsByTagName('relative_humidity')[0]).childNodes[0].data.encode('iso-8859-1')
	wind_string = (root[0].getElementsByTagName('wind_string')[0]).childNodes[0].data.encode('iso-8859-1')
	heat_index_string = (root[0].getElementsByTagName('heat_index_string')[0]).childNodes[0].data.encode('iso-8859-1')
	observation_time = (root[0].getElementsByTagName('observation_time')[0]).childNodes[0].data.encode('iso-8859-1')
	credit = (root[0].getElementsByTagName('credit')[0]).childNodes[0].data.encode('iso-8859-1')
	credit_URL = (root[0].getElementsByTagName('credit_URL')[0]).childNodes[0].data.encode('iso-8859-1')

	elDict = {'location': location, 'weather': weather, 'temperature_string': temperature_string, 'relative_humidity': relative_humidity,\
	'wind_string': wind_string, 'heat_index_string': heat_index_string, 'observation_time': observation_time, 'credit': credit, \
	'credit_URL': credit_URL}
	
	return elDict


def parseEl(root, el):
	pcall = "(root[0].getElementsByTagName(%s)[0]).childNodes[0].data.encode('iso-8859-1')" % ("'" + el + "'")
	#eldata = (root[0].getElementsByTagName(els)[0]).childNodes[0].data.encode('iso-8859-1')
	eldata = pcall
	return eldata
	


## main logic
xml = getXML(url)
elDict = getElements(xml)
print elDict
``` 

Notice that in the getElements function I've had to explictly get the text for each node I'm interested in and explictly build the dictionary.  I suspect it must be possible to do automate that.  Something like:
```
nodeList = root.getAllChildNodes
for node in nodeList:
  text = node.getText
  append node and node text to dictionary

```

I know you can't append to dictionaries, but there must be some way to automate the aquisition of nodes, node text, and performing the dictionary creation.  

Anyone have any thoughts?  Thanks.

---

### Post by anthro398 on 2006-07-23
I've gotten about as far as I'm going to get for awhile.  See this in action at [http://braggtown.com/webcam.html]("http://braggtown.com/webcam.html") or download the code at [http://braggtown.com/projects.html]("http://braggtown.com/projects.html").  Let me know if you use it or have suggestions to improve it.  Thanks.

---

### Post by cwaldbieser on 2006-07-23
> **anthro398 said:**
> I've been playing with (re)writing a python cgi to parse National Weather Service XML weather pages.  My question is, can help me create a list of all child nodes of a given node?  It's easy enough to write with explict parsing instructions for each node, but I'd like to just loop through all the nodes.  See the example:

```
#!/usr/bin/env python

### Import Python modules
import cgi#, cgitb; cgitb.enable()
from urllib import urlopen
from xml.dom import minidom
from sys import exit

## Set url variable.  Get url from http://www.nws.noaa.gov/data/current_obs/
url = "http://www.nws.noaa.gov/data/current_obs/KRDU.xml"

# Acquire, parse, and normalize xml from NWS.  Return xml tree object.
def getXML(url):
	try:			
		content = urlopen(url).read()
		xml = minidom.parseString(content)
		xml.normalize()	
		return 	xml
	except IOError:
		print " No valid data at ", url
		exit()	

# Parse out selected elements and populate variables.  Return variable dictionary.
def getElements(xml):
	root = xml.getElementsByTagName('current_observation')

	location = (root[0].getElementsByTagName('location')[0]).childNodes[0].data.encode('iso-8859-1')
	weather = (root[0].getElementsByTagName('weather')[0]).childNodes[0].data.encode('iso-8859-1')
	temperature_string = (root[0].getElementsByTagName('temperature_string')[0]).childNodes[0].data.encode('iso-8859-1')
	relative_humidity = (root[0].getElementsByTagName('relative_humidity')[0]).childNodes[0].data.encode('iso-8859-1')
	wind_string = (root[0].getElementsByTagName('wind_string')[0]).childNodes[0].data.encode('iso-8859-1')
	heat_index_string = (root[0].getElementsByTagName('heat_index_string')[0]).childNodes[0].data.encode('iso-8859-1')
	observation_time = (root[0].getElementsByTagName('observation_time')[0]).childNodes[0].data.encode('iso-8859-1')
	credit = (root[0].getElementsByTagName('credit')[0]).childNodes[0].data.encode('iso-8859-1')
	credit_URL = (root[0].getElementsByTagName('credit_URL')[0]).childNodes[0].data.encode('iso-8859-1')

	elDict = {'location': location, 'weather': weather, 'temperature_string': temperature_string, 'relative_humidity': relative_humidity,\
	'wind_string': wind_string, 'heat_index_string': heat_index_string, 'observation_time': observation_time, 'credit': credit, \
	'credit_URL': credit_URL}
	
	return elDict


def parseEl(root, el):
	pcall = "(root[0].getElementsByTagName(%s)[0]).childNodes[0].data.encode('iso-8859-1')" % ("'" + el + "'")
	#eldata = (root[0].getElementsByTagName(els)[0]).childNodes[0].data.encode('iso-8859-1')
	eldata = pcall
	return eldata
	


## main logic
xml = getXML(url)
elDict = getElements(xml)
print elDict
``` 

Notice that in the getElements function I've had to explictly get the text for each node I'm interested in and explictly build the dictionary.  I suspect it must be possible to do automate that.  Something like:
```
nodeList = root.getAllChildNodes
for node in nodeList:
  text = node.getText
  append node and node text to dictionary

```

I know you can't append to dictionaries, but there must be some way to automate the aquisition of nodes, node text, and performing the dictionary creation.  

Anyone have any thoughts?  Thanks.


Maybe something like this?:
```

def select_nodes(start_node, path):
    """
    Return a list of all nodes that match the path given from the starting node.
    """
    if path[0] == "/":
        path = path[1:]
    if path[-1] == "/":
        path = path[0:-1]
    components = path.split("/")
    parent_nodes = [start_node]
    for component in components:
        if component[0] == "@":
            attrib_flag = True
            component = component[1:]
        else:
            attrib_flag = False
        child_nodes = []
        for parent_node in parent_nodes:
            if attrib_flag:
                child_nodes.append(parent_node.attributes.getNamedItem(component))
            else:
                child_nodes.extend(parent_node.getElementsByTagName(component))
        parent_nodes = child_nodes
    return child_nodes

```

This function will let you select nodes from a starting node using an XPath-like notation.  e.g. select_nodes(root, "path/to/@nodes") returns a list of attribute nodes.

---

