---
title: "Quicker way in PHP to display database table data"
date: 2008-08-25
forum: Programming Talk
---

### Post by tc101 on 2008-08-25
In php, if I read data from a table, for example "select * from table1" and want to display the data on a web page, do I have to loop through the results and format each line using <tr> and <td> tags, or is there some quicker way to display the data?

---

### Post by LaRoza on 2008-08-25
Not sure what you want. It would be a single foreach loop. Doesn't get much shorter than that.

---

### Post by tc101 on 2008-08-25
Thanks LaRoza.  No problem doing that, but if there was some simple onword way to do it I wanted to know.  I am new to this.

---

### Post by tc101 on 2008-08-25
I wrote the following code below, and it echos each value twice.  Any idea why?

while ($row = mysql_fetch_array($result)) {
   echo '<p> ';
	foreach ($row as $value) {
		echo $value. " ";
	}
}

---

### Post by Reiger on 2008-08-25
Yes there is:

> 
Note

It is possible to obtain XML-formatted output from MySQL in the mysql and mysqldump clients by invoking them with the --xml option. See Section 4.5.1, &#8220;mysql &#8212; The MySQL Command-Line Tool&#8221;, and Section 4.5.4, &#8220;mysqldump &#8212; A Database Backup Program&#8221;.

[size="1"]-- From: [http://dev.mysql.com/doc/refman/5.1/en/xml-functions.html](http://dev.mysql.com/doc/refman/5.1/en/xml-functions.html)[/size]

Which entails... You can test how your MySQL db returns the stuff; then use an XSLT stylesheet to format it into w/ever you want it to end up looking like. 

Then echo the result within the webpage.

So: fetch XML formatted results instead of raw text; grab formatXML($row,$style,$isBody); echo it as you see fit.

From a PHP file I wrote a while ago:
[php]
	function formatXML($doc,$style,$isBody) {
		
		// Load the XML
		$xml = new DomDocument;
		$xml ->load($doc);
		
		if($style!='xhtml') {
			// Load the XSLT
			$xslt= new DomDocument;
			$xslt->load($style);
			
			// Transform the XML to XHTML using the XSLT
			$proc= new XSLTProcessor;
			$proc->importStylesheet($xslt);
			$xhtml= $proc->transformToXML($xml);
		}
		/**
		@ Note allowing raw XHTML to pass through the function 'unharmed'.
		**/
		else
			$xhtml=$xml->saveXML();
		
		if($xhtml)
			return trimXHTML($xhtml);
		else
			if($isBody)
				return '<body><div><h2>XSLT Processing Failed!</h2></div></body>';
			else
				return '<div><h2>XSLT Processing Failed!</h2></div>';
	}

	function trimXHTML($xhtml)
	{
		return preg_replace("/[\t\n]|&#\d+;|<\\?.*\\?>/",'',$xhtml);
	}
[/php]

Note that formatXML() was written to keep returning valid XHTML hence the $isBody switch (in case the bit formatted was required to act as <body></body> section too).

---

