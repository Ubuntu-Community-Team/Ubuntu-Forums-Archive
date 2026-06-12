---
title: "media scraper questions"
date: 2012-09-23
forum: Programming Talk
---

### Post by feardotcom on 2012-09-23
Ok, so im a CS major in college and im currently taking a java class. I'm looking to create full featured, all-in-one, media manager for linux using java. It will handle movies, tv shows and music. It will rename and organize the files and folders according to xbmc specifications. It will scrape movies, tv shows, and music for descriptions, fanart, cd/dvd art, band bio, and actor/actress lists.

Just glancing over thetvdb.com programming api wiki and they talk about a php interface. Does this mean i have to use php to connect to their api?

Any tips for programming, or feature requests are appreciated.

---

### Post by greenpeace on 2012-09-24
no, it looks like it is an XML API.  It reads like they probably just mean that they implemented the API in PHP on their side.

you'll need to work with XML documents.

---

### Post by feardotcom on 2012-09-24
Ok, thank you for your reply.

---

### Post by PoxSpax on 2012-09-24
Also, might want to familiarize yourself with [http://en.wikipedia.org/wiki/ID3](http://en.wikipedia.org/wiki/ID3).

---

### Post by josephmills on 2012-09-24
I use 
[http://thetvdb.com/](http://thetvdb.com/)

to gather info for tv shows 

For Movies 

[http://www.themoviedb.org/](http://www.themoviedb.org/)


both are open source and used by mythtv and xbmc 

there is also api's for google and rotten tomato's ect

[http://www.programmableweb.com/apis](http://www.programmableweb.com/apis)


I love the fact that qt-quick has the Element XMLListModel 
[http://www.youtube.com/watch?v=po-4f-Xzmzo](http://www.youtube.com/watch?v=po-4f-Xzmzo)
[http://doc.qt.digia.com/4.7-snapshot/qml-xmllistmodel.html](http://doc.qt.digia.com/4.7-snapshot/qml-xmllistmodel.html)

as it can read data live and parse the xml that the api's provide 

Example 

```

import Qt 4.7

XmlListModel {
	id: seriesModel

	function newSearch(text) {
		console.log("Searching: " + text);
		source = [COLOR="Red"]"http://thetvdb.com/api/GetSeries.php?seriesname=dexter"[/COLOR]
		reload()
	}

	source: "http://thetvdb.com/api/GetSeries.php?seriesname="
	query: "/Data/Series"

	XmlRole { name: "name"; query: "SeriesName/string()" }
	XmlRole { name: "seriesid"; query: "seriesid/string()" }
	XmlRole { name: "overview"; query: "Overview/string()" }
	XmlRole { name: "banner"; query: "banner/string()" }

	onStatusChanged: {
		if (status == XmlListModel.Ready) console.log("Loaded")
		if (status == XmlListModel.Loading) console.log("Loading");
		if (status == XmlListModel.Error) console.log("Error: " + errorString);
	}
}




```



[COLOR="red"]http://thetvdb.com/api/GetSeries.php?seriesname=dexter[/COLOR]

Looks up the small info of the tv show "dexter"

then the code parse's it out byt the xml tags 


 query: "/Data/Series"

so get the xml from 

[http://thetvdb.com/api/GetSeries.php?seriesname=dexter](http://thetvdb.com/api/GetSeries.php?seriesname=dexter)


and start a query

query: "/Data/Series"


then we make all them into XmlRole 
[http://doc.qt.digia.com/4.7-snapshot/qml-xmlrole.html](http://doc.qt.digia.com/4.7-snapshot/qml-xmlrole.html)

so that we can call later for say like 

XmlRole { name: "[COLOR="RoyalBlue"]seriesid[/COLOR]"; query: "seriesid/string()" }

this will let us use that later. 

example: 

```

import Qt 4.7
 XmlListModel {
        id serieModel

        function load([COLOR="RoyalBlue"]seriesId[/COLOR]) {
            console.log("Loading " + [COLOR="RoyalBlue"]seriesId[/COLOR])
            source = "http://thetvdb.com/api/<YOUR API KEY>/series/" + [COLOR="RoyalBlue"]seriesId[/COLOR] + "/all/en.xml"
            reload();
        }

        source: ''
        query: "/Data/Series"

        XmlRole { name: "seriesid"; query: "id/string()" }

        XmlRole { name: "title"; query: "SeriesName/string()" }

}

```


That should give you some where to start


I would also say that having a Gimp 2 qml converter has saved me 100's of hours 
[http://www.youtube.com/watch?v=2Hgo9CWV400](http://www.youtube.com/watch?v=2Hgo9CWV400)

---

### Post by feardotcom on 2012-09-25
Thank you, i'll look into that more. Appreciate your input.

Quick question though, is there already a app on linux that i haven't found?

---

