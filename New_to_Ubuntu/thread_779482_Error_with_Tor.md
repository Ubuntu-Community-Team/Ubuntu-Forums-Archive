---
title: "Error with Tor"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by bhougland on 2008-05-02
Hey guys-

I followed the guide from this site, to set up tor, but am having errors come up when I enable tor (through the Torbutton extention in firefox).

[http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html](http://www.ubuntu-unleashed.com/2007/09/setup-vidalia-tor-gui-with-ubuntu-and.html)


THis is the error message I am getting:


Exception in sandbox evaluation. Date hooks not applied:
[Exception... "Not enough arguments"  nsresult: "0x80570001 (NS_ERROR_XPC_NOT_ENOUGH_ARGS)"  location: "JS frame :: chrome://torbutton/content/torbutton.js :: anonymous :: line 1722"  data: no]

anyone have any clue how to fix this?

Thank you,
B

---

### Post by Nero_Flint on 2009-06-27
I had problems using Torbutton as well so I stopped using it. Uninstall Torbutton in Firefox and install QuickProxy: 

[https://addons.mozilla.org/en-US/firefox/addon/1557](https://addons.mozilla.org/en-US/firefox/addon/1557)

Restart Firefox and go to Edit--> Preferences --> Advanced --> Network --> Connection --> Settings and click Manual Proxy Settings and enter the following information:

HTTP Proxy/SSL Proxy/FTP Proxy/Gopher Proxy= 127.0.0.7 Port: 8118

SOCKS Host= 127.0.0.1 Port: 9050

Click OK and right click on the QuickProxy button on the lower right side of the status bar and then check off "Manual Proxy Configuration" and click OK. 

Click on the QuickProxy button to turn on Tor (red colour means proxy is off and green colour means its on).

Go here to see if Tor is working:

[http://ip-address.domaintools.com/](http://ip-address.domaintools.com/)

If Tor is not working that means there is a problem with how you set it up and we'll see if we can figure it out from there.

---

