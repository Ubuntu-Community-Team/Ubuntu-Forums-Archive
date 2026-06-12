---
title: "Need help with ajax/javascript population..."
date: 2010-01-08
forum: Programming Talk
---

### Post by hockey97 on 2010-01-08
Hi, I made a form that asks to select your country,state/region,city,item.

It's a market system where you can locally find items for sale.

I used ajax so that for where state/region is it would say select a country first so that based off what country the person picked they will get a drop down menu populated with either the states or regions of that country. The city will still say please select a state/region.. so that based off what state and region you selected it will then populated the cities drop down menu with all the cities name of that state or region.

It works 100% great with Firefox. The problem is when I tried it on IE8 and IE7  it didn't work. I could only use the country drop down menu but when I go to select the state/region names based of what country I selected it gives a blank drop down menu.

I am guessing it's a ajax problem cuz it seems like it's not grabing the data from the database which is mysql. 

Yet this same code works perfectly with any firefox version. I haven't tried google chrome or any other browser other then firefox and IE7,8

would like to know if their is anything special I need to do to get the code working for IE browsers?

here is the code by the way it's javascript:

```
<script language="javascript" type="text/javascript">

function getXMLHTTP() { 

		var xmlhttp=false;	

		try{

			xmlhttp=new XMLHttpRequest();

		}

		catch(e)	{		

			try{			

				xmlhttp= new ActiveXObject("Microsoft.XMLHTTP");

			}

			catch(e){

				try{

				xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");

				}

				catch(e1){

					xmlhttp=false;

				}

			}

		}

		 	

		return xmlhttp;

    }

	

	function getState(country) {		

		

		var strURL="/libs/findState.php?country="+country;

		var req = getXMLHTTP();

		

		if (req) {

			

			req.onreadystatechange = function() {

				if (req.readyState == 4) {

					// only if "OK"

					if (req.status == 200) {
						

	document.getElementById('States').innerHTML=req.responseText;	
					

					} else {

						alert("There was a problem while using XMLHTTP:\n" + req.statusText);

					}

				}				

			}			

			req.open("GET", strURL, true);

			req.send(null);

		}		

	}

	function getCity(country,States) {		

		var strURL="/libs/findCity.php?country="+country+"&state="+States;

		var req = getXMLHTTP();

		

		if (req) {

			

			req.onreadystatechange = function() {

				if (req.readyState == 4) {

					// only if "OK"

					if (req.status == 200) {						

						document.getElementById('City').innerHTML=req.responseText;						

					} else {

						alert("Error:\n Cannot Proccess City Find request.\n Please Contact the website admin about this error.");

					}

				}				

			}			

			req.open("GET", strURL, true);

			req.send(null);

		}

				

	}

</script>
```

---

### Post by WitchCraft on 2010-01-08
The long term solution is to uninstall and ignore IE.

The short term solution is to catch the exceptions and actually output them...
Try to output the exceptions in an alert box!
alert(ex.Message);

---

### Post by myrtle1908 on 2010-01-08
Consider using jQuery or ExtCore.  These handle all of the browser differences for you and generally make your life easier.

[http://jquery.com/](http://jquery.com/)
[http://www.extjs.com/products/extcore/](http://www.extjs.com/products/extcore/)

---

### Post by caelestis2 on 2010-01-08
IMO jQuery is made for javascript newbies who like ajax widgets.

Use [mootools]("http://mootools.net")

Heres how to do what you are doing:

[PHP]
mootools includes here

$('elementid').load('/libs/findState.php?country='+country);
[/PHP]

elementid is the id of the element you want to inject the response of findState into. Or if you didn't want to inject:

[PHP]
myrequest = new Request({
  method:'post',
  url:'/libs/findState.php',
  onSuccess: function(response) {
    yourvariable = response;
  }
});
myrequest.send('country='+country);
[/PHP] 

and yourvariable will contain the response sent by the php file.

And of course, mootools is cross-browser compatible.

---

### Post by myrtle1908 on 2010-01-08
> **caelestis2 said:**
> IMO jQuery is made for javascript newbies who like ajax widgets.

Both jQuery or ExtCore are perfectly fine for what the OP is dealing with.  I'm not sure what you are inferring here.

If you need a full blown UI toolkit for professional corporate-style applications then ExtJS is the way to go.  Nothing even comes close.

---

### Post by hockey97 on 2010-01-09
Hi, thanks for the responses. 

I currently am using jquery for other stuff in my site. I never understood how to use jquery for what I am trying to do.

Is there any tutorial on about using ajax with jquery?

I am using the same php page. this page has a form asking for country,state/region,city,Item  all drop down menu.

What this php page loads it shows a list of countries in it's drop down menu.

the state drop down menu would have a text message saying Please select a Country First.

the city will have Please select a state first. 

so when the user uses the drop down menu of the country list and selects a country.

Then ajax/javascript will sent what country the person select it to other php files which will go a mysql query and grab a list of States or regions in that country and then come back and populate the States drop down menu  with those state or regions names and take out that message saying please selecte a country first.

once they select a state or region then based on that state or region they selected and the country it will got to another php file that will do a mysql query to get a city list for that country and state or region. 
It then will populate the drop down menu of the cities in that state or region at that country.

I don't want to redirect a person to another page or anything.

I looked at the jquery documentation and it only said to inject html into a dom. would this be what I need?

Thanks for the help.

---

### Post by hockey97 on 2010-01-10
I don't get how to use jquery ajax.  

I read this: [http://docs.jquery.com/Ajax/jQuery.ajax](http://docs.jquery.com/Ajax/jQuery.ajax)

what I am doing is making a form to get populate when a person selects a country first.

I want to use ajax to send the data to my php file which will be first a country name then it will do a mysql query lookup and find a list of states in that country that was selected.

I then want ajax to send back a list of state names and populate in the second drop down menu the list. 

Once the person selects a state name from the list it will then pass back both the country and state that the user selected. This will then make the php file to get that data and then do a myql query for cities based off what country and state the user selected. 

Then it will send that list back to the page we are on with that form and then it will populate the city drop down menu. 

that is it. 

I know that load function is to load the php file. But how would I first pass using get method to my php files and then return with data in this case a list of states or cities.

any idea?

---

### Post by WitchCraft on 2010-01-14
The problem is that in that with Microcrap Internet Exterminator, you cannot modify a table or a dropdown box by assigning it innerHTML, because very obviously, MSFT doesn't pay sufficiently to get programmers who actually can create dynamic data structures, that is to say innerHTML is Read-only, but only in Internet Explorer, unfortunately in every version of IE...

That's why you cannot have a comfortable life, and have to write a lot of bogus code to get this done.

See below code on how to populate dropdowns in IE.
At the time, it took me about a day to figure out why it doesn't work and how to get around(I had the same problem with tables).

Note that I don't retrieve the data with XMLhttp, I have it in an array.
But populating the array via XMLhttp with JSON serialization is very easy. (note: don't take XML serialization)

I've included my getHTTPObject, because you version seems to be inferior. Good luck, enjoy !
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html>
<head>
<title>AJAX GridView</title>

<script type="text/javascript" language="javascript">

function getHTTPObject() 
{
	if (window.XMLHttpRequest)  // code for IE7+, Mozilla, Chrome, Opera, Safari
	{ 
		var http = new XMLHttpRequest();
		if (http.overrideMimeType) 
		{
			//http.overrideMimeType('text/text');
			//http.overrideMimeType('text/html');
			//http.overrideMimeType('text/xml');
			//http.overrideMimeType('application/x-javascript');
			//netscape.security.PrivilegeManager.enablePrivilege("UniversalPreferencesRead");
		}
		return http;
		
	} 		
	else if (window.ActiveXObject) // IE < 7
	{ 
		var AllHosteLittleParsers = ["Msxml2.XMLHTTP.6.0", "MSXML2.XMLHTTP.3.0", "MSXML2.XMLHTTP", "Microsoft.XMLHTTP"];
		for (var parserID in AllHosteLittleParsers) 
		{
			try
			{
				return new ActiveXObject(AllHosteLittleParsers[parserID]);
            }
			catch(e)
			{ /* Not this parser */ }
		}
		alert("Awwww snap, you're using those crappy old MS programs...");
		return null;
	}
	
	alert('Browser or Browser version not supported.\nFailed to create XMLHttpRequest');
	return null;
}


    
function state_Change(xmlhttp)
{
		alert(xmlhttp.readyState);
		alert(xmlhttp.status);
		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) 
		{
			document.getElementById('test').innerHTML=xmlhttp.responseText
		}
		else if (http.status == 401)
		{
			alert('Cannot access cross domain information.');
		}
		else if (http.status == 0 && xmlhttp.readyState != 0)
		{
			alert('Cannot access cross domain information.');
		}
}

function timeoutFired()
{
	alert("timeout!!!");
}


function loadXMLDocSynchronous(url)
{
	var xmlhttp = getHTTPObject();
	if(xmlhttp == null || xmlhttp == 'undefined')
	{
		alert("HTTP AJAX request cancelled, because you have one of those crappy browsers that do not support AJAX...");
		return;
	}

	xmlhttp.open("GET",url,false);
	if(xmlhttp.timeout)
	{
		xmlhttp.timeout = 15000;
		xmlhttp.ontimeout = timeoutFired;
	}
	xmlhttp.setRequestHeader("Cache-Control", "no-cache");
	xmlhttp.send(null);
	

	//alert(xmlhttp.readyState);
	//alert(xmlhttp.status);
	//state_Change(xmlhttp);
	
	document.getElementById('test').innerHTML=xmlhttp.responseText;
}



function LoadXML(xmlhttp)
{	
	var x;
	//alert(xmlhttp.responseXML.documentElement.tagName); // CATALOG
	//alert(); // CD, for non IE
	//alert(); // CD, for non IE
	
	var TableNames = new Array ();
	
	if(document.all)
	{
		var strCollectionElement=xmlhttp.responseXML.documentElement.childNodes[0].tagName;// CD
		//x=xmlhttp.responseXML.documentElement.getElementsByTagName("CD");
		x=xmlhttp.responseXML.documentElement.getElementsByTagName(strCollectionElement);
		for(var j=0; j < xmlhttp.responseXML.documentElement.childNodes[0].childNodes.length;++j)
		{
			TableNames[j]= xmlhttp.responseXML.documentElement.childNodes[1].childNodes[j].nodeName;
		}
	}
	else
	{
		var strCollectionElement=xmlhttp.responseXML.documentElement.childNodes[1].tagName; //CD
		x=xmlhttp.responseXML.documentElement.getElementsByTagName(strCollectionElement);
		
		for(var j=0; j < xmlhttp.responseXML.documentElement.childNodes[1].childNodes.length;++j)
		{
			if(xmlhttp.responseXML.documentElement.childNodes[1].childNodes[j].nodeType==3)
				continue;
			
			TableNames[Math.floor(j/2)]= xmlhttp.responseXML.documentElement.childNodes[1].childNodes[j].nodeName;
			//alert(xmlhttp.responseXML.documentElement.childNodes[1].childNodes[j].tagName); //TITLE
		
		}
	}	
	
	var strTable="";
	//strTable+="<table>";
	var strHeader="<tr>";

	for(var k=0; k < TableNames.length;++k)
	{
		strHeader+='<th style="width: 50mm; text-align: left;">'+TableNames[k]+'</th>';
		//alert(TableNames[k]);
	}
	
	strHeader+="</tr>";
	
	document.getElementById('mytableheader').innerHTML=strHeader;
	//strTable+=strHeader;
	
	for (var l=0;l<x.length;l++)
	{
		strTable+='<tr>';
		for(var m=0; m < TableNames.length;++m)
		{
			strTable+='<td>';
			y=x[l].getElementsByTagName(TableNames[m]);
			var strThisNode;
			if(y[0].firstChild == null)
				strThisNode = '';
			else
				strThisNode =y[0].firstChild.nodeValue;
			//alert(strThisNode);
			strTable+=strThisNode;
			strTable+='</td>';
		}
		strTable+='</tr>';
	}


	//strTable+="</table>";
	/*
	<THEAD id="mytableheader">
	<TFOOT id="mytablefooter">
	<TBODY id="firstBlock">
	<TBODY id="secondBlock">
	*/
	document.getElementById('secondBlock').innerHTML=strTable;
}



function loadXMLDocAsynchronous(url)
{
	var xmlhttp = getHTTPObject();
	if (xmlhttp == null || xmlhttp == 'undefined')
	{
		alert("Cancel http request.");
		return;
	}
	
	
	
	xmlhttp.onreadystatechange=function()
	{
		//alert(xmlhttp.readyState);
		//alert(xmlhttp.status);
		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) 
		{
			LoadXML(xmlhttp);
			//document.getElementById('test').innerHTML=xmlhttp.responseText
		}
		else if (xmlhttp.status == 401)
		{
			alert('Access denied.');
		}
		else if (xmlhttp.status == 0)
		{
			alert('Cannot access cross domain information.');
		}
	}

	xmlhttp.open("GET",url,true);
	if(xmlhttp.timeout)
	{
		xmlhttp.timeout = 15000;
		xmlhttp.ontimeout = timeoutFired;
	}
	xmlhttp.setRequestHeader("Cache-Control", "no-cache");
	xmlhttp.send(null);
}




</script>
</head>

<body>



<TABLE id="mytable" style="border-collapse: collapse;">
<THEAD id="mytableheader" onclick="javascript:alert(this.parentNode.id);">
	<TR>
		<th>
			Month
		</th>
		<th>
			Savings
		</th>
	</TR>
</THEAD>
<TFOOT id="mytablefooter">
	<TR>
		<th colspan="2" style="text-align: left;">
			...footer information...
		</th>
	</TR>
</TFOOT>
<TBODY id="firstBlock">
     <TR>
		<td>...first row of block one data...</td>
	</TR>
     <TR>
		<td>
			 ...second row of block one data...
		</td>
	 </TR>
</TBODY>
<TBODY id="secondBlock">
     <TR>
		<td>
			 ...first row of block two data...
		</td>
	 </TR>
     <TR>
		<td>
			...second row of block two data...
		</td>
	 </TR>
</TBODY>
</TABLE>


<table id="newtable">
</table>

	<div>
		<h2 id="test">
			Click to let AJAX change this text
		</h2>
	</div>




<script type="text/javascript" language="javascript">


function ClearTable(strTableName)
{
	var target = document.getElementById(strTableName);
	while (target.rows.length > 0) 
	{
		target.deleteRow(0);
	}
}



function PopulateTable()
{
	ClearTable('mytable');
	
	
	var div = document.createElement("DIV");
	div.innerHTML = '<table id="tempTable" style="display: none"><tr style="background-color: red;"><td style="width: 50mm;">' + "lol" + '</td><td style="width: 50mm";>lol2</td></tr></table>';
	var tt = div.getElementsByTagName('table')[0];

	ClearTable('mytable');
	var target = document.getElementById('mytable');
	for(var i=0; i <tt.rows.length; i++)
	{
		target.appendChild(tt.rows[i]);
		// target.appendChild(tt.rows[i].cloneNode(true));
	}
	
	//div.parentNode.removeChild(div);
	

}


</script>

<!--
<button type="button" onclick="loadXMLDocSynchronous('http://ajax.googleapis.com/ajax/services/search/web?v=1.0&q=Paris%20Hilton')">Synchro Cross-Domain</button>
<button type="button" onclick="loadXMLDocAsynchronous('http://ajax.googleapis.com/ajax/services/search/web?v=1.0&q=Paris%20Hilton')">Async Cross-Domain</button>
-->
<button type="button" onclick="loadXMLDocSynchronous('txtxchange.txt')">Test Synchronos</button>
<button type="button" onclick="loadXMLDocAsynchronous('cd_catalog.xml')">Test asynchronos</button>
<button type="button" onclick="javascript:PopulateTable();">Populate Table</button><br>


</body>
</html>


```

---

### Post by WitchCraft on 2010-01-15
Sorry, I've posted you the GridView instead of the dropdown.

Here's the right example, with XMLloading:

Server Side (ashx):
```

using System;
using System.Collections.Generic;
using System.Web;

namespace JSONserializer
{
    /// <summary>
    /// Summary description for CountryStatesGrabber
    /// </summary>
    public class CountryStatesGrabber : IHttpHandler
    {

        public void ProcessRequest(HttpContext context)
        {
            context.Response.ContentType = "text/plain";
            string[] astrAllStates ;//= { "St. Gallen", "Appenzell", "Zürich", "Schaffhausen" };

            string strCountry = context.Request.QueryString["SelectedCountry"];
            
	
	
	switch (strCountry)
	{
		case "Afghanistan":
			astrAllStates=new string[]{"Badakhshan", "Badghis", "Baghlan", "Balkh", "Bamian", "Farah", "Faryab", "Ghazni", "Ghowr", "Helmand", "Herat", "Jowzjan", "Kabul", "Kandahar", "Kapisa", "Konarha", "Kondoz", "Laghman", "Lowgar", "Nangarhar", "Nimruz", "Paktia", "Paktika", "Parwan", "Samangan", "Sar-e Pol", "Takhar", "Uruzgan", "Wardak", "Zabul"}; // literal array
			break;
		case "Albania":
			astrAllStates=new string[]{"Berat", "Bulqize", "Delvine", "Devoll", "Diber", "Durres", "Elbasan", "Fier", "Gjirokaster", "Gramsh", "Has", "Kavaje", "Kolonje", "Korce", "Kruje", "Kucove", "Kukes", "Lac", "Lezhe", "Librazhd", "Lushnje", "Malesia e Madhe", "Mallakaster", "Mat", "Mirdite", "Peqin", "Permet", "Pogradec", "Puke", "Sarande", "Shkoder", "Skrapar", "Tepelene", "Tirane", "Tropoje", "Vlore"};
			break;
			
		case "Aruba":
			astrAllStates=new string[]{"Brasil", "Bubali", "Ceru Colorado", "Cura Cabai", "Madiki", "Malmok", "Noord", "Oranjestad", "Piedra Plat", "Ponton", "Pos Chikitu", "San Nicolas", "Santa Cruz", "Savaneta", "Wayaca"};
			break;
			
		case "America":
			astrAllStates=new string[]{"California", "Texas", "New York", "Florida", "Illinois", "Pennsylvania", "Ohio", "Michigan", "Georgia", "North Carolina", "New Jersey", "Virginia", "Washington", "Arizona", "Massachusetts", "Indiana", "Tennessee", "Missouri", "Maryland", "Wisconsin", "Minnesota", "Colorado", "Alabama", "South Carolina", "Louisiana", "Kentucky", "Puerto Rico", "Oregon", "Oklahoma", "Connecticut", "Iowa", "Mississippi", "Arkansas", "Kansas", "Utah", "Nevada", "New Mexico", "West Virginia", "Nebraska", "Idaho", "Maine", "New Hampshire", "Hawaii", "Rhode Island", "Montana", "Delaware", "South Dakota", "Alaska", "North Dakota", "Vermont", "District of Columbia", "Wyoming", "Guam", "U.S. Virgin Islands", "Northern Mariana Is.", "American Samoa"};
			break;
        default:
            astrAllStates = new string[] { "No match in the database" };
            break;
	}



            
            // In System.Web.Extensions
            System.Web.Script.Serialization.JavaScriptSerializer serializer = new System.Web.Script.Serialization.JavaScriptSerializer();
            context.Response.Write(serializer.Serialize(astrAllStates));
        }


        public bool IsReusable
        {
            get
            {
                return false;
            }
        }
    }
}

```

Here the HTML:
```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html>
<head>
<title>Select Box AJAX Populate</title>

<script type="text/javascript" language="javascript">
function getHTTPObject() 
{
	if (window.XMLHttpRequest)  // code for IE7+, Mozilla, Chrome, Opera, Safari
	{ 
		var http = new XMLHttpRequest();
		if (http.overrideMimeType) 
		{
			//http.overrideMimeType('text/text');
			//http.overrideMimeType('text/html');
			//http.overrideMimeType('text/xml');
			//http.overrideMimeType('application/x-javascript');
			//netscape.security.PrivilegeManager.enablePrivilege("UniversalPreferencesRead");
		}
		return http;
		
	} 		
	else if (window.ActiveXObject) // IE < 7
	{ 
		var AllHosteLittleParsers = ["Msxml2.XMLHTTP.6.0", "MSXML2.XMLHTTP.3.0", "MSXML2.XMLHTTP", "Microsoft.XMLHTTP"];
		for (var parserID in AllHosteLittleParsers) 
		{
			try
			{
				return new ActiveXObject(AllHosteLittleParsers[parserID]);
            }
			catch(e)
			{ /* Not this parser */ }
		}
		alert("Awwww snap, you're using those crappy old MS programs...");
		return null;
	}
	
	alert('Browser or Browser version not supported.\nFailed to create XMLHttpRequest');
	return null;
}


function state_Change(xmlhttp)
{
		alert(xmlhttp.readyState);
		alert(xmlhttp.status);
		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) 
		{
			document.getElementById('test').innerHTML=xmlhttp.responseText
		}
		else if (http.status == 401)
		{
			alert('Cannot access cross domain information.');
		}
		else if (http.status == 0 && xmlhttp.readyState != 0)
		{
			alert('Cannot access cross domain information.');
		}
}

function RetrieveDropDownData(xmlhttp)
{
	// Retrieve Data, call populate
	alert(xmlhttp.responseText);
}


function loadXMLDocAsynchronous(url)
{
	var xmlhttp = getHTTPObject();
	if (xmlhttp == null || xmlhttp == 'undefined')
	{
		alert("Cancel http request.");
		return;
	}
	
	
	
	xmlhttp.onreadystatechange=function()
	{
		//alert(xmlhttp.readyState);
		//alert(xmlhttp.status);
		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) 
		{
			RetrieveDropDownData(xmlhttp);
			//document.getElementById('test').innerHTML=xmlhttp.responseText
		}
		else if (xmlhttp.status == 401)
		{
			alert('Access denied.');
		}
		else if (xmlhttp.status == 0)
		{
			alert('Cannot access cross domain information.');
		}
	}

	xmlhttp.open("GET",url,true);
	if(xmlhttp.timeout)
	{
		xmlhttp.timeout = 15000;
		xmlhttp.ontimeout = timeoutFired;
	}
	xmlhttp.setRequestHeader("Cache-Control", "no-cache");
	xmlhttp.send(null);
}


function loadJSONSynchronous(url)
{
	var xmlhttp = getHTTPObject();
	if(xmlhttp == null || xmlhttp == 'undefined')
	{
		alert("HTTP AJAX request cancelled, because you have one of those crappy browsers that do not support AJAX...");
		return;
	}

	xmlhttp.open("GET",url,false);
	if(xmlhttp.timeout)
	{
		xmlhttp.timeout = 15000;
		xmlhttp.ontimeout = timeoutFired;
	}
	xmlhttp.setRequestHeader("Cache-Control", "no-cache");
	xmlhttp.send(null);
	

	//alert(xmlhttp.readyState);
	//alert(xmlhttp.status);
	//state_Change(xmlhttp);
	
	return xmlhttp.responseText;
	//document.getElementById('test').innerHTML=xmlhttp.responseText;
}


function PopulateDropDown(CallingDropdown)
{
	//alert(CallingDropdown.options[CallingDropdown.selectedIndex].value);
	//alert(document.getElementById('Countries').innerHTML);
	var DropDown2Populate = document.getElementById('States');
	DropDown2Populate.disabled=false;
	myOnChange = new Function("e", "location.href=this.options[this.selectedIndex].value");
	DropDown2Populate.onchange = myOnChange;
	
	var txtResponse = loadJSONSynchronous('http://localhost/jsontest/CountryStatesGrabber.ashx?SelectedCountry='+escape(CallingDropdown.options[CallingDropdown.selectedIndex].text));
	var astrStates=new Array(); // condensed array
	astrStates=eval(txtResponse);
	/*
	switch (CallingDropdown.options[CallingDropdown.selectedIndex].text)
	{
		case "Afghanistan":
			astrStates=["Badakhshan", "Badghis", "Baghlan", "Balkh", "Bamian", "Farah", "Faryab", "Ghazni", "Ghowr", "Helmand", "Herat", "Jowzjan", "Kabul", "Kandahar", "Kapisa", "Konarha", "Kondoz", "Laghman", "Lowgar", "Nangarhar", "Nimruz", "Paktia", "Paktika", "Parwan", "Samangan", "Sar-e Pol", "Takhar", "Uruzgan", "Wardak", "Zabul"]; // literal array
			break;
		case "Albania":
			astrStates=["Berat", "Bulqize", "Delvine", "Devoll", "Diber", "Durres", "Elbasan", "Fier", "Gjirokaster", "Gramsh", "Has", "Kavaje", "Kolonje", "Korce", "Kruje", "Kucove", "Kukes", "Lac", "Lezhe", "Librazhd", "Lushnje", "Malesia e Madhe", "Mallakaster", "Mat", "Mirdite", "Peqin", "Permet", "Pogradec", "Puke", "Sarande", "Shkoder", "Skrapar", "Tepelene", "Tirane", "Tropoje", "Vlore"];
			break;
			
		case "Aruba":
			astrStates=["Brasil", "Bubali", "Ceru Colorado", "Cura Cabai", "Madiki", "Malmok", "Noord", "Oranjestad", "Piedra Plat", "Ponton", "Pos Chikitu", "San Nicolas", "Santa Cruz", "Savaneta", "Wayaca"];
			break;
			
		case "America":
			astrStates=["California", "Texas", "New York", "Florida", "Illinois", "Pennsylvania", "Ohio", "Michigan", "Georgia", "North Carolina", "New Jersey", "Virginia", "Washington", "Arizona", "Massachusetts", "Indiana", "Tennessee", "Missouri", "Maryland", "Wisconsin", "Minnesota", "Colorado", "Alabama", "South Carolina", "Louisiana", "Kentucky", "Puerto Rico", "Oregon", "Oklahoma", "Connecticut", "Iowa", "Mississippi", "Arkansas", "Kansas", "Utah", "Nevada", "New Mexico", "West Virginia", "Nebraska", "Idaho", "Maine", "New Hampshire", "Hawaii", "Rhode Island", "Montana", "Delaware", "South Dakota", "Alaska", "North Dakota", "Vermont", "District of Columbia", "Wyoming", "Guam", "U.S. Virgin Islands", "Northern Mariana Is.", "American Samoa"];
			break;
		default:
			astrStates=["No match in the database"];
	}
	*/
	
	astrStates.sort(); // Forgot to sort US States
	//http://www.javascriptkit.com/javatutors/arraysort.shtml
	//astrStates.reverse(); // Descending order
	
	DropDown2Populate.innerHTML="";
	// DropDown2Populate.innerHTML='<option value="" selected="true">--- Please Select ---</option>';
	var theOption=document.createElement("OPTION");
	var theText=document.createTextNode("--- Please Select ---");
	theOption.appendChild(theText);
	// theOption.setAttribute("value","Tutorial.htm");
	// theOption.setAttribute("text","Tutorial.htm");
	// theOption.text="Alabama";
	DropDown2Populate.appendChild(theOption);
	
	
	for(var i=0; i<astrStates.length;++i)
	{
		theOption=document.createElement("OPTION");
		theText=document.createTextNode(astrStates[i]);
		theOption.appendChild(theText);
		theOption.value="http://www.wolframalpha.com/input/?i="+ astrStates[i];
		DropDown2Populate.appendChild(theOption);
	}	
}



</script>
<head>

<body>


<select id="Countries" onchange="PopulateDropDown(this)">
  <option value="volvo">Afghanistan</option>
  <option value="saab">Albania</option>
  <option value="mercedes">Aruba</option>
  <option value="audi">America</option>
  <option value="volvo" selected="true">--- Please select ---</option>
</select>
<br />
<br />
<br />
<!-- multiple="multiple" size="2" -->
<select id="States" disabled="true" >
	<option value="Testentry.htm" >Test entry</option>
	<option selected="true" value="">--- Please Select ---</option>
</select>

<button type="button" onclick="javascript:PopulateDropDown();">Populate Dropdown</button>

</body>
</html>

```

---

