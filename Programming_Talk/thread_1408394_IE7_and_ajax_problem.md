---
title: "IE7 and ajax problem"
date: 2010-02-16
forum: Programming Talk
---

### Post by meastwood on 2010-02-16
I think this is an old problem but am unable to resolve it.  

Am implementing unobtrusive javascript.  If javascript is enabled I have a function that 'ajaxifies' all my links - this works fine in the usual browsers as well as IE6 and IE8.  

In IE7 (7.0.6000.16982) however, when an 'ajaxified' link is clicked data is downloaded and displayed in the browser ok (after some css hacks/modifications that is).  IE7 then keeps calling the same function that downloads the data. It loops indefinitely ... 

Am running lighttpd on ubuntu - the logs show that no additional requests for the same data are being made/logged.  Yet to monitor the network.

To date I have found that this may be an old problem circa 2006/7 for IE7 where the ActiveX XHR object continues to resend the XMLHttpRequest.  The solution is to use the native IE7 XHR object instead of the ActiveX one.

I'm using JQuery (latest version) - so I would of expected this issue to have been resolved.

So - if it is this problem how do I get JQuery to use the native IE7 XHR object?

If it is not this problem - does any one have any ideas please.

---

### Post by Hellkeepa on 2010-02-16
HELLo!

Do you have a link to a site where this problem is demonstrated? We can't do much about this, before we have something to test, after all.

Happy codin'!

---

### Post by meastwood on 2010-02-17
Unfortunately not yet - I'm building everything from scratch at home.  The server is on a separate box on my internal lan.  Server build is yet to be 'secured', only bits of the build are working as 'designed' at the moment (dummy links, old html, old css) - would need to tidy it all up - no harm in that I guess.  

Have yet to get a domainname for it - could set up a firewall route on my internal router to allow outside access via my ISP's allocated domainname for the modem or via the modem's IP : port - not really wanting to do this yet.  Some ISPs block certain ports though can configure to use alternate port to 80.  

Just not too keen on opening the box up at the moment ...

###
Am fairly sure now that this is the problem.  JQuery's $.ajax() default's to using the ActiveX XHR.  I noted on Microsoft's Development Network that they recommend that the ActiveX XHR should be used as a 'last resort' and it is this that causes the looping.

It is possible to change $.ajax()'s default behaviour via '$.ajax({xhr:"...."})' - just do not know what to use in place of "...." so that IE7's native XHR is used? 
###

###
Have tried
......
```
var brwsr = detect_ie();
if ( brwsr == "IE7" ){
   $.ajaxSetup({xhr:function(){
       return new XMLHttpRequest();
   }});
}
```
......

Still get the same problem; traced network - requests are not being resent to server.

---

### Post by meastwood on 2010-02-17
As stated earlier this only occurred on IE7 ....  The problem was not with the XHR object - either ActiveX or Native, both work OK now.  

When javascript is enabled on a browser I have a function js_anchors() that adds a click event to all links.  This event causes the ajaxIt() function to be run instead of the links's default behaviour.  This function first runs on document.ready() to set up the links in the 'home' page.

Original js_anchors():
[HTML]function js_anchors() {
   		$('.ajax_it').click(function () {
  		  	var param = $(this).attr('rel');
  		  	$(this).attr('href','#');
  		  	ajaxIt(param);
  		});
  }[/HTML]

Whenever a link is clicked new data is added to a div in the 'home' page.  This new data will also have links that need to be 'ajaxified'.  I was doing this by calling js_anchors() from ajaxIT()  each time it had successfully downloaded new data.  Never too happy with this - links that are always present on the 'home' page would have the same event handler added multiple times - do not know the consequences of this however everything seemed to work OK.

Original ajaxIt():
[HTML]function ajaxIt(tag_url) {
                 var tag_and_url = tag_url.split(","); 
                 var tag = tag_and_url[0];
                 var url = tag_and_url[1];
                 var match_idx = /idx\.html/;
                 if ( url.search(match_idx) != -1 ) {
                    ...................
                 };

                $('#menu2').load(url+' .hide_it','', function () {
                    ...................     
                });

               $(tag).load(url+' #contents','', function () {
                    js_anchors();
                    local_links(); });
}[/HTML]

On IE7 it was the calling of js_anchors() from ajaxIt() that was causing the infinite loop.  It would appear that instead of adding an event handler to run ajaxIt() it was calling ajaxIt() directly.  This does not occur when js_anchors() is run for the first time on document.ready().  So, in IE7, perhaps this is the consequence of adding the same event multiple times to the same object.  If the event already exists for an object IE7 calls the handler rather than ignoring it ... ??

To fix:
Removed the js_anchors() call from ajaxIt().

Read up a bit on on jquery events and modified js_anchors() to:
[HTML]function js_anchors() {
   		$('.ajax_it').live('click', (function () {
  		  	var param = $(this).attr('rel');
  		  	$(this).attr('href','#');
  		  	ajaxIt(param);
  		});
  }  [/HTML]

The .live() "attaches a handler to the event for all elements which match the current selector, now or in the future"

---

