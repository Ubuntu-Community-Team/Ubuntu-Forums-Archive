---
title: "Problem Downloading Free MP3 Files with 'wget'"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by rammerjammer665 on 2011-12-09
hello everyone,

rammerjammer here with another newbie(ish) question. i am sorry in advance if i am posting in the wrong section, please forgive me.

GOAL: i am trying to legally download a free mp3 that is on a website using the 'wget' command in terminal. i would also like to legally download a variety of other free mp3s that are in the same directory.

PROBLEM: after entering the 'wget [http:///path.to.mp3](http:///path.to.mp3)' i am redirected and end up downloading a small, useless file. the file is named correctly but has no data. i am not sure what the issue is (hence newbie).

DETAILS:

-i loaded the page the contains the link to the mp3 i would like would like to legally download
([http://www.xlr8r.com/podcast/2011/12/om-unit](http://www.xlr8r.com/podcast/2011/12/om-unit))
 
-i then looked at the page source that tells me where the file i would like is located
([http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3))

-here is the page source script that lead me to the address above
<script type="text/javascript">$(document).ready(function(){  $("#podcast_m4a a").click(function(){  $.post("/token/create",{        url: "http://media.xlr8r.com/files/podcast/m4a/XLR8R_Podcast_Om_Unit_Podcast_2011_12_06.m4a"      }, function(xml) {    handleResponse(xml);  });  return false; });

 $("#podcast_mp3 a").click(function(){  $.post("/token/create",{        url: "http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3"      }, function(xml) {    handleResponse(xml);  });  return false; });  })

;  function handleResponse(xml){     if(xml==0){         $('#downloadMsg').html("Error downloading file. Please try again.");     }else{         $('#downloadMsg').html("Thank you. Your download will start immediately.");         console.log(xml);         window.location.href=xml;     }              $('#downloadMsg').show(); }</script>

-here is what i see after entering 'wget [http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3)'

--2011-XX-XX XX:XX:XX--  [http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3)
Resolving media.xlr8r.com... 72.21.81.253
Connecting to media.xlr8r.com|72.21.81.253|:80... connected.
HTTP request sent, awaiting response... 307 Temporary Redirect
Location: [http://www.xlr8r.com](http://www.xlr8r.com) [following]
--2011-xx-xx xx-xx--  [http://www.xlr8r.com/](http://www.xlr8r.com/)
Resolving [www.xlr8r.com]("http://www.xlr8r.com")... 174.120.15.146
Connecting to [www.xlr8r.com|174.120.15.146|:80]("http://www.xlr8r.com%7C174.120.15.146%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `XLR8R_Podcast_Om_Unit_2011_12_06.mp3'

    [  <=>                                                                               ] 59,334       187K/s   in 0.3s    

2011-XX-XX XX:XX:XX (187 KB/s) - `XLR8R_Podcast_Om_Unit_2011_12_06.mp3' saved [59334]

-the mp3 file that is downloaded does not work.

QUESTION#1-what have i done wrong that is preventing me from downloading the mp3 listed above??

QUESTION#2-is it  possible to download all of the mp3s by using 'wget [http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_*](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_*)'  ?

final thoughts
-i am certainly able to click through the site and download the original mp3, however, the point is to use terminal to download it.
-in addition, if i wanted to compile all of the mp3s that were released i would have to click through pages for hours. i believe there must be an easier way.

thanks in advance and i hope the situation doesn't sound too confusing.

---

### Post by ilikelinuxitisthebest on 2011-12-10
why exactly do you want to use the terminal to download it?

---

### Post by sandyd on 2011-12-10
> **rammerjammer665 said:**
> [FONT=Verdana][SIZE=2]hello everyone,

rammerjammer here with another newbie(ish) question. i am sorry in advance if i am posting in the wrong section, please forgive me.

GOAL: i am trying to legally download a free mp3 that is on a website using the 'wget' command in terminal. i would also like to legally download a variety of other free mp3s that are in the same directory.

PROBLEM: after entering the 'wget [http:///path.to.mp3](http:///path.to.mp3)' i am redirected and end up downloading a small, useless file. the file is named correctly but has no data. i am not sure what the issue is (hence newbie).

DETAILS:

-i loaded the page the contains the link to the mp3 i would like would like to legally download
([http://www.xlr8r.com/podcast/2011/12/om-unit](http://www.xlr8r.com/podcast/2011/12/om-unit))
 
-i then looked at the page source that tells me where the file i would like is located
([http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3))

-here is the page source script that lead me to the address above
[/SIZE][/FONT][FONT=Verdana][SIZE=2]<script type="text/javascript">$(document).ready(function(){  $("#podcast_m4a a").click(function(){  $.post("/token/create",{        url: "http://media.xlr8r.com/files/podcast/m4a/XLR8R_Podcast_Om_Unit_Podcast_2011_12_06.m4a"      }, function(xml) {    handleResponse(xml);  });  return false; });

 $("#podcast_mp3 a").click(function(){  $.post("/token/create",{        url: "http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3"      }, function(xml) {    handleResponse(xml);  });  return false; });  })

;  function handleResponse(xml){     if(xml==0){         $('#downloadMsg').html("Error downloading file. Please try again.");     }else{         $('#downloadMsg').html("Thank you. Your download will start immediately.");         console.log(xml);         window.location.href=xml;     }              $('#downloadMsg').show(); }</script>

[/SIZE][/FONT][FONT=Verdana][SIZE=2]-here is what i see after entering 'wget [/SIZE][/FONT][FONT=Verdana][SIZE=2]http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3'

--2011-XX-XX XX:XX:XX--  [http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_Om_Unit_2011_12_06.mp3)
Resolving media.xlr8r.com... 72.21.81.253
Connecting to media.xlr8r.com|72.21.81.253|:80... connected.
HTTP request sent, awaiting response... 307 Temporary Redirect
Location: [http://www.xlr8r.com](http://www.xlr8r.com) [following]
--2011-xx-xx xx-xx--  [http://www.xlr8r.com/](http://www.xlr8r.com/)
Resolving [www.xlr8r.com]("http://www.xlr8r.com")... 174.120.15.146
Connecting to [www.xlr8r.com|174.120.15.146|:80]("http://www.xlr8r.com%7C174.120.15.146%7C:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `XLR8R_Podcast_Om_Unit_2011_12_06.mp3'

    [  <=>                                                                               ] 59,334       187K/s   in 0.3s    

2011-XX-XX XX:XX:XX (187 KB/s) - `XLR8R_Podcast_Om_Unit_2011_12_06.mp3' saved [59334]

-the mp3 file that is downloaded does not work.[/SIZE][/FONT][FONT=Verdana][SIZE=2]

QUESTION#1-what have i done wrong that is preventing me from downloading the mp3 listed above??

QUESTION#2-is it  possible to download all of the mp3s by using 'wget [http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_*](http://media.xlr8r.com/files/podcast/mp3/XLR8R_Podcast_*)'  ?

final thoughts
-i am certainly able to click through the site and download the original mp3, however, the point is to use terminal to download it.
-in addition, if i wanted to compile all of the mp3s that were released i would have to click through pages for hours. i believe there must be an easier way.

thanks in advance and i hope the situation doesn't sound too confusing.



[/SIZE][/FONT][SIZE=2]
[/SIZE]
You can't use wget. they have hotlinking protection on.

---

