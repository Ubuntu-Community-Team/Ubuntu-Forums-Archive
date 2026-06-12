---
title: "Python feedback"
date: 2009-06-19
forum: Programming Talk
---

### Post by matmatmat on 2009-06-19
I have this:
```

import sys
import os
import re
import httplib
import urlparse

cwd = os.getcwd()

def httpExists(url):
    	host, path = urlparse.urlsplit(url)[1:3]
    	found = 0
    	try:
        	connection = httplib.HTTPConnection(host)  ## Make HTTPConnection Object
        	connection.request("HEAD", path)
        	responseOb = connection.getresponse()      ## Grab HTTPResponse Object

        	if responseOb.status == 200:
            		found = 1
        	else:
            		found = 0
    	except Exception, e:
        	found = 0
    	return found

pages = []
css = []
if len(sys.argv) == 2:
        for root, dirs, files in os.walk(sys.argv[1]):
                for f in files:
                        filename = os.path.join(root, f)
                        if (filename.endswith('.html')) or (filename.endswith('.htm')):
                                pages.append(filename)
			if (filename.endswith('.css')):
				css.append(filename)


licount = 0
ecount = 0
scount = 0
uerror = 0
terror = 0
cerror = 0
bfiles = []
blines = []
berror = 0
colours = []
local = 0
imcount = 0
for page in pages:
        f = open(page, "r")
        lines = f.readlines()
        count = 1
        otcount = 0
        etcount = 0
	probwithfile = False
        pstring = ""
	lcount = 0
        for line in lines:
		count += 1
                if re.match("[\sa-zA-Z<>=\"\']*<a href=\"", line):
                        split1 = re.split("<a href=\"", line)[1]
                        split = re.split("\"", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "################### Link Error ###################"
		                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
							probwithfile = True
							local += 1
                                                        pstring += str(count) + ", "
				if (split[0].startswith("http")):
					exists = httpExists(split[0])
					if exists != 1:
						print "################# URL/Link Error #################"
						print "Error with line %i in file %s, the webpage '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                print line
		                                ecount += 1
						uerror += 1
						probwithfile = True
                                                pstring += str(count) + ", "
                                if (split[0].startswith("www")):
                                        split[0] = "http://" + split[0]
					exists = httpExists(split[0])
					if exists != 1:
						print "################# URL/Link Error #################"
						print "Error with line %i in file %s, the webpage '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                print line
		                                ecount += 1
						uerror += 1
						probwithfile = True
                                                pstring += str(count) + ", "

                        licount += 1

                elif re.match("[\sa-zA-Z<>=]*<a href='", line):
                        split1 = re.split("<a href='", line)[1]
                        split = re.split("'", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "################### Link Error ###################"
		                                        print "Error with line %i in file %s, the page '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
							local += 1
							probwithfile = True
                                                        pstring += str(count) + ", "

				if (split[0].startswith("www")) or (split[0].startswith("http")):
					exists = httpExists(split[0])
					if exists != 1:
						print "################# URL/Link Error #################"
						print "Error with line %i in file %s, the webpage '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                print line
		                                ecount += 1
						uerror += 1
						probwithfile = True
                                                pstring += str(count) + ", "
                        licount += 1

                elif re.match("[\sa-zA-Z<>=\"\']*<link href=\"", line):
                        split1 = re.split("<link href=\"", line)[1]
                        split = re.split("\"", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "############# Stylesheet/Link Error ##############"
		                                        print "Error with line %i in file %s, the css sheet '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
							scount += 1
							probwithfile = True
                                                        pstring += str(count) + ", "
                        licount += 1

                elif re.match("[\sa-zA-Z<>=]*<link href='", line):
                        split1 = re.split("<link href='", line)[1]
                        split = re.split("'", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "############# Stylesheet/Link Error ##############"
		                                        print "Error with line %i in file %s, the css '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
							scount += 1
							probwithfile = True
                                                        pstring += str(count) + ", "
                        licount += 1

                elif re.match("[\sa-zA-Z<>=\"\']*<img src=\"", line):
                        split1 = re.split("<img src=\"", line)[1]
                        split = re.split("\"", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
						if not split[0].startswith("mailto"):
		                                        print "################### Link Error ###################"
		                                        print "Error with line %i in file %s, the image '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                        print line
		                                        ecount += 1
							probwithfile = True
							local += 1
                                                        pstring += str(count) + ", "
							imcount += 1
				if (split[0].startswith("http")):
					exists = httpExists(split[0])
					if exists != 1:
						print "################# URL/Link Error #################"
						print "Error with line %i in file %s, the image '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                print line
		                                ecount += 1
						uerror += 1
						probwithfile = True
                                                pstring += str(count) + ", "
						imcount += 1
                                if (split[0].startswith("www")):
                                        split[0] = "http://" + split[0]
					exists = httpExists(split[0])
					if exists != 1:
						print "################# URL/Link Error #################"
						print "Error with line %i in file %s, the image '%s' doesn't exist:" % (count, page, split[0].rstrip())
		                                print line
		                                ecount += 1
						uerror += 1
						probwithfile = True
                                                pstring += str(count) + ", "
						imcount += 1

                        licount += 1

                ultimate_regexp = "(?i)<\/?\w+((\s+\w+(\s*=\s*(?:\".*?\"|'.*?'|[^'\">\s]+))?)+\s*|\s*)\/?>"
                for match in re.finditer(ultimate_regexp, line):
                        if not re.match(".*?<!.*", line):
                                if repr(match.group()).startswith("'</") or repr(match.group()).endswith("/>"):
                                        etcount += 1
                                else:
                                        otcount += 1
                 
        if otcount != etcount:
                print "#################### Tag Error ###################"        
                print "Number of tags opened does not equal the number of tags closed!"
                print "%i tags opened, %i tags closed in file %s" % (otcount, etcount, page)
                terror += 1
		probwithfile = True
                pstring += "?, "
	if probwithfile:
		bfiles.append(page)
                blines.append(pstring)

scount = 0
cerror = 0
coerror = 0
for page in css:
        f = open(page, "r")
        lines = f.readlines()
        count = 1
        obcount = 0
        ebcount = 0
	probwithfile = False
        pstring = ""
        for line in lines:
                if re.match(".*?:.*", line):
                        if not re.match("[a-zA-Z0-9_=#:\s\.,]*\{.*",line):
                                if not re.match("[a-zA-Z0-9_=#:\s\.]*?,\s*", line):
                                        split = re.split(":", line)
                                        split =  re.split(";", split[1])
                                        #import webcolors as webcolours
                                        #try:
                                                #colour = webcolours.normalize_hex(split[0])
                                                #warning = True
                                        #except:
                                                #colour = split[0]
                                        colour = split[0].strip()
                                        if colour.startswith("#"):
                                                if not re.match("^#[a-zA-Z0-9]{6}$", colour):
                                                        print "################# CSS Colour Error ################"
                                                        print "Line %i in file '%s' contains a colour error" % (count, page)
                                                        print line
                                                        coerror += 1
                                                        cerror += 1
                                                        pstring += str(count) + ", "
                                                        probwithfile = True
                                                #if warning:
                                                 #       print "################ CSS Colour Warning ###############"
                                                  #      print "Line %i may not be a valid colour" % count
                                                   #     print line


                for match in re.finditer("}", line):
                        ebcount += 1
                for match in re.finditer("{", line):
                        obcount += 1    
                if not re.match("[\.a-zA-Z0-9=#:\s_,]*\}.*", line):
                        if not re.match("[a-zA-Z0-9_=#:\s\.,]*\{.*",line):
                                if not re.match("[a-zA-Z0-9_=#:\s\.]*?,\s*", line):
                                        if not re.match("^\s+$", line):
                                                if not re.match("/\*.+", line):                                                
                                                       if not re.match(".*?;.*", line):
                                                                print "#################### CSS Error ###################"
                                                                print "Line does not end with ';' in file %s on line %i" % (page, count)
                                                                print line
                                                                scount += 1
                                                                probwithfile = True
                                                                cerror += 1
                                                                pstring += str(count) + ", "
                      


	        count += 1
	if obcount != ebcount:
		print "#################### CSS Error ###################"          	
                print "Number of braces opened does not equal the number of braces closed!"
                print "%i braces opened, %i braces closed in file %s" % (obcount, ebcount, page)
                berror += 1
                cerror += 1
		probwithfile = True
                pstring += str(count) + ", "

	if probwithfile:
		bfiles.append(page)
                blines.append(pstring)

filecount = 0
for brfile in bfiles:
	filecount += 1           

print "###################### Summary ###########################"
print "#### %i files with errors in" % filecount
print "##########################################################"
print "###################### HTML ##############################"
print "###################### Links #############################"
print "#### %i errors in %i links " % (ecount, licount)
print "#### %i local errors       " % local
print "#### %i web error          " % uerror
print "#### %i stylesheet errors  " % scount
print "###################### Tags  #############################"
print "#### %i tag errors" % terror       
print "##########################################################"
print "###################### CSS ###############################" 
print "#### %i errors" % cerror
print "#### %i brace errors" % berror
print "#### %i ';' errors" % scount
print "#### %i colour errors" % coerror
print "##########################################################"
os.chdir(cwd)
f = open("SITEsnake.txt", "w")
f.write("")
f.close()
for i in range(0, len(bfiles)):
        f = open("SITEsnake.txt", "a")
        f.write("%s\t\t%s\n" % (blines[i], bfiles[i]))
        
f.close()

```
can anyone tell me what other features to do or what you think?

---

### Post by dandaman0061 on 2009-06-19
I'm not too sure what you're expecting comments on but I have at least one suggestion... try to limit the amount of indenting a bit more.  It makes code harder to read.

e.g.
```

                if not re.match("[\.a-zA-Z0-9=#:\s_,]*\}.*", line):
                        if not re.match("[a-zA-Z0-9_=#:\s\.,]*\{.*",line):
                                if not re.match("[a-zA-Z0-9_=#:\s\.]*?,\s*", line):
                                        if not re.match("^\s+$", line):
                                                if not re.match("/\*.+", line):                                                
                                                       if not re.match(".*?;.*", line):
                                                                print "#################### CSS Error ###################"
                                                                print "Line does not end with ';' in file %s on line %i" % (page, count)
                                                                print line
                                                                scount += 1
                                                                probwithfile = True
                                                                cerror += 1
                                                                pstring += str(count) + ", "

```

Now I didn't read exactly what your regexes are doing, but could this not be done in one regex instead of multiple?  Or if not, this may be easier for the reader (me) to understand what you're going for if you move this code into an aptly named function e.g. 'check_line_colon_end'

I feel that this kind of goes with your whole script... it would be much easier to read and much easier to reuse if you broke it up into multiple functions and have the "main" function call each in order.  Just my .02

---

### Post by imdano on 2009-06-19
Try to keep your indentation consistent.  It looks like you have a mix of spaces and tabs in there.  Also the convention in Python is to use 4-space indentation, not 8, and definitely not actual tabs.

---

### Post by Martin Witte on 2009-06-19
I fully agree with dandaman0061, all his comments are spot on. My idea on how to approach this is along these lines, see the comments in the code for my suggestions

```
#!/usr/bin/env python

import httplib
import urlparse
import re
import os.path

#
# document your code
#

# use built in features
# - Booleans are more clear for true/false testing than 0/1
# - httplib defines a constant for 200, so use the constant instead of a hardcoded value
def httpExists(url, debug = False):
	# tests if argument url is valid

	# don't loose information too early
	(scheme, host, path, query, fragment) = urlparse.urlsplit(url)
	if debug:
		print (scheme, host, path, query, fragment)
	
	# repair url if scheme misses
	if not scheme:
		url = "http://%s" % url
		(scheme, host, path, query, fragment) = urlparse.urlsplit(url)

	found = False
	try:
		connection = httplib.HTTPConnection(host)  ## Make HTTPConnection Object
		connection.request("HEAD", path)
		responseOb = connection.getresponse()	 ## Grab HTTPResponse Object
		if responseOb.status == httplib.OK:
			found = True
		else:
			found = False
	except Exception, e:
		found = False
	return found

# add some debug code to your sources - it helps to see how a function is supposed to be used
debug = True # set to False prints no debug code
if debug:
	print httpExists("http://docs.python.org/library/httplib.html?highlight=httplib", True)
	print httpExists("http://www.osnews.com", True)
	print httpExists("www.osnews.com", True)

# define methods for all other cases as well
def fileExists(url):
	# test if url is existing file
	return os.path.exists(url)

def mailExists(url):
	# test if url is a mailto: reference
	retval = False
	if re.match("mailto:.*", url):
		retval = True

	return retval

def handleError(url):
	print "%s is not valid" % url

pages = ["test.html"]
for page in pages:
	f = open(page, "r")
	for line in f:
		# with regular expressions groups can clarify your code a lot 
		m = re.match(".*<[Aa] href=\"(.+)\">(.*)</[Aa]>.*", line)
		if m:
			if debug:
				print m.group(1)

			# keep the depth for your if/then/else structures low
			if fileExists(m.group(1)):
				pass
			elif httpExists(m.group(1)):
				pass
			elif mailExists(m.group(1)):
				pass
			else:
				handleError(m.group(1))
	f.close()

```

---

### Post by Martin Witte on 2009-06-19
> **imdano said:**
> Try to keep your indentation consistent.  It looks like you have a mix of spaces and tabs in there.  Also the convention in Python is to use 4-space indentation, not 8, and definitely not actual tabs.

The convention is a little more subtle, see [the style guide]("http://www.python.org/dev/peps/pep-0008/")

---

### Post by imdano on 2009-06-19
> **Martin Witte said:**
> The convention is a little more subtle, see [the style guide]("http://www.python.org/dev/peps/pep-0008/")

>   Indentation

    Use 4 spaces per indentation level.

    For really old code that you don't want to mess up, you can continue to
    use 8-space tabs.

  Tabs or Spaces?

    Never mix tabs and spaces.

    The most popular way of indenting Python is with spaces only.  The
    second-most popular way is with tabs only.  Code indented with a mixture
    of tabs and spaces should be converted to using spaces exclusively.  When
    invoking the Python command line interpreter with the -t option, it issues
    warnings about code that illegally mixes tabs and spaces.  When using -tt
    these warnings become errors.  These options are highly recommended!

    For new projects, spaces-only are strongly recommended over tabs.  Most
    editors have features that make this easy to do.
It says don't mix spaces and tabs, and that unless you're maintaining legacy code (and the OP is not) you should favor 4-space indentation.  Which is what I said, I think?

---

### Post by Martin Witte on 2009-06-19
> **imdano said:**
> It says don't mix spaces and tabs, and that unless you're maintaining legacy code (and the OP is not) you should favor 4-space indentation.  Which is what I said, I think?
Thats right, mixing is evil, but as the author of the guide knows a lot of people still use tabs, and so it is not disallowed.

---

### Post by simeon87 on 2009-06-19
> **Martin Witte said:**
> Thats right, mixing is evil, but as the author of the guide knows a lot of people still use tabs, and so it is not disallowed.

That's not what is says. It says that only legacy code, if it happens to have tabs, should be maintained using tabs just for consistency. In addition, it says:

> For new projects, spaces-only are strongly recommended over tabs. Most
editors have features that make this easy to do. 

So yes, tabs are disallowed if you have to ability to change it easily without worrying about breaking too much. In this case, that can be done because it's a new project (no user base yet) and just one file (let the editor do it and you're done).

---

### Post by Martin Witte on 2009-06-19
> **simeon87 said:**
> That's not what is says. It says that only legacy code, if it happens to have tabs, should be maintained using tabs just for consistency. In addition, it says:



So yes, tabs are disallowed if you have to ability to change it easily without worrying about breaking too much. In this case, that can be done because it's a new project (no user base yet) and just one file (let the editor do it and you're done).

I'm getting into the splitting hairs territory here, I know, but: the style guide says 'For new projects, spaces-only are strongly recommended over tabs.' - so it is a recommendation, not strict rule. But I admit: four spaces are better, and should be used, I will adhere from now on.

---

### Post by sujoy on 2009-06-20
refactor, refactor. if you are indenting over 3 levels, then its probably time to refactor it.

---

### Post by matmatmat on 2009-06-20
Thanks, are there anyother things I could check for in HTML or CSS

---

### Post by Martin Witte on 2009-06-20
> **matmatmat said:**
> Thanks, are there anyother things I could check for in HTML or CSS
You could check if e-mail address is valid, e.g.:
```
def mailExists(url, debug = False):
    # test if url is a mailto: reference
    retval = False
    if re.match("^mailto:[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,4}", url):
        retval = True
    else:
        if debug:
            print url

    return retval

if debug:
    print mailExists("mailto:barack@whitehouse.gov", True)
    print mailExists("mailto:barack@whitehouse", True)
    print mailExists("mailto:barack@whitehouse.government", True)

```

---

### Post by pokerbirch on 2009-06-20
A quick tip regarding the whole indentation thing: most decent python editors will automatically correct tab indentations to 4 spaces. I use Editra for my Python work.

---

### Post by matmatmat on 2009-06-21
Any other features?

---

### Post by nvteighen on 2009-06-21
> **sujoy said:**
> refactor, refactor. if you are indenting over 3 levels, then its probably time to refactor it.

Hm... that's a rule Linus Torvalds stated for C... Take it as a guideline, never as an absolute rule... For example, when you code in Python and need classes, you'll be easily indenting over 3 levels (class, method level... will you refrain from using any conditionals, loops or whatever because of that rule?).

---

### Post by simeon87 on 2009-06-21
> **nvteighen said:**
> Hm... that's a rule Linus Torvalds stated for C... Take it as a guideline, never as an absolute rule... For example, when you code in Python and need classes, you'll be easily indenting over 3 levels (class, method level... will you refrain from using any conditionals, loops or whatever because of that rule?).

Probably over 3 levels within a function or method was meant.

---

### Post by Greyed on 2009-06-21
> **matmatmat said:**
> I have this:

Yikes, as others have mentioned, pare down the chained levels of indention.  I'll just give one example as it made the code visually busy and hard to follow.  IE, not even getting into functionality yet because the code just hits you with a hammer between the eyes visually.

```

                if re.match("[\sa-zA-Z<>=\"\']*<a href=\"", line):
                        split1 = re.split("<a href=\"", line)[1]
                        split = re.split("\"", split1)
                        os.chdir(os.path.dirname(page))
                        if not os.path.exists(os.path.abspath(split[0].rstrip())):
                                if not (split[0].startswith("www")) :
                                        if not split[0].startswith("http"):
                        if not split[0].startswith("mailto"):
                                                print "################### Link Error ###################"

```You're testing split[0] 3 times here in a chain of 3 ifs.  A slightly better solution would be using OR logic.

```

if not split[0].startswith("www") or not split[0].startswith("http") or not split[0].startswith("mailto"):

```Of course that's a dang long if statement, but it becomes readable with some handy, dandy slashes.

```

if not split[0].startswith("www") or \
   not split[0].startswith("http") or \
   not split[0].startswith("mailto"):

```Much cleaner visually.  It's clear you're looking for one of these.  Also it's simple to add another onto the chain.  Although any time I see multiple tests which might be expanded upon I'm a huge fan of looping.  Sure, there's a tad more verbage but overall it's easier for the human to parse when reading your code and it's easier for you to expand in the future.

```

def protocol_check(x):
    protocols = ["www", "http", "mailto"]
    for protocol in protocols:
        if x.startswith(protocol):
            return True
    else:
        return False
   
if protocol_check(split[0]):
    do_stuff_here()

```Of course this leads into my favorite construct.  What it looks like you're doing here is using these if checks to see which protocol you're looking at and doing something from there.  Instead of using if as you are couple it with a dict and the "x in y" form of lookup.

```

def www_handle():
    # www_logic_here

def http_handle():
    # http_logic_here

def mailto_handle():
    # mailto_logic_here


protocols = {"www" : www_handler,
             "http" : http_handler,
             "mailto" : mailto_handler}

if split[0].split(':') in protocols:
        protocol(split)
    else:
        print "Unknown protocol."

```To add a new protocol handler you just define a new function, add one key/reference to the protocols dict and you're done.  No need to change the if statement at all.  Well, presuming you can rely on the split on colon in use there.  ;)

Point is though using that form it is instantly clear what's going on.  First we, as humans, read that you're doing different stuff with the different protocols.  Then we see you're building references to those functions. Then we see a simple test back to the references.  All with minimal visual clutter.

---

### Post by simeon87 on 2009-06-21
> **Greyed said:**
> You're testing split[0] 3 times here in a chain of 3 ifs.  A slightly better solution would be using OR logic.

```

if not split[0].startswith("www") or not split[0].startswith("http") or not split[0].startswith("mailto"):

```Of course that's a dang long if statement, but it becomes readable with some handy, dandy slashes.

```

if not split[0].startswith("www") or \
   not split[0].startswith("http") or \
   not split[0].startswith("mailto"):

```

Please note that it should be AND in order to be equivalent to the previous code. All three statements should be true, not just one, otherwise I could feed it the string starting with "http" and it would accept it (as the first condition would be true).

---

### Post by Greyed on 2009-06-21
/facepalm

I think I was reversing the logic in my head.  IE, I'd be checking for positives (which leads into the for check and the dict logic) but forgot to pull the nots out of my C&P.  Thanks for the catch!

---

### Post by Copernicus1234 on 2009-06-21
I have a comment.

Use comments in your code!

You wont understand what the heck you were thinking 3 months from now. :)

And this program makes me want to split it up in classes, but thats just me.

---

### Post by sujoy on 2009-06-21
> **simeon87 said:**
> Probably over 3 levels within a function or method was meant.

yes.

ofcourse when you are using classes, you cant stick to the 3 level indent rule.

---

### Post by nvteighen on 2009-06-22
> **sujoy said:**
> yes.

ofcourse when you are using classes, you cant stick to the 3 level indent rule.
I still insist that can't be a rule, but a guideline.

---

### Post by sujoy on 2009-06-22
> **nvteighen said:**
> I still insist that can't be a rule, but a guideline.

offcourse, all best practices and so called rules are always to be taken with a grain of salt. :)

if a 4 level indent makes the code structure easy to comprehend and maintain then why not!
thats why i said that its "probably" the time to refactor it ;)

---

### Post by matmatmat on 2009-06-24
I think splitting it into methods would be GREAT if I could be bothered :)

---

