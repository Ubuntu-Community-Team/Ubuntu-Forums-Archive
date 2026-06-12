---
title: "some annoyances with ubuntu"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by irish66 on 2008-11-10
1. hitting the shift arrow key gives me 6 instead of highlighting text/
2. rapidshare account info has to be inputted everytime i reboot into ubuntu.
firefox crashes even more than it does in windows.
m

---

### Post by tuxxy on 2008-11-10
> **irish66 said:**
> 1. hitting the shift arrow key gives me 6 instead of highlighting text/
2. rapidshare account info has to be inputted everytime i reboot into ubuntu.
firefox crashes even more than it does in windows.
m

1. Did you check keyboard shortcuts app, ALT + > highlights text fine here

2. Are you clearing all your stored information on exiting Firefox? it should save your information

---

### Post by irish66 on 2008-11-10
nope, not doing anything with firefox settings except closing it
will have look at keyboard shortcuts later.
Thank you for tips.
M

---

### Post by Axos on 2008-11-10
> **tuxxy said:**
> Did you check keyboard shortcuts app
I don't see anything about text selection in the shortcuts app (System, Preferences, Keyboard Shortcuts).

---

### Post by AndrewTheArt on 2008-11-10
Sounds like problems specific to your machine.

**1. hitting the shift arrow key gives me 6 instead of highlighting text/**

What is the "shift arrow key"? Do you mean, the Shift key? Shift + dragging does ideeed highlight, at least in my Firefox/ubuntu, with no key settings changed.

**2. rapidshare account info has to be inputted everytime i reboot into ubuntu.**
Log into the website and make sure you say 'Save' when prompted by Firefox. Nothing else to say here.

**firefox crashes even more than it does in windows.**
Not for me. Here's a suggestion. Run Firefox from the terminal (Apps->Accessories->Terminal, then type in firefox, then press Enter). When it crashes, look what the terminal output says, and paste it here.


Good luck.

---

### Post by irish66 on 2008-11-11
1. Sorry, I should have said the shft key (ie key with the arrow symbol pointing upwards on the left of the keyboard) and the key with the arrow symbol pointing to the right.No hitting the shift key and the plus key gets me +. I may just have my my keyboard setting configured wrongly.
2+3. Thanks for those tips. I'll try them.
M

---

### Post by irish66 on 2008-11-11
I probably should have also said that I'm using a logitech wireless keyboard. Anyway i found a combination that works, but i have to turn on numlock to use it. it's numlock on, then holding the ctrl key and the arrow key above it down, then pressing the arrow key pointing to the right. 
But that's not really good enough, is it? :)
M

---

### Post by irish66 on 2008-11-14
Hi. had a firefox crash, after starting from terminal. Do you need all 
text from terminal or just the last few lines. 
M
.

---

### Post by LowSky on 2008-11-14
give us it all and use code tags, go to advanced post and use the # icon ot will wrap the text

---

### Post by irish66 on 2008-11-14
anyway, have to shut down ubuntu for now. So here is complete text from terminal.
llowscriptaccess=sameDomain -P bgcolor=#eaeaea -P flashvars=eventType=search&eventValue=superman&callTS=true -P height=1 -P id=spudts -P name=spudts -P quality=high -P src=http://www.veoh.com/static/flash/players/spudts.swf?version=4 -P style= -P type=application/x-shockwave-flash -P width=1 -P wmode=opaque - 
Forked successfully, child process PID is 7944
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xd17d258
PARAM: type = application/x-shockwave-flash
PARAM: src = [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf)
PARAM: style = 
PARAM: id = viewportflashPlayer
PARAM: name = viewportflashPlayer
PARAM: bgcolor = #000000
PARAM: quality = high
PARAM: wmode = opaque
PARAM: allowfullscreen = true
PARAM: allowscriptaccess = always
PARAM: flashvars = fwurl=http://2814.v.fwmrm.net/&fwid=11894&fwsandiskid=&contentRatingId=1&pFamilyFilter=on&dc_intel=true&dc_login=no&dc_publisher=appleg5&dc_hasPublished=&dc_pro=&dc_age18=no&pGender=&pvrn=93910823&dc_ucategory=category_animation;&dc_site=video&dc_tile=1&dc_target=250&dc_videopermalink=e10637&dc_veohtv=no&dc_sexy=false&dc_planguage=&pageUrl=http://www.veoh.com/videos/e10637&searchTerm=superman&player=videodetails&permalinkId=e10637&id=anonymous&playAuto=1&external=0&affiliateId=&pageUID=36413798&ss_partnerId=619&dc_pcategory=&videoId=10637&eventType=content&eventValue=104&veohVisitorId=CFF60A9-8AC7-4286-48EA-EB1DC4B7EA38B&pPubStat=Indie&contentSource=&dc_isHD=0&userName=&userAge21plus=&userAgeGroup=&webPlayerInstalled=false&webPlayerVersion=&webPlayerPort=&veohTvInstalled=false
PARAM: align = middle
PARAM: width = 540
PARAM: height = 438
NewStream: The full URL is [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf)
Closed 78 files.
Starting process: /usr/bin/gtk-gnash -x 61316113 -j 540 -k 438 -u [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf) -F 78 -U [http://www.veoh.com/videos/e10637?rank=2&jsonParams=%7B%22numResults%22%3A20%2C%22rlmin%22%3A0%2C%22query%22%3A%22superman%22%2C%22rlmax%22%3Anull%2C%22veohOnly%22%3Atrue%2C%22order%22%3A%22default%22%2C%22range%22%3A%22a%22%2C%22sId%22%3A%22268163083557965318%22%7D&searchId=268163083557965318&rank=3](http://www.veoh.com/videos/e10637?rank=2&jsonParams=%7B%22numResults%22%3A20%2C%22rlmin%22%3A0%2C%22query%22%3A%22superman%22%2C%22rlmax%22%3Anull%2C%22veohOnly%22%3Atrue%2C%22order%22%3A%22default%22%2C%22range%22%3A%22a%22%2C%22sId%22%3A%22268163083557965318%22%7D&searchId=268163083557965318&rank=3) -P align=middle -P allowfullscreen=true -P allowscriptaccess=always -P bgcolor=#000000 -P flashvars=fwurl=http://2814.v.fwmrm.net/&fwid=11894&fwsandiskid=&contentRatingId=1&pFamilyFilter=on&dc_intel=true&dc_login=no&dc_publisher=appleg5&dc_hasPublished=&dc_pro=&dc_age18=no&pGender=&pvrn=93910823&dc_ucategory=category_animation;&dc_site=video&dc_tile=1&dc_target=250&dc_videopermalink=e10637&dc_veohtv=no&dc_sexy=false&dc_planguage=&pageUrl=http://www.veoh.com/videos/e10637&searchTerm=superman&player=videodetails&permalinkId=e10637&id=anonymous&playAuto=1&external=0&affiliateId=&pageUID=36413798&ss_partnerId=619&dc_pcategory=&videoId=10637&eventType=content&eventValue=104&veohVisitorId=CFF60A9-8AC7-4286-48EA-EB1DC4B7EA38B&pPubStat=Indie&contentSource=&dc_isHD=0&userName=&userAge21plus=&userAgeGroup=&webPlayerInstalled=false&webPlayerVersion=&webPlayerPort=&veohTvInstalled=false -P height=438 -P id=viewportflashPlayer -P name=viewportflashPlayer -P quality=high -P src=http://www.veoh.com/static/flash/players/veohplayer.swf -P style= -P type=application/x-shockwave-flash -P width=540 -P wmode=opaque - 
Forked successfully, child process PID is 7946
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xce9fce8
PARAM: type = application/x-shockwave-flash
PARAM: src = [http://www.veoh.com/static/flash/players/spudts.swf?version=4](http://www.veoh.com/static/flash/players/spudts.swf?version=4)
PARAM: style = 
PARAM: id = spudts
PARAM: name = spudts
PARAM: bgcolor = #eaeaea
PARAM: quality = high
PARAM: wmode = opaque
PARAM: allowscriptaccess = sameDomain
PARAM: flashvars = eventType=search&eventValue=superman&callTS=true
PARAM: width = 1
PARAM: height = 1
NewStream: The full URL is [http://www.veoh.com/static/flash/players/spudts.swf?version=4](http://www.veoh.com/static/flash/players/spudts.swf?version=4)
Closed 68 files.
Starting process: /usr/bin/gtk-gnash -x 61323673 -j 1 -k 1 -u [http://www.veoh.com/static/flash/players/spudts.swf?version=4](http://www.veoh.com/static/flash/players/spudts.swf?version=4) -F 68 -U [http://www.veoh.com/search.html?type=v&searchId=268163083557965318&search=superman](http://www.veoh.com/search.html?type=v&searchId=268163083557965318&search=superman) -P allowscriptaccess=sameDomain -P bgcolor=#eaeaea -P flashvars=eventType=search&eventValue=superman&callTS=true -P height=1 -P id=spudts -P name=spudts -P quality=high -P src=http://www.veoh.com/static/flash/players/spudts.swf?version=4 -P style= -P type=application/x-shockwave-flash -P width=1 -P wmode=opaque - 
Forked successfully, child process PID is 7948
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xc59aae8
PARAM: type = application/x-shockwave-flash
PARAM: src = [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf)
PARAM: style = 
PARAM: id = viewportflashPlayer
PARAM: name = viewportflashPlayer
PARAM: bgcolor = #000000
PARAM: quality = high
PARAM: wmode = opaque
PARAM: allowfullscreen = true
PARAM: allowscriptaccess = always
PARAM: flashvars = fwurl=http://2814.v.fwmrm.net/&fwid=11894&fwsandiskid=&contentRatingId=1&pFamilyFilter=on&dc_intel=true&dc_login=no&dc_publisher=shakeymonkey&dc_hasPublished=&dc_pro=&dc_age18=no&pGender=&pvrn=29844428&dc_ucategory=category_animation;&dc_site=video&dc_tile=1&dc_target=250&dc_videopermalink=v1343263mGM7Zt2M&dc_veohtv=no&dc_sexy=false&dc_planguage=&pageUrl=http://www.veoh.com/videos/v1343263mGM7Zt2M&searchTerm=superman&player=videodetails&permalinkId=v1343263mGM7Zt2M&id=anonymous&playAuto=1&external=0&affiliateId=&pageUID=61115652&ss_partnerId=619&dc_pcategory=&videoId=1343263&eventType=content&eventValue=104&veohVisitorId=CFF60A9-8AC7-4286-48EA-EB1DC4B7EA38B&pPubStat=Indie&contentSource=&dc_isHD=0&userName=&userAge21plus=&userAgeGroup=&webPlayerInstalled=false&webPlayerVersion=&webPlayerPort=&veohTvInstalled=false
PARAM: align = middle
PARAM: width = 540
PARAM: height = 438
NewStream: The full URL is [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf)
Closed 77 files.
Starting process: /usr/bin/gtk-gnash -x 61331558 -j 540 -k 438 -u [http://www.veoh.com/static/flash/players/veohplayer.swf](http://www.veoh.com/static/flash/players/veohplayer.swf) -F 80 -U [http://www.veoh.com/videos/v1343263mGM7Zt2M?rank=3&jsonParams=%7B%22numResults%22%3A20%2C%22rlmin%22%3A0%2C%22query%22%3A%22superman%22%2C%22rlmax%22%3Anull%2C%22veohOnly%22%3Atrue%2C%22order%22%3A%22default%22%2C%22range%22%3A%22a%22%2C%22sId%22%3A%22268163083557965318%22%7D&searchId=268163083557965318&rank=4](http://www.veoh.com/videos/v1343263mGM7Zt2M?rank=3&jsonParams=%7B%22numResults%22%3A20%2C%22rlmin%22%3A0%2C%22query%22%3A%22superman%22%2C%22rlmax%22%3Anull%2C%22veohOnly%22%3Atrue%2C%22order%22%3A%22default%22%2C%22range%22%3A%22a%22%2C%22sId%22%3A%22268163083557965318%22%7D&searchId=268163083557965318&rank=4) -P align=middle -P allowfullscreen=true -P allowscriptaccess=always -P bgcolor=#000000 -P flashvars=fwurl=http://2814.v.fwmrm.net/&fwid=11894&fwsandiskid=&contentRatingId=1&pFamilyFilter=on&dc_intel=true&dc_login=no&dc_publisher=shakeymonkey&dc_hasPublished=&dc_pro=&dc_age18=no&pGender=&pvrn=29844428&dc_ucategory=category_animation;&dc_site=video&dc_tile=1&dc_target=250&dc_videopermalink=v1343263mGM7Zt2M&dc_veohtv=no&dc_sexy=false&dc_planguage=&pageUrl=http://www.veoh.com/videos/v1343263mGM7Zt2M&searchTerm=superman&player=videodetails&permalinkId=v1343263mGM7Zt2M&id=anonymous&playAuto=1&external=0&affiliateId=&pageUID=61115652&ss_partnerId=619&dc_pcategory=&videoId=1343263&eventType=content&eventValue=104&veohVisitorId=CFF60A9-8AC7-4286-48EA-EB1DC4B7EA38B&pPubStat=Indie&contentSource=&dc_isHD=0&userName=&userAge21plus=&userAgeGroup=&webPlayerInstalled=false&webPlayerVersion=&webPlayerPort=&veohTvInstalled=false -P height=438 -P id=viewportflashPlayer -P name=viewportflashPlayer -P quality=high -P src=http://www.veoh.com/static/flash/players/veohplayer.swf -P style= -P type=application/x-shockwave-flash -P width=540 -P wmode=opaque - 
Forked successfully, child process PID is 7950
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xcdc9bc0
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
PARAM: src = [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
PARAM: flashvars = basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66
PARAM: quality = high
PARAM: wmode = transparent
PARAM: bgcolor = #ffffff
PARAM: name = small_badge_top
PARAM: allowscriptaccess = sameDomain
PARAM: type = application/x-shockwave-flash
PARAM: pluginspage = [http://www.macromedia.com/go/getflashplayer](http://www.macromedia.com/go/getflashplayer)
PARAM: align = middle
PARAM: width = 300
PARAM: height = 78
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xa098d60
NewStream: The full URL is [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
Closed 66 files.
Starting process: /usr/bin/gtk-gnash -x 61343285 -j 300 -k 78 -u [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf) -F 67 -U [http://www.tioti.com/show/actorsstudio/seasons_episodes](http://www.tioti.com/show/actorsstudio/seasons_episodes) -P align=middle -P allowscriptaccess=sameDomain -P bgcolor=#ffffff -P flashvars=basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66 -P height=78 -P name=small_badge_top -P pluginspage=http://www.macromedia.com/go/getflashplayer -P quality=high -P src=http://www.tioti.com/swf/small_badge_2.6.swf -P type=application/x-shockwave-flash -P width=300 -P wmode=transparent - 
Forked successfully, child process PID is 7952
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
PARAM: src = [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
PARAM: flashvars = basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66
PARAM: quality = high
PARAM: wmode = transparent
PARAM: bgcolor = #ffffff
PARAM: name = small_badge_top
PARAM: allowscriptaccess = sameDomain
PARAM: type = application/x-shockwave-flash
PARAM: pluginspage = [http://www.macromedia.com/go/getflashplayer](http://www.macromedia.com/go/getflashplayer)
PARAM: align = middle
PARAM: width = 300
PARAM: height = 78
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xc2280d8
NewStream: The full URL is [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
Closed 66 files.
Starting process: /usr/bin/gtk-gnash -x 61346588 -j 300 -k 78 -u [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf) -F 67 -U [http://www.tioti.com/show/actorsstudio/S01E01](http://www.tioti.com/show/actorsstudio/S01E01) -P align=middle -P allowscriptaccess=sameDomain -P bgcolor=#ffffff -P flashvars=basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66 -P height=78 -P name=small_badge_top -P pluginspage=http://www.macromedia.com/go/getflashplayer -P quality=high -P src=http://www.tioti.com/swf/small_badge_2.6.swf -P type=application/x-shockwave-flash -P width=300 -P wmode=transparent - 
Forked successfully, child process PID is 7955
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
PARAM: src = [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
PARAM: flashvars = basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66
PARAM: quality = high
PARAM: wmode = transparent
PARAM: bgcolor = #ffffff
PARAM: name = small_badge_top
PARAM: allowscriptaccess = sameDomain
PARAM: type = application/x-shockwave-flash
PARAM: pluginspage = [http://www.macromedia.com/go/getflashplayer](http://www.macromedia.com/go/getflashplayer)
PARAM: align = middle
PARAM: width = 300
PARAM: height = 78
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xc3aae30
NewStream: The full URL is [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf)
Closed 66 files.
Starting process: /usr/bin/gtk-gnash -x 61349448 -j 300 -k 78 -u [http://www.tioti.com/swf/small_badge_2.6.swf](http://www.tioti.com/swf/small_badge_2.6.swf) -F 67 -U [http://www.tioti.com/show/actorsstudio/seasons_episodes](http://www.tioti.com/show/actorsstudio/seasons_episodes) -P align=middle -P allowscriptaccess=sameDomain -P bgcolor=#ffffff -P flashvars=basePath=http://www.tioti.com/&userBadgesPage=people/irish66/badges&serviceURL=http://www.tioti.com/services/tioti?wsdl&username=irish66 -P height=78 -P name=small_badge_top -P pluginspage=http://www.macromedia.com/go/getflashplayer -P quality=high -P src=http://www.tioti.com/swf/small_badge_2.6.swf -P type=application/x-shockwave-flash -P width=300 -P wmode=transparent - 
Forked successfully, child process PID is 7958
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Player request channel hang up
Shutting down
Child process exited with status 0
plugin instance destruction
shutting down input chan 0xc0557d8
Shutting down
Child process exited with status 15
plugin instance destruction
shutting down input chan 0xd0cc510
** Message: ~totemPlugin [0xc4130e8]
** Message: ~totemGMPPlayer [0xcfea728]
** Message: NP_Shutdown
^[NS_PluginInitialize called, but ignored (we already initialized)
PARAM: src = [http://www.youtube.com/v/G66B3_hApgo&hl=en&fs=1](http://www.youtube.com/v/G66B3_hApgo&hl=en&fs=1)
PARAM: type = application/x-shockwave-flash
PARAM: allowfullscreen = true
PARAM: width = 375
PARAM: height = 303
PARAM: src = [http://www.youtube.com/v/NBSKPOhdVmU&hl=en&fs=1](http://www.youtube.com/v/NBSKPOhdVmU&hl=en&fs=1)
PARAM: type = application/x-shockwave-flash
PARAM: allowfullscreen = true
PARAM: width = 375
PARAM: height = 303
PARAM: src = [http://www.youtube.com/v/WrljnWhaOeg&hl=en&fs=1](http://www.youtube.com/v/WrljnWhaOeg&hl=en&fs=1)
PARAM: type = application/x-shockwave-flash
PARAM: allowscriptaccess = always
PARAM: allowfullscreen = true
PARAM: width = 375
PARAM: height = 303
NewStream: The full URL is [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=G66B3_hApgo&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html&iurl=http%3A//i4.ytimg.com/vi/G66B3_hApgo/hqdefault.jpg&sk=vGbaxWMquu9XpV_ei0NRBoHW5Wz_PkTAC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=G66B3_hApgo&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html&iurl=http%3A//i4.ytimg.com/vi/G66B3_hApgo/hqdefault.jpg&sk=vGbaxWMquu9XpV_ei0NRBoHW5Wz_PkTAC&use_get_video_info=1&load_modules=1&fs=1&hl=en)
Forked successfully, child process PID is 8173
Closed 67 files.
Starting process: /usr/bin/gtk-gnash -x 61368903 -j 375 -k 303 -u [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=G66B3_hApgo&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html&iurl=http%3A//i4.ytimg.com/vi/G66B3_hApgo/hqdefault.jpg&sk=vGbaxWMquu9XpV_ei0NRBoHW5Wz_PkTAC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=G66B3_hApgo&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html&iurl=http%3A//i4.ytimg.com/vi/G66B3_hApgo/hqdefault.jpg&sk=vGbaxWMquu9XpV_ei0NRBoHW5Wz_PkTAC&use_get_video_info=1&load_modules=1&fs=1&hl=en) -F 69 -U [http://goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html](http://goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-1-of-4.html) -P allowfullscreen=true -P height=303 -P src=http://www.youtube.com/v/G66B3_hApgo&hl=en&fs=1 -P type=application/x-shockwave-flash -P width=375 - 
NewStream: The full URL is [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=NBSKPOhdVmU&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html&iurl=http%3A//i3.ytimg.com/vi/NBSKPOhdVmU/hqdefault.jpg&sk=JfOeUlJE-uWva_25CxKw52BmkJ-vPsnlC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=NBSKPOhdVmU&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html&iurl=http%3A//i3.ytimg.com/vi/NBSKPOhdVmU/hqdefault.jpg&sk=JfOeUlJE-uWva_25CxKw52BmkJ-vPsnlC&use_get_video_info=1&load_modules=1&fs=1&hl=en)
Forked successfully, child process PID is 8174
Closed 68 files.
Starting process: /usr/bin/gtk-gnash -x 61368964 -j 375 -k 303 -u [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=NBSKPOhdVmU&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html&iurl=http%3A//i3.ytimg.com/vi/NBSKPOhdVmU/hqdefault.jpg&sk=JfOeUlJE-uWva_25CxKw52BmkJ-vPsnlC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=NBSKPOhdVmU&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html&iurl=http%3A//i3.ytimg.com/vi/NBSKPOhdVmU/hqdefault.jpg&sk=JfOeUlJE-uWva_25CxKw52BmkJ-vPsnlC&use_get_video_info=1&load_modules=1&fs=1&hl=en) -F 70 -U [http://goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html](http://goshlondon.blogspot.com/2008/10/gosh-interviews-kevin-oneill-2-of-4.html) -P allowfullscreen=true -P height=303 -P src=http://www.youtube.com/v/NBSKPOhdVmU&hl=en&fs=1 -P type=application/x-shockwave-flash -P width=375 - 
NewStream: The full URL is [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=WrljnWhaOeg&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html&iurl=http%3A//i4.ytimg.com/vi/WrljnWhaOeg/hqdefault.jpg&sk=nzI5sPhOE3TcNo9_mo0y3jld-7YcNIqcC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=WrljnWhaOeg&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html&iurl=http%3A//i4.ytimg.com/vi/WrljnWhaOeg/hqdefault.jpg&sk=nzI5sPhOE3TcNo9_mo0y3jld-7YcNIqcC&use_get_video_info=1&load_modules=1&fs=1&hl=en)
Forked successfully, child process PID is 8175
Closed 69 files.
Starting process: /usr/bin/gtk-gnash -x 61369195 -j 375 -k 303 -u [http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=WrljnWhaOeg&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html&iurl=http%3A//i4.ytimg.com/vi/WrljnWhaOeg/hqdefault.jpg&sk=nzI5sPhOE3TcNo9_mo0y3jld-7YcNIqcC&use_get_video_info=1&load_modules=1&fs=1&hl=en](http://www.youtube.com/swf/l.swf?swf=http%3A//s.ytimg.com/yt/swf/cps-vfl64504.swf&video_id=WrljnWhaOeg&rel=1&showsearch=1&eurl=http%3A//goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html&iurl=http%3A//i4.ytimg.com/vi/WrljnWhaOeg/hqdefault.jpg&sk=nzI5sPhOE3TcNo9_mo0y3jld-7YcNIqcC&use_get_video_info=1&load_modules=1&fs=1&hl=en) -F 71 -U [http://goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html](http://goshlondon.blogspot.com/2008/11/gosh-interviews-kevin-oneill-3-of-4.html) -P allowfullscreen=true -P allowscriptaccess=always -P height=303 -P src=http://www.youtube.com/v/WrljnWhaOeg&hl=en&fs=1 -P type=application/x-shockwave-flash -P width=375 - 
RcInitFile: couldn't open file: /usr/etc/gnashrc
RcInitFile: couldn't open file: RcInitFile: couldn't open file: /usr/etc/gnashrc
/usr/etc/gnashrc
RcInitFile: couldn't open file: RcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc
/home/irish/.gnashrcRcInitFile: couldn't open file: /home/irish/.gnashrc
RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc

RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc

(firefox:7219): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:7219): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:7219): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:7219): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:7219): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:7219): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:7219): Gtk-CRITICAL **: gtk_text_buffer_get_insert: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(firefox:7219): Gtk-CRITICAL **: gtk_text_buffer_get_iter_at_mark: assertion `GTK_IS_TEXT_MARK (mark)' failed

(firefox:7219): Gtk-CRITICAL **: _gtk_text_layout_get_block_cursor: assertion `layout != NULL' failed

(firefox:7219): Gtk-CRITICAL **: gtk_text_layout_get_cursor_locations: assertion `layout != NULL' failed

(firefox:7219): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed

(firefox:7219): Gdk-CRITICAL **: gdk_window_invalidate_rect: assertion `window != NULL' failed
Segmentation fault
irish@ubuntu:~$ Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
Main loop ended, cleaning up
Any segfault past this message is likely due to improper threads cleanup.
irish@ubuntu:~$ 2llowsllowsllows

---

### Post by starcannon on 2008-11-14
Open up System>Administration>Synaptic Package Manager, search for gnash, uninstall gnash, then search for ubuntu-restricted-extras, install ubuntu-restricted-extras, this should have your firefox flash crash fixed, it may occasionally crash still, but for me I haven't had a flash crash in many months, others still report it as an issue.

GL and keep it fun

---

### Post by irish66 on 2008-11-15
Thank you very much. Well the first thing, I've noticed is, that there isn't a lot of text after "firefox" when i type it into terminal. There
was before. 
But as I mentioned previously, it also crashes in Windows. I've been doing a google "flash player crashes web browsers, and see that addons might conflict with it. So I guess that's the next thing to look at, in windows and if i experience more crashes here.
M

---

### Post by irish66 on 2008-11-17
Well, still having problem with keyboard even though I finally found out how to change settings to keyboard I have, and to Ireland.
I still get 6 when pressing shft key and right arrow key.
alt key and right arrow key get me the letter c in terminal, but do nothing otherwise.
M

---

### Post by starcannon on 2008-11-17
Your keyboard layout must be an oddball, all of my keyboards are happy to hi-lite using Shift+Arrow keys.

A place to start may be with:
System>Preferences>Keyboard

Try the US layout see if that fixes you (US is working as expected here), if that doesn't sort you out, I'd cycle through the rest of the English language layouts. If that still doesn't fix things, then we'll take up from there.

GL, and keep smilin'

---

### Post by irish66 on 2008-11-17
Ta, that is something I'll do in little bits ie cycling throug various european countries. American settings don't work, as that's how it was
set up initally.
Keyboard  is cordless logitech ex110 and is set in keyboard settings that.
I guess one solution when wrting something is to emulate a windows program with Wine. I KNOW TEXt selection in windows notepad through wine works fine> and indeed in pEERWeb.

---

### Post by sirjoebob on 2008-11-17
> **irish66 said:**
> RcInitFile: couldn't open file: /usr/etc/gnashpluginrc
RcInitFile: couldn't open file: /home/irish/.gnashpluginrc

Based on this, looks like a flash issue. I would try the flash-nonfree plugin rather than using Gnash. It has caused issues for me before.

---

### Post by irish66 on 2008-11-17
yep, have that done. It's too early yet to say whether or not, Flash is crashing less though.
M

---

