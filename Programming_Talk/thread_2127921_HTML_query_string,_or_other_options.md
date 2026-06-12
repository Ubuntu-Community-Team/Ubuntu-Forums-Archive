---
title: "HTML query string, or other options"
date: 2013-03-21
forum: Programming Talk
---

### Post by Grenage on 2013-03-21
Greetings,

I rarely need to code, but when I do, it's generally bash scripts and some C.  In this instance, my task involves a web page-based solution - of which I have little experience.  The page basically needs to have two fields and a submit button; the purpose is sending SMS messages.  HTTP GET is used to send a query string to the server, which then sends the message.  It has to be GET, which is where I am stuck - here is an example string:

```
http://192.168.50.15:81/sendmsg?user=USER&passwd=PASSWORD&cat=1&to=77665455037&text=hi there
```

Observe the space at the end, I know that URLs shouldn't have spaces, but the bloody unit takes the strings literally, so resulting SMS messages have a "+" between every word.  I could get around this if I was able to use POST, but I cannot.  Can anyone suggest a route to take where I can construct a URL based on form data *and* utilise spaces?

---

### Post by lykwydchykyn on 2013-03-21
Is url encoding the string not an option?  I don't think spaces will work in HTTP URLS.  %20 would be a space in URL encoding, try that.

---

### Post by Grenage on 2013-03-21
Hi there, and thanks for your reply.

I considered that, but I'm not sure how to convert spaces to %20 when the form is submitted.

---

### Post by lykwydchykyn on 2013-03-21
What's handling the form submission?  Typically form data is automatically URL encoded.

---

### Post by Grenage on 2013-03-21
I'm just using a basic form:

```
<form action='http://192.168.50.15:81/sendmsg' method='get'>
  <input type='hidden' name='user' value='user' />
  <input type='hidden' name='passwd' value='password' />
  <input type='hidden' name='cat' value='1' />
  <div>
    SMS Number:
    <input type='text' name='to' />
  </div>
  <div>
    Message:
    <input type='text' name='text' maxlength="160" />
  </div>
  <input type='submit' />
</form
```

I'm very novice at HTML work, so forgive me if I've missed anything obvious here.

---

### Post by conradin on 2013-03-21
In a similar situation Grenage, I have used macros to get the job done. Like Imacros, which can be called from bash as scripts. 

I am confused however, is using the website mandatory?  I guess it is if you want other web users sending you sms.
Can you just send data to the server directly using curl, wput, expect, or wget --post-file=filetoSend URL
(I try to stick with expect or  wget as much as possible, they are very handy)

lykwydchykyn is sysing that
[http://192.168.50.15:81/sendmsg?user=USER&passwd=PASSWORD&cat=1&to=77665455037&text=hi](http://192.168.50.15:81/sendmsg?user=USER&passwd=PASSWORD&cat=1&to=77665455037&text=hi) there
should look like [http://192.168.50.15:81/sendmsg?user=USER&passwd=PASSWORD&cat=1&to=77665455037&text=hi%20there](http://192.168.50.15:81/sendmsg?user=USER&passwd=PASSWORD&cat=1&to=77665455037&text=hi%20there)

in your bash script, you could call firefox to load your webform, and get the perk of having firefox handle the encoding. 

I am a a little confused about the scope of this project... who is using the web form?

---

### Post by lykwydchykyn on 2013-03-21
I see, you're submitting directly to the service, which leaves it up to the browser to url encode the form.  You could do a submit using javascript and url encode the data before submission, or submit to an intermediate webserver that could process the submission.

---

### Post by Grenage on 2013-03-21
Hi again, and thank you both for your input.

This is basically going to be used by multiple users across multiple operating systems, and we're after a lightweight method of sending SMS messages manually.  I wrote a C app which handles automated messages via TCP (the unit has both a TCP and HTTP API), but that just sits on a debian nagios box and does its thing.  I am entirely open to suggestions on doing this another way, as long as it's reasonably lightweight and will work across OSs.  Enter the phone number, type a quick message, click to send.

I'll have a look into Javascript (something else I've not had to touch before), and see what I can do there; I was basically going mad with the HTTP forms, and wondering if I was missing something that others took for granted.  At least it makes the day interesting! ;)

---

### Post by lykwydchykyn on 2013-03-21
I think the easiest thing would be to write a little PHP or Perl script that properly formats your form submission for the C app, and have your HTML form submit to that. I'm not clear on why you can't do POST submissions if you have control of the C code.

---

### Post by Grenage on 2013-03-21
The device itself won't accept POST submissions, and the C app I wrote merely processes a CVS export and sends it to the device on its TCP API; the C code itself isn't the recipient - the device is a multimodem iSMS server.  We don't maintain any production webservers interally, so I was hoping that I could use a basic page that runs on the client.  The Javascript option you mentioned is probably going to be my first port of call, otherwise I could try and write an app that receives submissions and forwards it on.

As you can probably tell, coding is not my normal remit. ;)

---

### Post by lykwydchykyn on 2013-03-21
Yeah, if the HTML isn't behaving, and you aren't running a web service, then javascript is your only recourse as far as I can see.

---

### Post by Grenage on 2013-03-21
Thanks a lot for your advice, it's much appreciated. :)

---

### Post by r-senior on 2013-03-22
Does it matter that this is all very insecure?

---

### Post by Grenage on 2013-03-22
Not in this particular scenario, no. ;)

---

### Post by Grenage on 2013-03-22
Just to say cheers again.  I recalled that we have a Hylafax server with an Avantfax front-end; I used it for the PHP processing, and got it sorted quite sharpish.

---

### Post by dazman19 on 2013-03-26
Yeh probably use encodeURIComponent().

buf+=encodeURIComponent(name)+'='+encodeURIComponent(value)+'&';

---

