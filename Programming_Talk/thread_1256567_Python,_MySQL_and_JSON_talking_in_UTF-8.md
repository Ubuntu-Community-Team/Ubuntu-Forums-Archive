---
title: "Python, MySQL and JSON talking in UTF-8"
date: 2009-09-02
forum: Programming Talk
---

### Post by delude on 2009-09-02
I've spent almost 24h on google trying to find out the solution to what appears to be a simple problem so I decided to ask here.

I'm working on a web form which stores and reads data in a mysql database and updates the form via ajax. I have trouble with non-ascii characters however (the form is in Bulgarian). I successfully save them to the database in utf-8, but when I try to retrieve them with python and send them back to the user agent via JSON they get scrambled. 

When I fetch e column it comes in hex utf-8 
{'Name' : '\xd0\x9b\xd0\xb8\xd0\xbb', ...} 
but JavaScript can't interpret this and gives me errors.  
I can't find any way to turn that data into readable and valid text. What am I missing?

Here are relevant parts of the python script and the ajax request.
Python:
```
db = MySQLdb.connect(host="localhost", user="me", passwd="pwd", db="mydb", cursorclass=MySQLdb.cursors.DictCursor, charset="utf8", use_unicode=0)
dbc = db.cursor()
dbc.execute("SELECT * FROM companylist WHERE ID = 123")
data = dbc.fetchone()
print 'Content-type: application/json; charset=utf-8\n'
print data

```
JavaScript:
```
var data = eval( "(" + response.responseText + ")" );
for (i in data){
  var entry = data[i];
  if (entry!= '0') $('#'+i).val(entry);
}
```

---

### Post by Reiger on 2009-09-02
Not an actual answer to your problem, but why are you using eval() so much?

```

for(var i in data) {
  var entry = data[i]; // entry set to the property with index i in the data list
}

```

---

### Post by myrtle1908 on 2009-09-02
Quotes?  The following works just fine.  It's a few greek characters.

```

var j = {greekUnicode: '\u03B0\u03F4\u03A6\u03A9'};
alert(j.greekUnicode);

```

---

### Post by delude on 2009-09-03
Reiger, that makes sense, I edited it.
myrtle1908, quotes were there. 
Basically the dictionary that python gets from the db is a valid javascript object so it makes it convenient to JSON the response.

Trouble is the encoding is totally wrong. I have UTF-8 set everywhere - on the webpage, the form, the database, the mysqldb connection, the python file and the JSON response. Yet here's what happens to one of the values (a street name).

actual user input: 
> &#1054;&#1084;&#1091;&#1088;&#1090;&#1072;&#1075; 
(phpmyAdmin shows the same, which confirms it's ok in the db)

python: 
```
>>>data['street']
'\xd0\x9e\xd0\xbc\xd1\x83\xd1\x80\xd1\x82\xd0\xb0\xd0\xb3'
>>>print data['street']
&#1087;·&#1087;&#9578;&#1103;&#9488;&#1103;&#9472;&#1103;&#9484;&#1087;&#9567;&#1087;&#1025;
```

javascript:
```
>alert (data['street'])
ÐžÐ¼ÑƒÑ€Ñ‚Ð°Ð³
```

---

### Post by myrtle1908 on 2009-09-03
> **delude said:**
> myrtle1908, quotes were there.

I doubt that.

Anyways you need to decode eg.

[PHP]
<script language="javascript">
var Utf8 = {
	decode : function (utftext) {
		var string = "";
		var i = 0;
		var c = c1 = c2 = 0;
		while (i < utftext.length) {
			c = utftext.charCodeAt(i);
			if (c < 128) {
				string += String.fromCharCode(c);
				i++;
			}
			else if((c > 191) && (c < 224)) {
				c2 = utftext.charCodeAt(i+1);
				string += String.fromCharCode(((c & 31) << 6) | (c2 & 63));
				i += 2;
			}
			else {
				c2 = utftext.charCodeAt(i+1);
				c3 = utftext.charCodeAt(i+2);
				string += String.fromCharCode(((c & 15) << 12) | ((c2 & 63) << 6) | (c3 & 63));
				i += 3;
			}
		}
		return string;
	}
}

var j = {street: '\xd0\x9e\xd0\xbc\xd1\x83\xd1\x80\xd1\x82\xd0\xb0\xd0\xb3'};
alert(Utf8.decode(j.street));
</script>[/PHP]

I should also point out that if you are dealing with large strings then you should probably push and finally join using an array rather than concatenate as I have demonstrated above,

---

### Post by delude on 2009-09-03
You saved my day, myrtle1908. Thanks!

By the way I have python 2.4 on the hosting server. I wouldn't have had that problem with python3 and passing unicode, too bad they won't upgrade.

---

