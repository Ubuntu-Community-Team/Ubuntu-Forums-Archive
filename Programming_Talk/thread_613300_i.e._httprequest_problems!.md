---
title: "i.e. httprequest problems!"
date: 2007-11-14
forum: Programming Talk
---

### Post by dmwilson86 on 2007-11-14
Could someone please tell me what is wrong with the internet explorer httprequest I have made here....it works in firefox (of course) but fails miserably with explorer:


function createXMLHttpRequest() {
	try { return new ActiveXObject("Msxml2.XMLHTTP"); } catch (e) {}
	try { return new ActiveXObject("Microsoft.XMLHTTP"); } catch (e) {}
	try { return new XMLHttpRequest(); } catch(e) {}
	alert("XMLHTTPRequest not supported");
	return null;
   }


function $(id) { return document.getElementById(id); }
var xhr = createXMLHttpRequest();

window.onload = function() {

	$("li1").onclick = function() {
		xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "whatsnew.php", true);
	xhr.send(null);
}	
	
		$("li2").onclick = function() {
		xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "about.html", true);
	xhr.send(null);
}	

		$("li3").onclick = function() {
		xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "contact.html", true);
	xhr.send(null);
}	

		$("li4").onclick = function() {
		xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "portfolio.html", true);
	xhr.send(null);
}	

		$("li5").onclick = function() {
		xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "credits.html", true);
	xhr.send(null);
}	




	xhr.onreadystatechange = function() {
		if (xhr.readyState==4) { // Request is finished
		if (xhr.status==200) {
		$("content").innerHTML = xhr.responseText;
		}  else { alert("Message returned, but with error status.");}}}
	xhr.open("POST", "start.html", true);
	xhr.send(null);
}



-->Thanks a mill for any help or suggestions!!

---

### Post by germania on 2007-11-15
What you're doing to get the xmlhttprequest object should work fine.  Try using firebug or an excessive number of alert()'s to figure out where it's going wrong... also make sure ActiveX is enabled in IE.

HTH

---

### Post by smartbei on 2007-11-15
@germania: Since it works in Firefox, I am puzzled as to how debugging with FireBug would help.

@OP: Try finding out exactly what part doesn't work in IE. For example, does the function createXMLHttpRequest return null? Report back with findings :D.

By the way, couldn't:
```

xhr.onreadystatechange = function() {
    if (xhr.readyState==4) { // Request is finished
        if (xhr.status==200) {
            $("content").innerHTML = xhr.responseText;
        } else { alert("Message returned, but with error status.");
        }
    }
}
xhr.open("POST", "start.html", true);
xhr.send(null);

```

Be made into a single function? That would seem to be far shorter. It would just need to take as input the page name - that's the only thing that changes between copy-and-pastes :p.

Also, please use code tags - See the "#" symbol in the advanced editor/post writer.

---

### Post by kefler on 2007-11-15
> 
    var fsObjId = "";    



    function fetchPage(url, id) {

	var httpRequest;



	var ie = document.all?true:false;



	var fsobj = document.createElement("DIV");

	fsobj.style.position = "absolute";

	fsobj.style.top = 0;

	fsobj.style.left = 0;

	fsobj.style.width = document.body.clientWidth;

	fsobj.style.height = document.body.clientHeight;

	fsobj.style.zIndex = 100;

	fsobj.style.backgroundColor = "#2A2A2A";

	fsobj.innerHTML = "<table width='100%' height='100%'><tr><td align='center'>Loading...</td></tr></table>";

	fsobj.id = "loadingScreen";



	if(ie) {

		fsobj.style.filter = "alpha(opacity=75)";

	} else {

		fsobj.style.opacity = 0.75;

	}



	document.body.appendChild(fsobj);



        if (window.XMLHttpRequest) {

            httpRequest = new XMLHttpRequest();

            if (httpRequest.overrideMimeType) {

                httpRequest.overrideMimeType('text/html');

            }

        } 

        else if (window.ActiveXObject) {

            try {

                httpRequest = new ActiveXObject("Msxml2.XMLHTTP");

                } 

                catch (e) {

                           try {

                                httpRequest = new ActiveXObject("Microsoft.XMLHTTP");

                               } 

                             catch (e) {}

                          }

                                       }



        if (!httpRequest) {

            alert('Giving up :( Cannot create an XMLHTTP instance');

            return false;

        }



	fsObjId = id;



        httpRequest.onreadystatechange=function() { getContent(httpRequest); };

        if(url.indexOf("http://") < 0) httpRequest.open('GET', url, true); 

	if(url.indexOf("http://") >= 0) httpRequest.open('GET', 'httpRequest.php?url='+url, true);

        httpRequest.send(null);



    }



    function getContent(httpRequest) {

        if (httpRequest.readyState == 4) {

		document.getElementById(fsObjId).innerHTML = httpRequest.responseText;

		document.body.removeChild(document.getElementById("loadingScreen"));

        }

    }


Sorry about all the custom mumbo jumbo in my code, it hasn't been optimized yet, and this is used for my site, I do not take any credit for the initial code as it was taken from the mozilla getting started with ajax guide written by someone else.

---

