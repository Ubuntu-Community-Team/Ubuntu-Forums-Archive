---
title: "javascript: xml to sqlite import issues"
date: 2009-08-25
forum: Programming Talk
---

### Post by lovinglinux on 2009-08-25
I'm re-writing the code of a Firefox extension, which used several bash scripts. I need to abandon shell scripts and make everything through javascript. I have already completed 99% of the new code, but the xml import functions are giving me headaches.

I need to import a xml file into a sqlite database. So far I have managed to import elements and attributes values, but I have no idea how to filter element values based on specific attributes. The problem is that the xml source might have multiple values for the same element, according to language attributes. I'm using the code below:

```
	

	      var storageService = Components.classes["@mozilla.org/storage/service;1"]
			    .getService(Components.interfaces.mozIStorageService);
	      var mDBConn = storageService.openDatabase(database)

	      var xmlDoc = new XMLHttpRequest();
	      xmlDoc.open('GET', xmltv_path, false);
	      xmlDoc.send(null);
	      if(xmlDoc.status == 0) {
		  dump(xmlDoc.responseXML);
		  var xml = xmlDoc.responseXML

		  var elcategory=null;
		 elcategory = xml.getElementsByTagName('category');
		  var categoryname=null;

		  if (elcategory.length > 0){
		      for(var i=0; i< elcategory.length; i++){
		      categoryname={name: elcategory[i].firstChild.nodeValue};
		      categoryname=categoryname.name;
		      mDBConn.executeSimpleSQL("INSERT INTO dataprogrammecat (name) VALUES ('"+categoryname+"')");
		      }
		  }
		  }
		 

```

When the element "category" has multiple entries for different languages, I get a new entry in the database for each language. How do I filter the data from the xml file, to use just one entry from the element "category" based on the element attribute "lang"?

Another issue is that I'm experiencing a huge disk activity when importing lots of data. For example, the code below don't even stop after several minutes and the disk activity is huge. When I import the same data with a shell script, it's way faster than with this javascript and does not put too much load on the disk. I suspect I must be doing something wrong, which might be creating a loop or extra sql writing:

```

	      var xmlDoc = new XMLHttpRequest();
	      xmlDoc.open('GET', xmltv_path, false);
	      xmlDoc.send(null);
	      if(xmlDoc.status == 0) {
		  dump(xmlDoc.responseXML);
		  var xml = xmlDoc.responseXML

		  var elprogramme=null;
		  elprogramme = xml.getElementsByTagName('programme');
		  var programmeschedule=null;
		  var programmestart=null;
		  var programmestop=null;
		  var programmechannel=null;

		  if (elprogramme.length > 0){
		      for(var i=0; i< elprogramme.length; i++){
		      programmeschedule={astart:elprogramme[i].getAttribute('start')
					  , astop:elprogramme[i].getAttribute('stop')
					  , achannel:elprogramme[i].getAttribute('channel')};
		      programmestart=programmeschedule.astart;
		      programmestop=programmeschedule.astop;
		      programmechannel=programmeschedule.achannel;

		      mDBConn.executeSimpleSQL("INSERT INTO xmltvrawschedule (channel,start,stop) VALUES ('"+programmechannel+"','"+programmestart+"','"+programmestop+"')");
		      }
		  }
		  }
```

Any help will be much appreciated.

---

