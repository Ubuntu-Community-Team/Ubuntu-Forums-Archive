---
title: "[SOLVED] grease monkey script safe"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by methodmarvel on 2008-06-02
I've downloaded a greasemonkey script which lets me add my facebook events to google calender which is a functionality I really want. I've looked through the source and think it's "safe" or "trustworthy" but I don't really know anything about scripting/code.

I'd really appreciate it if those in the know give it a quick look over just to tell me if it is ok or malicious.

Download from here- [http://www.lostways.com/uploads/facebooktogooglecalendar.user.js](http://www.lostways.com/uploads/facebooktogooglecalendar.user.js)

```
// ==UserScript==

// @name Facebook to Google Calendar

// @namespace http://userscripts.org/scripts/show/8294

// @description Add your facebook events to currently logged in Google Calendar.

// @include http*://*.facebook.com/event.php?eid=*

//

//Version 1.5

//

//Known issues:

// - Doesn't support names with quotation marks in them

//

//Thanks to:

//Michael Seiler, Richard Lainchbury

// ==/UserScript==



(function() {



timezoneoffset=0;

timetype="00";



  var tagline, start, end, date, loc1, loc2, loc3, tagline, replacements, regex, key, namenodes, namenode, name, hostnodes, hostnode, host; 



  monthchanges = { 

    "January": "01",

    "February": "02",

    "March": "03",

    "April": "04",

    "May": "05",

    "June": "06",

    "July": "07",

    "August": "08",

    "September": "09",

    "October": "10",

    "November": "11",

    "December": "12",

    };



//add troublesome characters as they're discovered

  unicode = { 

    '!': "%21",

    '#': "%23",

    ' ': "%20",

    '&': "%26",

    };





regex = {}; 

for (key in monthchanges) { 

    regex[key] = new RegExp(key, 'g'); 

} 

for (key in unicode) { 

    regex[key] = new RegExp(key, 'g'); 

} 



var nametr, tagtr, hosttr, typetr;

for (var r = 0; r < 10; r++) { 

	testnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[1]/TBODY[1]/TR["+r+"]/TD[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < testnodes.snapshotLength; i++) { 

    		node = testnodes.snapshotItem(i); 

    		test1 = node.data; 

		if (test1=="Name:"){

			nametr=r;

			}

		else if (test1=="Tagline:"){

			tagtr=r;

			}

		else if (test1=="Host:"){

			hosttr=r;

			}

		else if (test1=="Type:"){

			typetr=r;

			}

	}

} 

 var starttr, endtr, citytr, streettr, loctr, timetr, datetr;

for (var r = 0; r < 10; r++) { 

	testnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+r+"]/TD[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < testnodes.snapshotLength; i++) { 

    		node = testnodes.snapshotItem(i); 

    		test1 = node.data; 

		if (test1=="Date:"){

			datetr=r;

			oneday=1;

			}

		else if (test1=="Time:"){

			timetr=r;

			}

		if (test1=="Start Time:"){

			starttr=r;

			oneday=0;

			}

		else if (test1=="End Time:"){

			endtr=r;

			}

		else if (test1=="Location:"){

			loctr=r;

			}

		else if (test1=="Street:"){

			streettr=r;

			}

		else if (test1=="City/Town:"){

			citytr=r;

			}

	}

} 

//testtext = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[1]/TBODY[1]/TR[1]/TD[2]/DIV[1]//text()", 



//document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

//for (var i = 0; i < testtext.snapshotLength; i++) { 

//    node = testtext.snapshotItem(i); 

//    s = node.data; 

//    for (key in unicode) { 

//       s = s.replace(regex[key], unicode[key]); 

//    } 

//   node.data = s; 

//} 

namenodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[1]/DIV[1]/H2[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < namenodes.snapshotLength; i++) { 

		node = namenodes.snapshotItem(i); 

		escape(node.data);

		name = node.data; 

		escape(name);

	} 

hostnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[1]/TBODY[1]/TR["+hosttr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < hostnodes.snapshotLength; i++) { 

		node = hostnodes.snapshotItem(i); 

		host = node.data;

		escape(host);

		host = "Hosted by: " + host + "%0A";

	} 

tagnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[1]/TBODY[1]/TR["+tagtr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < tagnodes.snapshotLength; i++) { 

		node = tagnodes.snapshotItem(i); 

		tagline = node.data;

		escape(tagline); 

		tagline = "Tagline: " + tagline + "%0A";

	} 

startnodes = 



document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+starttr+"]/TD[2]/DIV[1]//text()", document, 



null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < startnodes.snapshotLength; i++) { 

	    node = startnodes.snapshotItem(i); 

	    start = node.data; 

	start = start.split(" at ");

	date = start[0];

	} 

endnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+endtr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < endnodes.snapshotLength; i++) { 

		node = endnodes.snapshotItem(i); 

		end = node.data; 

		end = end.split(" at ");

		date2 = end[0];

		time = start[1] + " - " + end[1];

	} 

datenodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+datetr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < datenodes.snapshotLength; i++) { 

 	   node = datenodes.snapshotItem(i); 

	   date = node.data; 

	   date2 = date; 

		}

	var dates = date.split(", ");

	var weekday = dates[0];

	var year = dates[2];

	var monthday = dates[1].split(" ");

	var month = monthday[0];

	var day = monthday[1];

	if (day<10) {

		day = "0" + day; 

	}

	for (key in monthchanges) { 

	        month = month.replace(regex[key], monthchanges[key]); 

	    }

	var dates2 = date2.split(", ");

	var weekday2 = dates2[0];

	var year2 = dates2[2];

	var monthday2 = dates2[1].split(" ");

	var month2 = monthday2[0];

	var day2 = monthday2[1];

	if (day2<10) {

		day2 = "0" + day2; 

	}

	for (key in monthchanges) { 

	        month2 = month2.replace(regex[key], monthchanges[key]); 

	    }



timenodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+timetr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < timenodes.snapshotLength; i++) { 

	    node = timenodes.snapshotItem(i); 

	    time = node.data;

	}

	var times = time.split(" - ");

	var mintime = times[0];

	var maxtime = times[1];

	mintime = mintime.replace ("am",":am");

	mintime = mintime.replace ("pm",":pm");

	starttime = mintime.split(":");

	if (starttime[0]==12) {

		starttime[0] = starttime[0] - 12;

	}

	if (starttime[2]=="pm") {

		starttime = starttime[0]*100 - timezoneoffset*100 + starttime[1]*1 + 1200;

	} else {

		starttime = starttime[0]*100 - timezoneoffset*100 + starttime[1]*1;

		}

	if (starttime<10){

		starttime = "000" + starttime;

		} else if (starttime<100) {

		starttime = "00" + starttime;

		} else if (starttime<1000) {

		starttime = "0" + starttime;

	}

	maxtime = maxtime.replace ("am",":am");

	maxtime = maxtime.replace ("pm",":pm");

	endtime = maxtime.split(":");

	if (endtime[0]==12) {

		endtime[0] = endtime[0] - 12;

	}

	if (endtime[2]=="pm") {

		endtime = endtime[0]*100 - timezoneoffset*100 + endtime[1]*1 + 1200;

	} else {

		endtime = endtime[0]*100 - timezoneoffset*100 + endtime[1]*1;

		}

	if (endtime<10){

		endtime = "000" + endtime;

		} else if (endtime<100) {

		endtime = "00" + endtime;

		} else if (endtime<1000) {

		endtime = "0" + endtime;

	}

loc1nodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+loctr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null); 

	for (var i = 0; i < loc1nodes.snapshotLength; i++) { 

	    node = loc1nodes.snapshotItem(i); 

	    loc1 = node.data; 

	    loc1 = "Location: " + loc1 + "%0A"; 

	} 

loc2nodes = 



document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+streettr+"]/TD[2]/DIV[1]//text()", document, 



null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null);

	for (var i = 0; i < loc2nodes.snapshotLength; i++) { 

	    node = loc2nodes.snapshotItem(i); 

	    loc2 = node.data; 

	    loc2 = loc2 + ", "; 

	} 

loc3nodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[2]/TABLE[2]/TBODY[1]/TR["+citytr+"]/TD[2]/DIV[1]//text()", 



document, null, XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null);

	for (var i = 0; i < loc3nodes.snapshotLength; i++) { 

	    node = loc3nodes.snapshotItem(i); 

	    loc3 = node.data; 

	} 

descnodes = document.evaluate("//HTML[1]/BODY/DIV[2]/DIV[3]/DIV[2]/DIV[1]/DIV[1]/DIV[2]/DIV[1]/DIV[4]//text()", document, null, 



XPathResult.UNORDERED_NODE_SNAPSHOT_TYPE, null);

	for (var i = 0; i < descnodes.snapshotLength; i++) { 

		node = descnodes.snapshotItem(i); 

		desc1 = node.data;

		escape(desc1);

		desc1 = "Description: " + desc1;

}

if (tagline){

}else{

tagline="";

}

if (loc2){

}else{

loc2="";

}



for (key in unicode) { 

//	        name = name.replace(regex[key], unicode[key]); 

	        host = host.replace(regex[key], unicode[key]); 

//	        tagline = tagline.replace(regex[key], unicode[key]); 

//		desc1 = desc1.replace(regex[key], unicode[key]); 

	}



description = host + tagline + loc1 + desc1;

loc = loc2 + loc3;

startdate=year+ month + day;

enddate=year2+ month2 + day2;

finaldate = startdate + "T" + starttime + timetype + "/" + enddate + "T" + endtime + timetype;



var addtogcal = document.createElement("div");

var allLists = document.getElementsByTagName('UL');



addtogcal.innerHTML = '<div class="ical_section" style="margin-bottom:1em;float:left;clear:left;"><div class="ical_text"> <a class="ical" target="_fbtogcal" href="http://www.google.com/calendar/event' + '?action=TEMPLATE&text=' + name + '&dates=' + finaldate + '&details=' + description +  '&location=' + loc + '&trp=true' + '&sprop=www.facebook.com&sprop=name:" class="tools">Add to GCal</a></div></div>';


for(var i = 0; i < allLists.length; i++)

{

	if(allLists[i].className=='actionspro')

	{

		allLists[i].parentNode.insertBefore(addtogcal, allLists[i].nextSibling.nextSibling.nextSibling.nextSibling);

	}

}



})();
```

---

### Post by Xiong Chiamiov on 2008-06-02
Javascript's not my strong points (JQuery's about as far as I'll go), but I don't see anything malicious in there.

+points to you for actually looking through code for security.  We say that's one of the benefits to open-source software, but most of us just take things for granted.

---

