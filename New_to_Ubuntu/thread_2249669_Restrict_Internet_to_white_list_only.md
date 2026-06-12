---
title: "Restrict Internet to white list only"
date: 2014-10-23
forum: New to Ubuntu
---

### Post by ben5 on 2014-10-23
In setting up some 200+ Ubuntu PCs in a call center where I want them to only be able to reach specific websites on a white list.


At our other call center they are organized into a subnet sign blocking at the firewall.  But in this call center things are not as organized and I'm hoping to do the restriction at the PC.


I looked at some other threads and see that people mention dansguardian a lot.  I have not looked at it yet as I wanted to ask around first because **the emphasis here is on simple to set up.  I don't need features all I need is to block everything except the white list of domains.  And I want to set it up initially with a script as well as update the white list when needed with a script.  Anything gui/interactive is not an option. **


If Dan's Guardian has a simple plaintext config file and doesn't require any interactive set up that might work.


If not I am wondering about doing this via DNS/hosts file.  I know how to 'blacklist'the site by adding it to the hosts file with the bogus IP but I'm wondering if it is possible to basically have a wildcard entry in the hosts file pointing everything to a bogus IP except for specific sites.


From what I have read this might not be possible.  I saw one person suggest perhaps just manually putting the weight listed sites in the hosts file and disabling external DNS.  Though this is less than ideal as it would need to be updated if the domain name changes IP's.  


Any thoughts or ideas?

---

### Post by ben5 on 2014-10-23
Dansguardian seems pretty good...

I followed example here. 

[http://contentfilter.futuragts.com/wiki/doku.php?id=configuration_examples](http://contentfilter.futuragts.com/wiki/doku.php?id=configuration_examples)

Basically put ** in bannedsitelist and then list the whitelisted sites in exceptionsitelist. 

Simple enough... I can script that...

However I restart the dansguardian service after that and I can still get to any site.   Any ideas?

---

### Post by ben5 on 2014-10-24
FYI - dansguardian seemed like too much trouble for what I am looking for... have to install squid proxy and then make the PC use the proxy etc... 

I decided to go with a simple dns setup... remove " dns" from the nsswitch file and then have my server generate a hosts file every 5 minutes for the PC.  (i.e. it looks up the current IP address for every server on the white list and writes it to a hosts file that is then downloaded to all the clients and viola... they can only access the sites I have added to their hosts files)

---

