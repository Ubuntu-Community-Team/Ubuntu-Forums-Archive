---
title: "Curl help"
date: 2014-09-12
forum: Programming Talk
---

### Post by peter_brickles on 2014-09-12
HI I am trying to write a script where i can enter a dvd's bar code at the cli and return the price sites will pay for the dvd.

the bard code im using for testing is

> ** 8717418242275 **

this site is

> [http://www.webuydvds.co.uk/start-here.aspx](http://www.webuydvds.co.uk/start-here.aspx)

through use of httpfox i have found some info whic i need to use with curl 

> 
ctl00$ScriptManager1    ctl00$upGetValue|ctl00$btnGetValue 
ctl00$txtBarcode    8717418242275 
ctl00$ContentPlaceHolder1$hndMinItem    10 
ctl00$ContentPlaceHolder1$hndMaxItem    500 
ctl00$ContentPlaceHolder1$hndMinPrice     
ctl00$ContentPlaceHolder1$hndMaxPrice     
ctl00$ContentPlaceHolder1$hndMaxSalesRank     
ctl00$ContentPlaceHolder1$hndMaxDupItems    1 
ctl00$ContentPlaceHolder1$hndGridItemCount    1 
__LASTFOCUS     
__EVENTTARGET     
__EVENTARGUMENT     
__VIEWSTATE    /wEPDwUJLTU3ODM4OTEyD2QWAmYPZBYCAgQPZBYIAgMPFgIeB1Zpc2libGVnFgICAQ8PFgIfAGdkFgoCAQ8WAh8AZ2QCAw8WAh8AZ2QCBQ8WAh8AZ2QCCQ8WAh8AaGQCCw8WAh8AZ2QCBw9kFgJmD2QWAgIBDw9kFgIeCm9ua2V5cHJlc3MFKHJldHVybiBjb250cm9sRW50ZXIoJ2N0bDAwX2J0bkdldFZhbHVlJylkAggPFQ0NL0RlZmF1bHQuYXNweBAvc3RhcnQtaGVyZS5hc3B4Fi9ob3ctaXQtYWxsLXdvcmtzLmFzcHgPL3NlbGwtZHZkcy5hc3B4EC9zZWxsLWdhbWVzLmFzcHgOL3NlbGwtY2RzLmFzcHgWL0Nhc2gtZm9yLW1vYmlsZXMuYXNweA4vYWJvdXQtdXMuYXNweAkvZmFxLmFzcHgPL2NvbnRhY3R1cy5hc3B4BS9ibG9nHi9TZW5kaW5nWW91ckl0ZW1zVG9Vc0ZyZWUuYXNweA0vYmxvZy9zaXRlbWFwZAIJD2QWAmYPZBYCZg9kFgwCAQ8PFgIeBFRleHRlZGQCAw8PFgIfAmVkZAIFDzwrABEDAA8WBB4LXyFEYXRhQm91bmRnHgtfIUl0ZW1Db3VudGZkARAWABYAFgAMFCsAAGQCCQ8PZBYCHgdvbmNsaWNrBT1qYXZhc2NyaXB0OnJldHVybiBDaGVja0lmVXNlckxvZ2dlZEluRm9yU2F2aW5nT3JkZXIoJ0ZhbHNlJyk7ZAILD2QWAmYPD2QWAh8FBTFqYXZhc2NyaXB0OnJldHVybiBDaGVja1Rlcm1BbmRDb25kaXRpb24oJ0ZhbHNlJyk7ZAIMDxUBGi90ZXJtcy1hbmQtY29uZGl0aW9ucy5hc3B4ZBgCBR5fX0NvbnRyb2xzUmVxdWlyZVBvc3RCYWNrS2V5X18WAQUuY3RsMDAkQ29udGVudFBsYWNlSG9sZGVyMSRjaGtUZXJtc0FuZENvbmRpdGlvbgUmY3RsMDAkQ29udGVudFBsYWNlSG9sZGVyMSRndkVhbk51bWJlcnMPPCsADAIGFQEQT1JERVJfREVUQUlMU19JRAhmZA== 
__ASYNCPOST    true 
ctl00$btnGetValue    




can any one advise me how to formulate a curl command with the relevant info which will return the page containing  the price offered for the dvd ? 

any help at all would be appreciated 


Pete

---

