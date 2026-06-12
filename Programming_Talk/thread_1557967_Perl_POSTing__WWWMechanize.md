---
title: "Perl POSTing / WWW::Mechanize"
date: 2010-08-21
forum: Programming Talk
---

### Post by StOoZ on 2010-08-21
I have the following code, which uses Mechanize the TableExtract module,everything works like a charm, except the fact that I'm not capable of moving to the next pages.... 
I'm trying a list of hotspots from: 
[http://www.wigle.net/gps/gps/main](http://www.wigle.net/gps/gps/main) 

UserID: natty_a 
password: natty 

click on '[searching' 
and then on 'Query' 

my script should accept coords and data and bring that table.... it does that, but only for the first page, seems like I cannot move to the next pages (cant clikcon 'Next100 >>' 

I tried clicking on it like that: 
1) 	
[PHP] $mech_browser->post('https://wigle.net/gps/gps/main/confirmquery/',[ pagestart => $i, 
                                                                               Query => 'Next100 >>' ])[/PHP]

mech_browser is of the WWW::Mechanize 
and i is just the num of results to get (Used HTTP Live Headers to find it out) 

2)	
[PHP] $mech_browser->click_button(  value => 'Next100 >>')[/PHP]

nothing...doesnt work. 
any idea??? 

thanks,

---

