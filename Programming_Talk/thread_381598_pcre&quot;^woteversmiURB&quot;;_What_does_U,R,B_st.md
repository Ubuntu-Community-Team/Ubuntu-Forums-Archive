---
title: "pcre:&quot;/^wotever/smiURB&quot;; What does U,R,B stand for?"
date: 2007-03-11
forum: Programming Talk
---

### Post by Andrea_44 on 2007-03-11
PCRE(Perl Compatible Regular Expression)
What does the modifier /U, /R, /B at the end of the following PCRE stand for?

pcre:"/\x2F[^\r\n]*\.(dat)|(xml)\?[^\r\n]*v=[^\r\n]*t=[^\r\n]*c=/Ui";

pcre:"/a\x3a\s*propfind.*?xmlns\x3a\s*a=[\x21\x22]?DAV[\x21\x22]?/iR";

pcre:"/T.*?T.*?Y.*?P.*?R.*?O.*?M.*?P.*?T/RBi";

Here is the documentation of the language, but I cannot find anything related to those modifier:
[http://perldoc.perl.org/perlre.html]("http://perldoc.perl.org/perlre.html")

I have been stuck on this issues for a little while, any help will be greatly appreciated!

Cheers~
Andrea

FYI, those PCRE are from the following Snort rules:

alert tcp $HOME_NET any -> $EXTERNAL_NET $HTTP_PORTS (msg:"SPYWARE-PUT Hijacker comet systems runtime detection - update requests"; flow:to_server,established; uricontent:"v="; nocase; uricontent:"t="; nocase; uricontent:"c="; nocase; content:"Host|3A|"; nocase; content:"update.cc.cometsystems.com"; distance:0; nocase; pcre:"/\x2F[^\r\n]*\.(dat)|(xml)\?[^\r\n]*v=[^\r\n]*t=[^\r\n]*c=/Ui"; pcre:"/^Host\x3A[^\r\n]*update\.cc\.cometsystems\.com/smi"; threshold:type limit, track by_src, count 1, seconds 600; reference:url,[www.spywareguide.com/product_show.php?id=428;](www.spywareguide.com/product_show.php?id=428;) reference:url,www3.ca.com/securityadvisor/pest/pest.aspx?id=453088065; classtype:misc-activity; sid:5831; rev:1;)

alert tcp $EXTERNAL_NET any -> $HTTP_SERVERS $HTTP_PORTS (msg:"WEB-MISC WebDAV propfind access"; flow:to_server,established; content:"propfind"; nocase; pcre:"/<a\x3a\s*propfind.*?xmlns\x3a\s*a=[\x21\x22]?DAV[\x21\x22]?/iR"; reference:bugtraq,1656; reference:cve,2000-0869; reference:nessus,10505; reference:url,[www.microsoft.com/technet/security/bulletin/MS04-030.mspx;](www.microsoft.com/technet/security/bulletin/MS04-030.mspx;) classtype:web-application-activity; sid:1079; rev:15;)

alert tcp $EXTERNAL_NET any -> $HTTP_SERVERS $HTTP_PORTS (msg:"WEB-MISC WebDAV propfind access"; flow:to_server,established; content:"propfind"; nocase; pcre:"/ $TELNET_SERVERS 23 (msg:"TELNET login buffer non-evasive overflow attempt"; flow:to_server,established; flowbits:isnotset,ttyprompt; content:"|FF FA|'|00 00|"; rawbytes; pcre:"/T.*?T.*?Y.*?P.*?R.*?O.*?M.*?P.*?T/RBi"; flowbits:set,ttyprompt; reference:bugtraq,3681; reference:cve,2001-0797; reference:nessus,10827; classtype:attempted-admin; sid:3274; rev:4;)

---

### Post by phossal on 2007-03-11
You're looking for this: [http://www.snort.org/docs/snort_manual/node21.html#SECTION004510000000000000000](http://www.snort.org/docs/snort_manual/node21.html#SECTION004510000000000000000)

> Snort specific modifiers 
R 	Match relative to the end of the last pattern match. (Similar to distance:0; )
U 	Match the decoded URI buffers (Similar to uricontent)
B 	Do not use the decoded buffers (Similar to rawbytes)

---

### Post by Andrea_44 on 2007-03-12
Thank you so much for the information!
Very much appreciated!

Cheers~
Andrea

---

