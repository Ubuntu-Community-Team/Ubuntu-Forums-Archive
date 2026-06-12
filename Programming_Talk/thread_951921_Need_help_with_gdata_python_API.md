---
title: "Need help with gdata python API"
date: 2008-10-18
forum: Programming Talk
---

### Post by onemillionaway on 2008-10-18
I've run into a weird error while testing out a script I've been working on to upload files to Google Docs. Here is the script:

```
import gdata
import gdata.docs
import gdata.docs.service
import mimetypes
import os.path
doctype = 0

def makechoice():
	choicetext = "What are you uploading? \n\
	[1] Word Document \n\
	[2] Spreadsheet \n\
	[3] Presentation\n\
Please enter a choice:"
	global doctype
	while True:
		try:
			doctype = int(input(choicetext))
			break
		except:
			print 'That is not a valid choice.'

def create_client():
	gd_client = gdata.docs.service.DocsService()
	gd_client.email = raw_input("Enter your Google Account e-mail address: ")
	gd_client.password = raw_input("Enter your Google Account password: ")
	gd_client.ProgrammaticLogin()
	print 'Login success.'
	return gd_client

def upload_file():
	global doctype
	while True:
		makechoice()
		if (doctype < 1):
			print 'That is not a valid choice.'
		elif (doctype > 3):
			print 'That is not a valid choice.'
		else:
			break
	while True:
		file_path = raw_input("Please enter the full path of the file you wish to upload: ")
		if os.path.isfile(file_path) == False:
			print 'That is not a valid file path.'
		else:
			break
	while True:
		default_title = file_path.split( '/' )[-1]
		default_title = default_title.split ( '.' )[0]
		title = raw_input("What would you like to name this file? Default is: " + default_title +" ")
		if (title != ""):
			break
		else:
			title = default_title
			break
	type = mimetypes.guess_type(file_path)
	ms = gdata.MediaSource(file_path = file_path, content_type = type[0])
	gd_client = create_client()
	if (doctype == 1):
		entry = gd_client.UploadDocument(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	elif (doctype == 2):
		entry = gd_client.UploadSpreadsheet(ms,title)
		print 'Link:', entry.getAlternateLink().href
	elif (doctype == 3):
		entry = gd_client.UploadPresentation(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	else:
		print 'Something failed.'

upload_file()
```

With anything other than a Word Document, i get an error stating that DocService has no attribute UploadPresentation or UploadSpreadsheet. Any help would be appreciated

---

### Post by snova on 2008-10-18
I have no idea what might be happening, but I wonder how you can use both getAlternateLink() and GetAlternateLink().

---

### Post by Can+~ on 2008-10-18
> **onemillionaway said:**
> I've run into a weird error while testing out a script I've been working on to upload files to Google Docs. Here is the script:

```
import gdata
import gdata.docs
import gdata.docs.service
import mimetypes
import os.path
doctype = 0

def makechoice():
	choicetext = "What are you uploading? \n\
	[1] Word Document \n\
	[2] Spreadsheet \n\
	[3] Presentation\n\
Please enter a choice:"
	global doctype
	while True:
		try:
			doctype = int(input(choicetext))
			break
		except:
			print 'That is not a valid choice.'

def create_client():
	gd_client = gdata.docs.service.DocsService()
	gd_client.email = raw_input("Enter your Google Account e-mail address: ")
	gd_client.password = raw_input("Enter your Google Account password: ")
	gd_client.ProgrammaticLogin()
	print 'Login success.'
	return gd_client

def upload_file():
	global doctype
	while True:
		makechoice()
		if (doctype < 1):
			print 'That is not a valid choice.'
		elif (doctype > 3):
			print 'That is not a valid choice.'
		else:
			break
	while True:
		file_path = raw_input("Please enter the full path of the file you wish to upload: ")
		if os.path.isfile(file_path) == False:
			print 'That is not a valid file path.'
		else:
			break
	while True:
		default_title = file_path.split( '/' )[-1]
		default_title = default_title.split ( '.' )[0]
		title = raw_input("What would you like to name this file? Default is: " + default_title +" ")
		if (title != ""):
			break
		else:
			title = default_title
			break
	type = mimetypes.guess_type(file_path)
	ms = gdata.MediaSource(file_path = file_path, content_type = type[0])
	gd_client = create_client()
	if (doctype == 1):
		entry = gd_client.UploadDocument(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	elif (doctype == 2):
		entry = gd_client.UploadSpreadsheet(ms,title)

		print 'Link:', entry.getAlternateLink().href
	elif (doctype == 3):
		entry = gd_client.UploadPresentation(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	else:
		print 'Something failed.'

upload_file()
```

With anything other than a Word Document, i get an error stating that DocService has no attribute UploadPresentation or UploadSpreadsheet. Any help would be appreciated

I don't understand why you create a global out of doctype, when it could be perfectly returned by the function, also, move all the user input validation to the function make_choice and then just return a tuple or an object out of it, this is for tidiness mostly.

As for the problem goes, I'm still trying to figure out the mistake. The function is clearly being called, the problem lies in the gd_client object, do a [font="Courier New"]print dir(gd_client)[/font] in your code.

---

### Post by onemillionaway on 2008-10-19
Putting a print dir(gd_client) outputs:

['ClientLogin', 'Delete', 'GenerateAuthSubURL', 'Get', 'GetAuthSubToken', 'GetClientLoginToken', 'GetDocumentListEntry', 'GetDocumentListFeed', 'GetEntry', 'GetFeed', 'GetMedia', 'Post', 'ProgrammaticLogin', 'Put', 'Query', 'QueryDocumentListFeed', 'RevokeAuthSubToken', 'SetAuthSubToken', 'SetClientLoginToken', 'UpgradeToSessionToken', 'UploadDocument', 'UploadSpreadsheet', 'UseBasicAuth', '_CreateConnection', '_GDataService__GetAuthToken', '_GDataService__GetCaptchaToken', '_GDataService__GetCaptchaURL', '_GDataService__GetSource', '_GDataService__SetAuthSubToken', '_GDataService__SetSource', '_GDataService__auth_token', '_GDataService__auth_type', '_GDataService__captcha_token', '_GDataService__captcha_url', '_GDataService__gsessionid', '_GDataService__source', '_GetAuthToken', '_GetCaptchaToken', '_GetCaptchaURL', '_PrepareConnection', '_ProcessUrl', '_SetAuthSubToken', '_UploadFile', '__class__', '__delattr__', '__dict__', '__doc__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__str__', '__weakref__', 'account_type', 'additional_headers', 'auth_token', 'captcha_token', 'captcha_url', 'debug', 'email', 'password', 'port', 'server', 'service', 'skip_host', 'source', 'ssl']

It's showing UploadSpreadsheet now but the Google PyDoc for this object also lists UploadPresentation. Any ideas? Is Ubuntu's gData API just out of date?

---

### Post by onemillionaway on 2008-10-19
Okay, I cleaned up the code a little bit and put in a few messages to the user about the title and success of login. Also, Documents and Spreadsheets are working, but presentations still fail due to the attribute not existing in Ubuntu's version at least.

```
import gdata.docs.service
import mimetypes
import os.path

def create_client():
	client = gdata.docs.service.DocsService()
	client.email = raw_input("Enter your Google Account e-mail address: ")
	client.password = raw_input("Enter your Google Account password: ")
	client.ProgrammaticLogin()
	print 'Login success.'
	return client

def choose_file():
	choicetext = "What are you uploading? \n\
	[1] Word Document \n\
	[2] Spreadsheet \n\
	[3] Presentation\n\
Please enter a choice: "
	while True:
		try:
			doctype = int(input(choicetext))
			break
		except:
			print 'That is not a valid choice. 1'
	while True:
		if (doctype < 1):
			print 'That is not a valid choice. 2'
		if (doctype > 3):
			print 'That is not a valid choice. 3'
		else:
			break
	while True:
		file_path = raw_input("Please enter the full path of the file you wish to upload: ")
		if os.path.isfile(file_path) == False:
			print 'That is not a valid file path.'
		else:
			break
	default_title = file_path.split( '/' )[-1]
	default_title = default_title.split( '.' )[0]
	title = raw_input("Enter a name for the file(Default is " + default_title + "): ")
	if (title == ""):
		title = default_title
		print "Title is: " + title + "."
	else:
		print "Title is: " + title + "."
	return doctype, title, file_path

def UploadFile():
	doctype, title, file_path = choose_file()
	type = mimetypes.guess_type(file_path)
	ms = gdata.MediaSource(file_path = file_path, content_type = type[0])
	client = create_client()
	if (doctype == 1):
		entry = client.UploadDocument(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	elif (doctype == 2):
		entry = client.UploadSpreadsheet(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	elif (doctype == 3):
		entry = client.UploadPresentation(ms,title)
		print 'Link:', entry.GetAlternateLink().href
	else:
		print 'Something failed.'
		return 1

UploadFile()
```

---

### Post by Can+~ on 2008-10-19
Other things you can improve:

**1.**
instead of "[FONT="Courier New"]if (doctype < 1) ... if (doctype > 3)[/FONT]" you can use "[FONT="Courier New"]if doctype in range(1,4):[/FONT]" or at least stick both conditions into one "[FONT="Courier New"](doctype < 1 and doctype > 3)[/FONT]"

**2.**
Use [FONT="Courier New"]os.sep[/FONT] for handling the separator in different platforms. In fact, you can use [FONT="Courier New"]os.path.split(path)[/FONT] to make a safe split (it returns a tuple with a pair (folder, filename)

**3.**
When asking for the title, use _.strip()_* to make sure the user doesn't enter empty characters (" ").

**4.**
```
print "Title is: " + title + "."
```

can be written as (at least with pre-python 3):

```
print "Title is: %s." % title
```

In fact, you can summarize that whole part as (a little binary tuple trick)

```
title = title.split()
print "Title is: %s." % (title, default_title)[title == ""]
```

(title = "" returns True or False (0 or 1), if fed to a tuple (x, y)[condition] you can access the 0 or 1 element of said tuple with this technique, this is totally optional, if you want clearer code, stick with the if-elif method)

*edit: I wrote split instead of strip.

---

### Post by onemillionaway on 2008-10-19
> 1.
instead of "if (doctype < 1) ... if (doctype > 3)" you can use "if doctype in range(1,4):" or at least stick both conditions into one "(doctype < 1 and doctype > 3)"

2.
Use os.sep for handling the separator in different platforms. In fact, you can use os.path.split(path) to make a safe split (it returns a tuple with a pair (folder, filename)

3.
When asking for the title, use .split() to make sure the user doesn't enter empty characters (" ").

Okay. I've changed #1 to both conditionals on one line, and that works perfectly. #2 was also changed to use os.path.split(path) in order to get the filename a little cleaner. I'm not sure how to implement #3 however(I think google automatically gives it the equivalent of default_title when it gets an empty string), I'm still a newbie at python, most of what I've got so far took the better part of a weekend and a lot of luck to get. :) 

With how many revisions I'm making to this, I might as well start a sourceforge page for it or something. I'm hoping to have a fully functional shell program that will allow a user to list the contents of their Google Docs account, delete content, search for content, and of course, upload more content. I should probably move the create_client() function off into it's own login.py file, and just import it into each other file.

---

### Post by onemillionaway on 2008-10-20
Nevermind what this post said, I just fixed the problem. :) The script now uploads files, lists files, searches files, and deletes files from google docs. Can you take a look at the code and give suggestions/patches on how to clean it up a little? There's 6 .py files.

---

### Post by markybob on 2010-05-03
> **onemillionaway said:**
> Nevermind what this post said, I just fixed the problem. :) The script now uploads files, lists files, searches files, and deletes files from google docs. Can you take a look at the code and give suggestions/patches on how to clean it up a little? There's 6 .py files.

can you post the final code, please?

---

