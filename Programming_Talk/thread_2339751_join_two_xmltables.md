---
title: "join two xmltables"
date: 2016-10-12
forum: Programming Talk
---

### Post by marchello_lippi2 on 2016-10-12
Hi all, 

I got some data returned by web api in json format. It is list of regions with timezone id. 
I  can select regions and timezone id (the path is /root/regions) in one  sql request. I can select timezone id with timezone description (the  path is /root/timezones) in other sql request as well. The api used for  both sql request is the same.
The question is how do I join these two  sql request into one? I'm not familiar with syntaxis so far. Please  help, requests below include some "black box", because I got function  that uses external webservice. Any help to perform join is appreciated.

```

SELECT 
"xmlTable.idColumn",
"xmlTable.description",
"xmlTable.id",
"xmlTable.countryid",
"xmlTable.datetimeformatid",
"xmlTable.numberformatid",
"xmlTable.timezoneid"
FROM 
(exec  "webservice1".invokeHTTP(endpoint=>'2.0/api1',requestHeaders=>  'App-Key:  key1',action=>'GET',requestContentType=>'application/xml')) w,
XMLTABLE(XMLNAMESPACES(  'http://www.w3.org/2001/XMLSchema-instance' as "xsi" ),'/root/regions'  PASSING JSONTOXML('root',to_chars(w.result,'UTF-8'))
   COLUMNS 
   "idColumn" FOR ORDINALITY,
   "description" STRING  PATH 'description',
   "id" STRING  PATH 'id',
   "countryid" STRING  PATH 'countryid',
   "datetimeformatid" STRING  PATH 'datetimeformatid',
   "numberformatid" STRING  PATH 'numberformatid',
   "timezoneid" STRING  PATH 'timezoneid'
) "xmlTable" 

```

```

SELECT "xmlTable.idColumn","xmlTable.id","xmlTable.description","xmlTable.offset" FROM 
(exec   "webservice1".invokeHTTP(endpoint=>'2.0/api1',requestHeaders=>'App-Key:  key1',action=>'GET',requestContentType=>'application/xml')) w,
XMLTABLE(XMLNAMESPACES(  'http://www.w3.org/2001/XMLSchema-instance' as "xsi"  ),'/root/timezones' PASSING JSONTOXML('root',to_chars(w.result,'UTF-8'))
   COLUMNS 
   "idColumn" FOR ORDINALITY,
   "id" STRING  PATH 'id',
   "description" STRING  PATH 'description',
   "offset" STRING  PATH 'offset'
) "xmlTable"

```

---

### Post by marchello_lippi2 on 2016-10-12
Ok, I figured out how to join, but my code looks ugly. Now my question  is how to optimize code below, because I use the same subquery twice

```
(exec  "webservice1".invokeHTTP(endpoint=>'2.0/api1',requestHeaders=>  'App-Key:  key1',action=>'GET',requestContentType=>'application/xml'))
```

```
    SELECT 
"xmlTable.idColumn",
"xmlTable.description",
"xmlTable.id",
"xmlTable.countryid",
"xmlTable.datetimeformatid",
"xmlTable.numberformatid",
"xmlTable.timezoneid",
"timeZones.description" as "timezonedescription", 
"timeZones.offset"
FROM 
(exec  "webservice1".invokeHTTP(endpoint=>'2.0/api1',requestHeaders=>  'App-Key:  key1',action=>'GET',requestContentType=>'application/xml')) w,
XMLTABLE(XMLNAMESPACES(  'http://www.w3.org/2001/XMLSchema-instance' as "xsi" ),'/root/regions'  PASSING JSONTOXML('root',to_chars(w.result,'UTF-8')) 
   COLUMNS 
   "idColumn" FOR ORDINALITY,
   "description" STRING  PATH 'description',
   "id" STRING  PATH 'id',
   "countryid" STRING  PATH 'countryid',
   "datetimeformatid" STRING  PATH 'datetimeformatid',
   "numberformatid" STRING  PATH 'numberformatid',
   "timezoneid" integer  PATH 'timezoneid'
) "xmlTable", 
(exec   "webservice1".invokeHTTP(endpoint=>'2.0/api1',requestHeaders=>'App-Key:  key1',action=>'GET',requestContentType=>'application/xml')) w2,
XMLTABLE(XMLNAMESPACES(  'http://www.w3.org/2001/XMLSchema-instance' as "xsi"  ),'/root/timezones' PASSING  JSONTOXML('root',to_chars(w2.result,'UTF-8'))
   COLUMNS 
   "idColumn" FOR ORDINALITY,
   "id" integer  PATH 'id',
   "description" STRING  PATH 'description',
   "offset" STRING  PATH 'offset'
) "timeZones"
where "xmlTable"."timezoneid" = "timeZones"."id";
```

---

