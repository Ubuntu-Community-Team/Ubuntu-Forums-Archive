---
title: "easiest way to cp files 'tween two Lubuntus that share the same router/house"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by innn on 2013-07-03
hi,
I've tried samba and it works but had this major annoyance that starting to copy a 2 GB large directory it told me will do it in 40 minutes. 
I declined and came here looking for a friendly how-to that works and is decent speedwise.

---

### Post by Morbius1 on 2013-07-03
If this is just a one-off type of thing here's something easy enough to try and undo if it doesn't work:

Open a terminal and cd to the directory containing the file you want the other machine to copy. For example, If I have a large file in my Documents folder then in a terminal:
```
cd Documents
```
Then run the following command:
```
python -m SimpleHTTPServer 
```
Now on the client machine open up your Web Browser and enter:
```
http://192.168.0.100:8000
```
[COLOR=#0000cd]*Where 192.168.0.100 is the ip address of the machine with the file to be copied.*[/COLOR]

It should list the contents of the directory so you could then right click the file and use the "save link as" function.

If it works then undo the temporary http server you created by running: Ctrl+C

---

### Post by innn on 2013-07-03
yesss
it works, why would I need a samba construction just for this
I thank you greatly.

---

### Post by kurja on 2014-03-17
> **Morbius1 said:**
> If this is just a one-off type of thing here's something easy enough to try and undo if it doesn't work:
```
python -m SimpleHTTPServer 
```
Now on the client machine open up your Web Browser and enter:
```
http://192.168.0.100:8000
```
[COLOR=#0000cd]*Where 192.168.0.100 is the ip address of the machine with the file to be copied.*[/COLOR]

It should list the contents of the directory so you could then right click the file and use the "save link as" function.

If it works then undo the temporary http server you created by running: Ctrl+C

Can this be used to make files accessible to outside of lan?

---

### Post by Easy Limits on 2014-03-18
Try Dukto.

[https://code.google.com/p/dukto/](https://code.google.com/p/dukto/)

---

### Post by Morbius1 on 2014-03-19
> **kurja said:**
> Can this be used to make files accessible to outside of lan?
It probably could but I wouldn't do it - and in fact I never used it that way.

This isn't a full fledged HTTP server with all the security mechanisms in place that make it safe. This is for when you absolutely positively have to get a file from A to B in your own network.

---

### Post by kurja on 2014-03-19
Yes I realize that security would be a big issue, but seems like a super convenient way to temporarily share a folder to someone outside of lan. I tried it but it didn't work 'out of the box', maybe I'll need to forward that port on my router/nat.

---

### Post by Vladlenin5000 on 2014-03-19
> **kurja said:**
> Yes I realize that security would be a big issue, but seems like a super convenient way to temporarily share a folder to someone outside of lan. I tried it but it didn't work 'out of the box', maybe I'll need to forward that port on my router/nat.

You need to do that indeed and I hope you're aware of the security issue already discussed above. That said, when accessing from outside your LAN you'll be using your public IP, the one given by your ISP (or you can use some DDNS).

---

### Post by gifford on 2014-03-19
We use NitroShare on our LAN. Works great.

---

### Post by kurja on 2014-03-19
> **Vladlenin5000 said:**
> You need to do that indeed and I hope you're aware of the security issue already discussed above. That said, when accessing from outside your LAN you'll be using your public IP, the one given by your ISP (or you can use some DDNS).

Those 'security issues' just got even better as I discovered that port forwarding alone won't cut it - my zyxel router's firewall also needs to be disabled, there's no configuring an exception to it as the firewall settings consist of an on/off button :roll:

---

### Post by HermanAB on 2014-03-19
Howdy,

Here is a fun way using netcat.

On the destination machine:
$ nc -l 1234 > filename

On the source machine:
$ nc destinationipaddress 1234 < filename

---

### Post by gabmuks on 2014-09-21
> **Easy Limits said:**
> Try Dukto.

[https://code.google.com/p/dukto/](https://code.google.com/p/dukto/)


THANKS MUCH!!!!


That was so easy!

 Installed Dukto R6 on both computers and in a about 5 minutes
all of my files including lots of photos went from Desktop to Laptop!!!


Amazing!!!!

Am now taking this old 2003 Desktop off line for good.
Already have a replacement.

---

### Post by eightbits2010 on 2015-03-30
I don't want to use samba or the HTTP type server. Looking at a couple of youtube videos they seem based on modifying the  Ethernet drop down box from the top line. Using the
'edit connections'. However, I don't understand why the settings are made and which PC do I change or both? I am looking for an example(s) of how to set up both machines and then use the connection(s). 
Are there any examples/tutorials that are that complete and take you step by step?
So, how does one fill in the edit connections starting with the add button on that drop down ? As anyone can see, I am clueless at this point. I spent several hours just sneaker net copy of just the the music directory :mad:

I guess a real kludge might me to copy directories/files to an external HD and then transfer that way. But that is just a way to get the 'new' machine with files from the
old machine.

I do recall that sometime before this was set up at the company I was working at, but most of that was set up by the IT dept. And, that was quite a long time ago.
Thanks for any suggestions ;)

---

