---
title: "Running cgi scripts in Python"
date: 2009-06-30
forum: Programming Talk
---

### Post by scheibo on 2009-06-30
I've been trying to do CGI scripting in python on my linux, but I have problems getting it to work. I'm trying to follow "Programming Python" (Mark Lutz, 3rd edition), and i'm using the web server program he offers on page 968:

```
#!/usr/bin/python
#python server (968)

webdir = '.' #where html and cgi-bin files live
port = 80    #use http://localhost/

import os, sys
from BaseHTTPServer import HTTPServer
from CGIHTTPServer import CGIHTTPRequestHandler

if len(sys.argv) > 1: webdir = sys.argv[1]
if len(sys.argv) > 2: port = int(sts.argv[2])
print 'webdir: "%s", port %s' % (webdir, port)

#windows hack, os.environ not propagated
if sys.platform[:3] == 'win':
    CGIHTTPRequestHandler.have_popen2 = False
    CGIHTTPRequestHandler.have_popen3 = False #emulate path after fork
    sys.path.append('cgi-bin')                #else only adds my dir

os.chdir(webdir)                              #run in HTML root dir
srvraddr = ("", port)                         #my hostname, port number
srvrobj = HTTPServer(srvraddr, CGIHTTPRequestHandler)
srvrobj.serve_forever()                       #serve clients till exit


```

this script resides in my home directory,and when i run it with 'python server.py' it gives me a the following error:

scheibo@knb$ python server.py 
webdir: ".", port 80
Traceback (most recent call last):
  File "server.py", line 23, in <module>
    srvrobj = HTTPServer(srvraddr, CGIHTTPRequestHandler)
  File "/usr/lib/python2.6/SocketServer.py", line 400, in __init__
    self.server_bind()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 108, in server_bind
    SocketServer.TCPServer.server_bind(self)
  File "/usr/lib/python2.6/SocketServer.py", line 411, in server_bind
    self.socket.bind(self.server_address)
  File "<string>", line 1, in bind
[COLOR="Red"]socket.error: [Errno 13] Permission denied[/COLOR]

permission denied? i then try 'sudo python server.py', and after this the script works fine. the server runs as a daemon and everything seems peachy keen. however, my problem is when trying to actually USE it with my browser. Using the tutor0.py:example from the book (which resides in a cgi-bin directory in my home director)

```

print "Content-type: text/html\n"
print "<TITLE>CGI 101</TITLE>"
print "<H1>A First CGI script</H1>"
print "<P>Hello, CGI World!</P>"

```

i type: [http://localhost/cgi-bin/tutor0.py](http://localhost/cgi-bin/tutor0.py) into firefox and a box pops up asking me what to do with 'tutor0.py, python script'. the default option it provides is to open in a text editor, but upon opening the file it is blank. 

My problem is that I want to figure out how to get the generated tutor.py script output to appear in my web browser. if i look at the output in the terminal that is running server.py, I see:


webdir: ".", port 80
localhost - - [30/Jun/2009 00:14:11] "GET /cgi-bin/tutor0.py HTTP/1.1" 200 -
[COLOR="Red"]Traceback (most recent call last):
  File "/usr/lib/python2.6/CGIHTTPServer.py", line 255, in run_cgi
    os.execve(scriptfile, args, os.environ)
OSError: [Errno 13] Permission denied[/COLOR]
localhost - - [30/Jun/2009 00:14:11] CGI script exit status 0x7f00
localhost - - [30/Jun/2009 00:14:20] "GET /cgi-bin/tutor0.py HTTP/1.1" 200 -


which judging by the permission denied again leads me to believe that this is an administrator privilege thing. i've tried running this script on 2.5, 2.6 and 3.0 and no luck (for 3.0 i changed the print statements to function calls of course). any idea how i can get this cgi stuff to work?

tia

---

### Post by monraaf on 2009-06-30
For the first problem, choose a port >= 1024 (e.g. 8080) instead of using sudo. For the second problem:

```

chmod a+x tutor0.py

```

Oh, and also make sure the tutor0.py script starts with:

```

#!/usr/bin/env python

```

---

### Post by The Cog on 2009-06-30
monraaf is right.

Firstly, normal users are not allowed to open listening sockets on port numbers below 1024.

Secondly, the cgi script must be executable by the server. This involves setting the executable flag, and also specifying on the first line of the script which interpreter should be used (e.g. python, perl etc).

---

### Post by scheibo on 2009-06-30
I had already made both files (server and tutor) fully executable using chmod beforehand, so that's not the problem. Sorry I forgot to mention it, I just thought it would be assumed that I had made it executable seeing as I was trying to run it as a program. My bad. My python is also located at /usr/bin/python, so using env doesn't necessarily help. 

The trick was in fact to do as monraaf suggested and change ports. I changed the initilization of the port in the server.py script to 'port = 8080' and then used: [http://localhost:8080/cgi-bin/tutor0.py](http://localhost:8080/cgi-bin/tutor0.py) in the browser instead and it worked! Thanks a lot guys!

---

### Post by Can+~ on 2009-06-30
Or you can use any port and access with

[http://127.0.0.1:number](http://127.0.0.1:number)

You're not restricted to 80/8080, you could use any port.

---

### Post by jdmcbr on 2011-03-23
I hope reviving an old thread is okay. I was running in to the same error as the original poster, and followed the advice in the thread to change ports. After doing that, I no longer received the original error message. Instead, I am now seeing 

localhost - - [23/Mar/2011 14:38:49] "GET /cgi-bin/tutor0.py HTTP/1.1" 200 -
: No such file or directory
localhost - - [23/Mar/2011 14:38:49] CGI script exit status 0x7f00

The file definitely exists. I am running webserver.py, and in the directory in which webserver.py is running, there is a directory called cgi-bin with a file called tutor0.py in it. I have tried both variations of 

#!/usr/bin/env python
and
#!/usr/bin/python

Also, /usr/bin/ is where python is, and all the files are executable. So I think I have addressed all of the suggestions here for what the problem might be, but I still cannot get it to work. 

Thanks in advance for any help.

---

### Post by gabdab on 2011-04-15
> I hope reviving an old thread is okay. I was running in to the same error as the original poster, and followed the advice in the thread to change ports. After doing that, I no longer received the original error message. Instead, I am now seeing

I found the permissions settings to be critical :
```
chmod a+x cgi-bin/ -R

```
Ports are not a clue .

---

### Post by jdmcbr on 2011-04-15
I mentioned having already changed the permissions to make all files executable, so unfortunately, that is not it.

---

### Post by hyperfocus on 2011-08-16
i had this problem after moving the scripts from windows to linux. I ran dos2unix on the files and all is well.

---

### Post by jdmcbr on 2011-08-16
Thanks so much! That worked for me.

---

