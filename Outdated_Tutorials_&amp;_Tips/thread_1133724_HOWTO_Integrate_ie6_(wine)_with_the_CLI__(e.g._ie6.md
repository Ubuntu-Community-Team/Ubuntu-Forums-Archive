---
title: "HOWTO: Integrate ie6 (wine) with the CLI  (e.g. ie6 localhost/test.html)"
date: 2009-04-23
forum: Outdated Tutorials &amp; Tips
---

### Post by kirsis on 2009-04-23
Here's a little python script I made for myself, to ease the pain of having to test web pages in IE6.

With this, you can open pages in IE6 from Nautilus (right click -> open with > script_name) or from the CLI (script_name file1.html file2.html)

You can specify multiple filenames to open. Since IE6 doesn't have tabs, it will open them in seperate IE6 instances (or, if you set the env var SEQ, it will open them one after another in the order specified).

The script should be able to detect if an URI is a local file (and translate that, using winepath), or a remote page (in which case, it will pass the argument to ie6 as-is).

For extra ease-of-use, the script will recognize URIs with the string "localhost" in them and treat them as remote (that is, instead of passing localhost to winepath, it will pass it to ie6 as-is).

If you wish to use a hostname from your hosts file, create a new url regex like this:
    1. Copy the regex for localhost
    2. Change the word localhost to your desired name
    3. That's all to it :)

REQUIREMENTS:

IE6 as installed, using winetricks (I haven't tested it with ies4lin, as it didn't work last time I tried it). The script assumes it's installed to *~/.wine/drive_c/Program Files/Internet Explorer*

INSTALLATION:

Save the script to a file in your path (e.g. to /usr/bin/ie6).

Chmod it executable (**chmod +x `which ie6`**, for example)

EXAMPLE USE:

```

ie6 localhost /wtf.html http://kirsis:pass@somedomain.lv http://pods.lv

```

NOTE:

Remote URIs require the protocol to be present. Local ones do not.

THE ACTUAL SCRIPT:

```

#!/usr/bin/python

import sys, re, os


# Regular expressions for URL matching (to determine if argument = file or URI)
urlexps = [
	# For most URIs (excluding mailto:)	
	re.compile("^(?#Protocol)(?:(?:ht|f)tp(?:s?)\:\/\/|~/|/)?(?#Username:Password)(?:\w+:\w+@)?(?#Subdomains)(?:(?:[-\w]+\.)+(?#TopLevel Domains)(?:com|org|net|gov|mil|biz|info|mobi|name|aero|jobs|museum|travel|[a-z]{2}))(?#Port)(?::[\d]{1,5})?(?#Directories)(?:(?:(?:/(?:[-\w~!$+|.,=]|%[a-f\d]{2})+)+|/)+|\?|#)?(?#Query)(?:(?:\?(?:[-\w~!$+|.,*:]|%[a-f\d{2}])+=(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)(?:&(?:[-\w~!$+|.,*:]|%[a-f\d{2}])+=(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)*)*(?#Anchor)(?:#(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)?$"),
	
	# For localhost. Does not require the TLD or protocol
	re.compile("^(?#Protocol)(?:(?:ht|f)tp(?:s?)\:\/\/|~/|/)*(?#Username:Password)(?:\w+:\w+@)?(?#localhost)(?:localhost)(?#Port)(?::[\d]{1,5})?(?#Directories)(?:(?:(?:/(?:[-\w~!$+|.,=]|%[a-f\d]{2})+)+|/)+|\?|#)?(?#Query)(?:(?:\?(?:[-\w~!$+|.,*:]|%[a-f\d{2}])+=(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)(?:&(?:[-\w~!$+|.,*:]|%[a-f\d{2}])+=(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)*)*(?#Anchor)(?:#(?:[-\w~!$+|.,*:=]|%[a-f\d]{2})*)?$")
]


# Path to ie6 (if installed with winetricks. Not sure about ies4lin)
homedir = os.path.expanduser("~")
ie6_path = homedir+"/.wine/drive_c/Program\ Files/Internet\ Explorer/iexplore.exe "


if len(sys.argv) <= 1:
	os.system("wine " + ie6_path)
else:

	# IE6 doesn't support tabs, so you can't pass it more than one argument. 
	# Instead, launch ie6 multiple times.
	
	commands = []
	for x in xrange(len(sys.argv)-1):
	
		found_url = None	
		for exp in urlexps:
			found_url = found_url or exp.match(sys.argv[x+1])
		
		if found_url:
			commands.append( "wine " + ie6_path + found_url.group() )
		else:
			commands.append( "wine " + ie6_path + "`winepath -w "+ sys.argv[x+1]+"`" )

	# Execute the commands simultaneously unless the env var SEQ is given (for those with obscure habits :))
	for command in commands:
		os.system( command + ("& " if not os.getenv("SEQ") else "") )

```
 

CREDIT:

Got the regex for remote URIs from here: [http://geekswithblogs.net/casualjim/archive/2005/12/01/61722.aspx]("http://geekswithblogs.net/casualjim/archive/2005/12/01/61722.aspx"). It seems to work very well :)

I hope this is useful to some poor fellow web developer, who needs to check web pages in ie6 but is using Linux. 

Cheers.

---

