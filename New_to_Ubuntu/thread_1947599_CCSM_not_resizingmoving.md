---
title: "CCSM not resizing/moving"
date: 2012-03-26
forum: New to Ubuntu
---

### Post by ssdt on 2012-03-26
I am trying to make an window for gnome image viewer open at the same location (bottom left) and at the same size. I have been trying ccsm in the ubuntu 11.10 system but until now i didn't have any success.

these are the settings that i have now that didn't fix this issue.
[IMG]http://imgur.com/343UO[/IMG]
[IMG]http://imgur.com/gGWXx[/IMG]

can anyone tell me how i can fix this so that gnome image viewer opens at the bottom left with a 150p X 150p screen?

---

### Post by yetiman64 on 2012-03-26
Probably a bit easier would be to install devilspie and gdevilspie and use them. I've never had success with ccsm for this.

devilspie runs as a daemon (can be set to run at startup) and monitors any rules for windows/applications you set in the gui (gdevilspie).

Very easy to set the geometry rules, placement and size, for the windows you mention. When saving a rule remember to stop then restart the daemon from the rules window to see the changes and then alter if needed.

---

### Post by ssdt on 2012-03-27
i have installed devilspie and added this as my rule:


( if 
( begin 
( contains ( window_class ) "eog" )
( contains ( application_name ) "Image Viewer" )
) 
( begin 
( geometry "542x484+0+0" )
( println "match" )
)
)


still this doesn't work. can anyone tell me why?

---

### Post by yetiman64 on 2012-03-27
> **ssdt said:**
> i have installed devilspie and added this as my rule:


( if 
( begin 
( contains ( window_class ) "eog" )
( contains ( application_name ) "Image Viewer" )
) 
( begin 
( geometry "542x484+0+0" )
( println "match" )
)
)


still this doesn't work. can anyone tell me why?
One that works here by comparison
> ( if 
( begin 
( is ( application_name ) "gdevilspie" )
( is ( window_name ) "gDevilspie" )
) 
( begin 
( geometry "650x650+445+0" )
( println "match" )
)
)
Note the application_name and window_name here where you have used application_name and window_class. This example keeps the main devilspie window to a 650x650 size and moves it across to middle top of the the screen.

---

### Post by ssdt on 2012-03-27
but it's not possible to edit the code. could you edit it?

---

### Post by yetiman64 on 2012-03-27
> **ssdt said:**
> but it's not possible to edit the code. could you edit it?
You don't edit the raw output as you posted, you will need to select the Rule Name in the main window and click edit > Set up Matching rules (this is where you need to tick application_name and window_name) > Finally set up the geometry rules as you need them.

See attached screenshots for a visual example of the above steps.

---

### Post by ssdt on 2012-03-28
Solved. Thanks. I just had to change the window name to "Image Viewer" and not eog. thanks

---

