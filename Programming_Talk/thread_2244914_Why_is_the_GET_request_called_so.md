---
title: "Why is the GET request called so?"
date: 2014-09-19
forum: Programming Talk
---

### Post by IAMTubby on 2014-09-19
Hello,
 As per my understanding, both GET and POST are used for sending data from client(browser) to the server which may be a cgi form or a php backend or a servlet etc. I understand the difference between GET and POST is that you can see the parameters in the URL in a GET request, whereas, in case of POST, the parameters are in the body.

_However, my question is, why is the GET request called so, when we are not getting, but sending data from the client to the server?_ The word GET confuses me, as I begin pondering over whether GET is used to send data from the server to the client.

Thanks.

---

### Post by Lars Noodén on 2014-09-19
There are more [HTTP methods](http://tools.ietf.org/html/rfc7231#section-4.3) than just GET or POST.  But with GET, your client is requesting to *get* what ever resource is at the end of the URL it is sending.  So any data sent do the server is encoded in the requested URL.  Nothing is actually sent aside for a request for a resource, it's just that the URL itself can be parsed for data.  

If you are using HTTP and not HTTPS you can use Wireshark or raw Tcpdump to watch the request and response and see what is actually sent back and forth between the client and the server.

---

### Post by slickymaster on 2014-09-19
Because the GET method retrieves whatever information is identified by the Request-URI.

See [RFC 2616]("http://tools.ietf.org/html/rfc2616.html")

---

### Post by IAMTubby on 2014-09-19
Thanks Lars Noodén for the reply.

> **Lars Noodén said:**
> But with GET, your client is requesting to *get* what ever resource is at the end of the URL it is sending.  So any data sent do the server is encoded in the requested URL.
Hmm, I'm trying to spend some thinking on the above reply. But what would you say about POST then? Even in POST, aren't we requesting to ***get*** what ever resource is **in the message body**?

> 
If you are using HTTP and not HTTPS you can use Wireshark or raw Tcpdump to watch the request and response and see what is actually sent back and forth between the client and the server.
Okay, in the meanwhile, let me try spending some time on these.

---

### Post by Lars Noodén on 2014-09-19
If you look at POST vs GET,

```

sudo tcpdump -i eth0 -lA 'host ubuntuforums.org' | less

```

You'll see that the POST sends data separately from the headers.  With GET, if there is any data, it must be passed encoded inside the URL.  So POST is actually posting information, GET is just asking for a particular URL.

---

### Post by tdawgf on 2014-09-19
There are several different HTTP Verbs.

With Rest API's POST is used when the client needs to create data in the system. A simple example would be when a user creates a new account on a website or service. They enter their information in a form and that information then uses a POST request to create the information.

GET is when a user is usually used when a person wants to retrieve information/data from a specific known source.

A PUT is commonly used by a lot of web developers to update information, but this is actually incorrect. Both POST and PUT are similar however a PUT is supposed to be used to send the request to a known location (I know this might be confusing at first but there are some great articles out there for more information).

A DELETE is used to delete (or remove access) to a given resource.

These are probably the most common HTTP verbs, but there are more. I have found, however, that they are rarely used as intended (especially PUT).

I hope this answers your question.

---

