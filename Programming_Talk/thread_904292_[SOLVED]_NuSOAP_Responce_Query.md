---
title: "[SOLVED] NuSOAP Responce Query"
date: 2008-08-29
forum: Programming Talk
---

### Post by s.fox on 2008-08-29
Hi Everybody,

I have been working on SOAP using a PHP package called NuSOAP. Unfortunately I have not been very successful. Currently I can receive a POST from another server and save the XML file but as it is an HTTP POST from the sending server an HTTP 500 error is sent back as the response from the receiving server.

Basically, I need to send back a HTTP 200 Success response on receiving a POST.

I was wondering whether you might have any ideas as to what I might be doing wrong.

Here is the code that I am using:

	```

        require_once('lib/nusoap.php');
	$server = new soap_server;
	$server->register('hello');
	$message = 'Success ';
	$postSuccess = $server->fault('HTTP 200','',$message, "Successful Post");
	$HTTP_RAW_POST_DATA = isset($HTTP_RAW_POST_DATA) ? $HTTP_RAW_POST_DATA : '';
	$server->service($HTTP_RAW_POST_DATA);
```

What would be the best way to handle HTTP POST and sending a RESPONSE back to the originating server?

If anybody can help me sort the response out I would be very grateful. If any more detail is needed please say.

-Ash

---

### Post by s.fox on 2008-09-01
Ok,  I managed to get it to work.  Hooray for echo!  Its usually the simplest thing!:lolflag:

---

### Post by Starl1n on 2010-05-27
Hello, i know this is a kind of old post , but i have created one webservice server with nusoap i can consume it very well by WSDL, but when i try to consume it by HTTP POST request i got the same message, error 500.

So i figured it out that you have made it, could you please be a little more specific with this issue? thanks before all.

---

