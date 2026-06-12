---
title: "Making a GUI to call on specific CSS entries. How to get started?"
date: 2012-08-26
forum: Programming Talk
---

### Post by Roasted on 2012-08-26
I have been using "Motion" for a while now for my video surveillance needs. To say it's bombproof and headache free is an absolute understatement. One thing I've been striving for is a way to view multiple mjpg streams on a single web page so I can monitor many cameras at once. Using some light HTML/CSS I accomplished that. My buddy planted the idea, what if you could rig up a GUI to input the IP/ports/scaling for you?

This got me wondering, how on earth do I get started? Am I in over my head? 

Basically the code I'm looking at is this:

```
<!DOCTYPE html>
<html>
	<head>
                <style type="text/css">
		body { text-align:center }
                .container {
                        background: #000000;
			width:100%;
                }
                .motion {
                        border: 0;
			text-align:center;
                        width: 25%;
                        height: auto;
                }
		.clear {
			clear:both;
		}
                </style>
	</head>
	<body>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<br />
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<br />
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
<a href="http://192.168.1.15:8081"><img class="motion" src="http://192.168.1.15:8081" /></a>
	</body>
</html>
```

Really all that would be needed is a way to adjust the IP address, the port used, and the "width" parameter higher up. I can't see a need for anything else, as the goal would be for super easy and simple changes. This layout here currently works great for me, but I also added in the IP addresses and whatnot manually. Sure, easy enough to do it manually, but if it can be altered a bit to be a bit easier for some users out there, we'd have a winner.

Any/all insight would be greatly appreciated!

---

### Post by conradin on 2012-08-26
NOt really sure, but here are some ideas.
if you had a list of cams available, and some (max) number of slots for those cam spaces. Possibly a default cam to load as well. I think you could do it with image frames. qt or gambas would be were I would go for rapid GUI development. I dont know what you think about such things. 
use the image frames as references to the urls of you cams and reload the images frequently. IDK, maybe QT or gambas has a streaming cam option already in there. Im not realy sure if your going for something like automation of which cams to stream.. infact, if you have a site that does it already, im not really sure why you would want a wrapper. You could write a browser for your streaming page just as easily, and have it act more like an application, though still be a webpage, or series of webpages. 

Can you post a pic of what you want this thing to look like / what it already looks like?

---

### Post by Roasted on 2012-08-26
I'm not really sure I know of a working example to be honest. Likewise, the only IP address that matters is the server itself. So if my server is 192.168.1.15, that's the IP that'll be populated in each box. The real key is the server IP + port... ports dictate which camera you're seeing.

I'm curious about seeing an actual text user box, entitled "Server IP". The user puts in their server IP. Let's say it's 172.19.180.10. Once they hit submit, that IP replaces every instance of the 192.168.1.15 you see above in my original example. On top of that, the user will have buttons available for adding port numbers for camera 1, camera 2, etc. So they can type in:

Camera 1 - <8081>
Camera 2 - <8082>
Camera 3 - <8083>
(with the < > areas being what the user can type)

Once done, it'll plug in the port with the server IP, so you'd see the following:

<a href="http://172.19.180.18:8081"><img class="motion" src="http://172.19.180.10:8081" /></a>
<a href="http://172.19.180.18:8082"><img class="motion" src="http://172.19.180.10:8082" /></a>
<a href="http://172.19.180.18:8083"><img class="motion" src="http://172.19.180.10:8083" /></a>


See what I'm getting at? It's a matter of a handful of additional features and text boxes. User sees "Server IP" box, along with text boxes for Camera 1, Camera 2, etc - plug in server IP, ports to cameras, bingo bango - done.

---

