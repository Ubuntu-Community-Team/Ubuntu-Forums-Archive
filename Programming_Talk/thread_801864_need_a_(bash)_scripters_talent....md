---
title: "need a (bash?) scripters talent..."
date: 2008-05-21
forum: Programming Talk
---

### Post by woedend on 2008-05-21
hi guys.  I have something like 400 pictures that are archived on a server that I don't remember the username or password to.  They are all numbered pic001.jpg to pic382.jpg.  There is no index page to do a mass copy.  me, having no knowledge of bash, is wondering if there is a way that a bash script could be written, where X could be set as a 3 digit integer variable, where i could save picX.jpg to /home/pictures/picX.jpg, then do a X + 1 until X = 599
Any scripts would be GREATLY welcome, doing this manually in firefox is taking FOREVER.
Thanks for any help,
alex.

---

### Post by Can+~ on 2008-05-21
I'm not an expert on bash scripts, but I could do a python one:

[PHP]import urllib
import os


def storeFile(folder, filename, baseurl):
	#local folder
	fullpath = os.path.join(folder, filename)
	
	#and website's url
	fullurl = baseurl + filename

	#If file is not locally, store it.	
	if not os.path.exists(fullpath):
		print "Storing %s" % (filename),
		#Open and read
		furl	= urllib.urlopen(fullurl)
		flocal	= furl.read()
		
		#Store
		ffile = open(fullpath, "w")
		ffile.write(flocal)
		ffile.close()
		print "... stored"""
		
	print fullpath, fullurl

def start():
	#Change this:
	#Make sure the baseurl ends with "/"!!
	#Also, make sure the folder exists before attempting to run this.
	folder = "/home/yourname/pictures/"
	baseurl = "http://www.myhost.com/mysite/"
	basename = "pic"
	filetype = ".jpg"
	
	#Main iteration
	for id in xrange(1,383):
		filename = basename+str(id).zfill(3)+filetype
		
		storeFile(folder, filename, baseurl)

start()[/PHP]

---

### Post by ghostdog74 on 2008-05-21
> **woedend said:**
> hi guys.  I have something like 400 pictures that are archived on a server that I don't remember the username or password to.  They are all numbered pic001.jpg to pic382.jpg.  There is no index page to do a mass copy.  me, having no knowledge of bash, is wondering if there is a way that a bash script could be written, where X could be set as a 3 digit integer variable, where i could save picX.jpg to /home/pictures/picX.jpg, then do a X + 1 until X = 599
Any scripts would be GREATLY welcome, doing this manually in firefox is taking FOREVER.
Thanks for any help,
alex.
don't understand. seems like you want to move all the picX.jpg into /home/pictures?? then simple mv pic* /home/pictures may suffice. unless i am missing out something.

---

### Post by geirha on 2008-05-21
Do you mean you want to download those images from a web-server?
The following should download pic001.jpg to pic400.jpg from a web-server.
```

for i in $(seq -f"%03g" 1 400); do
  wget http://hostname/pic${i}.jpg
done

```

---

### Post by rye_ on 2008-05-21
hmmm.

messes this up

---

