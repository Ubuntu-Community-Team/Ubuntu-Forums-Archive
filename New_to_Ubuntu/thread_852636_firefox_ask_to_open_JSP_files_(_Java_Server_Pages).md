---
title: "firefox ask to open JSP files ( Java Server Pages)"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by aBitLater on 2008-07-07
I'm trying to watch video at [http://www.history.com]("http://www.history.com") in firefox 3 on hardy.

I'm using the beta 2 of flashplugin, and it shows up correctly in firefox about:plugins

when I get to the page to open full episodes for UFO Hunters, firefox tries to save or open the jsp files... neither option helps my page display correctly.  Opening it just displays the code in sections of the web page.

I checked Edit / Preferences / Applications / JSP File, and it has the following options:

Always ask
Save File
Use firefox-3.0 (because I pointed it to firefox-3.0 once)
Use other
Application Details

Does anyone else have this issue? and/or how can I fix it?

Maybe someone can go here --> [http://www.history.com/minisites/ufohunters]("http://www.history.com/minisites/ufohunters") ... and click on the link "Watch full episodes", just under "highlights".

Many thanks in advance!
Brian

---

### Post by webofunni on 2008-07-08
Hi,

  What is the result of following link 

[http://www.history.com//bcplayers/Player/3Tier/SharedFiles/playerPage.jsp?action=&bcpid=1431564227&bclid=1519677067&bctid=1521061002&bclrid=&asof=&playerID=1431564227&baseURL=/bcconfig/Player/3Tier/UFO_Hunters/config-xml&adTechID=1491160&pageAdTechID=1497127&baseDIR=/bcplayers/Player/3Tier/SharedFiles&grp=%22+pageGroupId](http://www.history.com//bcplayers/Player/3Tier/SharedFiles/playerPage.jsp?action=&bcpid=1431564227&bclid=1519677067&bctid=1521061002&bclrid=&asof=&playerID=1431564227&baseURL=/bcconfig/Player/3Tier/UFO_Hunters/config-xml&adTechID=1491160&pageAdTechID=1497127&baseDIR=/bcplayers/Player/3Tier/SharedFiles&grp=%22+pageGroupId)

---

### Post by aBitLater on 2008-07-08
> What is the result of following link

[http://www.history.com//bcplayers/Pl...22+pageGroupId](http://www.history.com//bcplayers/Pl...22+pageGroupId)

I've attached a screenshot of firefox at that link - the media window has a grayed out play button and the screen doesn't appear properly.

I *may* have fixed the JSP problem, though.  I had installed version 10, beta 2 of Adobe flash per instructions from another ubuntu thread, but version 9 was still on my system.  I removed it via Synaptic, and I think it got rid of some dependent files for version 10, so I reinstalled version 10.  After doing that, firefox is not opening JSP files - but the Prefs / Application still has them listed as "always ask".

At [http://www.history.com/minisites/ufohunters]("http://www.history.com/minisites/ufohunters") the flash video window is very slow to load (though it will eventually play the commercial), and firefox just creeps when I'm on that tab.  Even menu clicks take about 2 seconds to respond... but I click on the ubuntu tab (where I'm writing this), and firefox responds normally.

Thanks again.

---

