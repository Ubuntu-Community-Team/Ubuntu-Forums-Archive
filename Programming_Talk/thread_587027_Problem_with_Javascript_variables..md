---
title: "Problem with Javascript variables."
date: 2007-10-22
forum: Programming Talk
---

### Post by CornMaster on 2007-10-22
I'm working on an AJAX site using PHP.  I have a php page that requests information.  I have another PHP page that returns the info, and two javascript files which relay this info.

Basically my layout is like this:
PHP page -> JS file (this handles the display of the page) -> JS file (This talks to the server) -> PHP file (this returns the info)

I've done something similar to this before, except I only used one file as my interface, and it was quite messy.  So I want to separate this into two separate files.  

The error I get is that the variable is always undefined when I return it.  Here is the code from the relevant files.

(This function gets the XML file from the server.  I'm able to spit out the XML data here, and I know it is all there are formatted properly.  Firebug allows be to traverse the tree)
```

function listExamsAJAX(type){
	xmlHttp=GetXmlHttpObject();
	if (xmlHttp==null){
		alert ("Browser does not support HTTP Request");
		return;
	} 
	xmlHttp.onreadystatechange=function(){
	  if(xmlHttp.readyState==4 || xmlHttp.readyState=="complete"){
    	// Get the data from the server's response
    	xmldoc = xmlHttp.responseXML;
     	return xmldoc;
	  }	
	}
	xmlHttp.open("GET","libs/invigilator.php?action=1&sid=" + Math.random(),false);
	xmlHttp.send(null);
}

```


This function originally called the function above and I'm assigning the output to a variable.  No matter what I return from the listExamsAJAX function, returnedXML always equals undefined.  I even tried returning a string, and it was still undefined.  I don't do a lot of JS programming, so I imagine I'm missing something basic.
```

function listExams(){
	returnedXML = listExamsAJAX("basic");
	alert(returnedXML);
	var sitediv = document.getElementById("exams");
	var newexam = document.createElement("p");

	var examid = returnedXML.getElementsByTagName("id")[0].childNodes[0].nodeValue;
	var date = returnedXML.getElementsByTagName("date")[0].childNodes[0].nodeValue;
	var starttime = returnedXML.getElementsByTagName("starttime")[0].childNodes[0].nodeValue;
	var endtime = returnedXML.getElementsByTagName("endtime")[0].childNodes[0].nodeValue;
	var invigilator = returnedXML.getElementsByTagName("invigilator")[0].childNodes[0].nodeValue;
	var notes = returnedXML.getElementsByTagName("notes")[0].childNodes[0].nodeValue;

	newexam.setAttribute('id', examid);
	
	sitediv.innerHTML = 'Date: ' + date + ' --- Start Time: ' + starttime + ' --- End Time: ' + endtime  + ' --- Invigilator: ' + invigilator + ' --- Notes: ' + notes;
	
	sitediv.appendChild(newexam);

}

```

Any insights would be appreciated.  This is causing me great frustration.

---

### Post by germania on 2007-10-22
Your problem is that the onreadystatechange function is returning the xml document, and the browser-internal stuff that calls onreadystatechange is what it's returned to.  You need to refactor what you have so it's event driven, EG make it

```


function listExamsAJAX(type, onload) {
	xmlHttp=GetXmlHttpObject();
	if (xmlHttp==null){
		alert ("Browser does not support HTTP Request");
		return;
	} 
	xmlHttp.onreadystatechange=function(){
	  if(xmlHttp.readyState==4 || xmlHttp.readyState=="complete"){
    	// Get the data from the server's response
    	xmldoc = xmlHttp.responseXML;
     	onload.call(this, xmldoc);
	  }	
	}
	xmlHttp.open("GET","libs/invigilator.php?action=1&sid=" + Math.random(),false);
	xmlHttp.send(null);

}


```

then you can call it like:

```


var parseExams = function(returnedXML) {
	alert(returnedXML);
	var sitediv = document.getElementById("exams");
	var newexam = document.createElement("p");

	var examid = returnedXML.getElementsByTagName("id")[0].childNodes[0].nodeValue;
	var date = returnedXML.getElementsByTagName("date")[0].childNodes[0].nodeValue;
	var starttime = returnedXML.getElementsByTagName("starttime")[0].childNodes[0].nodeValue;
	var endtime = returnedXML.getElementsByTagName("endtime")[0].childNodes[0].nodeValue;
	var invigilator = returnedXML.getElementsByTagName("invigilator")[0].childNodes[0].nodeValue;
	var notes = returnedXML.getElementsByTagName("notes")[0].childNodes[0].nodeValue;

	newexam.setAttribute('id', examid);
	
	sitediv.innerHTML = 'Date: ' + date + ' --- Start Time: ' + starttime + ' --- End Time: ' + endtime  + ' --- Invigilator: ' + invigilator + ' --- Notes: ' + notes;
	
	sitediv.appendChild(newexam);

};

listExamsAJAX("basic", parseExams);


```

edit:  It might be worth noting that call() is a function available to all function objects... the first argument is what 'this' will refer to (the scope variable), and all arguments after it are actual arguments to the function

---

### Post by CornMaster on 2007-10-23
That worked great.  I think I'll do some extra reading so I can try to understand what is going on. ;)

Now I need to figure out why it chokes on an XML item that is empty.  And also design a loop to display all the entries no matter the size.

Thanks for the help. :)

---

