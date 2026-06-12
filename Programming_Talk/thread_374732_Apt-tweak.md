---
title: "Apt-tweak"
date: 2007-03-02
forum: Programming Talk
---

### Post by kerry_s on 2007-03-02
Hey all, i came across this site-> [http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/](http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/)

and it sounds very interesting, the problem is i don't know jack about code, but i'm reading. I would like to remove the wget feature and have it use the pipelining for any thing less than 1mb and axle for anything above that. So far i just made it computer independent, by moving everything to /usr/bin/. Also there's sometimes a problem at the end of "sudo apt-get update" were it seems to hang on "bzip2".

So anyone want to take a look and see if we can improve apt some?
Code attached:

---

### Post by kerry_s on 2007-03-02
Hey sorry had to step out.

So what i think would be the easiest would be to have the "wget section" instead point back to the orginal /usr/lib/apt/methods/http.save.

So any one can tell me what to put.

```
#!/usr/bin/python
import httplib
import urlparse
import sys
import os

url=urlparse.urlsplit(sys.argv[1])

conn = httplib.HTTP(url[1])
conn.putrequest("HEAD", url[2])
conn.putheader("HOST",url[1]);
conn.endheaders();
errcode,errmsg,headers = conn.getreply()

#f = open("/tmp/test.log","a")
#f.write("File : " + url[1] + " " + url[2] + "\n");
#f.write("Status Code : " + str(errcode) + "\n")
if (errcode!=200 and errcode!=301) :
	if (errcode==404):
		sys.exit(15)
	sys.exit(errcode)
try:
	size = int(headers["Content-Length"])
except KeyError:
	size = 101*1024

#f.write("Size : " + str(size) + "\n");

if (size<=(100*1024)):
#	f.write("wget " + url[2] + " " + str(size)+"\n")
	os.system("wget -c -O " + sys.argv[2] + " " + sys.argv[1])
else :
	count = int(size)/(10*1024)
	if (count>50): 
		count=50
#	f.write("axel " + url[2] + "\n" )
	os.system("axel -n " + str(count) + " -o " + sys.argv[2] + " " + sys.argv[1])

#f.close()

```

---

### Post by Canes on 2007-03-04
I don't think you can call the original http file again, it doesn't accept any command line parameters.

---

### Post by go_beep_yourself on 2007-10-29
You could try this guide instead.

[http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/](http://www.sandaru1.com/2007/02/14/enhance-apt-get-downloading-using-an-external-download-acceleratoraxelprozillaaget/)

---

