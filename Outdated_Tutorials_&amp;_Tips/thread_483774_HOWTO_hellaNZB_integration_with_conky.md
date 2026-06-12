---
title: "HOWTO: hellaNZB integration with conky"
date: 2007-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by honeydew on 2007-06-25
1) I got information for this howto all over the place....
[http://hellanzb.com/](http://hellanzb.com/)
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)
[http://www.python.org/](http://www.python.org/)

2) I am on feisty using the xfce4 interface I have a core2 duo I am running the generic kernel

3) This is a set of python scripts that help integrate hellanzb and conky

4) You will need HellaNZB and Conky

5) I cant really support this! this isnt official I just spent 4 hours of my life figuring this out..  I am a active BSD/linux user but I would consider myself a n00b in every sense of the word.  I will be back here to improve on this and work with others to make this work better.. but really really do this at your own risk.. I REALLY REALLY dont know what Im doing... etc etc.

my setup currently involves hellafox(firefox newzbin download extension) and then a couple little scripts that report the output to conky..

**this script is in active development please go [here]("http://wiki.arcintel.com/doku.php?id=hellaconk") for the most current information**

wiki: [http://wiki.arcintel.com/doku.php?id=hellaconk]("http://wiki.arcintel.com/doku.php?id=hellaconk")

here is a screenshot of conky+hellanzb in action =]

---

### Post by Computer-Geek on 2007-06-27
It's great.

---

### Post by kaath on 2007-06-27
nice script but doesn't work :(

any idea on what i need to do?

```
14:02 guillaume@guillaume-desktop ~% conky
Traceback (most recent call last):
  File "/usr/bin/hellaconk.py", line 41, in <module>
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.5/optparse.py", line 1378, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1422, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1529, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.5/optparse.py", line 782, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.5/optparse.py", line 802, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "/usr/bin/hellaconk.py", line 10, in NZB
    download = hellanzbServer.status()['currently_downloading']
  File "/usr/lib/python2.5/xmlrpclib.py", line 1147, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1437, in __request
    verbose=self.__verbose
  File "/usr/lib/python2.5/xmlrpclib.py", line 1183, in request
    self.send_content(h, request_body)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1297, in send_content
    connection.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 856, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 728, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 695, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 679, in connect
    raise socket.error, msg
socket.error: (111, 'Connection refused')


```

---

### Post by phoenixnr on 2007-06-27
I get the same error. :(

---

### Post by honeydew on 2007-06-27
momment.. Im checking on this.. seeing if I can diagnose the problem...

---

### Post by honeydew on 2007-06-27
2 things I could think of.. 

1. your server isnt running? or you didnt enter in your login info correctly at the top of the script. 

2.  Turn on conky.. enqueue a NZB(ignore any errors, they wont hurt yah) and see if you have the same issues...

I havnt learned howto write if/else statements in python yet... thus getting rid of some of these errors..  I took grabbed the exact script off mysite.. changed the ip info because my hellanzb isnt at local host.. and then enqueued a nzb and everything worked..

```

~$ ./hell.py -h
Usage: hell.py [options]

Options:
  -h, --help     show this help message and exit
  -n, --nzb      output current NZB
  -r, --rate     output hellanzb rate
  -p, --percent  output completion percentage of current NZB
  -e, --eta      displays the ETA of the current NZB
~$ ./hell.py -n
The Simpsons - 5x07 - Bart's Inner Child
~$ ./hell.py -r
97
~$ ./hell.py -p
12
~$ ./hell.py -e
00:25:57


```

when my server was not configured properly I received the same error(check in your hellanzb.conf file for that info)
```

~$ ./hell.py -e
Traceback (most recent call last):
  File "./hell.py", line 42, in <module>
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.5/optparse.py", line 1378, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1422, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1529, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.5/optparse.py", line 782, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.5/optparse.py", line 802, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "./hell.py", line 23, in ETA
    eta = hellanzbServer.status()['eta']
  File "/usr/lib/python2.5/xmlrpclib.py", line 1147, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1437, in __request
    verbose=self.__verbose
  File "/usr/lib/python2.5/xmlrpclib.py", line 1183, in request
    self.send_content(h, request_body)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1297, in send_content
    connection.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 856, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 728, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 695, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 679, in connect
    raise socket.error, msg
socket.error: (111, 'Connection refused')

```

I receive this error when something it runs with out anything queued..
```

~$ ./hell.py -n
Traceback (most recent call last):
  File "./hell.py", line 42, in <module>
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.5/optparse.py", line 1378, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1422, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1529, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.5/optparse.py", line 782, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.5/optparse.py", line 802, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "./hell.py", line 11, in NZB
    print download[0]['nzbName']
IndexError: list index out of range

```


I hope this helps you a bit.. all this can/will be fixed when I learn a bit more about python.. or someone helps me out a bit.

---

### Post by kaath on 2007-06-27
i'll check this tomorrow morning ;)

---

### Post by phoenixnr on 2007-06-27
Thanks! Fixed for me.

---

### Post by kaath on 2007-06-28
fixed for me too, was a wrong password	:-$

---

### Post by honeydew on 2007-06-28
hey just for kicks it would be cool if you guys could post a screenshot of your conky with hellanzb in action.. I would love to post them on my wiki..

---

### Post by kd7swh on 2007-11-24
Nice work on the script, here is a screenshot as requested for your wiki.

---

### Post by honeydew on 2007-11-25
2000kbs!! are you on the new ny fios?

---

### Post by kd7swh on 2007-11-25
No, I am on a campus network.

---

### Post by kd7swh on 2007-12-26
I am having problems with the ETA feature. I think it is a bottleneck issue. I just had my bandwidth boosted. (getting about 9,000 - 10,000kbps) So I think its downloading the rest of a file before it can update the ETA and it gets stuck.

I haven't even looked yet but I am sure there is an update interval in the python script. Can this safely be changed to accommodate faster connections?

---

### Post by theluddite on 2008-01-20
After a bit of mucking about, I was able to get Hellanzb working but I'm having trouble integrating it into my browser and desktop like honeydew did.  

First problem:  I can't get hellafox to work.  I'm a complete neophyte so I may have the settings wrong or something.  Exactly where in the hellanzb.conf file would I find the settings for Hellafox?  The only password I entered in the conf file is the one for hellanzb to connect 
to my newserver, where is the password to connect to hellanzb?

Second problem:  Hellaconk isn't working.  I've got similar errors to the other posts (below), but I still have no clue how to correctly configure my server.  Can someone walk me through it?


> theluddite@small:~$ conky
Conky: can't load font 'arial'
Conky: statfs '/media/hda1': No such file or directory
Conky: statfs '/media/hdb3': No such file or directory
Conky: desktop window (e0013f) is subwindow of root window (52)
Conky: window type - override
Conky: drawing to created window (3e00003)
Conky: drawing to double buffer
Conky: statfs '/media/hdb3': No such file or directory
Conky: statfs '/media/hda1': No such file or directory
Traceback (most recent call last):
  File "/usr/local/bin/hellaconk.py", line 48, in <module>
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.5/optparse.py", line 1378, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1422, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.5/optparse.py", line 1529, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.5/optparse.py", line 782, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.5/optparse.py", line 802, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "/usr/local/bin/hellaconk.py", line 17, in NZB
    download = hellanzbServer.status()['currently_downloading']
  File "/usr/lib/python2.5/xmlrpclib.py", line 1147, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1437, in __request
    verbose=self.__verbose
  File "/usr/lib/python2.5/xmlrpclib.py", line 1183, in request
    self.send_content(h, request_body)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1297, in send_content
    connection.endheaders()
  File "/usr/lib/python2.5/httplib.py", line 856, in endheaders
    self._send_output()
  File "/usr/lib/python2.5/httplib.py", line 728, in _send_output
    self.send(msg)
  File "/usr/lib/python2.5/httplib.py", line 695, in send
    self.connect()
  File "/usr/lib/python2.5/httplib.py", line 663, in connect
    socket.SOCK_STREAM):
socket.gaierror: (-2, 'Name or service not known')


Third problem (and this is off-topic):  I'm new to .nzb, but I seem to be downloading a lot of bad files.  I get this in Hellanzb frequently:

> hellanzb-tmp-the_file_1971_720p_hddvd_x264-sinners.file0025 segment: 1 Article is missing!

I'm using binsearch.info and a firefox to browse my newserver.  What gives?

---

### Post by kd7swh on 2008-01-21
Problems 1 & 2 Its the same problem in both cases.

in hellanzb.conf:

```
# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'
```

is were you need to input a password.

in this case "changeme" is the password that you would put in hellaconk and hellafox.

I hope this helps.

Problem 3:

That is the fault of your news servers retention. Try a better (paid) server.

---

### Post by awangk on 2008-01-22
First post :)

The script produces a lot of errors when querying the nzb-name when hellanzb is not downloading anything.

To fix, change the NZB function to:
```

def NZB(option, opt, value, parser):
        download = hellanzbServer.status()['currently_downloading']
        if len(download) > 0:
                print download[0]['nzbName']
        else:
                print 'none'


```

---

### Post by theluddite on 2008-01-22
Thanks for the quick reply Honeydew.  I think I've tried every possible server/password/port/username combination possible and still can't get Hellaconk and Hellafox to work.  There's got to be something really obviously wrong with my settings:

In hellanzb.conf:

> defineServer(id = 'Easynews',
             hosts = [ 'news.easynews.com:8760' ],
             #hosts = [ 'news.easynews.com', 'morenews.easynews.com:8760' ],


             username = 'my_easynews_username',
             password = 'my_easynews_password',
             #username = None,           # no auth
             #password = None,


> # Hostname for the XMLRPC client to connect to. By default, localhost
Hellanzb.XMLRPC_SERVER = 'localhost'

# Port number the XML RPC server will listen on, and the client will connect to.
# Set to 'None' (without the quotes!) for no XML RPC server
Hellanzb.XMLRPC_PORT = 8760

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# [http://hellanzb:my_ubuntu_username@localhost:8760](http://hellanzb:my_ubuntu_username@localhost:8760)
Hellanzb.XMLRPC_PASSWORD = 'changeme'


In hellaconk:

> #change this next line to represent your hellanzb server info
SERVER = 'http://hellanzb:my_ubuntu_username@localhost:8760/'
username = 'hellanzb'
password = 'changeme'
hellanzbServer = xmlrpclib.ServerProxy(SERVER)

In hellafox:

> The hostname of the machine running hellanzb:  localhost
The port upon which hellanzb is listening:  8760
The password used to connect to hellanzb:  changeme


---

### Post by honeydew on 2008-01-23
theluddite Ill take a look at this a bit more tonight..  awangk thanks much.. Im very much a novice when it comes to programing.. just have done some light bash scripting for automating admin tasks.  I have also noticed the mass amounts of errors but ignored them.. thanks for fixing this!!!  Also I am trying to piece together another python script that parses a newzbin rss feed and automaticly downloads nzb files.. would you be interested in looking at what I have so far?

---

### Post by honeydew on 2008-01-23
> **theluddite said:**
> Thanks for the quick reply Honeydew.  I think I've tried every possible server/password/port/username combination possible and still can't get Hellaconk and Hellafox to work.  There's got to be something really obviously wrong with my settings:

In hellanzb.conf:





In hellaconk:



In hellafox:


try this in the terminal.. 
```
telnet localhost 8760
```

what does that give you?

---

### Post by theluddite on 2008-01-23
Here's what I tried:

> theluddite@small:~$ telnet localhost 8760
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
theluddite@small:~$ sudo telnet localhost 8760
[sudo] password for theluddite:
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
theluddite@small:~$ ping localhost 8760
PING 8760 (0.0.34.56) 56(124) bytes of data.

--- 8760 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9012ms
theluddite@small:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.027 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.018 ms

--- 127.0.0.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 0.018/0.026/0.031/0.006 ms
theluddite@small:~$ 


So you can't see any differences between my settings and yours?  
And I'm not the best guy to look at your new script, I've only just started learning perl and I don't know python at all.  Too bad I can't help a fellow Canadian eh?

---

### Post by honeydew on 2008-01-24
ey no worries.. so yah.. you not being able to telnet to that port means your server is not running your problem lies somewhere with hellanzb or your hellanzb.conf.  Are you running the latest version?

here is my config relating to the xmlrpc server...

```

# Password for the XML RPC server. You might probably never use this, but the
# command line XML RPC calls do -- it should definitely be changed from its
# default value. The XML RPC username is hardcoded as 'hellanzb' -- E.g. URL:
# http://hellanzb:changeme@localhost:8760
Hellanzb.XMLRPC_PASSWORD = 'changeme'

``` 

notice how the line with [http://hellanzb:changeme@localhost:8760](http://hellanzb:changeme@localhost:8760) is commented out?  I think you should try that as well..

---

### Post by honeydew on 2008-01-24
also do you really connect to easynews on 8760? I believe its much more likely that you are using port 119 or 80 or 443 or something...   

here is the rss-nzb downloader.. it works for a bit and then seems to die..

[http://wiki.arcintel.com/doku.php?id=feedmenzb](http://wiki.arcintel.com/doku.php?id=feedmenzb)

---

### Post by theluddite on 2008-01-24
Yeah, the port may have been part of the problem, although I'm sure I had already tried port 119 to connect to my newserver.  I took a look at the settings in this post:  [http://ubuntuforums.org/showthread.php?t=650832](http://ubuntuforums.org/showthread.php?t=650832) which really helped.  Particularly, I added these lines to my hellanzb.conf file which were absent for some reason:

> # IP address on which the XMLRPC Server will be binded to.
# Type '0.0.0.0' for any interfaces, '127.0.0.1' will disable remote access
Hellanzb.XMLRPC_SERVER_BIND = '127.0.0.1'


I think that was the problem, because I've finally got hellanzb and hellaconk working.  Attached is my screenshot.  And I'd totally be interested in adding a download bar to hellaconk.  I'll look into it, but let me know if you're able to figure it out.

Now I've just got to get hellafox working.  Finally, there's no errors when I download the nzb file, but hellanzb gives me this:

> Downloading from [http://downloads.members.easynews.com/news/f/c/2/fc215ca7ccfbebaf163d5efcee965ce605321033e.nzb/The_Machinist__2004_.nzb](http://downloads.members.easynews.com/news/f/c/2/fc215ca7ccfbebaf163d5efcee965ce605321033e.nzb/The_Machinist__2004_.nzb)..
Unable to download from [http://downloads.members.easynews.com/news/f/c/2/fc215ca7ccfbebaf163d5efcee965ce605321033e.nzb/The_Machinist__2004_.nzb:](http://downloads.members.easynews.com/news/f/c/2/fc215ca7ccfbebaf163d5efcee965ce605321033e.nzb/The_Machinist__2004_.nzb:) [Failure instance: Traceback (failure with no frames): <class 'twisted.web.error.Error'>: 401 Authorization Required
]


I've checked my username and password for the newserver in hellanzb.conf, any other ideas?

---

### Post by honeydew on 2008-01-28
hrmm.. I dont know if hellafox works with easynews I thought it was for newzbin integration.. I could be wrong though.

---

### Post by theluddite on 2008-01-28
Yeah.  I'd love to try it on Newzbin buy you need an invite now to sign-up.  Hellafox should work with Easynews too though.  From the wiki, 

 > hellafox works by placing a 'Download this NZB' entry in the right-click context menu. It will insert the context menu entry in the following situations:
    *  When right clicking anywhere on the page, when the current page is a post report page on the site, Newzbin.
    * When right clicking on a link to a Newzbin post report page.
    * When right clicking on a NZB download link in the ZipManager on Usenet service provider EasyNews...
    * When right clicking on any link to a file ending in ".nzb". 

It'd be great if someone could let me know if they were able to get this firefox add-on working outside of Newsbin -- and how.

---

### Post by theluddite on 2008-01-30
Or someone that can give a kindred linux user an invite to Newzbin...:wink:  Anyone?...  Anyone?...  Bueller?...

---

### Post by honeydew on 2008-01-30
> **theluddite said:**
> Or someone that can give a kindred linux user an invite to Newzbin...:wink:  Anyone?...  Anyone?...  Bueller?...

pm me with your email.. kindered cannuck =]

---

### Post by theluddite on 2008-02-01
Yup.  Hellafox works perfectly with Newzbin.  Thanks again for your help!:D

---

### Post by phoenixnr on 2008-02-12
Can anyione post this script? site is down ;(

---

### Post by honeydew on 2008-02-13
> **phoenixnr said:**
> Can anyione post this script? site is down ;(

hrmm the site is running off a really old laptop(400mhz 64mb of ram) in utah(on the other side of the universe).  I have a backup around here somewhere I will work on restoring everything this week..  


INSTALL:
```
place this in your executables directory(mine is /usr/local/bin) and set 
it as executable (chmod +x). Also I think I should mention you need to 
change the SERVER = "" to the information that matches the ip of your 
hellanzb server and the same user/password that is in your hellanzb.conf

enjoy!
```

hellaconk.py
```
#!/usr/bin/python

# writen by Austin Trask
# contact austin@arcintel.com
# visit http://wiki.arcintel.com for more info

import xmlrpclib
import optparse

#change this next line to represent your hellanzb server info
SERVER = 'http://hellanzb:changeme@192.168.1.33:8760/'
hellanzbServer = xmlrpclib.ServerProxy(SERVER)

def NZB(option, opt, value, parser):
        download = hellanzbServer.status()['currently_downloading']
        print download[0]['nzbName']

def rate(option, opt, value, parser):
        rate = int(hellanzbServer.status()['rate'])
        print rate

def percentage(option, opt, value, parse):
        percent = hellanzbServer.status()['percent_complete']
        print percent


def ETA(option, opt, value, parse):
        eta = hellanzbServer.status()['eta']
        hours = (eta/3600)
        minutes = (eta/60)%60
        seconds = (eta%60)
        time_left = "%02d:%02d:%02d" % (hours, minutes, seconds)
        print time_left


parser = optparse.OptionParser()
parser.add_option("-n", "--nzb", action="callback", callback=NZB,
                  help="output current NZB")
parser.add_option("-r", "--rate", action="callback", callback=rate,
                  help="output hellanzb rate")
parser.add_option("-p", "--percent", action="callback", callback=percentage,
                  help="output completion percentage of current NZB")
parser.add_option("-e", "--eta", action="callback", callback=ETA,
                  help="displays the ETA of the current NZB")

(options, args) = parser.parse_args()

```

hope this helps..

---

### Post by phoenixnr on 2008-02-13
Thanks! Script Rocks!

---

### Post by VincentKriek on 2008-02-14
I want the script too, but the site is still down.

// didnt read far enough

*shame

---

### Post by honeydew on 2008-02-15
still working on it.. I actually just picked up some really rad boards to replace the laptop that was hosting the website..  Im just working out some kinks =]  
Ive got 2 of these guys
[http://www.mini-box.com/Jetway-Versa-J7F4K1G2E-Fanless?sc=8&category=99](http://www.mini-box.com/Jetway-Versa-J7F4K1G2E-Fanless?sc=8&category=99)

and they will be load balancing web connections with under 60w =]

should be up by the end of the weekend.  Also there are a few bug fixes in the script that have not been committed so stay tunned =]

---

### Post by marscay on 2008-03-08
any update m8, this script looks hella nice (ha).

---

### Post by doubledouce on 2008-03-14
Hi!

This script is a great idea, but I can't seem to get it to work... :(

When I try to run conky I get:

$ conky
Conky: desktop window (1a6) is root window
Conky: window type - normal
Conky: drawing to created window (1800001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/usr/bin/hellaconk.py", line 12, in <module>
    hellanzbServer = xmlrpclib.ServerProxy(SERVER)
  File "/usr/lib/python2.5/xmlrpclib.py", line 1411, in __init__
    raise IOError, "unsupported XML-RPC protocol"
IOError: unsupported XML-RPC protocol


There's something wrong with the sentence:

hellanzbServer = xmlrpclib.ServerProxy(SERVER)

in hellaconk.py, but I don't know what to do. Anyone?

----------------------------------------------------------------------------------------------------
Edit: YES! I finally got it fixed. Changed localhost to the host name of my computer.
Thought I'd done that already, but it seems i didn't.

Off to fine tune the setup in conky. :D

---

### Post by honeydew on 2008-03-18
mm good to hear... I need to get around to adding a few fixes for this script..   (needs to find a ballance of ganj and scripting  ;) )

---

### Post by thecount on 2008-04-15
When there's unicode in the nzb name the script pukes out:
Traceback (most recent call last):
  File "/usr/bin/hellaconk.py", line 46, in ?
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.4/optparse.py", line 1277, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.4/optparse.py", line 1321, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.4/optparse.py", line 1428, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.4/optparse.py", line 709, in process
    return self.take_action(
  File "/usr/lib/python2.4/optparse.py", line 728, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "/usr/bin/hellaconk.py", line 16, in NZB
    print download[0]['nzbName'] 
UnicodeEncodeError: 'ascii' codec can't encode characters in position 8-9: ordinal not in range(128)

Any ideas?

---

### Post by thecount on 2008-04-15
changing this:
print download[0]['nzbName']
to this:
print download[0]['nzbName'].encode('ascii', 'ignore')
Does the trick.

---

### Post by honeydew on 2008-04-15
I justed updated the script.. with the bug fixes suggested in the discussion.. thanks for the help guys!

---

### Post by doubledouce on 2008-04-26
> **honeydew said:**
> mm good to hear... I need to get around to adding a few fixes for this script..   (needs to find a ballance of ganj and scripting  ;) )

Ah, the balance. ;)

Anyways, My conkyrc got deleted and now I can't remember how the text for hellaconk was set up in it. I had the name of the file, % and ETA. Can you post it? The wiki seems to be offline.

EDIT: Nwm, I found it. :)

---

### Post by phoenixnr on 2008-05-17
Any progress on this? Conky is causing crash reports under hardy. Popups every 5 seconds a re highly annoying....

---

### Post by honeydew on 2008-05-17
crazy... havnt used conky under hardy yet..but Ill give it a go.  I just have to find my server drive with the wiki on it..

---

### Post by Scruffynerf on 2008-05-18
I've got conky working fine with Hardy. Make sure that you install the dependencies - like curl.

---

### Post by phoenixnr on 2008-05-22
> **thecount said:**
> changing this:
print download[0]['nzbName']
to this:
print download[0]['nzbName'].encode('ascii', 'ignore')
Does the trick.

My crashes are related to this and the post above does not solve the error for me. Any suggestions?

---

### Post by honeydew on 2008-05-23
what is the popup error that you are receiving?

---

### Post by phoenixnr on 2008-05-25
When there is no active nzb's i get "This problem report does not apply to a packaged program." As conky sees it as an error.

---

### Post by honeydew on 2008-05-26
o right.. I think someone wrote some code that fixes this issue.. if you scan back in this thread you may find the fix.  I havnt been able to put any time towards this.. and my drive with my wiki on it has gone missing =/

---

### Post by phoenixnr on 2008-06-08
What commands go in the conky config file again? Fresh install and forgot to copy it over. :)

---

### Post by phoenixnr on 2008-06-08
Never mind.. got it. In case anyone else needs it. 

HELLA:
${execi 10 hellaconk.py -n}    
Speed: ${execi 10 hellaconk.py -r} k/s  
Percent Done: ${execi 10 hellaconk.py -p}%  
ETA:${execi 10 hellaconk.py -e}

---

### Post by kebes on 2008-06-11
The script works great on Kubuntu 8.04 (Hardy Heron).

Thanks so much for this useful script!

---

### Post by doubledouce on 2008-11-29
Ok, I changed my Usenet news host and now I get these errors when starting conky:

Traceback (most recent call last):
  File "/usr/bin/hellaconk.py", line 53, in <module>
    (options, args) = parser.parse_args()
  File "/usr/lib/python2.6/optparse.py", line 1378, in parse_args
    stop = self._process_args(largs, rargs, values)
  File "/usr/lib/python2.6/optparse.py", line 1422, in _process_args
    self._process_short_opts(rargs, values)
  File "/usr/lib/python2.6/optparse.py", line 1529, in _process_short_opts
    option.process(opt, value, values, self)
  File "/usr/lib/python2.6/optparse.py", line 782, in process
    self.action, self.dest, opt, value, values, parser)
  File "/usr/lib/python2.6/optparse.py", line 802, in take_action
    self.callback(self, opt, value, parser, *args, **kwargs)
  File "/usr/bin/hellaconk.py", line 15, in NZB
    download = hellanzbServer.status()['currently_downloading']
  File "/usr/lib/python2.6/xmlrpclib.py", line 1199, in __call__
    return self.__send(self.__name, args)
  File "/usr/lib/python2.6/xmlrpclib.py", line 1489, in __request
    verbose=self.__verbose
  File "/usr/lib/python2.6/xmlrpclib.py", line 1235, in request
    self.send_content(h, request_body)
  File "/usr/lib/python2.6/xmlrpclib.py", line 1349, in send_content
    connection.endheaders()
  File "/usr/lib/python2.6/httplib.py", line 868, in endheaders
    self._send_output()
  File "/usr/lib/python2.6/httplib.py", line 740, in _send_output
    self.send(msg)
  File "/usr/lib/python2.6/httplib.py", line 699, in send
    self.connect()
  File "/usr/lib/python2.6/httplib.py", line 683, in connect
    self.timeout)
  File "/usr/lib/python2.6/socket.py", line 498, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
socket.gaierror: [Errno -2] Name or service not known


Hmm... The only thing I've changed is the one line in hellanzb.conf where I put in my news host server. Why did this break hellaconk? Is it possible that my new host doesn't support the xmlrpclib.ServerProxy-thingy or something?

I hope someone can help me cause I've gotten very used to this amazing script. :)

Edit: Figured it out. Had to change the server info in hellaconk back to changeme@localhost
Ahh, great to have it working again! :)

---

### Post by jakeman66 on 2009-01-07
Anyway to get the script to show how many or what is in the queue?

---

### Post by kebes on 2009-01-07
> **jakeman66 said:**
> Anyway to get the script to show how many or what is in the queue?

If you invoke the hell.py script with the "-n" argument, it will return the name of the currently downloading file:
```
./hell.py -n
```

If you want to get the names for other things in the queue, you can adjust the script accordingly. The hellanzbServer.status() call returns an associative array with (among many other things) a 'queued' list.

Below is a slightly modified version of the script:

```

#!/usr/bin/python

# writen by Austin Trask
# contact austin@arcintel.com
# visit http://wiki.arcintel.com for more info

import xmlrpclib
import optparse

#change this next line to represent your hellanzb server info
SERVER = 'http://hellanzb:Xeitie2o@localhost:8760/'
hellanzbServer = xmlrpclib.ServerProxy(SERVER)

def NZB(option, opt, value, parser):
        download = hellanzbServer.status()['currently_downloading']
	if( len(download)>0):
       		print download[0]['nzbName'].encode('ascii', 'ignore')
	else:
		print 'None'

def rate(option, opt, value, parser):
        rate = int(hellanzbServer.status()['rate'])
        print rate

def percentage(option, opt, value, parse):
        percent = hellanzbServer.status()['percent_complete']
        print percent


def ETA(option, opt, value, parse):
        eta = hellanzbServer.status()['eta']
        hours = (eta/3600)
        minutes = (eta/60)%60
        seconds = (eta%60)
        time_left = "%02d:%02d:%02d" % (hours, minutes, seconds)
        print time_left


parser = optparse.OptionParser()
parser.add_option("-n", "--nzb", action="callback", callback=NZB,
                  help="output current NZB")
parser.add_option("-r", "--rate", action="callback", callback=rate,
                  help="output hellanzb rate")
parser.add_option("-p", "--percent", action="callback", callback=percentage,
                  help="output completion percentage of current NZB")
parser.add_option("-e", "--eta", action="callback", callback=ETA,
                  help="displays the ETA of the current NZB")




#[B] New function definitions added by ubuntuforums user "kebes"
# to allow for query of the queue:
def NZBNext(option, opt, value, parser):
        queued = hellanzbServer.status()['queued']
        if( len(queued)>0):
                print queued[0]['nzbName'].encode('ascii', 'ignore')
        else:
                print 'None'

def QueueLength(option, opt, value, parser):
        queued = hellanzbServer.status()['queued']
        print len(queued)

def ListQueued(option, opt, value, parser):
        queued = hellanzbServer.status()['queued']
        if( len(queued)>0):
                for item in queued:
                    print item['nzbName'].encode('ascii', 'ignore')
        else:
                print 'None'



parser.add_option("-N", "--next", action="callback", callback=NZBNext,
                  help="output next NZB")
parser.add_option("-l", "--length", action="callback", callback=QueueLength,
                  help="output queue length")
parser.add_option("-q", "--list", action="callback", callback=ListQueued,
                  help="output all items in queue")[/B]




(options, args) = parser.parse_args()

```

With this version of the script, you can use "./hell.py -N" to get the name of the next item in the queue, "./hell.py -l" to get the length of the queue, and "./hell.py -q" to list everything in the queue (all this excludes the currently downloading item). Other variants of querying the queue can be easily accomplished with similar modifications to the python code.

Hope that helps.

---

### Post by jakeman66 on 2009-01-07
I'll give that a shot with my Conky setup tomorrow..  Something to play with.  Thanks Mate.

---

### Post by jakeman66 on 2009-01-08
Kebes,

Your the cat's meow..  your script mod works like a champ..  Thanks.

---

### Post by nhasian on 2009-05-13
i just installed conky today with the hellanzb integration.  one small issue, when it displays the current file downloading or a queued item with a long filename conky stretches out to half my desktop!  How can I tell it to show only the first 20 characters? or restrict the size it takes somehow?  here's what i have in my .conkyrc now:

```
HELLA:
${execi 10 ~/scripts/hella.py -n}
Speed: ${execi 10 ~/scripts/hella.py -r} k/s
Percent Done: ${execi 10 ~/scripts/hella.py -p}%
ETA:${execi 10 ~/scripts/hella.py -e}
Queued: ${execi 10 ~/scripts/hella.py -q}
```

---

