---
title: "IE8 ajax asynchronous  racing condition"
date: 2011-06-21
forum: Programming Talk
---

### Post by pharubu on 2011-06-21
The below ajax code works on all browsers except IE8 where it works only 50% of the time. 

It works in asynchronous mode only when the php code returns the data quickly enough.

But when its not fast enough, it ignores the wait function and only returns the data after 
the code hits "return true".

Somewhat annoying when using predictive text on an html input box.

The problem can be solved by inserting an alert but thats not ideal.

Any thoughts appreciated.  

```


<html>
<head>

<SCRIPT type="text/javascript">


var gbOnLoad = false;

function getHttpResponse(psUrl, poFunc, pbIsSynchronous) 
{
  var fiIsIE8Plus = window.XDomainRequest ? true : false;
  var http = getXmlHttpObject();

  if (fiIsIE8Plus) {
    gbOnLoad = false;
    http.ontimeout = function() { alert("Please try again. On repeated display of this message please contact the webmaster"); };
    http.onerror = function() { alert("An error ocurred. Please try again or contact the webmaster"); };
    http.onprogress = function() {};

    http.onload = function() {
      poFunc(http);
      gbOnLoad = true;
    };
  }
  else {
    if ( pbIsSynchronous == false ) {
      http.onreadystatechange=function() {
        if(http.readyState == 4) {
          if(http.status == 200) {
            poFunc(http);
          }
        }
      }
    }  
  }
  
  if ( pbIsSynchronous == false ) {  
    http.open("GET", psUrl, true);
    http.send(null);
  } 
  else {

    if (fiIsIE8Plus) {
      http.open("GET", psUrl, true);
      http.send(null);

// Doesnt work; there seems to be a race condition (50% of the time) that can only be fixed with an alert or prompt
//      if (gbOnLoad == false) {      
//        waitForData();
//      }  
    }
    else  {
      http.open("GET", psUrl, false);
      http.send(null);
      poFunc(http);
    }
  }
}


function getXmlHttpObject()
{
  var foXhr = 0;
  var fiIsMSIE = /*@cc_on!@*/0;
 
  if (fiIsMSIE) {

    for (fiIdx=1;fiIdx<=8;fiIdx++) {
      try {

        if ( fiIdx == 1 ) {
          foXhr = new XDomainRequest();
          break;
        }
        if ( fiIdx == 2 ) {
          foXhr = new ActiveXObject("MSXML2.XMLHTTP.6.0");
          break;
        }
        if ( fiIdx == 3 ) {
          foXhr = new ActiveXObject("MSXML2.XMLHTTP.5.0");
          break;
        }
        if ( fiIdx == 4 ) {
          foXhr = new ActiveXObject("MSXML2.XMLHTTP.4.0");
          break;
        }
        if ( fiIdx == 5 ) {
          foXhr = new ActiveXObject("MSXML2.XMLHTTP.3.0");
          break;
        }
        if ( fiIdx == 6 ) {
          foXhr = new ActiveXObject("MSXML2.XMLHTTP.2.0");
          break;
        }
        if ( fiIdx == 7 ) {
          foXhr = new ActiveXObject("Microsoft.XMLHTTP");
          break;
        }
        if ( fiIdx == 8 ) {
          foXhr = window.createRequest();
          break;
        }
      }
      catch( e1 )
      {
      }     
    }
  }
  else {
    for (fiIdx=1;fiIdx<=2;fiIdx++) {
      try {

        if ( fiIdx == 1 ) {
          foXhr = new XMLHttpRequest();
          break;
        }
        if ( fiIdx == 2 ) {
          foXhr = window.createRequest();
          break;
        }
      }
      catch( e1 )
      {
      }     
    }
  }
   
  return foXhr;
} 

function pause(piMilliseconds) {
  var foDate = new Date();
  while ( (new Date()) - foDate <= piMilliseconds) 
  { 
    // Do nothing  
  }
}


function waitForData() {
  // Wait time in milliseconds
  var fiMilliseconds = 100;
  // Wait 30 Seconds. So work out the number of loops needed and return as an int 
  var fiWaitMaxSecond = ((30 * 1000 ) / fiMilliseconds) | 0; 

  for (var fiIdx=0; fiIdx<fiWaitMaxSecond; fiIdx++) {
    if (gbOnLoad == true) {
      break;
    }  
    pause(fiMilliseconds); 
  }
}


function callUrlOne() {
 
  var foFunc = function(poHttp) {
                 var foDivId = document.getElementById("one");
                 foDivId.innerHTML = poHttp.responseText;
               }
               
  getHttpResponse('test.php', foFunc, true); 
  
  // Extra code here to return true or false
  
  return true;
}


</SCRIPT>

</head>
<body>

<!-- Suspect race condition is created by return -->
<button type="submit" onclick="return callUrlOne();">One</button>

<div id="one">
  test
</div>

<div id="two">
</div>

</body>
</html>

```[PHP]<?php
  // IE needs the header to work
  header('Access-Control-Allow-Origin: *');
  echo "data";
?>  
[/PHP]

---

