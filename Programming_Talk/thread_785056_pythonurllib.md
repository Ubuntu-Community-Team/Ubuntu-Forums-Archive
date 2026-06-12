---
title: "python:urllib"
date: 2008-05-07
forum: Programming Talk
---

### Post by bala_biophy on 2008-05-07
Dear friends,
I have written a small code to fetch a list of files from a url. I hv pasted the code and error, kindly write me what goes wrong.

import urllib                                                                                                           
f1=open("list")
l=f1.readlines()
for x in l:

---

### Post by bala_biophy on 2008-05-07
_code_
import urllib                                                                                                           
f1=open("list")
l=f1.readlines()
for x in l:
     f=urllib.urlopen("http://www.rcsb.org/pdb/explore/explore.do?structureId="+x)
    sh=f.read()
    f.close()
    print sh

_error_
Traceback (most recent call last):
  File "retrieve.py", line 6, in ?
    f=urllib.urlopen("http://www.rcsb.org/pdb/explore/explore.do?structureId="+x)
  File "/usr/local/lib/python2.4/urllib.py", line 82, in urlopen
    return opener.open(url)
  File "/usr/local/lib/python2.4/urllib.py", line 190, in open
    return getattr(self, name)(url)
  File "/usr/local/lib/python2.4/urllib.py", line 313, in open_http
    h.endheaders()
  File "/usr/local/lib/python2.4/httplib.py", line 798, in endheaders
    self._send_output()
  File "/usr/local/lib/python2.4/httplib.py", line 679, in _send_output
    self.send(msg)
  File "/usr/local/lib/python2.4/httplib.py", line 646, in send
    self.connect()
  File "/usr/local/lib/python2.4/httplib.py", line 614, in connect
    socket.SOCK_STREAM):
IOError: [Errno socket error] (-2, 'Name or service not known')

---

### Post by skeeterbug on 2008-05-07
```

import urllib

if __name__ == "__main__":
    url = 'http://www.rcsb.org/pdb/explore/explore.do'
    post_data = {'structureId' : '10'}
    param = urllib.urlencode(post_data)
    opener = urllib.urlopen(url, param)
    html = opener.read()
    opener.close()
    print html

```

Works for me, the HTML it returned indicates my parameter caused this application to throw an exception. What are you using for the querystring? Make sure to encode it (so it can handle special characters, spaces, etc).

---

### Post by pk_rulz on 2009-12-18
Even I am facing a similar problem

***********************
import urllib

f = urllib.urlopen("http://www.python.com/")
s = f.read()
print s
f.close()
****************************

The above mentioned code is taken from python official documentation but it does not work on my machine and raises the error

IOError: [Errno socket error] (-2, 'Name or service not known')


I have tried many websites in the url including some under construction websites but nothin seems to work ... My computer is connected to the internet without any proxy. Also my urlopen has failed when I used it to open the request object returned by urlib2.Request 

Any help please ... My 3rd day with Python

---

### Post by insanecrazy4 on 2009-12-18
this is just a shot in the dark so python gurus dont flame me :P

it worked fine for me in 2.6 could it be the because you may be using 3.0?

---

### Post by pk_rulz on 2009-12-19
> **insanecrazy4 said:**
> this is just a shot in the dark so python gurus dont flame me :P

it worked fine for me in 2.6 could it be the because you may be using 3.0?

Well I am using v2.5.2 on Ibex ... any comments on that

---

### Post by pk_rulz on 2009-12-20
Well got that problem sorted ... was behind my university proxy for some time ... after I was home I did change the proxy and test but it never worked  ...

The reason ... a reboot was needed after changing the proxy in systems >> preferences >> network proxy

after that just to be sure I reinstalled my python v2.5 ... using the GUI package manager ...

Bing problem sorted ...  Bala I thnk dat may hlp U

---

