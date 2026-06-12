---
title: "How to convert base64 email attachment to jpg?"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by bustard on 2011-12-30
I receive a lot of emails from my Christmas gift of a wireless webcam, each one containing a jpeg attachment. When I look at the attachment as a text file, it begins:

```

--===Message_0123456789
Content-Type: text/plain; charset=us-ascii

Camera Name : DCS-932L
IP Address : 192.168.0.196
Time : 2011-12-30 07:24:36

--===Message_0123456789
Content-Type: image/jpeg; name="20111230_072436_00.jpg"
Content-Transfer-Encoding: base64

/9j/xAFeAAACAwEBAQEBAAAAAAAAAAAAAQIDBAUGBwgJEAACAQIEBAMEBwUEBgEAAFcBAgMAEQQS
ITETQVFhBSIyFHGBkRUjQlJiobEGM3LB0SRDU4IWNJKi4fHwBwgXGCUmJyg1Njc4REVGR0hUVVZX
WGNkZWZnaHN0dXZ3eIOEhYaHiJOUlZaXmKOkpaanqLKztLW2t7jCw8TFxsfI0tPU1dbX2OLj5OXm
5+jy8/T19vf4AQEBAQEBAQEBAQEAAAAAAAAAAQIDBAUGBwgJEQACAQIEBAMEBwUEBgEAAFcAAREC
IQMSMUETIlFhBDJxBRQjQjNSgZGhsfAGFcHR4SRDYvEWJTRTcoKSBwgXGCYnKDU2NzhERUZHSFRV

```I'm guessing the part I am interested in begins with

Content-Type: image/jpeg;


but if I save the part beginning with that, or beginning with anything else, it is not recognized as a .jpg file.

I tried running the imagemagick convert command, but no .jpg emerges from it.

I used to know a simple windows command to do this, which I have long forgotten, and assume there is an equally simple linux command, but it is not apparent in the bing.com searches I have done, or in searches here.

Anybody know the solution?  Thanks

---

### Post by Paqman on 2011-12-30
> **bustard said:**
> When I look at the attachment as a text file

Is there some reason you're doing this? Surely all you want to do is view the image? Just open it with an image viewer.

---

### Post by Frogs Hair on 2011-12-30
There are some base 64 decoders available . Here is one of many results . [http://userlogos.org/node/4678](http://userlogos.org/node/4678)

---

### Post by bustard on 2011-12-30
> **Paqman said:**
> Is there some reason you're doing this? Surely all you want to do is view the image?That is not all I want to do.

---

### Post by Paqman on 2011-12-30
> **bustard said:**
> That is not all I want to do.

Can you be a little more specific? What are you doing? Steganography?

---

### Post by bustard on 2011-12-30
> **Frogs Hair said:**
> There are some base 64 decoders available . Here is one of many results . [http://userlogos.org/node/4678](http://userlogos.org/node/4678)Thank you, that worked, running under Wine I guess (at least I have Wine installed).

I was able to call it from a python script, so it will be possible to feed it each stripped-down attachment and write out the resulting .jpg.

Your phrase 'base64 decoder' made me run to the repository and I found something called uudeview. Since that is native linux, I'll try it out, but if it doesn't work, your program will do nicely. Thanks again.

---

