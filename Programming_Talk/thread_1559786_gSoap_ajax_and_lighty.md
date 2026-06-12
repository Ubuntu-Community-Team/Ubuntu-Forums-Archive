---
title: "gSoap ajax and lighty"
date: 2010-08-24
forum: Programming Talk
---

### Post by vikas.sood on 2010-08-24
OK!! I am writting a simple web service using gSoap. Its meant to respond to ajax requests coming from a web based application. To test the web service i wrote a simplest java script to send ajax requests using yahoo's yui. (checked out some HOW TO's of yui). I am a c++ developer and i do not fully understand web related stuff. So a little help can save me ;)

javascript.
```

function ajaxRequest()
{
    alert("request method called");
    var callback = { success:functionSuccess, failure:functionFailure }
    var newRequest = YAHOO.util.Connect.asyncRequest("POST", ‘/soap.ajax’, callback);
}
function functionSuccess()
{
    alert("SUCCESS");
}
function functionFailure()
{
    alert("FAILURE");
}

```I call the script from an html page.

```

<html>
<head>
<title>Simple Ajax Request</title>
</head>
<body>
<script type=”text/javascript” src=”yui/yahoo.js”></script>
<script type=”text/javascript” src=”yui/event.js”></script>
<script type=”text/javascript” src=”yui/connection.js”></script>
<script type="text/javascript" src="scripts/soap-test-ajax.js" language="javascript"></script>

<h1>Simple Example of creating Ajax Request</h1>

<input name="name" id="name" />
<input value="Soap Test" type="button" onclick="ajaxRequest()" />

<div id="container">Result:
<div id="result">
</div>
<div id="soap">
</div>
</div>
</html>

```The html page is hosted using lighttpd running on port 80.
My web service awaits soap requests on port 8080.

1. web service fails to receive any request. I think i am missing out on something. What could it be?
2. How does lighttpd handles ajax request? And how will it know what to do with it? Will there be some configuration for the web servers? Like i said i do not fully understand web related stuff.
3. var newRequest = YAHOO.util.Connect.asyncRequest("POST", ‘/soap.ajax’,  callback);
This line from the java script above. what does it do for an asynchronous request? Are the parameters correct?

Please help   ](*,)

---

