---
title: "New to Python: Google Docs Upload Project"
date: 2008-10-18
forum: Programming Talk
---

### Post by onemillionaway on 2008-10-18
Hello everyone. I'm a beginner to Python and I've decided to start a project to help me learn the language. Since I could not find an easy way to upload files to Google Docs from the desktop, I figured that I could help both myself and the community by attempting to create one. At the moment I have a very basic prototype that asks for authentication info and the full path of a file, while checking and outputting the content-type to the Google Docs server. I'd like to add some basic user input checks and possibly migrate it over to PyGTK with more features, such as a list of all files, a delete function, mass upload, and possibly download. If anyone could help me that'd be great, as I am completely lost with PyGTK.

Here's the script I have so far:
```
from gdata.docs import service
import mimetypes

def create_client():
	client = service.DocsService()
	client.email = raw_input("Enter your Google Account e-mail address: ")
	client.password = raw_input("Enter your Google Account password: ")
	client.ProgrammaticLogin()
	return client

def upload_file():
	import gdata
	file_path = raw_input("Please enter the full path of the file you wish to upload: ")
	title = raw_input("What would you like to name this file? ")
	type = mimetypes.guess_type(file_path)
	ms = gdata.MediaSource(file_path = file_path, content_type = type[0])
	client = create_client()
	entry = client.UploadDocument(ms,title)
	print 'Link:', entry.GetAlternateLink().href

upload_file()

```

---

### Post by true_friend on 2008-10-18
I was looking for the same idea in C#. It will help me to write code in C#.

---

### Post by Can+~ on 2008-10-18
Don't waste time with PyGTK. I mean, is not bad, but build a full working application first in the shell, and when that is done, build a GUI with Glade, Micah Carrik has a good tutorial for all that:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html)

---

