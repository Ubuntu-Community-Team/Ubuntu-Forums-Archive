---
title: "python-fuse help"
date: 2009-12-13
forum: Programming Talk
---

### Post by matmatmat on 2009-12-13
I am trying to use fuse with google docs to create a local version of the files:
```

-*- coding: utf-8 -*-
import gdata.docs.service
import fuse
from fuse import *
import os
import tempfile
from errno import * 
import time

user = '###'
passwrd = '###'

cachedir = tempfile.mkdtemp(prefix='fuse-')
os.mkdir(os.path.join(cachedir, 'odt'))
os.mkdir(os.path.join(cachedir, 'pdf'))

class MyStat(Stat):
	def __init__(self):
		self.st_mode = 0
		self.st_ino = 0
		self.st_dev = 0
		self.st_nlink = 0
		self.st_uid = 0
		self.st_gid = 0
		self.st_size = 0
		self.st_atime = 0
		self.st_mtime = 0
		self.st_ctime = 0

	def tuple():
		return (self.st_mode, self.st_ino, self.st_dev, self.st_nlink, self.st_uid, self.st_gid, self.st_size, self.st_atime, self.st_mtime, self.st_ctime)
class MyFS(Fuse):
	def getattr(self, path):
		st = MyStat()
		st.st_atime = int(time.time())
		st.st_mtime = st.st_atime
		st.st_ctime = st.st_atime
		path_element = path.split('/')
		if path == '/':
			#return os.lstat(path)
			st.st_mode = stat.S_IFDIR | 0755
			st.st_nlink = 2
			st.st_size = 4096
		elif path_element[1] == 'odt':
			if len(path_element) == 2:
				return os.lstat(path)
				st.st_mode = stat.S_IFDIR | 0775
				st.st_nlink = 2
			else:
				tpath = os.path.join(cachedir, path[1:])
				if os.path.exists(tpath):
					real = os.stat(tpath)
					st.st_size = real.st_size
				else:
					st.st_size = 2045
				st.st_mode = stat.S_IFREG | 0444
				st.st_nlink = 1
		else:
			return -errno.ENOENT
		return st

	def readdir(self, path, offset):
		dirents = ['.','..']
		if path == '/':
			dirents.extend(['odt','doc','pdf'])
		elif path == '/odt':
			client = gdata.docs.service.DocsService()
			client.ClientLogin(user,passwrd)
			list = client.GetDocumentListFeed()
			for entry in list.entry:
				if entry.GetDocumentType() == 'document':
					dirents.append(entry.title.text + '.odt')

		for e in dirents:
			yield fuse.Direntry(e)

	def open(self, path, flags):			
		path_element = path.split('/')
		fname = path_element[-1]
		client=gdata.docs.service.DocsService()
		client.ClientLogin(user,passwrd)
		q = gdata.docs.serice.DocumentQuery()
		q['title'] = fname[:-4]
		q['title-exact'] = 'true'
		list = client.Query(q.ToUri())
		tfile = os.path.join(cachedir, path[1:])
		client.Export(list.entry[0], tfile)
		filehandle = open(tfile, 'r')
		return filehandle

	def read(self, path, size, offset=0, filehandle=None):
		filehandle.seek(offset)
		buffer = filehandle.read(size)
		return buffer


fuse.fuse_python_api = (0, 2)
fs = MyFS()
fs.parse(errex=1)
fs.main()


```
when I try to ls the dir:
```

[matio@myhost fuse]$ python fuse_docs.py mount
/usr/lib/python2.6/site-packages/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
[matio@myhost fuse]$ ls mount/
ls: cannot access mount/: Invalid argument
[matio@myhost fuse]$

```
can someone help?

---

### Post by matmatmat on 2009-12-14
No one?

---

### Post by nutznboltz on 2010-01-15
Install dependencies:

aptitude install python-fuse python-elementtree 

Karmic only has python-gdata 1.2.4-0ubuntu2 which is FAIL.

[http://code.google.com/p/gdata-python-client/](http://code.google.com/p/gdata-python-client/) has gdata 2.0.6

Fetch and install that.

Once the dependencies are satisfied:

svn co http://google-docs-fs.googlecode.com/^Cn/trunk/ google-docs-fs

and install that.

Then "gmount /doc john.doe" will work.

mount | grep gFile
gFile.py on /g type fuse.gFile.py (rw,nosuid,nodev,user=nutznboltz)

---

### Post by matmatmat on 2010-01-24
Thanks for the reply, I was hoping to use the script I posted earlier, but it doesn't seem to work (I've tried it on Ubuntu & Arch).

---

### Post by Yrrepperry on 2010-09-13
what about when not using fuse?
e.g. with google app engine, I get the same problem:
DeprecationWarning: the sha module is deprecated; use the hashlib module instead
 DeprecationWarning: the md5 module is deprecated; use hashlib instead

(use of these modules in not in anything I wrote, but so I gather it is in the Google appengine SDK)

---

### Post by juancarlospaco on 2010-09-13
```
import fuse
from fuse import *
```

BTW is redundant, or im wrong *(?)*

---

