---
title: "PHP xml from webservice into useful string?"
date: 2011-02-20
forum: Programming Talk
---

### Post by sdowney717 on 2011-02-20
how can I use what comes back?
What is coming back?
what I want to do is turn it into some string data to load into the various fields of a mysql database.

I cant understand how to get the string and convert elements to something useful
I tried running this in Chrome and I just get text, in firefox it shows xml headers.
So I dont understand what I really have here.

[PHP]<?PHP
//from here http://www.devshed.com/c/a/PHP/Fetching-Search-Results-as-Serialized-Arrays-with-Yahoo-Web-Services-and-PHP-5/1/
//http://php.net/manual/en/book.simplexml.php
// example using LOC SRU Search Web Service - search results are displayed in raw XML format

try{

$request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';

// trigger the http request

if(!$results=file_get_contents($request)){throw new Exception('Error requesting LOC SRU Web service');}

// display the results in XML format

header('Content-type:text/xml;charset=iso-8859-1');
echo $results;

}//end of try

catch(Exception $e){echo $e->getMessage();exit();}


?>[/PHP]

roughly it is this, you save the xml to a file
then you have to parse it.
The file needs to exist and have read write permissions
if it does not exist then it likely wont be created due to a permissions problem.

[PHP]<?PHP
//from here http://www.devshed.com/c/a/PHP/Fetching-Search-Results-as-Serialized-Arrays-with-Yahoo-Web-Services-and-PHP-5/1/
//http://php.net/manual/en/book.simplexml.php
// example using LOC SRU Search Web Service - search results are displayed in raw XML format

try{

$request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';

// trigger the http request

//if(!$results=file_get_contents($request)){throw new Exception('Error requesting LOC SRU Web service');}

// display the results in XML format

//header('Content-type:text/xml;charset=iso-8859-1');
//echo $results;

}//end of try

catch(Exception $e){echo $e->getMessage();exit();}
   $request='http://z3950.loc.gov:7090/voyager?version=1.1&operation=searchRetrieve&query=dinosaur&startRecord=2&maximumRecords=5';
   echo $request;

   $filename = dirname(__FILE__)."/loc.xml";
   $raw_xml = file_get_contents($request);
   echo $raw_xml;
   $fp = fopen($filename, "w");
   fwrite($fp, $raw_xml);
   fclose ($fp);




?>[/PHP]

---

