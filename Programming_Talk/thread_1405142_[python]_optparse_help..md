---
title: "[python] optparse help."
date: 2010-02-12
forum: Programming Talk
---

### Post by Hume's doona on 2010-02-12
I've never used optparse before, but I need to implement a command line parser to take a file name as input.


[PHP]def read_file():
	try:
		file1=open(raw_input("Enter the file to open: >> "),'r')
		xml_format=file1.read()
		file1.close()
	except IOError:
		print "File or extension not valid, try again."
		xml_format=read_file()
	return xml_format
[/PHP]

Would I be on the right track with something along the lines of:

[PHP]from optparse import OptionParser
    parser = OptionParser(usage='usage: %prog [options] ')
    parser.add_option('-x', '--xml',default=False,
    action="store", type="string", dest="file1")
[/PHP]

??

And does anyone know of any decent online documentation/tutorials? 

Cheers

---

