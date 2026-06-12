---
title: "Need Advice On Updating Files on Server"
date: 2010-05-18
forum: Programming Talk
---

### Post by Black Mage on 2010-05-18
I am currently developing some online software and one of the requirements is the ability for a registered user to to connect to a remote server, authenticate and then download files to the current server and replace the older ones.

One of the most important aspect is the users cannot know the directory of these files.

Right now the only possible solution I can think of is using XML-RPC, does anyone else have any other suggestions?

BTW, the current application is written in PHP and supports javascript/jquery/prototype/mootools.

---

### Post by bvdelft on 2010-05-18
How about placing the files in a folder that the user has no access to (i.e. outside /var/www and other folders available from the web). Give the apache/php-service access to this folder, make it read the files in memory and stream them buffered to the user requesting the download.

[http://www.google.nl/search?hl=nl&q=php+stream+file&aq=f&aqi=g1&aql=&oq=&gs_rfai=](http://www.google.nl/search?hl=nl&q=php+stream+file&aq=f&aqi=g1&aql=&oq=&gs_rfai=)

---

